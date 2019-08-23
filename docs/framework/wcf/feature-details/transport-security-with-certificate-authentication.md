---
title: Sertifika Kimlik Doğrulama ile Taşıma Güvenliği
ms.date: 03/30/2017
dev_langs:
- csharp
ms.assetid: 3d726b71-4d8b-4581-a3bb-02b9af51d11b
ms.openlocfilehash: f94be530fb680320813a93e256e8e411234f2e40
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968655"
---
# <a name="transport-security-with-certificate-authentication"></a>Sertifika Kimlik Doğrulama ile Taşıma Güvenliği
Bu konuda, aktarım güvenliği kullanılırken sunucu ve istemci kimlik doğrulaması için X. 509.440 sertifikalarının kullanımı ele alınmaktadır. X. 509.440 sertifikaları hakkında daha fazla bilgi için bkz. [x. 509.440 ortak anahtar sertifikaları](/windows/desktop/SecCertEnroll/about-x-509-public-key-certificates). Sertifikalar, genellikle bir üçüncü taraf sertifika veren olan bir sertifika yetkilisi tarafından verilmelidir. Bir Windows Server etki alanında Active Directory Sertifika Hizmetleri, etki alanındaki istemci bilgisayarlara sertifika vermek için kullanılabilir. Daha fazla bilgi için bkz. [Windows 2008 R2 Sertifika Hizmetleri](https://go.microsoft.com/fwlink/?LinkID=209949&clcid=0x409). Bu senaryoda, hizmet Güvenli Yuva Katmanı (SSL) ile yapılandırılan Internet Information Services (IIS) altında barındırılır. Hizmet, istemcilerin sunucu kimliğini doğrulamasına izin vermek için bir SSL (X. 509.440) sertifikası ile yapılandırılır. İstemci Ayrıca hizmetin istemci kimliğini doğrulamasına izin veren bir X. 509.440 sertifikası ile yapılandırılır. Sunucu sertifikası istemci tarafından güvenilir olmalıdır ve istemcinin sertifikasına sunucu tarafından güvenilmelidir. Hizmetin ve istemcinin her birinin kimliğini nasıl doğrulayadığına ilişkin gerçek bir mekanizması, bu konunun kapsamının dışındadır. Daha fazla bilgi için bkz. [Vikipde dijital imza](https://go.microsoft.com/fwlink/?LinkId=253157).  
  
 Bu senaryo, aşağıdaki diyagramda gösterildiği gibi bir istek/yanıt iletisi deseninin bir listesini uygular.  
  
 ![Sertifikaları kullanarak güvenli aktarım](../../../../docs/framework/wcf/feature-details/media/8f7b8968-899f-4538-a9e8-0eaa872a291c.gif "8f7b8968-899F-4538-a9e8-0eaa872a291c")  
  
 Hizmeti olan bir sertifika kullanma hakkında daha fazla bilgi için bkz. [sertifikalarla çalışma](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) ve [nasıl yapılır: SSL sertifikası](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)Ile bir bağlantı noktası yapılandırın. Aşağıdaki tabloda senaryonun çeşitli özellikleri açıklanmaktadır.  
  
|Özellik|Açıklama|  
|--------------------|-----------------|  
|Güvenlik modu|Aktarım|  
|Birlikte Çalışabilirlik|Mevcut Web hizmeti istemcileri ve hizmetleriyle.|  
|Kimlik doğrulaması (sunucu)<br /><br /> Kimlik doğrulaması (Istemci)|Evet (bir SSL sertifikası kullanarak)<br /><br /> Evet (bir X. 509.440 sertifikası kullanarak)|  
|Veri bütünlüğü|Evet|  
|Veri gizliliği|Evet|  
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

- [Güvenliğe Genel Bakış](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [Windows Server App Fabric için güvenlik modeli](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
