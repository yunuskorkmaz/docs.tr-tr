---
title: DotNet sln command - .NET Core CLI
description: "Dotnet sln komutu eklemek, kaldırmak ve bir çözüm dosyasını projelerinde listelemek için uygun bir seçenek sağlar."
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: deb66ff52074630616c7be47f1a9751246db501d
ms.sourcegitcommit: 70dcc89737127e4d5f20500242409b687e51b07e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/11/2018
---
# <a name="dotnet-sln"></a>DotNet sln

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Ad

`dotnet sln`-Bir .NET Core çözüm dosyasını değiştirir.

## <a name="synopsis"></a>Özet

```
dotnet sln [<SOLUTION_NAME>] add <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] add <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] remove <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] remove <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] list
dotnet sln [-h|--help]
```

## <a name="description"></a>Açıklama

`dotnet sln` Komut eklemek, kaldırmak ve bir çözüm dosyasını projelerinde listelemek için kullanışlı bir yol sağlar.

## <a name="commands"></a>Komutlar

`add <PROJECT> ...`

`add <GLOBBING_PATTERN>`

Bir proje veya birden çok proje çözümü dosyasına ekler. [Genelleme desenleri](https://en.wikipedia.org/wiki/Glob_(programming)) UNIX/Linux tabanlı Terminal üzerinde desteklenir.

`remove <PROJECT> ...`

`remove <GLOBBING_PATTERN>`

Bir proje veya birden çok proje çözümü dosyasından kaldırır. [Genelleme desenleri](https://en.wikipedia.org/wiki/Glob_(programming)) UNIX/Linux tabanlı Terminal üzerinde desteklenir.

`list`

Bir çözüm dosyasındaki tüm projeleri listeler.

## <a name="arguments"></a>Arguments

`SOLUTION_NAME`

Çözüm dosyası kullanın. Belirtilmezse, komut için geçerli dizin arar. Dizinde birden çok çözüm dosyalarını varsa belirtilmelidir.

## <a name="options"></a>Seçenekler

`-h|--help`

Komutu için kısa bir Yardım yazdırır.

## <a name="examples"></a>Örnekler

Bir C# projesi bir çözüme ekleyin:

`dotnet sln todo.sln add todo-app/todo-app.csproj`

Bir C# projesi bir çözümden kaldırın:

`dotnet sln todo.sln remove todo-app/todo-app.csproj`

Birden çok C# projeleri bir çözüme ekleyin:

`dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj`

Birden çok C# projeleri bir çözümden kaldırın:

`dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj`

Birden çok C# projeleri genelleme desen kullanan bir çözüme ekleyin:

`dotnet sln todo.sln add **/*.csproj`

Birden çok C# projeleri genelleme desen kullanan bir çözüm kaldırın:

`dotnet sln todo.sln remove **/*.csproj`
