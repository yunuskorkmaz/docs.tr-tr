---
title: Mimari Yaklaşımlar-sunucusuz uygulamalar
description: N katmanlı mimarilerin sunucusuz 'e kadar bulut tabanlı kurumsal uygulamalar oluşturmaya yönelik mimariye bir giriş.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 74de96bef48f16ced4adf82855a740aa0afcdf1d
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72522904"
---
# <a name="architecture-approaches"></a>Mimari yaklaşımları

Kurumsal uygulamaları mimarmaya yönelik mevcut yaklaşımların anlaşılması sunucusuz tarafından yürütülen rolü açıklığa kavuşturmaya yardımcı olur. Yazılım geliştirme ve tüm uzmanlarının kendi uzmanlarına ve dezavantajlarına sahip birçok yaklaşım ve desen vardır. Çoğu durumda, en son çözüm tek bir yaklaşım üzerinde karar vermeyebilir ancak çeşitli yaklaşımları tümleştirebilir. Geçiş senaryoları genellikle bir mimarinin bir karma yaklaşım aracılığıyla bir mimariden diğerine kaydırılmasıyla ilgilidir.

Bu bölümde, kurumsal uygulamalar için hem mantıksal hem de fiziksel mimari desenlerine genel bir bakış sağlanmaktadır.

## <a name="architecture-patterns"></a>Mimari desenleri

Modern iş uygulamaları çeşitli mimari desenlerini izler. Bu bölüm ortak desenlerin bir anketini temsil eder. Burada listelenen desenler tüm en iyi uygulamalar değildir, ancak farklı yaklaşımlar gösterir.

