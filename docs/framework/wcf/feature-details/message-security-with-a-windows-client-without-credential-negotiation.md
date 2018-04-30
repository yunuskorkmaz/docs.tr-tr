---
title: Windows İstemcisi ile Kimlik Bilgileri Görüşmesi Olmadan İleti Güvenliği
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: fc07a26c-cbee-41c5-8fb0-329085fef749
caps.latest.revision: 18
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 056e743ff1849457f8a0e8ee509a56475f09435c
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="message-security-with-a-windows-client-without-credential-negotiation"></a>Windows İstemcisi ile Kimlik Bilgileri Görüşmesi Olmadan İleti Güvenliği
Aşağıdaki senaryoda gösterildiği bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Kerberos protokolü tarafından güvenli hale getirilmiş hizmet ve istemci.  
  
 Hem hizmet hem de istemci aynı etki alanında veya güvenilen etki alanlarında olan.  
  
> [!NOTE]
>  Bu senaryo arasındaki farkı ve [Windows İstemcisi ile ileti güvenliği](../../../../docs/framework/wcf/feature-details/message-security-with-a-windows-client.md) olduğu Bu senaryoda uygulama iletiyi göndermeden önce hizmetiyle hizmet kimlik bilgilerini gerçekleştirmez. Ayrıca, bu Kerberos protokolü gerektirdiğinden, bu senaryo, bir Windows etki alanı ortamında gerektirir.  
  
 ![Güvenlik kimlik bilgileri görüşmesi olmadan ileti](../../../../docs/framework/wcf/feature-details/media/0c9f9baa-2439-4ef9-92f4-43c242d85d0d.gif "0c9f9baa-2439-4ef9-92f4-43c242d85d0d")  
  
|Özelliği|Açıklama|  
|--------------------|-----------------|  
|Güvenlik modu|İleti|  
|Birlikte Çalışabilirlik|Evet, Kerberos belirteci profili uyumlu istemcileri ile WS güvenliği|  
|Kimlik doğrulaması (sunucu)|İstemci ve sunucu, karşılıklı kimlik doğrulaması|  
|Kimlik doğrulaması (istemci)|İstemci ve sunucu, karşılıklı kimlik doğrulaması|  
|Bütünlük|Evet|  
|Gizliliği|Evet|  
|Taşıma|HTTP|  
|Bağlama|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a>Hizmet  
 Aşağıdaki kod ve yapılandırma bağımsız olarak çalışmaya yöneliktir. Aşağıdakilerden birini yapın:  
  
-   Kod yapılandırma gerektirmeden kullanarak tek başına bir hizmet oluşturun.  
  
-   Sağlanan yapılandırma kullanarak bir hizmet oluşturun, ancak uç tanımlamıyor.  
  
### <a name="code"></a>Kod  
 Aşağıdaki kod, ileti güvenliği kullanan hizmet uç noktası oluşturur. Kod hizmeti kimlik bilgileri görüşmesi ve bir güvenlik bağlamı belirteci (SCT) oluşturulmasını devre dışı bırakır.  
  
> [!NOTE]
>  Windows kimlik bilgisi türü anlaşma olmadan kullanmak için hizmetin kullanıcı hesabının Active Directory etki alanı ile kayıtlı hizmet asıl adı (SPN) erişimi olmalıdır. Bunu iki şekilde yapabilirsiniz:  
  
1.  Kullanım `NetworkService` veya `LocalSystem` , hizmetinizi çalıştırmak için hesap. Bu hesapların makine Active Directory etki alanına katıldığında, kurulur SPN makine erişiminiz olduğundan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygun SPN öğe içinde hizmet uç noktası hizmetin meta veriler (Web Hizmetleri otomatik olarak oluşturur Açıklama Dili veya WSDL).  
  
2.  Hizmetinizi çalıştırmak için rasgele bir Active Directory etki alanı hesabı kullanın. Bu durumda, bu etki alanı hesabı için bir SPN oluşturmanız gerekir. Bunu yapmanın bir yolu, Setspn.exe yardımcı programı aracını kullanmaktır. Hizmet hesabı için SPN oluşturulduktan sonra yapılandırma [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bu SPN hizmetin istemcileri meta verilerini (WSDL) aracılığıyla yayımlamak için. Bu uç nokta kimliği gösterilen uç noktası için ayarlayarak yapılır ya da bir uygulama yapılandırma dosyası veya kod. Aşağıdaki örnek kimliği programlı olarak yayımlar.  
  
 SPN'ler hakkında daha fazla bilgi, Kerberos protokolü ve Active Directory için bkz: [Kerberos teknik Eki'ni Windows için](http://go.microsoft.com/fwlink/?LinkId=88330). Uç nokta kimlikler hakkında daha fazla bilgi için bkz: [SecurityBindingElement kimlik doğrulama modları](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md).  
  
 [!code-csharp[C_SecurityScenarios#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#12)]
 [!code-vb[C_SecurityScenarios#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#12)]  
  
### <a name="configuration"></a>Yapılandırma  
 Aşağıdaki yapılandırma kodu yerine kullanılabilir.  
  
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
 Aşağıdaki kod ve yapılandırma bağımsız olarak çalışmaya yöneliktir. Aşağıdakilerden birini yapın:  
  
-   Kod (ve istemci kodu) kullanan bir tek başına istemci oluşturun.  
  
-   Herhangi bir uç nokta adresi tanımlamıyor bir istemci oluşturun. Bunun yerine, yapılandırma adı bağımsız değişken olarak alan İstemci Oluşturucu kullanın. Örneğin:  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a>Kod  
 Aşağıdaki kod istemci yapılandırır. İletiye güvenlik modunu ayarlama ve istemci kimlik bilgisi türü Windows ayarlanır. Unutmayın <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> ve <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> özelliklerinin `false`.  
  
> [!NOTE]
>  Windows kimlik bilgisi türü anlaşma olmadan kullanmak için İstemci hizmet hesabı SPN hizmetiyle iletişim başlatmadan önce yapılandırılması gerekir. İstemci kimlik doğrulaması ve hizmeti ile iletişimi güvenli hale getirmek için Kerberos belirteci almak için SPN kullanır. Aşağıdaki örnek, sunucunun hizmetin SPN'si ile istemci yapılandırma gösterilmektedir. Kullanıyorsanız [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) hizmetin meta veri içeriyorsa, istemci oluşturmak için sunucunun hizmetin SPN'si otomatik olarak istemciye hizmetin meta verilerini (WSDL) yayılır Bu bilgileri. Hizmetin meta verilerde kendi SPN içerecek şekilde hizmetin yapılandırma hakkında daha fazla bilgi için bu konunun devamındaki "Hizmet" bölümüne bakın.  
>   
>  SPN'ler, Kerberos ve Active Directory hakkında daha fazla bilgi için bkz: [Kerberos teknik Eki'ni Windows için](http://go.microsoft.com/fwlink/?LinkId=88330). Uç nokta kimlikler hakkında daha fazla bilgi için bkz: [SecurityBindingElement kimlik doğrulama modları](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md) konu.  
  
 [!code-csharp[C_SecurityScenarios#19](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#19)]
 [!code-vb[C_SecurityScenarios#19](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#19)]  
  
### <a name="configuration"></a>Yapılandırma  
 Aşağıdaki kod istemci yapılandırır. Unutmayın [ \<servicePrincipalName >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md) öğesi, sunucunun hizmetin SPN'si Active Directory etki alanındaki hizmet hesabının kayıtlı adıyla eşleşecek şekilde ayarlanmalıdır.  
  
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
 [Windows Server App Fabric için güvenlik modeli](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
