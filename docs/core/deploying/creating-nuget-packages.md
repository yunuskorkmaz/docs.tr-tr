---
title: .NET Core CLI bir NuGet paketi oluşturma
description: "' DotNet Pack ' komutuyla bir NuGet paketi oluşturmayı öğrenin."
author: cartermp
ms.date: 06/20/2016
ms.technology: dotnet-cli
ms.openlocfilehash: ddc19faa7547637036686146f8600f40713541a8
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740868"
---
# <a name="how-to-create-a-nuget-package-with-net-core-command-line-interface-cli-tools"></a>.NET Core komut satırı arabirimi (CLı) araçlarıyla bir NuGet paketi oluşturma

> [!NOTE]
> Aşağıda UNIX kullanan komut satırı örnekleri gösterilmektedir. Burada gösterildiği gibi `dotnet pack` komutu, Windows 'ta aynı şekilde çalışmaktadır.

.NET Standard ve .NET Core kitaplıklarının NuGet paketleri olarak dağıtılması beklenmektedir. Bu, tüm .NET Standard kitaplıklarının dağıtılma ve tüketilme olgusuna sahiptir. Bu, `dotnet pack` komutuyla kolayca yapılır.

NuGet üzerinden dağıtmak istediğiniz harika yeni bir kitaplığı yazdığınız hakkında düşünün. Tek yapmanız gereken, platformlar arası araçlarla bir NuGet paketi oluşturabilirsiniz! Aşağıdaki örnek, `netstandard1.0`hedefleyen **Superawesomelibrary** adlı bir kitaplık olduğunu varsayar.

Başka bir pakete bağlı bir proje olan geçişli bağımlılıklarınız varsa, bir NuGet paketi oluşturmadan önce `dotnet restore` komutuyla tüm çözüme yönelik paketleri geri yüklediğinizden emin olun. Bunun başarısız olması, `dotnet pack` komutunun düzgün şekilde çalışmamasını sağlar.

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

Bu, hata ayıklama yapabilen bir paket oluşturur. Yayın ikilileriyle bir NuGet paketi oluşturmak istiyorsanız, tüm yapmanız gereken `--configuration` (veya `-c`) anahtarını ekleyip bağımsız değişken olarak `release` kullanmaktır.

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

## <a name="dont-confuse-dotnet-pack-with-dotnet-publish"></a>`dotnet pack` `dotnet publish` karıştırmayın

Dahil edilen `dotnet publish` komut olmadığı unutulmamalıdır. `dotnet publish` komutu, aynı paket içindeki tüm bağımlılıklarıyla uygulama dağıtmaya yöneliktir; NuGet ile dağıtılacak ve tüketilecek bir NuGet paketi oluşturmak için değildir.

## <a name="see-also"></a>Ayrıca bkz.

- [Hızlı başlangıç: paket oluşturma ve yayımlama](/nuget/quickstart/create-and-publish-a-package-using-the-dotnet-cli)
