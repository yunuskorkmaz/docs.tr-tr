---
title: WS 2007 Federasyon HTTP Bağlama
ms.date: 03/30/2017
ms.assetid: 91c1b477-a96e-4bf5-9330-5e9312113371
ms.openlocfilehash: bf61e64733859d96adf42fbacf08266eca1f5b45
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183179"
---
# <a name="ws-2007-federation-http-binding"></a>WS 2007 Federasyon HTTP Bağlama

Bu örnek, WS-Trust belirtiminin <xref:System.ServiceModel.WS2007FederationHttpBinding>sürüm 1.3'ü destekleyen federe senaryolar oluşturmak için kullanabileceğiniz standart bir bağlayıcının kullanımını göstermektedir.

> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.

Örnek bir konsol tabanlı istemci programı *(Client.exe),* konsol tabanlı bir güvenlik belirteç hizmet programı *(Securitytokenservice.exe)* ve konsol tabanlı bir hizmet programı *(Service.exe)* oluşur. Hizmet, istek/yanıt iletişimi deseni tanımlayan bir sözleşme uygular. Sözleşme, matematik işlemlerini `ICalculator` ortaya çıkaran arayüz tarafından`Add` `Subtract`tanımlanır `Multiply`( `Divide`, , , ve . İstemci, Güvenlik Belirteci Hizmeti'nden (STS) bir güvenlik belirteci alır ve belirli bir matematik işlemi için hizmete eşzamanlı istekte bulunmayı sağlar. Hizmet daha sonra sonucu yanıtlar. İstemci etkinliği konsol penceresinde görünür.

Örnek, öğeyi kullanarak `ICalculator` `ws2007FederationHttpBinding` sözleşmeyi kullanılabilir hale getirir. İstemci için bu bağlama yapılandırması aşağıdaki kodda gösterilir:

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

Güvenlik>, `security` değer hangi güvenlik modunun kullanılması gerektiğini belirtir. [ \< ](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md) Bu örnekte, güvenlik kullanılır, `message` bu nedenle [ \<ileti>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) [ \<güvenlik>](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md)içinde belirtilir. [ \<](../../configure-apps/file-schema/wcf/issuer.md) [İletinin \<](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) içindeki>öğesi>, istemcinin `ICalculator` hizmete kimlik doğrulaması yapabilmesi için istemciye güvenlik belirteci veren STS adresini ve bağlamayı belirtir.
  
Hizmet için bu bağlama yapılandırması aşağıdaki kodda gösterilir:

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

Güvenlik>, `security` değer hangi güvenlik modunun kullanılması gerektiğini belirtir. [ \< ](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md) Bu örnekte, güvenlik kullanılır, `message` bu nedenle [ \<ileti>](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) [ \<güvenlik>](../../configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md)içinde belirtilir. İleti [ \<](../../configure-apps/file-schema/wcf/issuermetadata.md) nin `ws2007FederationHttpBinding` [ \<](../../configure-apps/file-schema/wcf/message-element-of-ws2007federationhttpbinding.md) içindeki meta veri>öğesi>, STS için meta verileri almak için kullanılabilecek bir bitiş noktasının adresini ve kimliğini belirtir.

Hizmetin davranışı aşağıdaki kodda gösterilir:

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
  
[>>verilen TokenAuthentication, hizmetin istemcilerin kimlik doğrulama sırasında sunmasına izin verdiği belirteçler üzerindeki kısıtlamaları belirtmesine olanak tanır. \<](../../configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) Bu yapılandırma, konu adı CN=STS olan bir sertifika tarafından imzalanan belirteçlerin hizmet tarafından kabul edildiğini belirtir.

STS, standardı <xref:System.ServiceModel.WS2007HttpBinding>kullanarak tek bir uç noktayı kullanılabilir hale getirir. Hizmet, istemcilerin belirteçisteklerine yanıt verir. İstemci bir Windows hesabı kullanılarak kimlik doğrulaması yapılırsa, hizmet talep olarak istemcinin kullanıcı adını içeren bir belirteç verir. Belirteci oluşturmanın bir parçası olarak, STS belirteci CN=STS sertifikası ile ilişkili özel anahtarı kullanarak imzalar. Buna ek olarak, simetrik bir anahtar oluşturur ve CN=localhost sertifikası ile ilişkili ortak anahtarı kullanarak şifreler. Belirteci istemciye döndürürken, STS simetrik anahtarı da döndürür. İstemci verilen belirteci `ICalculator` hizmete sunar ve iletiyi bu anahtarla imzalayarak simetrik anahtarı bildiğini kanıtlar.

Örneği çalıştırdığınızda, güvenlik belirteci isteği STS konsol penceresinde gösterilir. İşlemin istek ve yanıtları istemci ve servis konsolu pencerelerinde görüntülenir. Uygulamayı kapatmak için konsol pencerelerinden herhangi birinde ENTER tuşuna basın.

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714
Press <ENTER> to terminate client.
```

Bu örnekle birlikte bulunan *Setup.bat* dosyası, sunucuyu ve STS'yi kendi barındırılan bir uygulamayı çalıştırmak için ilgili sertifikalarla yapılandırmanıza olanak tanır. Toplu iş dosyası, LocalMachine/TrustedPeople sertifika deposunda iki sertifika oluşturur. İlk sertifika CN=STS özne adı vardır ve STS tarafından istemciye verdiği güvenlik belirteçlerini imzalamak için kullanılır. İkinci sertifika CN=localhost özne adı vardır ve STS tarafından bir anahtarı hizmetin şifresini çözebileceği şekilde şifrelemek için kullanılır.

## <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için
  
1. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.

2. Yönetici ayrıcalıklarına sahip Visual Studio için bir Geliştirici Komut Komut Ustem'i açın ve gerekli sertifikaları oluşturmak için Setup.bat dosyasını çalıştırın.

 Bu toplu işlem dosyası, Windows SDK ile dağıtılan *Certmgr.exe* ve Makecert.exe'yi kullanır. Ancak, komut dosyasının bu araçları bulmasını sağlamak için Visual Studio komut istemi içinden *Setup.bat* çalıştırmalısınız.

1. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](building-the-samples.md)yönergeleri izleyin.

2. Örneği tek veya bilgisayar lar arası yapılandırmada çalıştırmak [için, Windows Communication Foundation Samples'ı çalıştıran](running-the-samples.md)yönergeleri izleyin. Windows Vista kullanıyorsanız, *Service.exe,* *Client.exe*ve *SecurityTokenService.exe'yi* yüksek ayrıcalıklarla çalıştırmanız gerekir (dosyaları sağ tıklatın ve ardından **yönetici olarak Çalıştır'ı**tıklatın).

> [!IMPORTANT]
> Örnekler bilgisayarınıza zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin:
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer alır:
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\WS2007FederationHttp`
