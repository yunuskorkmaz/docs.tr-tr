---
title: Oturumda Kuyruğa Alınmış İletileri Gruplandırma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- queues [WCF]. grouping messages
ms.assetid: 63b23b36-261f-4c37-99a2-cc323cd72a1a
ms.openlocfilehash: 231310e5c427f507141e3c144cb02b8e848d4fbf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185154"
---
# <a name="grouping-queued-messages-in-a-session"></a>Oturumda Kuyruğa Alınmış İletileri Gruplandırma
Windows Communication Foundation (WCF), ilgili iletiler kümesini tek bir alıcı uygulama tarafından işlenmek üzere gruplandırmanızı sağlayan bir oturum sağlar. Oturumun parçası olan iletiler aynı işlemin parçası olmalıdır. Tüm iletiler aynı işlemin parçası olduğundan, bir ileti işlenmezse tüm oturum geri alınır. Oturumlar ölü harf kuyrukları ve zehir kuyrukları ile ilgili benzer davranışlara sahiptir. Oturumlar için yapılandırılan sıralı bir bağlama üzerinde ayarlanmış Yaşam Süresi (TTL) özelliği oturuma bir bütün olarak uygulanır. Oturumdaki iletilerin yalnızca bazıları TTL'nin süresi dolmadan önce gönderilirse, oturumun tamamı ölü harf sırasına yerleştirilir. Benzer şekilde, oturumdaki iletiler uygulama kuyruğundan bir uygulamaya gönderilmediğinde, tüm oturum zehir kuyruğuna (varsa) yerleştirilir.  
  
## <a name="message-grouping-example"></a>İleti Gruplandırma Örneği  
 İletileri gruplandırmanın yararlı olduğu durumlardan biri, bir Sipariş işleme uygulamasını WCF hizmeti olarak uygularken elde edilir. Örneğin, bir istemci bu uygulamaya bir dizi öğe içeren bir sipariş gönderir. Her öğe için istemci hizmete çağrı yapar ve bu da ayrı bir iletinin gönderilmesiyle sonuçlanır. Hizmetin A'nın ilk öğeyi alması, Sunucu B'nin ikinci öğeyi alması mümkündür. Her öğe eklendiğinde, sunucu bu öğeyi işleme uygun siparişi bulmak ve son derece verimsiz olan öğeyi eklemek zorundadır. Sunucunun şu anda işlenen tüm siparişleri izlemesi ve yeni öğenin hangisine ait olduğunu belirlemesi gerektiğinden, tüm istekleri yalnızca tek bir sunucuyla bu tür verimsizliklerle karşınıza çıkabilirsiniz. Tek bir sipariş için tüm istekleri gruplandırma büyük ölçüde böyle bir uygulamanın uygulanmasını kolaylaştırır. İstemci uygulaması bir oturumda tek bir sipariş için tüm öğeleri gönderir, bu nedenle hizmet siparişi işlerse, tüm oturumu aynı anda işler. \  
  
## <a name="procedures"></a>Yordamlar  
  
#### <a name="to-set-up-a-service-contract-to-use-sessions"></a>Oturumları kullanmak için bir hizmet sözleşmesi ayarlamak için  
  
1. Oturum gerektiren bir hizmet sözleşmesi tanımlayın. Belirterek öznitelik ile <xref:System.ServiceModel.ServiceContractAttribute> bunu yapın:  
  
    ```csharp
    SessionMode=SessionMode.Required  
    ```  
  
2. Bu yöntemler hiçbir şeyi döndürmediği için sözleşmedeki işlemleri tek yönlü olarak işaretleyin. Bu belirterek <xref:System.ServiceModel.OperationContractAttribute> öznitelik ile yapılır:  
  
    ```csharp  
    [OperationContract(IsOneWay = true)]  
    ```  
  
3. Hizmet sözleşmesini uygulayın <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode> ve <xref:System.ServiceModel.InstanceContextMode.PerSession?displayProperty=nameWithType>bir . Bu, her oturum için yalnızca bir kez hizmeti anında verir.  
  
    ```csharp  
    [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
    ```  
  
4. Her hizmet işlemi bir işlem gerektirir. Bunu öznitelik <xref:System.ServiceModel.OperationBehaviorAttribute> ile belirtin. İşlemi tamamlayan işlem de ' <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete> `true`olarak ayarlanmalıdır.  
  
    ```csharp  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    ```  
  
5. Sistem tarafından sağlanan `NetMsmqBinding` bağlamayı kullanan bir bitiş noktası yapılandırın.  
  
6. 'yi kullanarak <xref:System.Messaging>bir işlem sırası oluşturun. İleti Sıralaması (MSMQ) veya MMC'yi kullanarak da sıra oluşturabilirsiniz. Bunu yaparsanız, bir işlem sırası oluşturun.  
  
7. Kullanarak hizmet için bir hizmet <xref:System.ServiceModel.ServiceHost>ana bilgisayar oluşturun.  
  
8. Hizmeti kullanılabilir hale getirmek için servis ana bilgisayarını açın.  
  
9. Servis ana bilgisayarını kapatın.  
  
#### <a name="to-set-up-a-client"></a>İstemci ayarlamak için  
  
1. İşlem sırasına yazmak için bir hareket kapsamı oluşturun.  
  
2. [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) aracını kullanarak WCF istemcisini oluşturun.  
  
3. Siparişi ver.  
  
4. WCF istemcisini kapatın.  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek, hizmetin `IProcessOrder` ve bu hizmeti kullanan bir istemcinin kodunu sağlar. WCF'nin gruplandırma davranışını sağlamak için sıraya girilen oturumları nasıl kullandığını gösterir.  
  
### <a name="code-for-the-service"></a>Hizmet Kodu  
 [!code-csharp[S_Msmq_Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/service.cs#1)]
 [!code-vb[S_Msmq_Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/service.vb#1)]  

### <a name="code-for-the-client"></a>İstemci kodu  
 [!code-csharp[S_Msmq_Session#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/client.cs#3)]
 [!code-vb[S_Msmq_Session#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/client.vb#3)]  

## <a name="see-also"></a>Ayrıca bkz.

- [Oturumlar ve Kuyruklar](../../../../docs/framework/wcf/samples/sessions-and-queues.md)
- [Kuyruklar Genel Bakış](../../../../docs/framework/wcf/feature-details/queues-overview.md)
