---
title: Windows İstemcisi ile Kimlik Bilgileri Görüşmesi Olmadan İleti Güvenliği
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fc07a26c-cbee-41c5-8fb0-329085fef749
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 7f46ea28fe0827e7919b62550492d66a51a125fc
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2018
ms.locfileid: "44365919"
---
# <a name="message-security-with-a-windows-client-without-credential-negotiation"></a>Windows İstemcisi ile Kimlik Bilgileri Görüşmesi Olmadan İleti Güvenliği
Aşağıdaki senaryoda, bir Windows Communication Foundation (WCF) istemci ve hizmet Kerberos protokolü tarafından güvenliği sağlanan gösterilmektedir.  
  
 Hem hizmet hem de istemci aynı etki alanında veya güvenilen etki alanlarında olan.  
  
> [!NOTE]
>  Bu senaryo arasındaki farkı ve [Windows İstemcisi ile ileti güvenliği](../../../../docs/framework/wcf/feature-details/message-security-with-a-windows-client.md) olduğu Bu senaryoda hizmeti kimlik bilgileri uygulama iletisi göndermeden önce hizmet ile gerçekleştirmez. Ayrıca, bu Kerberos protokolü gerektiğinden, bu senaryo, bir Windows etki alanı ortamı gerektirir.  
  
 ![Güvenlik kimlik bilgileri görüşmesi olmadan ileti](../../../../docs/framework/wcf/feature-details/media/0c9f9baa-2439-4ef9-92f4-43c242d85d0d.gif "0c9f9baa-2439-4ef9-92f4-43c242d85d0d")  
  
|Özelliği|Açıklama|  
|--------------------|-----------------|  
|Güvenlik modu|İleti|  
|Birlikte Çalışabilirlik|Evet, Kerberos belirteci profili uyumlu istemcilerle WS-güvenlik|  
|Kimlik doğrulaması (sunucu)|İstemci ve sunucu, karşılıklı kimlik doğrulaması|  
|Kimlik doğrulaması (istemci)|İstemci ve sunucu, karşılıklı kimlik doğrulaması|  
|Bütünlüğü|Evet|  
|Gizliliği|Evet|  
|Taşıma|HTTP|  
|Bağlama|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a>Hizmet  
 Aşağıdaki kod ve yapılandırma, bağımsız olarak çalışmaya yöneliktir. Aşağıdakilerden birini yapın:  
  
-   Kod ile yapılandırma kullanarak tek başına bir hizmet oluşturun.  
  
-   Sağlanan Yapılandırması'nı kullanarak bir hizmet oluşturma, ancak tüm uç noktalar tanımlamaz.  
  
### <a name="code"></a>Kod  
 Aşağıdaki kod, ileti güvenliği kullanan bir hizmet uç noktası oluşturur. Kod hizmeti kimlik bilgileri görüşmesi yanı sıra, oluşumunu bir güvenlik bağlamı belirteci (SCT) devre dışı bırakır.  
  
> [!NOTE]
>  Anlaşma olmadan Windows kimlik bilgisi türü kullanmak için hizmetin kullanıcı hesabını Active Directory etki alanı ile kayıtlı hizmet asıl adı (SPN) erişiminiz olmalıdır. Bunu iki şekilde yapabilirsiniz:  
  
1.  Kullanım `NetworkService` veya `LocalSystem` hizmetinizi çalıştırmak için hesap. Bu hesapların makinenin Active Directory etki alanına katıldığında kurulur SPN makineye erişimi olduğundan, WCF uygun SPN öğe içinde hizmet uç noktası hizmetin meta verilerinde (Web Hizmetleri Açıklama otomatik olarak oluşturur. Dil veya WSDL).  
  
