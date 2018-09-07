---
title: Mimari yaklaşımları - sunucusuz uygulamalar
description: Giriş mimarisi, N katmanlı mimariler için sunucusuz bulut tabanlı kurumsal uygulamalar oluşturmaya yönelik yaklaşıyor.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 21e191f17e7d0b4f2d64454fb14c46a4831a8375
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44084007"
---
# <a name="architecture-approaches"></a>Mimari yaklaşımları

Kurumsal uygulamaları tasarlamak için varolan yaklaşımlara anlama yardımcı tarafından sunucusuz oynadığı rol açıklayın. Birçok yaklaşımlar ve yazılım geliştirme yıllardır içinde gelişerek desenleri vardır ve tüm kendi Artıları ve eksileri vardır. Çoğu durumda, bir çözüm üzerinde tek bir yaklaşım karar gerektirebilir değil, ancak çeşitli yaklaşımlar tümleştirme. Geçiş senaryoları, genellikle bir mimari yaklaşımı, karma bir yaklaşım aracılığıyla başka bir kaydırma içerir.

Bu bölümde, kurumsal uygulamalar için her iki mantıksal ve fiziksel mimari desenleri için genel bir bakış sağlar.

## <a name="architecture-patterns"></a>Mimari desenleri

Modern iş uygulamaları mimarisi desenleri çeşitli izleyin. Bu bölümde genel desenleri araştırma temsil eder. Burada listelenen desenleri mutlaka tüm en iyi değildir, ancak farklı bir yaklaşım gösterilmektedir.

Daha fazla bilgi için [Azure Uygulama Mimarisi Kılavuzu](https://docs.microsoft.com/azure/architecture/guide/).

## <a name="monoliths"></a>Hamleye olanak

Birçok iş uygulaması tek deseni izler. Eski uygulamaları genellikle hamleye olanak uygulanır. Tek düzende, tüm uygulama sorunları tek bir dağıtımda yer alır. Her şeyi veritabanı çağrıları için kullanıcı arabirimi, aynı kod temelinde dahil edilir.

![Tek mimarisi](./media/monolith-architecture.png)

Tek yaklaşım için çeşitli avantajları vardır. Genellikle, tek bir kod tabanının çekmek ve çalışmaya başlamak çok kolaydır. Gelişim süresini daha az olabilir ve test ortamları oluşturmayı sağlayan yeni bir kopya olarak kadar kolaydır. Tek birden çok bileşenler ve uygulamalar dahil etmek için tasarlanmış olabilir.

Ne yazık ki, tek düzen ölçekte bölünme eğilimindedir. Tek yaklaşım ana dezavantajları şunlardır:

* Aynı kod tabanını paralel çalışma zordur.
* Nasıl Önemsiz fark etmeksizin herhangi bir değişiklik, uygulamanın tamamı yeni bir sürümünü gerektirir.
* Potansiyel olarak yeniden düzenleme, uygulamanın tamamını etkiler.
* Genellikle ölçeklendirmek için tek bir çözüm birden çok oluşturmaktır yoğun kaynak tek kopyası.
* Sistemleri genişletin veya diğer sistemlere elde edilen tümleştirme zor olabilir.
* Tüm tek yapılandırmaya gerek nedeniyle test etmek zor olabilir.
* Kod yeniden kullanımını zordur ve genellikle kendi kod kopyaları olan diğer uygulamaları edersiniz.

Birçok işletme, tek uygulamaları geçirme ve aynı anda daha fazla kullanılabilir desenleri için bunları yeniden düzenleme için bir fırsat olarak buluta arayın. Korunan, dağıtılan ve ayrı olarak ölçeği izin vermek üzere tek tek uygulamalar ve bileşenler kesmek için yaygındır.

## <a name="n-layer-applications"></a>N katmanlı uygulamalar

N katmanlı uygulama bölüm belirli katmanlara uygulama mantığı. En yaygın Katmanlar şunlardır:

* Kullanıcı arabirimi
* İş mantığı
* Veri erişimi

Diğer Katmanlar, ara yazılım ve toplu işlem API'si içerebilir. Katmanları mantıksal olduğuna dikkat edin önemlidir. Yalıtılmış olarak geliştirilen olsa da, bunların tümü aynı hedef platformu için dağıtılabilir.

![N katmanlı mimari](./media/n-layer-architecture.png)

N katmanlı yaklaşımın çeşitli avantajları vardır dahil olmak üzere:

* Yeniden düzenleme, bir katman için ayrı tutulur.
* Takımların bağımsız olarak derleme, test, dağıtabilir ve ayrı katmanlar korumak.
* Katmanlar takas edilebilir, UI yerleşiminde değişikliğe gerek kalmadan veri katmanı birden çok veritabanı örneğin erişebilir.

Sunucusuz bir veya daha fazla katmanı uygulamak için kullanılabilir.

## <a name="microservices"></a>Mikro hizmetler

**[Mikro Hizmetler](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/microservices)**  mimarileri içeren ortak özellikleri içerir:

* Uygulamaları birkaç küçük hizmetlerini oluşur.
* Her hizmet kendi işleminde çalışır.
* Hizmetleri iş etki alanı hizalanır.
* Hizmetler, genellikle HTTP aktarım olarak kullanarak basit API'ler üzerinden iletişim kurar.
* Hizmetleri, dağıtılmış ve bağımsız olarak yükseltildi.
* Hizmetleri bir tek veri deposuna bağımlı değildir.
* Sistem hatası düşünülerek tasarlanmıştır ve bile belirli hizmetleri başarısız olduğunda uygulama çalışmaya devam.

Mikro hizmetler, diğer mimari yaklaşımları birbirini dışlayan olması gerekmez. Örneğin, N katmanlı bir mimari, mikro hizmetler için orta katman kullanabilir. Mikro hizmetler çeşitli yollarla, kapsayıcılar için IIS konaklardaki sanal dizinlerden uygulamak mümkündür. Mikro hizmet özelliklerini bunları sunucusuz uygulamalar için özellikle ideal hale getirir.

![Mikro hizmet mimarisi](./media/microservices-architecture.png)

Mikro hizmet mimarileri profesyoneller şunlardır:

* Yeniden düzenleme genellikle tek bir hizmet için ayrı tutulur.
* Hizmetleri birbirinden yükseltilebilir.
* Tek başına hizmetlerinden gereksinimlerini karşılamak için ayarlanabilecek, dayanıklılık ve esneklik.
* Geliştirme paralel olarak birbirinden farklı ekipler ve platformlar arasında gerçekleşebilir.
* Yalıtılmış Hizmetleri için kapsamlı testler yazmak daha kolaydır.

Mikro hizmetler de dahil olmak üzere kendi zorluklar getirir:

* Hangi hizmetlerin kullanılabileceğini ve bunları nasıl belirleme.
* Yaşam döngüsü Hizmetleri yönetme.
* Hizmetleri genel uygulama birbirine nasıl uyduğunu anlama.
* Farklı hizmet arasında yapılan çağrılar tam sistem testi.

Sonuç olarak tüm daha sonra açıklanan avantajları sunucusuz olarak dahil olmak üzere, bu sorunları ele almak için çözümleri vardır.

>[!div class="step-by-step"]
[Önceki](index.md)
[İleri](architecture-deployment-approaches.md)
