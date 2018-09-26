---
title: 'Nasıl yapılır: WCF Hizmeti İşlemlerini Zaman Uyumsuz Olarak Çağırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0face17f-43ca-417b-9b33-737c0fc360df
ms.openlocfilehash: 90e00e4264ff808151c9e1c58fdaf290765620c8
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47077726"
---
# <a name="how-to-call-wcf-service-operations-asynchronously"></a>Nasıl yapılır: WCF Hizmeti İşlemlerini Zaman Uyumsuz Olarak Çağırma
Bu konu nasıl bir istemci bir hizmet işlemi zaman uyumsuz olarak erişebileceğiniz kapsar. Bu konuda hizmeti uygulayan `ICalculator` arabirimi. İstemci bu arabirimdeki işlemleri olay tabanlı zaman uyumsuz çağırma modelini kullanarak zaman uyumsuz olarak çağırabilirsiniz. (Olay tabanlı zaman uyumsuz çağırma modeli hakkında daha fazla bilgi için bkz. [birden çok iş parçacıklı programlama ile olay tabanlı zaman uyumsuz desen](https://go.microsoft.com/fwlink/?LinkId=248184)). Nasıl bir işlem zaman uyumsuz olarak bir hizmet olarak uygulayacağınızı gösteren bir örnek için bkz: [nasıl yapılır: zaman uyumsuz bir hizmet işlemi uygulama](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md). Zaman uyumlu ve zaman uyumsuz işlemler hakkında daha fazla bilgi için bkz: [zaman uyumlu ve zaman uyumsuz işlemler](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).  
  
> [!NOTE]
>  Olay tabanlı zaman uyumsuz çağırma modeli kullanılırken desteklenmeyen bir <xref:System.ServiceModel.ChannelFactory%601>. Kullanarak zaman uyumsuz çağrıları yapma hakkında bilgi için <xref:System.ServiceModel.ChannelFactory%601>, bkz: [nasıl yapılır: çağrı işlemlerini zaman uyumsuz olarak kullanarak kanal fabrikası](../../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).  
  
## <a name="procedure"></a>Yordam  
  
#### <a name="to-call-wcf-service-operations-asynchronously"></a>WCF Hizmeti işlemlerini zaman uyumsuz olarak çağırmak için  
  
1.  Çalıştırma [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) hem aracıyla `/async` ve `/tcv:Version35` komutu seçenekleri birlikte aşağıdaki komutta gösterildiği gibi.  
  
    ```  
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a /tcv:Version35  
    ```  
  
     Bu, zaman uyumlu hem de standart temsilci tabanlı zaman uyumsuz işlemlerin yanı sıra, içeren bir WCF istemcisi sınıfı oluşturur:  
  
    -   İki <`operationName` > `Async` işlemleri ile olay tabanlı zaman uyumsuz çağırma yaklaşımı kullanmak için. Örneğin:  
  
         [!code-csharp[EventAsync#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#1)]
         [!code-vb[EventAsync#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#1)]  
  
    -   Formun işlemi tamamlandı olayları <`operationName` > `Completed` ile olay tabanlı zaman uyumsuz çağırma yaklaşımı kullanmak için. Örneğin:  
  
         [!code-csharp[EventAsync#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#2)]
         [!code-vb[EventAsync#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#2)]  
  
    -   <xref:System.EventArgs?displayProperty=nameWithType> Her işlem için türleri (form <`operationName`>`CompletedEventArgs`) ile olay tabanlı zaman uyumsuz çağırma yaklaşımı kullanmak için. Örneğin:  
  
         [!code-csharp[EventAsync#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#3)]
         [!code-vb[EventAsync#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#3)]  
  
2.  Zaman uyumsuz işlemi aşağıdaki örnek kodda gösterildiği gibi tamamlandığında çağrılacak bir geri çağırma yöntemi çağıran uygulamada oluşturun.  
  
     [!code-csharp[EventAsync#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#4)]
     [!code-vb[EventAsync#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#4)]  
  
3.  Yeni genel kullanma işlemi çağırmadan önce <xref:System.EventHandler%601?displayProperty=nameWithType> türü <`operationName` > `EventArgs` (önceki adımda oluşturulan) işleyicisi yöntemi eklemek için <`operationName` > `Completed` olay. Ardından çağırın <`operationName` > `Async` yöntemi. Örneğin:  
  
     [!code-csharp[EventAsync#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#5)]
     [!code-vb[EventAsync#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#5)]  
  
## <a name="example"></a>Örnek  
  
> [!NOTE]
>  Olay tabanlı zaman uyumsuz model için tasarım yönergeleri birden fazla değer döndürmüyorsa, bir değer olarak döndürülen durum `Result` özelliği ve diğerleri döndürülür özellikleri olarak üzerinde <xref:System.EventArgs> nesne. Bunun bir sonucu olduğundan, bu, bir istemci, olay tabanlı zaman uyumsuz komut seçeneklerini kullanarak meta verilerini içeri aktarır ve işlemin birden fazla değer, varsayılan döndürürse <xref:System.EventArgs> nesnesini bir değer olarak döndürür `Result` özelliği ve kalan özelliklerini <xref:System.EventArgs> nesne. İleti nesnesi olarak almak istiyorsanız `Result` özelliği ve o nesnenin özellikleri olarak döndürülen değerlerin `/messageContract` seçeneği komutu. Bu yanıt iletisi olarak döndüren bir imza oluşturur `Result` özelliği <xref:System.EventArgs> nesne. Tüm iç dönüş değerleri ardından yanıt iletisi nesnenin özellikleridir.  
  
 [!code-csharp[EventAsync#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#6)]
 [!code-vb[EventAsync#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#6)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Zaman Uyumsuz Bir Hizmet İşlemi Uygulama](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md)
