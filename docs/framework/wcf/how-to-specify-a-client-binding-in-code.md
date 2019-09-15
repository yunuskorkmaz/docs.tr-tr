---
title: 'Nasıl yapılır: Kodda İstemci Bağlama Belirtme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6bee5da4-adf7-42e6-8f78-63a9e5c6dbad
ms.openlocfilehash: 37769a84ca623e2f7f246d36180aa17537e90bfa
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70990230"
---
# <a name="how-to-specify-a-client-binding-in-code"></a>Nasıl yapılır: Kodda İstemci Bağlama Belirtme
Bu örnekte, bir Hesaplayıcı hizmeti kullanmak için bir istemci oluşturulur ve bu istemci için bağlama kodda imperatively belirtilir. İstemci, `ICalculator` arabirimini uygulayan `CalculatorService`öğesine erişir ve hem hizmet <xref:System.ServiceModel.BasicHttpBinding> hem de istemci sınıfını kullanır.  
  
 Bu yordam, hesap makinesi hizmetinin çalıştığını varsayar. Hizmeti oluşturma hakkında bilgi için bkz [. nasıl yapılır: Yapılandırmada](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)bir hizmet bağlaması belirtin. Ayrıca, istemci bileşenlerini otomatik olarak oluşturmak için [ServiceModel meta veri yardımcı programı aracı 'nı (Svcutil. exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)WINDOWS COMMUNICATION FOUNDATION (WCF) kullanır. Araç, hizmete erişmek için istemci kodunu üretir.  
  
 İstemci iki bölümde oluşturulmuştur. Svcutil. exe, `ClientCalculator` `ICalculator` arabirimini uygulayan öğesini oluşturur. Bu istemci uygulaması daha sonra bir örneği `ClientCalculator` oluşturup ardından kodda hizmet için bağlama ve adres belirtilerek oluşturulur.  
  
 Bu örneğin kaynak kopyası için bkz. [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md) örneği.  
  
### <a name="to-specify-a-custom-binding-in-code"></a>Kodda özel bir bağlama belirtmek için  
  
1. Hizmet meta verilerinden kod oluşturmak için komut satırından Svcutil. exe ' yi kullanın.  
  
    ```console  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2. Oluşturulan istemci, istemci uygulamasının karşılaması gereken `ICalculator` hizmet sözleşmesini tanımlayan arabirimi içerir.  
  
     [!code-csharp[C_HowTo_CodeClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#1)]
     [!code-vb[C_HowTo_CodeClientBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#1)]  
  
3. Oluşturulan istemci, `ClientCalculator`uygulamasını da içerir.  
  
     [!code-csharp[C_HowTo_CodeClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#2)]
     [!code-vb[C_HowTo_CodeClientBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#2)]  
  
4. Bir istemci uygulamasında <xref:System.ServiceModel.BasicHttpBinding> sınıfını kullanan `ClientCalculator` öğesinin bir örneğini oluşturun ve ardından belirtilen adresteki hizmet işlemlerini çağırın.  
  
     [!code-csharp[C_HowTo_CodeClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#3)]
     [!code-vb[C_HowTo_CodeClientBinding#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#3)]  
  
5. İstemcisini derleyin ve çalıştırın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
