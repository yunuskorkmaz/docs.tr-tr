---
title: "Nasıl yapılır: WCF Hizmeti İşlemlerini Zaman Uyumsuz Olarak Çağırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 0face17f-43ca-417b-9b33-737c0fc360df
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 549510d4d2b2ae0ee031b1c5426e7e28ab902bcd
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-call-wcf-service-operations-asynchronously"></a>Nasıl yapılır: WCF Hizmeti İşlemlerini Zaman Uyumsuz Olarak Çağırma
Bu konu, nasıl bir istemci bir hizmet işlemi zaman uyumsuz olarak erişebilir kapsar. Bu konuda hizmeti uygulayan `ICalculator` arabirimi. İstemci bu arabirimde işlemleri olay tabanlı zaman uyumsuz çağırma modelini kullanarak zaman uyumsuz olarak çağırabilirsiniz. (Olay tabanlı zaman uyumsuz çağırma modeli hakkında daha fazla bilgi için bkz: [birden çok iş parçacıklı programlama olay tabanlı zaman uyumsuz desen ile](http://go.microsoft.com/fwlink/?LinkId=248184)). Bir işlem zaman uyumsuz olarak bir hizmet olarak uygulamak gösteren örnek için bkz: [nasıl yapılır: zaman uyumsuz bir hizmet işlemi uygulama](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md). Zaman uyumlu ve zaman uyumsuz işlemler hakkında daha fazla bilgi için bkz: [zaman uyumlu ve zaman uyumsuz işlemleri](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).  
  
> [!NOTE]
>  Olay tabanlı zaman uyumsuz çağırma modeli kullanılırken desteklenmeyen bir <xref:System.ServiceModel.ChannelFactory%601>. Kullanarak zaman uyumsuz çağrıları yapma hakkında bilgi için <xref:System.ServiceModel.ChannelFactory%601>, bkz: [nasıl yapılır: çağrı işlemlerini zaman uyumsuz olarak kullanarak bir kanal fabrikası](../../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).  
  
## <a name="procedure"></a>Yordam  
  
#### <a name="to-call-wcf-service-operations-asynchronously"></a>WCF Hizmeti işlemlerini zaman uyumsuz olarak çağırmak için  
  
1.  Çalıştırma [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) her ikisi de aracıyla `/async` ve `/tcv:Version35` komutu seçenekleri birlikte aşağıdaki komutta gösterildiği gibi.  
  
    ```  
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a /tcv:Version35  
    ```  
  
     Bu, zaman uyumlu ve standart temsilci tabanlı zaman uyumsuz işlemlerin yanı sıra, oluşturur bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] içeren istemci sınıfı:  
  
    -   İki <`operationName` > `Async` işlemleri için olay tabanlı zaman uyumsuz çağırma yaklaşımı kullanın. Örneğin:  
  
         [!code-csharp[EventAsync#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#1)]
         [!code-vb[EventAsync#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#1)]  
  
    -   İşlem tamamlandı olayları formun <`operationName` > `Completed` olay tabanlı zaman uyumsuz çağırma yaklaşımı ile kullanım için. Örneğin:  
  
         [!code-csharp[EventAsync#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#2)]
         [!code-vb[EventAsync#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#2)]  
  
    -   <xref:System.EventArgs?displayProperty=nameWithType>Her bir işlemin türleri (form <`operationName`>`CompletedEventArgs`) olay tabanlı zaman uyumsuz çağırma yaklaşımı ile kullanım için. Örneğin:  
  
         [!code-csharp[EventAsync#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#3)]
         [!code-vb[EventAsync#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#3)]  
  
2.  Arama uygulamasında zaman uyumsuz işlemi aşağıdaki örnek kodda gösterildiği gibi tamamlandığında çağrılacak bir geri çağırma yöntemi oluşturun.  
  
     [!code-csharp[EventAsync#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#4)]
     [!code-vb[EventAsync#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#4)]  
  
3.  Yeni genel kullanma işlemi çağırmadan önce <xref:System.EventHandler%601?displayProperty=nameWithType> türü <`operationName` > `EventArgs` (önceki adımda oluşturulan) işleyici yöntemi eklemek için <`operationName` > `Completed` olay. ' I çağırın <`operationName` > `Async` yöntemi. Örneğin:  
  
     [!code-csharp[EventAsync#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#5)]
     [!code-vb[EventAsync#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#5)]  
  
## <a name="example"></a>Örnek  
  
> [!NOTE]
>  Olay tabanlı zaman uyumsuz modeli için tasarım yönergeleri birden fazla değer döndürülürse, tek bir değer olarak döndürülen durum `Result` özelliği ve diğerleri döndürülür özellikleri olarak üzerinde <xref:System.EventArgs> nesnesi. Bunun bir sonucu olduğundan, bu, istemci olay tabanlı zaman uyumsuz komut seçeneklerini kullanarak meta verilerini alır ve birden fazla değer, varsayılan işlemi döndürürse <xref:System.EventArgs> nesnesi döndüren bir değer olarak `Result` özelliği ve geri kalan özelliklerini <xref:System.EventArgs> nesnesi. İleti nesnesi olarak almak istiyorsanız `Result` özelliği ve bu nesne üzerinde özellikleri kullanma gibi döndürülen değerlere sahip `/messageContract` komut seçeneği. Bu olarak yanıt iletisi döndüren bir imza oluşturur `Result` özellikte <xref:System.EventArgs> nesnesi. Tüm iç dönüş değerleri yanıt iletisi nesnesi sonra özellikleridir.  
  
 [!code-csharp[EventAsync#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#6)]
 [!code-vb[EventAsync#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#6)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: bir zaman uyumsuz hizmet işlemi uygulama](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md)
