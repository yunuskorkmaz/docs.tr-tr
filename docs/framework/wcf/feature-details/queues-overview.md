---
title: Kuyruklar Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- queues [WCF], MSMQ integration
ms.assetid: b8757992-ffce-40ad-9e9b-3243f6d0fce1
ms.openlocfilehash: 3e75b6d5926b65a93204241eb7c71ca23a5694af
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596727"
---
# <a name="queues-overview"></a>Sıralara genel bakış

Bu bölümde, kuyruğa alınan iletişimin arkasındaki genel ve temel kavramlar tanıtılmaktadır. Sonraki bölümlerde, burada açıklanan sıraya alma kavramlarının Windows Communication Foundation (WCF) tarafından nasıl tanımlandığı hakkında ayrıntılı bilgiler verilmektedir.  
  
## <a name="basic-queuing-concepts"></a>Temel sıraya alma kavramları  
 Dağıtılmış bir uygulama tasarlarken, hizmetler ve istemciler arasında iletişim için doğru taşımanın seçilmesi önemlidir. Birçok etken kullanılacak aktarım türünü etkiler. Bir önemli etken — hizmet, istemci ve taşıma arasında yalıtım —, sıraya alınan bir taşımanın veya TCP veya HTTP gibi doğrudan bir taşımanın kullanımını belirler. TCP ve HTTP gibi doğrudan aktarımların doğası nedeniyle, hizmet veya istemcinin çalışmayı durdurması veya ağ başarısız olursa iletişim tamamen durdurulur. Uygulamanın çalışması için hizmetin, istemcinin ve ağın aynı anda çalışıyor olması gerekir. Sıraya alınan aktarımlar yalıtım sağlar; Bu, hizmet veya istemci başarısız olursa veya aralarındaki iletişim bağlantıları başarısız olursa, istemci ve hizmetin çalışmaya devam edebilmesini sağlar.  
  
 Kuyruklar, iletişim kuran taraflara veya ağa yönelik hatalarla birlikte güvenilir iletişim sağlar. Kuyruklar, iletişim kuran taraflar arasında değiş tokuş edilen iletileri yakalar ve teslim edebilir. Kuyruklar genellikle geçici veya dayanıklı olabilen bir mağaza türü tarafından desteklenir. Kuyruklar, iletileri bir hizmet adına bir istemciden depolar ve daha sonra bu iletileri hizmete iletir. Yöneltme kuyrukları, her iki taraf tarafından hata yalıtımı sağlar ve bu sayede yüksek kullanılabilirlik sistemleri ve bağlantısı kesilen hizmetler için tercih edilen iletişim mekanizması haline gelir. Yöneltme, yüksek gecikme süresine sahiptir. *Gecikme* süresi, istemcinin bir ileti gönderdiği zaman ve hizmetin aldığı zaman arasındaki gecikme gecikmesidir. Bu, bir ileti gönderildiğinde iletinin ne zaman işlenebileceği bilinmiyor anlamına gelir. En fazla sıraya alınan uygulamalar yüksek gecikme süresine sahiptir. Aşağıdaki çizimde, kuyruğa alınmış iletişimin kavramsal modeli gösterilmektedir.  
  
 ![Sıraya alınan iletişimin modeli](media/qconceptual-figure1c.gif "Qkavramsal-Figure1c")  
  
 Kuyruğa alınan iletişim kavramsal modeli  
  
 Gerçekte sıra, dağıtılmış bir kavramdır. Bu nedenle, her iki tarafın da yerel veya uzak bir yerele alınabilir. Genellikle, kuyruk hizmete yereldir. Bu yapılandırmada, istemci, sürekli kullanılabilir olması için uzak kuyrukla bağlantıya bağlı olamaz. Benzer şekilde, sıra, kuyruktan gelen hizmet okuma kullanılabilirliğinden bağımsız olarak kullanılabilir olmalıdır. Kuyruk Yöneticisi bir kuyruk koleksiyonunu yönetir. Diğer kuyruk yöneticilerinden kuyruklarına gönderilen iletileri kabul etmekten sorumludur. Ayrıca, uzak kuyrukların bağlantısını yönetmekten ve iletileri bu uzak sıralara aktarmaya de sorumludur. İstemci veya hizmet uygulama hatalarıyla aynı olmasına rağmen kuyrukların kullanılabilirliğini sağlamak için kuyruk Yöneticisi genellikle dış hizmet olarak çalışır.  
  
 İstemci bir sıraya bir ileti gönderdiğinde, hizmetin Queue Manager tarafından yönetilen kuyruk olan hedef sıraya yönelik iletiyi ele alınmaktadır. İstemcideki kuyruk yöneticisi iletiyi bir iletim (veya giden) kuyruğuna gönderir. İletim kuyruğu, istemci kuyruğu yöneticisinde iletileri hedef sıraya iletilmek üzere depolayan bir sıradır. Kuyruk Yöneticisi daha sonra, hedef sıranın sahibi olan kuyruk yöneticisinin yolunu bulur ve iletiyi buna aktarır. Güvenli iletişim sağlamak için kuyruk yöneticileri veri kaybını önlemeye yönelik güvenilir bir Aktarım Protokolü uygular. Hedef kuyruk yöneticisi, sahip olduğu hedef sıralara yönelik iletileri kabul eder ve iletileri depolar. Hizmet, hedef sıradan okuma istekleri yapar, bu durumda kuyruk yöneticisi daha sonra iletiyi hedef uygulamaya gönderir. Aşağıdaki çizimde, dört taraf arasındaki iletişim gösterilmektedir.  
  
 ![Kuyruğa alınmış uygulama diyagramı](media/distributed-queue-figure.jpg "Dağıtılmış kuyruk-şekil")  
  
 Tipik bir dağıtım senaryosunda sıraya alınmış iletişim  
  
 Bu nedenle, kuyruk yöneticisi, gönderenin ve alıcının gerçek iletişimi etkilemeden bağımsız olarak başarısız olması için gerekli yalıtımı sağlar. Kuyrukların sağladığı ek yöneltme avantajı, birden fazla uygulama örneğinin aynı kuyruktan okunmasını sağlar, böylece düğümler arasında çalışma daha yüksek bir işleme ulaşır. Bu nedenle, daha yüksek ölçek ve aktarım hızı gereksinimlerine ulaşmak için kullanılan kuyrukları görmek yaygın olmayan bir durumdur.  
  
