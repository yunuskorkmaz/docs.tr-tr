---
title: Oturumda Kuyruğa Alınmış İletileri Gruplandırma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- queues [WCF]. grouping messages
ms.assetid: 63b23b36-261f-4c37-99a2-cc323cd72a1a
ms.openlocfilehash: 37f0874ea99ee928e49a54a3e6a05ea4ef06f84e
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59294671"
---
# <a name="grouping-queued-messages-in-a-session"></a>Oturumda Kuyruğa Alınmış İletileri Gruplandırma
Windows Communication Foundation (WCF) tarafından tek bir alıcı uygulamanın bir dizi ilgili ileti işleme için bir arada gruplandırmak izin veren bir oturum sağlar. Bir oturumun parçasıdır iletileri aynı işlemin bir parçası olmalıdır. Tüm oturum işlenmek üzere bir ileti başarısız olursa tüm iletiler aynı işlemin bir parçası olduğundan geri alınır. Oturumları edilemeyen ve zehirli kuyrukları benzer davranışlara sahip. Oturumları için yapılandırılmış bir kuyruğa alınmış bağlaması üzerindeki yaşam süresi (TTL) özelliği zaman oturum bir bütün olarak uygulanır. Yalnızca TTL'nin süresi dolmadan önce bazı oturumdaki iletiler gönderilir, tüm oturumda edilemeyen sırasına konur. Benzer şekilde, uygulama kuyruktan bir uygulamaya gönderilecek bir oturumda ileti başarısız olursa, tüm oturumda (varsa) zehirli sıraya konur.  
  
## <a name="message-grouping-example"></a>İleti gruplama örneği  
 İletileri gruplandırma yararlı olduğu bir örnek, bir sipariş işleme uygulaması bir WCF hizmeti olarak uygularken verilebilir. Örneğin, bir istemci birçok öğe içeren bu uygulama için bir sipariş gönderir. Her öğe için istemci ayrı bir ileti gönderilmekte olan sonuçları hizmetine çağrıda bulunur. İkinci öğe almak için Sunucu B ve ilk öğeyi almak, hizmet A mümkündür. Her zaman uygun sırayı bulmak ve öğe eklemek bu öğe işleme sunucunun sahip bir öğe eklendiğinde, son derece verimsizdir. Sunucu şu anda işlenmekte olan tüm siparişleri izlemek ve yeni öğenin ait olduğu hangisinin belirlemek için tüm istekleri işleme yalnızca tek bir sunucuyla yine de böyle verimsizlikleri çalıştırın. Tüm istekler tek bir sipariş için büyük ölçüde gruplandırma tür bir uygulamanın uygulama basitleştirir. İstemci uygulama, tek bir sipariş için tüm öğeleri bir oturumda gönderir. hizmet sırası işlediğinde, tek seferde tüm oturum işler için. \  
  
## <a name="procedures"></a>Yordamlar  
  
#### <a name="to-set-up-a-service-contract-to-use-sessions"></a>Oturumlarının kullanmak için bir hizmet anlaşmasını oluşturan ayarlamak için  
  
1. Bir oturum gerektiren bir hizmet sözleşmesini tanımlama. İle bunu <xref:System.ServiceModel.OperationContractAttribute> özniteliği ve belirterek:  
  
    ```  
    SessionMode=SessionMode.Required  
    ```  
  
2. Bu yöntemlerin herhangi bir şey döndürmeyen çünkü tek yönlü olarak sözleşme işlemlerinde işaretleyin. Bunun <xref:System.ServiceModel.OperationContractAttribute> özniteliği ve belirterek:  
  
    ```  
    [OperationContract(IsOneWay = true)]  
    ```  
  
3. Hizmet sözleşmesini uygulama ve belirtin bir `InstanceContextMode` , `PerSession`. Bu hizmet her oturum için yalnızca bir kez başlatır.  
  
    ```  
    [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
    ```  
  
4. Her hizmet işlemi, bir işlem gerektirir. Bu konuda belirtin <xref:System.ServiceModel.OperationBehaviorAttribute> özniteliği. İşlem tamamlandığında işlemi de ayarlamalısınız `TransactionAutoComplete` için `true`.  
  
    ```  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]   
    ```  
  
5. Sistem tarafından sağlanan kullanan bir uç nokta yapılandırma `NetMsmqBinding` bağlama.  
  
6. Bir işlem sırası kullanarak oluşturma <xref:System.Messaging>. Message Queuing (MSMQ) veya MMC kullanarak kuyruk oluşturabilirsiniz. Bunu yaparsanız, bir işlem kuyruğu oluşturun.  
  
7. Kullanarak bir hizmet konağı için hizmet oluşturma <xref:System.ServiceModel.ServiceHost>.  
  
8. Hizmet kullanılabilir hale getirmek için hizmet ana bilgisayarı açın.  
  
9. Hizmet ana bilgisayarını kapatın.  
  
#### <a name="to-set-up-a-client"></a>Bir istemcinin ayarlamak için  
  
1. İşlem kuyruğa yazmak için bir işlem kapsamı oluşturun.  
  
2. Kullanarak bir WCF istemcisi oluşturma [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) aracı.  
  
3. Sipariş verin.  
  
4. WCF İstemcisi'ni kapatın.  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek kodunu sağlar `IProcessOrder` hizmet ve bir istemci için bu hizmeti kullanır. Bu, kuyruğa alınmış oturumları WCF gruplandırma davranışı sağlamak için nasıl kullandığını gösterir.  
  
### <a name="code-for-the-service"></a>Hizmet kodu  
 [!code-csharp[S_Msmq_Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/service.cs#1)]
 [!code-vb[S_Msmq_Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/service.vb#1)]  

### <a name="code-for-the-client"></a>İstemci kodu  
 [!code-csharp[S_Msmq_Session#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/client.cs#3)]
 [!code-vb[S_Msmq_Session#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/client.vb#3)]  

## <a name="see-also"></a>Ayrıca bkz.

- [Oturumlar ve Kuyruklar](../../../../docs/framework/wcf/samples/sessions-and-queues.md)
- [Kuyruklar Genel Bakış](../../../../docs/framework/wcf/feature-details/queues-overview.md)
