---
title: "Service Fabric Windows kapsayıcıları dağıtma zamanı"
description: "Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Service Fabric Windows kapsayıcıları dağıtma zamanı"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.prod: .net
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 3698643238cd43ec187c269a3814857b1f6fb054
ms.sourcegitcommit: d3cfda0943364aaf6ccd574f55f584576c8a4fee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2018
---
# <a name="when-to-deploy-windows-containers-to-service-fabric"></a>Service Fabric Windows kapsayıcıları dağıtma zamanı

Windows kapsayıcılarında tabanlı uygulamaları hızlı bir şekilde daha uzakta Iaas Vm'lerden taşıma platformları kullanmanız gerekir. Bu geliştirilmiş otomatik ölçeklenebilirlik ve yüksek ölçeklenebilirlik içindir ve tam yönetim deneyiminde dağıtımlar için önemli geliştirmeler kazanmak için yükseltir, sürüm oluşturma, alma ve sistem durumu izleme. Azure Service Fabric, Microsoft Azure bulut, aynı zamanda şirket içi veya başka bir bulutta bile kullanılabilir orchestrator ile bu hedefleri elde edebilirsiniz.

Birçok kuruluş kaldırma ve iki nedenden dolayı kapsayıcılara tek yapılı uygulamalarınız kaydırma:

-   Maliyet düşürülmesi, ya da birleştirme ve temizleme mevcut donanım veya yüksek yoğunluk çalışan uygulamalar nedeniyle.

-   Geliştirme ve işlemler arasında tutarlı bir dağıtım sözleşme.

Maliyet azaltması sürdürdüğünü anlaşılabilir ve tüm organizasyonlar bu hedefe birleştirme olasıdır. Tutarlı bir dağıtım, değerlendirilecek daha zor, ancak aynı derecede önemli olarak gelir. Tutarlı bir dağıtım sözleşme geliştiriciler bunları uygun teknolojiyi kullanmak üzere seçmek ücretsiz ve işlemler ekibinin uygulamaları dağıtmak ve yönetmek için tek bir yolu alır söyler. Bu anlaşma birçok farklı teknolojiler karmaşıklık ile ilgili işlemleri olması ya da yalnızca belirli teknolojileri ile geliştiricilerin zorlama sorunları azaltır. Esas olarak, her uygulamanın kendi içinde bulunan yansıması kapsayıcılı.

Bazı kuruluşlar, mikro (bulut optimize ve bulut-yerel uygulamalar) ekleyerek modernizing devam eder. Birçok kuruluş, burada (bulut DevOps hazır) durdurur. İçin gerekmeyebilir çünkü Şekil 4-8'de gösterildiği gibi bu kuruluşların mikro mimarileri taşınmaz. Herhangi bir durumda, bunlar zaten kapsayıcıları artı Service Fabric kullanarak, dağıtım, içeren sağlayan bir tam yönetim deneyimi yükseltmeleri avantajları, sürüm oluşturma, alma ve sistem durumu izleme alın.

> ![Kaldırın ve Service Fabric uygulama kaydırma](./media/image8.png)
>
> **Şekil 4-8.** Kaldırın ve Service Fabric uygulama kaydırma

Bir anahtar Service Fabric için var olan kodu yeniden kullanma ve yalnızca kaldırın ve shift yaklaşımdır. Bu nedenle, geçerli .NET Framework uygulamalarınızın Windows kapsayıcıları kullanarak geçirmek ve bunları Service Fabric dağıtabilirsiniz. Bu, sonuç olarak, yeni mikro ekleyerek modernizing giderek tutmak daha kolay olacaktır.

Service Fabric diğer orchestrators karşılaştırıldığında, Service Fabric Windows tabanlı uygulamalar ve hizmetler çalıştıran en çok olgun vurgulamak önemlidir. Service Fabric, Windows tabanlı hizmetler ve uygulamalar, Microsoft, Katman 1, kritik ürünlerinden yıldır dahil olmak üzere çalıştığı. Windows kapsayıcıları (Mayıs 2017) için genel kullanılabilirlik sağlamak için ilk orchestrator oluştu. Diğer, Kubernetes, DC/OS ve Docker Swarm, gibi Linux içinde daha da olgun için Service Fabric Windows tabanlı uygulamalar ve Windows kapsayıcıları daha az olgun ancak kapsayıcılardır.

Service Fabric nihai amacı bir mikro yaklaşım kullanarak uygulamaları oluşturma karmaşıklıkları azaltmaktır. Sonunda maliyetli redesigns önlemek için uygulama türlerini belirli olmasını istediğiniz budur. Küçük başlayın, gerektiğinde ölçeklendirme, hizmetleri Kaldır, yeni hizmet ekleme ve müşteri ile uygulamanızı geliştirin. Mikro çoğu geliştiriciler için daha erişilebilir yapma çözülecek henüz olan diğer birçok sorunlar olduğunu biliyoruz. Şu anda yalnızca kaldırma ve çalıştığınız uygulamanın Windows kapsayıcılarla kaydırma, ancak gelecekte kapsayıcılarında tabanlı mikro ekleme hakkında düşünüyorum, Service Fabric Lezzetli nokta olmasıdır.

>[!div class="step-by-step"]
[Önceki](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
[sonraki](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
