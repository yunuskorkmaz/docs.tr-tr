---
title: Kuyruklar Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- queues [WCF], MSMQ integration
ms.assetid: b8757992-ffce-40ad-9e9b-3243f6d0fce1
ms.openlocfilehash: 78d80a88153ee15f7ab152da44801c77900f874d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184594"
---
# <a name="queues-overview"></a>Kuyruklara genel bakış

Bu bölümde, sıralı iletişimin arkasındaki genel ve temel kavramlar tanıtışlar. Sonraki bölümler, burada açıklanan kuyruk kavramlarının Windows Communication Foundation 'da (WCF) nasıl tezahür ettiği ne kadar ayrıntılı olarak ele alınır.  
  
## <a name="basic-queuing-concepts"></a>Temel Kuyruk Kavramları  
 Dağıtılmış bir uygulama tasarlarken, hizmetler ve istemciler arasındaki iletişim için doğru taşımayı seçmek önemlidir. Çeşitli faktörler kullanılacak taşıma türünü etkiler. Hizmet, istemci ve aktarım arasındaki yalıtım gibi önemli bir faktör, sıraya ait bir aktarım veya TCP veya HTTP gibi doğrudan bir aktarım kullanımını belirler. TCP ve HTTP gibi doğrudan taşımaların doğası gereği, hizmet veya istemci çalışmayı durdurursa veya ağ başarısız olursa iletişim tamamen durur. Uygulamanın çalışması için hizmet, istemci ve ağ aynı anda çalışıyor olmalıdır. Sıralanan aktarımlar yalıtım sağlar, bu da hizmet veya istemci başarısız olursa veya aralarındaki iletişim bağlantıları başarısız olursa istemci ve hizmetin çalışmaya devam edebileceği anlamına gelir.  
  
 Kuyruklar, iletişim taraflarındaki veya ağdaki hatalarla bile güvenilir iletişim sağlar. Kuyruklar, iletişim kuran taraflar arasında değiş tokuş edilen iletileri yakalar ve teslim eder. Kuyruklar genellikle geçici veya dayanıklı olabilecek bir tür mağaza tarafından yedeklenir. Kuyruklar bir hizmet adına istemciden gelen iletileri depolar ve daha sonra bu iletileri hizmete iletir. Yönlendirme kuyrukları, başarısızlığın taraflardan herhangi biri tarafından izole edilmesini sağlayarak, yüksek kullanılabilirlik sistemleri ve bağlantısız hizmetler için tercih edilen iletişim mekanizması haline getirir. Yönlendirme yüksek gecikme maliyeti ile birlikte gelir. *Gecikme süresi,* istemcinin bir iletiyi gönderdiği saat ile hizmetin aldığı saat arasındaki gecikmedir. Bu, bir ileti gönderildikten sonra, iletinin ne zaman işlenebileceğini bilmediğiniz anlamına gelir. Sıraya alan uygulamaların çoğu yüksek gecikme süresiyle başa çıkatır. Aşağıdaki resimde sıralanmış iletişimkavramsal bir model gösterilmektedir.  
  
 ![Sıralı iletişim modeli](../../../../docs/framework/wcf/feature-details/media/qconceptual-figure1c.gif "QConceptual-Figure1c")  
  
 Sıraya ait iletişim kavramsal modeli  
  
 Gerçekte, sıra dağıtılmış bir kavramdır. Bu nedenle, her iki partiye de yerel veya her iki tarafa da uzak olabilir. Genellikle, sıra hizmetiçin yereldir. Bu yapılandırmada, istemci sürekli kullanılabilir olmak için uzak sıraya bağlantı bağlı olamaz. Benzer şekilde, sıra, hizmet okumasının kuyruktan bağımsız olarak kullanılabilir olması gerekir. Kuyruk yöneticisi bir sıra koleksiyonunu yönetir. Diğer sıra yöneticilerinden sıralarına gönderilen iletileri kabul etmekten sorumludur. Ayrıca, uzak kuyruklara bağlantı yönetiminden ve iletileri bu uzak kuyruklara aktarmaktan da sorumludur. İstemci veya hizmet uygulaması hatalarına rağmen kuyrukların kullanılabilirliğini sağlamak için, sıra yöneticisi genellikle harici bir hizmet olarak çalıştırılır.  
  
 İstemci kuyruğa ileti gönderdiğinde, iletiyi hizmetin sıra yöneticisi tarafından yönetilen sıra olan hedef sıraya gider. İstemci deki sıra yöneticisi iletiyi bir aktarım (veya giden) sıraya gönderir. İleti sırası, iletileri hedef sıraya aktalamak için depolayan istemci sıra yöneticisindeki bir sıradır. Sıra yöneticisi daha sonra hedef sıranın sahibi olan sıra yöneticisine giden bir yol bulur ve iletiyi ona aktarır. Güvenilir iletişim sağlamak için, kuyruk yöneticileri veri kaybını önlemek için güvenilir bir aktarım protokolü uygular. Hedef sıra yöneticisi, sahip olduğu hedef kuyruklara yönelik iletileri kabul eder ve iletileri depolar. Hizmet, hedef sıradan okuma isteklerini yapar ve bu sırada kuyruk yöneticisi iletiyi hedef uygulamaya teslim eder. Aşağıdaki resimde dört taraf arasındaki iletişim gösterilmektedir.  
  
 ![Sıralı Uygulama Diyagramı](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "Dağıtılmış Sıra-Şekil")  
  
 Tipik bir dağıtım senaryosunda sıralanmış iletişim  
  
 Böylece, sıra yöneticisi, gönderenin ve alıcının gerçek iletişimi etkilemeden bağımsız olarak başarısız olması için gerekli yalıtımı sağlar. Kuyrukların sağladığı ek yönlendirmenin yararı, birden çok uygulama örneğinin aynı sıradan okunmasını sağlar, böylece düğümler arasında tarım işi daha yüksek iş elde eder. Bu nedenle, daha yüksek ölçek ve iş verme gereksinimleri elde etmek için kullanılan kuyrukları görmek nadir değildir.  
  
