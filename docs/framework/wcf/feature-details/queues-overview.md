---
title: Kuyruklar Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- queues [WCF], MSMQ integration
ms.assetid: b8757992-ffce-40ad-9e9b-3243f6d0fce1
ms.openlocfilehash: c181a415c8702c3032077728139b23e86d85d1f0
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46562141"
---
# <a name="queues-overview"></a>Kuyruklar Genel Bakış
Bu bölümde genel tanıtır ve ardındaki temel kavramları, kuyruğa alınmış iletişim. Sonraki bölümlerde, sıraya alma burada açıklanan kavramlar, Windows Communication Foundation (WCF) nasıl bildirilen hakkında ayrıntılara gidin.  
  
## <a name="basic-queuing-concepts"></a>Kuyruğa ilişkin temel kavramlar  
 Dağıtılmış bir uygulama tasarlarken, hizmetleri ve istemciler arasındaki iletişimi için doğru taşıma önemlidir seçme. Pek çok etken kullanılacak aktarım türünü etkiler. Önemli bir faktördür — hizmet ve istemci taşıma arasında yalıtım — sıraya alınan aktarım veya TCP veya HTTP gibi doğrudan bir aktarım kullanımını belirler. TCP ve HTTP gibi doğrudan taşımalar yapısı nedeniyle, iletişim durdurur tamamen hizmet veya istemcinin çalışmamaya veya ağ başarısız olur. Hizmet, istemci ve ağ uygulamanın çalışması aynı anda çalıştırılması gerekir. Sıraya alınan taşımalar, hizmet veya istemcinin başarısız olursa veya aralarında iletişim bağlantıları başarısız olursa, istemci ve hizmet çalışmaya devam edebilir, yani, yalıtım sağlar.  
  
 Kuyruklar bile iletişim kuran taraflar ya da ağ hataları olan iletişiminizin sağlar. Kuyruklar, yakalayın ve iletişim kuran taraflar arasında alışverişi mesaj teslim eder. Kuyruklar, genellikle bir deposu geçici veya kalıcı olabilir bir tür tarafından desteklenir. Kuyruklar, bir hizmet adına istemciden gelen iletileri depolamak ve daha sonra bu hizmet iletileri iletecek. Kuyruklar yöneltme yüksek kullanılabilirlik sistemler için tercih edilen iletişim mekanizması getirerek bu nedenle, her iki taraf tarafından hata Yalıtımı sağlamış ve Hizmetleri bağlantısı kesildi. Yöneltme yüksek gecikme maliyeti ile birlikte gelir. *Gecikme süresi* olduğu zaman istemci bir ileti gönderir ve hizmet aldığı zamana arasındaki gecikme süresini. Bu, bir ileti gönderdikten sonra ne zaman bu iletiyi işlenebilir bildiğinizden yok anlamına gelir. Sıraya alınan uygulamaların en yüksek gecikme süresiyle başa. Kuyruğa alınan iletişim kavramsal modelin aşağıda gösterilmiştir.  
  
 ![Kuyruğa alınan iletişim model](../../../../docs/framework/wcf/feature-details/media/qconceptual-figure1c.gif "QConceptual Figure1c")  
  
 Kuyruğa alınan iletişim kavramsal model  
  
 Gerçekte, sıra dağıtılmış bir kavramdır. Bu nedenle, bunlar için her iki taraf da yerel veya uzak her iki taraf için olabilir. Genellikle, kuyruk hizmeti için yereldir. Bu yapılandırmada, istemcinin bağlantısı uzak kuyruğa sürekli kullanılabilir olmasını bağımlı olamaz. Benzer şekilde, sıranın kuyruktan okuma hizmet kullanılabilirliği kullanılabilir bağımsız olması gerekir. Bir kuyruk Yöneticisi sıra koleksiyonunu yönetir. Diğer kuyruğu yöneticileri, kuyruğa gönderilen iletileri kabul etmek için sorumludur. Bağlantı uzak kuyruklara yönetmek ve uzak sıraların iletilerini aktarma sorumludur. İstemci veya hizmet uygulama hatalarına rağmen kuyruklar kullanılabilirliğini sağlamak için Kuyruk yöneticisi genellikle bir dış hizmet çalıştırılır.  
  
 Bir istemci bir kuyruğa bir ileti gönderdiğinde hizmet Kuyruk yöneticisi tarafından yönetilen sırası hedef kuyruğa ileti yöneliktir. Sıra yöneticisini istemcide iletilmesi için iletiyi gönderir (veya giden) kuyruk. İletim sırası, iletilmesi için hedef kuyruk iletileri depolayan istemci Kuyruk Yöneticisi üzerinde kuyruğudur. Sıra yöneticisini ardından hedef sıranın sahibi ve ileti aktarımları Kuyruk yöneticisi bir yolunu bulur. Güvenilir iletişim sağlamak için veri kaybını önlemek için bir Güvenilir Aktarım Protokolü sıra yöneticileri uygulayın. Hedef sıra yöneticisini sahip olan ve iletileri depolayan hedef sıraya gönderilen iletileri kabul eder. Hizmet aynı zamanda Kuyruk yöneticisi ardından iletiyi hedef uygulamaya teslim hedef kuyruğu'ndan okuma isteklerinin yapar. Aşağıdaki çizimde, dört taraflar arasındaki iletişimi gösterir.  
  
 ![Uygulama diyagramı kuyruğa](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "dağıtılmış-kuyruk-Şekil")  
  
 Bir normal dağıtım senaryosunda kuyruğa alınan iletişim  
  
 Bu nedenle, kuyruk Yöneticisi gerekli yalıtımı sağlar, böylece alıcı ve gönderen bağımsız olarak gerçek iletişim etkilemeden başarısız olabilir. Böylece düğümler arasında iş farming daha yüksek aktarım hızı elde kuyruklar ek yöneltme avantajı da aynı kuyruktan okunmak üzere birden fazla uygulama örneğinin sağlar. Bu nedenle, daha yüksek ölçek ve aktarım hızı gereksinimleri elde etmek için kullanılan kuyrukları görmek için seyrek değil.  
  
