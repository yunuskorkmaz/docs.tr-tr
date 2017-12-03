---
title: "Nasıl yapılır: Yapılandırmada Hizmet Bağlama Belirtme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 885037f7-1c2b-4d7a-90d9-06b89be172f2
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0220dffd07f41210051953130cf99ebbfd4f0173
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-specify-a-service-binding-in-configuration"></a>Nasıl yapılır: Yapılandırmada Hizmet Bağlama Belirtme
Bu örnekte, bir `ICalculator` anlaşma temel hesaplayıcı hizmeti için tanımlanan, hizmet içinde uygulanan `CalculatorService` sınıfı ve kendi uç noktası burada belirtilen hizmet kullandığını Web.config dosyasında yapılandırılmış <xref:System.ServiceModel.BasicHttpBinding> . Kod yerine bir yapılandırmayla bu hizmetinin nasıl yapılandırılacağı açıklaması için bkz: [nasıl yapılır: kodda hizmet bağlama belirtme](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-code.md).  
  
 Bağlama ve adres bilgilerini yapılandırma yerine imperatively kod bildirimli olarak belirtmek için genellikle en iyi uygulamadır. Bağlamalar ve dağıtılmış bir hizmet için adresleri hizmet geliştirildiği sırada kullanılan olanlardan genellikle farklı olduğu için uç noktalar kodda tanımlama genellikle pratik değildir. Daha genel olarak, bağlama tutulması ve adresleme bilgilerini kodu dışında yeniden derleyin veya uygulamayı yeniden dağıtmak zorunda kalmadan değiştirmek için bunları sağlar.  
  
 Tüm aşağıdaki yapılandırma adımlarını kullanarak üstlendiği [Yapılandırma Aracı (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).  
  
 Bu örnekte kaynak kopyası için bkz: [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md).  
  
### <a name="to-specify-the-basichttpbinding-to-use-to-configure-the-service"></a>Hizmeti yapılandırmak için kullanılacak BasicHttpBinding belirtmek için  
  
1.  Hizmet türü için bir hizmet sözleşmesini tanımlama.  
  
     [!code-csharp[C_HowTo_ConfigureServiceBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureservicebinding/cs/source.cs#1)]
     [!code-vb[C_HowTo_ConfigureServiceBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_configureservicebinding/vb/source.vb#1)]  
  
2.  Bir hizmet sınıfında Hizmet sözleşmesini uygulama.  
  
     [!code-csharp[C_HowTo_ConfigureServiceBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureservicebinding/cs/source.cs#2)]
     [!code-vb[C_HowTo_ConfigureServiceBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_configureservicebinding/vb/source.vb#2)]  
  
    > [!NOTE]
    >  Hizmet uygulaması içinde adres veya bağlama bilgisi belirtilmemiş. Ayrıca, bu bilgileri yapılandırma dosyasından getirmek için yazılacak kodu yok.  
  
3.  Bir uç nokta için yapılandırmak için bir Web.config dosyası oluşturma `CalculatorService` kullanan <xref:System.ServiceModel.WSHttpBinding>.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.serviceModel>  
        <services>  
          <service name=" CalculatorService" >  
            <endpoint   
            <-- Leave the address blank to be populated by default-->  
            <--from the hosting environment,in this case IIS, so -->  
            <-- the address will just be that of the IIS Virtual -->  
            <--Directory.-->  
                address=""   
            <--Specify the binding type -->  
                binding="wsHttpBinding"  
            <--Specify the binding configuration name for that -->  
            <--binding type. This is optional but useful if you  -->  
            <--want to modify the properties of the binding. -->  
            <--The bindingConfiguration name Binding1 is defined  -->  
            <--below in the bindings element.  -->  
                bindingConfiguration="Binding1"  
                contract="ICalculator" />  
          </service>  
        </services>  
        <bindings>  
          <wsHttpBinding>  
            <binding name="Binding1">  
              <-- Binding property values can be modified here. -->  
              <--See the next procedure. -->  
            </binding>  
          </wsHttpBinding>  
       </bindings>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
4.  Aşağıdaki satırı içeren bir Service.svc dosyası oluşturun ve Internet Information Services (IIS) sanal dizininizde yerleştirin.  
  
    ```  
    <%@ServiceHost language=c# Service="CalculatorService" %>   
    ```  
  
### <a name="to-modify-the-default-values-of-the-binding-properties"></a>Bağlama özelliklerinin varsayılan değerlerini değiştirmek için  
  
1.  Varsayılan özellik değerlerini birini değiştirmek için <xref:System.ServiceModel.WSHttpBinding>, yeni bir bağlama yapılandırma adı - oluşturmak `<binding name="Binding1">` - içinde [ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) öğesi ve öznitelikleri için yeni değerleri ayarlayın Bu bağlama öğesinde bağlama. Örneğin, varsayılan açık değiştirmek ve 1 dakika 2 dakika olarak zaman aşımı değerlerini kapatmak için aşağıdaki yapılandırma dosyasına ekleyin.  
  
    ```xml  
    <wsHttpBinding>  
      <binding name="Binding1"  
               closeTimeout="00:02:00"  
               openTimeout="00:02:00">  
      </binding>  
    </wsHttpBinding>  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hizmetler ve istemcileri yapılandırmak için bağlamaları kullanma](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [Bir uç noktası adresi belirtme](../../../docs/framework/wcf/specifying-an-endpoint-address.md)
