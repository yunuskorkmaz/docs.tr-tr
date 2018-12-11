---
title: DevOps işbirliğinin temeli olarak kapsayıcılar
description: Microsoft Platformu ve araçları ile kapsayıcı Docker uygulaması yaşam
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: ccc8ef765cadfec31a2f714767d8e6eb76508093
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53126633"
---
# <a name="containers-as-the-foundation-for-devops-collaboration"></a>DevOps işbirliğinin temeli olarak kapsayıcılar

Kapsayıcıları ve Docker teknolojisini çok gereği, geliştiriciler kendi yazılım ve bağımlılıkları kolayca ile BT işlemleri ve üretim ortamları tipik "Benim makinemde çalışıyor" excuse sorununu ortadan kaldırırken paylaşabilir. Kapsayıcılar, farklı ortamlar arasında uygulama çakışmaları çözün. Dolaylı olarak kapsayıcıları ve Docker geliştiriciler ve BT işlemleri daha yakın bir araya, bunları etkin bir biçimde işbirliği kolaylaştırmaya getirin. Birçok müşteri, kapsayıcı iş akışı'ı benimsemeyi DevOps sürekliliği Aranan ancak daha karmaşık yayın yapılandırması aracılığıyla uygulama ve komut zincirleri oluşturmak vardı sağlar. Kapsayıcılar, DevOps derleme/test/dağıtma hatlarında basitleştirin.

![](./media/image1.png)

Şekil 2-1: Kapsayıcılı Docker uygulamaları için yaşam döngüsü "Kişiler" başına ana iş yükleri

Kapsayıcı (uygulama ve hizmeti ve bağımlılıklarını çerçeveleri ve bileşenleri) ve kapsayıcılar ve hizmetler hizmetler topluluğu tarafından oluşturulmuş bir uygulama olarak birlikte nasıl davranacağını nedir ile Docker kapsayıcılarında, geliştiricilerin kendi. Birden çok kapsayıcı bağımlılıkları docker-compose.yml dosyası veya ne çağrılabilir tanımlanan bir *dağıtım bildirimi*. Bu arada, BT işlem ekipleri (BT uzmanları ve yönetim), üretim ortamları yönetimine odaklanabilir; Altyapı; ölçeklenebilirlik; İzleme; ve sonuç olarak, uygulamaların düzgün bir şekilde, son kullanıcılar için çeşitli kapsayıcıları içeriğini bilmek zorunda kalmadan sunduğunuzdan kullandığınızdan emin olun. Bu nedenle, "geri çağırma gerçek nakliye benzerliği ad kapsayıcısı,". Bu nedenle, bir kapsayıcının içerik sahipleri kendilerini nasıl kapsayıcıya gönderilecek ve kargo şirketi taşımalar kaynaklandığı noktaya kapsayıcıdan hedefine bilerek veya içeriği hakkında caring olmadan endişe. Benzer şekilde, geliştiricilerin oluşturabilir ve kendi kendilerini "taşıma" mekanizmaları ile uğraşmak zorunda kalmadan bir Docker kapsayıcısı içinde içeriği.

Şekil 2-1'in sol tarafındaki pillar, geliştiriciler, yazma ve yerel kod için Docker Windows veya Mac kullanarak Docker kapsayıcılarında çalıştırın Bir Docker görüntüsü halinde kodlarını oluşturmaya yönelik derleme adımları yanı sıra çalıştırmak için temel işletim sistemi belirten bir Dockerfile'ı kullanarak kod işletim ortamını tanımlarlar. Bir veya daha fazla görüntü yukarıda sözü edilen kullanarak nasıl çalışmak geliştiriciler tanımlamak *docker-compose.yml* dosya dağıtım bildirimi. Kendi yerel geliştirme tamamlandıkça bunlar kendi uygulama kodunu ve Docker yapılandırma dosyalarını kod depoya seçtikleri (diğer bir deyişle, Git deposu) gönderin.

DevOps sütununu kullanarak kod deposunda sağlanan Dockerfile derleme – sürekli tümleştirme (CI) işlem hatları tanımlar. CI sistemi seçilen Docker kayıt defterinden temel kapsayıcı görüntülerini çeker ve uygulaması için özel Docker görüntülerini oluşturur. Görüntüleri ardından doğrulandı ve birden çok ortama dağıtımları için kullanılan Docker kayıt defterine gönderildi.

Sağ sütun takımları yönetme işlemleri uygulamalarınızın ve altyapınızın geri bildirim ve geliştirme ekibi, uygulamanın nasıl olabileceği hakkında içgörüler sağlayabilir bir ortam ve uygulamaların izleme sırasında üretimde dağıtılan geliştirildi. Kapsayıcı uygulamalar genellikle kapsayıcı düzenleyicileri kullanarak üretim ortamında çalıştırılır.

Büyük ölçüde uygulama yaşam döngüsü içinde iki takımların işbirliği geliştirme sırasında bir görev ayrımı nettir bir sözleşme sağlayan bir temel platform (Docker kapsayıcıları) üzerinden iki takımların işbirliği. Operasyon ekibi bildiriminin yanı sıra yerleşik görüntüleri alın ve bunları kendi düzenleme sistemi içinde çalışan geliştiricilerin kapsayıcı içeriğini, kendi işletim ortamını ve kapsayıcı bağımlılıklarını aittir.

