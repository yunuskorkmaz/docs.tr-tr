---
title: Karar tablosu. Docker için kullanılacak .NET çerçeveleri
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | Karar tablosu, Docker için kullanılacak .NET çerçeveleri
ms.date: 09/11/2018
ms.openlocfilehash: 0087d80c2d949daf14e1edd773dd310f47c508a9
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71039673"
---
# <a name="decision-table-net-frameworks-to-use-for-docker"></a>Karar tablosu: Docker için kullanılacak .NET çerçeveleri

Aşağıdaki karar tablosu .NET Framework veya .NET Core 'un kullanılıp kullanılmayacağını özetler. Linux kapsayıcılarında, Linux tabanlı Docker konakları (VM 'Ler veya sunucular) gerektiğini ve Windows kapsayıcıları için Windows Server tabanlı Docker konaklarının (VM 'Ler veya sunucular) gerekli olduğunu unutmayın.

> [!IMPORTANT]
> Geliştirme makineleriniz, Linux veya Windows 'un bulunduğu bir Docker ana bilgisayarı çalıştırır. Çalıştırmak ve tek bir çözümde birlikte test etmek istediğiniz ilgili mikro hizmetler, tümünün aynı kapsayıcı platformunda çalıştırılması gerekir.

| Mimari/uygulama türü | Linux kapsayıcıları | Windows kapsayıcıları |
|-------------------------|------------------|--------------------|
| Kapsayıcılar üzerinde mikro hizmetler | .NET Core | .NET Core |
| Tek parçalı uygulama | .NET Core | .NET Framework <br/> .NET Core |
| Sınıfının en iyisi performansı ve ölçeklenebilirliği | .NET Core | .NET Core |
| Windows Server eski uygulaması ("kahverengi-Field") kapsayıcılara geçiş | -- | .NET Framework |
| Yeni kapsayıcı tabanlı geliştirme ("yeşil-alan") | .NET Core | .NET Core |
| ASP.NET Core | .NET Core | .NET Core (önerilir) <br/> .NET Framework |
| ASP.NET 4 (MVC 5, Web API 2 ve Web Forms) | -- | .NET Framework |
| SignalR Hizmetleri | .NET Core 2,1 veya üzeri sürümü | .NET Framework <br/> .NET Core 2,1 veya üzeri sürümü |
| WCF, WF ve diğer eski çerçeveler | .NET Core 'da WCF (yalnızca istemci kitaplığı) | .NET Framework <br/> .NET Core 'da WCF (yalnızca istemci kitaplığı) |
| Azure hizmetleri kullanımı | .NET Core <br/> (sonuç olarak tüm Azure hizmetleri .NET Core için istemci SDK 'larını sağlar) | .NET Framework <br/> .NET Core <br/> (sonuç olarak tüm Azure hizmetleri .NET Core için istemci SDK 'larını sağlar) |

>[!div class="step-by-step"]
>[Önceki](net-framework-container-scenarios.md)İleri
>[](net-container-os-targets.md)
