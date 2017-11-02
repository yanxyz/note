---
permalink: /powershell/lang/types/
---

# PowerShell Types

PowerShell 建立在 .Net framework 上，有许多 types。不同于 C#，PowerShell

- 不要求声明类型，不过可以声明类型。
- 自动转换类型。

PowerShell 常见的类型：null, booleans, integers, strings, arrays, hash tables, objects（比如 processes, services, event logs, computers）。

## GetType

```powershell
(3).GetType().FullName  # System.Int32
3 | Get-Member
```

## Type Operators

```powershell
help about_Type_Operators
```

`-is`, `-isNot` 判断对象是否为指定 .NET type 的实例。
以 `[type]` 或 `"type"` 的形式指定 type。type 可以省略 `System`

```powershell
3 -is [Float]  # False
3 -is "Int"    # True
(get-process PowerShell)[0] -is [System.Diagnostics.Process] # True
```

`-as` 尝试将对象转为指定 .NET type，若成功则返回转换后的对象，若失败什么也不返回，并不会抛出错误。

```powershell
"12/31/07" -is [DateTime]
# False

"12/31/07" -as [DateTime]
# 是否成功取决于当前 CultureInfo
```

## cast

PowerShell 自动转换类型

对于表达式，取决于左操作数的类型。

```powershell
$true -eq 2  # True
2 -eq $true  # False
[int]$true   # 1
```