## <a name="queues-and-transactions"></a>Kuyruklar ve işlemler  
 İşlemler bir işlem başarısız olursa, tüm işlemler başarısız olacak şekilde bir dizi işlemlerini gruplamanıza izin verin. Bir kişi kendi tasarruf hesabından 1,000 kendi denetleme hesabınıza aktarmak bir ATM kullandığında hareketleri kullanmak nasıl bir örneğidir. Bu, şu işlemleri kapsar:  
  
-   1.000 ABD Doları tasarruf hesaptan geri alınmasının.  
  
-   1,000 denetleme hesaba ürünü.  
  
 İlk işlemi başarılı olur ve 1.000 ABD Doları tasarruf hesabından çekildiğinde ancak ikinci işlem başarısız ise, zaten tasarruf hesabından iptal olduğundan 1,000 kaybolur. Bir işlem başarısız olursa hesapları geçerli bir durumda tutmak için iki işlem başarısız olmalıdır.  
  
 İleti işlem, iletiler kuyruğuna gönderilen ve bir işlem altında kuyruğa alınır. İleti hiçbir zaman varmış gibi bu nedenle, bir işlemde bir ileti gönderilir ve işlem geri alınır, ardından sonucu kuyruğa gönderilir. İleti hiçbir zaman varmış gibi benzer şekilde bir işlemde bir ileti alındı ve işlem geri alınır, ardından sonuç alınana. İleti okumak için kuyrukta kalır.  
  
 Hedef kuyruğunu ulaşmak ya da yapmak için ne kadar alan olduğunu bilmesinin imkanı sahip bir ileti gönderirken yüksek gecikme nedeniyle ne hizmetinin ileti işleme için sürdüğünü bildirin. Bu nedenle, tek bir işlem ileti gönder, ileti alabilir ve ardından iletiyi işlemek için kullanmak istediğiniz değil. Bu, belirsiz bir süre boyunca teslim edilmemiş bir işlem oluşturur. Hizmet ve istemci bir işlem kullanarak kuyruk iletişim kurduğunda, iki işlem söz konusu: bir istemci ve hizmet. Aşağıdaki çizim işlem sınırları içinde tipik kuyruğa alınan iletişim gösterir.  
  
 ![Kuyruk işlemle](../../../../docs/framework/wcf/feature-details/media/qwithtransactions-figure3.gif "QWithTransactions Figure3")  
  
 Yakalama ve teslimi için ayrı işlem gösteren kuyruğa alınan iletişim  
  
 İstemci işlem işler ve ileti gönderir. İşlem tamamlandığında, ileti aktarım kuyruğundadır. Hizmet işlem hedef kuyruktan ileti okuyan, iletiyi işler ve ardından hareketi tamamlar. İşleme sırasında bir hata meydana gelirse, ileti geri ve hedef sırasına yerleştirilecek.  
  
