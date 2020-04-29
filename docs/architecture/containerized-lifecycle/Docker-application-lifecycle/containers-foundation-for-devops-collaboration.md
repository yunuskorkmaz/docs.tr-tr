---
title: DevOps işbirliğinin temeli olarak kapsayıcılar
description: DevOps 'u kolaylaştırmak için kapsayıcıların anahtar rolünü anlayın.
ms.date: 04/16/2020
ms.openlocfilehash: 83bebc92a242a5ac2906d9997b7b278f87f0db96
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507356"
---
# <a name="containers-as-the-foundation-for-devops-collaboration"></a>DevOps işbirliğinin temeli olarak kapsayıcılar

Kapsayıcılar ve Docker teknolojisinin çok doğası gereği, geliştiriciler, yazılım ve bağımlılıklarını BT işlemleriyle ve üretim ortamlarıyla kolayca paylaşabilir, bu da tipik "makinem üzerinde çalıştığı" heyecanına göz ortadan kaldırır. Kapsayıcılar, farklı ortamlar arasındaki uygulama çakışmalarını çözüyor. Dolaylı olarak, kapsayıcılar ve Docker, geliştiricilere ve BT işlemlerine daha yakın bir şekilde işbirliği yaparak, bunların verimli bir şekilde işbirliği yapmalarını kolaylaştırır. Kapsayıcı iş akışını benimseme, kullandıkları DevOps sürekliliği ile birçok müşteriye sahiptir ancak daha önce yayın ve derleme işlem hatları için daha karmaşık yapılandırma aracılığıyla uygulama gerekiyordu. Kapsayıcılar DevOps içindeki derleme/test/dağıtım işlem hatlarını basitleştirir.

![Docker uygulamasının yaşam döngüsünün sahipliğini gösteren diyagram.](./media/containers-foundation-for-devops-collaboration/persona-workloads-docker-container-lifecycle.png)

**Şekil 2-1.** Kapsayıcılı Docker uygulamaları için yaşam döngüsünde "personas" başına ana iş yükleri

Docker Kapsayıcıları sayesinde, geliştiriciler kapsayıcı içinde (uygulama ve hizmet ve çerçeveler ile bileşenlere bağımlılıklar) ve kapsayıcı ve hizmetlerin bir hizmet koleksiyonu tarafından oluşturulan bir uygulama olarak birlikte nasıl davrandığına sahiptir. Birden çok kapsayıcının bağımlılıkları bir `docker-compose.yml` dosyada tanımlanır veya bir *dağıtım bildirimi*olarak çağrılabilir. Bu arada, BT operasyon ekipleri (BT uzmanları ve yönetimi) üretim ortamlarının yönetimine odaklanabilir. gerekli sorun izlemesinin ve sonuç olarak, uygulamaların son kullanıcılar için çeşitli kapsayıcıların içeriğini bilmeden doğru şekilde teslim edilmesini sağlamaktır. Bu nedenle, "kapsayıcı" adı, benzerleme vurguladı gerçek dünya teslim kapsayıcılarına geri çekiliyor. Bu nedenle, kapsayıcının içeriğinin sahipleri, kapsayıcının nasıl sevk edileceği ile ilgilenmemelidir ve sevkiyat şirketi, içeriği bilmeden veya bunlarla ilgili bilgi sahibi olmadan kaynak noktasından bir kapsayıcıyı hedefine aktarır. Benzer şekilde, geliştiriciler, "taşıma" mekanizmalarıyla ilgilenmenize gerek kalmadan bir Docker kapsayıcısı içinde içerik oluşturabilir ve kendilerinin bulunabilir.

Şekil 2-1 'nın sol tarafındaki sayfalarda, geliştiriciler Docker for Windows veya Mac kullanarak Docker kapsayıcılarında yerel olarak kod yazar ve çalıştırır. Bunlar, çalıştırılacak temel işletim sistemini ve bir Docker görüntüsüne kod oluşturmaya yönelik yapı adımlarını belirleyen bir Dockerfile kullanarak kodun işletim ortamını tanımlar. Geliştiriciler bir veya daha fazla görüntünün, belirtilen `docker-compose.yml` dosya dağıtım bildirimini kullanarak nasıl birlikte çalıştığını tanımlar. Kendi yerel geliştirilmesini tamamladıkları için, uygulama kodunu ve Docker yapılandırma dosyalarını kendi seçtikleri kod deposuna (yani, git deposu) iletebilirler.

