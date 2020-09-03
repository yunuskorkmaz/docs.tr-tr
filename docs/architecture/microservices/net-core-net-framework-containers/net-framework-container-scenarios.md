---
title: Docker kapsayıcıları için ne zaman .NET Framework seçilmelidir?
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | Docker kapsayıcıları için .NET Framework seçme
ms.date: 01/30/2020
ms.openlocfilehash: 116ba02878a60487f1af3c2b2e084307fad29618
ms.sourcegitcommit: b1f4756120deaecb8b554477bb040620f69a4209
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2020
ms.locfileid: "89414428"
---
# <a name="when-to-choose-net-framework-for-docker-containers"></a>Docker kapsayıcıları için ne zaman .NET Framework seçilmelidir?

.NET Core yeni uygulamalar ve uygulama desenleri için önemli avantajlar sağladığından, .NET Framework birçok mevcut senaryo için iyi bir seçenek olmaya devam edecektir.

## <a name="migrating-existing-applications-directly-to-a-windows-server-container"></a>Mevcut uygulamaları doğrudan bir Windows Server kapsayıcısına geçirme

Mikro hizmetler oluşturmasanız bile, yalnızca dağıtımı basitleştirmek için Docker kapsayıcılarını kullanmak isteyebilirsiniz. Örneğin, Docker ile DevOps iş akışınızı geliştirmek isteyebilirsiniz. kapsayıcılar, size daha iyi yalıtılmış test ortamları verebilir ve ayrıca bir üretim ortamına geçtiğinizde eksik bağımlılıklardan kaynaklanan dağıtım sorunlarını ortadan kaldırabilir. Bunlar gibi durumlarda, tek parçalı bir uygulama dağıtsanız bile, geçerli .NET Framework uygulamalarınız için Docker ve Windows kapsayıcıları kullanmak mantıklı olur.

Bu senaryo için çoğu durumda, mevcut uygulamalarınızı .NET Core 'a geçirmeniz gerekmez; geleneksel .NET Framework içeren Docker Kapsayıcıları kullanabilirsiniz. Ancak, ASP.NET Core ' de yeni bir hizmet yazma gibi, mevcut bir uygulamayı genişletmekle birlikte .NET Core kullanmak önerilen bir yaklaşımdır.

## <a name="using-third-party-net-libraries-or-nuget-packages-not-available-for-net-core"></a>.NET Core için mevcut olmayan üçüncü taraf .NET kitaplıklarını veya NuGet paketlerini kullanma

