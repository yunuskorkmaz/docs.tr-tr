---
title: "Nasıl yapılır: Kanal Fabrikası Kullanarak İşlemlere Zaman Uyumsuz Olarak Çağrı Yapma"
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
ms.assetid: cc17dd47-b9ad-451c-a362-e36e0aac7ba0
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 216c0d529a15004ea9f7d6f087aeee4bf4f10e56
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-call-operations-asynchronously-using-a-channel-factory"></a>Nasıl yapılır: Kanal Fabrikası Kullanarak İşlemlere Zaman Uyumsuz Olarak Çağrı Yapma
Bu konu, nasıl bir istemci bir hizmet işlemi zaman uyumsuz olarak kullanırken erişebilir kapsar bir <xref:System.ServiceModel.ChannelFactory%601>-tabanlı istemci. (Kullanırken bir <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> olay tabanlı zaman uyumsuz çağırma model kullanabileceğiniz hizmetini çağırmak için nesne. Daha fazla bilgi için bkz: [nasıl yapılır: hizmet işlemlerini zaman uyumsuz çağrı](../../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md). Olay tabanlı zaman uyumsuz çağırma modeli hakkında daha fazla bilgi için bkz: [birden çok iş parçacıklı programlama olay tabanlı zaman uyumsuz desen ile](../../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md).)  
  
 Bu konuda hizmeti uygulayan `ICalculator` arabirimi. İstemci bu arabirimde işlemlerini zaman uyumsuz olarak işlemlerini ister anlamına gelir çağırabilirsiniz `Add` iki yöntem bölme `BeginAdd` ve `EndAdd`, eski biri çağrı başlatır ve ikincisi biri alır sonucu İşlem tamamlandığında. Bir işlem zaman uyumsuz olarak bir hizmet olarak uygulamak nasıl gösteren bir örnek için bkz: [nasıl yapılır: zaman uyumsuz bir hizmet işlemi uygulama](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md). Zaman uyumlu ve zaman uyumsuz işlemler hakkında daha fazla ayrıntı için bkz: [zaman uyumlu ve zaman uyumsuz işlemleri](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).  
  
## <a name="procedure"></a>Yordam  
  
#### <a name="to-call-wcf-service-operations-asynchronously"></a>WCF Hizmeti işlemlerini zaman uyumsuz olarak çağırmak için  
  
1.  Çalıştırma [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ile aracı `/async` seçenek aşağıdaki komutta gösterildiği gibi.  
  
    ```  
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a  
    ```  
  
     Bu işlem için hizmet sözleşmesini zaman uyumsuz istemci sürümünü oluşturur.  
  
2.  Zaman uyumsuz işlemi aşağıdaki örnek kodda gösterildiği gibi tamamlandığında çağrılacak bir geri çağırma işlevini oluşturun.  
  
     [!code-csharp[C_How_To_CF_Async#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/client.cs#2)]
     [!code-vb[C_How_To_CF_Async#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/client.vb#2)]  
  
3.  Bir hizmet işlemi zaman uyumsuz olarak erişmek için istemci ve çağrı oluşturma `Begin[Operation]` (örneğin, `BeginAdd`) ve aşağıdaki örnek kodda gösterildiği gibi bir geri çağırma işlevi belirtin.  
  
     [!code-csharp[C_How_To_CF_Async#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/client.cs#3)]
     [!code-vb[C_How_To_CF_Async#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/client.vb#3)]  
  
     Geri çağırma işlevi yürütüldüğünde, istemcinin çağıran `End<operation>` (örneğin, `EndAdd`) sonucu alınamadı.  
  
## <a name="example"></a>Örnek  
 Önceki yordamda kullanılan istemci kodu ile birlikte kullanılan hizmeti uygulayan `ICalculator` arabirimi aşağıdaki kodda gösterildiği gibi. Hizmet tarafında `Add` ve `Subtract` sözleşmenin işlemleri zaman uyumlu olarak göre çağrılır [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] önceki istemci adımları istemcide zaman uyumsuz olarak çağrılır olsa da, çalıştırma. `Multiply` Ve `Divide` işlemleri kullanılan zaman uyumsuz olarak hizmet tarafında hizmetini çağırmak için bile istemci bunları zaman uyumlu olarak çağırır. Bu örnek ayarlar <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> özelliğine `true`. Uygulaması ile birlikte bu özellik ayarı [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zaman uyumsuz desen işlemi zaman uyumsuz olarak çağırmak için çalışma süresi söyler.  
  
 [!code-csharp[C_How_To_CF_Async#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/service.cs#4)]
 [!code-vb[C_How_To_CF_Async#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/service.vb#4)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hizmet sözleşmesi: Zaman uyumsuz örnek](http://msdn.microsoft.com/library/833db946-f511-4f64-a26f-2759a11217c7)
