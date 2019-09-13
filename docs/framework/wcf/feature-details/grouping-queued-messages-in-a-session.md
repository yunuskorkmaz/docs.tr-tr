---
title: Oturumda Kuyruğa Alınmış İletileri Gruplandırma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- queues [WCF]. grouping messages
ms.assetid: 63b23b36-261f-4c37-99a2-cc323cd72a1a
ms.openlocfilehash: 995697e618ff5d56a719efc5d69b97583733d980
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70892745"
---
# <a name="grouping-queued-messages-in-a-session"></a>Oturumda Kuyruğa Alınmış İletileri Gruplandırma
Windows Communication Foundation (WCF), bir dizi ilgili iletiyi tek bir alıcı uygulamayla işlemek üzere gruplandırmaya olanak tanıyan bir oturum sağlar. Bir oturumun parçası olan mesajlar aynı işlemin parçası olmalıdır. Tüm iletiler aynı işlemin parçası olduğundan, bir ileti işlenemezse tüm oturum geri alınır. Oturumlar, atılacak ileti kuyrukları ve zarar kuyruklarıyla ilgili benzer davranışları vardır. Oturumlar için yapılandırılmış bir sıraya alınmış bağlamada ayarlanan yaşam süresi (TTL) özelliği, oturuma bir bütün olarak uygulanır. Oturumun yalnızca bir kısmı TTL 'nin süresi dolmadan önce gönderilirse, tüm oturum atılacak ileti kuyruğuna yerleştirilir. Benzer şekilde, bir oturumdaki iletiler uygulama kuyruğundan bir uygulamaya gönderilemezse, tüm oturum zarar sırasına (varsa) yerleştirilir.  
  
## <a name="message-grouping-example"></a>İleti gruplandırma örneği  
 Bir örnek iletileri, bir WCF hizmeti olarak bir sıra işleme uygulaması uygularken yararlı olduğu bir örnektir. Örneğin, bir istemci bu uygulamaya bir dizi öğe içeren bir sıra gönderir. İstemci, her öğe için hizmete bir çağrı yapar ve bu, ayrı bir ileti gönderilmesine neden olur. İlk öğeyi almak için A hizmeti ve ikinci öğeyi almak için sunucu B 'yi sağlamak mümkündür. Her öğe eklendiğinde, bu öğeyi işleyen sunucu uygun siparişi bulmak ve öğeyi bu öğeye eklemek için çok verimsiz bir işlem olur. Yalnızca tüm istekleri işleyen tek bir sunucu ile bu verimsizlikleri içinde çalışmaya devam edersiniz, çünkü sunucu işlenmekte olan tüm siparişlerin izlenmesini ve yeni öğenin ait olduğunu tespit etmelidir. Tek bir sıraya yönelik tüm isteklerin gruplandırılması, bu tür bir uygulamanın uygulanmasını büyük ölçüde basitleştirir. İstemci uygulaması tüm öğeleri bir oturumda tek bir sıraya gönderir; bu nedenle hizmet siparişi işlediğinde, tüm oturumu aynı anda işler. \  
  
## <a name="procedures"></a>Yordamlar  
  
#### <a name="to-set-up-a-service-contract-to-use-sessions"></a>Oturumları kullanmak üzere bir hizmet sözleşmesi ayarlamak için  
  
1. Oturum gerektiren bir hizmet sözleşmesi tanımlayın. Şunu belirterek bunu özniteliğiyle yapın: <xref:System.ServiceModel.ServiceContractAttribute>  
  
    ```csharp
    SessionMode=SessionMode.Required  
    ```  
  
2. Bu yöntemlerin hiçbir şey döndürmediği için sözleşmede işlemleri tek yönlü olarak işaretleyin. Bu, <xref:System.ServiceModel.OperationContractAttribute> özniteliği belirtilerek yapılır:  
  
    ```csharp  
    [OperationContract(IsOneWay = true)]  
    ```  
  
3. Hizmet sözleşmesini uygulayın ve bir <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode> <xref:System.ServiceModel.InstanceContextMode.PerSession?displayProperty=nameWithType>' i belirtin. Bu, her oturum için hizmeti yalnızca bir kez başlatır.  
  
    ```csharp  
    [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
    ```  
  
4. Her hizmet işlemi için bir işlem gerekir. Bunu <xref:System.ServiceModel.OperationBehaviorAttribute> özniteliğiyle birlikte belirtin. İşlemi tamamlayan işlem de olarak <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete> `true`ayarlanmalıdır.  
  
    ```csharp  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]   
    ```  
  
5. Sistem tarafından sağlanmış `NetMsmqBinding` bağlamayı kullanan bir uç nokta yapılandırın.  
  
6. Kullanarak <xref:System.Messaging>bir işlem kuyruğu oluşturun. Kuyruğu Message Queuing (MSMQ) veya MMC kullanarak da oluşturabilirsiniz. Bunu yaparsanız, bir işlem kuyruğu oluşturun.  
  
7. Kullanarak <xref:System.ServiceModel.ServiceHost>hizmet için bir hizmet ana bilgisayarı oluşturun.  
  
8. Hizmeti kullanılabilir hale getirmek için hizmet ana bilgisayarını açın.  
  
9. Hizmet konağını kapatın.  
  
#### <a name="to-set-up-a-client"></a>Bir istemciyi ayarlamak için  
  
1. İşlemsel sıraya yazılacak bir işlem kapsamı oluşturun.  
  
2. [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ARACıNı kullanarak WCF istemcisi oluşturun.  
  
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

- [Oturumlar ve Kuyruklar](../../../../docs/framework/wcf/samples/sessions-and-queues.md)
- [Kuyruklara Genel Bakış](../../../../docs/framework/wcf/feature-details/queues-overview.md)
