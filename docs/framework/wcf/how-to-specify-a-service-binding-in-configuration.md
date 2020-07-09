---
title: 'Nasıl yapılır: Yapılandırmada Hizmet Bağlama Belirtme'
description: Bir yapılandırma dosyasında bir WCF hizmeti için uç nokta yapılandırmayı öğrenin. Bir sözleşme, bir hizmet için tanımlanır ve bir sınıfa uygulanır.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 885037f7-1c2b-4d7a-90d9-06b89be172f2
ms.openlocfilehash: 3b9dd12f2a28ae2d420e82013459613cee8140f1
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051954"
---
# <a name="how-to-specify-a-service-binding-in-configuration"></a>Nasıl yapılır: Yapılandırmada Hizmet Bağlama Belirtme
Bu örnekte, bir `ICalculator` anlaşma temel Hesaplayıcı hizmeti için tanımlanmıştır, hizmet `CalculatorService` sınıfında uygulanır ve ardından uç noktası, hizmetin kullandığı Web.config dosyasında yapılandırılır <xref:System.ServiceModel.BasicHttpBinding> . Bu hizmeti yapılandırma yerine kod kullanarak yapılandırma hakkında açıklama için bkz. [nasıl yapılır: kod Içinde hizmet bağlaması belirtme](how-to-specify-a-service-binding-in-code.md).  
  
 Genellikle, bağlama ve adres bilgilerini, kod içinde imperatively yerine bildirimli olarak yapılandırmaya göre belirlemek en iyi uygulamadır. Dağıtılmış bir hizmetin bağlamaları ve adresleri genellikle hizmet geliştirildiğinde kullanılanlardan farklı olduğundan, koddaki uç noktaların tanımlanması genellikle pratik değildir. Daha genel olarak, bağlama ve adresleme bilgilerini koddan tutmanın, uygulamayı yeniden derlemek veya yeniden dağıtmak zorunda kalmadan değiştirilmesine izin verir.  
  
 Aşağıdaki yapılandırma adımlarının tümü, [yapılandırma Düzenleyicisi aracı (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md)kullanılarak uygulanabilir.  
  
 Bu örneğin kaynak kopyası için bkz. [BasicBinding](./samples/basicbinding.md).  
  
## <a name="to-specify-the-basichttpbinding-to-use-to-configure-the-service"></a>Hizmeti yapılandırmak için kullanılacak BasicHttpBinding 'i belirtmek için  
  
1. Hizmet türü için bir hizmet sözleşmesi tanımlayın.  
  
     [!code-csharp[C_HowTo_ConfigureServiceBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureservicebinding/cs/source.cs#1)]
     [!code-vb[C_HowTo_ConfigureServiceBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_configureservicebinding/vb/source.vb#1)]  
  
2. Hizmet sözleşmesini bir hizmet sınıfına uygulayın.  
  
     [!code-csharp[C_HowTo_ConfigureServiceBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureservicebinding/cs/source.cs#2)]
     [!code-vb[C_HowTo_ConfigureServiceBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_configureservicebinding/vb/source.vb#2)]  
  
    > [!NOTE]
    > Hizmet uygulamasının içinde adres veya bağlama bilgisi belirtilmemiş. Ayrıca, bu bilgileri yapılandırma dosyasından getirmek için kodun yazılması gerekmez.  
  
3. Kullanan için bir uç nokta yapılandırmak üzere bir Web.config dosyası oluşturun `CalculatorService` <xref:System.ServiceModel.WSHttpBinding> .  
  
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
  
4. Aşağıdaki satırı içeren bir Service. svc dosyası oluşturun ve bunu Internet Information Services (IIS) sanal dizinine yerleştirin.  
  
    ```aspx-csharp
    <%@ServiceHost language=c# Service="CalculatorService" %>
    ```  
  
## <a name="to-modify-the-default-values-of-the-binding-properties"></a>Bağlama özelliklerinin varsayılan değerlerini değiştirmek için  
  
1. Öğesinin varsayılan özellik değerlerinden birini değiştirmek için, <xref:System.ServiceModel.WSHttpBinding> öğesi içinde yeni bir bağlama yapılandırma adı oluşturun `<binding name="Binding1">` [\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) ve bu Binding öğesindeki bağlamanın özniteliklerinin yeni değerlerini ayarlayın. Örneğin, varsayılan açık ve kapalı zaman aşımı değerlerini 1 dakikalık ila 2 dakikaya değiştirmek için yapılandırma dosyasına aşağıdakini ekleyin.  
  
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
