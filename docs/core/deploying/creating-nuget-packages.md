---
title: .NET Core CLI ile NuGet paketi oluşturun
description: "'dotnet paketi' komutuyla bir NuGet paketi oluşturmayı öğrenin."
author: cartermp
ms.date: 06/20/2016
ms.technology: dotnet-cli
ms.openlocfilehash: 3f8e75a501cfc48e1c416f71e91290cab1a4ffae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76920913"
---
# <a name="how-to-create-a-nuget-package-with-the-net-core-cli"></a>.NET Core CLI ile NuGet paketi nasıl oluşturulur?

> [!NOTE]
> Aşağıdaki Unix kullanarak komut satırı örnekleri gösterir. Burada `dotnet pack` gösterildiği gibi komut Windows'da da aynı şekilde çalışır.

.NET Standard ve .NET Core kitaplıklarının NuGet paketleri olarak dağıtılması beklenmektedir. Bu aslında tüm .NET Standart kitaplıklarının nasıl dağıtıldığı ve tüketildiğini. Bu en kolay `dotnet pack` komutu ile yapılır.

NuGet üzerinden dağıtmak istediğiniz harika bir yeni kütüphane yazdığınızı düşünün. Bunu tam olarak yapmak için çapraz platform araçları ile bir NuGet paketi oluşturabilirsiniz! Aşağıdaki örnek, **SuperAwesomeLibrary** adlı bir `netstandard1.0`kitaplığı hedefler varsayar.

Geçişli bağımlılıklarınız varsa, yani başka bir pakete dayanan bir projevarsa, bir NuGet `dotnet restore` paketi oluşturmadan önce komutla tüm çözüm için paketleri geri yüklediğinden emin olun. Aksi takdirde komutun `dotnet pack` düzgün çalışmaması durumunda.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Paketlerin geri yüklendiğinden emin olduktan sonra, kitaplığın yaşadığı dizine gidebilirsiniz:

```console
cd src/SuperAwesomeLibrary
```

O zaman komut satırından sadece tek bir komut:

```dotnetcli
dotnet pack
```

*/bin/Hata Ayıklama* klasörünüz şimdi şu şekilde görünecektir:

```console
$ ls bin/Debug
netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

Bu debugged olma yeteneğine sahip bir paket üretir. Sürüm ikilileri içeren bir NuGet paketi oluşturmak istiyorsanız, tek yapmanız `--configuration` gereken `-c`(veya) `release` anahtarını eklemek ve bağımsız değişken olarak kullanmaktır.

```dotnetcli
dotnet pack --configuration release
```

*/bin* klasörünüz artık Sürüm ikilileriyle birlikte NuGet paketinizi içeren bir *sürüm* klasörüne sahip olacaktır:

```console
$ ls bin/release
netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

Ve şimdi bir NuGet paketi yayınlamak için gerekli dosyaları var!

## <a name="dont-confuse-dotnet-pack-with-dotnet-publish"></a>Ile karıştırmayın `dotnet pack``dotnet publish`

Hiçbir noktada ilgili `dotnet publish` komut olduğunu unutmayın. Komut, `dotnet publish` tüm bağımlılıkları olan uygulamaları aynı pakette dağıtmak içindir -- NuGet üzerinden dağıtılacak ve tüketilecek bir NuGet paketi oluşturmak için değil.

## <a name="see-also"></a>Ayrıca bkz.

- [Quickstart: Bir paket oluşturma ve yayımlama](/nuget/quickstart/create-and-publish-a-package-using-the-dotnet-cli)
