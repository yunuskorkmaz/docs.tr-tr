---
title: .NET Core komut satırı arabirimi (CLı) araçlarıyla bir NuGet paketi oluşturma
description: "' DotNet Pack ' komutuyla bir NuGet paketi oluşturmayı öğrenin."
author: cartermp
ms.date: 06/20/2016
ms.technology: dotnet-cli
ms.custom: seodec18
ms.openlocfilehash: d36a6ee7d524933577928daa9993fba8ce62f6c7
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71116702"
---
# <a name="how-to-create-a-nuget-package-with-net-core-command-line-interface-cli-tools"></a>.NET Core komut satırı arabirimi (CLı) araçlarıyla bir NuGet paketi oluşturma

> [!NOTE]
> Aşağıda UNIX kullanan komut satırı örnekleri gösterilmektedir. Burada `dotnet pack` gösterilen komut, Windows 'ta aynı şekilde çalışmaktadır.

.NET Standard ve .NET Core kitaplıklarının NuGet paketleri olarak dağıtılması beklenmektedir. Bu, tüm .NET Standard kitaplıklarının dağıtılma ve tüketilme olgusuna sahiptir. Bu, `dotnet pack` komutla en kolay şekilde yapılır.

NuGet üzerinden dağıtmak istediğiniz harika yeni bir kitaplığı yazdığınız hakkında düşünün. Tek yapmanız gereken, platformlar arası araçlarla bir NuGet paketi oluşturabilirsiniz! Aşağıdaki örnek, ' i hedefleyen `netstandard1.0` **Superawesomelibrary** adlı bir kitaplık olduğunu varsayar.

Geçişli bağımlılıklarınız varsa; diğer bir deyişle, başka bir pakete bağımlı olan bir proje, bir NuGet paketi oluşturmadan önce `dotnet restore` komutuyla tüm çözümünüze yönelik paketleri geri yüklediğinizden emin olmanız gerekir. Bunun başarısız olmasının nedeni `dotnet pack` komutun düzgün şekilde çalışmamasını sağlar.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Paketlerin geri yüklenmesini sağlamaktan sonra, kitaplığın yaşadığı dizine gidebilirsiniz:

```console
cd src/SuperAwesomeLibrary
```

Bu durumda, komut satırından yalnızca tek bir komuttur:

```dotnetcli
dotnet pack
```

`/bin/Debug` Klasörünüz şimdi şöyle görünür:

```console
$ ls bin/Debug

netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

Bu, hata ayıklama yapabilen bir paket üretebileceğini unutmayın. Yayın ikilileriyle bir NuGet paketi oluşturmak istiyorsanız, tüm yapmanız gereken, `--configuration` (veya `-c`) anahtarını ve bağımsız değişkeni olarak kullanmayı `release` eklemektir.

```dotnetcli
dotnet pack --configuration release
```

Klasörünüz artık sürüm ikilileriyle NuGet `release` paketinizi içeren bir klasöre sahip olur: `/bin`

```console
$ ls bin/release

netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

Artık bir NuGet paketi yayımlamak için gerekli dosyalara sahipsiniz!

## <a name="dont-confuse-dotnet-pack-with-dotnet-publish"></a>İle karıştırmayın `dotnet pack``dotnet publish`

Hiçbir noktadan söz konusu `dotnet publish` komutun olmadığı unutulmamalıdır. Bu `dotnet publish` komut, aynı paketteki tüm bağımlılıklarıyla uygulama dağıtmaya yöneliktir--NuGet paketini, NuGet aracılığıyla dağıtılacak ve tüketilecek şekilde bir NuGet paketi oluşturmak için değil.

## <a name="see-also"></a>Ayrıca bkz.

- [Hızlı Başlangıç: Paket oluşturma ve yayımlama](/nuget/quickstart/create-and-publish-a-package-using-the-dotnet-cli)
