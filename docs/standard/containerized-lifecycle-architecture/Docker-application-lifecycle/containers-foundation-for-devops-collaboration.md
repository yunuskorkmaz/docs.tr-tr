---
title: DevOps işbirliği için temel olarak kapsayıcıları
description: Microsoft Platformu ve araçları ile kapsayıcılı Docker uygulama yaşam döngüsü
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 0fa43263e789bba5b720792e7e8dc5321af795b7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="containers-as-the-foundation-for-devops-collaboration"></a>DevOps işbirliği için temel olarak kapsayıcıları

Docker teknolojisi ve kapsayıcıları çok gereği, geliştiricilerin kendi yazılım ve bağımlılıkları kolayca BT işlemleri ve üretim ortamlarını tipik "Benim makinede çalışır" excuse ortadan sırasında paylaşabilirsiniz. Kapsayıcıları farklı ortamlar arasındaki uygulama çakışmaları çözün. Dolaylı olarak kapsayıcıları ve Docker geliştiriciler ve BT işlemleri daha yakın bir araya, bunları etkili bir şekilde işbirliği yapmak için daha kolay hale getirir. Kapsayıcı iş akışı benimsenmesi birçok müşteri DevOps sürekliliği Aranan ancak sürüm için daha karmaşık yapılandırması aracılığıyla uygulamak ve işlem hatlarını oluşturmak daha önce sahip olduğunuz sağlar. Kapsayıcı içinde DevOps yapı/test/dağıtma ardışık düzen basitleştirin.

![](./media/image1.png)

Şekil 2-1: ana iş yükleri yaşam döngüsündeki kapsayıcılı Docker uygulamalar için "Kişiler" başına

Kapsayıcı (uygulama ve hizmet ve bağımlılıkları çerçeveler ve bileşenleri için) ve kapsayıcılar ve Hizmetleri hizmetler topluluğu tarafından oluşan bir uygulama olarak birlikte nasıl davranacağını içinde nedir Docker ile kapsayıcıları, geliştiricilerin kendi. Birden çok kapsayıcı bağımlılıklarını docker-compose.yml dosyası veya ne çağrılabilir tanımlanan bir *dağıtım bildirimi*. Bu sırada, BT işletim ekipleri (BT uzmanları ve yönetim) üretim ortamlarında yönetimine odaklanabilir; Altyapı; ölçeklenebilirlik; İzleme; ve sonuç olarak, uygulamaların düzgün son kullanıcılar için çeşitli kapsayıcıları içeriğini bilmek zorunda kalmadan sunduğunuzdan sağlama. Bu nedenle, "gerçek sevkiyat kapsayıcıları benzerliği geri çağırma ad kapsayıcısı,". Bu nedenle, bir kapsayıcının içerik sahipleri kendilerini kapsayıcı sevk nasıl ve sevkiyat şirket taşımalar kaynaklandığı noktaya kapsayıcıdan hedefine bilerek veya içeriği hakkında caring olmadan endişe. Benzer şekilde, geliştiriciler oluşturabilir ve Docker kapsayıcısı kendilerini "aktarma" mekanizmalarıyla ilgilendiren gerek olmadan içeriği sahip.

Şekil 2-1'in sol tarafındaki sütun, geliştiriciler, yazma ve Docker kapsayıcılarında yerel olarak çalıştırmak için Docker Windows veya Mac kullanarak kodu Bunlar, işletim sistemi ortamında kodu için Docker görüntüsüne kendi kodu oluşturmak için oluşturma adımlarının yanı sıra çalıştırmak için temel işletim sistemi belirten bir Dockerfile kullanarak tanımlayın. Bir veya daha fazla görüntü daha önce bahsedilen kullanarak nasıl çalışmanız geliştiriciler tanımlamak *docker-compose.yml* dosya dağıtım bildirimi. Kendi yerel geliştirme tamamlandıkça bunlar kendi uygulama kodu artı Docker yapılandırma dosyalarını kod deposuna kendi seçtikleri (diğer bir deyişle, Git deposu) Gönder.

DevOps pillar kod deposunda sağlanan Dockerfile kullanılarak yapı – sürekli tümleştirme (CI) işlem hatlarını tanımlar. CI sistemi seçili Docker kayıt defterinden temel kapsayıcı görüntüleri çeker ve uygulama için özel Docker görüntü oluşturur. Görüntüleri ardından doğrulandığını ve birden çok ortamı dağıtımları için kullanılan Docker kayıt defteri için gönderilir.

Sağdaki sütun içinde takımları yönetme işlemleri uygulamalarını ve altyapısını geri bildirim ve uygulama nasıl olabileceği hakkında geliştirme ekibi ınsights'a sağlayabilecek bir ortam ve uygulamaların izleme sırasında üretimde dağıtılan Geliştirilmiş. Kapsayıcı uygulamaları genellikle kapsayıcı orchestrators kullanan üretim ortamlarında çalışır.

