---
title: "Kuyruklar Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: queues [WCF], MSMQ integration
ms.assetid: b8757992-ffce-40ad-9e9b-3243f6d0fce1
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c0952f238c34176112f6ec6a8520fb603cca4750
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="queues-overview"></a>Kuyruklar Genel Bakış
Bu bölümde genel tanıtır ve temel kavramları kuyruğa alınmış iletişim. Sonraki bölümlerde Git nasıl, burada açıklanan queuing kavramları bildirilmiş hakkında ayrıntılar içine [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].  
  
## <a name="basic-queuing-concepts"></a>Sıraya alma ilişkin temel kavramlar  
 Dağıtılmış bir uygulama tasarlarken, hizmetleri ve istemciler arasında iletişim için doğru taşıma önemlidir seçme. Pek çok etken kullanılacak aktarım türünü etkiler. Önemli bir etken — hizmeti, istemci ile taşıma arasında yalıtım — sıraya alınan aktarım veya TCP veya HTTP gibi doğrudan bir aktarım kullanımını belirler. TCP ve HTTP gibi doğrudan taşımaları yapısı nedeniyle, iletişim durdurur tamamen hizmet ya da istemci çalışmayı durdurmasına veya ağ başarısız olur. Hizmet, istemci ve ağ uygulamanın çalışması aynı anda çalıştırması gerekir. Sıraya alınan taşımaları hizmet ya da istemci başarısız olursa veya aralarında iletişim bağlantıları başarısız olursa, istemci ve hizmet çalışmaya devam edebilirsiniz yalıtımı sağlar.  
  
 Kuyruklar bile iletişim kuran taraflar veya ağ hataları olan güvenilir iletişim sağlar. Kuyruklar, yakalama ve iletişim kuran tarafların arasında alınıp iletileri sunmak. Kuyruklar genellikle volatile veya dayanıklı bir depolama çeşit tarafından desteklenir. Kuyruklar, bir hizmet adına bir istemciden gelen iletileri depolamak ve daha sonra bu iletiler hizmetine iletmek. Kuyruklar sağlamak yöneltme yalıtım hata böylece yüksek kullanılabilirlik sistemleri için tercih edilen iletişim mekanizması yapma, her iki taraf tarafından güvence altına ve Hizmetleri bağlantısı kesildi. Yöneltme sahip olma maliyeti yüksek gecikme süresi ile birlikte gelir. *Gecikme süresi* istemci bir ileti gönderir saati ve hizmet alır saati arasındaki gecikme süresini değil. Bu, bir ileti gönderildikten sonra bu iletiyi zaman işlenebilir bildiğinizden değil anlamına gelir. Sıraya alınan uygulamaları en yüksek gecikme süresiyle başa çıkacak. Aşağıdaki resimde kuyruğa alınan iletişim kavramsal modeli gösterilmektedir.  
  
 ![Kuyruğa alınan iletişim model](../../../../docs/framework/wcf/feature-details/media/qconceptual-figure1c.gif "QConceptual Figure1c")  
  
 Kuyruğa alınan iletişim kavramsal model  
  
 Gerçekte, sıra dağıtılmış bir kavramdır. Bu nedenle, bunlar için her iki taraf yerel veya uzak hem taraflara olabilir. Genellikle, hizmete yerel sırasıdır. Bu yapılandırmada, istemci bağlantı sürekli olarak kullanılabilir olması için Uzak kuyruğa bağımlı olamaz. Benzer şekilde, sıranın sıradan okuma hizmetin kullanılabilirliğini kullanılabilir bağımsız olması gerekir. Sıra yöneticisini sıra koleksiyonunu yönetir. Diğer sıra yöneticileri kendi sıralara gönderilen iletileri kabul etmek için sorumludur. Bağlantı uzak sıralara yönetmek ve uzak sıraların iletilerini aktarma sorumludur. İstemci veya hizmet uygulaması arızalarına karşı sıraları kullanılabilirliğini sağlamak için sıra yöneticisini genellikle bir dış hizmet olarak çalıştırılır.  
  
 Bir istemci bir sıraya bir ileti gönderdiğinde, hizmetin sıra yöneticisi tarafından yönetilen sırası hedef sıra iletiye giderir. Sıra yöneticisini istemcide iletilmesi için iletiyi gönderir (veya giden) sırası. İletim sırası iletilmesi için hedef sıra iletileri depolayan istemci sıra yöneticisi bulunan bir sıra var. Sıra yöneticisini sonra hedef sıranın sahibi ve iletiye aktarımları sıra yöneticisi yola bulur. Güvenilir iletişim sağlamak için veri kaybını önlemek için bir Güvenilir Aktarım Protokolü sıra yöneticilerini kullanır. Hedef sıra yöneticisinin, sahibi ve iletileri depolayan hedef sıralara ele iletileri kabul eder. Aynı zamanda sıra yöneticisini sonra ileti hedef uygulamaya gönderir hedef sıra okuma isteklerine hizmet yapar. Aşağıdaki çizimde, dört taraflar arasındaki iletişimi gösterir.  
  
 ![Sıraya alınan uygulama diyagramı](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "dağıtılmış-sıra-Şekil")  
  
 Tipik dağıtım senaryosunda kuyruğa alınan iletişim  
  
 Bu nedenle, böylece göndereni ve alıcısı bağımsız olarak gerçek iletişimi etkilemeden yük devredebilir sıra yöneticisini gerekli yalıtımı sağlar. Böylece iş düğümler arasında farming daha yüksek verimlilik elde eder sıraları sağlayan ek yöneltme yararı Ayrıca aynı kuyruktan okunmak üzere birden çok uygulama örnekleri sağlar. Bu nedenle, daha yüksek ölçek ve üretilen iş gereksinimleri elde etmek için kullanılan sıraları görmek için seyrek değil.  
  
