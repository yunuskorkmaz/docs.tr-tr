---
title: 'Nasıl yapılır: Yapılandırmada İstemci Bağlama Belirtme'
ms.date: 03/30/2017
ms.assetid: 4a7c79aa-50ee-4991-891e-adc0599323a7
ms.openlocfilehash: e2ea5a4b1c2ca9b661be5d4c653a3b5668bd26f5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33499066"
---
# <a name="how-to-specify-a-client-binding-in-configuration"></a>Nasıl yapılır: Yapılandırmada İstemci Bağlama Belirtme
Bu örnekte, bir istemci konsol uygulaması hesaplayıcı hizmetini kullanmak için oluşturulur ve bu istemci için bağlama bildirimli olarak yapılandırma dosyasında belirtilen. İstemcisinin eriştiği `CalculatorService`, hangi uygulayan `ICalculator` arabirimi ve hizmet ve Kullan istemci <xref:System.ServiceModel.BasicHttpBinding> sınıfı.  
  
 Özetlenen yordamı hesap makinesi hizmetinin çalıştığını varsayar. Hizmet oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: yapılandırmada hizmet bağlama belirtme](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md). Ayrıca kullanır [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) Windows Communication Foundation (WCF) istemci bileşenlerini otomatik olarak oluşturmak için sağlar. Aracı istemci kodu ve hizmete erişim için yapılandırma oluşturur.  
  
 İstemci iki parça halinde yerleşik olarak bulunur. Svcutil.exe oluşturur `ClientCalculator` uygulayan `ICalculator` arabirimi. Bu istemci uygulaması örneğini oluşturarak sonra oluşturulan `ClientCalculator`.  
  
 Bağlama ve adres bilgilerini yapılandırma yerine imperatively kod bildirimli olarak belirtmek için genellikle en iyi uygulamadır. Bağlamalar ve dağıtılmış bir hizmet için adresleri hizmet geliştirildiği sırada kullanılan olanlardan genellikle farklı olduğu için uç noktalar kodda tanımlama genellikle pratik değildir. Daha genel olarak, bağlama tutulması ve adresleme bilgilerini kodu dışında yeniden derleyin veya uygulamayı yeniden dağıtmak zorunda kalmadan değiştirmek için bunları sağlar.  
  
 Tüm aşağıdaki yapılandırma adımlarını kullanarak yerine [Yapılandırma Aracı (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).  
  
 Bu örnekte kaynak kopyası için bkz: [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md) örnek.  
  
### <a name="specifying-a-client-binding-in-configuration"></a>Bir istemci yapılandırmasında bağlama belirtme  
  
1.  Hizmet meta verilerinden kodu oluşturmak için komut satırından svcutil.exe kullanma.  
  
    ```  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2.  Oluşturulan istemci içeren `ICalculator` istemci uygulaması getirmelidir hizmet sözleşmesini tanımlayan arabirimi.  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#1)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#1)]  
  
3.  Oluşturulan istemci uygulamasını da içerir `ClientCalculator`.  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#2)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#2)]  
  
4.  Svcutil.exe ayrıca kullanan istemci yapılandırması oluşturur <xref:System.ServiceModel.BasicHttpBinding> sınıfı. Visual Studio kullanırken, bu App.config dosyasının adı. Adres ve bağlama bilgileri herhangi bir yere hizmet uygulaması içinde belirtilmedi olduğunu unutmayın. Ayrıca, bu bilgileri yapılandırma dosyasından almak için yazılacak kodu yok.  
  
     [!code-xml[C_HowTo_ConfigureClientBinding#100](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/common/client.exe.config#100)]   
            
5.  Bir örneğini oluşturmak `ClientCalculator` bir uygulamada ve hizmet işlemleri çağırın.  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/client.cs#3)]  
  
6.  Derleme ve istemci çalıştırın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
