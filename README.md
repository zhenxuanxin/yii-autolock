# yii-autolock
自动为当前命令程序加锁，从而使其以单进程的方式运行。

## 使用方法
1. 下载源代码，放入 components 目录；
2. 使你的子类继承自该类即可。

> 注意：项目配置中，需要设置 import 来将 components 目录的类加载进来。

### 参考样例

`config/main.php` 中增加如下配置，并将 `AutoLockCommand.php` 放入 `components` 目录：
```php
'import' => [
    'application.components.*',
],
```

编写需要应用自动加锁机制的业务代码：
```php
<?php

class BusinessLogicCommand extends AutoLockCommand
{
    public function actionSingleRun()
    {
        // 业务代码
    }
}
```

执行命令的时候，可见 `runtime` 目录下会生成以命令名（command + action）作为文件名的锁文件。
