---
title: <message> / <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: 9def5a35-475d-40d6-b716-ccdbd93863c7
ms.openlocfilehash: b37d6b1bd8f5372c230acbc2ada299415b2e40b3
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204859"
---
# <a name="message-of-nethttpbinding"></a>\<message> / \<netHttpBinding>

İleti düzeyi güvenliği için ayarları tanımlar [\<netHttpBinding>](nethttpbinding.md) .  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
         clientCredentialType="UserName/Certificate" />
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  

 Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|algorithmSuite|İleti şifrelemesini ve anahtar sarması algoritmalarını ayarlar. Bu öznitelik, <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> algoritmaları ve anahtar boyutlarını belirten türüdür. Bu algoritmalar güvenlik Ilkesi dili (WS-SecurityPolicy) belirtiminde belirtilen olanlarla eşlenir.<br /><br /> Varsayılan değer: `Basic256`.|  
|clientCredentialType|İleti tabanlı güvenlik kullanarak istemci kimlik doğrulaması gerçekleştirirken kullanılacak kimlik bilgisinin türünü belirtir. Varsayılan değer: `UserName`.|  
  
## <a name="clientcredentialtype-attribute"></a>clientCredentialType özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|UserName|-İstemcinin bir Kullanıcı adı kimlik bilgisiyle sunucuda kimlik doğrulamasını gerektirir. Bu kimlik bilgisinin <> öğesi kullanılarak belirtilmesi gerekir `clientCredentials` .<br />-WCF parola özetinin gönderilmesini veya parolaları kullanarak anahtar türemesini veya ileti güvenliği için bu tuşları kullanmayı desteklemez. Bu nedenle, WCF, Kullanıcı adı kimlik bilgileri kullanılırken taşımanın güvenli olmasını zorlar. İçin, `basicHttpBinding` bunun için BIR SSL kanalı ayarlanması gerekir.|  
|Sertifika|İstemcinin bir sertifika kullanarak sunucuda kimlik doğrulamasını gerektirir. Bu durumda istemci kimlik bilgisinin <`clientCredentials`> ve <> kullanılarak belirtilmesi gerekir `clientCertificate` . Ayrıca, ileti güvenliği modunu kullanırken, istemcinin hizmet sertifikasıyla sağlanması gerekir. Bu durumda hizmet kimlik bilgilerinin <xref:System.ServiceModel.Description.ClientCredentials> sınıf veya `ClientCredentials` davranış öğesi kullanılarak belirtilmesi ve serviceCredentials öğesi kullanılarak hizmet sertifikası belirtilmesi gerekir \<serviceCertificate> .|  
  
### <a name="child-elements"></a>Alt Öğeler  

 Yok  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|<`security` <> öğesi `netHttpBinding`>|<> öğesi için güvenlik yeteneklerini tanımlar `netHttpBinding` .|  
  
## <a name="example"></a>Örnek  

 Bu örnek, basicHttpBinding ve ileti güvenliği kullanan bir uygulamanın nasıl uygulanacağını gösterir. Bir hizmet için aşağıdaki yapılandırma örneğinde, uç nokta tanımı basicHttpBinding öğesini belirtir ve adlı bir bağlama yapılandırmasına başvurur `Binding1` . Hizmetin istemcinin kimliğini doğrulamak için kullandığı sertifika, `behaviors` öğesinin altındaki yapılandırma dosyasının bölümünde ayarlanır `serviceCredentials` . İstemcinin hizmete kendi kimliğini doğrulamak için kullandığı sertifika için geçerli olan doğrulama modu, `behaviors` öğesinin altındaki bölümünde de ayarlanır `clientCertificate` .  
  
 Aynı bağlama ve güvenlik ayrıntıları istemci yapılandırma dosyasında belirtilmiştir.  
  
```xml  
<system.serviceModel>
  <services>
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <host>
        <baseAddresses>
          <add baseAddress="http://localhost:8000/ServiceModelSamples/service" />
        </baseAddresses>
      </host>
      <!-- this endpoint is exposed at the base address provided by host: http://localhost:8000/ServiceModelSamples/service  -->
      <endpoint address=""
                binding="basicHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
      <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->
      <endpoint address="mex"
                binding="mexHttpBinding"
                contract="IMetadataExchange" />
    </service>
  </services>
  <bindings>
    <basicHttpBinding>
      <!-- This configuration defines the SecurityMode as Message and
           the clientCredentialType as Certificate. -->
      <binding name="Binding1" >
        <security mode = "Message">
          <message clientCredentialType="Certificate" />
        </security>
      </binding>
    </basicHttpBinding>
  </bindings>
  <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
  <behaviors>
    <serviceBehaviors>
      <behavior name="CalculatorServiceBehavior">
        <serviceMetadata httpGetEnabled="True" />
        <serviceDebug includeExceptionDetailInFaults="False" />
        <!-- The serviceCredentials behavior allows one to define a service certificate.
             A service certificate is used by a client to authenticate the service and provide message protection.
             This configuration references the "localhost" certificate installed during the setup instructions. -->
        <serviceCredentials>
          <serviceCertificate findValue="localhost"
                              storeLocation="LocalMachine"
                              storeName="My"
                              x509FindType="FindBySubjectName" />
          <clientCertificate>
            <!-- Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate
                 is in the user's Trusted People store, then it will be trusted without performing a
                 validation of the certificate's issuer chain. This setting is used here for convenience so that the
                 sample can be run without having to have certificates issued by a certification authority (CA).
                 This setting is less secure than the default, ChainTrust. The security implications of this
                 setting should be carefully considered before using PeerOrChainTrust in production code. -->
            <authentication certificateValidationMode="PeerOrChainTrust" />
          </clientCertificate>
        </serviceCredentials>
      </behavior>
    </serviceBehaviors>
  </behaviors>
</system.serviceModel>
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../wcf/feature-details/securing-services-and-clients.md)
- [Bağlamalar](../../../wcf/bindings.md)
- [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
