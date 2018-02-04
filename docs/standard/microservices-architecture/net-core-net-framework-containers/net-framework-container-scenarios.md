---
title: "Ne zaman Docker kapsayıcıları için .NET Framework seçin"
description: "Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Ne zaman Docker kapsayıcıları için .NET Framework seçin"
keywords: Docker, Microservices, ASP.NET, Container
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: fcfb78bf521107b14d7796235f52c836f48f41fe
ms.sourcegitcommit: d2da0142247ef42a219a5d2907f153e62dc6ea0d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2018
---
# <a name="when-to-choose-net-framework-for-docker-containers"></a>Ne zaman Docker kapsayıcıları için .NET Framework seçin

.NET Core yeni uygulamalar ve uygulama düzenleri için önemli avantajlar sunar, ancak .NET Framework birçok varolan senaryoları için iyi bir seçimdir olmaya devam edecektir.

## <a name="migrating-existing-applications-directly-to-a-windows-server-container"></a>Doğrudan Windows Server kapsayıcı mevcut uygulamalarını geçirme

Mikro oluşturmadığınızı olsa bile dağıtım, yalnızca basitleştirmek için Docker kapsayıcılar kullanmak isteyebilirsiniz. Örneğin, belki de DevOps iş akışınızı docker'la artırmak istediğiniz — kapsayıcıları daha iyi yalıtılmış test ortamları verebilir ve ayrıca bir üretim ortamına taşıdığınızda tarafından eksik bağımlılıklar nedeniyle dağıtım sorunlarını ortadan kaldırabilirsiniz. Tek yapılı bir uygulama dağıttığınız olsa bile bu gibi durumlarda, Docker ve Windows kapsayıcıları için geçerli .NET Framework uygulamalarınızı kullanmaya mantıklıdır.

Bu senaryo için çoğu durumda, mevcut uygulamalarınızı .NET Core geçirmek gerekmez; Geleneksel .NET Framework dahil Docker kapsayıcıları kullanabilirsiniz. Ancak, önerilen yaklaşım yeni bir hizmet ASP.NET Core yazma gibi varolan bir uygulama, genişletme gibi .NET Core kullanmaktır.

## <a name="using-third-party-net-libraries-or-nuget-packages-not-available-for-net-core"></a>Üçüncü taraf .NET kitaplıklarına veya NuGet paketlerini kullanılamaz .NET Core için kullanma

