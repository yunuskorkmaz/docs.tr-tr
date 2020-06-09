---
title: Oturumda Kuyruğa Alınmış İletileri Gruplandırma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- queues [WCF]. grouping messages
ms.assetid: 63b23b36-261f-4c37-99a2-cc323cd72a1a
ms.openlocfilehash: 66f51267f20f8cdad8feeedf37435ccfa733146e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597364"
---
# <a name="grouping-queued-messages-in-a-session"></a>Oturumda Kuyruğa Alınmış İletileri Gruplandırma
Windows Communication Foundation (WCF), bir dizi ilgili iletiyi tek bir alıcı uygulamayla işlemek üzere gruplandırmaya olanak tanıyan bir oturum sağlar. Bir oturumun parçası olan mesajlar aynı işlemin parçası olmalıdır. Tüm iletiler aynı işlemin parçası olduğundan, bir ileti işlenemezse tüm oturum geri alınır. Oturumlar, atılacak ileti kuyrukları ve zarar kuyruklarıyla ilgili benzer davranışları vardır. Oturumlar için yapılandırılmış bir sıraya alınmış bağlamada ayarlanan yaşam süresi (TTL) özelliği, oturuma bir bütün olarak uygulanır. Oturumun yalnızca bir kısmı TTL 'nin süresi dolmadan önce gönderilirse, tüm oturum atılacak ileti kuyruğuna yerleştirilir. Benzer şekilde, bir oturumdaki iletiler uygulama kuyruğundan bir uygulamaya gönderilemezse, tüm oturum zarar sırasına (varsa) yerleştirilir.  
  
## <a name="message-grouping-example"></a>İleti gruplandırma örneği  
 Bir örnek iletileri, bir WCF hizmeti olarak bir sıra işleme uygulaması uygularken yararlı olduğu bir örnektir. Örneğin, bir istemci bu uygulamaya bir dizi öğe içeren bir sıra gönderir. İstemci, her öğe için hizmete bir çağrı yapar ve bu, ayrı bir ileti gönderilmesine neden olur. İlk öğeyi almak için A hizmeti ve ikinci öğeyi almak için sunucu B 'yi sağlamak mümkündür. Her öğe eklendiğinde, bu öğeyi işleyen sunucu uygun siparişi bulmak ve öğeyi bu öğeye eklemek için çok verimsiz bir işlem olur. Yalnızca tüm istekleri işleyen tek bir sunucu ile bu verimsizlikleri içinde çalışmaya devam edersiniz, çünkü sunucu işlenmekte olan tüm siparişlerin izlenmesini ve yeni öğenin ait olduğunu tespit etmelidir. Tek bir sıraya yönelik tüm isteklerin gruplandırılması, bu tür bir uygulamanın uygulanmasını büyük ölçüde basitleştirir. İstemci uygulaması tüm öğeleri bir oturumda tek bir sıraya gönderir; bu nedenle hizmet siparişi işlediğinde, tüm oturumu aynı anda işler. \  
  
## <a name="procedures"></a>Yordamlar  
  
#### <a name="to-set-up-a-service-contract-to-use-sessions"></a>Oturumları kullanmak üzere bir hizmet sözleşmesi ayarlamak için  
  
1. Oturum gerektiren bir hizmet sözleşmesi tanımlayın. Şunu <xref:System.ServiceModel.ServiceContractAttribute> belirterek bunu özniteliğiyle yapın:  
  
    ```csharp
    SessionMode=SessionMode.Required  
    ```  
  
2. Bu yöntemlerin hiçbir şey döndürmediği için sözleşmede işlemleri tek yönlü olarak işaretleyin. Bu, <xref:System.ServiceModel.OperationContractAttribute> özniteliği belirtilerek yapılır:  
  
    ```csharp  
    [OperationContract(IsOneWay = true)]  
    ```  
  
3. Hizmet sözleşmesini uygulayın ve bir ' i <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode> belirtin <xref:System.ServiceModel.InstanceContextMode.PerSession?displayProperty=nameWithType> . Bu, her oturum için hizmeti yalnızca bir kez başlatır.  
  
    ```csharp  
    [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
    ```  
  
4. Her hizmet işlemi için bir işlem gerekir. Bunu özniteliğiyle birlikte belirtin <xref:System.ServiceModel.OperationBehaviorAttribute> . İşlemi tamamlayan işlem de <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete> olarak ayarlanmalıdır `true` .  
  
    ```csharp  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    ```  
  
5. Sistem tarafından sağlanmış bağlamayı kullanan bir uç nokta yapılandırın `NetMsmqBinding` .  
  
6. Kullanarak bir işlem kuyruğu oluşturun <xref:System.Messaging> . Kuyruğu Message Queuing (MSMQ) veya MMC kullanarak da oluşturabilirsiniz. Bunu yaparsanız, bir işlem kuyruğu oluşturun.  
  
7. Kullanarak hizmet için bir hizmet ana bilgisayarı oluşturun <xref:System.ServiceModel.ServiceHost> .  
  
8. Hizmeti kullanılabilir hale getirmek için hizmet ana bilgisayarını açın.  
  
9. Hizmet konağını kapatın.  
  
#### <a name="to-set-up-a-client"></a>Bir istemciyi ayarlamak için  
  
1. İşlemsel sıraya yazılacak bir işlem kapsamı oluşturun.  
  
2. [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) ARACıNı kullanarak WCF istemcisi oluşturun.  
  
3. Siparişi yerleştir.  
  
4. WCF istemcisini kapatın.  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek, `IProcessOrder` hizmetine ve bu hizmeti kullanan bir istemciye yönelik kodu sağlar. WCF 'nin gruplandırma davranışını sağlamak için sıraya alınan oturumları nasıl kullandığını gösterir.  
  
### <a name="code-for-the-service"></a>Hizmet kodu  
 [!code-csharp[S_Msmq_Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/service.cs#1)]
 [!code-vb[S_Msmq_Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/service.vb#1)]  

### <a name="code-for-the-client"></a>Istemci için kod  
 [!code-csharp[S_Msmq_Session#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/client.cs#3)]
 [!code-vb[S_Msmq_Session#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/client.vb#3)]  

## <a name="see-also"></a>Ayrıca bkz.

- [Oturumlar ve Kuyruklar](../samples/sessions-and-queues.md)
- [Kuyruklar Genel Bakış](queues-overview.md)
