---
title: 'Nasıl yapılır: Yapılandırmada İstemci Bağlama Belirtme'
ms.date: 03/30/2017
ms.assetid: 4a7c79aa-50ee-4991-891e-adc0599323a7
ms.openlocfilehash: 574f56173c2acfcf41a5e9a9e99abe45281e3636
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184044"
---
# <a name="how-to-specify-a-client-binding-in-configuration"></a>Nasıl yapılır: Yapılandırmada İstemci Bağlama Belirtme
Bu örnekte, bir hesap makinesi hizmeti kullanmak için bir istemci konsoluygulaması oluşturulur ve bu istemci için bağlama yapılandırmada bildirimsel olarak belirtilir. `CalculatorService`İstemci, `ICalculator` arabirimi uygulayan , hizmete ve istemciye erişir <xref:System.ServiceModel.BasicHttpBinding> ve sınıfı kullanır.  
  
 Özetlenen yordam, hesap makinesi hizmetinin çalıştığını varsayar. Hizmetin nasıl oluşturulabildiğini öğrenmek için [bkz.](how-to-specify-a-service-binding-in-configuration.md) Ayrıca, Windows Communication Foundation'ın (WCF) istemci bileşenlerini otomatik olarak oluşturmak için sağladığı [ServiceModel Metadata Utility Tool'u (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) kullanır. Araç, hizmete erişmek için istemci kodu ve yapılandırma oluşturur.  
  
 İstemci iki bölümden oluşur. Svcutil.exe `ICalculator` arayüzü `ClientCalculator` uygular oluşturur. Bu istemci uygulaması daha sonra bir `ClientCalculator`örnek oluşturarak oluşturulur.  
  
 Bağlayıcı ve adres bilgilerini zorunlu olarak kodda değil, yapılandırmada bildirimsel olarak belirtmek genellikle en iyi yöntemdir. Dağıtılmış bir hizmetin bağlamaları ve adresleri genellikle hizmet geliştirilirken kullanılanlardan farklı olduğundan, koddaki uç noktaları tanımlamak genellikle pratik değildir. Daha genel olarak, bağlama ve adresleme bilgilerini kodun dışında tutmak, uygulamayı yeniden derlemek veya yeniden dağıtmak zorunda kalmadan değişmelerini sağlar.  
  
 [Yapılandırma Düzenleyicisi Aracını (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md)kullanarak aşağıdaki yapılandırma adımlarının tümlerini gerçekleştirebilirsiniz.  
  
 Bu örneğin kaynak kopyası için [Temel Bağlama](./samples/basicbinding.md) örneğine bakın.  
  
### <a name="specifying-a-client-binding-in-configuration"></a>Yapılandırmada istemci bağlama belirtme  
  
1. Hizmet meta verilerinden kod oluşturmak için komut satırından Svcutil.exe'yi kullanın.  
  
    ```console  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
    ```  
  
2. Oluşturulan istemci, istemci `ICalculator` uygulamasının karşılaması gereken hizmet sözleşmesini tanımlayan arabirimi içerir.  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#1)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#1)]  
  
3. Oluşturulan istemci de uygulanmasını `ClientCalculator`içerir.  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#2)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#2)]  
  
4. Svcutil.exe ayrıca <xref:System.ServiceModel.BasicHttpBinding> sınıfı kullanan istemci için yapılandırma oluşturur. Visual Studio'yu kullanırken bu dosyayı App.config olarak adlandırın. Adres ve bağlama bilgilerinin hizmetin uygulanması nın herhangi bir yerinde belirtilmediğini unutmayın. Ayrıca, yapılandırma dosyasından bu bilgileri almak için kod yazılması gerekmez.  
  
     [!code-xml[C_HowTo_ConfigureClientBinding#100](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/common/client.exe.config#100)]

5. Bir uygulamadaki `ClientCalculator` nin bir örneğini oluşturun ve ardından servis işlemlerini arayın.  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/client.cs#3)]  
  
6. İstemciyi derle ve çalıştır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](using-bindings-to-configure-services-and-clients.md)
