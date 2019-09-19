---
title: DotNet sln komutu
description: DotNet-sln komutu bir çözüm dosyasındaki projeleri eklemek, kaldırmak ve listelemek için kullanışlı bir seçenek sağlar.
ms.date: 06/13/2018
ms.openlocfilehash: 84508aaefff61b31e2965576ebc2daaae7331951
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117586"
---
# <a name="dotnet-sln"></a>dotnet sln

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Ad

`dotnet sln`-Bir .NET Core çözüm dosyasını değiştirir.

## <a name="synopsis"></a>Özeti

```dotnetcli
dotnet sln [<SOLUTION_NAME>] add <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] add <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] remove <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] remove <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] list
dotnet sln [-h|--help]
```

## <a name="description"></a>Açıklama

`dotnet sln` Komut, bir çözüm dosyasındaki projeleri eklemek, kaldırmak ve listelemek için kullanışlı bir yol sağlar.

`dotnet sln` Komutunu kullanmak için, çözüm dosyası zaten var olmalıdır. Bir tane oluşturmanız gerekiyorsa, aşağıdaki örnekte olduğu gibi [DotNet New](dotnet-new.md) komutunu kullanın:

```dotnetcli
dotnet new sln
```

## <a name="commands"></a>Komutlar

`add <PROJECT> ...`

`add <GLOBBING_PATTERN>`

Çözüm dosyasına bir proje veya birden çok proje ekler. [Glob desenleri](https://en.wikipedia.org/wiki/Glob_(programming)) UNIX/Linux tabanlı terminallerde desteklenir.

`remove <PROJECT> ...`

`remove <GLOBBING_PATTERN>`

Çözüm dosyasından bir projeyi veya birden çok projeyi kaldırır. [Glob desenleri](https://en.wikipedia.org/wiki/Glob_(programming)) UNIX/Linux tabanlı terminallerde desteklenir.

`list`

Bir çözüm dosyasındaki tüm projeleri listeler.

## <a name="arguments"></a>Arguments

`SOLUTION_NAME`

Kullanılacak çözüm dosyası. Belirtilmemişse, komut geçerli dizinde bir arama yapar. Dizinde birden çok çözüm dosyası varsa, birinin belirtilmesi gerekir.

## <a name="options"></a>Seçenekler

`-h|--help`

Komut için kısa bir yardım yazdırır.

## <a name="examples"></a>Örnekler

Bir çözüme C# proje ekleme:

`dotnet sln todo.sln add todo-app/todo-app.csproj`

Bir C# projeyi çözümden kaldırma:

`dotnet sln todo.sln remove todo-app/todo-app.csproj`

Bir çözüme C# birden çok proje ekleyin:

`dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj`

Bir çözümden C# birden çok proje kaldırma:

`dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj`

Bir glob C# deseninin kullanıldığı bir çözüme birden fazla proje ekleyin:

`dotnet sln todo.sln add **/*.csproj`

Bir glob C# deseninin kullanıldığı bir çözümden birden fazla projeyi kaldırma:

`dotnet sln todo.sln remove **/*.csproj`

> [!NOTE]
> Glob, bir CLı özelliği değil, bir komut kabuğu özelliği değil. Dosyaları başarılı bir şekilde genişletmek için glob destekleyen bir kabuk kullanmanız gerekir. Glob hakkında daha fazla bilgi için bkz. [Vikipedi](https://en.wikipedia.org/wiki/Glob_(programming)).
