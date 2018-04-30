---
title: Bir İşlemde Toplu İleti İşleme
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- batching messages [WCF]
ms.assetid: 53305392-e82e-4e89-aedc-3efb6ebcd28c
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 17d9bd3b58e8320bfe1f62ac56aff59ba52f4374
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="batching-messages-in-a-transaction"></a>Bir İşlemde Toplu İleti İşleme
Sıraya alınan uygulamaları işlemleri doğruluk ve iletilerin güvenilir teslimini emin olmak için kullanın. İşlemler, ancak pahalı işlemleri ve ileti işleme önemli ölçüde azaltabilir. İleti verimini artırmak için bir uygulamanın okuma ve tek bir işlem içinde birden çok iletileri işlemek için yoludur. Performans ve kurtarma arasında dengelemeyi olduğundan: toplu ileti sayısı arttıkça, bu nedenle işlemler geri alınacak, gerekli kurtarma iş miktarı verir. Toplu işlem ve oturumları ileti işleme arasındaki farkı dikkate almak önemlidir. A *oturum* tek bir uygulama tarafından işlenen ve tek bir birim olarak kabul edilen ilgili iletiler grubudur. Oturumlar, genellikle bir grup ilgili iletiler birlikte işlenmesi gereken olduğunda kullanılır. Bunun bir örneğini çevrimiçi bir alışveriş Web sitesidir. *Toplu* birden çok işlemek için kullanılan, ilgisiz artar verimlilik ileti şekilde iletileri. Oturumları hakkında daha fazla bilgi için bkz: [gruplandırma sıraya alınan iletileri bir oturumda](../../../../docs/framework/wcf/feature-details/grouping-queued-messages-in-a-session.md). Bir toplu iletiler de tek bir uygulama tarafından işlenen ve tek bir birim olarak kabul edilen, ancak toplu iletileri arasında hiçbir ilişki olabilir. Bir işlemde toplu ileti işleme, uygulama nasıl çalışacağını değişmeyen bir hale getirilmesidir.  
  
## <a name="entering-batching-mode"></a>Toplu işleme modunu girme  
 <xref:System.ServiceModel.Description.TransactedBatchingBehavior> Toplu işleme uç noktası davranışı denetimleri. Bu uç noktası davranışı bir hizmet uç noktası ekleme söyler [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] bir işlemde toplu iletileri. Bir işlem gerektiren yalnızca iletileri bir toplu işlemde yerleştirilir bunu tüm iletileri bir işlem gerektirir ve yalnızca işlemlerinden gönderilen iletiler ile işaretlenen `TransactionScopeRequired`  =  `true` ve `TransactionAutoComplete`  =  `true` olan Toplu işlem için kabul edilir. Hizmet sözleşmesi tüm işlemler ile işaretlenmiş ise `TransactionScopeRequired`  =  `false` ve `TransactionAutoComplete`  =  `false`, toplu işlem modu hiç girilmedi sonra.  
  
## <a name="committing-a-transaction"></a>Bir işlem yapılıyor  
 Bir toplu işlem, aşağıdaki ölçütlere dayalı taahhüt eder:  
  
-   `MaxBatchSize`. Bir özelliği <xref:System.ServiceModel.Description.TransactedBatchingBehavior> davranışı. Bu özellik toplu yerleştirilir iletilerin sayısını belirler. Bu sayıya ulaşıldığında, toplu taahhüt eder. Bu değer katı bir sınır değil, bu ileti sayısı almadan önce bir toplu iş yürütme mümkündür.  
  
-   `Transaction Timeout`. Yüzde 80'işlemdeki zaman aşımı geçtikten sonra toplu taahhüt eder ve yeni bir toplu işi oluşturulur. Bu, yüzde 20 anlamına gelir veya bir işlem için verilen süreyi daha az korunur, toplu taahhüt eder.  
  
