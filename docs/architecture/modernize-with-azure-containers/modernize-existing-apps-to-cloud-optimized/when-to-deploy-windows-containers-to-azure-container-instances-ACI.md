---
title: Azure Container Instances (ACI) için Windows kapsayıcıları ne zaman dağıtılır
description: Azure bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernleştirin | Azure Container Instances (ACI) için Windows kapsayıcıları ne zaman dağıtılır
ms.date: 12/21/2020
ms.openlocfilehash: 556fe7cbec7d259db9ec886b777feda9eed09116
ms.sourcegitcommit: 5d9cee27d9ffe8f5670e5f663434511e81b8ac38
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98025139"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-instances-aci"></a>Azure Container Instances (ACI) için Windows kapsayıcıları ne zaman dağıtılır

Azure Container Instances ana değer teklifi, kapsayıcıyı buna doğrudan dağıtıp dağıtabilmenize gerek kalmaz, bu ortamın bakımını yapmanız gerekmez, temeldeki işletim sistemini veya VM 'Leri yükseltmeniz/düzeltme eki uygulamanız gerekmez, tüm bunlar saydam olur ve yalnızca kullanım için kullanıma uygun bir ortama dağıtabilirsiniz.

Azure VM 'lerini kapsayıcılarla birlikte kullanırken ACI 'yi kullanmak isteyebileceğiniz nedenler ve senaryolar ana senaryolara benzerdir, bu nedenle temel olarak Azure Container Instances kullanmaya yönelik temel senaryolar şunlardır:

- **Geliştirme ve test senaryoları**
- **Görev Otomasyonu**
- **CI/CD aracıları**
- **Küçük/ölçekli toplu iş işleme**
- **Basit Web uygulamaları**

Basit Web Apps senaryosu, acı için bir teme senaryosudur, ancak her kapsayıcı görüntüsü için yalnızca tek bir kapsayıcı örneğiniz olduğundan, yüksek kullanılabilirliğe sahip olmayacaktır ve yalnızca sınırlı ölçeklenebilirliğe sahip kalmazsınız.

Ancak tek bir kapsayıcı örnekleri sağladığından, acı altyapısı olarak kabul edilse bile, Windows Server ile normal Azure VM 'lerine kıyasla büyük bir avantaj vardır. ACI ile, kapsayıcıları yalnızca kendi kendine korunan bir ortama dağıtırsınız ve yalnızca bu kapsayıcılar için ödeme yaparsınız. VM 'Leri korumanız/güncelleştirmeniz gerekmez, bu nedenle kapsayıcılarla VM 'Leri kullandığınız birçok senaryo için çok daha iyi bir platformdur. ACI 'yi kullanarak, yalnızca bir kapsayıcı dağıtırsınız, yalnızca kapsayıcıları dağıttığınız bir VM ortamı oluşturmanız gerekmez.

Azure Container Instances (ACI) 'nin başlıca avantajları şunlardır:

- Sunucuları yönetmeksizin kapsayıcıları çalıştırma
- İsteğe bağlı kapsayıcılarla çevikliği artırma
- Tek bir komutla, kapsayıcıları, daha önce basit ve hızlı bir şekilde buluta dağıtın.
- Hiper yönetici yalıtımına sahip uygulamaları güvenli hale getirme

Kısaca, ACI ile, sanal makineleri yönetmeden veya yeni araçlar öğrenmeden uygulamalar geliştirebilir. Yalnızca uygulamanız bulutta çalışan bir kapsayıcıda yer alabilir.

> [!div class="step-by-step"]
> [Önceki](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md) 
>  [Sonraki](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
