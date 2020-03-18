---
title: Docker kapsayıcıları için ne zaman .NET Framework seçilmelidir?
description: .NET Microservices Mimari Containerized .NET Uygulamaları için | Docker kapsayıcıları için .NET Framework ne zaman seçilir?
ms.date: 01/30/2020
ms.openlocfilehash: dfb1e8883fc9c3d9235672bc2885858bfb64afa5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77501967"
---
# <a name="when-to-choose-net-framework-for-docker-containers"></a>Docker kapsayıcıları için ne zaman .NET Framework seçilmelidir?

.NET Core yeni uygulamalar ve uygulama kalıpları için önemli avantajlar sunarken, .NET Framework varolan birçok senaryo için iyi bir seçim olmaya devam edecektir.

## <a name="migrating-existing-applications-directly-to-a-windows-server-container"></a>Varolan uygulamaları doğrudan bir Windows Server kapsayıcısına geçirme

Mikro hizmetler oluşturmasanız bile, docker kapsayıcılarını dağıtımı basitleştirmek için kullanmak isteyebilirsiniz. Örneğin, DevOps iş akışınızı Docker ile iyileştirmek isteyebilirsiniz-kapsayıcılar size daha iyi yalıtılmış test ortamları sağlayabilir ve üretim ortamına taşındığınızda eksik bağımlılıklardan kaynaklanan dağıtım sorunlarını da ortadan kaldırabilir. Bu gibi durumlarda, yekpare bir uygulama dağıtıyor olsanız bile, geçerli .NET Framework uygulamalarınız için Docker ve Windows Kapsayıcıları kullanmak mantıklıdır.

Bu senaryonun çoğu durumunda, varolan uygulamalarınızı .NET Core'a geçirmeniz gerekmez; geleneksel .NET Framework içeren Docker kapsayıcılarını kullanabilirsiniz. Ancak, ASP.NET Core'da yeni bir hizmet yazmak gibi varolan bir uygulamayı genişletirken .NET Core'u kullanmanız önerilir.

## <a name="using-third-party-net-libraries-or-nuget-packages-not-available-for-net-core"></a>Üçüncü taraf .NET kitaplıklarını veya .NET Core için kullanılamayan NuGet paketlerini kullanma

Üçüncü taraf kitaplıkları, [.NET](../../../standard/net-standard.md)Core da dahil olmak üzere tüm .NET tatlarında kod paylaşımını sağlayan .NET Standard'ı hızla benimsiyor. .NET Standart 2.0 ve sonraki ile, farklı çerçeveler arasında API yüzey uyumluluğu önemli ölçüde daha büyük hale gelmiştir. Dahası, .NET Core 2.x ve yeni uygulamalar da doğrudan mevcut .NET Framework kitaplıklarına başvuruyapabilir (bkz. [.NET Framework 4.6.1 destekleyen .NET Standart 2.0).](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#net-framework-461-supporting-net-standard-20)

Ayrıca, [Windows Uyumluluk Paketi,](../../../core/porting/windows-compat-pack.md) Windows'da .NET Standart 2.0 için kullanılabilir API yüzeyini genişletir. Bu paket, varolan kodun çoğunun Windows'da çalıştırılabilmek için çok az değişiklik le veya hiç değişiklik olmadan .NET Standard 2.x'e yeniden derlemesine olanak tanır.

Ancak, .NET Standart 2.0 ve .NET Core 2.1'den bu yana bu olağanüstü ilerlemeyle bile, bazı NuGet paketlerinin çalıştırmak için Windows'a ihtiyaç duyduğu ve .NET Core'u desteklemeyebileceği durumlar olabilir. Bu paketler uygulamanız için kritik se, Windows Kapsayıcılar üzerinde .NET Framework kullanmanız gerekir.

## <a name="using-net-technologies-not-available-for-net-core"></a>.NET Core için kullanılamıyor .NET teknolojilerini kullanma

