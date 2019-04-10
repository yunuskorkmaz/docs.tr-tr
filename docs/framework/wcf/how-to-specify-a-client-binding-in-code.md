---
title: 'Nasıl yapılır: Kodda İstemci Bağlama Belirtme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6bee5da4-adf7-42e6-8f78-63a9e5c6dbad
ms.openlocfilehash: 6d8683108ebe87b8533551d212296b13630b4e19
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59218608"
---
# <a name="how-to-specify-a-client-binding-in-code"></a>Nasıl yapılır: Kodda İstemci Bağlama Belirtme
Bu örnekte, bir hesap makinesi hizmetini kullanması için bir istemci oluşturulur ve o istemci için bağlama kesin kodda belirtilen. İstemcisinin eriştiği `CalculatorService`, uygulayan `ICalculator` arabirimi ve hizmet ve Kullan istemci <xref:System.ServiceModel.BasicHttpBinding> sınıfı.  
  
 Bu yordam, hesap makinesi hizmetinin çalıştığını varsayar. Hizmet oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: Yapılandırmada hizmet bağlaması belirtme](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md). Ayrıca kullanan [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)istemci bileşenlerini otomatik olarak oluşturmak için Windows Communication Foundation (WCF) sağlar. Araç, hizmete erişmek için istemci kodu oluşturur.  
  
 İstemci, iki parça halinde oluşturulmuştur. Svcutil.exe oluşturur `ClientCalculator` uygulayan `ICalculator` arabirimi. Bu istemci uygulaması, ardından bir örneğini oluşturarak oluşturulur `ClientCalculator` ve kod içinde bağlama ve hizmet adresini belirterek.  
  
 Bu örnekte kaynak kopyası için bkz: [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md) örnek.  
  
### <a name="to-specify-a-custom-binding-in-code"></a>Kodda özel bir bağlama belirtmek için  
  
1.  Komut satırından hizmet meta verilerinden kod üretmek için Svcutil.exe kullanımı.  
  
    ```  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2.  Oluşturulan istemci içeren `ICalculator` istemci uygulaması karşılaması gereken hizmet sözleşmesini tanımlayan arabirimi.  
  
     [!code-csharp[C_HowTo_CodeClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#1)]
     [!code-vb[C_HowTo_CodeClientBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#1)]  
  
3.  Oluşturulan istemci uygulamasını da içeren `ClientCalculator`.  
  
     [!code-csharp[C_HowTo_CodeClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#2)]
     [!code-vb[C_HowTo_CodeClientBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#2)]  
  
4.  Bir örneğini oluşturmak `ClientCalculator` kullanan <xref:System.ServiceModel.BasicHttpBinding> sınıfı bir istemci uygulamasına ve belirtilen adresteki hizmet işlemleri çağırma.  
  
     [!code-csharp[C_HowTo_CodeClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#3)]
     [!code-vb[C_HowTo_CodeClientBinding#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#3)]  
  
5.  Derleyin ve istemci çalıştırın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
