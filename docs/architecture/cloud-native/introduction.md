---
title: Bulutta yerel uygulamalara giriş
description: Bulutta yerel bilgi işlem hakkında bilgi edinin
author: robvet
ms.date: 08/26/2019
ms.openlocfilehash: a99e4b5599efee8b171c48a5b17e75b9e6cd63ca
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182855"
---
# <a name="introduction-to-cloud-native-applications"></a>Bulutta yerel uygulamalara giriş

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Diğer bir gün, ofiste "bir sonraki büyük şey" üzerinde çalışıyor.

Cellphone halkaları. Bu, size, yeni işler hakkında günde iki kez çağrı yapan kolay bir çalışmadır.

Ancak bu süre farklıdır: Başlangıç, hisse senedi ve çok sayıda komik.

Bulut ve son teknoloji teknolojisinin bahsetme, sizi kenar altına iter.

Birkaç hafta ileri sarma ve artık bir tasarım oturumunda, önemli bir Duytadaki bir uygulama mimarisi olan yeni bir çalışanınız. Diğer önde gelen eticaret siteleriyle tamamlayacağız.

Nasıl oluşturacaksınız?

Son 15 yıldan yönergeleri izlerseniz, büyük olasılıkla Şekil 1,1 ' de gösterilen sistemi derleyebilirsiniz.

![Geleneksel tek parçalı tasarım](./media/monolithic-design.png)

**Şekil 1-1**. Geleneksel tek parçalı tasarım

Tüm etki alanı mantığınızı içeren büyük bir çekirdek uygulama oluşturursunuz. Kimlik, katalog, sıralama ve daha fazlasını içeren modüller içerir. Çekirdek uygulama büyük bir ilişkisel veritabanıyla iletişim kurar. Çekirdek, işlevselliği bir HTML arabirimi aracılığıyla kullanıma sunar.

Tebrikler!  Yalnızca bir tek parçalı uygulama oluşturdunuz.

Hepsi kötü değildir. Tek tek avantajlar, bazı farklı avantajlar sunmaktadır. Örneğin, bunlar basittir...

- derleme 
- test
- Dağıtımı
- Giderilmesine
- ölçek

Günümüzde mevcut birçok başarılı uygulama tek bir şekilde oluşturulmuştur. Uygulama bir isabet ediyor ve gelişmeye devam ediyor, yineleme sonrasında yineleme, daha fazla işlevsellik ve daha fazla işlev ekliyor.

Ancak, bir noktada rahatsız duymaktan başlayabilirsiniz. Uygulamanın kayıp denetimini bulabilirsiniz. Zaman kaldığında, çok daha yoğun hale gelir ve sonunda **korku çevrimi**olarak bilinen bir durum girersiniz.

- Uygulama, tek bir kişi tarafından anlasız overwhelmingly karmaşık hale geldi.
- Değişiklikler yapılıyor-her değişiklik istenmeden ve pahalı yan etkilere sahiptir.
- Yeni özellikler/düzeltmeler, uygulama için karmaşık, zaman alan ve pahalı hale gelir.
- Her yayın, tüm uygulamanın tam dağıtımını gerektirir.
- Kararsız bir bileşen sistemin tamamını kilitedebilir.
- Yeni teknolojiler ve çerçeveler bir seçenek değildir.
- Çevik teslim yöntemlerinin uygulanması zordur.
- Kod tabanı, ' de hiçbir zaman sonlandırma "özel durumlar" ile bir arada bulunan mimari Eroi 'ler olarak ayarlanır.
- Danışmanları yeniden yazmak için size bildirir.

Birçok kuruluş, sistem oluşturmaya yönelik bulut Yerel yaklaşımını benimseerek tek parçalı korku döngüsünü ele alıyor. Şekil 1-2, bulutta yerel teknikler ve uygulamalar uygulayan aynı sistemi gösterir.

![Bulutta yerel tasarım](./media/cloud-native-design.png)

**Şekil 1-2**. Bulutta yerel tasarım

Uygulamanın, küçük bir yalıtılmış mikro hizmetler kümesi üzerinde nasıl oluştuğunu aklınızda edin. Her hizmet kendi içinde bulunur ve kendi kodunu, verilerini ve bağımlılıklarını kapsüller. Her biri bir yazılım kapsayıcısında dağıtılır ve bir kapsayıcı Orchestrator tarafından yönetilir. Büyük bir ilişkisel veritabanı yerine, her hizmet kendi veri deposuna sahiptir ve veri ihtiyaçlarına göre farklılık gösteren tür. Bazı hizmetlerin, NoSQL veritabanlarında diğer bir ilişkisel veritabanına nasıl bağlı olduğunu not edin. Bir hizmet, durumunu dağıtılmış bir önbellekte depolar. Tüm trafiğin, ana arka uç hizmetleriyle trafiği yönlendirmekten ve birçok çapraz kesme ile ilgili sorunları zorlarken sorumlu bir API ağ geçidi hizmeti üzerinden nasıl yönlendirdiğine dikkat edin. En önemlisi, uygulama modern bulut platformlarında bulunan ölçeklenebilirlik ve dayanıklılık özelliklerinden tam olarak yararlanır.

### <a name="cloud-native-computing"></a>Bulutta yerel bilgi işlem

Hmm... "*Cloud Native*" terimini kullandık. Önce "Bu anlamı nedir?" olarak düşündük. Daha fazla bilgi pazarlamak için yazılım satıcıları tarafından başka bir sektör Buzzword tarafından işbirliği yapılıyor mu? "

Neyse ki, bu kitapta çok farklı ve bu kitabın sizi ikna etmeye yardımcı olacak.

Kısa bir süre içinde, Cloud Native, yazılım sektörde bir gidiş eğilimi haline geldi. Modern yazılım geliştirme uygulamalarından, teknolojisinden ve bulut altyapısından yararlanan bir yaklaşım olan büyük, karmaşık sistemler oluşturmayı düşünmek için yeni bir yoldur. Yaklaşım, sistemleri tasarlama, uygulama, dağıtma ve gerçekleştirme şeklini değiştirir.

Sektörünü çalıştıran sürekli hype aksine, Cloud native "*for-Real*" dır. Bulut Yerel bilgi işlem altyapısı 'nı (cncf), bulutta yerel bilgi işlem, teknoloji ve bulut yığınları genelinde bir arada bulundurmamıza yardımcı olan 300 ana kurumdan oluşan bir [konsorsiyunuzu](https://www.cncf.io/) düşünün. En etkili açık kaynaklı gruplardan biri olarak, GitHub 'da en hızlı büyüyen açık kaynaklı projelerin birçoğunu barındırır. [Kubernetes](https://kubernetes.io/), [Prometheus](https://prometheus.io/), [Held](https://helm.sh/), [Envoy](https://www.envoyproxy.io/)ve [GRPC](https://grpc.io/)gibi projeleri içerirler.

CNCF, açık kaynaklı ve satıcıya özgü bir ekosistemi bir arada bulunan. Bundan sonra, teknolojiden bağımsız olarak bulut Yerel ilkeleri, desenleri ve en iyi uygulamaları sunuyoruz. Aynı zamanda, bulutta yerel sistemler oluşturmak için Microsoft Azure bulutu 'nda bulunan hizmetleri ve altyapıyı tartıştık. 

Bu nedenle, yerel olarak bulut Native nedir? Geri dönerek bu yeni dünyayı araştırmanıza yardımcı olun.

>[!div class="step-by-step"]
>[Önceki](index.md)
>[İleri](definition.md)
