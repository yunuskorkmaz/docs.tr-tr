---
title: Dağıtılmış veriler
description: Azure için Cloud Native .NET uygulamaları tasarlama | Bulut Yerel uygulamaları için dağıtılmış veriler
ms.date: 06/30/2019
ms.openlocfilehash: 92086c52b02360e90461aea9ad23a2068224e187
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183135"
---
# <a name="distributed-data-for-cloud-native-apps"></a>Bulutta yerel uygulamalar için dağıtılmış veriler

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Birçok bağımsız mikro hizmetten oluşan, bulut tabanlı bir sistem oluştururken, veri depolama değişikliklerini düşündüğünüz şekilde düşünün.

Geleneksel tek parçalı uygulamalar Şekil 5-1 ' de gösterilen merkezi bir veri deposuna tercih ediyor. 

![Tek monoparçalı veritabanı](./media/single-monolithic-database.png)

**Şekil 5-1**. Tek monoparçalı veritabanı

Önceki şekilde, tüm uygulama bileşenlerinin tek bir ilişkisel veritabanını nasıl tükettiğine göz önünde.

Bu yaklaşımın pek çok avantajı vardır. Verileri birden çok tabloya yaymak kolaydır ve veri tutarlılığı sağlayan [ACID işlemlerini](https://docs.microsoft.com/windows/desktop/cossdk/acid-properties) uygulamak basittir. Her zaman *anında tutarlılık*vardır: tüm veri güncelleştirmelerinizi veya hiçbirini hiç bir şekilde sonlandırın.

Bulut Yerel sistemleri, Şekil 5-2 ' de gösterilen, her mikro hizmetin kendi verilerini sahip olduğu ve kapsülleyen bir veri mimarisini tercih ediyor.

![Mikro hizmetler genelinde birden çok veritabanı](./media/data-across-microservices.png)

**Şekil 5-2**. Mikro hizmetler genelinde birden çok veritabanı

Önceki şekilde, her bir mikro hizmetin BT veri mağazasını nasıl sahip olduğunu ve bu verileri yalnızca ortak API 'sinden dış dünyayı açığa çıkardığını aklınızda saklayın.
 
Bu model, her mikro hizmetin, veri şeması değişikliklerini diğer mikro hizmetlerle koordine etmek zorunda kalmadan bağımsız olarak gelişmesine olanak sağlar. Her mikro hizmet, ihtiyaçlarına en iyi eşleşen veri deposunu (ilişkisel veritabanı, belge veritabanı, anahtar-değer deposu) uygulamak için ücretsizdir. Çalışma zamanında, her mikro hizmet verilerini uygun şekilde ölçeklendirebilir. Bu şekil 5-3 ' de gösterilmiştir:

![Çok yönlü veri kalıcılığı](./media/polyglot-data-persistence.png)

**Şekil 5-3**. Çok yönlü veri kalıcılığı

Önceki şekilde, ürün kataloğu ve Inventory mikro hizmetlerinin ilişkisel veritabanlarını, sıralama mikro hizmetini, bir NoSql belge veritabanını ve bir dış anahtar-değer deposu olan alışveriş sepeti mikro hizmetini benimsediğini not edin. İlişkisel veritabanları karmaşık verilerle mikro hizmetler için uygun olmaya devam ederken, NoSQL veritabanları önemli ölçüde popülerliği kazanmıştır, hızlı arama ve yüksek kullanılabilirlik sağlar. Şeicilerin, veri sınıflarının bir mimarisinden ve ORMs de daha pahalı ve zaman alıcı bir mimariden uzaklaşmasını sağlar.

>[!div class="step-by-step"]
>[Önceki](service-mesh-communication-infrastructure.md)
>[İleri](data-patterns.md)
