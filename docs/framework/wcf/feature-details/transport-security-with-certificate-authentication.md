---
title: Sertifika Kimlik Doğrulama ile Taşıma Güvenliği
ms.date: 03/30/2017
dev_langs:
- csharp
ms.assetid: 3d726b71-4d8b-4581-a3bb-02b9af51d11b
ms.openlocfilehash: 47322cbcddf9f33101bbfbeaa07a3fab74b9d26a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84576024"
---
# <a name="transport-security-with-certificate-authentication"></a>Sertifika Kimlik Doğrulama ile Taşıma Güvenliği

Bu makalede, aktarım güvenliği kullanılırken sunucu ve istemci kimlik doğrulaması için X. 509.440 sertifikalarının kullanımı ele alınmaktadır. X. 509.440 sertifikaları hakkında daha fazla bilgi için bkz. [x. 509.440 ortak anahtar sertifikaları](/windows/desktop/SecCertEnroll/about-x-509-public-key-certificates). Sertifikalar, genellikle bir üçüncü taraf sertifika veren olan bir sertifika yetkilisi tarafından verilmelidir. Bir Windows Server etki alanında Active Directory Sertifika Hizmetleri, etki alanındaki istemci bilgisayarlara sertifika vermek için kullanılabilir. Bu senaryoda, hizmet Güvenli Yuva Katmanı (SSL) ile yapılandırılan Internet Information Services (IIS) altında barındırılır. Hizmet, istemcilerin sunucu kimliğini doğrulamasına izin vermek için bir SSL (X. 509.440) sertifikası ile yapılandırılır. İstemci Ayrıca hizmetin istemci kimliğini doğrulamasına izin veren bir X. 509.440 sertifikası ile yapılandırılır. Sunucu sertifikası istemci tarafından güvenilir olmalıdır ve istemcinin sertifikasına sunucu tarafından güvenilmelidir. Hizmetin ve istemcinin her birinin kimliğini nasıl doğrulayadığına ilişkin gerçek bir mekanizması, bu makalenin kapsamı dışındadır. Daha fazla bilgi için bkz. Vikipde [dijital imza](https://en.wikipedia.org/wiki/Digital_signature) .
  
 Bu senaryo, aşağıdaki diyagramda gösterildiği gibi bir istek/yanıt iletisi deseninin bir listesini uygular.  
  
 ![Sertifikaları kullanarak güvenli aktarım](media/8f7b8968-899f-4538-a9e8-0eaa872a291c.gif "8f7b8968-899F-4538-a9e8-0eaa872a291c")  
  
 Hizmeti olan bir sertifika kullanma hakkında daha fazla bilgi için bkz. [sertifikalarla çalışma](working-with-certificates.md) ve bir [SSL sertifikası Ile bağlantı noktası yapılandırma](how-to-configure-a-port-with-an-ssl-certificate.md). Aşağıdaki tabloda senaryonun çeşitli özellikleri açıklanmaktadır.  
  
|Özellik|Açıklama|  
|--------------------|-----------------|  
|Güvenlik modu|Aktarım|  
|Birlikte çalışabilirlik|Mevcut Web hizmeti istemcileri ve hizmetleriyle.|  
|Kimlik doğrulaması (sunucu)<br /><br /> Kimlik doğrulaması (Istemci)|Evet (bir SSL sertifikası kullanarak)<br /><br /> Evet (bir X. 509.440 sertifikası kullanarak)|  
|Veri bütünlüğü|Yes|  
|Veri gizliliği|Yes|  
|Aktarım|HTTPS|  
|Bağlama|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="configure-the-service"></a>Hizmeti yapılandırma  
 Bu senaryodaki hizmet IIS altında barındırıldığından, Web. config dosyası ile yapılandırılır. Aşağıdaki Web. config, <xref:System.ServiceModel.WSHttpBinding> ' ın Transport Security ve X. 509.440 istemci kimlik bilgilerini kullanacak şekilde nasıl yapılandırılacağını gösterir.  
  
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
  
## <a name="configure-the-client"></a>Istemciyi yapılandırma  
 İstemci kodda veya bir App. config dosyasında yapılandırılabilir. Aşağıdaki örnek, kodda istemcisinin nasıl yapılandırılacağını gösterir.  
  
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
  
 Alternatif olarak, aşağıdaki örnekte gösterildiği gibi, istemcisini bir App. config dosyasında yapılandırabilirsiniz:  
  
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

- [Güvenliğe genel bakış](security-overview.md)
- [Windows Server App Fabric için güvenlik modeli](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