-   `TransactionScopeRequired`. Toplu iletiler, varsa işlerken [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sahip bir tane bulana `TransactionScopeRequired`  =  `false`, toplu işi tamamlar ve yeni bir toplu işi ile ilk iletinin alınması, üzerinde açana `TransactionScopeRequired`  =  `true` ve `TransactionAutoComplete` = `true`.  
  
-   Sırada başka ileti mevcut sonra geçerli toplu işlem kararlıdır olsa bile `MaxBatchSize` ulaşılana veya yüzde 80'işlemdeki zaman aşımı geçtikten değil.  
  
## <a name="leaving-batching-mode"></a>Toplu işleme modunu bırakarak  
 Bir ileti bir toplu işlemin iptal etmek neden olursa, aşağıdaki adımlardan oluşur:  
  
1.  Toplu işin tamamını iletilerinin geri alınır.  
  
2.  İleti iki kez Maksimum toplu iş boyutu okuma iletilerin sayısını aşıyor kadar bir kerede salt okunurdur.  
  
3.  Toplu iş modunda yeniden girilen ' dir.  
  
## <a name="choosing-the-batch-size"></a>Toplu iş boyutu seçme  
 Bir toplu iş boyutu uygulama bağımlıdır. Ampirik yöntemi, bir uygulama için en iyi toplu boyutta ulaşması için en iyi yoludur. Uygulamanızın gerçek dağıtım modeli göre boyutu seçmek için bir toplu iş boyutu seçerken unutmamak önemlidir. Örneğin, uzak makine ve sıra yayılan bir işlem üzerinde bir SQL server ve SQL server gerekiyorsa Uygulama dağıtırken, ardından toplu iş boyutu en iyi tam bu yapılandırma çalışan tarafından belirlenir.  
  
## <a name="concurrency-and-batching"></a>Eşzamanlılık ve toplu işleme  
 Verimliliğini artırmak için de aynı anda çalışacak birçok toplu sahip olabilir. Ayarlayarak `ConcurrencyMode.Multiple` içinde `ServiceBehaviorAttribute`, eş zamanlı toplu etkinleştirme.  
  
 *Hizmet azaltma* hizmette kaç maksimum eşzamanlı çağrı yapılabilmesi için göstermek için kullanılan bir hizmet davranıştır. Çok sayıda eş zamanlı toplu çalıştırılabilir nasıl toplu işleme ile kullanıldığında, bu yorumlanır. Azaltma hizmet ayarlanmamışsa [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] en fazla eşzamanlı çağrıları 16 Varsayılanları. Toplu işleme davranışı varsayılan olarak eklendiyse, bu nedenle, en fazla 16 toplu işlemler aynı anda etkin olabilir. Azaltma hizmet ayarlamak en iyisidir ve kapasite toplu işleme dayalı. İşleme bağlı olarak 16 işlemleri olabileceğinden, etkin, açık toplu işleme olmamasından benzer Örneğin, 100 iletileri kuyruğa varsa ve 20 toplu istenen, 16'ya ayarlanmış maksimum eşzamanlı çağrıları sahip yararlı değil. Bu nedenle, performansı için ince ayar olduğunda değil eşzamanlı toplu işleme sahip ya da eş zamanlı doğru hizmet kısıtlama boyutuyla toplu işleme sahip.  
  
## <a name="batching-and-multiple-endpoints"></a>Toplu işleme ve birden çok uç noktaları  
 Bir uç nokta bir adresi ve bir sözleşme oluşur. Aynı bağlama paylaşan birden çok uç nokta olabilir. Aynı bağlama paylaşma ve Tekdüzen Kaynak Tanımlayıcısı (URI) veya sıra adresini dinlemek iki uç nokta için mümkündür. İki uç nokta aynı sıra okunurken ve işlenen ise davranışı toplu işleme, her iki uç noktaları, belirtilen boyutlarını meydana gelebilecek toplu işlemindeki bir çakışma eklenir. Bu, iki işlenen toplu davranışları arasında belirtilen en düşük toplu iş boyutu kullanarak toplu işleme uygulayarak çözümlenir. Uç noktalardan biri işlenen toplu işleme, belirtmiyor Bu senaryoda, ardından her iki uç noktaları toplu işleme kullanmamanız.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte nasıl belirtileceğini gösterir `TransactedBatchingBehavior` bir yapılandırma dosyası.  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="TransactedBatchingBehavior"
              maxBatchSize="100" />
  </endpointBehaviors>
</behaviors>
```  
  
 Aşağıdaki örnekte nasıl belirtileceğini gösterir <xref:System.ServiceModel.Description.TransactedBatchingBehavior> kod.  
  
```csharp
using (ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService)))
{
     ServiceEndpoint sep = ServiceHost.AddServiceEndpoint(typeof(IOrderProcessor), new NetMsmqBinding(), "net.msmq://localhost/private/ServiceModelSamplesTransacted");
     sep.Behaviors.Add(new TransactedBatchingBehavior(100));
     
     // Open the ServiceHost to create listeners and start listening for messages.
    serviceHost.Open();
  
    // The service can now be accessed.
    Console.WriteLine("The service is ready.");
    Console.WriteLine("Press <ENTER> to terminate service.");
    Console.WriteLine();
    Console.ReadLine();
  
    // Close the ServiceHostB to shut down the service.
    serviceHost.Close();
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kuyruklara Genel Bakış](../../../../docs/framework/wcf/feature-details/queues-overview.md)  
 [WCF'de Kuyruğa Alma](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)