Daha fazla bilgi için bkz. [Azure Uygulama Mimarisi Kılavuzu](https://docs.microsoft.com/azure/architecture/guide/).

## <a name="monoliths"></a>Tek tek

Birçok iş uygulaması tek bir düzende izler. Eski uygulamalar genellikle tek tek olarak uygulanır. Tek bir düzende, tüm uygulama kaygıları tek bir dağıtımda bulunur. Kullanıcı arabiriminden veritabanı çağrılarına olan her şey aynı kod tabanına dahildir.

![Monolith mimarisi](./media/monolith-architecture.png)

Tek tek yaklaşımın çeşitli avantajları vardır. Tek bir kod temelini çekmek ve çalışmaya başlamak genellikle kolaydır. Artırma süresi daha az olabilir ve test ortamları oluşturmak, yeni bir kopya sağlamak kadar basittir. MONOLITH birden çok bileşeni ve uygulamayı kapsayacak şekilde tasarlanmış olabilir.

Ne yazık ki, tek bir model ölçeklendirmeye göre daha fazla eğilimi gösterir. Tek tek yaklaşımın önemli dezavantajları şunlardır:

- Aynı kod tabanında paralel çalışmayı zorlaştırıyor.
- Tüm değişiklikler, ne kadar önemsiz olsun, tüm uygulamanın yeni bir sürümünü dağıtmanız gerekir.
- Yeniden düzenleme büyük olasılıkla uygulamanın tamamını etkiler.
- Genellikle ölçeklendirmeye yönelik tek çözüm, tek başına birden çok, yoğun kaynak yoğunluklu kopya oluşturmaktır.
- Sistemler Genişlemeden veya diğer sistemler alındığından, tümleştirme zor olabilir.
- Tek bir tam yapılandırma gereksiniminden dolayı test edilmesi zor olabilir.
- Kod yeniden kullanımı zor ve genellikle diğer uygulamalar kendi kod kopyalarına sahip olur.

Birçok işletme, tek bir uygulamayı geçirme fırsatı olarak buluta bakar ve aynı zamanda bunları daha kullanılabilir desenlere yeniden düzenleyin. Ayrı ayrı uygulamaları ve bileşenleri, bunların korunmasını, dağıtılmasını ve ayrı olarak ölçeklendirilmesine olanak tanımak için yaygın olarak kullanılır.

## <a name="n-layer-applications"></a>N katmanlı uygulamalar

N katmanlı uygulama bölümü uygulama mantığını belirli katmanlara dönüştürür. En yaygın katmanlar şunlardır:

- Kullanıcı arabirimi
- İş mantığı
- Veri erişimi

Diğer katmanlar, ara yazılım, toplu işlem ve API içerebilir. Katmanların mantıklı olduğunu unutmamak önemlidir. Yalıtılmış olarak geliştirilse de, hepsi aynı hedef platforma dağıtılabilir.

![N katmanlı mimari](./media/n-layer-architecture.png)

N katmanlı yaklaşımda aşağıdakiler de dahil olmak üzere birkaç avantaj vardır:

- Yeniden düzenleme bir katmana yalıtılmış.
- Takımlar bağımsız olarak ayrı katmanları oluşturabilir, test edebilir, dağıtabilir ve koruyabilir.
- Katmanlar dışarı değiştirilebilir, örneğin veri katmanı, Kullanıcı arabirimi katmanında değişiklik gerektirmeden birden çok veritabanına erişebilir.

Sunucusuz, bir veya daha fazla katmanı uygulamak için kullanılabilir.

## <a name="microservices"></a>Mikro hizmetler

**[Mikro hizmet](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/microservices)** mimarileri, aşağıdakiler dahil olmak üzere ortak özellikler içerir:

- Uygulamalar çeşitli küçük hizmetlerden oluşur.
- Her hizmet kendi sürecinde çalışır.
- Hizmetler, iş etki alanları etrafında hizalanır.
- Hizmetler, genellikle aktarım olarak HTTP kullanarak basit API 'Ler üzerinden iletişim kurar.
- Hizmetler bağımsız olarak dağıtılabilir ve yükseltilebilir.
- Hizmetler tek bir veri deposuna bağımlı değil.
- Sistem, sorun göz önünde bulundurularak tasarlanmıştır ve bazı hizmetler başarısız olduğunda bile uygulama çalışmaya devam edebilir.

Mikro hizmetlerin diğer mimari yaklaşımlar için birbirini dışlamalı olması gerekmez. Örneğin, N katmanlı bir mimaride, orta katman için mikro hizmetler kullanılabilir. Mikro Hizmetleri, IIS konaklarındaki sanal dizinlerden kapsayıcılara çok çeşitli yollarla uygulamak da mümkündür. Mikro hizmetlerin özellikleri, özellikle sunucusuz uygulamalar için idealdir.

![Mikro hizmetler mimarisi](./media/microservices-architecture.png)

Mikro hizmet mimarilerinin uzmanları şunlardır:

- Yeniden düzenleme, genellikle tek bir hizmet olarak yalıtılır.
- Hizmetler birbirinden bağımsız olarak yükseltilebilir.
- Dayanıklılık ve esneklik, bireysel hizmet taleplerine ayarlanabilir.
- Geliştirme, farklı ekipler ve platformlar arasında paralel olarak gerçekleşebilir.
- Yalıtılmış hizmetler için kapsamlı testler yazmak daha kolay.

Mikro hizmetler aşağıdakiler dahil olmak üzere kendi güçlüklarıyla birlikte gelir:

- Hangi hizmetlerin kullanılabilir olduğunu ve bunların nasıl çağrılacağını belirleme.
- Hizmet yaşam döngüsünü yönetme.
- Hizmetlerin genel uygulamada nasıl bir araya uyduğunu anlama.
- Farklı hizmetler genelinde yapılan çağrıların tam sistem testi.

Son olarak, daha sonra ele alınan sunucusuz avantajlarına dokunma dahil olmak üzere tüm bu zorlukları ele alan çözümler vardır.

>[!div class="step-by-step"]
>[Önceki](index.md)
>[İleri](architecture-deployment-approaches.md)
