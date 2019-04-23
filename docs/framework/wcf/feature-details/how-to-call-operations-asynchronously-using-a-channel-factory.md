---
title: 'Nasıl yapılır: Kanal Fabrikası Kullanarak İşlemlere Zaman Uyumsuz Olarak Çağrı Yapma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cc17dd47-b9ad-451c-a362-e36e0aac7ba0
ms.openlocfilehash: 17b6dd979f7554cd433cc1abcf2a4da8dd9b83cb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59772689"
---
# <a name="how-to-call-operations-asynchronously-using-a-channel-factory"></a>Nasıl yapılır: Kanal Fabrikası Kullanarak İşlemlere Zaman Uyumsuz Olarak Çağrı Yapma
Bu konu nasıl bir istemci bir hizmet işlemi zaman uyumsuz olarak kullanılırken erişebilir kapsayan bir <xref:System.ServiceModel.ChannelFactory%601>-tabanlı istemci uygulaması. (Kullanırken bir <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> olay tabanlı zaman uyumsuz çağırma modeli kullandığınız bir hizmeti çağırmak için nesne. Daha fazla bilgi için [nasıl yapılır: Hizmet işlemlerini zaman uyumsuz çağırma](../../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md). Olay tabanlı zaman uyumsuz çağırma modeli hakkında daha fazla bilgi için bkz. [olay tabanlı zaman uyumsuz desen (EAP)](../../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).)  
  
 Bu konuda hizmeti uygulayan `ICalculator` arabirimi. İstemci bu arabirimdeki işlemlerini zaman uyumsuz olarak işlemleri gibi sağladığı anlamına gelir çağırabilirsiniz `Add` iki yöntem bölme `BeginAdd` ve `EndAdd`, biri önceki çağrı başlatır ve ikincisi biri sonucunu alır İşlem tamamlandığında. Bir işlemi zaman uyumsuz olarak bir hizmet olarak uygulama gösteren bir örnek için bkz [nasıl yapılır: Zaman uyumsuz bir hizmet işlemi uygulama](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md). Zaman uyumlu ve zaman uyumsuz işlemler hakkında daha fazla ayrıntı için bkz: [zaman uyumlu ve zaman uyumsuz işlemler](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).  
  
## <a name="procedure"></a>Yordam  
  
#### <a name="to-call-wcf-service-operations-asynchronously"></a>WCF Hizmeti işlemlerini zaman uyumsuz olarak çağırmak için  
  
1. Çalıştırma [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ile aracı `/async` seçenek aşağıdaki komutta gösterildiği gibi.  
  
    ```  
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a  
    ```  
  
     Bu işlem için hizmet sözleşmesi bir zaman uyumsuz istemci sürümünü oluşturur.  
  
2. Zaman uyumsuz işlemi aşağıdaki örnek kodda gösterildiği gibi tamamlandığında çağrılacak bir geri çağırma işlevi oluşturun.  
  
     [!code-csharp[C_How_To_CF_Async#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/client.cs#2)]
     [!code-vb[C_How_To_CF_Async#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/client.vb#2)]  
  
3. Bir hizmet işlemi zaman uyumsuz olarak erişmek için istemci ve çağrı oluşturma `Begin[Operation]` (örneğin, `BeginAdd`) ve aşağıdaki örnek kodda gösterildiği gibi bir geri çağırma işlevini belirtin.  
  
     [!code-csharp[C_How_To_CF_Async#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/client.cs#3)]
     [!code-vb[C_How_To_CF_Async#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/client.vb#3)]  
  
     İstemci geri çağırma işlevi yürütüldüğünde, çağıran `End<operation>` (örneğin, `EndAdd`) sonuç almak için.  
  
## <a name="example"></a>Örnek  
 Önceki yordamda kullanılan istemci kodu ile kullanılan hizmeti uygulayan `ICalculator` arabirimi aşağıdaki kodda gösterildiği gibi. Hizmet tarafında, `Add` ve `Subtract` sözleşmenin operations çağrılır zaman uyumlu olarak Windows Communication Foundation (çalışma zamanı, WCF) tarafından rağmen önceki istemci adımları zaman uyumsuz olarak istemcide çağrılır. `Multiply` Ve `Divide` operations zaman uyumsuz olarak hizmet tarafında hizmetini çağırmak için kullanılan bile istemcisi eşzamanlı olarak onları çağırır. Bu örnekte ayarlar <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> özelliğini `true`. Uygulaması ile birlikte bu özellik ayarı [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] işlemini zaman uyumsuz olarak çağırmak için çalışma zamanı zaman uyumsuz desen söyler.  
  
 [!code-csharp[C_How_To_CF_Async#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/service.cs#4)]
 [!code-vb[C_How_To_CF_Async#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/service.vb#4)]  