## <a name="queues-and-transactions"></a>Kuyruklar ve işlemler  
 İşlemler, böylece bir işlem başarısız olursa, tüm işlemler başarısız bir işlemler kümesini gruplamak izin verir. Bir kişinin 1,000 kendi tasarrufları hesabından kendi denetleme hesabına aktarmak için bir ATM kullandığında hareketleri kullanmak nasıl bir örnektir. Bu, aşağıdaki işlemleri kapsar:  
  
-   Yoksundur 1,000 tasarrufları hesabından.  
  
-   1,000 denetleme dikkate ürünü.  
  
 İlk işlemi başarılı olur ve 1,000 tasarrufları hesabından geri alınmış ancak ikinci bir işlem başarısız olursa, onu zaten tasarrufları hesabından iptal olduğundan 1,000 kaybolur. Bir işlem başarısız olursa hesapları geçerli bir durumda tutmak için her iki işlem başarısız olmalıdır.  
  
 İşlem iletileri içinde iletiler kuyruğuna gönderilen ve sıra bir işlem altında aldı. İleti hiçbir zaman sahipmiş gibi bu nedenle, bir işlem içinde bir ileti gönderilir ve işlem geri alındı, ardından sonucu sırasına gönderilir. İleti hiçbir zaman sahipmiş gibi benzer şekilde bir işlem içinde bir ileti aldı ve işlem geri alındı, ardından sonucu aldı. İleti okumak için kuyruğunda kalır.  
  
 Hedef sıra ulaşmak ya da yapmak için gereken süreyi bilmesinin yolu yoktur bir ileti gönderirken yüksek gecikme nedeniyle hizmetinin iletiyi işlemek için gereken süreyi bildirin. Bu nedenle, tek bir işlem iletiyi göndermek, ileti almak ve iletiyi işlemek için kullanmak istediğiniz değil. Belirsiz bir süre boyunca teslim edilmemiş bir işlem oluşturur. Bir istemci ve hizmet bir işlem kullanarak sıra iletişim kurduğunda, iki işlemleri oynayan: bir istemci hem de bir hizmet. Aşağıdaki çizimde tipik kuyruğa alınan iletişim işlem sınırlarını gösterir.  
  
 ![Sıra hareketlerle](../../../../docs/framework/wcf/feature-details/media/qwithtransactions-figure3.gif "QWithTransactions Figure3")  
  
 Yakalama ve teslimi için ayrı işlemleri gösteren kuyruğa alınan iletişim  
  
 İstemci işlem işler ve iletiyi gönderir. İşlem tamamlandığında, ileti iletim kuyrukta bulunuyor. Hizmet işlem iletiyi hedef sıradan okur, iletiyi işler ve hareketi tamamlar. İşleme sırasında bir hata meydana gelirse, ileti geri alınamaz ve hedef sırasına yerleştirilecek.  
  
