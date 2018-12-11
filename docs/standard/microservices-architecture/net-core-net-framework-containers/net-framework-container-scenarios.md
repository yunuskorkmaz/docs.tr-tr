---
title: .NET Framework Docker kapsayıcıları için ne zaman
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | .NET Framework Docker kapsayıcıları için ne zaman
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/11/2018
ms.openlocfilehash: 1a91f645aa6f9ce8652fb18243c2e2775abe87d1
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53128758"
---
# <a name="when-to-choose-net-framework-for-docker-containers"></a>.NET Framework Docker kapsayıcıları için ne zaman

.NET Core için yeni uygulamalar ve uygulama desenleri önemli avantaj sunar, ancak .NET Framework, varolan birçok senaryo için iyi bir seçim olmaya devam edecektir.

## <a name="migrating-existing-applications-directly-to-a-windows-server-container"></a>Doğrudan Windows Server kapsayıcı mevcut uygulamalarını geçirme

Mikro hizmetler oluşturmadığınızı olsa bile dağıtım, yalnızca basitleştirmek için Docker kapsayıcıları kullanmak isteyebilirsiniz. Örneğin, belki de Docker ile DevOps iş akışınızın geliştirmek istediğiniz — kapsayıcılar, daha iyi yalıtılmış ve test ortamları verebilir ve ayrıca, bir üretim ortamına taşıdığınızda nedeni eksik bağımlılıklardır dağıtım sorunlarını ortadan kaldırabilir. Tek parça bir uygulamayı dağıtacak olsanız bile bu gibi durumlarda, Docker ve Windows kapsayıcıları geçerli .NET Framework uygulamalarınız için kullanmanın mantıklıdır.

Bu senaryo için çoğu durumda, mevcut uygulamalarınızı .NET Core geçişi gerekmez; Geleneksel .NET Framework'ü içeren Docker kapsayıcıları kullanabilirsiniz. Ancak, önerilen yaklaşım yeni bir hizmet içinde ASP.NET Core yazma gibi mevcut bir uygulamayı yeniden genişletirken .NET Core kullanmaktır.

## <a name="using-third-party-net-libraries-or-nuget-packages-not-available-for-net-core"></a>.NET Core için üçüncü taraf .NET kitaplıkları veya kullanılabilir değil NuGet paketlerini kullanma

