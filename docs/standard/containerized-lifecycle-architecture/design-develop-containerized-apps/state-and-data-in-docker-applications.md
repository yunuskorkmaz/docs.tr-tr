---
title: Durum ve Docker uygulamalarında veri
description: Microsoft Platformu ve araçları ile kapsayıcı Docker uygulaması yaşam
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 78db191bdec4c25c11728d819d89eaaaff4bd7da
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44070270"
---
# <a name="state-and-data-in-docker-applications"></a>Durum ve Docker uygulamalarında veri

Bir basit kapsayıcıların değiştirilemezlik ' dir. Bir VM'ye karşılaştırıldığında kapsayıcıları sık karşılaştıkları kaybolur yok. Bir VM, çeşitli biçimlerde ölü işlemleri, aşırı yüklenmiş CPU ya da tam ya da başarısız bir disk başarısız olabilir. Henüz VM kullanılabilir olmasını bekliyoruz ve RAID sürücüleri sürücü hataları korumak güvence altına almak için sıradan bir hale gelir.

İşlem örneklerinin olmasını kapsayıcıları düşündüğünüz ancak. Bir işlem kalıcı durumunu korumak değil. Yerel depolama alanı için bir kapsayıcı yazabilirsiniz olsa da, bu örneği çevresinde süresiz olarak olacağı varsayılarak tek kopyası bellek kalıcı olduğu varsayılarak için eşdeğer olacaktır. Sonlandırılan, işlemler, olduğu gibi kapsayıcılar da çoğaltılır veya yönetilen bir kapsayıcı Düzenleyicisi ile bunların taşınmış olabilir varsaymanız gerekir.

Docker kullanan bir özellik olarak bilinen bir *kaplama dosya sistemi* depolayan herhangi bir yazarken kopyalama işlemini uygulamak için bu temel özgün görüntüye kıyasla, bir kapsayıcı kök dosya sistemine bilgiler güncelleştirilmiştir. Kapsayıcı sistemden sonradan silinirse bu değişiklikler kaybolur. Bir kapsayıcı varsayılan olarak bu nedenle, bir şekilde kalıcı depolama alanı yok. Kapsayıcı durumu kaydetmek mümkün olsa da, bu geçici bir sistem tasarımı kapsayıcı mimarisi ilkesini çakışıyor olabilir.

Docker uygulamalarında kalıcı verileri yönetmek için yaygın çözümleri vardır:

-   [**Veri birimleri**](https://docs.docker.com/engine/tutorials/dockervolumes/) bu belirtilenlerle yalnızca ana bilgisayara bağlayın.

-   [**Veri birim kapsayıcıları**](https://docs.docker.com/engine/tutorials/dockervolumes/#/creating-and-mounting-a-data-volume-container) bunlar arasında geçiş yapabilir, dış bir kapsayıcısını kullanan kapsayıcılar arasında paylaşılan depolama sağlar.

-   [**Birim eklentileri**](https://docs.docker.com/engine/tutorials/dockervolumes/#/mount-a-shared-storage-volume-as-a-data-volume) bu uzun vadeli kalıcılığını sağlayan uzak konumlara birimleri bağlayın.

-   **Uzak Veri kaynaklarını** örnekler SQL ve NO-SQL veritabanlarını dahil et veya önbellek Redis gibi hizmetler.

-   [**Azure depolama**](https://docs.microsoft.com/azure/storage/) bu kadar uzun süreli Kalıcılık kapsayıcıları en iyi şekilde sağlayan bir hizmet (PaaS) depolama coğrafi dağıtılabilir platform sağlar.

Veri birimleri atlama veya daha fazla kapsayıcı içindeki dizinlerin atanan özel [birleşim dosya sistemi](https://docs.docker.com/glossary/?term=Union%20file%20system). Veri birimleri, veri, kapsayıcının yaşam döngüsünü bağımsız korumak için tasarlanmıştır. Bir kapsayıcı kaldırın ya da "Çöp toplama" birimleri, bir kapsayıcı tarafından artık başvurulmayan olacak docker bu nedenle hiçbir zaman otomatik olarak birimleri siler. Konak işletim sistemi göz atabilir ve veri birimlerini tutumlu kullanmak için başka bir neden olduğu herhangi bir birim verileri özgürce düzenleyin.

A [veri birim kapsayıcısı](https://docs.docker.com/glossary/?term=volume) normal veri birimleri üzerinde bir geliştirme olduğu. İçinde oluşturulan (daha önce açıklandığı gibi) bir veya daha fazla veri hacimleri sahip aslında bir etkinliği olmayan kapsayıcıdır. Veri birim kapsayıcısı, bir merkezi takma noktasından kapsayıcılar için erişim sağlar. Bu yöntemin erişim veri kapsayıcısı mantıksal bağlama noktası yapma, özgün verilerin konumu soyutlar avantajdır. Ayrıca, "uygulama" kapsayıcıları oluşturulması ve adanmış bir kapsayıcıda kalıcı verileri korurken yok veri kapsayıcısı birimlere erişen sağlar.

Şekil 4-5 normal Docker birimleri depolama kapsayıcıları dışında ancak ana sunucu/VM fiziksel sınırları içinde yerleştirilebilir gösterir. *Docker birimler bir konak sunucu/VM'den bir birim başka bir kullanabilme sahip değilseniz*.

![](./media/image5.png)

Şekil 4-5: veri hacimleri ve kapsayıcı uygulamalar/kapsayıcılar için dış veri kaynakları

Sabit konak/VM, Docker konağının olmadığı sürece, birimleri iş verilerini çünkü kullanmamasını önerilir doğrulanamadığından ayrı fiziksel ana bilgisayarda çalışan kapsayıcılar arasında paylaşılan verileri yönetmek için Docker kapsayıcıları bir orchestrator'da kullanırken kapsayıcılar, bir küme tarafından gerçekleştirilecek iyileştirmeleri bağlı olarak başka bir konağa taşınıp beklenir.

Bu nedenle, normal veri hacimleri izleme dosyaları, geçici dosyaları ya da iş veri tutarlılığı, ya da birden çok konak genelinde kapsayıcılarınızı taşındığında etkilemez herhangi benzer kavramı çalışmak için iyi bir mekanizması mevcuttur.

[Birim eklentileri](https://docs.docker.com/engine/extend/plugins_volume/) veri kümesindeki tüm konaklar arasında sağlayın. Tüm birim eklentileri eşit olarak oluşturulmuş olsa da, birim eklentileri genellikle değişmez kapsayıcılardan te dış kalıcı güvenilir depolama sağlar.

Uzak Veri kaynaklarını ve SQL veritabanı, DocumentDB ve Redis gibi uzak bir önbellek gibi önbellekler kapsayıcı geliştirme ile aynı olacaktır. Bu, iş uygulama verilerini depolamak için tercih edilen ve kendini kanıtlamış, yollardan biridir.


>[!div class="step-by-step"]
[Önceki](monolithic-applications.md)
[İleri](soa-applications.md)
