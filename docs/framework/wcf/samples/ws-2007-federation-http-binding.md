---
title: WS 2007 Federasyon HTTP Bağlama
ms.date: 03/30/2017
ms.assetid: 91c1b477-a96e-4bf5-9330-5e9312113371
ms.openlocfilehash: 550a88552658864e3eedb70463e676ad6f9a2511
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59769534"
---
# <a name="ws-2007-federation-http-binding"></a>WS 2007 Federasyon HTTP Bağlama
Bu örnek, kullanımını gösterir. <xref:System.ServiceModel.WS2007FederationHttpBinding>, WS-Güven belirtimini destek sürümünün 1.3 Federasyon senaryolarında oluşturmak için kullanabileceğiniz bağlama standart.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
 Örnek bir konsol tabanlı istemci programını (Client.exe), bir konsol tabanlı güvenlik belirteci hizmeti program (Securitytokenservice.exe) ve konsol tabanlı hizmet programı (Service.exe) oluşur. Hizmet istek/yanıt iletişim deseni tanımlayan bir sözleşme uygular. Anlaşma tarafından tanımlanan `ICalculator` matematik işlemlerinden sunan arabirimi (`Add`, `Subtract`, `Multiply`, ve `Divide`). İstemci güvenlik belirteci hizmeti (STS) gelen bir güvenlik belirteci alır ve hizmet verilen matematik işlemi için zaman uyumlu istekleri yapar. Hizmet ardından sonucu, yanıt. İstemci etkinliği konsol penceresinde görünür.  
  
 Örnek yapar `ICalculator` sözleşme aracılığıyla kullanılabilir `ws2007FederationHttpBinding` öğesi. Bu bağlamanın istemcide yapılandırma aşağıdaki kodda gösterilmiştir.  
  
```xml  
<bindings>  
  <ws2007FederationHttpBinding>  
    <binding name="ServiceFed" >  
      <security mode ="Message">  
        <message issuedKeyType ="SymmetricKey"  
                 issuedTokenType ="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1" >  
          <!-- Endpoint address and binding for Security Token Service -->  
          <issuer address ="http://localhost:8000/sts/windows"   
                  binding ="ws2007HttpBinding" />                
        </message>  
      </security>  
    </binding>  
  </ws2007FederationHttpBinding>  
</bindings>  
```  
  
 Üzerinde [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md), `security` hangi güvenlik modunda kullanılması gereken bir değer belirtir. Bu örnekte `message` güvenlik kullanılır, neden olduğu [ \<ileti >](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) içinde belirtilen [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md). [ \<Veren >](../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md) öğe içinde [ \<ileti >](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) STS için istemciye bir güvenlik belirteci verir ve böylece istemci için bağlamasını ve adresini belirtir. kimlik doğrulaması `ICalculator` hizmeti.  
  
 Bu bağlamanın hizmet yapılandırma aşağıdaki kodda gösterilmiştir.  
  
