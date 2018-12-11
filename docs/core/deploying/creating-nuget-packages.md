---
title: .NET Core komut satırı arabirimi (CLI) araçlarını bir NuGet paketi oluşturma
description: Bir NuGet paketi 'dotnet paketi' komutuyla oluşturmayı öğrenin.
author: cartermp
ms.date: 06/20/2016
ms.technology: dotnet-cli
ms.custom: seodec18
ms.openlocfilehash: 14e3dc265991634b4ef4814fb149f0aaebbcfab6
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53170060"
---
# <a name="how-to-create-a-nuget-package-with-net-core-command-line-interface-cli-tools"></a>.NET Core komut satırı arabirimi (CLI) araçlarını bir NuGet paketi oluşturma

> [!NOTE]
> Aşağıda, UNIX kullanan komut satırı örnekleri gösterilmektedir. `dotnet pack` Burada gösterilen şekilde, Windows üzerinde aynı şekilde çalışır.

.NET standard ve .NET Core kitaplıkları, NuGet paketleri olarak dağıtılmış beklenir. Aslında nasıl tüm .NET standart kitaplıklarına dağıtılmış ve kullanıldığını belirmenize budur. Bu en kolay ile yapılır `dotnet pack` komutu.

Az önce NuGet dağıtmak istediğiniz bir harika yeni kitaplık yazdığınız varsayalım. Tam olarak bunu yapmak için platformlar arası araçlarla NuGet paketi oluşturabilirsiniz! Aşağıdaki örnekte adlı bir kitaplığı varsayılır **SuperAwesomeLibrary** hangi hedeflerin `netstandard1.0`.

Geçişli bağımlılıkları varsa, diğer bir deyişle, başka bir pakete bağımlı bir proje ile tüm çözümünüz için paketleri geri yüklediğinizden emin olmak ihtiyacınız `dotnet restore` NuGet paketini oluşturmadan önce komutu. Bunu yapmazsanız sonuçlanır `dotnet pack` düzgün çalışmasını komutu.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Olduktan sonra paketleri geri yüklenir, burada kitaplık bulunduğu dizine gidin:

```console
$ cd src/SuperAwesomeLibrary`
```

Yalnızca tek bir komutu komut satırından sonra:

```console
$ dotnet pack
```

`/bin/Debug` Klasör şimdi şuna benzeyebilir:

```console
$ ls bin/Debug

netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

Bu ayıklanan özelliğine sahip olan bir paket oluşturur unutmayın. NuGet paketi sürüm ikili dosyaları oluşturmak istiyorsanız, tüm yapmanız gereken eklemek `--configuration` (veya `-c`) kullanın ve geçiş `release` bağımsız değişken olarak.

```console
$ dotnet pack --configuration release
```

`/bin` Klasör artık sahip olacak bir `release` NuGet paketinizi yayın ikili dosyaları içeren klasör:

```console
$ ls bin/release

netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

Ve artık bir NuGet paketi yayımlamak için gerekli dosyaları sahipsiniz!

## <a name="dont-confuse-dotnet-pack-with-dotnet-publish"></a>Karıştırmayın `dotnet pack` ile `dotnet publish`

Hiçbir noktada olduğuna dikkat edin önemlidir `dotnet publish` komut söz konusu. `dotnet publish` Komutu tüm bağımlılıklarını dağıtılmış ve NuGet aracılığıyla kullanılan NuGet paketini oluşturmak için değil aynı paket--uygulama dağıtmak için.

## <a name="see-also"></a>Ayrıca bkz.

- [Hızlı Başlangıç: Bir paketi oluşturma ve yayımlama](/nuget/quickstart/create-and-publish-a-package-using-the-dotnet-cli)