Üçüncü taraf kitaplıklar hızla benimsemenin [.NET Standard](../../net-standard.md), .NET Core dahil olmak üzere tüm .NET özellikleri arasında paylaşımı kod sağlar. .NET Standard kitaplığı 2.0 ve API yüzeyi ötesinde uyumluluk farklı çerçeveler arasında önemli ölçüde daha büyük hale geldi ve de .NET Core 2.x uygulamaları doğrudan mevcut .NET Framework kitaplıkları başvurabilir (bkz [compat Dolgu](https://github.com/dotnet/standard/blob/master/docs/netstandard-20/README.md#net-framework-461-supporting-net-standard-20)).

Ayrıca, [Windows Uyumluluk Paketi](../../../core/porting/windows-compat-pack.md) Windows üzerinde .NET Standard 2.0 için kullanılabilir bir API yüzeyi genişletmek için Kas 2017 tarihinde yayınlanmıştır. Bu paketi .NET Standard için çoğu mevcut kodu yeniden derlemeden sağlayan 2.x ile Windows üzerinde çalıştırmak için çok az kayıpla veya hiç değişiklik.

Ancak, bile bu olağanüstü ilerleme ile .NET Standard 2.0 ve .NET Core 2.1 beri burada belirli NuGet paketlerini çalıştırmak için Windows gerekir ve .NET Core desteklemeyebilir durumlar olabilir. Ardından bu paketleri, uygulamanız için kritik olan, .NET Framework Windows kapsayıcılarında kullanmanız gerekir.

## <a name="using-net-technologies-not-available-for-net-core"></a>.NET Core için kullanılabilir değil .NET teknolojileri kullanarak 

Bazı .NET Framework teknolojilerini .NET Core (sürüm 2.1 şu andan itibaren)'ın geçerli sürümünde kullanılabilir değil. Bunların bazılarını daha sonra .NET Core sürümlerde kullanılabilir olacaktır (.NET Core 2.x), ancak diğerleri desenleri .NET Core tarafından hedeflenen ve hiçbir zaman kullanılabilir yeni uygulama için geçerli değildir.

Aşağıdaki liste de .NET Core kullanılamayan teknolojilerinin çoğu gösterir 2.x:

-   ASP.NET Web Forms. Bu teknoloji, yalnızca .NET Framework üzerinde kullanılabilir. Şu anda .NET Core ile ASP.NET Web Forms getirmek için hiçbir plan yok.

-   WCF hizmetleri. Zaman bile bir [WCF istemci Kitaplığı](https://github.com/dotnet/wcf) mid-2017, WCF sunucusu uygulaması yalnızca .NET Framework üzerinde kullanılabilir olarak .NET Core, gelen WCF hizmetleri kullanma kullanıma sunulmuştur. Bu senaryo olarak kabul edilir .NET Core, gelecek sürümleri için kabul edilme bile bazı API'leri vardır [Windows Uyumluluk Paketi](../../../core/porting/windows-compat-pack.md).

-   İş akışı ile ilgili hizmetler. Windows Workflow Foundation (WF) iş akışı Hizmetleri (WCF + WF tek bir hizmette) ve WCF Veri Hizmetleri (eski adıyla ADO.NET Data Services da bilinir) yalnızca .NET Framework üzerinde kullanılabilir. Şu anda .NET Core getirilecek herhangi bir plan da vardır.

Teknolojilerin yanı sıra resmi listelenen [.NET Core yol haritası](https://github.com/aspnet/Home/wiki/Roadmap), diğer özellikler, .NET Core için unity'nin. Olarak etiketlenmiş öğeler tam listesi için bakmak [bağlantı noktası çekirdek](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aport-to-core) Corefx'te GitHub sitesinde. Bu liste bu bileşenler, .NET Core getirmek için Microsoft'un taahhüdü temsil etmiyor Not — öğeleri yalnızca topluluk gelen istekleri yakalayın. Yukarıda listelenen bileşenleri önem verdiğiniz, böylece kendi sesinizi heard GitHub üzerindeki tartışmaların katılan göz önünde bulundurun. Ve bir şeyler eksik olduğunu düşünüyorsanız, lütfen [Corefx'te depoya yeni bir sorun dosya](https://github.com/dotnet/corefx/issues/new).

.NET Core 3 (Bu çalışır, bu makalenin yazıldığı sırada) çok sayıda mevcut .NET Framework API desteği içerecektir olsa da, bu nedenle, şu anda yönelik Masaüstü bunlar, kapsayıcı dünyanın herhangi bir kullanıma çeken.

## <a name="using-a-platform-or-api-that-does-not-support-net-core"></a>Bir platform veya .NET Core desteği olmayan API kullanma

.NET Core, bazı Microsoft veya üçüncü taraf platformları desteklemez. Örneğin, bazı Azure Hizmetleri henüz .NET Core tüketim için kullanılabilir olmayan bir SDK'sı sağlar. Tüm Azure Hizmetleri, .NET Core sonunda kullanacağınız için bu geçici budur. Örneğin, [.NET Core için Azure DocumentDB SDK'sı](https://www.nuget.org/packages/Microsoft.Azure.DocumentDB.Core/1.2.1) 16 Kasım 2016, önizleme olarak yayımlanan ancak kararlı bir sürüm olarak genel kullanıma (GA) sunuldu.

Bu arada, herhangi bir platform veya Azure hizmeti yine de .NET Core API istemcisini ile desteklemiyorsa, .NET Framework üzerinde Azure hizmet veya istemci SDK'sı karşılığı REST API kullanabilirsiniz.

### <a name="additional-resources"></a>Ek kaynaklar

-   **.NET Core Kılavuzu**  
    [https://docs.microsoft.com/dotnet/core/index](../../../core/index.md)

-   **.NET Core ile .NET Framework'ten taşıma**  
    [https://docs.microsoft.com/dotnet/core/porting/index](../../../core/porting/index.md)

-   **Docker Üzerinde .NET Framework Kılavuzu**  
    [https://docs.microsoft.com/dotnet/framework/docker/](../../../framework/docker/index.md)

-   **.NET bileşenleri'ne genel bakış**  
    [https://docs.microsoft.com/dotnet/standard/components](../../components.md)

>[!div class="step-by-step"]
>[Önceki](net-core-container-scenarios.md)
>[İleri](container-framework-choice-factors.md)