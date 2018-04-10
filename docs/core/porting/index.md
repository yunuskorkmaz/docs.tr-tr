---
title: .NET Core için .NET Framework'bağlantı noktası oluşturma
description: Taşıma işlemini anlamanıza ve .NET Core .NET Framework projeye bağlantı noktası oluşturma, faydalı bulabileceğiniz araçları keşfedin.
keywords: .NET, .NET core
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 00d00d38-99af-44f4-a75f-defcd9729dc5
ms.workload:
- dotnetcore
ms.openlocfilehash: 3413b73c2a0a3c3ebf49b0b3ec81d00c6558d9a8
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="porting-to-net-core-from-net-framework"></a>.NET Core için .NET Framework'bağlantı noktası oluşturma

.NET Framework üzerinde çalışan kodu ekranınız varsa, .NET Core 1.0 kodunuz çalışan ilgilenebilirsiniz.  Bu makalede taşıma işlemine genel bakış ve .NET Core için bağlantı noktası oluşturma, faydalı bulabileceğiniz araçların listesi yer almaktadır.

## <a name="overview-of-the-porting-process"></a>Taşıma işlemine genel bakış

Taşıma için önerilen işlemi aşağıdaki adımları dizi izler.  İşlemin bu parçaların her birini daha fazla makalelerinde daha ayrıntılı değinilmiştir.

1. Tanımlamak ve, üçüncü taraf bağımlılıkları için hesap.

   Bu, hangi üçüncü taraf bağımlılıkları olan, bağımlı nasıl anlama gerektireceğini bunları yoksa ayrıca .NET Core ve adımları çalıştırırsanız, görmek için uygulayabileceğiniz nasıl.
   
2. Hedef .NET Framework 4.6.2 bağlantı noktasına istediğiniz tüm projeleri yeniden hedefleyin.

   Bu, .NET Core belirli bir API'yi burada destekleyemez durumlarda .NET Framework özgü hedefler için API alternatifleri kullanabilmesini sağlar.
   
3. Kullanım [API taşınabilirlik Çözümleyicisi aracını](https://github.com/Microsoft/dotnet-apiport/) derlemeleriniz çözümlemek ve onun sonuçlarına dayalı bağlantı noktasına yönelik bir plan geliştirmek için.

   API taşınabilirlik Çözümleyicisi aracını derlenmiş derlemeleriniz çözümleyebilir ve üst düzey taşınabilirlik Özet gösteren bir rapor ve .NET Core üzerinde kullanılabilir değil, kullanmakta olduğunuz her API bir dökümünü oluşturur.  Bu rapor analizini yanında kullanabilirsiniz, nasıl üzerinden kodunuzu bağlantı için bir plan geliştirmek için codebase.
   
4. Testleri kodunuzu bağlantı noktası.

   .NET Core taşıma temelinizde için büyük değişiklik olduğundan, yüksek oranda üzerinden kod bağlantı noktası olarak testleri çalıştırabilmeniz için bağlantı noktası kurulmuş testleri almak için önerilir.  Mstest'i, xUnit ve NUnit .NET Core 1.0 bugün destekler.
   
6. Taşıma için planınızı yürütme!

## <a name="tools-to-help"></a>Yardımcı olacak araçlar

Yararlı bulabilirsiniz araçları kısa bir listesi aşağıda verilmiştir:

* NuGet - [Nuget istemci](https://dist.nuget.org/index.html) veya [NuGet paketi Gezgini](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer), Microsoft'un .NET uygulamaları için Paket Yöneticisi.
* API taşınabilirlik Çözümleyicisi - [komut satırı aracı](https://github.com/Microsoft/dotnet-apiport/releases) veya [Visual Studio Uzantısı](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b), nasıl taşınabilir kodunuzu .NET Framework ve .NET Core arasında sahip olduğu bir rapor oluşturabilirsiniz bir araç zinciri bir sorunları dökümünü derleme tarafından derleme.  Bkz: [işlemi yardımcı olmak için araç](https://github.com/Microsoft/dotnet-apiport/blob/master/docs/HowTo/) daha fazla bilgi için.
* Paket arama - A ters [yararlı web hizmeti](https://packagesearch.azurewebsites.net) bir türünü aramak ve bu türü içeren paketler bulmak sağlar.

## <a name="next-steps"></a>Sonraki adımlar

[Üçüncü taraf bağımlılıkları çözümleniyor.](third-party-deps.md)
   
