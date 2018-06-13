---
title: Bir mikro hizmet Basitleştirilmiş CQRS ve DDD düzenleri uygulama
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Bir mikro hizmet Basitleştirilmiş CQRS ve DDD düzenleri uygulama
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 4e30b4755af001f85649e611c9f1f976ed294cab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33577052"
---
# <a name="applying-simplified-cqrs-and-ddd-patterns-in-a-microservice"></a>Bir mikro hizmet Basitleştirilmiş CQRS ve DDD düzenleri uygulama

CQRS verileri okurken ve yazarken modelleri ayıran bir tasarım örüntüsü ' dir. İlgili dönem [komutu sorgu ayırma (CQS)](https://martinfowler.com/bliki/CommandQuerySeparation.html) Bertrand Meyer tarafından kendi Defteri'nde ilk olarak tanımlandı *nesne yönelimli yazılım oluşturması*. Sistemin işlemleri iki keskin ayrılmış kategorilere bölebilirsiniz temel fikirdir:

-   Sorgular. Bu bir sonuç döndürür ve sistem durumunu değiştirmez ve yan etkileri ücretsizdir.

-   Komutları. Bu bir sistem durumunu değiştirin.

CQS olan basit bir kavram — aynı nesne içinde yöntemlerini hakkındadır sorgular veya komutları bırakılıyor. Her yöntem durumunu döndürür veya durumu, ancak ikisini değiştirdiği. Bile bir tek depo düzeni nesnesi CQS ile uyumlu. CQS temel İlkesi CQRS için kabul edilebilir.

[Komut ve sorgu sorumluluk ayrımı (CQRS)](https://martinfowler.com/bliki/CQRS.html) Greg Young tarafından sunulan ve UDI Dahan ve başkaları tarafından kesinlikle yükseltildi. Daha ayrıntılı rağmen CQS ilkesine temel alır. Komutlar ve olayları artı isteğe bağlı olarak zaman uyumsuz ileti üzerinde dayalı bir desen değerlendirilebilir. Çoğu durumda, okumalar (sorgular) yazma (güncelleştirmeler) için farklı bir fiziksel veritabanı olması gibi daha Gelişmiş senaryolar CQRS ilgilidir. Ayrıca, daha fazla sistem gereksinimleri CQRS sistem uygulayabilir [olay kaynak Hizmeti'nden (ES)](http://codebetter.com/gregyoung/2010/02/20/why-use-event-sourcing/) güncelleştirmeleri veritabanınız için böylece yalnızca depoladığınız olayları geçerli durumu verilerini depolamak yerine etki alanı modeli. Ancak, bu kılavuzda kullanılan yaklaşım değildir; sorguları komutları yalnızca ayırarak oluşur en basit CQRS yaklaşım kullanıyoruz.

CQRS ayırma yönünü bir katmandaki sorgu işlemleri ve başka bir katmana komutlarda gruplandırarak elde edilir. Her katman kendi veri modelindeki (modeli, mutlaka farklı bir veritabanına dediğimiz unutmayın) ve kendi desenleri ve teknolojileri kullanan yerleşik olarak bulunur. Daha da önemlisi, iki katmanlı, aynı katman veya (mikro hizmet sıralama) örnekte olduğu gibi bu kılavuz için kullanılan mikro içinde olabilir. Ya da bunlar kullanılabilir en iyi duruma getirilmiş ve çıkışı ayrı ayrı bir diğer etkilemeden ölçeklendirilmiş böylece bunlar farklı mikro veya işlemler uygulanabilir.

CQRS diğer bağlamlarda var olduğu bir okuma/yazma işlemi için iki nesne sahip olmak anlamına gelir. Daha gelişmiş CQRS belgelerinde öğrenebilirsiniz bir Normalleştirilmemiş okuma veritabanı için nedenleri vardır. Ancak bu yaklaşımı Burada amaç toplamalar gibi DDD düzenleri kısıtlamaları sorgularıyla sınırlama yerine sorgularda daha fazla esnekliğe sahip olduğu kullanıyoruz değil.

Bu tür bir hizmet eShopOnContainers başvuru uygulamasından sıralama mikro örnektir. Bu hizmet üzerinde basitleştirilmiş bir CQRS yaklaşım tabanlı mikro hizmet uygular. Tek bir veri kaynağı veya veritabanı, ancak iki mantıksal modelleri artı DDD desenleri işlem etki alanı için Şekil 9-2'de gösterildiği gibi kullanır.

![](./media/image2.png)

**Şekil 9-2**. Mikro hizmet CQRS ve DDD tabanlı Basitleştirilmiş

Uygulama katmanı Web API olabilir. Burada önemli tasarım en boy mikro hizmet sorgular ve ViewModels (özellikle istemci uygulamaları için oluşturulan veri modelleri) bölündü komutlar, etki alanı modeli ve CQRS desen aşağıdaki işlemleri ' dir. Bu yaklaşım sorguları kısıtlamaları ve sonraki bölümlerde açıklandığı gibi işlemleri ve güncelleştirmeler için anlamlı yalnızca DDD desenleri'ten gelen kısıtlamalarını bağımsız olarak korur.


>[!div class="step-by-step"]
[Önceki] (index.md) [sonraki] (eshoponcontainers-cqrs-bbb-microservice.md)