2.  Hizmetinizi çalıştırmak için rastgele bir Active Directory etki alanı hesabı kullanın. Bu durumda, bu etki alanı hesabı için bir SPN oluşturmanız gerekir. Bunu yapmanın bir yolu, Setspn.exe yardımcı programı aracını kullanmaktır. Hizmet hesabı için SPN'nin oluşturulduktan sonra WCF meta verilerini (WSDL) aracılığıyla hizmetin istemciler söz konusu SPN yayımlamak için yapılandırın. Bu ortaya çıkarılan uç nokta için uç nokta kimliğini ayarlayarak yapılır ya da bir uygulama yapılandırma dosyası veya kod. Aşağıdaki örnek kimliğini programlı olarak yayımlar.  
  
 SPN hakkında daha fazla bilgi, Kerberos protokolü ve Active Directory için bkz. [Kerberos teknik ek Windows için](https://go.microsoft.com/fwlink/?LinkId=88330). Uç nokta kimlikleri hakkında daha fazla bilgi için bkz. [SecurityBindingElement kimlik doğrulama modları](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md).  
  
 [!code-csharp[C_SecurityScenarios#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#12)]
 [!code-vb[C_SecurityScenarios#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#12)]  
  
### <a name="configuration"></a>Yapılandırma  
 Aşağıdaki yapılandırmayı kod yerine kullanılabilir.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors />  
    <services>  
      <service behaviorConfiguration="" name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"   
                  binding="wsHttpBinding"  
                  bindingConfiguration="KerberosBinding"  
                  name="WSHttpBinding_ICalculator"  
                  contract="ServiceModel.ICalculator"   
                  listenUri="net.tcp://localhost/metadata" >  
         <identity>  
            <servicePrincipalName value="service_spn_name" />  
         </identity>  
        </endpoint>  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="KerberosBinding">  
          <security>  
            <message negotiateServiceCredential="false"   
                     establishSecurityContext="false" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a>İstemci  
 Aşağıdaki kod ve yapılandırma, bağımsız olarak çalışmaya yöneliktir. Aşağıdakilerden birini yapın:  
  
-   Bir tek başına istemci kodu (ve istemci kodu) kullanarak oluşturun.  
  
-   Herhangi bir uç nokta adresi tanımlamıyor bir istemci oluşturun. Bunun yerine, yapılandırma adı bağımsız değişkeni olarak alan İstemci Oluşturucu kullanın. Örneğin:  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a>Kod  
 Aşağıdaki kod, istemciyi yapılandırır. İleti güvenlik modunu ayarlanır ve istemci kimlik bilgisi türü için Windows ayarlanır. Unutmayın <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> ve <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> özelliklerinin `false`.  
  
> [!NOTE]
>  Windows kimlik bilgisi türü görüşmesi olmadan kullanmak için İstemci hizmet hesabı SPN hizmeti ile iletişimi işlemi hızlandırılabilir önce yapılandırılması gerekir. İstemci kimlik doğrulaması ve hizmeti ile iletişimi güvenli hale getirmek için Kerberos belirteci almak için SPN kullanır. Aşağıdaki örnek, sunucunun hizmetin SPN'si ile istemci yapılandırma işlemi gösterilmektedir. Kullanıyorsanız [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) hizmetin meta veri içeriyorsa, istemci üretmek için sunucunun hizmetin SPN'si otomatik olarak istemciye hizmet meta verileri (WSDL) iletilir Bu bilgileri. Hizmet meta verilerde, SPN eklemek için hizmet yapılandırma hakkında daha fazla bilgi için bu konunun ilerleyen bölümlerindeki "Hizmeti" bölümüne bakın.  
>   
>  SPN, Kerberos ve Active Directory hakkında daha fazla bilgi için bkz. [Kerberos teknik ek Windows için](https://go.microsoft.com/fwlink/?LinkId=88330). Uç nokta kimlikleri hakkında daha fazla bilgi için bkz. [SecurityBindingElement kimlik doğrulama modları](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md) konu.  
  
 [!code-csharp[C_SecurityScenarios#19](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#19)]
 [!code-vb[C_SecurityScenarios#19](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#19)]  
  
### <a name="configuration"></a>Yapılandırma  
 Aşağıdaki kod, istemciyi yapılandırır. Unutmayın [ \<servicePrincipalName >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md) öğesi hizmet hesabının Active Directory etki alanında kayıtlı sunucunun hizmetin SPN'si eşleşecek şekilde ayarlanması gerekir.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="Windows"   
                     negotiateServiceCredential="false"  
                     establishSecurityContext="false" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://localhost/Calculator"   
                binding="wsHttpBinding"  
                bindingConfiguration="WSHttpBinding_ICalculator"  
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator">  
        <identity>  
          <servicePrincipalName value="service_spn_name" />  
        </identity>  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Güvenliğe Genel Bakış](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Kimlik Doğrulama ile Hizmet Kimliği](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [Windows Server AppFabric için güvenlik modeli](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