## <a name="introduction-to-a-generic-end-to-end-docker-application-life-cycle-workflow"></a>Bir genel uçtan uca Docker uygulaması yaşam döngüsü iş giriş

Şekil 2-2, bu örnekte belirli DevOps etkinlikleri ve varlıklar üzerinde odaklanarak bir Docker uygulaması yaşam döngüsü için daha ayrıntılı bir iş akışı sunar.

![](./media/image2.png)

Şekil 2-2: Docker kapsayıcı uygulama yaşam döngüsü için üst düzey iş akışı

Her şeyi Geliştirici iç döngü akışında kod yazmaya başlar ile başlar. Geliştiriciler kodu depoya (örneğin, bir kaynak denetim sistemi Git gibi) kod göndermeden önce gerçekleşen her şeyi burada tanımlarsınız iç döngü aşamadır. Taahhüt edilen olduktan sonra depo sürekli tümleştirme (CI) ve iş akışının geri kalanı tetikler.

İç döngü temelde "code"Çalıştır""test"ve"debug"yanı sıra ek adımlar doğrudan uygulamayı yerel olarak çalıştırmadan önce" gibi tipik adımları içerir. Geliştirici çalıştırdığında ve bir Docker kapsayıcısı olarak uygulama testleri budur. İzleyen bölümlerde iç döngü iş akışı açıklanacaktır.

Bir adım sonuna kadar son iş akışı sırasında bakmak için geri alma, DevOps iş akışı bir teknoloji veya bir araç kümesi büyük: kültürel evrimi gerektiren bir yaklaşımdır. Bu kişilerin, işlemlerin ve uygun araçları, uygulama yaşam döngüsü daha hızlı ve daha öngörülebilir hale getirmek için olur. Kapsayıcıya alınmış bir iş akışı genellikle benimseyen kuruluşlar, kuruluşlarının, insanları ve kapsayıcılı iş akışıyla eşleşecek işlemleri temsil etmek için yeniden yapılandırabilirsiniz.

DevOps uygulayan daha hızlı birlikte için rekabet baskılarına sonuçları geliştirilmiş izlenebilirlik ve yinelenebilir iş akışları Otomasyon, hata yapmaya açık ve el ile gerçekleştirilen işlemleri değiştirerek yanıt ekipleri yardımcı olabilir. Kuruluşlar da ortamları daha verimli bir şekilde yönetebilir ve şirket içi ve bulut kaynakları ile maliyet tasarrufu yanı sıra sıkıca tümleşik Araçlar farkında olun.

Docker uygulamaları için DevOps iş akışınızın uygularken, Docker'ın teknolojileri için derleme test CI aşaması, iç döngü (çalışma kodu, hata ayıklama) çalışırken, geliştirme kutusundan mevcut iş akışı, neredeyse her aşamasında olduğunu görürsünüz ve Tabii ki üretim ve hazırlık ortamları ve kapsayıcılarınızı ortamlar için dağıtım yaparken.

Kalite uygulamalarının geliştirme düzeltme maliyeti azaltır Geliştirme döngüsünün başlarında, kusurlarını tanımlamaya yardımcı olur. Görüntüde ortam ve bağımlılıklar dahil olmak üzere ve birden çok ortamda aynı görüntüsü dağıtma bir felsefesi benimseme ayıklama dağıtımları daha güvenilir hale ortama özgü yapılandırmaları olan bir uzmanlık alanı tanıtın.

Etkili Araçları (izleme ve tanılama) alınan zengin veriler, performans sorunlarını ve gelecekteki öncelikleri ve Yatırımlar için rehberlik için kullanıcı davranışını hakkında Öngörüler sağlar.

DevOps yolculuğu, bir hedef kabul edilmelidir. Artımlı olarak kendisinden, başarı göstermek, öğrenin ve evrim Geçiren uygun kapsamlı projelerini aracılığıyla uygulanmalıdır.

## <a name="benefits-of-devops-for-containerized-applications"></a>Kapsayıcılı uygulamalar için DevOps avantajları

Düz bir DevOps iş akışı tarafından sağlanan en önemli avantajlarından bazıları şunlardır:

-   Daha hızlı ve daha iyi uyumluluk daha kaliteli yazılım sunun

-   Sürekli gelişim ve ayarlamaları önceden ve daha ekonomik bir şekilde artırın

-   Saydamlık ve hissedarlar sunmaya ve yazılım işletim arasında işbirliğini artırın

-   Sağlanan kaynakları daha etkili bir şekilde güvenlik riskleri en aza indirerek yazılımınız olması ve maliyetleri denetim

-   Tak ve iyi yatırımları içinde açık kaynak dahil olmak üzere, var olan DevOps yatırımlarınızı birçoğu ile Çalıştır

>[!div class="step-by-step"]
>[Önceki](index.md)
>[İleri](../Microsoft-platform-tools-containerized-apps/index.md)