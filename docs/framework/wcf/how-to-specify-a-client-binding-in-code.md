---
title: 'Nasıl yapılır: Kodda İstemci Bağlama Belirtme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6bee5da4-adf7-42e6-8f78-63a9e5c6dbad
ms.openlocfilehash: 9be571d7be020aef546fdd7ec7cb7519a48ea350
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184051"
---
# <a name="how-to-specify-a-client-binding-in-code"></a>Nasıl yapılır: Kodda İstemci Bağlama Belirtme
Bu örnekte, bir hesap makinesi hizmeti kullanmak için bir istemci oluşturulur ve bu istemci için bağlama zorunlu olarak kod olarak belirtilir. `CalculatorService`İstemci, `ICalculator` arabirimi uygulayan , hizmete ve istemciye erişir <xref:System.ServiceModel.BasicHttpBinding> ve sınıfı kullanır.  
  
 Bu yordam, hesap makinesi hizmetinin çalıştığını varsayar. Hizmet oluşturma hakkında daha fazla bilgi için [bkz: Yapılandırmada Bir Hizmet Bağlama belirtin.](how-to-specify-a-service-binding-in-configuration.md) Ayrıca [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)Windows Communication Foundation (WCF) istemci bileşenlerini otomatik olarak oluşturmak için sağlar kullanır. Araç, hizmete erişmek için istemci kodunu oluşturur.  
  
 İstemci iki bölümden oluşur. Svcutil.exe `ICalculator` arayüzü `ClientCalculator` uygular oluşturur. Bu istemci uygulaması daha sonra bir `ClientCalculator` örnek oluşturarak ve daha sonra kod içinde hizmet için bağlama ve adres belirterek oluşturulur.  
  
 Bu örneğin kaynak kopyası için [Temel Bağlama](./samples/basicbinding.md) örneğine bakın.  
  
### <a name="to-specify-a-custom-binding-in-code"></a>Kodda özel bir bağlama belirtmek için  
  
1. Hizmet meta verilerinden kod oluşturmak için komut satırından Svcutil.exe'yi kullanın.  
  
    ```console  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
    ```  
  
2. Oluşturulan istemci, istemci `ICalculator` uygulamasının karşılaması gereken hizmet sözleşmesini tanımlayan arabirimi içerir.  
  
     [!code-csharp[C_HowTo_CodeClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#1)]
     [!code-vb[C_HowTo_CodeClientBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#1)]  
  
3. Oluşturulan istemci de uygulanmasını `ClientCalculator`içerir.  
  
     [!code-csharp[C_HowTo_CodeClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#2)]
     [!code-vb[C_HowTo_CodeClientBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#2)]  
  
4. İstemci uygulamasında `ClientCalculator` <xref:System.ServiceModel.BasicHttpBinding> sınıfı kullananların bir örneğini oluşturun ve ardından belirtilen adresteki servis işlemlerini çağırın.  
  
     [!code-csharp[C_HowTo_CodeClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#3)]
     [!code-vb[C_HowTo_CodeClientBinding#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#3)]  
  
5. İstemciyi derle ve çalıştır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](using-bindings-to-configure-services-and-clients.md)
