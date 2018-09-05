---
title: Platformlar arası araçlarla NuGet paketi oluşturma
description: Bir NuGet paketi 'dotnet paketi' komutuyla oluşturmayı öğrenin.
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.technology: dotnet-cli
ms.openlocfilehash: 6be94c2e2cef443f69b2d6df7c2d490cb1fb629d
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43536027"
---
# <a name="how-to-create-a-nuget-package-with-cross-platform-tools"></a>Platformlar arası araçlarla NuGet paketi oluşturma

> [!NOTE]
> Aşağıda, UNIX kullanan komut satırı örnekleri gösterilmektedir.  `dotnet pack` Burada gösterilen şekilde, Windows üzerinde aynı şekilde çalışır.

.NET Core 1.0 için kitaplıkları NuGet paketleri olarak dağıtılmış beklenir.  Aslında nasıl tüm .NET standart kitaplıklarına dağıtılmış ve kullanıldığını belirmenize budur.  Bu en kolay ile yapılır `dotnet pack` komutu.

Az önce NuGet dağıtmak istediğiniz bir harika yeni kitaplık yazdığınız varsayalım.  Tam olarak bunu yapmak için platformlar arası araçlarla NuGet paketi oluşturabilirsiniz!  Aşağıdaki örnekte adlı bir kitaplığı varsayılır **SuperAwesomeLibrary** hangi hedeflerin `netstandard1.0`.

Geçişli bağımlılıkları varsa, diğer bir deyişle, başka bir projede bağımlı bir proje ile tüm çözümünüz için paketleri geri yüklediğinizden emin olmak ihtiyacınız `dotnet restore` NuGet paketini oluşturmadan önce komutu.  Bunu yapmazsanız sonuçlanır `dotnet pack` düzgün çalışmasını komutu.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]


Olduktan sonra paketleri geri yüklenir, burada kitaplık bulunduğu dizine gidin:

`$ cd src/SuperAwesomeLibrary`

Yalnızca tek bir komutu komut satırından sonra:
    
`$ dotnet pack`

`/bin/Debug` Klasör şimdi şuna benzeyebilir:

```
$ ls bin/Debug

netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

Bu ayıklanan özelliğine sahip olan bir paket oluşturur unutmayın.  NuGet paketi sürüm ikili dosyaları oluşturmak istiyorsanız, tüm yapmanız gereken eklemek `-c` / `--configuration` kullanın ve geçiş `release` bağımsız değişken olarak.

`$ dotnet pack --configuration release`

`/bin` Klasör artık sahip olacak bir `release` NuGet paketinizi yayın ikili dosyaları içeren klasör:

```
$ ls bin/release

netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

Ve artık bir NuGet paketi yayımlamak için gerekli dosyaları sahipsiniz!

## <a name="dont-confuse-dotnet-pack-with-dotnet-publish"></a>Karıştırmayın `dotnet pack` ile `dotnet publish`

Hiçbir noktada olduğuna dikkat edin önemlidir `dotnet publish` komut söz konusu.  `dotnet publish` Komutu tüm bağımlılıklarını dağıtılmış ve NuGet aracılığıyla kullanılan NuGet paketini oluşturmak için değil aynı paket - uygulama dağıtmak için.
