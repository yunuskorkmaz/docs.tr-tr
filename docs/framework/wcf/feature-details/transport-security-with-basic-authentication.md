---
title: Temel Kimlik Doğrulama ile Taşıma Güvenliği
description: Bir WCF hizmeti ve istemcisi için temel kimlik doğrulaması gösteren bu WCF senaryosunu inceleyin. Hizmetin, istemcinin güvendiği geçerli bir sertifikası olması gerekir.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b54f491d-196b-4279-876c-76b83ec0442c
ms.openlocfilehash: 2add8c21ca8ade4b530e0e6b1b3c5bba66e100ab
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556791"
---
# <a name="transport-security-with-basic-authentication"></a>Temel Kimlik Doğrulama ile Taşıma Güvenliği
Aşağıdaki çizimde bir Windows Communication Foundation (WCF) hizmeti ve istemcisi gösterilmektedir. Sunucu, Güvenli Yuva Katmanı (SSL) için kullanılabilecek geçerli bir X. 509.440 sertifikasına ihtiyaç duyuyor ve istemcilerin sunucunun sertifikasına güvenmesi gerekir. Ayrıca, Web hizmeti zaten kullanılabilecek bir SSL uygulamasına sahiptir. Internet Information Services (IIS) üzerinde temel kimlik doğrulamasını etkinleştirme hakkında daha fazla bilgi için bkz <https://docs.microsoft.com/iis/configuration/system.webserver/security/authentication/basicauthentication> ..  
  
 ![Temel kimlik doğrulaması ile taşıma güvenliğini gösteren ekran görüntüsü.](./media/transport-security-with-basic-authentication/transport-security-basic-authentication.gif)  
  
|Özellik|Description|  
|--------------------|-----------------|  
|Güvenlik modu|Aktarım|  
|Birlikte Çalışabilirlik|Mevcut Web hizmeti istemcileri ve hizmetleriyle|  
|Kimlik doğrulaması (sunucu)<br /><br /> Kimlik doğrulaması (Istemci)|Evet (HTTPS kullanarak)<br /><br /> Evet (Kullanıcı adı/parola aracılığıyla)|  
|Bütünlük|Yes|  
|Gizlilik|Yes|  
|Aktarım|HTTPS|  
|Bağlama|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a>Hizmet  
 Aşağıdaki kod ve yapılandırma bağımsız olarak çalışacak şekilde tasarlanmıştır. Şunlardan birini yapın:  
  
- Yapılandırma olmadan kodu kullanarak tek başına bir hizmet oluşturun.  
  
- Sağlanan yapılandırmayı kullanarak bir hizmet oluşturun, ancak herhangi bir uç nokta tanımlamaz.  
  
### <a name="code"></a>Kod  
 Aşağıdaki kod, aktarım güvenliği için bir Windows etki alanı Kullanıcı adı ve parolası kullanan bir hizmet uç noktası oluşturmayı gösterir. Hizmetin, istemcinin kimliğini doğrulamak için bir X. 509.440 sertifikası gerektirdiğini unutmayın. Daha fazla bilgi için bkz. [sertifikalarla çalışma](working-with-certificates.md) ve [nasıl yapılır: SSL sertifikası Ile bağlantı noktası yapılandırma](how-to-configure-a-port-with-an-ssl-certificate.md).  
  
 [!code-csharp[C_SecurityScenarios#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#1)]
 [!code-vb[C_SecurityScenarios#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#1)]  
  
## <a name="configuration"></a>Yapılandırma  
 Aşağıda, aktarım düzeyi güvenlik ile temel kimlik doğrulaması kullanmak için bir hizmet yapılandırılır:  
  
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
 Aşağıdaki kod, Kullanıcı adını ve parolasını içeren istemci kodunu gösterir. Kullanıcının geçerli bir Windows Kullanıcı adı ve parolası sağlaması gerektiğini unutmayın. Kullanıcı adını ve parolayı döndüren kod burada gösterilmez. Bilgileri Kullanıcı için sorgulamak üzere bir iletişim kutusu veya başka bir arabirim kullanın.  
  
> [!NOTE]
> Kullanıcı adı ve parola yalnızca kod kullanılarak ayarlanabilir.  
  
 [!code-csharp[C_SecurityScenarios#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#2)]
 [!code-vb[C_SecurityScenarios#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#2)]  
  
### <a name="configuration"></a>Yapılandırma  
 Aşağıdaki kod, istemci yapılandırmasını gösterir.  
  
> [!NOTE]
> Kullanıcı adını ve parolayı ayarlamak için yapılandırma kullanamazsınız. Burada gösterilen yapılandırma, Kullanıcı adı ve parolasını ayarlamak için kod kullanılarak artıralınmalıdır.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>
- [Sertifikalarla Çalışma](working-with-certificates.md)
- [Nasıl yapılır: SSL Sertifikası ile Bir Bağlantı Noktasını Yapılandırma](how-to-configure-a-port-with-an-ssl-certificate.md)
- [Güvenliğe genel bakış](security-overview.md)
- [\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md)
- [Windows Server App Fabric için güvenlik modeli](/previous-versions/appfabric/ee677202(v=azure.10))
