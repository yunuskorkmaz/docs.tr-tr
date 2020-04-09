---
title: Bulutta yerel uygulamalara giriş
description: Bulut tabanlı bilgi işlem hakkında bilgi edinin
author: robvet
ms.date: 08/26/2019
ms.openlocfilehash: c9ffd34ec3deb04abddbbf85a9e5a6ed2b57c8f9
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989057"
---
# <a name="introduction-to-cloud-native-applications"></a>Bulutta yerel uygulamalara giriş

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Başka bir gün, ofiste, "bir sonraki büyük şey" üzerinde çalışmak.

Cep telefonun çalıyor. Bu senin dost iş verenin, seni günde iki kez yeni işlerle arayan kişi.

Ama bu sefer farklı: Start-up, özkaynak, ve finansman bol.

Bulutve en ileri teknolojiden bahsetmek sizi uçurumun kenarına iter.

Hızlı ileri birkaç hafta ve şimdi büyük bir e-ticaret uygulaması mimarı bir tasarım oturumunda yeni bir çalışan konum. Diğer önde gelen e-ticaret siteleri ile tamamlamak için gidiyoruz.

Nasıl inşa edeceğiz?

Son 15 yılın rehberliğini izlerseniz, büyük olasılıkla Şekil 1.1'de gösterilen sistemi oluşturursunuz.

![Geleneksel monolitik tasarım](./media/monolithic-design.png)

**Şekil 1-1**. Geleneksel monolitik tasarım

Tüm etki alanı mantığınızı içeren büyük bir çekirdek uygulama oluşturuyorsunuz. Kimlik, Katalog, Sipariş ve daha fazlası gibi modülleri içerir. Çekirdek uygulama büyük bir ilişkisel veritabanı ile iletişim kurar. Çekirdek, html arabirimi üzerinden işlevselliği ortaya çıkarır.

Tebrikler!  Az önce yekpare bir uygulama yarattın.

Her şey kötü değil. Monolitler bazı belirgin avantajlar sunar. Örneğin, onlar için basit konum ...

- derleme
- test
- Dağıtmak
- troubleshoot
- scale

Bugün var olan birçok başarılı uygulama monolit olarak oluşturuldu. Uygulama bir hit ve daha fazla işlevsellik ekleyerek, yineleme sonra yineleme gelişmeye devam ediyor.

Bir noktada, ancak, rahatsız hissetmeye başlar. Kendinizi uygulamanın kontrolünü kaybederken buluyorsunuz. Zaman geçtikçe, duygu daha yoğun hale gelir ve sonunda **Korku Döngüsü**olarak bilinen bir devlet girin.

- Uygulama o kadar karmaşık hale geldi ki tek bir kişi bile anlamıyor.
- Değişiklik yapmaktan korkuyorsunuz - her değişikliğin istenmeyen ve pahalı yan etkileri vardır.
- Yeni özellikler/düzeltmeler zor, zaman alıcı ve uygulanması pahalı hale gelir.
- Her sürüm ne kadar küçük olabilir, tüm uygulamanın tam olarak dağıtılmasını gerektirir.
- Kararsız bir bileşen tüm sistemi çökertebilir.
- Yeni teknolojiler ve çerçeveler bir seçenek değildir.
- Çevik teslimat metodolojilerini uygulamak zordur.
- Mimari erozyon, kod tabanının hiç bitmeyen "özel durumlar" ile bozulmasıyla ortaya çıkmaktadır.
- Danışmanlar sana yeniden yazmanı söylüyor.

Birçok kuruluş, sistemler oluşturmak için bulut ait bir yaklaşım benimseyerek yekpare korku döngüsünü ele alamışlardır. Şekil 1-2, bulut-doğal teknikler ve uygulamaları uygulayarak inşa edilen sistemin aynısını gösterir.

![Bulut-Yerli Tasarım](./media/cloud-native-design.png)

**Şekil 1-2**. Buluta özgü tasarım

Uygulamanın küçük yalıtılmış mikro hizmetler kümesi nde nasıl ayrıştırıldığını unutmayın. Her hizmet kendi kendine yeten ve kendi kodunu, verilerini ve bağımlılıklarını kapsüller. Her biri bir yazılım kabında dağıtılır ve bir konteyner orkestratör tarafından yönetilir. Büyük bir ilişkisel veritabanı yerine, her hizmet, veri gereksinimlerine bağlı olarak değişen türü kendi veri deposuna sahip olur. Bazı hizmetlerin ilişkisel bir veritabanına, diğerinin ise NoSQL veritabanlarına nasıl bağlı olduğunu unutmayın. Bir hizmet durumunu dağıtılmış bir önbellekte depolar. Temel arka uç hizmetlerine trafiği yönlendirmekten ve birçok çapraz kesme endişesini zorlamaktan sorumlu bir API Ağ Geçidi hizmeti aracılığıyla tüm trafik yollarının nasıl olduğunu unutmayın. En önemlisi, uygulama modern bulut platformlarında bulunan ölçeklenebilirlik ve esneklik özelliklerinden tam olarak yararlanır.

### <a name="cloud-native-computing"></a>Bulut ait bilgi işlem

Hmm... "Cloud*Native"* terimini kullandık. İlk olarak "Bu tam olarak ne anlama geliyor?" diye düşündün. Başka bir sanayi buzzword yazılım satıcıları tarafından daha fazla şeyler pazarlamak için uydurulmuş?"

Neyse ki çok farklı ve umarım bu kitap sizi ikna yardımcı olacaktır.

Kısa bir süre içinde, bulut yerli yazılım sektöründe bir itici eğilim haline gelmiştir. Bu, büyük, karmaşık sistemler oluşturmanın yeni bir yoludur, modern yazılım geliştirme uygulamalarından, teknolojilerinden ve bulut altyapısından tam olarak yararlanan bir yaklaşımdır. Yaklaşım, sistemleri tasarlama, uygulama, dağıtma ve operasyonelleştirme şeklinizi değiştirir.

Bizim sanayi sürücüler sürekli yutturmaca aksine, bulut yerli "*gerçek*". Bulut [Yerli Bilgi İşlem Vakfı'nı](https://www.cncf.io/) (CNCF), teknoloji ve bulut yığınları arasında bulut ayarı bilgi işlemin her yerde olmasını sağlamak için 300'den fazla büyük şirketten oluşan bir konsorsiyumu düşünün. En etkili açık kaynak gruplarından biri olarak, GitHub'daki en hızlı büyüyen açık kaynak projelerinin çoğuna ev sahipliği yapmaktadır. Onlar [Kubernetes,](https://kubernetes.io/) [Prometheus,](https://prometheus.io/) [Helm,](https://helm.sh/) [Elçi](https://www.envoyproxy.io/)ve [gRPC](https://grpc.io/)gibi projeler içerir.

CNCF açık kaynak ve satıcı tarafsızlığı bir ekosistem teşvik eder. Bu ipucunun ardından, teknoloji agnostik olan bulut-yerel ilkeler, desenler ve en iyi uygulamaları salıyoruz. Aynı zamanda, buluta özgü sistemler oluşturmak için Microsoft Azure bulutunda bulunan hizmetleri ve altyapıyı tartışıyoruz.

Peki, Cloud Native tam olarak nedir? Arkanıza yat, rahatla ve bu yeni dünyayı keşfetmenize yardım edelim.

>[!div class="step-by-step"]
>[Önceki](index.md)
>[Sonraki](definition.md)
