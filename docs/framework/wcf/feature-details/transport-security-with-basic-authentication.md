---
title: Temel Kimlik Doğrulama ile Taşıma Güvenliği
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b54f491d-196b-4279-876c-76b83ec0442c
author: BrucePerlerMS
ms.openlocfilehash: 4a6ad2746bea9dfea1999e272796d44f0341e64d
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47082350"
---
# <a name="transport-security-with-basic-authentication"></a>Temel Kimlik Doğrulama ile Taşıma Güvenliği
Aşağıdaki çizimde, bir Windows Communication Foundation (WCF) hizmet ve istemci gösterir. Sunucusunda Güvenli Yuva Katmanı (SSL) için kullanılabilecek geçerli bir X.509 sertifikası olması gerekir ve istemcilerin sunucu sertifikasına güvenmelidir. Daha fazla Web hizmetinin kullanılabilmesi için bir SSL uygulaması zaten sahip. Daha fazla etkinleştirme temel kimlik doğrulaması hakkında Internet Information Services (IIS) hakkında bilgi için [ https://go.microsoft.com/fwlink/?LinkId=83822 ](https://go.microsoft.com/fwlink/?LinkId=83822).  
  
 ![Aktarım güvenliği temel kimlik doğrulaması ile](../../../../docs/framework/wcf/feature-details/media/securedbyusername.gif "SecuredbyUsername")  
  
|Özelliği|Açıklama|  
|--------------------|-----------------|  
|Güvenlik modu|Taşıma|  
|Birlikte Çalışabilirlik|Mevcut Web hizmeti istemcileri ve Hizmetleri ile|  
|Kimlik doğrulaması (sunucu)<br /><br /> Kimlik doğrulaması (istemci)|Evet (HTTPS kullanarak)<br /><br /> Evet (kullanıcı adı/parola)|  
|Bütünlüğü|Evet|  
|Gizliliği|Evet|  
|Taşıma|HTTPS|  
|Bağlama|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a>Hizmet  
 Aşağıdaki kod ve yapılandırma, bağımsız olarak çalışmaya yöneliktir. Aşağıdakilerden birini yapın:  
  
-   Kod ile yapılandırma kullanarak tek başına bir hizmet oluşturun.  
  
-   Sağlanan Yapılandırması'nı kullanarak bir hizmet oluşturma, ancak tüm uç noktalar tanımlamaz.  
  
### <a name="code"></a>Kod  
 Aşağıdaki kod, bir Windows etki alanı kullanıcı adı ve parola aktarım güvenliği için kullanan bir hizmet uç noktası oluşturma gösterilmektedir. Hizmete istemcinin kimliğini doğrulamak için bir X.509 sertifikası gerektiğini unutmayın. Daha fazla bilgi için [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) ve [nasıl yapılır: bir SSL sertifikası ile bir bağlantı noktası yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).  
  
 [!code-csharp[C_SecurityScenarios#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#1)]
 [!code-vb[C_SecurityScenarios#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#1)]  
  
## <a name="configuration"></a>Yapılandırma  
 Temel kimlik doğrulaması ile aktarım düzeyi güvenlik kullanan bir hizmet yapılandırır:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
    <system.serviceModel>  
        <bindings>  
            <wsHttpBinding>  
                <binding name="UsernameWithTransport">  
                    <security mode="Transport">  
                        <transport clientCredentialType="Basic" />  
                    </security>  
                </binding>  
            </wsHttpBinding>  
        </bindings>  
        <services>  
            <service name="BasicAuthentication.Calculator">  
                <endpoint address="https://localhost/Calculator"  
                          binding="wsHttpBinding"   
                          bindingConfiguration="UsernameWithTransport"  
                          name="BasicEndpoint"   
                          contract="BasicAuthentication.ICalculator" />  
            </service>  
        </services>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a>İstemci  
  
### <a name="code"></a>Kod  
 Aşağıdaki kod, kullanıcı adı ve parola içeren istemci kodu gösterir. Kullanıcı geçerli bir Windows kullanıcı adı ve parola sağlamalıdır unutmayın. Kullanıcı adını ve parolasını döndürmek için kod burada gösterilmez. Kullanıcıdan bilgi sorgulamak için bir iletişim kutusu veya diğer arabirim kullanın.  
  
> [!NOTE]
>  Kullanıcı adı ve parola yalnızca kod kullanılarak ayarlanabilir.  
  
 [!code-csharp[C_SecurityScenarios#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#2)]
 [!code-vb[C_SecurityScenarios#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#2)]  
  
### <a name="configuration"></a>Yapılandırma  
 Aşağıdaki kod, istemci yapılandırmasını gösterir.  
  
> [!NOTE]
>  Kullanıcı adı ve parolasını ayarlamak için yapılandırma kullanamazsınız. Burada gösterilen yapılandırma, kodla kullanıcı adını ve parolasını ayarlamak için yükseltilmelidir.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Transport">  
            <transport clientCredentialType="Basic" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="https://machineName/Calculator"   
                binding="wsHttpBinding"  
                bindingConfiguration="WSHttpBinding_ICalculator"   
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator" />  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>  
 <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>  
 [Sertifikalarla Çalışma](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Nasıl Yapılır: SSL Sertifikası ile Bir Bağlantı Noktasını Yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)  
 [Güvenliğe Genel Bakış](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [\<clientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)  
 [Windows Server AppFabric için güvenlik modeli](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