Üçüncü taraf kitaplıklar hızla benimsemenin [.NET standart](https://docs.microsoft.com/dotnet/standard/net-standard), .NET Core dahil olmak üzere tüm .NET özellikleri arasında paylaşımı kodu sağlar. API yüzeyi ötesinde .NET standart kitaplığı 2.0 ile uyumluluk farklı çerçeveler arasında önemli ölçüde daha büyük hale geldi ve .NET Core 2. 0 ' uygulamaları doğrudan da var olan .NET Framework kitaplıkları başvurabilir (bkz [compat Dolgu](https://github.com/dotnet/standard/blob/master/docs/faq.md#how-does-net-standard-versioning-work)).

Ancak, bile bu olağanüstü progression ile .NET standart 2.0 ve .NET Core 2.0 itibaren olabilir durumlarda bazı NuGet paketleri çalıştırmak için Windows gerekiyor ve .NET Core desteklemeyebilir. Ardından bu paketleri, uygulamanız için kritik olan, .NET Framework Windows kapsayıcılarında kullanmanız gerekecektir.

## <a name="using-net-technologies-not-available-for-net-core"></a>.NET Core için kullanılabilir değil .NET teknolojilerini kullanarak 

Bazı .NET Framework teknolojiler .NET Core (sürüm 2.0 bu yazma itibariyle) geçerli sürümünde kullanılabilir değildir. Bazıları daha sonra .NET Core sürümlerde kullanılabilir olur (.NET Core 2.x), ancak diğer desenleri .NET Core tarafından hedeflenen ve hiçbir zaman kullanılabilir yeni uygulama için geçerli değildir.

Aşağıdaki liste, .NET Core 2. 0 ' kullanılabilir değil teknolojileri çoğunu gösterir:

-   ASP.NET Web formları. Bu teknoloji, yalnızca .NET Framework üzerinde kullanılabilir. Şu anda ASP.NET Web Forms .NET Core getirmek için plan yok.

-   WCF hizmetleri. Zaman bile bir [WCF istemci Kitaplığı](https://github.com/dotnet/wcf) .NET Core WCF hizmetlerini kullanmak kullanılabilir. mid-2017 itibariyle, WCF sunucusu uygulaması yalnızca .NET Framework üzerinde kullanılabilir. Bu senaryo, .NET Core gelecek sürümler için değerlendirilebilir.

-   İş akışı ile ilgili hizmetlerin. Windows Workflow Foundation (WF), (WCF + tek bir hizmette WF) iş akışı hizmetleri ve WCF Veri Hizmetleri (önceki adıyla ADO.NET Data Services bilinir) yalnızca .NET Framework üzerinde kullanılabilir. Şu anda .NET Core getirmek için plan yok.

Ek olarak teknolojileri listelenen resmi [.NET Core yol haritası](https://github.com/aspnet/Home/wiki/Roadmap), diğer özellikler için .NET Core bağlantı noktalı. Olarak etiketlenmiş öğeleri için tam bir listesi, bakmak [bağlantı noktası çekirdek](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aport-to-core) CoreFX GitHub sitesinde. Bu liste bu bileşenler için .NET Core getirmek için Microsoft'un taahhüdü göstermiyor Not — öğeleri yalnızca topluluk gelen istekleri yakalama. Yukarıda listelenen bileşenleri önem verdiğiniz, böylece sesinizi heard github'da tartışmalara katılan düşünün. Ve şeyin eksik olduğunu düşünüyorsanız, lütfen [CoreFX depoya yeni bir sorun dosya](https://github.com/dotnet/corefx/issues/new).

## <a name="using-a-platform-or-api-that-does-not-support-net-core"></a>Bir platform veya .NET Core desteklemiyor API kullanma

Bazı Microsoft veya üçüncü taraf platformları .NET Core desteklemez. Örneğin, bazı Azure Hizmetleri henüz .NET Core üzerinde tüketimi için kullanılabilir olmayan bir SDK'sı sağlar. Tüm Azure hizmetlerini sonunda .NET Core kullanacağı geçici, olmasıdır. Örneğin, [.NET Core için Azure DocumentDB SDK'sı](https://www.nuget.org/packages/Microsoft.Azure.DocumentDB.Core/1.2.1) 16 Kasım 2016 önizleme olarak yayımlanan ancak şimdi kararlı bir sürüm olarak genel olarak kullanılabilir (GA).

Bu arada, herhangi bir platform veya Azure hizmetinde hala .NET Core kendi istemci API desteklemiyorsa, .NET Framework üzerinde Azure hizmeti veya SDK İstemcisi'nden eşdeğer REST API kullanabilirsiniz.

### <a name="additional-resources"></a>Ek kaynaklar

-   **.NET core Kılavuzu**
    [*https://docs.microsoft.com/dotnet/core/index*](https://docs.microsoft.com/dotnet/core/index)

-   **.NET Framework'teki .NET Core taşıma**
    [*https://docs.microsoft.com/dotnet/core/porting/index*](https://docs.microsoft.com/dotnet/core/porting/index)

-   **.NET framework Docker kılavuzu üzerinde**
    [*https://docs.microsoft.com/dotnet/framework/docker/*](https://docs.microsoft.com/dotnet/framework/docker/)

-   **.NET bileşenleri'ne genel bakış**
    [*https://docs.microsoft.com/dotnet/standard/components*](https://docs.microsoft.com/dotnet/standard/components)




>[!div class="step-by-step"]
[Önceki] (net-core-kapsayıcı-scenarios.md) [sonraki] (kapsayıcı-framework-seçim-factors.md)
