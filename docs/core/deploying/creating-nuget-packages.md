---
title: "Çapraz Platform araçları ile bir NuGet paketi oluşturma"
description: "Bir NuGet paketi 'dotnet pack' komutuyla oluşturmayı öğrenin."
keywords: .NET, .NET core NuGet
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 2f0415c1-110b-433d-87c1-ae3d543a8844
ms.openlocfilehash: a5738a4f3755a959660db4be683677673af61ef9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-a-nuget-package-with-cross-platform-tools"></a>Çapraz Platform araçları ile bir NuGet paketi oluşturma

> [!NOTE]
> UNIX kullanarak komut satırı örnekleri gösterilmektedir.  `dotnet pack` Aşağıda gösterildiği gibi komutu Windows'da aynı şekilde çalışır.

.NET Core 1.0 için kitaplıkları NuGet paketleri olarak dağıtılmış beklenir.  Aslında nasıl tüm .NET standart kitaplıkları dağıtılmış tüketilen ve budur.  Bu en kolay gerçekleştirilir `dotnet pack` komutu.

Yalnızca NuGet dağıtmak istediğiniz bir harika yeni kitaplık yazdığınız düşünün.  Bir NuGet paketi ile tam olarak bunu yapmak için platformu araçları çapraz oluşturabilirsiniz!  Aşağıdaki örnek adlı bir kitaplık varsayar **SuperAwesomeLibrary** hangi hedefleri `netstandard1.0`.

Geçişli bağımlılıkları varsa; diğer bir deyişle, başka bir projeye bağlıdır bir proje çözümünüzle birlikte paketlerini geri yüklemek emin olmak ihtiyacınız vardır `dotnet restore` bir NuGet paketi oluşturmadan önce komutu.  Bunu yapmazsanız neden olur `dotnet pack` düzgün çalışmasını komutu.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]


Olduktan paketler geri yüklenir, bir kitaplık nerede yaşıyor dizinine gidin:

`$ cd src/SuperAwesomeLibrary`

Yalnızca tek bir komut komut satırından sonra:
    
`$ dotnet pack`

`/bin/Debug` Klasörü şimdi şuna benzeyebilir:

```
$ ls bin/Debug

netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

Bu hata ayıklaması işleyebilen bir paket oluşturur unutmayın.  Bir NuGet paketi yayın ikililerini oluşturmak istiyorsanız, tüm yapmanız gereken ekleyin `-c` / `--configuration` geçin ve kullanmak `release` bağımsız değişkeni olarak.

`$ dotnet pack --configuration release`

`/bin` Klasörü şimdi sahip olacak bir `release` NuGet paketinizle yayın ikili dosyaları içeren klasör:

```
$ ls bin/release

netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

Ve şimdi bir NuGet paketi yayımlamak için gerekli dosyaları!

## <a name="dont-confuse-dotnet-pack-with-dotnet-publish"></a>Karıştırmayın `dotnet pack` ile`dotnet publish`

Herhangi bir noktada olduğunu dikkate almak önemlidir `dotnet publish` komut söz konusu.  `dotnet publish` Komuttur dağıtılmış ve NuGet üzerinden tüketilen bir NuGet paketi oluşturma değil aynı gruptaki -, bağımlılıklarının tümü ile uygulamaları dağıtmak için.