```xml  
<bindings>  
  <ws2007FederationHttpBinding>  
    <binding name="ServiceFed" >  
      <security mode ="Message">  
        <message issuedKeyType ="SymmetricKey"  
                 issuedTokenType ="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1" >  
          <!-- Metadata address for Security Token Service -->  
          <issuerMetadata address ="http://localhost:8000/sts/mex" >  
            <identity>  
              <certificateReference storeLocation ="CurrentUser"   
                                    storeName="TrustedPeople"   
                                    x509FindType ="FindBySubjectDistinguishedName"   
                                    findValue ="CN=STS" />  
            </identity>  
          </issuerMetadata>  
        </message>  
      </security>  
    </binding>  
  </ws2007FederationHttpBinding>  
</bindings>  
```  
  
 Üzerinde [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md), `security` hangi güvenlik modunda kullanılması gereken bir değer belirtir. Bu örnekte `message` güvenlik kullanılır, neden olduğu [ \<ileti >](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) içinde belirtilen [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md). [ \<İssuedtokenparameters >](../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md) öğesinin `ws2007FederationHttpBinding` içinde [ \<ileti >](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) almak için kullanılan bir uç nokta için kimlik ve adresini belirtir STS meta verileri.  
  
 Hizmet davranışı, aşağıdaki kodda gösterilir.  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name ="ServiceBehaviour" >  
      <serviceDebug includeExceptionDetailInFaults ="true"/>  
      <serviceMetadata httpGetEnabled ="true"/>  
      <serviceCredentials>  
        <issuedTokenAuthentication>  
          <knownCertificates>  
            <add storeLocation ="LocalMachine"  
                 storeName="TrustedPeople"  
                 x509FindType="FindBySubjectDistinguishedName"  
                 findValue="CN=STS" />  
          </knownCertificates>  
        </issuedTokenAuthentication>  
        <serviceCertificate storeLocation ="LocalMachine"  
                            storeName ="My"  
                            x509FindType ="FindBySubjectDistinguishedName"  
                            findValue ="CN=localhost"/>  
      </serviceCredentials>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 [ \<ServiceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)> Hizmet istemcileri kimlik doğrulaması sırasında sunmak veren belirteçleri kısıtlamaları belirlemenizi sağlar. Bu yapılandırma, belirteçleri CN konu adı olan bir sertifika tarafından imzalanmış belirtir = STS hizmeti tarafından kabul edilir.  
  
 STS kullanımınıza tek bir uç nokta standardını kullanarak <xref:System.ServiceModel.WS2007HttpBinding>. Belirteçler için istemcilerden hizmet isteklerine yanıt verir. İstemci bir Windows hesabı kullanarak kimlik doğrulaması gerekiyorsa, hizmeti bir talep olarak istemcinin kullanıcı adını içeren bir belirteç verir. Belirteç, STS işaretleri CN ile ilişkili özel anahtarı kullanarak belirteci oluşturma işleminin parçası olarak STS sertifikasını =. Ayrıca, bir simetrik anahtar oluşturur ve CN ile ilişkili bir ortak anahtar kullanarak şifreler = localhost sertifikasına. Belirteci istemciye göndermeden, STS, simetrik anahtarı da döndürür. İstemci için verilen belirtecin sunar `ICalculator` hizmet ve bunu simetrik anahtarı bu anahtarla ileti açarak bilen kanıtlar.  
  
 Örneği çalıştırdığında, güvenlik belirteci isteği STS konsol penceresinde gösterilir. İşlem istekleri ve yanıtları istemci ve hizmet Konsolu pencerelerinde görüntülenir. Uygulamayı kapatın, herhangi bir windows konsol ENTER tuşuna basın.  

```
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714
Press <ENTER> to terminate client.
```

 Bu örnekle dahil Setup.bat dosyasının, STS'ye ve sunucu şirket içinde barındırılan bir uygulamayı çalıştırmak için ilgili sertifikalarla yapılandırmanıza olanak sağlar. Toplu iş dosyasını iki sertifikalar LocalMachine/TrustedPeople sertifika deposunda oluşturur. İlk sertifikayı sahip bir konu adı CN = STS ve STS tarafından istemcinin verdiği güvenlik belirteçleri imzalamak için kullanılır. İkinci sertifikayı sahip bir konu adı CN = localhost ve STS tarafından bir anahtar hizmet şifresini çözebilir bir şekilde şifrelemek için kullanılır.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1. Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Yönetici ayrıcalıklarıyla Visual Studio için geliştirici komut istemi açın ve gerekli sertifikaları oluşturmak için Setup.bat dosyasını çalıştırın.  
  
 Windows SDK'sı ile dağıtılmış Certmgr.exe ve Makecert.exe, bu toplu iş dosyası kullanır. Ancak, bu araçları bulmak betik etkinleştirmek için Visual Studio komut istemi içinde gelen Setup.bat çalıştırmanız gerekir.  
  
1. Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2. Tek veya çoklu bilgisayar yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md). Kullanıyorsanız [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)]SecurityTokenService.exe ile yükseltilmiş ayrıcalıklar ve Service.exe, Client.exe, çalıştırmanız gerekir (dosyaları sağ tıklayın ve ardından **yönetici olarak çalıştır**).  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\WS2007FederationHttp`  
