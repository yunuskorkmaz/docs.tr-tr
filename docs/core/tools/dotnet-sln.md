---
title: DotNet sln komutu
description: Dotnet sln komutu eklemek, kaldırmak ve bir çözüm dosyası projelerinde listelemek için uygun bir seçenek sağlar.
ms.date: 06/13/2018
ms.openlocfilehash: a88e22c68f639f2a42e59f9a271e431f04e24a2b
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53169150"
---
# <a name="dotnet-sln"></a>DotNet sln

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Ad

`dotnet sln` -.NET Core çözüm dosyasını değiştirir.

## <a name="synopsis"></a>Özeti

```
dotnet sln [<SOLUTION_NAME>] add <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] add <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] remove <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] remove <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] list
dotnet sln [-h|--help]
```

## <a name="description"></a>Açıklama

`dotnet sln` Komutu eklemek, kaldırmak ve bir çözüm dosyası projelerinde listelemek için kolay bir yol sağlar.

Kullanılacak `dotnet sln` komutu, çözüm dosyası zaten var olmalıdır. Oluşturmak ihtiyacınız varsa [yeni dotnet](dotnet-new.md) komutu gibi aşağıdaki örnekte:

```
dotnet new sln
```

## <a name="commands"></a>Komutlar

`add <PROJECT> ...`

`add <GLOBBING_PATTERN>`

Bir proje ya da birden çok proje, çözüm dosyasına eklenir. [Glob desenlerinin](https://en.wikipedia.org/wiki/Glob_(programming)) UNIX/Linux tabanlı terminaller üzerinde desteklenir.

`remove <PROJECT> ...`

`remove <GLOBBING_PATTERN>`

Bir proje ya da birden çok proje çözümü dosyasından kaldırır. [Glob desenlerinin](https://en.wikipedia.org/wiki/Glob_(programming)) UNIX/Linux tabanlı terminaller üzerinde desteklenir.

`list`

Bir çözüm dosyasındaki tüm projeleri listeler.

## <a name="arguments"></a>Arguments

`SOLUTION_NAME`

Çözüm dosyası kullanın. Belirtilmezse, komut için geçerli dizinde arar. Dizinde birden fazla çözüm dosyası varsa, biri belirtilmelidir.

## <a name="options"></a>Seçenekler

`-h|--help`

Komut için kısa bir Yardım yazdırır.

## <a name="examples"></a>Örnekler

Bir C# projesi çözüme ekleyin:

`dotnet sln todo.sln add todo-app/todo-app.csproj`

Bir C# projesi bir çözümden Kaldır:

`dotnet sln todo.sln remove todo-app/todo-app.csproj`

Birden çok C# projeleri çözüme ekleyin:

`dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj`

Birden çok C# projelerini bir çözümden Kaldır:

`dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj`

Birden çok C# projelerinde, Glob deseni kullanılarak çözüm ekleyin:

`dotnet sln todo.sln add **/*.csproj`

Birden çok C# projelerinde, Glob deseni kullanılarak bir çözümden kaldırmak:

`dotnet sln todo.sln remove **/*.csproj`

> [!NOTE]
> Genelleştirme CLI özelliği ancak yerine bir komut kabuğu özelliği değil. Dosyalar başarılı bir şekilde genişletmek için genelleştirme destekleyen bir kabuk kullanmanız gerekir. Genelleştirme hakkında daha fazla bilgi için bkz: [Wikipedia](https://en.wikipedia.org/wiki/Glob_(programming)).
