# 计时器

在 Bevy 中，你可以使用计时器（Timer）来实现定时任务和时间相关的功能。Bevy 提供了 `Timer` 类型，可以方便地创建、启动、停止和查询计时器。

## 一般用法

1. 导入 `bevy::prelude::*`，以引入 Bevy 相关的模块和类型。
2. 创建一个 `Timer` 实例，并指定计时器的持续时间（即触发事件的时间间隔）。
3. 在适当的地方，通过 `timer.tick(delta_time)` 更新计时器的状态，其中 `delta_time` 是每帧的时间增量。
4. 通过 `timer.finished()` 或 `timer.just_finished` 检查计时器是否已经完成（即达到了指定的持续时间）。
5. 在计时器完成时执行相应的操作，比如触发事件或执行特定的逻辑。

## 示例代码

```rust
use bevy::prelude::*;

fn main() {
    App::build()
        .add_plugins(DefaultPlugins)
        .add_startup_system(setup.system())
        .add_system(timer_system.system())
        .run();
}

fn setup(commands: &mut Commands) {
    commands.spawn().insert(Timer::from_seconds(1.0, true));
}

fn timer_system(time: Res<Time>, mut query: Query<&mut Timer>) {
    for mut timer in query.iter_mut() {
        timer.tick(time.delta_seconds());
        if timer.finished() {
            println!("Timer finished!");
        }
    }
}
```

在这个示例中，我们在启动系统时创建了一个持续时间为 1 秒的计时器，并设置为循环模式（即一直重复触发）。
在 `timer_system` 系统中，我们更新计时器的状态，并检查计时器是否完成。如果计时器完成，我们打印出一条消息。

这个示例展示了如何使用 Bevy 计时器来实现定时任务。你可以根据自己的需求，在计时器完成时执行相应的操作，比如触发游戏事件、更新游戏状态等。

## 常见用法

- 触发重复事件：可以设置一个计时器来触发重复事件，比如每隔一定时间生成新的敌人或更新游戏状态。

- 延迟执行操作：可以使用计时器来延迟执行一些操作，比如在游戏开始后等待几秒钟再开始玩家控制。

- 动画效果：计时器可以用于创建动画效果，比如在一定时间内逐渐改变一个实体的位置、大小或颜色。

- 游戏倒计时：计时器可以用于实现游戏中的倒计时功能，比如在一定时间内完成任务或挑战。

- 超时处理：可以设置一个计时器来处理超时情况，比如在玩家未在规定时间内完成操作时触发相应的逻辑。

## 常用API

1. `new`: 创建一个新的计时器，并指定延迟时间和是否重复执行。

```rust
let timer = Timer::new(duration, repeat);
```

2. `tick`: 更新计时器的状态，传入时间间隔作为参数。通常在每个帧循环中调用。

```rust
timer.tick(delta_time);
```

3. `reset`: 重置计时器为初始状态，重新开始计时。

```rust
timer.reset();
```

4. `restart`: 重启计时器，即将计时器重置并开始计时。

```rust
timer.restart();
```

5. `pause` 和 `resume`: 暂停和恢复计时器的运行。

```rust
timer.pause();
timer.resume();
```

6. `finished`: 检查计时器是否已经完成，即达到了设定的延迟时间。

```rust
if timer.finished {
    // 计时器已完成，执行相应的逻辑
}
```

7. `just_finished`: 检查计时器是否刚刚完成，即上一帧还未完成，当前帧已经完成。

```rust
if timer.just_finished {
    // 计时器刚刚完成，执行相应的逻辑
}
```

8. `remaining_seconds`: 获取计时器剩余的秒数。

```rust
let remaining_seconds = timer.remaining_seconds();
```