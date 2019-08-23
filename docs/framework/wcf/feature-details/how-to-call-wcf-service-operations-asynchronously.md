---
title: 'Nasıl yapılır: WCF hizmeti Işlemlerini zaman uyumsuz olarak çağır'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0face17f-43ca-417b-9b33-737c0fc360df
ms.openlocfilehash: 2d075bfebf7b5cbd2b2ce031a1c3855a925405a2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964027"
---
# <a name="how-to-call-wcf-service-operations-asynchronously"></a>Nasıl yapılır: WCF hizmeti Işlemlerini zaman uyumsuz olarak çağır
Bu konu, bir istemcinin bir hizmet işlemine zaman uyumsuz olarak nasıl erişebildiğini anlatmaktadır. Bu konudaki hizmet, `ICalculator` arabirimini uygular. İstemci, olay odaklı zaman uyumsuz çağrı modelini kullanarak bu arabirimdeki işlemleri zaman uyumsuz olarak çağırabilir. (Olay tabanlı zaman uyumsuz çağrı modeli hakkında daha fazla bilgi için bkz. çok [Iş parçacıklı programlama, olay tabanlı zaman uyumsuz model ile](https://go.microsoft.com/fwlink/?LinkId=248184)). Bir hizmette zaman uyumsuz bir işlemin nasıl uygulanacağını gösteren bir örnek için bkz [. nasıl yapılır: Zaman uyumsuz bir hizmet Işlemi](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md)uygulayın. Zaman uyumlu ve zaman uyumsuz işlemler hakkında daha fazla bilgi için bkz. [eşzamanlı ve zaman uyumsuz işlemler](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).  
  
> [!NOTE]
> Kullanılarak olay odaklı zaman uyumsuz çağırma modeli desteklenmez <xref:System.ServiceModel.ChannelFactory%601>. Kullanarak <xref:System.ServiceModel.ChannelFactory%601>zaman uyumsuz çağrılar yapma hakkında bilgi için bkz [. nasıl yapılır: Kanal fabrikası](../../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md)kullanarak işlemleri zaman uyumsuz olarak çağırın.  
  
## <a name="procedure"></a>Yordam  
  
#### <a name="to-call-wcf-service-operations-asynchronously"></a>WCF hizmeti işlemlerini zaman uyumsuz olarak çağırma  
  
1. Aşağıdaki komutta gösterildiği gibi, `/async` `/tcv:Version35` hem hem de komut seçenekleriyle birlikte [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) aracını çalıştırın.  
  
    ```  
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a /tcv:Version35  
    ```  
  
     Bu, zaman uyumlu ve standart temsilci tabanlı zaman uyumsuz işlemlere ek olarak şunları içeren bir WCF istemci sınıfı oluşturur:  
  
    - Olay tabanlı`operationName` zaman uyumsuz çağırma yaklaşımıyla birlikte kullanmak için iki <> `Async` işlemi. Örneğin:  
  
         [!code-csharp[EventAsync#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#1)]
         [!code-vb[EventAsync#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#1)]  
  
    - Olay tabanlı zaman uyumsuz çağırma yaklaşımıyla`operationName` kullanılmak üzere <> `Completed` form işlem tamamlandı olayları. Örneğin:  
  
         [!code-csharp[EventAsync#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#2)]
         [!code-vb[EventAsync#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#2)]  
  
    - <xref:System.EventArgs?displayProperty=nameWithType>Olay tabanlı zaman uyumsuz çağırma yaklaşımıyla kullanılmak üzere`operationName`her bir işlemin (form <>`CompletedEventArgs`) türleri. Örneğin:  
  
         [!code-csharp[EventAsync#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#3)]
         [!code-vb[EventAsync#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#3)]  
  
2. Çağıran uygulamada, aşağıdaki örnek kodda gösterildiği gibi zaman uyumsuz işlem tamamlandığında çağrılacak bir geri arama yöntemi oluşturun.  
  
     [!code-csharp[EventAsync#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#4)]
     [!code-vb[EventAsync#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#4)]  
  
3. İşlem <xref:System.EventHandler%601?displayProperty=nameWithType> çağrılmadan önce, <> `EventArgs` `operationName` olayınaişleyici`operationName` yöntemini (önceki adımda oluşturulan) eklemek için < türünde yeni bir genel kullanın.> `Completed` Sonra <`operationName` > yönteminiçağırın.`Async` Örneğin:  
  
     [!code-csharp[EventAsync#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#5)]
     [!code-vb[EventAsync#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#5)]  
  
## <a name="example"></a>Örnek  
  
> [!NOTE]
> Olay tabanlı zaman uyumsuz model için, birden fazla değer döndürülürse, `Result` özellik olarak bir değer döndürülür ve diğerleri <xref:System.EventArgs> nesne üzerinde özellikler olarak döndürülür. Bunun sonucunda, bir istemci, olay tabanlı zaman uyumsuz komut seçeneklerini kullanarak meta verileri içeri aktardığında ve işlem birden fazla değer döndürürse, varsayılan <xref:System.EventArgs> nesne `Result` özellik olarak bir değer döndürür ve geri kalanı <xref:System.EventArgs> nesnenin özellikleri. İleti nesnesini `Result` özellik olarak almak ve döndürülen değerlerin bu nesnede özellikler olarak elde etmek istiyorsanız, `/messageContract` komut seçeneğini kullanın. Bu, `Result` <xref:System.EventArgs> nesne üzerindeki özelliği olarak yanıt iletisini döndüren bir imza oluşturur. Tüm iç dönüş değerleri, yanıt iletisi nesnesinin özellikleridir.  
  
 [!code-csharp[EventAsync#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#6)]
 [!code-vb[EventAsync#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Zaman uyumsuz bir hizmet Işlemi uygulama](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md)
