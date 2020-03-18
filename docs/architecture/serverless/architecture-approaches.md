---
title: Mimari yaklaşımlar - Sunucusuz uygulamalar
description: N katmanlı mimarilerden sunucusuzlara bulut tabanlı kurumsal uygulamalar oluşturmak için mimari yaklaşımlarına giriş.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 74de96bef48f16ced4adf82855a740aa0afcdf1d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522904"
---
# <a name="architecture-approaches"></a>Mimari yaklaşımları

Kurumsal uygulamaların mimarlanmasına yönelik varolan yaklaşımların anlaşılması, sunucusuzların oynadığı rolün açıklığa kavuşturulmasına yardımcı olur. Yazılım geliştirme onlarca yıl içinde gelişti birçok yaklaşım ve desenler vardır, ve tüm kendi artıları ve eksileri var. Çoğu durumda, nihai çözüm tek bir yaklaşım üzerinde karar içermeyebilir, ancak çeşitli yaklaşımlar entegre edebilir. Geçiş senaryoları genellikle bir mimari yaklaşımdan diğerine hibrit bir yaklaşımla geçiş yapmayı içerir.

Bu bölümde, kurumsal uygulamalar için hem mantıksal hem de fiziksel mimari desenlere genel bir bakış sağlanmıştır.

## <a name="architecture-patterns"></a>Mimari desenleri

Modern iş uygulamaları çeşitli mimari desenleri izler. Bu bölüm, ortak desenlerin bir anketini temsil eder. Burada listelenen desenler mutlaka tüm en iyi uygulamalar değildir, ancak farklı yaklaşımlar göstermektedir.

Daha fazla bilgi için [Azure uygulama mimarisi kılavuzuna](https://docs.microsoft.com/azure/architecture/guide/)bakın.

## <a name="monoliths"></a>Yekpare

Birçok iş uygulamaları monolit desen izleyin. Eski uygulamalar genellikle monolit olarak uygulanır. Monolit desende, tüm uygulama sorunları tek bir dağıtımda bulunur. Kullanıcı arabiriminden veritabanı aramalarına kadar her şey aynı kod tabanına dahildir.

![Monolit mimarisi](./media/monolith-architecture.png)

Monolit yaklaşımın çeşitli avantajları vardır. Genellikle tek bir kod tabanını aşağı çekmek ve çalışmaya başlamak kolaydır. Rampa süresi daha az olabilir ve test ortamları oluşturmak yeni bir kopya sağlamak kadar basittir. Monolit, birden çok bileşen ve uygulama içerecek şekilde tasarlanabilir.

Ne yazık ki, monolit desen ölçekte yıkmak eğilimindedir. Monolit yaklaşımın başlıca dezavantajları şunlardır:

- Aynı kod tabanında paralel olarak çalışmak zordur.
- Herhangi bir değişiklik, ne kadar önemsiz olursa olsun, tüm uygulamanın yeni bir sürümünü dağıtmayı gerektirir.
- Yeniden düzenleme, tüm uygulamayı etkileyebilecek şekilde etkiler.
- Genellikle ölçeklendirmek için tek çözüm monolitin birden çok, kaynak yoğun kopyasını oluşturmaktır.
- Sistemler genişledikçe veya diğer sistemler elde edilsinkçe, tümleştirme zor olabilir.
- Tüm monoliti yapılandırma gereksinimi nedeniyle test etmek zor olabilir.
- Kod yeniden kullanımı zordur ve genellikle diğer uygulamalar kendi kod kopyalarına sahip olmak zorunda kalırlar.

Birçok işletme bulutu monolit uygulamaları geçirmek ve aynı zamanda bunları daha kullanılabilir desenlere yeniden düzenleme fırsatı olarak görmek. Ayrı ayrı bakımı, dağıtılması ve ölçeklendirilmesine izin vermek için tek tek uygulamaları ve bileşenleri ayırmak yaygındır.

## <a name="n-layer-applications"></a>N-Katman uygulamaları

N-katmanlı uygulama bölüm uygulama mantığı belirli katmanlara. En yaygın katmanlar şunlardır:

- Kullanıcı arabirimi
- İş mantığı
- Veri erişimi

Diğer katmanlar ara yazılım, toplu işişleme ve API içerebilir. Katmanların mantıklı olduğunu unutmayın. Her ne kadar izole edilmiş olsalar da, hepsi aynı hedef platforma konuşlandırılabilir.

![N-Layer mimarisi](./media/n-layer-architecture.png)

N-Layer yaklaşımının çeşitli avantajları vardır:

- Yeniden düzenleme bir katmana izole edilmiştir.
- Takımlar ayrı katmanlar oluşturabilir, sınayabilir, dağıtabilir ve koruyabilir.
- Katmanlar değiştirilebilir, örneğin veri katmanı UI katmanında değişiklik gerektirmeden birden çok veritabanına erişebilir.

Sunucusuz bir veya daha fazla katmanları uygulamak için kullanılabilir.

## <a name="microservices"></a>Mikro hizmetler

**[Microservices](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/microservices)** mimarileri şunlardır:

- Uygulamalar birkaç küçük hizmetlerden oluşur.
- Her hizmet kendi sürecinde çalışır.
- Hizmetler iş alanları etrafında hizalanır.
- Hizmetler genellikle taşıma olarak HTTP kullanarak hafif API'ler üzerinden iletişim kurar.
- Hizmetler dağıtılabilir ve bağımsız olarak yükseltilebilir.
- Hizmetler tek bir veri deposuna bağlı değildir.
- Sistem hata göz önünde bulundurularak tasarlanmıştır ve uygulama bazı hizmetler başarısız olsa bile yine de çalışabilir.

Mikro hizmetler diğer mimari yaklaşımlara özel olmak zorunda değildir. Örneğin, Bir N-Tier mimarisi orta katman için mikro hizmetleri kullanabilir. IIS ana bilgisayarlarındaki sanal dizinlerden konteynerlere kadar çeşitli şekillerde mikro hizmetler uygulamak da mümkündür. Mikro hizmetlerin özellikleri, bunları özellikle sunucusuz uygulamalar için ideal kalmaktadır.

![Mikro hizmetler mimarisi](./media/microservices-architecture.png)

Mikrohizmet mimarilerinin artıları şunlardır:

- Yeniden düzenleme genellikle tek bir hizmete yalıtılır.
- Hizmetler birbirinden bağımsız olarak yükseltilebilir.
- Esneklik ve esneklik bireysel hizmetlerin taleplerine göre ayarlanabilir.
- Geliştirme birbirinden farklı takımlar ve platformlar arasında paralel olarak gerçekleşebilir.
- Yalıtılmış hizmetler için kapsamlı testler yazmak daha kolaydır.

Mikro hizmetler, şunları dahil olmak üzere kendi zorluklarıyla birlikte gelir:

- Hangi hizmetlerin kullanılabilip çağırılabildiğini belirleme.
- Hizmetlerin yaşam döngüsünü yönetme.
- Hizmetlerin genel uygulamada nasıl bir araya geldiğini anlama.
- Birbirinden farklı hizmetler arasında yapılan aramaların tam sistem testi.

Sonuç olarak, daha sonra tartışılan sunucusuzların avantajlarından yararlanmak da dahil olmak üzere tüm bu zorlukları ele alacak çözümler vardır.

>[!div class="step-by-step"]
>[Önceki](index.md)
>[Sonraki](architecture-deployment-approaches.md)
