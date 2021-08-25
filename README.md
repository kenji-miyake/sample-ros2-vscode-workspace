# sample-ros2-vscode-workspace

## Usage

### Setup

```sh
git clone git@github.com:kenji-miyake/sample-ros2-vscode-workspace.git
cd sample-ros2-vscode-workspace
mkdir src
vcs import src < workspace.repos
wget -O .cspell.json https://raw.githubusercontent.com/tier4/autoware-spell-check-dict/main/cspell/.cspell.json
code .
```

### Build

```sh
source /opt/ros/galactic/setup.bash
colcon build --symlink-install --cmake-args -DCMAKE_BUILD_TYPE=Release -DCMAKE_EXPORT_COMPILE_COMMANDS=1
```

### Test

```sh
source install/setup.bash
colcon test --event-handlers console_cohesion+
# Or to save time
colcon test --event-handlers console_cohesion+ --packages-skip-test-passed --packages-select package_name
# Or
colcon test --event-handlers console_cohesion+ --packages-skip-test-passed --base-paths src/sample_package
```