Bazı .NET Framework teknolojileri .NET Core'un geçerli sürümünde kullanılamaz (bu yazıitibariyle sürüm 3.1). Bazıları daha sonraki sürümlerde kullanılabilir hale gelebilir, ancak diğerleri .NET Core tarafından hedeflenen yeni uygulama desenlerine uymaz ve hiçbir zaman kullanılamayabilir.

Aşağıdaki liste,.NET Core 3.1'de bulunmayan teknolojilerin çoğunu gösterir:

- ASP.NET Web Formları. Bu teknoloji yalnızca .NET Framework'de kullanılabilir. Şu anda web formlarını .NET Core'a ASP.NET getirme planları bulunmamaktadır.

- WCF hizmetleri. Şubat-2020 itibariyle .NET Core'dan WCF hizmetlerini tüketmek için [wcf istemci kitaplığı](https://github.com/dotnet/wcf) kullanılabilir olsa bile, WCF sunucu uygulaması yalnızca .NET Framework'de kullanılabilir. Bu senaryo .NET Core'un gelecekteki sürümleri için düşünülebilir, windows [uyumluluk paketine](../../../core/porting/windows-compat-pack.md)eklenmesi için düşünülen bazı API'ler bile vardır.

- İş akışıyla ilgili hizmetler. Windows İş Akışı Temeli (WF), İş Akışı Hizmetleri (Tek bir hizmette WCF + WF) ve WCF Veri Hizmetleri (eski adıyla ADO.NET Veri Hizmetleri olarak bilinir) yalnızca .NET Framework'de kullanılabilir. Şu anda onları .NET Core'a getirme gibi bir plan bulunmamaktadır.

Resmi [.NET Core yol haritasında](https://github.com/dotnet/core/blob/master/roadmap.md)listelenen teknolojilere ek olarak, diğer özellikler .NET Core'a veya yeni [birleştirilmiş .NET platformuna](https://devblogs.microsoft.com/dotnet/introducing-net-5/)taşınabilir. Sesinizi duyurabilmek için GitHub'daki tartışmalara katılmayı düşünebilirsiniz. Ve bir şey eksik olduğunu düşünüyorsanız, [dotnet / runtime](https://github.com/dotnet/runtime/issues/new) GitHub deposunda yeni bir sorun dosya.

## <a name="using-a-platform-or-api-that-doesnt-support-net-core"></a>.NET Core'u desteklemeyen bir platform veya API kullanma

Bazı Microsoft ve üçüncü taraf platformlar .NET Core'u desteklemez. Örneğin, bazı Azure hizmetleri .NET Core'da henüz kullanılamayan bir SDK sağlar. Azure SDK'larının çoğu sonunda .NET Core/Standard'a taşınabilir, ancak bazıları çeşitli nedenlerden dolayı olmayabilir. Kullanılabilir Azure SDK SDK'larını [Azure SDK Son Sürümler](https://azure.github.io/azure-sdk/releases/latest/index.html) sayfasında görebilirsiniz.

Bu arada, Azure'daki herhangi bir platform veya hizmet istemci API'sıyla .NET Core'u hala desteklemiyorsa, Azure hizmetinden veya sdenisistemci SDK'dan .NET Framework'de eşdeğer REST API'sini kullanabilirsiniz.

### <a name="additional-resources"></a>Ek kaynaklar

- **.NET Çekirdek Rehberi** \
  [https://docs.microsoft.com/dotnet/core/index](../../../core/index.md)

- **.NET Framework'den .NET Core'a taşıma** \
  [https://docs.microsoft.com/dotnet/core/porting/index](../../../core/porting/index.md)

- **.NET Core Üzerinde Docker Kılavuzu** \
  [https://docs.microsoft.com/dotnet/core/docker/introduction](../../../core/docker/introduction.md)

- **.NET Bileşenlerine Genel Bakış** \
  [https://docs.microsoft.com/dotnet/standard/components](../../../standard/components.md)

>[!div class="step-by-step"]
>[Önceki](net-core-container-scenarios.md)
>[Sonraki](container-framework-choice-factors.md)