## <a name="queues-and-transactions"></a>Kuyruklar ve İşlemler  
 Hareketler, bir işlem başarısız olursa tüm işlemlerin başarısız olması için bir dizi işlemi bir araya gruplandırmanızı sağlar. İşlemlerin nasıl kullanılacağına bir örnek, bir kişinin tasarruf hesabından çek hesabına 1.000 TL aktarmak için ATM kullanmasıdır. Bu, aşağıdaki işlemleri gerektirir:  
  
- Tasarruf hesabından 1000 dolar çekiyorum.  
  
- Çek hesabına 1000 dolar yatırmak.  
  
 İlk işlem başarılı olursa ve tasarruf hesabından 1.000 TL çekilirse, ancak ikinci işlem başarısız olursa, 1.000 TL zaten tasarruf hesabından çekildiği için kaybolur. Hesapları geçerli bir durumda tutmak için, bir işlem başarısız olursa, her iki işlemin de başarısız olması gerekir.  
  
 İşlemli iletilerde, iletiler kuyruğa gönderilebilir ve bir hareket altında kuyruktan alınabilir. Bu nedenle, bir harekette bir ileti gönderilir ve hareket geri alınırsa, sonuç, ileti nin kuyruğa hiç gönderilmemiş gibi olur. Benzer şekilde, bir harekette bir ileti alınırsa ve hareket geri alınırsa, sonuç ileti hiç alınmamış gibi olur. İleti okunmak üzere sırada kalır.  
  
 Yüksek gecikme nedeniyle, bir ileti gönderdiğinizde hedef sıraya ulaşmanın ne kadar sürdüğünü bilmenizin bir yolu yoktur veya hizmetin iletiyi işlemesinin ne kadar sürdüğünü bilemezsin. Bu nedenle, iletiyi göndermek, iletiyi almak ve sonra iletiyi işlemek için tek bir hareket kullanmak istemezsinüz. Bu, belirsiz bir süre için taahhüt edilmedi bir hareket oluşturur. Bir istemci ve hizmet bir hareketi kullanarak bir kuyruk üzerinden iletişim kurduğunda, biri istemcide, diğeri hizmette olmak üzere iki işlem söz konusu olur. Aşağıdaki resimde, tipik sıralı iletişimde hareket sınırları gösterilmektedir.  
  
 ![Hareketlerle sıra](../../../../docs/framework/wcf/feature-details/media/qwithtransactions-figure3.gif "QWithTransactions-Şekil3")  
  
 Yakalama ve teslim için ayrı hareketleri gösteren sıralı iletişim  
  
 İstemci hareketi işlemleri ve ileti gönderir. Hareket işlendiğinde, ileti aktarım kuyruğundadır. Hizmette, hareket hedef sıradaki iletiyi okur, iletiyi işler ve sonra hareketi işler. İşlem sırasında bir hata oluşursa, ileti geri alınır ve hedef sıraya yerleştirilir.  
  
