---
title: WS 2007 Federasyon HTTP Bağlama
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 91c1b477-a96e-4bf5-9330-5e9312113371
caps.latest.revision: 23
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b7126e4c0c293bfbf78cecf97cc13ea91e6c0c62
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="ws-2007-federation-http-binding"></a>WS 2007 Federasyon HTTP Bağlama
Bu örnek kullanımını gösteren <xref:System.ServiceModel.WS2007FederationHttpBinding>, WS-Trust belirtimine destek sürümünün 1.3 Federasyon senaryoları oluşturmak için kullanabileceğiniz bağlama standart.  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
 Örnek bir konsol tabanlı istemci programını (Client.exe), bir konsol tabanlı güvenlik belirteci hizmeti programı (Securitytokenservice.exe) ve konsol tabanlı hizmet programı (Service.exe) oluşur. Hizmet istek/yanıt iletişim deseni tanımlayan bir sözleşme uygular. Anlaşma tarafından tanımlanan `ICalculator` matematik işlemleri kullanıma sunan arabirim (`Add`, `Subtract`, `Multiply`, ve `Divide`). İstemci güvenlik belirteci hizmeti (STS) bir güvenlik belirteci alır ve hizmet verilen matematik işlemi için zaman uyumlu istekleri yapar. Hizmet ardından sonucu, yanıt. İstemci etkinliği konsol penceresinde görünür olur.  
  
 Örnek yapar `ICalculator` sözleşme kullanılabilir kullanarak `ws2007FederationHttpBinding` öğesi. Bu bağlama istemcide yapılandırmasını aşağıdaki kodda gösterilir.  
  
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
  
 Üzerinde [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md), `security` değeri belirten hangi güvenlik modunda kullanılmalıdır. Bu örnekte `message` güvenlik kullanılır, neden olduğu [ \<ileti >](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) içinde belirtilen [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md). [ \<Veren >](../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md) öğesi içinde [ \<ileti >](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) STS için istemciye bir güvenlik belirteci verir ve böylece istemci için bağlama ve adresini belirtir kimlik doğrulaması `ICalculator` hizmet.  
  
 Bu bağlama hizmetinin yapılandırmasını aşağıdaki kodda gösterilir.  
  
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
  
 Üzerinde [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md), `security` değeri belirten hangi güvenlik modunda kullanılmalıdır. Bu örnekte `message` güvenlik kullanılır, neden olduğu [ \<ileti >](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) içinde belirtilen [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md). [ \<İssuedtokenparameters >](../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md) öğesinin `ws2007FederationHttpBinding` içinde [ \<ileti >](../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) almak için kullanılan bir uç nokta için kimlik ve adresini belirtir STS meta veriler.  
  
 Hizmeti için davranış aşağıdaki kodda gösterilir.  
  
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
  
 [ \<İssuedTokenAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)> kimlik doğrulaması sırasında sunmak istemcileri veren belirteçleri kısıtlamaları belirtmek hizmet sağlar. Bu yapılandırma belirteçleri konu adı olan CN sertifika tarafından imzalanan belirtir = STS hizmeti tarafından kabul edilir.  
  
 STS kullanılabilir hale getirir tek bir uç nokta standart kullanarak <xref:System.ServiceModel.WS2007HttpBinding>. Hizmet belirteçleri istemcilerden gelen isteklere yanıt verir. Bir Windows hesabı kullanarak istemcinin kimliğinin, hizmeti bir talep olarak istemcinin kullanıcı adını içeren bir belirteç verir. STS işaretlerini belirtecin CN ile ilişkili özel anahtarı kullanarak belirteci oluşturma bir parçası olarak STS sertifikası =. Ayrıca, bir simetrik anahtar oluşturur ve CN ile ilişkilendirilmiş ortak anahtar kullanarak şifreler localhost sertifika =. Belirteç istemciye döndürmeden içinde STS, simetrik anahtar da döndürür. Verilen belirteç istemci sunar `ICalculator` hizmet ve bunu simetrik anahtar bu anahtarla ileti imzalayarak bilen kanıtlar.  
  
 Örneği çalıştırdığınızda, güvenlik belirteci isteği STS konsol penceresinde gösterilir. İşlem istekleri ve yanıtları istemci ve hizmet Konsolu pencerelerinde görüntülenir. Herhangi bir windows konsol uygulamasını kapatmak için ENTER tuşuna basın.  

```
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714
Press <ENTER> to terminate client.
```

 Bu örnekle dahil Setup.bat dosya sunucusu ve STS kendini barındıran bir uygulamayı çalıştırmak için ilgili sertifikalarla yapılandırmanıza olanak sağlar. Toplu iş dosyası LocalMachine/TrustedPeople sertifika deposunda iki sertifikaları oluşturur. İlk sertifika CN bir konu adına sahip STS = ve STS tarafından istemcinin verdiği güvenlik belirteçleri imzalamak için kullanılır. İkinci sertifikanın CN bir konu adına sahip localhost = ve STS tarafından hizmet şifresini çözebilir şekilde anahtarı şifrelemek için kullanılır.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Yönetici ayrıcalıklarına sahip bir Visual Studio komut istemi açın ve gerekli sertifikaları oluşturmak için Setup.bat dosyasını çalıştırın.  
  
 Bu toplu iş dosyası Windows SDK ile birlikte dağıtılmış Certmgr.exe ve Makecert.exe, kullanır. Ancak, bu araçları bulmak betik etkinleştirmek için Visual Studio komut istemi içinde Setup.bat gelen çalıştırmanız gerekir.  
  
1.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2.  Tek veya çapraz bilgisayar yapılandırmasında örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md). Kullanıyorsanız [!INCLUDE[windowsver](../../../../includes/windowsver-md.md)]Service.exe, Client.exe, çalıştırmak ve SecurityTokenService.exe ile yükseltilmiş ayrıcalıklar (dosyaları sağ tıklatın ve ardından **yönetici olarak çalıştır**).  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\WS2007FederationHttp`  
  
## <a name="see-also"></a>Ayrıca Bkz.
