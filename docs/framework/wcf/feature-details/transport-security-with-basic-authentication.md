---
title: Temel Kimlik Doğrulama ile Taşıma Güvenliği
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b54f491d-196b-4279-876c-76b83ec0442c
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 65d076a9fef716fca4fe87df6bc5c7773e2dda0f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33499121"
---
# <a name="transport-security-with-basic-authentication"></a>Temel Kimlik Doğrulama ile Taşıma Güvenliği
Aşağıdaki çizimde, bir Windows Communication Foundation (WCF) hizmetini ve istemci gösterir. Güvenli Yuva Katmanı (SSL) için kullanılan geçerli bir X.509 sertifikası sunucu gerekir ve istemcilerin sunucu sertifikasına güvenmesi gerekir. Ayrıca, Web hizmeti, kullanılabilir bir SSL uygulaması zaten içeriyor. Daha fazla bilgi için etkinleştirme temel kimlik doğrulaması hakkında Internet Information Services (IIS) üzerinde [ http://go.microsoft.com/fwlink/?LinkId=83822 ](http://go.microsoft.com/fwlink/?LinkId=83822).  
  
 ![Taşıma güvenliği temel kimlik doğrulaması ile](../../../../docs/framework/wcf/feature-details/media/securedbyusername.gif "SecuredbyUsername")  
  
|Özelliği|Açıklama|  
|--------------------|-----------------|  
|Güvenlik modu|Taşıma|  
|Birlikte Çalışabilirlik|Mevcut Web hizmeti istemcileri ve Hizmetleri|  
|Kimlik doğrulaması (sunucu)<br /><br /> Kimlik doğrulaması (istemci)|Evet (HTTPS kullanarak)<br /><br /> Evet (kullanıcı adı/parola)|  
|Bütünlük|Evet|  
|Gizliliği|Evet|  
|Taşıma|HTTPS|  
|Bağlama|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a>Hizmet  
 Aşağıdaki kod ve yapılandırma bağımsız olarak çalışmaya yöneliktir. Aşağıdakilerden birini yapın:  
  
-   Kod yapılandırma gerektirmeden kullanarak tek başına bir hizmet oluşturun.  
  
-   Sağlanan yapılandırma kullanarak bir hizmet oluşturun, ancak uç tanımlamıyor.  
  
### <a name="code"></a>Kod  
 Aşağıdaki kod, bir Windows etki alanı kullanıcı adı ve parola aktarımı güvenlik için kullandığı bir hizmet uç noktası oluşturma gösterilmektedir. Hizmeti için istemci kimlik doğrulaması için bir X.509 sertifikası gerektirir. Daha fazla bilgi için bkz: [sertifikalarla çalışma](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) ve [nasıl yapılır: bir SSL sertifikası ile bir bağlantı noktası yapılandırın](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).  
  
 [!code-csharp[C_SecurityScenarios#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#1)]
 [!code-vb[C_SecurityScenarios#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#1)]  
  
## <a name="configuration"></a>Yapılandırma  
 Bir hizmet ile aktarım düzeyinde güvenlik temel kimlik doğrulaması kullanacak şekilde yapılandırır:  
  
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
 Aşağıdaki kod kullanıcı adını ve parolayı içeren istemci kodu gösterir. Kullanıcının geçerli bir Windows kullanıcı adı ve parola sağlamalısınız unutmayın. Kullanıcı adı ve parola döndürecek olan kodu burada gösterilmiyor. Bir iletişim kutusu veya diğer arabirimi kullanıcıdan bilgi sorgulamak için kullanın.  
  
> [!NOTE]
>  Kullanıcı adı ve parola yalnızca kod kullanılarak ayarlanabilir.  
  
 [!code-csharp[C_SecurityScenarios#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#2)]
 [!code-vb[C_SecurityScenarios#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#2)]  
  
### <a name="configuration"></a>Yapılandırma  
 Aşağıdaki kod istemci yapılandırmasını gösterir.  
  
> [!NOTE]
>  Kullanıcı adını ve parolasını ayarlamak için yapılandırma kullanamazsınız. Burada gösterilen yapılandırması, kullanıcı adını ve parolasını ayarlamak için kod kullanarak yükseltilmelidir.  
  
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
 [Windows Server App Fabric için güvenlik modeli](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
