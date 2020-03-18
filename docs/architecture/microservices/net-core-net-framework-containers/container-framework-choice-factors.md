---
title: Karar masası. .NET çerçeveleri Docker için kullanılacak
description: .NET Microservices Mimari Containerized .NET Uygulamaları için | Karar tablosu, .NET çerçeveleri Docker için kullanılacak
ms.date: 09/11/2018
ms.openlocfilehash: 8ffe2b7bc0bee976d3a63b274994dbcc8aef0c61
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77628325"
---
# <a name="decision-table-net-frameworks-to-use-for-docker"></a>Karar tablosu: Docker için kullanılacak .NET çerçeveleri

Aşağıdaki karar tablosunda .NET Framework veya .NET Core kullanılıp kullanılmayacakları özetlenmiştir. Linux kapsayıcıları için Linux tabanlı Docker ana bilgisayarlarına (VM veya sunucular) ve Windows Kapsayıcıları için Windows Server tabanlı Docker ana bilgisayarlarına (VM veya sunucu) ihtiyacınız olduğunu unutmayın.

> [!IMPORTANT]
> Geliştirme makineleriniz, Linux veya Windows olmak üzere bir Docker ana bilgisayarını çalıştıracaktır. Birlikte çalıştırmak ve test etmek istediğiniz ilgili mikro hizmetlerin aynı kapsayıcı platformunda çalıştırılması gerekir.

| Mimari / Uygulama Türü | Linux kapsayıcıları | Windows Kapsayıcıları |
|-------------------------|------------------|--------------------|
| Konteynerlerde mikro hizmetler | .NET Core | .NET Core |
| Monolitik uygulama | .NET Core | .NET Framework <br/> .NET Core |
| Sınıfının en iyisi performans ve ölçeklenebilirlik | .NET Core | .NET Core |
| Windows Server eski uygulaması ("kahverengi alan") kapsayıcılara geçiş | -- | .NET Framework |
| Yeni konteyner tabanlı geliştirme ("yeşil alan") | .NET Core | .NET Core |
| ASP.NET Çekirdeği | .NET Core | .NET Çekirdek (önerilir) <br/> .NET Framework |
| ASP.NET 4 (MVC 5, Web API 2 ve Web Formları) | -- | .NET Framework |
| SignalR hizmetleri | .NET Core 2.1 veya daha yüksek sürüm | .NET Framework <br/> .NET Core 2.1 veya daha yüksek sürüm |
| WCF, WF ve diğer eski çerçeveler | .NET Core'daki WCF (yalnızca istemci kitaplığı) | .NET Framework <br/> .NET Core'daki WCF (yalnızca istemci kitaplığı) |
| Azure hizmetlerinin tüketimi | .NET Core <br/> (sonunda çoğu Azure hizmeti .NET Core için istemci SDK'ları sağlar) | .NET Framework <br/> .NET Core <br/> (sonunda çoğu Azure hizmeti .NET Core için istemci SDK'ları sağlar) |

>[!div class="step-by-step"]
>[Önceki](net-framework-container-scenarios.md)
>[Sonraki](net-container-os-targets.md)