## <a name="asynchronous-communication-using-queues"></a>Kuyrukları Kullanarak Eşzamanlı İletişim  
 Kuyruklar eşzamanlı bir iletişim aracı sağlar. Kuyrukları kullanarak ileti gönderen uygulamalar, sıra yöneticisi tarafından tanıtılan yüksek gecikme süresi nedeniyle iletinin alıcı tarafından alınmasını ve işlenmesini bekleyemez. İletiler, uygulamanın amaçladığından çok daha uzun süre kuyrukta kalabilir. Bunu önlemek için, uygulama iletide Bir Zaman-To-Live değeri belirtebilir. Bu değer, iletinin iletim kuyruğunda ne kadar kalması gerektiğini belirtir. Bu zaman değeri aşıldıysa ve ileti hala hedef sıraya gönderilmemişse, ileti ölü harf kuyruğuna aktarılabilir.  
  
 Gönderen bir ileti gönderdiğinde, gönderme işleminden gelen dönüş, iletinin yalnızca gönderendeki iletim kuyruğuna geldiği anlamına gelir. Bu nedenle, iletinin hedef sıraya alınamaması durumunda, gönderen uygulama bu konuda hemen bilgi alamaz. Bu tür hataları dikkate almak için, başarısız ileti ölü harf kuyruğuna aktarılır.  
  
 Hedef sıraya ulaşılamayan bir ileti veya Zaman-To-Live süresi dolan ileti gibi herhangi bir hata ayrı olarak işlenmelidir. Bu nedenle, sıraya ait uygulamaların iki mantık kümesi yazması nadir değildir:  
  
- İleti gönderme ve almanın normal istemci ve hizmet mantığı.  
  
- Başarısız iletim veya teslimiletileri işlemek için telafi mantığı.  
  
 Aşağıdaki bölümlerde bu kavramlar tartışılmaktadır.  
  
## <a name="dead-letter-queue-programming"></a>Ölü Harf Sıra Programlama  
 Ölü harf kuyrukları, çeşitli nedenlerle hedef sıraya ulaşamayan iletiler içerir. Nedenler, süresi dolmuş iletilerden iletinin hedef sıraya aktarılmasını engelleyen bağlantı sorunlarına kadar değişebilir.  
  
 Genellikle, bir uygulama sistem genelinde ki ölü harf kuyruğundan iletileri okuyabilir, neyin yanlış gittiğini belirleyebilir ve hataları düzeltme ve iletiyi yeniden gönderme veya not alma gibi uygun eylemi gerçekleştirebilir.  
  
## <a name="poison-message-queue-programming"></a>Zehirli İleti Sıra Programlama  
 İleti hedef sıraya girdikten sonra, hizmet iletiyi tekrar tekrar işleyebilir. Örneğin, bir işlem altında kuyruktan bir ileti okuma ve veritabanını güncelleştirme veritabanı geçici olarak bağlantısı kesilmiş bulabilirsiniz. Bu durumda, hareket geri alınır, yeni bir hareket oluşturulur ve ileti kuyruktan yeniden okunur. İkinci bir deneme başarılı veya başarısız olabilir. Bazı durumlarda, hatanın nedenine bağlı olarak, ileti tekrar tekrar uygulamaya teslim başarısız olabilir. Bu durumda, ileti "zehir" olarak kabul edilir. Bu tür iletiler, zehir işleme uygulaması tarafından okunabilen bir zehir kuyruğuna taşınır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF'de Kuyruğa Alma](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)
- [Oturumlar ve Kuyruklar](../../../../docs/framework/wcf/samples/sessions-and-queues.md)
- [Teslim Edilemeyen İletiler Sırası](../../../../docs/framework/wcf/samples/dead-letter-queues.md)
- [Geçici Kuyruğa Alınmış İletişim](../../../../docs/framework/wcf/samples/volatile-queued-communication.md)
- [Windows Communication Foundation'dan İleti Kuyruğuna](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)
- [İleti Kuyruğa Alma Yükleme (MSMQ)](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)
- [Windows Communication Foundation'a İleti Kuyruğa Alma](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)
- [İleti Kuyruğa Alma ile İleti Güvenliği](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)
