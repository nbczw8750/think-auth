# 功能级权限
The ThinkPHP5 Auth Package

## 安装
> composer require nbczwphp/think-auth

## 权限认证类
功能特性：

1. 是对规则进行认证，不是对节点进行认证。用户可以把节点当作规则名称实现对节点进行认证。
   $auth=new Auth();  $auth->check('规则名称','用户id')
2. 可以同时对多条规则进行认证，并设置多条规则的关系（or或者and）
   $auth=new Auth();  $auth->check('规则1,规则2','用户id','and')
   第三个参数为and时表示，用户需要同时具有规则1和规则2的权限。 当第三个参数为or时，表示用户值需要具备其中一个条件即可。默认为or
3. 一个用户可以属于多个用户组(think_auth_group_access表 定义了用户所属用户组)。我们需要设置每个用户组拥有哪些规则(think_auth_group 定义了用户组权限)

4. 支持规则表达式。
   在think_auth_rule 表中定义一条规则时，如果type为1， condition字段就可以定义规则表达式。 如定义{score}>5  and {score}<100  表示用户的分数在5-100之间时这条规则才会通过。

## 配置

项目配置键为`auth_config`

```
'auth_on'           => true,                      // 认证开关
'auth_type'         => 1,                         // 认证方式，1为实时认证；2为登录认证。
'auth_group'        => '__AUTH_GROUP__',        // 用户组数据表名
'auth_group_access' => '__AUTH_GROUP_ACCESS__', // 用户-用户组关系表
'auth_rule'         => '__AUTH_RULE__',         // 权限规则表
'auth_user'         => '__USER__'             // 用户信息表
```
