---
title: 'Nasıl yapılır: Kanal Fabrikası Kullanarak İşlemlere Zaman Uyumsuz Olarak Çağrı Yapma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cc17dd47-b9ad-451c-a362-e36e0aac7ba0
ms.openlocfilehash: 3080514d06119a2f1b621cff16056ac7577c30b3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966811"
---
# <a name="how-to-call-operations-asynchronously-using-a-channel-factory"></a>Nasıl yapılır: Kanal Fabrikası Kullanarak İşlemlere Zaman Uyumsuz Olarak Çağrı Yapma
Bu konu, bir istemcinin bir hizmet işlemine tabanlı bir <xref:System.ServiceModel.ChannelFactory%601>istemci uygulaması kullanılırken zaman uyumsuz olarak nasıl erişebileceğini ele almaktadır. (Bir hizmeti çağırmak <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> için bir nesnesi kullanırken, olay odaklı zaman uyumsuz çağırma modelini kullanabilirsiniz. Daha fazla bilgi için [nasıl yapılır: Hizmet Işlemlerini zaman uyumsuz](../../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md)olarak çağırın. Olay tabanlı zaman uyumsuz çağrı modeli hakkında daha fazla bilgi için bkz. [olay tabanlı zaman uyumsuz model (EAP)](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).)  
  
 Bu konudaki hizmet, `ICalculator` arabirimini uygular. İstemci bu arabirimdeki işlemleri zaman uyumsuz olarak çağırabilir; bu da, gibi `Add` işlemler iki `BeginAdd` yönteme ayrılır ve `EndAdd`ilki çağrıyı başlatan ve ikincisi sonucu alan işlem tamamlandığında. Bir hizmetin bir hizmette zaman uyumsuz olarak nasıl uygulanacağını gösteren bir örnek için bkz [. nasıl yapılır: Zaman uyumsuz bir hizmet Işlemi](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md)uygulayın. Zaman uyumlu ve zaman uyumsuz işlemler hakkında ayrıntılar için bkz. [zaman uyumlu ve zaman uyumsuz işlemler](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).  
  
## <a name="procedure"></a>Yordam  
  
#### <a name="to-call-wcf-service-operations-asynchronously"></a>WCF hizmeti işlemlerini zaman uyumsuz olarak çağırma  
  
1. Aşağıdaki komutta gösterildiği gibi, [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) aracını `/async` seçeneğiyle çalıştırın.  
  
    ```  
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a  
    ```  
  
     Bu işlem için hizmet sözleşmesinin zaman uyumsuz bir istemci sürümünü oluşturur.  
  
2. Aşağıdaki örnek kodda gösterildiği gibi zaman uyumsuz işlem tamamlandığında çağrılacak bir geri arama işlevi oluşturun.  
  
     [!code-csharp[C_How_To_CF_Async#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/client.cs#2)]
     [!code-vb[C_How_To_CF_Async#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/client.vb#2)]  
  
3. Bir hizmet işlemine zaman uyumsuz olarak erişmek için istemcisini oluşturun ve `Begin[Operation]` (örneğin, `BeginAdd`) öğesini çağırın ve aşağıdaki örnek kodda gösterildiği gibi bir geri çağırma işlevi belirtin.  
  
     [!code-csharp[C_How_To_CF_Async#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/client.cs#3)]
     [!code-vb[C_How_To_CF_Async#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/client.vb#3)]  
  
     Geri çağırma işlevi yürütüldüğünde, istemci, sonucu almak `End<operation>` için (örneğin, `EndAdd`) çağırır.  
  
## <a name="example"></a>Örnek  
 Önceki yordamda kullanılan istemci koduyla kullanılan hizmet, aşağıdaki kodda gösterildiği gibi `ICalculator` arabirimini uygular. Hizmet tarafında, `Add` bir önceki istemci adımları `Subtract` istemcide zaman uyumsuz olarak çağrılsa bile, sözleşmenin ve işlemleri Windows Communication Foundation (WCF) çalışma zamanına göre zaman uyumlu olarak çağrılır. `Multiply` Ve`Divide` işlemleri, istemci, zaman uyumlu olarak çağırsa bile hizmet tarafında zaman uyumsuz olarak hizmeti çağırmak için kullanılır. Bu örnek, <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> özelliğini olarak `true`ayarlar. Bu özellik ayarı, .NET Framework zaman uyumsuz deseninin uygulanmasıyla birlikte, işlemi zaman uyumsuz olarak çağırmak için çalışma zamanına bildirir.  
  
 [!code-csharp[C_How_To_CF_Async#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/service.cs#4)]
 [!code-vb[C_How_To_CF_Async#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/service.vb#4)]  
