---
title: 'Nasıl yapılır: Kanal Fabrikası Kullanarak İşlemlere Zaman Uyumsuz Olarak Çağrı Yapma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cc17dd47-b9ad-451c-a362-e36e0aac7ba0
ms.openlocfilehash: 25d88b00e0bb1105be57989ff5d090a308177329
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601276"
---
# <a name="how-to-call-operations-asynchronously-using-a-channel-factory"></a>Nasıl yapılır: Kanal Fabrikası Kullanarak İşlemlere Zaman Uyumsuz Olarak Çağrı Yapma
Bu konu, bir istemcinin bir hizmet işlemine tabanlı bir istemci uygulaması kullanılırken zaman uyumsuz olarak nasıl erişebileceğini ele almaktadır <xref:System.ServiceModel.ChannelFactory%601> . (Bir <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> hizmeti çağırmak için bir nesnesi kullanırken, olay odaklı zaman uyumsuz çağırma modelini kullanabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: hizmet Işlemlerini zaman uyumsuz olarak çağırma](how-to-call-wcf-service-operations-asynchronously.md). Olay tabanlı zaman uyumsuz çağrı modeli hakkında daha fazla bilgi için bkz. [olay tabanlı zaman uyumsuz model (EAP)](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).)  
  
 Bu konudaki hizmet, `ICalculator` arabirimini uygular. İstemci bu arabirimdeki işlemleri zaman uyumsuz olarak çağırabilir. Bu, gibi işlemlerin `Add` iki yönteme bölündüğü `BeginAdd` ve `EndAdd` daha önce çağrıyı başlatan ve bu işlem tamamlandığında sonucu alan, ikincinin oluşturulduğu anlamına gelir. Bir hizmetin bir hizmette zaman uyumsuz olarak nasıl uygulanacağını gösteren bir örnek için bkz. [nasıl yapılır: Işlem zaman uyumsuz hizmet Işlemi uygulama](../how-to-implement-an-asynchronous-service-operation.md). Zaman uyumlu ve zaman uyumsuz işlemler hakkında ayrıntılar için bkz. [zaman uyumlu ve zaman uyumsuz işlemler](../synchronous-and-asynchronous-operations.md).  
  
## <a name="procedure"></a>Yordam  
  
#### <a name="to-call-wcf-service-operations-asynchronously"></a>WCF hizmeti işlemlerini zaman uyumsuz olarak çağırma  
  
1. Aşağıdaki komutta gösterildiği gibi, [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) aracını `/async` seçeneğiyle çalıştırın.  
  
    ```console
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a  
    ```  
  
     Bu işlem için hizmet sözleşmesinin zaman uyumsuz bir istemci sürümünü oluşturur.  
  
2. Aşağıdaki örnek kodda gösterildiği gibi zaman uyumsuz işlem tamamlandığında çağrılacak bir geri arama işlevi oluşturun.  
  
     [!code-csharp[C_How_To_CF_Async#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/client.cs#2)]
     [!code-vb[C_How_To_CF_Async#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/client.vb#2)]  
  
3. Bir hizmet işlemine zaman uyumsuz olarak erişmek için istemcisini oluşturun ve `Begin[Operation]` (örneğin,) öğesini çağırın `BeginAdd` ve aşağıdaki örnek kodda gösterildiği gibi bir geri çağırma işlevi belirtin.  
  
     [!code-csharp[C_How_To_CF_Async#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/client.cs#3)]
     [!code-vb[C_How_To_CF_Async#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/client.vb#3)]  
  
     Geri çağırma işlevi yürütüldüğünde, istemci, `End<operation>` sonucu almak için (örneğin, `EndAdd` ) çağırır.  
  
## <a name="example"></a>Örnek  
 Önceki yordamda kullanılan istemci koduyla kullanılan hizmet, `ICalculator` aşağıdaki kodda gösterildiği gibi arabirimini uygular. Hizmet tarafında, `Add` `Subtract` bir önceki istemci adımları istemcide zaman uyumsuz olarak çağrılsa bile, sözleşmenin ve işlemleri WINDOWS COMMUNICATION FOUNDATION (WCF) çalışma zamanına göre zaman uyumlu olarak çağrılır. `Multiply`Ve `Divide` işlemleri, istemci, zaman uyumlu olarak çağırsa bile hizmet tarafında zaman uyumsuz olarak hizmeti çağırmak için kullanılır. Bu örnek, <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> özelliğini olarak ayarlar `true` . Bu özellik ayarı, .NET Framework zaman uyumsuz deseninin uygulanmasıyla birlikte, işlemi zaman uyumsuz olarak çağırmak için çalışma zamanına bildirir.  
  
 [!code-csharp[C_How_To_CF_Async#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/service.cs#4)]
 [!code-vb[C_How_To_CF_Async#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/service.vb#4)]  
