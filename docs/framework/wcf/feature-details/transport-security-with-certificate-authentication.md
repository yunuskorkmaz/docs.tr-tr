---
title: Sertifika Kimlik Doğrulama ile Taşıma Güvenliği
ms.date: 03/30/2017
dev_langs:
- csharp
ms.assetid: 3d726b71-4d8b-4581-a3bb-02b9af51d11b
ms.openlocfilehash: ad2f0922afbd94e1699b383cf2fc9762771b637d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184324"
---
# <a name="transport-security-with-certificate-authentication"></a>Sertifika Kimlik Doğrulama ile Taşıma Güvenliği

Bu makalede, aktarım güvenliği kullanırken sunucu ve istemci kimlik doğrulaması için X.509 sertifikaları nın kullanılması anlatılmaktadır. X.509 sertifikaları hakkında daha fazla bilgi için [Bkz. X.509 Ortak Anahtar Sertifikaları.](/windows/desktop/SecCertEnroll/about-x-509-public-key-certificates) Sertifikalar, genellikle sertifikaların üçüncü taraf vereni olan bir sertifika yetkilisi tarafından verilmelidir. Bir Windows Server etki alanında, Etkin Dizin Sertifika Hizmetleri etki alanında istemci bilgisayarlara sertifika vermek için kullanılabilir. Bu senaryoda, hizmet Güvenli Soketkatmanı (SSL) ile yapılandırılan Internet Information Services (IIS) altında barındırılır. Hizmet, istemcilerin sunucunun kimliğini doğrulamasına olanak sağlamak için bir SSL (X.509) sertifikası ile yapılandırılır. İstemci ayrıca, hizmetin istemcinin kimliğini doğrulamasına olanak tanıyan bir X.509 sertifikasıyla da yapılandırılır. Sunucunun sertifikası istemci tarafından güvenilmeli ve istemcinin sertifikası sunucu tarafından güvenilmelidir. Hizmetin ve istemcinin birbirlerinin kimliğini doğrulama sının gerçek mekaniği bu makalenin kapsamı dışındadır. Daha fazla bilgi için Wikipedia'da [Dijital İmza'ya](https://en.wikipedia.org/wiki/Digital_signature) bakın.
  
 Bu senaryo, aşağıdaki diyagramda gösterildiği gibi bir istek/yanıt iletisi deseni uygular.  
  
 ![Sertifikaları kullanarak güvenli aktarım](../../../../docs/framework/wcf/feature-details/media/8f7b8968-899f-4538-a9e8-0eaa872a291c.gif "8f7b8968-899f-4538-a9e8-0eaa872a291c")  
  
 Hizmetli bir sertifika kullanma hakkında daha fazla bilgi için bkz: [Sertifikalarla Çalışma](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) ve [Nasıl Yapılandırılabilen: SSL Sertifikası olan bir Bağlantı Noktasını Yapılandırma.](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md) Aşağıdaki tabloda senaryonun çeşitli özellikleri açıklanmaktadır.  
  
|Özellik|Açıklama|  
|--------------------|-----------------|  
|Güvenlik Modu|Aktarım|  
|Birlikte çalışabilirlik|Mevcut Web hizmeti istemcileri ve hizmetleri ile.|  
|Kimlik Doğrulama (Sunucu)<br /><br /> Kimlik Doğrulama (İstemci)|Evet (SSL sertifikası kullanarak)<br /><br /> Evet (X.509 sertifikası kullanarak)|  
|Veri Bütünlüğü|Evet|  
|Veri Gizliliği|Evet|  
|Aktarım|HTTPS|  
|Bağlama|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="configure-the-service"></a>Hizmeti Yapılandırma  
 Bu senaryodaki hizmet IIS altında barındırıldığından, bir web.config dosyasıyla yapılandırılır. Aşağıdaki web.config taşıma güvenliği ve <xref:System.ServiceModel.WSHttpBinding> X.509 istemci kimlik bilgilerini kullanmak için nasıl yapılandırılabildiğini gösterir.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <protocolMapping>  
      <add scheme="https" binding="wsHttpBinding" />  
    </protocolMapping>  
    <bindings>  
      <wsHttpBinding>  
        <!-- configure wsHttp binding with Transport security mode and clientCredentialType as Certificate -->  
        <binding>  
          <security mode="Transport">  
            <transport clientCredentialType="Certificate"/>
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>
           <serviceDebug includeExceptionDetailInFaults="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="configure-the-client"></a>İstemciyi Yapılandırma  
 İstemci kod veya app.config dosyasında yapılandırılabilir. Aşağıdaki örnekte, istemcinin kod da nasıl yapılandırılabildiğini gösterilmektedir.  
  
```csharp
// Create the binding.  
var myBinding = new WSHttpBinding();  
myBinding.Security.Mode = SecurityMode.Transport;  
myBinding.Security.Transport.ClientCredentialType =  
   HttpClientCredentialType.Certificate;  
  
// Create the endpoint address. Note that the machine name
// must match the subject or DNS field of the X.509 certificate  
// used to authenticate the service.
var ea = new  
   EndpointAddress("https://localhost/CalculatorService/service.svc");  
  
// Create the client. The code for the calculator
// client is not shown here. See the sample applications  
// for examples of the calculator code.  
var cc =  
   new CalculatorClient(myBinding, ea);  
  
// The client must specify a certificate trusted by the server.  
cc.ClientCredentials.ClientCertificate.SetCertificate(  
    StoreLocation.CurrentUser,  
    StoreName.My,  
    X509FindType.FindBySubjectName,  
    "contoso.com");  
  
// Begin using the client.  
Console.WriteLine(cc.Add(100, 1111));  
//...  
cc.Close();  
```  
  
 Alternatif olarak, istemciyi aşağıdaki örnekte gösterildiği gibi bir App.config dosyasında yapılandırabilirsiniz:  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <!-- this endpoint has an https: address -->  
      <endpoint address=" https://localhost/CalculatorService/service.svc "
                behaviorConfiguration="endpointCredentialBehavior"  
                binding="wsHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.Samples.TransportSecurity.ICalculator"/>  
    </client>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="endpointCredentialBehavior">  
          <clientCredentials>  
            <clientCertificate findValue="contoso.com"  
                               storeLocation="CurrentUser"  
                               storeName="My"  
                               x509FindType="FindBySubjectName" />  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <bindings>  
      <wsHttpBinding>  
        <!-- configure wsHttpbinding with Transport security mode  
                   and clientCredentialType as Certificate -->  
        <binding name="Binding1">  
          <security mode="Transport">  
            <transport clientCredentialType="Certificate"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
  </system.serviceModel>  
  
<startup><supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.0"/></startup></configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenliğe Genel Bakış](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [Windows Server App Fabric için Güvenlik Modeli](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
