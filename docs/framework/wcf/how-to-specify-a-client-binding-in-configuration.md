---
title: 'Nasıl yapılır: Yapılandırmada İstemci Bağlama Belirtme'
ms.date: 03/30/2017
ms.assetid: 4a7c79aa-50ee-4991-891e-adc0599323a7
ms.openlocfilehash: 633bb0feeb0f9354bd6ff8ee6637f123d3e3cbf4
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59295139"
---
# <a name="how-to-specify-a-client-binding-in-configuration"></a>Nasıl yapılır: Yapılandırmada İstemci Bağlama Belirtme
Bu örnekte, bir hesap makinesi hizmetini kullanması için bir istemci konsol uygulaması oluşturulur ve o istemci için bağlama bildirimli olarak yapılandırmasında belirtilen. İstemcisinin eriştiği `CalculatorService`, uygulayan `ICalculator` arabirimi ve hizmet ve Kullan istemci <xref:System.ServiceModel.BasicHttpBinding> sınıfı.  
  
 Özetlenen yordamı, hesap makinesi hizmetinin çalıştığını varsayar. Derleme hizmeti hakkında daha fazla bilgi için bkz: [nasıl yapılır: Yapılandırmada hizmet bağlaması belirtme](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md). Ayrıca kullanan [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) istemci bileşenlerini otomatik olarak oluşturmak için Windows Communication Foundation (WCF) sağlar. Araç istemci kodu ve hizmete erişim yapılandırması oluşturur.  
  
 İstemci, iki parça halinde oluşturulmuştur. Svcutil.exe oluşturur `ClientCalculator` uygulayan `ICalculator` arabirimi. Bu istemci uygulaması, ardından bir örneğini oluşturarak oluşturulur `ClientCalculator`.  
  
 Yapılandırma yerine kesin kod bağlama ve adres bilgilerini bildirimli olarak belirtmek için genellikle en iyi uygulamadır. Bağlamalarında ve adreslerinde dağıtılan bir hizmette hizmet geliştirilen kullandığı olanlardan genellikle farklı olduğundan uç noktaları kodda tanımlama genellikle pratik değildir. Daha genel olarak, bağlama tutulması ve adresleme bilgilerini kodunun dışında yeniden derleyin veya uygulama yeniden dağıtmaya gerek kalmadan değiştirmek için bunları sağlar.  
  
 Tüm aşağıdaki yapılandırma adımlarını kullanarak gerçekleştirebileceğiniz [Yapılandırma Aracı (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).  
  
 Bu örnekte kaynak kopyası için bkz: [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md) örnek.  
  
### <a name="specifying-a-client-binding-in-configuration"></a>Bir istemci yapılandırmasında bağlama belirtme  
  
1. Komut satırından hizmet meta verilerinden kod üretmek için Svcutil.exe kullanımı.  
  
    ```  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2. Oluşturulan istemci içeren `ICalculator` istemci uygulaması karşılaması gereken hizmet sözleşmesini tanımlayan arabirimi.  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#1)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#1)]  
  
3. Oluşturulan istemci uygulamasını da içeren `ClientCalculator`.  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#2)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#2)]  
  
4. Svcutil.exe ayrıca kullanan istemci yapılandırmasını oluşturur <xref:System.ServiceModel.BasicHttpBinding> sınıfı. Visual Studio kullanarak, bu App.config dosyasının adı. Bağlama bilgileri ve adresi herhangi bir uygulama hizmetinin içinde belirtilmeyen olduğunu unutmayın. Ayrıca, yapılandırma dosyasından bu bilgileri almak için yazılacak kod yok.  
  
     [!code-xml[C_HowTo_ConfigureClientBinding#100](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/common/client.exe.config#100)]   
            
5. Bir örneğini oluşturmak `ClientCalculator` uygulamada ve hizmet işlemleri çağırma.  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/client.cs#3)]  
  
6. Derleyin ve istemci çalıştırın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
