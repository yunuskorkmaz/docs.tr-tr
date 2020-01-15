---
title: 'Nasıl yapılır: WCF Hizmeti İşlemlerini Zaman Uyumsuz Olarak Çağırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0face17f-43ca-417b-9b33-737c0fc360df
ms.openlocfilehash: 5eae08ab6b8dee5ebece66a1c41c87ebab3387bc
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/15/2020
ms.locfileid: "75963273"
---
# <a name="how-to-call-wcf-service-operations-asynchronously"></a>Nasıl yapılır: WCF Hizmeti İşlemlerini Zaman Uyumsuz Olarak Çağırma

Bu makalede, bir istemcinin bir hizmet işlemine zaman uyumsuz olarak nasıl erişebileceği ele alınmaktadır. Bu makaledeki hizmet `ICalculator` arabirimini uygular. İstemci, olay odaklı zaman uyumsuz çağrı modelini kullanarak bu arabirimdeki işlemleri zaman uyumsuz olarak çağırabilir. (Olay tabanlı zaman uyumsuz çağrı modeli hakkında daha fazla bilgi için bkz. çok [Iş parçacıklı programlama, olay tabanlı zaman uyumsuz model ile](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)). Bir hizmetin bir hizmette zaman uyumsuz olarak nasıl uygulanacağını gösteren bir örnek için bkz. [nasıl yapılır: Işlem zaman uyumsuz hizmet Işlemi uygulama](../how-to-implement-an-asynchronous-service-operation.md). Zaman uyumlu ve zaman uyumsuz işlemler hakkında daha fazla bilgi için bkz. [eşzamanlı ve zaman uyumsuz işlemler](../synchronous-and-asynchronous-operations.md).  
  
> [!NOTE]
> Olay odaklı zaman uyumsuz çağırma modeli <xref:System.ServiceModel.ChannelFactory%601>kullanılırken desteklenmez. <xref:System.ServiceModel.ChannelFactory%601>kullanarak zaman uyumsuz çağrılar yapma hakkında bilgi için bkz. [nasıl yapılır: bir kanal fabrikası kullanarak Işlemleri zaman uyumsuz olarak çağırma](../../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).  
  
## <a name="procedure"></a>Yordam  
  
#### <a name="to-call-wcf-service-operations-asynchronously"></a>WCF hizmeti işlemlerini zaman uyumsuz olarak çağırma  
  
1. Aşağıdaki komutta gösterildiği gibi hem `/async` hem de `/tcv:Version35` komutu seçenekleriyle birlikte [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) aracını çalıştırın.  
  
    ```console
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a /tcv:Version35  
    ```  
  
     Bu, zaman uyumlu ve standart temsilci tabanlı zaman uyumsuz işlemlere ek olarak şunları içeren bir WCF istemci sınıfı oluşturur:  
  
    - İki <`operationName`, olay tabanlı zaman uyumsuz çağırma yaklaşımıyla kullanım için `Async` >. Örneğin:  
  
         [!code-csharp[EventAsync#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#1)]
         [!code-vb[EventAsync#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#1)]  
  
    - `operationName`>`Completed` olay tabanlı zaman uyumsuz çağırma yaklaşımıyla kullanılacak işlem tamamlandı olayları. Örneğin:  
  
         [!code-csharp[EventAsync#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#2)]
         [!code-vb[EventAsync#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#2)]  
  
    - Olay tabanlı zaman uyumsuz çağırma yaklaşımıyla kullanılmak üzere her bir işlem için <xref:System.EventArgs?displayProperty=nameWithType> türler (`operationName`>`CompletedEventArgs`) <. Örneğin:  
  
         [!code-csharp[EventAsync#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#3)]
         [!code-vb[EventAsync#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#3)]  
  
2. Çağıran uygulamada, aşağıdaki örnek kodda gösterildiği gibi zaman uyumsuz işlem tamamlandığında çağrılacak bir geri arama yöntemi oluşturun.  
  
     [!code-csharp[EventAsync#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#4)]
     [!code-vb[EventAsync#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#4)]  
  
3. İşlem çağrılmadan önce, <`operationName`>`EventArgs` yeni bir genel <xref:System.EventHandler%601?displayProperty=nameWithType> kullanın (önceki adımda oluşturulan) <`operationName`>olayına işleyici metodunu eklemek için. Sonra <`operationName`>`Async` yöntemini çağırın. Örneğin:  
  
     [!code-csharp[EventAsync#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#5)]
     [!code-vb[EventAsync#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#5)]  
  
## <a name="example"></a>Örnek  
  
> [!NOTE]
> Olay tabanlı zaman uyumsuz model için, birden fazla değer döndürülürse, bir değer `Result` özellik olarak döndürülür ve diğerleri <xref:System.EventArgs> nesnesi üzerinde özellikler olarak döndürülür. Bunun sonucunda, bir istemci, olay tabanlı zaman uyumsuz komut seçeneklerini kullanarak meta verileri içeri aktardığında ve işlem birden fazla değer döndürürse, varsayılan <xref:System.EventArgs> nesnesi bir değeri `Result` özelliği olarak döndürür ve geri kalan <xref:System.EventArgs> nesnesinin özellikleridir. İleti nesnesini `Result` özelliği olarak almak ve döndürülen değerlerin bu nesnede özellikler olarak elde etmek istiyorsanız, `/messageContract` komut seçeneğini kullanın. Bu, <xref:System.EventArgs> nesnesinde `Result` özelliği olarak yanıt iletisini döndüren bir imza oluşturur. Tüm iç dönüş değerleri, yanıt iletisi nesnesinin özellikleridir.  
  
 [!code-csharp[EventAsync#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#6)]
 [!code-vb[EventAsync#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Zaman Uyumsuz Bir Hizmet İşlemi Uygulama](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md)
