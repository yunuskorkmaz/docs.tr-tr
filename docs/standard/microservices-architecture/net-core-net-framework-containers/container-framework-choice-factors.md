---
title: "Karar tablo. .NET Framework için Docker kullanmak için"
description: "Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Karar tablosu, .NET Framework için Docker kullanmak için"
keywords: "Docker, mikro, ASP.NET, kapsayıcı"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 40e6a14e7e3515194185e1f4558c91ac29429108
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="decision-table-net-frameworks-to-use-for-docker"></a>Karar tablosu: .NET Framework için Docker kullanmak için

.NET Framework veya .NET Core ve Windows veya Linux kapsayıcıları kullanıp kullanmayacağınızı aşağıda özetlenmiştir. Linux kapsayıcıları için Linux tabanlı Docker ana bilgisayarları (VM'ler veya sunucular) gerekir ve Docker konakları (VM'ler veya sunucular) göre Windows kapsayıcıları için Windows Server gerektiğini unutmayın.

Uygulamanızın kararınızı etkileyen çeşitli özellikler vardır. Bu özellikler önemini karar verirken tartmanız gerekir.

> [!IMPORTANT]
> Geliştirme makinelerinizi bir Docker ana bilgisayar, Linux veya Windows çalışır. Bir çözümde birlikte test ve çalıştırmak istediğiniz ilgili mikro tüm aynı kapsayıcı platformda çalışması gerekir.

* Uygulama Mimarisi seçimdir **kapsayıcılarında mikro**.
    - .NET uygulaması seçiminizi olmalıdır *.NET Core*.
    - Kapsayıcı platform tercih ettiğiniz ya da olabilir *Linux kapsayıcıları* veya *Windows kapsayıcıları*.
* Uygulama Mimarisi seçimdir bir **tek yapılı uygulama**.
    - .NET uygulaması tercih ettiğiniz ya da olabilir *.NET Core* veya *.NET Framework*.
    - Seçmiş olmanız durumunda *.NET Core*, kapsayıcı platform tercih ettiğiniz ya da olabilir *Linux kapsayıcıları* veya *Windows kapsayıcıları*.
    - Seçmiş olmanız durumunda *.NET Framework*, kapsayıcı platform seçiminizi olmalıdır *Windows kapsayıcıları*.
* Uygulamanız bir **yeni kapsayıcı tabanlı geliştirme ("alanı yeşil")**.
    - .NET uygulaması seçiminizi olmalıdır *.NET Core*.
    - Kapsayıcı platform tercih ettiğiniz ya da olabilir *Linux kapsayıcıları* veya *Windows kapsayıcıları*.
* Uygulamanız bir **kapsayıcıları için Windows Server eski uygulama ("alanı kahverengi") geçiş**
    - .NET uygulaması seçimdir *.NET Framework* framework bağımlılığını tabanlı.
    - Kapsayıcı platform seçiminizi olmalıdır *Windows kapsayıcıları* .NET Framework bağımlılık nedeniyle.
* Uygulamanızın tasarım hedefi olan **sınıfı içinde en iyi performans ve ölçeklenebilirlik**.
    - .NET uygulaması seçiminizi olmalıdır *.NET Core*.
    - Kapsayıcı platform tercih ettiğiniz ya da olabilir *Linux kapsayıcıları* veya *Windows kapsayıcıları*.
* Kullanarak uygulamanızı yerleşik **ASP.NET Core**.
    - .NET uygulaması seçiminizi olmalıdır *.NET Core*.
    - Kullanabileceğiniz *.NET Framework* diğer çerçevesi bağımlılıklarına varsa uygulaması.
    - Seçmiş olmanız durumunda *.NET Core*, kapsayıcı platform tercih ettiğiniz ya da olabilir *Linux kapsayıcıları* veya *Windows kapsayıcıları*.
    - Seçmiş olmanız durumunda *.NET Framework*, kapsayıcı platform seçiminizi olmalıdır *Windows kapsayıcıları*.
* Kullanarak uygulamanızı yerleşik **ASP.NET 4 (MVC 5, Web API 2 ve Web formları)**.
    - .NET uygulaması seçimdir *.NET Framework* framework bağımlılığını tabanlı.
    - Kapsayıcı platform seçiminizi olmalıdır *Windows kapsayıcıları* .NET Framework bağımlılık nedeniyle.
* Uygulamanızın kullandığı **SignalR Hizmetleri**.
    - .NET uygulaması seçiminizi olabilir *.NET Framework*, veya *.NET Core (yayımlandığında) 2.1 veya üzeri*.
    - Kapsayıcı platform seçiminizi olmalıdır *Windows kapsayıcıları* SignalR uygulama .NET Framework seçerseniz.
    - .NET Core 2.1 veya üzeri SignalR uygulaması (yayımlandığında) seçerseniz kapsayıcı platform seçiminizi Linux kapsayıcıları veya Windows kapsayıcıları olabilir.  
    - Zaman **SignalR Hizmetleri** çalıştıracağınız *.NET Core*, kullanabileceğiniz *Linux kapsayıcıları ya da Windows kapsayıcıları*.
* Uygulamanızın kullandığı **WCF, WF ve diğer eski çerçeveleri**.
    - .NET uygulaması seçimdir *.NET Framework*, veya *(ın gelecek sürümlerinden için yol haritası) .NET Core*.
    - Kapsayıcı platform seçiminizi olmalıdır *Windows kapsayıcıları* .NET Framework bağımlılık nedeniyle.
* Uygulamanızı içerir **tüketim, Azure Hizmetleri**.
    - .NET uygulaması seçimdir *.NET Framework*, veya *.NET Core (sonunda tüm Azure Hizmetleri sağlayacaktır istemci SDK'ları için .NET Core)*.
    - Kapsayıcı platform seçiminizi olmalıdır *Windows kapsayıcıları* .NET Framework istemci API kullanıyorsanız.
    - İstemci için kullanılabilen API'lerin kullanırsanız *.NET Core*, arasından seçim yapabilirsiniz *Linux kapsayıcıları ve Windows kapsayıcıları*.

>[!div class="step-by-step"]
[Önceki] (net-framework-kapsayıcı-scenarios.md) [sonraki] (net-kapsayıcı-os-targets.md)
