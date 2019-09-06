---
title: Bir mikro hizmete CQRS ve DDD desenlerini uygulama
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | CQRS ve DDD desenleri arasındaki genel ilişkiyi anlayın.
ms.date: 10/08/2018
ms.openlocfilehash: 36bffce37176aed6c7d9daea7f2995952b58e895
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296003"
---
# <a name="apply-simplified-cqrs-and-ddd-patterns-in-a-microservice"></a>Mikro hizmette Basitleştirilmiş CQRS ve DDD desenleri uygulama

CQRS, verileri okuma ve yazma modellerini ayıran mimari bir modeldir. İlgili terim [komut sorgu ayrımı (CQS)](https://martinfowler.com/bliki/CommandQuerySeparation.html) başlangıçta, kitap *nesne yönelimli yazılım oluşturma*bölümünde bertrve Meyer tarafından tanımlanmıştır. Temel düşünce, bir sistemin işlemlerini iki keskin ayrı kategoriye bölememektir:

- Lardır. Bu bir sonuç döndürür ve sistemin durumunu değiştirmez ve yan etkileri ücretsizdir.

- Komut. Bu, bir sistemin durumunu değiştirir.

CQS basit bir kavramdır; aynı nesne içindeki Yöntemler ya da komutlar. Her yöntem durum döndürür veya durumu değiştirmez, ancak ikisini birden etmez. Tek bir depo deseninin bir nesnesi de CQS ile uyumlu olabilir. CQS 'ler, CQRS için temel bir ilke olarak düşünülebilir.

[Komut ve sorgu sorumluluklarının ayrılığı (CQRS)](https://martinfowler.com/bliki/CQRS.html) , Greg başak tarafından sunulmuştur ve UDI Dahan ve diğerleri tarafından güçlü bir şekilde yükseltildi. Daha ayrıntılı olsa da, CQS ilkesini temel alır. Komutların ve olayların yanı sıra zaman uyumsuz iletilerde isteğe bağlı olarak bir model olarak düşünülebilir. Birçok durumda, CQRS, yazma (güncelleştirme) için farklı bir fiziksel veritabanı okuma (sorgular) gibi daha gelişmiş senaryolar ile ilgilidir. Üstelik, daha gelişmiş bir CQRS sistemi, güncelleştirmeler veritabanınız için [olay kaynağını (es)](https://martinfowler.com/eaaDev/EventSourcing.html) uygulayabilir, bu nedenle olayları yalnızca geçerli durum verilerini depolamak yerine etki alanı modelinde depolarsınız. Ancak, bu kılavuzda kullanılan yaklaşım değildir; yalnızca komutlardan oluşan sorguları ayıran en basit CQRS yaklaşımını kullanıyoruz.

CQRS 'nin ayrım yönü, sorgu işlemlerini bir katmanda ve komutları başka bir katmanda gruplandırarak elde edilir. Her katmanın kendi veri modeli vardır (model, farklı bir veritabanı olmak üzere değil) ve kendi desen ve teknolojilerin birleşimi kullanılarak oluşturulmuştur. Daha da önemlisi, bu kılavuz için kullanılan örnekte olduğu gibi iki katman aynı katmanda veya mikro hizmette olabilir (sıralama mikro hizmeti). Ya da farklı mikro hizmetlere veya süreçlere uygulanabilmeniz için, bunların bir diğeri etkilenmeden ayrı olarak iyileştirilebilir ve ölçeklenmesini sağlayabilirsiniz.

CQRS, diğer bağlamlarda bir okuma/yazma işlemi için iki nesneye sahip olduğu anlamına gelir. Daha gelişmiş CQRS belgeleriyle ilgili bilgi edinmek için, daha fazla sayıda okuma veritabanına sahip olma nedenleri vardır. Ancak bu yaklaşımı burada kullandığımızda, hedefin toplamalar gibi DDD desenlerinden gelen sorguları sınırlamak yerine sorgularda daha fazla esneklik elde eteceğiz.

Bu tür bir hizmet örneği, eShopOnContainers başvuru uygulamasından sipariş eden mikro hizmettir. Bu hizmet, Basitleştirilmiş bir CQRS yaklaşımını temel alan bir mikro hizmet uygular. Tek bir veri kaynağını veya veritabanını kullanır, ancak Şekil 7-2 ' de gösterildiği gibi, işlem etki alanı için iki mantıksal model ve ggg desenleri.

![Mantıksal sıralama mikro hizmeti, aynı Docker konağında olabilen veya bulunmayan sıralama veritabanını içerir. Veritabanının aynı Docker ana bilgisayarında olması, geliştirme için iyi, ancak üretim için değil.](./media/image2.png)

**Şekil 7-2**. Basitleştirilmiş CQRS ve DDD tabanlı mikro hizmet

Uygulama katmanı Web API 'SI olabilir. Buradaki önemli tasarım, mikro hizmetin sorguları ve Viewmodellerini (istemci uygulamalar için özel olarak oluşturulan veri modelleri), CQRS deseninin altındaki komutlardan, etki alanı modelinden ve işlemlerden ayırmıştır. Bu yaklaşım, sonraki bölümlerde açıklandığı gibi, yalnızca işlemler ve güncelleştirmeler için anlamlı olan DDD desenlerinden gelen kısıtlamaların ve kısıtlamalardan bağımsız olarak sorguları korur.

## <a name="additional-resources"></a>Ek kaynaklar

- **Greg başak. Olay kaynağını alınmış bir sistemde** sürüm oluşturma (çevrimiçi e-kitabı okumak için ücretsiz) \
   <https://leanpub.com/esversioning/read>

>[!div class="step-by-step"]
>[Önceki](index.md)İleri
>[](eshoponcontainers-cqrs-ddd-microservice.md)
