---
title: Service Fabric Windows kapsayıcıları dağıtma zamanı
description: Azure Bulut ve Windows kapsayıcılarla varolan .NET uygulamaları modernize | Service Fabric Windows kapsayıcıları dağıtma zamanı
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/30/2018
ms.openlocfilehash: c41db8b37c883f9369a6b8d1f8bccbc0535f504c
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/10/2018
---
# <a name="when-to-deploy-windows-containers-to-service-fabric"></a>Service Fabric Windows kapsayıcıları dağıtma zamanı

Windows kapsayıcılarında tabanlı uygulamaları hızlı bir şekilde daha uzakta Iaas Vm'lerden taşıma platformları kullanmanız gerekir. Bu geliştirilmiş otomatik ölçeklenebilirlik ve yüksek ölçeklenebilirlik içindir ve tam yönetim deneyiminde dağıtımlar için önemli geliştirmeler kazanmak için yükseltir, sürüm oluşturma, alma ve sistem durumu izleme. Azure Service Fabric, Microsoft Azure bulut, aynı zamanda şirket içi veya başka bir bulutta bile kullanılabilir orchestrator ile bu hedefleri elde edebilirsiniz.

Birçok kuruluş kaldırma ve iki nedenden dolayı kapsayıcılara tek yapılı uygulamalarınız kaydırma:

-   Maliyet düşürülmesi, ya da birleştirme ve temizleme mevcut donanım veya yüksek yoğunluk çalışan uygulamalar nedeniyle.

-   Geliştirme ve işlemler arasında tutarlı bir dağıtım sözleşme.

Maliyet azaltması sürdürdüğünü anlaşılabilir ve tüm organizasyonlar bu hedefe birleştirme olasıdır. Tutarlı bir dağıtım, değerlendirilecek daha zor, ancak aynı derecede önemli olarak gelir. Tutarlı bir dağıtım sözleşme geliştiriciler bunları uygun teknolojiyi kullanmak üzere seçmek ücretsiz ve işlemler ekibinin uygulamaları dağıtmak ve yönetmek için tek bir yolu alır söyler. Bu anlaşma birçok farklı teknolojiler karmaşıklık ile ilgili işlemleri olması ya da yalnızca belirli teknolojileri ile geliştiricilerin zorlama sorunları azaltır. Esas olarak, her uygulamanın kendi içinde bulunan yansıması kapsayıcılı.

Bazı kuruluşlar mikro (bulut yerel uygulamalar) ekleyerek modernizing devam edecek, ancak diğer birçok kuruluş burada (bulut iyileştirilmiş uygulamaları) durdurur. İçin gerekmeyebilir çünkü Şekil 4-8'de gösterildiği gibi bu kuruluşların mikro mimarileri taşınmaz. Herhangi bir durumda, bunlar zaten kapsayıcıları artı Service Fabric kullanarak, dağıtım, içeren sağlayan bir tam yönetim deneyimi yükseltmeleri avantajları, sürüm oluşturma, alma ve sistem durumu izleme alın.

> ![Kaldırın ve Service Fabric uygulama kaydırma](./media/image8.png)
>
> **Şekil 4-8.** Kaldırın ve Service Fabric uygulama kaydırma

Bir anahtar Service Fabric için var olan kodu yeniden kullanma ve kaldırın ve shift yaklaşımdır. Bu nedenle, geçerli .NET Framework uygulamalarınızın Windows kapsayıcıları kullanarak geçirmek ve bunları Service Fabric dağıtabilirsiniz. Bu, sonuç olarak, yeni mikro ekleyerek modernizing giderek tutmak daha kolay olacaktır.

Service Fabric diğer orchestrators karşılaştırıldığında, Service Fabric Windows tabanlı uygulamalar ve hizmetler çalıştıran en olgun vurgulamak önemlidir. Service Fabric, Windows tabanlı hizmetler ve uygulamalar, Katman 1, kritik ürünler Microsoft'tan yıl de dahil olmak üzere çalıştığı. Windows kapsayıcıları için genel kullanılabilirlik sağlamak için ilk orchestrator oluştu. Diğer, Kubernetes, DC/OS ve Docker Swarm, gibi Linux içinde daha da olgun için Service Fabric Windows tabanlı uygulamalar ve Windows kapsayıcıları daha az olgun ancak kapsayıcılardır.

Service Fabric nihai amacı bir mikro yaklaşım kullanarak uygulamaları oluşturma karmaşıklıkları azaltmaktır. Belirli türdeki maliyetli redesigns önlemek için uygulamalar için bir mikro sonunda istiyorsunuz. Küçük başlayın, gerektiğinde ölçeklendirme, hizmetleri Kaldır, yeni hizmet ekleme ve müşteri ile uygulamanızı geliştirin. Mikro çoğu geliştiriciler için daha erişilebilir yapma çözülecek henüz olan diğer birçok sorunları vardır. Şu anda yalnızca kaldırma ve çalıştığınız uygulamanın Windows kapsayıcılarla kaydırma, ancak gelecekte kapsayıcılarında tabanlı mikro ekleme hakkında düşünüyorum, Service Fabric Lezzetli nokta olmasıdır.

>[!div class="step-by-step"]
[Önceki](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
[sonraki](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