## <a name="queues-and-transactions"></a>Kuyruklar ve Işlemler  
 İşlemler, tek bir işlem başarısız olursa tüm işlemlerin başarısız olması için bir dizi işlemi birlikte gruplandırmanız sağlar. İşlemlerin nasıl kullanılacağına ilişkin bir örnek, bir kişinin tasarruf hesabından $1.000 aktarmak için bir ATM kullandığında denetim hesaplarına bir örnektir. Bu, aşağıdaki işlemleri kapsar:  
  
- Tasarruf hesabından $1.000 çizimi.  
  
- Denetim hesabına $1.000 ekleyin.  
  
 İlk işlem başarılı olursa ve $1.000 tasarruf hesabından geri çıkarsa ancak ikinci işlem başarısız olursa, tasarruf hesabından zaten geri alındığından, $1.000 kaybedilir. Hesapların geçerli bir durumda tutulması için, bir işlem başarısız olursa her iki işlem de başarısız olmalıdır.  
  
 İşlemsel mesajlaşma 'da iletiler kuyruğa gönderilebilir ve bir işlem altında kuyruktan alınabilir. Bu nedenle, bir ileti bir işlem içinde gönderiliyorsa ve işlem geri alınırsa, iletinin kuyruğa hiç gönderilmemesi durumunda sonuç olur. Benzer şekilde, bir işlemde bir ileti alınırsa ve işlem geri alınırsa, sonuç iletinin hiç alınmadıysa olur. İleti okunacak sırada kalır.  
  
 Yüksek gecikme nedeniyle, bir ileti gönderdiğinizde, hedef kuyruğuna ulaşmak için ne kadar süreceğine ya da hizmetin iletiyi işlemesi için ne kadar sürdüğünü bilemezsiniz. Bu nedenle, iletiyi göndermek, iletiyi almak ve sonra iletiyi işlemek için tek bir işlem kullanmak istemezsiniz. Bu, belirsiz bir süre için kaydedilmemiş bir işlem oluşturur. Bir istemci ve hizmet bir işlem kullanarak bir sıra üzerinden iletişim kurduğunda, iki işlem söz konusu demektir: biri istemcide ve diğeri hizmet üzerinde. Aşağıdaki çizimde, sıradaki genel iletişim içindeki işlem sınırları gösterilmektedir.  
  
 ![İşlem içeren kuyruk](media/qwithtransactions-figure3.gif "QWithTransactions-Figure3")  
  
 Yakalama ve teslim için ayrı işlemler gösteren sıraya alınmış iletişim  
  
 İstemci işlemi iletiyi işler ve gönderir. İşlem tamamlandığında ileti iletim kuyruğundan olur. Hizmette, işlem hedef sıradan iletiyi okur, iletiyi işler ve sonra işlemi kaydeder. İşlem sırasında bir hata oluşursa, ileti geri alınır ve hedef sıraya konur.  
  
