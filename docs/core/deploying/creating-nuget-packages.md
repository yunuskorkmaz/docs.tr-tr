---
title: .NET Core komut satırı arabirimi (CLı) araçlarıyla bir NuGet paketi oluşturma
description: "' DotNet Pack ' komutuyla bir NuGet paketi oluşturmayı öğrenin."
author: cartermp
ms.date: 06/20/2016
ms.technology: dotnet-cli
ms.custom: seodec18
ms.openlocfilehash: 2d876f921d079972e2a638788195aa69a2423c49
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771939"
---
# <a name="how-to-create-a-nuget-package-with-net-core-command-line-interface-cli-tools"></a>.NET Core komut satırı arabirimi (CLı) araçlarıyla bir NuGet paketi oluşturma

> [!NOTE]
> Aşağıda UNIX kullanan komut satırı örnekleri gösterilmektedir. Burada gösterildiği gibi `dotnet pack` komutu, Windows 'ta aynı şekilde çalışmaktadır.

.NET Standard ve .NET Core kitaplıklarının NuGet paketleri olarak dağıtılması beklenmektedir. Bu, tüm .NET Standard kitaplıklarının dağıtılma ve tüketilme olgusuna sahiptir. Bu, `dotnet pack` komutuyla kolayca yapılır.

NuGet üzerinden dağıtmak istediğiniz harika yeni bir kitaplığı yazdığınız hakkında düşünün. Tek yapmanız gereken, platformlar arası araçlarla bir NuGet paketi oluşturabilirsiniz! Aşağıdaki örnek, `netstandard1.0` hedefleyen **Superawesomelibrary** adlı bir kitaplık olduğunu varsayar.

Geçişli bağımlılıklarınız varsa; diğer bir deyişle, başka bir pakete bağımlı olan bir proje, bir NuGet paketi oluşturmadan önce `dotnet restore` komutuyla tüm çözümünüze yönelik paketleri geri yüklediğinizden emin olmanız gerekir. Bunun başarısız olması, `dotnet pack` komutunun düzgün şekilde çalışmamasını sağlar.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Paketlerin geri yüklenmesini sağlamaktan sonra, kitaplığın yaşadığı dizine gidebilirsiniz:

```console
cd src/SuperAwesomeLibrary
```

Bu durumda, komut satırından yalnızca tek bir komuttur:

```dotnetcli
dotnet pack
```

*/Bin/Debug* klasörünüz şimdi şöyle görünür:

```console
$ ls bin/Debug
netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

Bu, hata ayıklama yapabilen bir paket üretebileceğini unutmayın. Yayın ikilileriyle bir NuGet paketi oluşturmak istiyorsanız, tüm yapmanız gereken `--configuration` (veya `-c`) anahtarını ekleyip bağımsız değişken olarak `release` kullanmaktır.

```dotnetcli
dotnet pack --configuration release
```

*/Bin* klasörünüz artık sürüm Ikilileriyle NuGet paketinizi içeren bir *Sürüm* klasörüne sahip olur:

```console
$ ls bin/release
netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

Artık bir NuGet paketi yayımlamak için gerekli dosyalara sahipsiniz!

## <a name="dont-confuse-dotnet-pack-with-dotnet-publish"></a>@No__t_0 `dotnet publish` karıştırmayın

Dahil edilen `dotnet publish` komut olmadığı unutulmamalıdır. @No__t_0 komutu, aynı paket içindeki tüm bağımlılıklarıyla uygulama dağıtmaya yöneliktir; NuGet ile dağıtılacak ve tüketilecek bir NuGet paketi oluşturmak için değildir.

## <a name="see-also"></a>Ayrıca bkz.

- [Hızlı başlangıç: paket oluşturma ve yayımlama](/nuget/quickstart/create-and-publish-a-package-using-the-dotnet-cli)