DevOps sütun, kod deposunda sunulan dockerfile öğesini kullanarak derleme – sürekli tümleştirme (CI) işlem hatlarını tanımlar. CI sistemi, seçili Docker kayıt defterinden temel kapsayıcı görüntülerini çeker ve uygulama için özel Docker görüntülerini oluşturur. Görüntüler daha sonra onaylanır ve birden çok ortamda dağıtımlar için kullanılan Docker kayıt defterine gönderilir.

Sağ taraftaki işlemler, Operations ekipleri, geliştirme ekibine uygulamanın nasıl iyileşildiğini hakkında geri bildirim ve Öngörüler sağlayabilmeleri için ortamı ve uygulamaları izlerken, dağıtılan uygulamaları ve altyapıyı üretim sırasında yönetir. Kapsayıcı uygulamalar genellikle [Kubernetes](https://kubernetes.io/)gibi kapsayıcı düzenleyiciler kullanılarak üretimde çalışır; burada, Docker-Compose dosyaları yerine, genellikle [Helm grafiklerinin](https://helm.sh/) dağıtım birimlerini yapılandırmak için kullanılır.

İki ekip, bir sözleşme olarak ilgilendirmeyi sağlayan temel bir platform (Docker kapsayıcıları) aracılığıyla işbirliği yapar, ancak uygulama yaşam döngüsünde iki ekibin işbirliğini büyük ölçüde geliştirir. Geliştiriciler kapsayıcı içeriklerini, işletim ortamını ve kapsayıcı bağımlılarını kendi kendine alır, ancak operasyon ekipleri, derleme ve bunları düzenleme sistemlerinde çalıştırır.

## <a name="challenges-in-application-life-cycle-when-using-docker"></a>Docker kullanılırken uygulama yaşam döngüsü sorunları.

Yaklaşan yıllarda Kapsayıcılı uygulama sayısını artıracak birçok neden vardır ve bu nedenlerden biri, mikro hizmetlere dayalı olarak uygulamaların oluşturulmasına neden olur.

Son 15 yılda, Web Hizmetleri kullanımı binlerce uygulamanın temelini ve muhtemelen birkaç yıldan sonra, Docker Kapsayıcıları üzerinde çalışan mikro hizmet tabanlı uygulamalarla aynı durumu bulacağız.

Ayrıca, tek parçalı uygulamalar için Docker kapsayıcılarını de kullanabilirsiniz ve Docker avantajlarından büyük bir kısmını elde edebilirsiniz. Kapsayıcılar yalnızca mikro hizmetleri hedefetmez.

Docker containerleştirme ve mikro hizmetlerin kullanımı, kuruluşlarınızın geliştirme sürecinde yeni zorluk oluşmasına neden olur ve bu nedenle, üretim sistemlerinde çalışan çok sayıda kapsayıcıyı ve mikro hizmeti sürdürmek için kesintisiz bir stratejiye ihtiyacınız vardır. Sonuç olarak, kurumsal uygulamalarda, üretimde çalışan yüzlerce veya binlerce kapsayıcı/örnek olacaktır.

Bu sorunlar DevOps araçlarını kullanırken yeni talepler oluşturur, bu nedenle DevOps etkinliklerinizde yeni işlemler tanımlamanız ve bu tür sorulara cevap bulmanız gerekir:

- CI/CD, yönetim ve işlemler için geliştirme için hangi araçları kullanabilirim?

- Üretimde çalışırken şirketimdeki kapsayıcılardaki hataları nasıl yönetebilirim?

- Üretimde yazılımlarımızın parçalarını en düşük kapalı kalma süresiyle nasıl değiştirebilirim?

- Nasıl ölçeklendiriyoruz ve üretim sistemimizi nasıl izleyebiliriz?

- Yayın işlem hatmıza kapsayıcıların test ve dağıtımını nasıl dahil eteceğiz?

- Microsoft Azure kapsayıcılar için açık kaynaklı araçları/platformları nasıl kullanabiliriz?

Tüm bu soruları yanıtlayabiliyorsanız, uygulamalarınızı (mevcut veya yeni uygulamalar) Docker kapsayıcılarına taşımaya daha iyi hazırlanacağız.

## <a name="introduction-to-a-generic-end-to-end-docker-application-life-cycle-workflow"></a>Genel uçtan uca Docker uygulaması yaşam döngüsü iş akışına giriş

Şekil 2-2, bu örneğe belirli DevOps etkinlikleri ve varlıkları üzerinde odaklanan bir Docker uygulaması yaşam döngüsü için daha ayrıntılı bir iş akışı sunar.

![Docker uygulamasının genel uçtan uca yaşam döngüsünü gösteren diyagram.](./media/containers-foundation-for-devops-collaboration/generic-end-to-enddpcker-app-life-cycle.png)

**Şekil 2-2.** Docker Kapsayıcılı uygulama yaşam döngüsü için üst düzey iş akışı

Her şey, iç döngü iş akışında kod yazmaya başlayan geliştiriciyle başlar. İç döngü aşaması, geliştiricilerin kod deposuna kod göndermeden önce gerçekleşen her şeyi tanımlamaktır (örneğin, git gibi bir kaynak denetim sistemi). Oluşturulduktan sonra depo, sürekli tümleştirme (CI) ve iş akışının geri kalanını tetikler.

İç döngü temelde "Code," "Run," "test," ve "Debug" gibi tipik adımlardan oluşur ve uygulamayı yerel olarak çalıştırmadan önce gereken ek adımları içerir. Bu, uygulamayı bir Docker kapsayıcısı olarak çalıştırmak ve test etmek için geliştirici işlemidir. İç döngü iş akışı, izleyen bölümlerde açıklanacaktır.

Uçtan uca iş akışına bakmak için bir adım geri alma, DevOps iş akışı bir teknolojiden veya bir araç kümesinden daha fazla. Bu, kültürel bir evyi gerektiren bir anlayış. BT yaşamınızı daha hızlı ve öngörülebilir hale getirmek için insanlar, süreçler ve uygun araçlar. Kapsayıcılı bir iş akışını benimseyen kuruluşlar genellikle kuruluşlarını Kapsayıcılı iş akışıyla eşleşen kişileri ve süreçlerini temsil etmek üzere yeniden yapılandırabilir.

DevOps 'ın harekete geçmesini sağlamak, ekiplerin, gelişmiş izlenebilirlik ve yinelenebilir iş akışları ile sonuçlanan hataya açık el ile işlemleri Otomasyon ile değiştirerek rekabet baskılarına ile birlikte daha hızlı yanıt vermesini sağlar. Kuruluşlar ayrıca ortamları daha verimli bir şekilde yönetebilir ve şirket içi ve bulut kaynaklarının yanı sıra sıkı tümleşik araç oluşturma ile maliyet tasarrufu sağlayabilir.

Docker uygulamalarına yönelik DevOps iş akışınızı uygularken, Docker teknolojilerinin, iç döngüde (kod, çalıştırma, hata ayıklama), yapı-test-CI aşamasında ve son olarak bu kapsayıcıların hazırlama ve üretim ortamlarına dağıtılması gibi her bir iş akışının neredeyse her aşamasında bulunduğunu görürsünüz.

Kalite uygulamalarının geliştirilmesi, geliştirme döngüsünün başlarında kusurları tespit etmenize yardımcı olur ve bu da bunları düzeltme maliyetini azaltır. Ortamı ve bağımlılıkları görüntüye ekleyerek ve aynı görüntüyü birden çok ortamda dağıtmaya yönelik bir FIN benimseerek, dağıtımları daha güvenilir hale getiren ortama özgü yapılandırmaların ayıklanmasının bir disiplini yükseltiyor olursunuz.

Etkin izleme ile elde edilen zengin veriler (izleme ve tanılama), gelecekteki önceliklere ve yatırımlara kılavuzluk eden performans sorunları ve kullanıcı davranışına ilişkin öngörüler sağlar.

DevOps, hedef değil, bir yolculuğa göz önünde bulundurulmalıdır. Başarıyı, öğrendiğini ve geliştireceğinizi gösterebileceğiniz uygun kapsamlı projeler aracılığıyla artımlı olarak uygulanmalıdır.

## <a name="benefits-of-devops-for-containerized-applications"></a>Kapsayıcılı uygulamalar için DevOps 'ın avantajları

Katı bir DevOps iş akışı tarafından sunulan en önemli avantajlardan bazıları şunlardır:

- Daha hızlı ve daha iyi uyumluluk sayesinde daha iyi kalitede yazılım sunun.

- Sürekli geliştirme ve ayarlamaları daha önce ve daha ekonomi bir şekilde yapın.

- Sunmaya ve işletim yazılımlarına dahil olan paydaşlar arasındaki saydamlığı ve işbirliğini artırın.

- Güvenlik risklerini en aza indirmek için maliyetleri denetleyin ve sağlanan kaynakları daha verimli bir şekilde kullanın.

- Açık kaynaklı yatırımlar dahil olmak üzere mevcut DevOps yatırımlarınızdan çok sayıda Tak ve kullan.

>[!div class="step-by-step"]
>[Önceki](index.md)
>[İleri](../Microsoft-platform-tools-containerized-apps/index.md)