## <a name="asynchronous-communication-using-queues"></a>Zaman uyumsuz iletişim kuyrukları kullanma  
 Kuyruklar, zaman uyumsuz bir şekilde iletişim sağlar. Kuyrukları kullanarak iletileri gönderen uygulamayı olur ve Kuyruk yöneticisi tarafından sunulan yüksek gecikme nedeniyle alıcı tarafından işlenen ileti için sabırsızlanıyoruz. İletileri hedeflenen uygulamadan daha çok uzun bir süredir kuyrukta kalabilir. Bunu önlemek için uygulama iletide bir yaşam süresi değerini belirtebilirsiniz. Bu değer, ne kadar ileti aktarım kuyrukta kalması gerektiğini belirtir. Bu zaman değeri aştı ve iletinin hedef sıraya hala gönderilmedi, ileti atılacak için aktarılabilir.  
  
 Gönderen bir ileti gönderdiğinde ileti yalnızca gönderen iletimi sırasına yapılan, gönderme işlemi dönüş anlamına gelir. Bir hata varsa iletinin hedef sıraya alınırken, bu nedenle, gönderen uygulama bu konuda hemen bilemezsiniz. Bu tür hataları not almak için başarısız iletisi atılacak için aktarılır.  
  
 Hedef sıra ya da yaşam süresi sona ermekte ulaşmak başarısız olan bir ileti gibi herhangi bir hata ayrı olarak işlenmesi gerekir. Seyrek, bu nedenle, kuyruğa alınmış uygulamaları iki mantığı yazmak değil:  
  
-   İleti gönderme ve alma, service mantığı ve normal istemci.  
  
-   Başarısız iletim veya teslim gelen iletileri işlemek için telafi mantığı.  
  
 Aşağıdaki bölümlerde bu kavramlar açıklanmaktadır.  
  
## <a name="dead-letter-queue-programming"></a>Eski ileti sırası programlama  
 Edilemeyen çeşitli nedenlerden dolayı hedef sıra ulaşılamadı iletileri içerir. Süresi dolan iletileri nedenleri hedef kuyruğa ileti aktarımını engelleyen bağlantı sorunları değişebilir.  
  
 Genellikle, uygulamaya bir sistem genelinde edilemeyen kuyruktan ileti neyin yanlış gittiğini belirlemek ve hata düzeltme ve ileti veya alma Not yeniden gönderme gibi uygun bir işlemi okuyabilirsiniz.  
  
## <a name="poison-message-queue-programming"></a>Zehirli ileti kuyruğu programlama  
 İsteğe bağlı olarak bir ileti hedef sıraya yaptıktan sonra hizmetin sürekli olarak iletiyi işlemek başarısız olabilir. Örneğin, bir uygulama veritabanı geçici olarak bağlı bir işlem altında kuyruğa bir ileti okuma ve bir veritabanını güncelleştirmek bulabilirsiniz. Bu durumda, işlem geri alınır, yeni bir işlem oluşturulur ve kuyruktan ileti yeniden okuyun. İkinci denemesi başarılı veya başarısız. Hatanın nedenini bağlı olarak bazı durumlarda, iletiyi sürekli teslim uygulamaya başarısız olabilir. Bu durumda, ileti "poison" kabul edilir Bu türden iletilere poison işleme uygulama tarafından okunabilir bir zehirli kuyruğa taşınır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF'de Kuyruğa Alma](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [WCF'de Kuyruğa Alma](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [Oturumlar ve Kuyruklar](../../../../docs/framework/wcf/samples/sessions-and-queues.md)  
 [Teslim Edilemeyen İletiler Sırası](../../../../docs/framework/wcf/samples/dead-letter-queues.md)  
 [Geçici Kuyruğa Alınmış İletişim](../../../../docs/framework/wcf/samples/volatile-queued-communication.md)  
 [Windows Communication Foundation'dan Message Queuing’e](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)  
 [Message Queuing (MSMQ) Yükleme](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)  
 [Message Queuing tümleştirme bağlama örnekleri](https://msdn.microsoft.com/library/997d11cb-f2c5-4ba0-9209-92843d4d0e1a)  
 [Message Queuing’den Windows Communication Foundation'a](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)  
 [Message Queuing Üzerinden İleti Güvenliği](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)