## <a name="asynchronous-communication-using-queues"></a>Zaman uyumsuz iletişim kullanarak sıraları  
 Kuyruklar, iletişimin zaman uyumsuz bir yöntemdir. Kuyrukları kullanma ileti gönderme uygulamaları alınan ve sıra yöneticisi tarafından sunulan yüksek gecikme nedeniyle alıcı tarafından işlenen ileti Bekleyemez. İletiler kuyrukta hedeflenen uygulaması'ndan ne kadar uzun süre kalır. Bunu önlemek için uygulama ileti üzerinde bir yaşam süresi değeri belirtebilirsiniz. Bu değer, ne kadar ileti iletim sırasındaki kalması gerektiğini belirtir. Bu zaman değerini aştı ve iletinin hedef sıraya hala gönderilmedi, ileti teslim edilemeyen kuyruğuna aktarılabilir.  
  
 Gönderen bir ileti gönderdiğinde, gönderme işlemi dönüş iletiyi yalnızca gönderen iletimi sırasına yapılan olduğunu gösterir. Bir hata varsa iletinin hedef sıraya alınıyor, bu nedenle, gönderen uygulama hakkında hemen olmadığını bilemezsiniz. Bu tür hataları not almak için başarısız ileti sahipsiz sıraya aktarılır.  
  
 Hedef sıra ya da yaşam süresi sona ermekte ulaşmak başarısız olan bir ileti gibi herhangi bir hata ayrı olarak işlenmesi gerekir. Seyrek, bu nedenle, sıraya alınan uygulamaları iki mantığı yazmak değil:  
  
-   Normal istemci ve ileti gönderme ve alma, hizmet mantığı.  
  
-   Başarısız iletim veya teslim gelen iletileri işlemek için maaş mantığı.  
  
 Aşağıdaki bölümlerde bu kavramlar açıklanmaktadır.  
  
## <a name="dead-letter-queue-programming"></a>Sahipsiz Sıra programlama  
 Teslim edilemeyen iletiler sırası hedef sıra çeşitli nedenlerle geçemedi iletiler içerir. Nedenleri süresi dolan iletileri hedef sıraya ileti aktarımını önleme bağlantı sorunları değişebilir.  
  
 Genellikle, bir uygulama bir sistem genelinde sahipsiz sıraya alınan iletileri nelerin yanlış gittiğini belirlemek ve hatalarını düzeltme ve ileti veya alma Not yeniden göndermeyi gibi uygun eylemi gerçekleştirin okuyabilir.  
  
## <a name="poison-message-queue-programming"></a>Zehirli ileti sırası programlama  
 İsteğe bağlı olarak bir ileti hedef sıra yaptıktan sonra hizmet iletiyi işlemek sürekli olarak başarısız olabilir. Örneğin, bir uygulama geçici olarak bağlantısı kesilmiş veritabanı sıra bir işlem altında bir ileti okuma ve bir veritabanını güncelleştirme bulabilirsiniz. Bu durumda, işlem geri alındı, yeni bir işlem oluşturulur ve iletiyi sıradan yeniden okuyun. İkinci deneme başarılı veya başarısız. Hatanın nedenini bağlı olarak bazı durumlarda, ileti art arda uygulamaya teslim başarısız olabilir. Bu durumda, ileti "poison" kabul edilir Bu türden iletilere poison işleme uygulama tarafından okunabilir zararlı bir sıra taşınır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF'de kuyruğa alma](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [WCF'de kuyruğa alma](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [Oturumlar ve Kuyruklar](../../../../docs/framework/wcf/samples/sessions-and-queues.md)  
 [Teslim edilemeyen iletiler sırası](../../../../docs/framework/wcf/samples/dead-letter-queues.md)  
 [Geçici kuyruğa alınmış iletişim](../../../../docs/framework/wcf/samples/volatile-queued-communication.md)  
 [Message Queuing için Windows Communication Foundation](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)  
 [Message Queuing (MSMQ) yükleme](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)  
 [Message Queuing tümleştirme bağlama örnekleri](http://msdn.microsoft.com/en-us/997d11cb-f2c5-4ba0-9209-92843d4d0e1a)  
 [Windows Communication Foundation'a ileti kuyruğa alma](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)  
 [İleti kuyruğa alma ile ileti güvenliği](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)