Üçüncü taraf kitaplıkları, .NET Core dahil olmak üzere tüm .NET özellikleri genelinde kod paylaşımına izin veren [.NET Standard](../../../standard/net-standard.md)hızla bir şekilde bir şekilde kullanıyor. .NET Standard 2,0 ve üzeri sürümlerde, farklı çerçeveler genelinde API Surface uyumluluğu önemli ölçüde daha büyük hale gelmiştir. Daha da fazla .NET Core 2. x ve daha yeni uygulamalar, mevcut .NET Framework kitaplıklarına doğrudan başvurabilir (bkz. [.NET Framework 4.6.1 destekleme .NET Standard 2,0](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#net-framework-461-supporting-net-standard-20)).

Ayrıca, [Windows Uyumluluk Paketi](../../../core/porting/windows-compat-pack.md) windows üzerinde .NET Standard 2,0 için KULLANILABILIR olan API yüzeyini genişletir. Bu paket, Windows üzerinde çalıştırmak için çok sayıda kodu .NET Standard 2. x ' e yeniden derliyorsanız ve çok az değişiklikle.

Bununla birlikte, 2,0 ve .NET Core 2,1 ' den .NET Standard bu yana bu olağanüstü ilerlemeyi bile, bazı NuGet paketlerinin Windows 'un çalışması ve .NET Core 'u desteklememe gibi durumlar olabilir. Bu paketler uygulamanız için önemliyse, Windows kapsayıcılarında .NET Framework kullanmanız gerekir.

## <a name="using-net-technologies-not-available-for-net-core"></a>.NET Core için kullanılamayan .NET teknolojilerini kullanma

Bazı .NET Framework teknolojileri .NET Core 'un geçerli sürümünde (Bu yazma itibariyle sürüm 3,1) kullanılamaz. Bunlardan bazıları sonraki sürümlerde kullanılabilir hale gelebilir, ancak diğerleri .NET Core tarafından hedeflenen yeni uygulama desenlerine sığmıyor ve hiçbir şekilde kullanılamayabilir.

Aşağıdaki listede, .NET Core 3,1 ' de kullanılamayan teknolojilerin çoğu gösterilmektedir:

- ASP.NET Web Forms. Bu teknoloji yalnızca .NET Framework kullanılabilir. Şu anda ASP.NET Web Forms .NET Core 'a getirmeye yönelik bir plan yoktur.

- WCF Hizmetleri. WCF-2020 itibariyle, .NET Core 'dan WCF hizmetlerini kullanmak için bir [WCF-istemci kitaplığı](https://github.com/dotnet/wcf) kullanılabilir olduğunda bıle, WCF sunucu uygulamasının yalnızca .NET Framework kullanılabilir. Bu senaryo, .NET Core 'un gelecek sürümleri için göz önünde bulundurulmalı, [Windows Uyumluluk Paketi](../../../core/porting/windows-compat-pack.md)'ne dahil edilmesi Için bazı API 'ler bile vardır.

- İş akışı ile ilgili hizmetler. Windows Workflow Foundation (WF), Iş akışı hizmetleri (tek bir hizmette WCF + WF) ve WCF Veri Hizmetleri (eski adıyla ADO.NET veri Hizmetleri) yalnızca .NET Framework kullanılabilir. Şu anda bunları .NET Core 'a getirmeye yönelik bir plan yoktur.

Resmi [.NET Core yol haritasında](https://github.com/dotnet/core/blob/master/roadmap.md)listelenen teknolojilerin yanı sıra, diğer özellikler .NET Core veya yeni [Birleşik .NET platformu](https://devblogs.microsoft.com/dotnet/introducing-net-5/)için de olabilir. Sesinizin duyabilmesi için GitHub 'daki tartışmalara katılımını düşünebilirsiniz. Bir şeyin eksik olduğunu düşünüyorsanız, [DotNet/Runtime](https://github.com/dotnet/runtime/issues/new) GitHub deposunda yeni bir sorun verin.

## <a name="using-a-platform-or-api-that-doesnt-support-net-core"></a>.NET Core desteklemeyen bir platform veya API kullanma

Bazı Microsoft ve üçüncü taraf platformları .NET Core ' u desteklemez. Örneğin, bazı Azure hizmetleri henüz .NET Core üzerinde tüketim için kullanılamayan bir SDK sağlar. Azure SDK 'sının en sonunda .NET Core/Standard ile bağlantı edilmelidir, ancak bazıları çeşitli nedenlerden kaynaklanabilir. Kullanılabilir Azure [SDK 'Larını Azure SDK 'Sının en son sürümleri](https://azure.github.io/azure-sdk/releases/latest/index.html) sayfasında görebilirsiniz.

Bu sırada, Azure 'daki herhangi bir platform veya hizmet, istemci API 'SI ile .NET Core 'u desteklemiyorsa, Azure hizmetindeki veya .NET Framework istemci SDK 'sindeki eşdeğer REST API de kullanabilirsiniz.

### <a name="additional-resources"></a>Ek kaynaklar

- **.NET temelleri** \
  [https://docs.microsoft.com/dotnet/fundamentals](../../../fundamentals/index.yml)

- **.NET Framework 'den .NET Core 'a taşıma** \
  [https://docs.microsoft.com/dotnet/core/porting/index](../../../core/porting/index.md)

- **Docker kılavuzunda .NET Core** \
  [https://docs.microsoft.com/dotnet/core/docker/introduction](../../../core/docker/introduction.md)

- **.NET bileşenlerine genel bakış** \
  [https://docs.microsoft.com/dotnet/standard/components](../../../standard/components.md)

>[!div class="step-by-step"]
>[Önceki](net-core-container-scenarios.md) 
> [Sonraki](container-framework-choice-factors.md)
