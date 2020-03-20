---
title: 'Nasıl yapılır: Yapılandırmada Hizmet Bağlama Belirtme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 885037f7-1c2b-4d7a-90d9-06b89be172f2
ms.openlocfilehash: 245fe50ed5a80c51163652defb642cebefd55dbd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184026"
---
# <a name="how-to-specify-a-service-binding-in-configuration"></a>Nasıl yapılır: Yapılandırmada Hizmet Bağlama Belirtme
Bu örnekte, `ICalculator` temel bir hesap makinesi hizmeti için bir sözleşme `CalculatorService` tanımlanır, hizmet sınıfta uygulanır ve bitiş noktası Web.config dosyasında yapılandırılır <xref:System.ServiceModel.BasicHttpBinding>ve burada hizmetin . Yapılandırma yerine kodu kullanarak bu hizmeti yapılandırmanın nasıl yapılandırılabildiğini açıklamak için [bkz.](how-to-specify-a-service-binding-in-code.md)  
  
 Bağlayıcı ve adres bilgilerini zorunlu olarak kodda değil, yapılandırmada bildirimsel olarak belirtmek genellikle en iyi yöntemdir. Dağıtılmış bir hizmetin bağlamaları ve adresleri genellikle hizmet geliştirilirken kullanılanlardan farklı olduğundan, koddaki uç noktaları tanımlamak genellikle pratik değildir. Daha genel olarak, bağlama ve adresleme bilgilerini kodun dışında tutmak, uygulamayı yeniden derlemek veya yeniden dağıtmak zorunda kalmadan değişmelerini sağlar.  
  
 Aşağıdaki yapılandırma adımlarının tümü [Configuration Editor Aracı (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md)kullanılarak yapılabilir.  
  
 Bu örneğin kaynak kopyası için [BasicBinding'e](./samples/basicbinding.md)bakın.  
  
## <a name="to-specify-the-basichttpbinding-to-use-to-configure-the-service"></a>Hizmeti yapılandırmak için kullanılacak Temel HttpBinding'i belirtmek için  
  
1. Hizmet türü için bir hizmet sözleşmesi tanımlayın.  
  
     [!code-csharp[C_HowTo_ConfigureServiceBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureservicebinding/cs/source.cs#1)]
     [!code-vb[C_HowTo_ConfigureServiceBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_configureservicebinding/vb/source.vb#1)]  
  
2. Hizmet sözleşmesini bir hizmet sınıfında uygulayın.  
  
     [!code-csharp[C_HowTo_ConfigureServiceBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureservicebinding/cs/source.cs#2)]
     [!code-vb[C_HowTo_ConfigureServiceBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_configureservicebinding/vb/source.vb#2)]  
  
    > [!NOTE]
    > Adres veya bağlama bilgileri hizmetin uygulanması içinde belirtilmemiştir. Ayrıca, yapılandırma dosyasından bu bilgileri almak için kod yazılması gerekmez.  
  
3. Bir web.config dosyası oluşturmak için `CalculatorService` bir bitiş noktası <xref:System.ServiceModel.WSHttpBinding>kullanır .  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.serviceModel>  
        <services>  
          <service name=" CalculatorService" >  

            <!-- Leave the address blank to be populated by default -->
            <!-- from the hosting environment,in this case IIS, so -->
            <!-- the address will just be that of the IIS Virtual -->
            <!-- Directory. -->

            <!-- Specify the binding configuration name for that -->
            <!-- binding type. This is optional but useful if you -->
            <!-- want to modify the properties of the binding. -->
            <!-- The bindingConfiguration name Binding1 is defined -->
            <!-- below in the bindings element. -->
            <endpoint
                address=""
                binding="wsHttpBinding"  
                bindingConfiguration="Binding1"  
                contract="ICalculator" />  
          </service>  
        </services>  
        <bindings>  
          <wsHttpBinding>  
            <binding name="Binding1">  
              <!-- Binding property values can be modified here. -->  
              <!-- See the next procedure. -->  
            </binding>  
          </wsHttpBinding>  
       </bindings>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
4. Aşağıdaki satırı içeren bir Service.svc dosyası oluşturun ve internet bilgi hizmetleri (IIS) sanal dizininize yerleştirin.  
  
    ```  
    <%@ServiceHost language=c# Service="CalculatorService" %>
    ```  
  
## <a name="to-modify-the-default-values-of-the-binding-properties"></a>Bağlama özelliklerinin varsayılan değerlerini değiştirmek için  
  
1. Varsayılan özellik değerlerinden birini değiştirmek <xref:System.ServiceModel.WSHttpBinding>için, yeni bir `<binding name="Binding1">` bağlama yapılandırma adı oluşturun - - [ \<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) öğesi içinde ve bu bağlama öğesi bağlayıcı öznitelikleri için yeni değerler ayarlayın. Örneğin, varsayılan açma ve kapatma zaman ayırma değerlerini 1 dakikaile 2 dakika arasında değiştirmek için yapılandırma dosyasına aşağıdakileri ekleyin.  
  
    ```xml  
    <wsHttpBinding>  
      <binding name="Binding1"  
               closeTimeout="00:02:00"  
               openTimeout="00:02:00">  
      </binding>  
    </wsHttpBinding>  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](using-bindings-to-configure-services-and-clients.md)
- [Bir Uç Noktası Adresi Belirtme](specifying-an-endpoint-address.md)
