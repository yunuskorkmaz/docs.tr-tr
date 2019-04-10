---
title: 'Nasıl yapılır: Yapılandırmada Hizmet Bağlama Belirtme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 885037f7-1c2b-4d7a-90d9-06b89be172f2
ms.openlocfilehash: 5471e6d5610fd74a71a53624392d757f85304236
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59229868"
---
# <a name="how-to-specify-a-service-binding-in-configuration"></a>Nasıl yapılır: Yapılandırmada Hizmet Bağlama Belirtme
Bu örnekte, bir `ICalculator` anlaşma temel hesaplayıcı hizmeti için tanımlanan, hizmet içinde uygulanan `CalculatorService` sınıf ve onun uç noktası burada belirtilen hizmet kullandığını Web.config dosyasında yapılandırılmış <xref:System.ServiceModel.BasicHttpBinding> . Yapılandırma yerine kod kullanarak bu hizmeti yapılandırmak nasıl bir açıklaması için bkz [nasıl yapılır: Kodda hizmet bağlama belirtme](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-code.md).  
  
 Yapılandırma yerine kesin kod bağlama ve adres bilgilerini bildirimli olarak belirtmek için genellikle en iyi uygulamadır. Bağlamalarında ve adreslerinde dağıtılan bir hizmette hizmet geliştirilen kullandığı olanlardan genellikle farklı olduğundan uç noktaları kodda tanımlama genellikle pratik değildir. Daha genel olarak, bağlama tutulması ve adresleme bilgilerini kodunun dışında yeniden derleyin veya uygulama yeniden dağıtmaya gerek kalmadan değiştirmek için bunları sağlar.  
  
 Tüm aşağıdaki yapılandırma adımlarını kullanarak gerçekleştirilen [Yapılandırma Aracı (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).  
  
 Bu örnekte kaynak kopyası için bkz: [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md).  
  
### <a name="to-specify-the-basichttpbinding-to-use-to-configure-the-service"></a>BasicHttpBinding hizmeti yapılandırmak için kullanmak üzere belirtmek için  
  
1.  Hizmet türü için bir hizmet anlaşmasını tanımlar.  
  
     [!code-csharp[C_HowTo_ConfigureServiceBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureservicebinding/cs/source.cs#1)]
     [!code-vb[C_HowTo_ConfigureServiceBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_configureservicebinding/vb/source.vb#1)]  
  
2.  Hizmet sözleşmesi bir hizmet sınıfında uygulayın.  
  
     [!code-csharp[C_HowTo_ConfigureServiceBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureservicebinding/cs/source.cs#2)]
     [!code-vb[C_HowTo_ConfigureServiceBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_configureservicebinding/vb/source.vb#2)]  
  
    > [!NOTE]
    >  Adres veya bağlama bilgileri hizmeti uygulaması içinde belirtilmedi. Ayrıca, bu bilgileri yapılandırma dosyasından getirilecek yazılacak kod yok.  
  
3.  Bir uç nokta için yapılandırmak için bir Web.config dosyası oluşturma `CalculatorService` kullanan <xref:System.ServiceModel.WSHttpBinding>.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.serviceModel>  
        <services>  
          <service name=" CalculatorService" >  
            <endpoint   
            <!-- Leave the address blank to be populated by default -->  
            <!-- from the hosting environment,in this case IIS, so -->  
            <!-- the address will just be that of the IIS Virtual -->  
            <!-- Directory. -->  
                address=""   
            <!-- Specify the binding type -->  
                binding="wsHttpBinding"  
            <!-- Specify the binding configuration name for that -->  
            <!-- binding type. This is optional but useful if you -->  
            <!-- want to modify the properties of the binding. -->  
            <!-- The bindingConfiguration name Binding1 is defined -->  
            <!-- below in the bindings element. -->  
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
  
4.  Aşağıdaki satırı içeren bir Service.svc dosyası oluşturun ve, Internet Information Services (IIS) sanal dizinine yerleştirin.  
  
    ```  
    <%@ServiceHost language=c# Service="CalculatorService" %>   
    ```  
  
### <a name="to-modify-the-default-values-of-the-binding-properties"></a>Bağlama özelliklerin varsayılan değerlerini değiştirmek için  
  
1.  Varsayılan özellik değerlerini birini değiştirmek için <xref:System.ServiceModel.WSHttpBinding>, yeni bir bağlama Yapılandırması adı - oluşturma `<binding name="Binding1">` - içinde [ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) öğesi ve öznitelikleri için yeni değerleri ayarlayın Bu bağlama öğesi bağlama. Örneğin, varsayılan açık değiştirmek ve 1 dakika ile 2 dakikalık zaman aşımı değerlerini kapatmak için yapılandırma dosyasına aşağıdakileri ekleyin.  
  
    ```xml  
    <wsHttpBinding>  
      <binding name="Binding1"  
               closeTimeout="00:02:00"  
               openTimeout="00:02:00">  
      </binding>  
    </wsHttpBinding>  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [Bir Uç Noktası Adresi Belirtme](../../../docs/framework/wcf/specifying-an-endpoint-address.md)