İki takımlar büyük ölçüde uygulama yaşam döngüsü iki takımlar işbirliğini geliştirme sırasında sorunları bir ayrılması bir sözleşme sağlayan bir temel platform (Docker kapsayıcıları) üzerinden ortak çalışıyorsunuz. İşletim ekipleri bildirim yanı sıra yerleşik görüntüleri almak ve bunları kendi orchestration sisteminde çalışır ancak geliştiriciler kapsayıcı içeriğini, kendi işletim sistemi ortamında ve kapsayıcı bağımlılıklarını sahip.

## <a name="introduction-to-a-generic-end-to-end-docker-application-life-cycle-workflow"></a>Bir genel uçtan uca Docker uygulama yaşam döngüsü akışına giriş

Şekil 2-2, bu örnekte belirli DevOps etkinlikleri ve varlıkları odaklanan, Docker uygulama yaşam döngüsü için daha ayrıntılı bir iş akışı sunar.

![](./media/image2.png)

Şekil 2-2: Docker kapsayıcılı uygulama yaşam döngüsü için üst düzey iş akışı

Her şeyi iç döngü iş akışında kod yazma başlatan Geliştirici ile başlar. Burada geliştiriciler kod depoya (örneğin, bir kaynak denetim sistemi Git gibi) kod göndermeden önce gerçekleşen her şeyi tanımlarsınız iç döngü aşamasıdır. Taahhüt eder sonra depo sürekli tümleştirme (CI) ve iş akışının geri kalanı tetikler.

İç döngü temelde "code"Çalıştır""test"ve"hata ayıklama"artı ek adımlar doğrudan uygulama yerel olarak çalıştırmadan önce" gibi tipik adımlardan oluşur. Geliştirici çalıştırıldığında ve uygulamayı bir Docker kapsayıcısı olarak sınar budur. İç döngü iş akışı izleyen bölümlerde açıklandığı.

Bir adımı sonuna kadar bitiş şu iş akışını aramak için geri alma, DevOps iş akışı bir teknoloji veya bir araç kümesi büyük: kültürel evrimi gerektiren bir bakış değil. Bu kişiler, işlemleri ve uygun araçları, uygulama yaşam döngüsü daha hızlı ve daha tahmin edilebilir yapmak için olur. Kapsayıcılı iş akışı genellikle benimsemeyi kuruluşların kuruluşlarına kişiler ve kapsayıcılı iş akışı ile eşleşen işlemler temsil etmek için yeniden yapılandırabilirsiniz.

DevOps kapattığınızdan daha hızlı birlikte rekabet pressures geliştirilmiş izlenebilirlik ve tekrarlanabilir iş akışları ile sonuçlanır otomasyon ile hataya yatkın süreç değiştirerek yanıt ekipleri yardımcı olabilir. Kuruluşlar aynı zamanda ortamları daha verimli bir şekilde yönetme ve ile şirket içi ve bulut kaynakları birlikte maliyet tasarrufu ve aynı zamanda sıkı bir şekilde tümleşik araç unutmayın.

DevOps iş akışınız için Docker uygulamaları uygularken, Docker'ın teknolojileri iç döngü (çalışma kodu, hata ayıklama), yapı test CI aşamasına çalışırken, geliştirme kutusundan mevcut iş akışı, neredeyse her aşamada olduğunu görürsünüz ve Elbette üretim ve hazırlık ortamları ve kapsayıcılarınızı bu ortamlar için dağıtırken.

Kalite uygulamalarının geliştirme erken bunları düzeltmek maliyetini azaltır geliştirme döngüsü kusurlarını tanımlamaya yardım eder. Ortam ve bağımlılıkları görüntüsüne dahil ve birden çok ortamlar genelinde aynı görüntü dağıtma felsefesi benimsenmesi dağıtımları daha güvenilir yapmadan ortama özgü yapılandırmaları ayıklanması, uzmanlık yükseltin.

Etkili Araçları (izleme ve tanılama) elde zengin veri performans sorunlarını ve gelecekteki öncelikleri ve yatırımlarınızı kılavuza kullanıcı davranışı hakkında bilgi sağlar.

DevOps gezisine, bir hedef dikkate alınmalıdır. Artımlı olarak kendisinden da başarı göstermek, öğrenin ve gelişmesi uygun şekilde kapsamlı projeler uygulanmalıdır.

## <a name="benefits-of-devops-for-containerized-applications"></a>DevOps yararları kapsayıcılı uygulamalar için

Düz bir DevOps iş akışı tarafından sağlanan en önemli avantajlarından bazıları şunlardır:

-   Daha iyi kalite, daha hızlı ve daha iyi uyumluluk yazılımlara

-   Sürekli geliştirme ve düzeltmeleri daha önce ve daha ekonomik sürücü

-   Saydamlık ve Paydaşlar teslim etmek ve yazılım işletim ilgili arasında işbirliği artırın

-   Maliyetleri denetim ve güvenlik riskleri en aza indirerek sağlanan kaynakları daha verimli şekilde kullanma

-   Tak ve birçok açık kaynağında Yatırımlar dahil olmak üzere, varolan DevOps yatırımlarınızı ile iyi kullan

>[!div class="step-by-step"]
[Önceki] (index.md) [sonraki] (.. /Microsoft-Platform-Tools-containerized-Apps/index.MD)
