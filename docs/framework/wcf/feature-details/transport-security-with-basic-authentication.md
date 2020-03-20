---
title: Temel Kimlik Doğrulama ile Taşıma Güvenliği
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b54f491d-196b-4279-876c-76b83ec0442c
ms.openlocfilehash: 1b2b451eb1ea6a1a49ce1ba8cc1edef1fe72d01b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184348"
---
# <a name="transport-security-with-basic-authentication"></a>Temel Kimlik Doğrulama ile Taşıma Güvenliği
Aşağıdaki resimde bir Windows Communication Foundation (WCF) hizmeti ve istemcisi gösterilmektedir. Sunucunun Güvenli Soket katmanı (SSL) için kullanılabilecek geçerli bir X.509 sertifikasına ihtiyacı vardır ve istemcilerin sunucunun sertifikasına güvenmesi gerekir. Ayrıca, Web hizmeti zaten kullanılabilecek bir SSL uygulaması vardır. Internet Bilgi Hizmetleri 'nde (IIS) temel kimlik <https://docs.microsoft.com/iis/configuration/system.webserver/security/authentication/basicauthentication>doğrulamayı etkinleştirme hakkında daha fazla bilgi için bkz.  
  
 ![Temel kimlik doğrulaması ile aktarım güvenliğini gösteren ekran görüntüsü.](./media/transport-security-with-basic-authentication/transport-security-basic-authentication.gif)  
  
|Özellik|Açıklama|  
|--------------------|-----------------|  
|Güvenlik Modu|Aktarım|  
|Birlikte çalışabilirlik|Mevcut Web hizmeti istemcileri ve hizmetleri ile|  
|Kimlik Doğrulama (Sunucu)<br /><br /> Kimlik Doğrulama (İstemci)|Evet (HTTPS kullanarak)<br /><br /> Evet (Kullanıcı adı/Şifre ile)|  
|Bütünlük|Evet|  
|Gizlilik|Evet|  
|Aktarım|HTTPS|  
|Bağlama|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a>Hizmet  
 Aşağıdaki kod ve yapılandırma bağımsız olarak çalışmak içindir. Aşağıdakilerden birini yapın:  
  
- Yapılandırma olmadan kodu kullanarak tek başına bir hizmet oluşturun.  
  
- Sağlanan yapılandırmayı kullanarak bir hizmet oluşturun, ancak herhangi bir uç nokta tanımlamayın.  
  
### <a name="code"></a>Kod  
 Aşağıdaki kod, aktarım güvenliği için Windows etki alanı kullanıcı adı ve parolasını kullanan bir hizmet bitiş noktasının nasıl oluşturulurunun gösteriş olduğunu gösterir. Hizmetin istemciye kimlik doğrulaması için X.509 sertifikası gerektirdiğini unutmayın. Daha fazla bilgi için bkz: [Sertifikalarla Çalışma](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) ve [Nasıl Yapılacağını: SSL Sertifikası olan bir Bağlantı Noktasını Yapılandırma.](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)  
  
 [!code-csharp[C_SecurityScenarios#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#1)]
 [!code-vb[C_SecurityScenarios#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#1)]  
  
## <a name="configuration"></a>Yapılandırma  
 Aşağıdaki, bir hizmeti aktarım düzeyinde güvenlikle temel kimlik doğrulamasını kullanacak şekilde yapılandırır:  
  
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
 Aşağıdaki kod, kullanıcı adı ve parolayı içeren istemci kodunu gösterir. Kullanıcının geçerli bir Windows kullanıcı adı ve parola sağlaması gerektiğini unutmayın. Kullanıcı adını ve parolayı döndürecek kod burada gösterilmez. Bilgileri kullanıcıyı sorgulamak için bir iletişim kutusu veya başka bir arabirim kullanın.  
  
> [!NOTE]
> Kullanıcı adı ve parola yalnızca kod kullanılarak ayarlanabilir.  
  
 [!code-csharp[C_SecurityScenarios#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#2)]
 [!code-vb[C_SecurityScenarios#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#2)]  
  
### <a name="configuration"></a>Yapılandırma  
 Aşağıdaki kod istemci yapılandırmasını gösterir.  
  
> [!NOTE]
> Kullanıcı adını ve parolayı ayarlamak için yapılandırmayı kullanamazsınız. Burada gösterilen yapılandırma, kullanıcı adını ve parolayı ayarlamak için kod kullanılarak artırılmalıdır.  
  
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
- [Sertifikalarla Çalışma](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [Nasıl Yapılır: SSL Sertifikası ile Bir Bağlantı Noktasını Yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)
- [Güvenliğe Genel Bakış](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [\<istemciKimlik bilgileri>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)
- [Windows Server App Fabric için Güvenlik Modeli](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
