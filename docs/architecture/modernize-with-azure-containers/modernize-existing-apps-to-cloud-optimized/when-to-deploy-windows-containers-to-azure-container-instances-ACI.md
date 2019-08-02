---
title: Azure Container Instances (ACI) için Windows kapsayıcıları ne zaman dağıtılır
description: Azure bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernleştirin | Azure Container Instances (ACI) için Windows kapsayıcıları ne zaman dağıtılır
ms.date: 04/29/2018
ms.openlocfilehash: 3b6ae1ced9c4e01f5ab400e2575947a396064ebd
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68676909"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-instances-aci"></a>Azure Container Instances (ACI) için Windows kapsayıcıları ne zaman dağıtılır

Ana değer teklifini Azure Container Instances, kapsayıcıyı buna doğru bir şekilde dağıtmanızı ve bu ortamın bakımını yapmanıza gerek duymamanız, temel alınan işletim sistemini veya VM 'Leri yükseltmeniz/düzeltme eki uygulamanız gerekmez, hepsi saydam ve yeni bir dağıtım yapmanız gerekmez kullanıma hazırlama ortamına kapsayıcılar.

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
> [Önceki](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)İleri
> [](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
