---
title: 'Nasıl yapılır: Yapılandırmada İstemci Bağlama Belirtme'
ms.date: 03/30/2017
ms.assetid: 4a7c79aa-50ee-4991-891e-adc0599323a7
ms.openlocfilehash: 0757dac4cdcffc7c3550432a71fe45b587327660
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70990224"
---
# <a name="how-to-specify-a-client-binding-in-configuration"></a>Nasıl yapılır: Yapılandırmada İstemci Bağlama Belirtme
Bu örnekte, bir hesap makinesi hizmeti kullanmak için bir istemci konsol uygulaması oluşturulur ve bu istemcinin bağlaması yapılandırmada bildirimli olarak belirtilir. İstemci, `ICalculator` arabirimini uygulayan `CalculatorService`öğesine erişir ve hem hizmet <xref:System.ServiceModel.BasicHttpBinding> hem de istemci sınıfını kullanır.  
  
 Özetlenen yordamda, hesap makinesi hizmetinin çalıştığı varsayılmaktadır. Hizmeti oluşturma hakkında daha fazla bilgi için bkz [. nasıl yapılır: Yapılandırmada](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)bir hizmet bağlaması belirtin. Ayrıca, istemci bileşenlerini otomatik olarak oluşturmak için Windows Communication Foundation (WCF) tarafından sağlanan [ServiceModel meta veri yardımcı programı aracını (Svcutil. exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) kullanır. Araç, hizmete erişmek için istemci kodunu ve yapılandırmasını üretir.  
  
 İstemci iki bölümde oluşturulmuştur. Svcutil. exe, `ClientCalculator` `ICalculator` arabirimini uygulayan öğesini oluşturur. Bu istemci uygulaması daha sonra bir örneği `ClientCalculator`oluşturarak oluşturulur.  
  
 Genellikle, bağlama ve adres bilgilerini, kod içinde imperatively yerine bildirimli olarak yapılandırmaya göre belirlemek en iyi uygulamadır. Dağıtılmış bir hizmetin bağlamaları ve adresleri genellikle hizmet geliştirildiğinde kullanılanlardan farklı olduğundan, koddaki uç noktaların tanımlanması genellikle pratik değildir. Daha genel olarak, bağlama ve adresleme bilgilerini koddan tutmanın, uygulamayı yeniden derlemek veya yeniden dağıtmak zorunda kalmadan değiştirilmesine izin verir.  
  
 [Yapılandırma Düzenleyicisi aracını (SvcConfigEditor. exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)kullanarak aşağıdaki yapılandırma adımlarının tümünü gerçekleştirebilirsiniz.  
  
 Bu örneğin kaynak kopyası için bkz. [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md) örneği.  
  
### <a name="specifying-a-client-binding-in-configuration"></a>Yapılandırmada İstemci bağlaması belirtme  
  
1. Hizmet meta verilerinden kod oluşturmak için komut satırından Svcutil. exe ' yi kullanın.  
  
    ```console  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2. Oluşturulan istemci, istemci uygulamasının karşılaması gereken `ICalculator` hizmet sözleşmesini tanımlayan arabirimi içerir.  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#1)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#1)]  
  
3. Oluşturulan istemci, `ClientCalculator`uygulamasını da içerir.  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#2)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#2)]  
  
4. Svcutil. exe, <xref:System.ServiceModel.BasicHttpBinding> sınıfını kullanan istemcinin yapılandırmasını da oluşturur. Visual Studio 'Yu kullanırken, bu dosyayı App. config olarak adlandırın. Adres ve bağlama bilgilerinin, hizmet uygulamasının içinde herhangi bir yerde belirtilmediğini unutmayın. Ayrıca, bu bilgileri yapılandırma dosyasından almak için kodun yazılması gerekmez.  
  
     [!code-xml[C_HowTo_ConfigureClientBinding#100](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/common/client.exe.config#100)]   
            
5. Uygulamasının bir örneğini `ClientCalculator` oluşturun ve ardından hizmet işlemlerini çağırın.  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/client.cs#3)]  
  
6. İstemcisini derleyin ve çalıştırın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