## <a name="asynchronous-communication-using-queues"></a>Kuyrukları kullanarak zaman uyumsuz Iletişim  
 Kuyruklar, zaman uyumsuz iletişim sağlar. Kuyrukları kullanarak ileti gönderen uygulamalar, kuyruk yöneticisi tarafından sunulan yüksek gecikme nedeniyle ileti alıcı tarafından alınıp işlenmek üzere bekleyemez. İletiler, uygulamanın amaçlanan uygulamadan daha uzun bir süre için kuyrukta kalabilirler. Bu önlemek için, uygulama iletide bir yaşam süresi değeri belirtebilir. Bu değer, iletinin iletim kuyruğunda ne kadar süreyle kalması gerektiğini belirtir. Bu zaman değeri aşılırsa ve ileti hala hedef kuyruğuna gönderilmezse ileti, atılacak iletiler kuyruğuna aktarılabilir.  
  
 Gönderici bir ileti gönderdiğinde, gönder işleminden geri dönme, iletinin yalnızca gönderen iletim kuyruğuna yaptığı anlamına gelir. Bu nedenle, iletinin hedef sıraya alınması sırasında bir hata oluşursa gönderen uygulama hemen hakkında bilgi alamaz. Bu tür arızalara göz atın, başarısız ileti teslim edilemeyen bir sıraya aktarılır.  
  
 Hedef sıraya ulaşamamakta olan veya yaşam süresi dolan bir ileti gibi herhangi bir hata, ayrı olarak işlenmelidir. Bu nedenle, kuyruğa alınan uygulamaların iki mantıksal kümesini yazması için sık görülen bir durumdur:  
  
- İleti gönderme ve alma için normal istemci ve hizmet mantığı.  
  
- Hatalı iletim veya teslimattan iletileri işlemek için Dengeleme mantığı.  
  
 Aşağıdaki bölümlerde bu kavramlar ele alınmaktadır.  
  
## <a name="dead-letter-queue-programming"></a>Teslim edilemeyen ileti sırası programlama  
 Atılacak ileti sıraları, çeşitli nedenlerle hedef sıraya ulaşmayan iletileri içerir. Nedenler, iletinin hedef sıraya aktarımını engellemek için, zaman aşımına uğradı iletilerden bağlantı sorunlarına kadar değişebilir.  
  
 Genellikle, bir uygulama, sistem genelinde teslim edilemeyen ileti sırasından iletileri okuyabilir, neyin yanlış olduğunu belirleyebilir ve hataları düzeltmek ve iletiyi yeniden göndermeyi veya notun bir örneğini ele almak gibi uygun işlemleri gerçekleştirebilir.  
  
## <a name="poison-message-queue-programming"></a>Zarar Iletisi sırası programlama  
 Bir ileti, hedef sıraya alındıktan sonra, hizmet sürekli olarak iletiyi işleyemeyebilir. Örneğin, bir işlem altında kuyruktan bir ileti okuyan bir uygulama ve bir veritabanını güncelleştirdiğinizde veritabanını geçici olarak bağlantısı kesik olabilir. Bu durumda, işlem geri alınır, yeni bir işlem oluşturulur ve ileti kuyruktan tekrar okunur olur. İkinci bir deneme başarılı veya başarısız olabilir. Bazı durumlarda, hatanın nedenine bağlı olarak, ileti uygulamaya sürekli olarak teslim edebilir. Bu durumda, ileti "Poison" olarak kabul edilir. Bu tür iletiler, zarar veren bir uygulama tarafından okunabilen bir Poison kuyruğuna taşınır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF'de Kuyruğa Alma](queuing-in-wcf.md)
- [Oturumlar ve Kuyruklar](../samples/sessions-and-queues.md)
- [Teslim Edilemeyen İletiler Sırası](../samples/dead-letter-queues.md)
- [Geçici Kuyruğa Alınmış İletişim](../samples/volatile-queued-communication.md)
- [Windows Communication Foundation'dan İleti Kuyruğuna](../samples/wcf-to-message-queuing.md)
- [İleti Kuyruğa Alma Yükleme (MSMQ)](../samples/installing-message-queuing-msmq.md)
- [Windows Communication Foundation'a İleti Kuyruğa Alma](../samples/message-queuing-to-wcf.md)
- [İleti Kuyruğa Alma ile İleti Güvenliği](../samples/message-security-over-message-queuing.md)
