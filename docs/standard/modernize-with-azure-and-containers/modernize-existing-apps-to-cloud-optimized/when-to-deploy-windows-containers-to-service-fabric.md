---
title: Service Fabric’e Windows Kapsayıcıları ne zaman dağıtılmalıdır?
description: Azure Bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernleştirme | Service fabric'e Windows kapsayıcıları ne zaman
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/30/2018
ms.openlocfilehash: cf9f206852a483dbc391c4541762b885a0ba9660
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625649"
---
# <a name="when-to-deploy-windows-containers-to-service-fabric"></a>Service Fabric’e Windows Kapsayıcıları ne zaman dağıtılmalıdır?

Windows kapsayıcılarında tabanlı uygulamaları hızlı bir şekilde daha Iaas sanal makinelerinden taşımasına platformları kullanmanız gerekir. Geliştirilmiş otomatik ölçeklenebilirlik ve yüksek ölçeklenebilirlik için budur ve tam yönetim deneyiminde dağıtımlar için önemli geliştirmeler elde etmek için yükseltmeleri, sürüm oluşturma, geri alma işlemleri ve sistem durumu izleme. ' De Microsoft Azure bulut, şirket içi ya da başka bir bulutta kullanılabilir Azure Service Fabric, orchestrator ile bu hedeflere elde edebilirsiniz.

Birçok kuruluşun kaldırarak ve kapsayıcıları tek parçalı uygulamalarla mevcut iki nedenden dolayı kaydırma:

- Maliyet indirimleri, birleştirme ve temizleme mevcut donanım veya daha yüksek yoğunlukta çalışan uygulamaların nedeniyle.

- Geliştirme ve operasyon arasında tutarlı dağıtım sözleşme.

Maliyet indirimleri sürdürdüğünü anlaşılır ve tüm kuruluşların bu hedefe birleştirme izleme olasıdır. Tutarlı dağıtım, değerlendirmek için daha zor olduğu halde önemli olarak eşit olduğu. Geliştiriciler, bunları uygun teknolojiyi kullanmayı tercih ücretsizdir ve operasyon ekibinin uygulamaları dağıtmak ve yönetmek için tek bir yol alır tutarlı dağıtım sözleşme diyor. İşbu sözleşme işlemlerinin karmaşıklığını birçok farklı teknoloji ile uğraşmak zorunda ya da yalnızca belirli teknolojileri ile çalışmak için geliştiricilerin zorlama sorunları azaltır. Esas olarak, her uygulama kendi içinde yansıması kapsayıcıya alınmış.

Bazı kuruluşlar, mikro hizmetler (bulutta çalışan uygulamalar) ekleyerek modernleştirme devam eder ancak diğer pek çok kuruluş (uygulamaları bulut için iyileştirilmiş) burada durabilir. Şekil 4-8'de gösterildiği gibi bu kuruluşların, bunlar gerekmez çünkü mikro hizmet mimarileri taşınmaz. Herhangi bir durumda, bunlar zaten yanı sıra Service Fabric kapsayıcıları kullanarak, dağıtım, içeren tam yönetim sağlayan bir deneyimi yükseltme avantajları, sürüm oluşturma, geri alma işlemleri ve sistem durumu izleme alırsınız.

> ![Lift- and -shift Service Fabric uygulama](./media/image8.png)
>
> **Şekil 4-8.** Lift- and -shift Service Fabric uygulama

Bir anahtar Service Fabric için mevcut kodu yeniden kullanma ve kaldırma ve kaydırma yaklaşımdır. Bu nedenle, Windows kapsayıcıları kullanarak geçerli .NET Framework uygulamalarınızı geçirin ve bunları Service Fabric'e dağıtma. Bu, sonuç olarak, yeni mikro hizmetler ekleyerek modernleştirme giderek korumak daha kolay olacaktır.

Service Fabric için diğer düzenleyiciler karşılaştırılırken, Service Fabric Windows tabanlı uygulamaları ve Hizmetleri çalıştıran en olgun sahip olduğunu vurgulamak önemlidir. Service Fabric Windows tabanlı hizmetlerin ve uygulamaların yıllık Katman-1, görev açısından kritik Microsoft ürünlerinden dahil olmak üzere çalışıyor. Windows kapsayıcıları için genel kullanılabilirlik sağlamak için ilk orchestrator olduğu. Kubernetes, DC/OS ve Docker Swarm, gibi diğer kapsayıcılar, Linux fazla olgun için Service Fabric Windows tabanlı uygulamalar ve Windows kapsayıcıları'den az olgun ancak.

Service Fabric nihai amacı bir mikro hizmet yaklaşımı kullanarak uygulamaları oluşturma karmaşıklıkları azaltmaktır. Sonuçta bir mikro hizmetler belirli maliyetli yönelik çalışmalarımızı önlemek için uygulama türleri için kullanmanız gerekir. Küçükten başlayabilir, gerektiğinde ölçeklendirin, hizmetleri kullanımdan, yeni hizmetler ekleyin ve müşteri ile uygulamanızı geliştirmek. Henüz mikro hizmetler Çoğu geliştirici için daha erişilebilir hale getirmek için çözülmesi gereken birçok diğer sorunlar vardır. Şu anda yalnızca kaldırma ve kaydırma Windows kapsayıcıları ile bir uygulama, ancak gelecekte kapsayıcılarında tabanlı mikro Hizmetleri ekleme hakkında düşünmek, Service Fabric tatlı nokta olmasıdır.

>[!div class="step-by-step"]
>[Önceki](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
>[İleri](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)