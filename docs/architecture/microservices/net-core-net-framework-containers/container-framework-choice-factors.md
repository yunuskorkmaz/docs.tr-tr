---
title: Karar tablosu. Docker için kullanılacak .NET çerçeveleri
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | Karar tablosu, Docker için kullanılacak .NET çerçeveleri
ms.date: 01/13/2021
ms.openlocfilehash: 35f101b3f4030e081068677b3754363bf6cd8210
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98188666"
---
# <a name="decision-table-net-frameworks-to-use-for-docker"></a>Karar tablosu: Docker için kullanılacak .NET çerçeveleri

Aşağıdaki karar tablosu .NET Framework mi yoksa .NET 5 mi kullanacağınızı özetler. Linux kapsayıcılarında, Linux tabanlı Docker konakları (VM 'Ler veya sunucular) gerektiğini ve Windows kapsayıcıları için Windows Server tabanlı Docker konaklarının (VM 'Ler veya sunucular) gerekli olduğunu unutmayın.

> [!IMPORTANT]
> Geliştirme makineleriniz, Linux veya Windows 'un bulunduğu bir Docker ana bilgisayarı çalıştırır. Çalıştırmak ve tek bir çözümde birlikte test etmek istediğiniz ilgili mikro hizmetler, tümünün aynı kapsayıcı platformunda çalıştırılması gerekir.

| Mimari/uygulama türü | Linux kapsayıcıları | Windows Kapsayıcıları |
|-------------------------|------------------|--------------------|
| Kapsayıcılar üzerinde mikro hizmetler | .NET 5 | .NET 5 |
| Tek parçalı uygulama | .NET 5 | .NET Framework <br/> .NET 5 |
| Sınıfının en iyisi performansı ve ölçeklenebilirliği | .NET 5 | .NET 5 |
| Windows Server eski uygulaması ("kahverengi-Field") kapsayıcılara geçiş | -- | .NET Framework |
| Yeni kapsayıcı tabanlı geliştirme ("yeşil-alan") | .NET 5 | .NET 5 |
| ASP.NET Çekirdeği | .NET 5 | .NET 5 (önerilir) <br/> .NET Framework |
| ASP.NET 4 (MVC 5, Web API 2 ve Web Forms) | -- | .NET Framework |
| SignalR Hizmetleri | .NET Core 2,1 veya üzeri sürümü | .NET Framework <br/> .NET Core 2,1 veya üzeri sürümü |
| WCF, WF ve diğer eski çerçeveler | .NET Core 'da WCF (yalnızca istemci kitaplığı) | .NET Framework <br/> .NET 5 ' te WCF (yalnızca istemci kitaplığı) |
| Azure hizmetleri kullanımı | .NET 5 <br/> (en sonunda Azure Hizmetleri, .NET 5 için istemci SDK 'larını sağlar) | .NET Framework <br/> .NET 5 <br/> (en sonunda Azure Hizmetleri, .NET 5 için istemci SDK 'larını sağlar) |

>[!div class="step-by-step"]
>[Önceki](net-framework-container-scenarios.md) 
> [Sonraki](net-container-os-targets.md)
