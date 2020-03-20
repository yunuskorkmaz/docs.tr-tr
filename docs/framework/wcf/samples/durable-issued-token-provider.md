---
title: Dayanıklı Verilen Belirteç Sağlayıcısı
ms.date: 03/30/2017
ms.assetid: 76fb27f5-8787-4b6a-bf4c-99b4be1d2e8b
ms.openlocfilehash: 08c6837f45ba1c422cdc3df2c884aa81b50a7f2b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144753"
---
# <a name="durable-issued-token-provider"></a>Dayanıklı Verilen Belirteç Sağlayıcısı
Bu örnek, özel bir istemci tarafından verilen belirteç sağlayıcısının nasıl uygulanacağını gösterir.  
  
## <a name="discussion"></a>Tartışma  
 Windows Communication Foundation'daki (WCF) bir belirteç sağlayıcısı, güvenlik altyapısına kimlik bilgileri sağlamak için kullanılır. Genel olarak belirteç sağlayıcısı, güvenlik altyapısının iletiyi güvence altına alabilmesi için hedefi inceler ve uygun kimlik bilgilerini sorunları sağlar. Bir CardSpace belirteç sağlayıcısı ile WCF gemi. Özel belirteç sağlayıcıları aşağıdaki durumlarda yararlıdır:  
  
- Yerleşik belirteç sağlayıcısının çalışamadığı bir kimlik deponuz varsa.  
  
- Kullanıcının ayrıntıları wcf istemcisi kimlik bilgilerini kullandığı noktaya kadar dönüştürmek için kendi özel mekanizmasağlamak istiyorsanız.  
  
- Özel bir belirteç oluşturuyorsanız.  
  
 Bu örnek, bir Güvenlik Belirteç Hizmeti (STS) tarafından verilen belirteçleri önbelleğe alan özel bir belirteç sağlayıcısının nasıl oluşturulabildiğini gösterir.  
  
 Özetlemek gerekirse, bu örnek aşağıdakileri gösterir:  
  
- Bir istemcinin özel bir belirteç sağlayıcısıyla nasıl yapılandırılabildiği.  
  
- Verilen belirteçler nasıl önbelleğe alınabilir ve WCF istemcisine sağlanabilir.  
  
- Sunucunun X.509 sertifikasını kullanarak sunucunun istemci tarafından nasıl doğrulanır.  
  
 Bu örnek bir istemci konsol programı (Client.exe), bir güvenlik belirteç hizmet konsolu programı (Securitytokenservice.exe) ve bir hizmet konsolu programı (Service.exe) oluşur. Hizmet, istek-yanıt iletişim modelini tanımlayan bir sözleşme uygular. Sözleşme, matematik işlemlerini `ICalculator` (ekleme, çıkarma, çoğaltma ve bölme) ortaya çıkaran arabirim tarafından tanımlanır. İstemci, Güvenlik Belirteci Hizmeti'nden (STS) bir güvenlik belirteci alır ve belirli bir matematik işlemi için hizmete eşzamanlı isteklerde bulunduruyor ve sonuçla birlikte hizmet yanıtları veriyor. İstemci etkinliği konsol penceresinde görünür.  
  
> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.  
  
 Bu örnek [ \<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)kullanarak ICalculator sözleşme ortaya çıkarır. İstemci için bu bağlama yapılandırması aşağıdaki kodda gösterilir.  
  
```xml  
<bindings>
  <wsFederationHttpBinding>
    <binding name="ServiceFed">
      <security mode="Message">
        <message issuedKeyType="SymmetricKey"
                 issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">
          <issuer address="http://localhost:8000/sts/windows"
                  binding="wsHttpBinding" />
        </message>
      </security>
    </binding>
  </wsFederationHttpBinding>
</bindings>  
```  
  
 Öğe `security` üzerinde , `mode` değer yapılandırmahangi güvenlik modu kullanılmalıdır. `wsFederationHttpBinding` Bu örnekte, iletiler güvenlik kullanılıyor, bu `message` nedenle `wsFederationHttpBinding` öğenin `security` öğesi `wsFederationHttpBinding`içinde belirtilir. İç `issuer` öğenin `wsFederationHttpBinding` `message` öğesi, `wsFederationHttpBinding` istemcinin Hesap Makinesi hizmetine kimlik doğrulaması yapabilmesi için istemciye bir güvenlik belirteci veren Güvenlik Belirteci Hizmeti için adresi ve bağlamayı belirtir.  
  
 Hizmet için bu bağlama yapılandırması aşağıdaki kodda gösterilir.  
  
```xml  
<bindings>
  <wsFederationHttpBinding>
    <binding name="ServiceFed">
      <security mode="Message">
        <message issuedKeyType="SymmetricKey"
                 issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">
          <issuerMetadata address="http://localhost:8000/sts/mex">
            <identity>
              <certificateReference storeLocation="CurrentUser"
                                    storeName="TrustedPeople"
                                    x509FindType="FindBySubjectDistinguishedName"
                                    findValue="CN=STS" />
            </identity>
          </issuerMetadata>
        </message>
      </security>
    </binding>
  </wsFederationHttpBinding>
</bindings>  
```  
  
 Öğe `security` üzerinde , `mode` değer yapılandırmahangi güvenlik modu kullanılmalıdır. `wsFederationHttpBinding` Bu örnekte, iletiler güvenlik kullanılıyor, bu `message` nedenle `wsFederationHttpBinding` öğenin `security` öğesi `wsFederationHttpBinding`içinde belirtilir. İç `issuerMetadata` `wsFederationHttpBinding` öğenin `message` öğesi, `wsFederationHttpBinding` Güvenlik Belirteci Hizmeti için meta verileri almak için kullanılabilecek bir bitiş noktası için adres ve kimlik belirtir.  
  
 Hizmetin davranışı aşağıdaki kodda gösterilir.  
  
```xml  
<behavior name="ServiceBehavior">
  <serviceDebug includeExceptionDetailInFaults="true" />
  <serviceMetadata httpGetEnabled="true" />
  <serviceCredentials>
    <issuedTokenAuthentication>
      <knownCertificates>
        <add storeLocation="LocalMachine"
              storeName="TrustedPeople"
              x509FindType="FindBySubjectDistinguishedName"
              findValue="CN=STS" />
      </knownCertificates>
    </issuedTokenAuthentication>
    <serviceCertificate storeLocation="LocalMachine"
                        storeName="My"
                        x509FindType="FindBySubjectDistinguishedName"
                        findValue="CN=localhost" />
  </serviceCredentials>
</behavior>  
```  
  
 Öğenin `issuedTokenAuthentication` `serviceCredentials` içindeki öğe, hizmetin müşterilerin kimlik doğrulama sırasında sunmasına izin verdiği belirteçler üzerindeki kısıtlamaları belirtmesine olanak tanır. Bu yapılandırma, Özne Adı CN=STS olan bir sertifika tarafından imzalanan belirteçlerin hizmet tarafından kabul edildiğini belirtir.  
  
 Güvenlik Belirteç Hizmeti standart wsHttpBinding kullanarak tek bir uç noktası ortaya çıkarır. Güvenlik Belirteç Hizmeti, istemcilerin belirteçleri isteğine yanıt verir ve istemcinin bir Windows hesabı kullanarak kimlik doğrulaması vermesi koşuluyla, verilen belirteçte talep olarak istemcinin kullanıcı adını içeren bir belirteç verir. Belirteci oluşturmanın bir parçası olarak, Güvenlik Belirteci Hizmeti CN=STS sertifikasıile ilişkili özel anahtarı kullanarak belirteci imzalar. Buna ek olarak, simetrik bir anahtar oluşturur ve CN=localhost sertifikası ile ilişkili ortak anahtarı kullanarak şifreler. Belirteci istemciye döndürürken, Güvenlik Belirteci Hizmeti de simetrik anahtarı döndürür. İstemci, verilen belirteci Hesap Makinesi hizmetine sunar ve iletiyi bu anahtarla imzalayarak simetrik anahtarı bildiğini kanıtlar.  
  
## <a name="custom-client-credentials-and-token-provider"></a>Özel İstemci Kimlik Bilgileri ve Belirteç Sağlayıcısı  
 Aşağıdaki adımlar, verilen belirteçleri önbelleğe alan ve WCF ile tümleştiren özel bir belirteç sağlayıcısının nasıl geliştirilebildiğini gösterir: güvenlik.  
  
### <a name="to-develop-a-custom-token-provider"></a>Özel bir belirteç sağlayıcısı geliştirmek için  
  
1. Özel bir belirteç sağlayıcısı yazın.  
  
     Örnek, önbellekten alınan bir güvenlik belirteci döndüren özel bir belirteç sağlayıcısı uygular.  
  
     Bu görevi gerçekleştirmek için, özel belirteç <xref:System.IdentityModel.Selectors.SecurityTokenProvider> sağlayıcısı sınıfı <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> türeter ve yöntemi geçersiz kılar. Bu yöntem önbellekten bir belirteç almaya çalışır veya önbellekte bir belirteç bulunamıyorsa, temel sağlayıcıdan bir belirteç alır ve sonra bu belirteç önbelleğe alır. Her iki durumda da `SecurityToken`yöntem bir .  
  
    ```csharp  
    protected override SecurityToken GetTokenCore(TimeSpan timeout)  
    {  
      GenericXmlSecurityToken token;  
      if (!this.cache.TryGetToken(target, issuer, out token))  
      {  
        token = (GenericXmlSecurityToken) this.innerTokenProvider.GetToken(timeout);  
        this.cache.AddToken(token, target, issuer);  
      }  
      return token;  
    }  
    ```  
  
2. Özel güvenlik belirteç yöneticisi yazın.  
  
     Yöntemde <xref:System.IdentityModel.Selectors.SecurityTokenManager> `CreateSecurityTokenProvider` ona geçirilen <xref:System.IdentityModel.Selectors.SecurityTokenProvider> belirli <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> bir a oluşturmak için kullanılır. Güvenlik belirteç yöneticisi, belirteç kimlik doğrulayıcıları ve belirteç serileştiricileri oluşturmak için de kullanılır, ancak bunlar bu örnek tarafından karşılanmaz. Bu örnekte, özel güvenlik belirteç <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> yöneticisi sınıftan `CreateSecurityTokenProvider` devralır ve geçirilen belirteç gereksinimleri verilmiş bir belirteç istendiğini gösterdiğinde özel belirteç sağlayıcısını döndürmek için yöntemi geçersiz kılar.  
  
    ```csharp
    class DurableIssuedTokenClientCredentialsTokenManager :  
     ClientCredentialsSecurityTokenManager  
    {  
      IssuedTokenCache cache;  
  
      public DurableIssuedTokenClientCredentialsTokenManager ( DurableIssuedTokenClientCredentials creds ): base(creds)  
      {  
        this.cache = creds.IssuedTokenCache;  
      }  
  
      public override SecurityTokenProvider CreateSecurityTokenProvider ( SecurityTokenRequirement tokenRequirement )  
      {  
        if (IsIssuedSecurityTokenRequirement(tokenRequirement))  
        {  
          return new DurableIssuedSecurityTokenProvider ((IssuedSecurityTokenProvider)base.CreateSecurityTokenProvider( tokenRequirement), this.cache);  
        }  
        else
        {  
          return base.CreateSecurityTokenProvider(tokenRequirement);  
        }  
      }  
    }  
    ```  
  
3. Özel bir istemci kimlik bilgisi yazın.  
  
     İstemci kimlik bilgileri sınıfı, istemci proxy için yapılandırılan kimlik bilgilerini temsil etmek için kullanılır ve belirteç kimlik doğrulayıcıları, belirteç sağlayıcıları ve belirteç serileştiricileri elde etmek için kullanılan güvenlik belirteci yöneticisioluşturur.  
  
    ```csharp
    public class DurableIssuedTokenClientCredentials : ClientCredentials  
    {  
      IssuedTokenCache cache;  
  
      public DurableIssuedTokenClientCredentials() : base()  
      {  
      }  
  
      DurableIssuedTokenClientCredentials ( DurableIssuedTokenClientCredentials other) : base(other)  
      {  
        this.cache = other.cache;  
      }  
  
      public IssuedTokenCache IssuedTokenCache  
      {  
        get  
        {  
          return this.cache;  
        }  
        set  
        {  
          this.cache = value;  
        }  
      }  
  
      protected override ClientCredentials CloneCore()  
      {  
        return new DurableIssuedTokenClientCredentials(this);  
      }  
  
      public override SecurityTokenManager CreateSecurityTokenManager()  
      {  
        return new DurableIssuedTokenClientCredentialsTokenManager ((DurableIssuedTokenClientCredentials)this.Clone());  
      }  
    }  
    ```  
  
4. Belirteç önbelleğini uygulayın. Örnek uygulama, belirli bir belirteç önbelleğinin tüketicilerinin önbellekle etkileşimde bulunduğu soyut bir taban sınıf kullanır.  
  
    ```csharp
    public abstract class IssuedTokenCache  
    {  
      public abstract void AddToken ( GenericXmlSecurityToken token, EndpointAddress target, EndpointAddress issuer);  
      public abstract bool TryGetToken(EndpointAddress target, EndpointAddress issuer, out GenericXmlSecurityToken cachedToken);  
    }  
    // Configure the client to use the custom client credential.  
    ```  
  
     İstemcinin özel istemci kimlik bilgilerini kullanması için, örnek varsayılan istemci kimlik bilgilerini siler ve yeni istemci kimlik bilgilerini sağlar.  
  
    ```csharp
    clientFactory.Endpoint.Behaviors.Remove<ClientCredentials>();  
    DurableIssuedTokenClientCredentials durableCreds = new DurableIssuedTokenClientCredentials();  
    durableCreds.IssuedTokenCache = cache;  
    durableCreds.ServiceCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.PeerOrChainTrust;  
    clientFactory.Endpoint.Behaviors.Add(durableCreds);  
    ```  
  
## <a name="running-the-sample"></a>Örneği çalıştırma  
 Örneği çalıştırmak için aşağıdaki yönergeleri izleyin. Örneği çalıştırdığınızda, güvenlik belirteci isteği Güvenlik Belirteci Hizmeti konsolpenceresinde gösterilir. İşlem istekleri ve yanıtları istemci ve servis konsolu pencerelerinde görüntülenir. Uygulamayı kapatmak için konsol pencerelerinden herhangi birinde ENTER tuşuna basın.  
  
## <a name="the-setupcmd-batch-file"></a>Setup.cmd Toplu Dosya  
 Bu örnekte yer alan Setup.cmd toplu iş dosyası, sunucu ve güvenlik belirteci hizmetini kendi barındırılan bir uygulamayı çalıştırmak için ilgili sertifikalarla yapılandırmanıza olanak tanır. Toplu iş dosyası, CurrentUser/TrustedPeople sertifika deposunda iki sertifika oluşturur. İlk sertifika CN=STS özne adı vardır ve güvenlik belirteçleri tarafından istemciye verdiği güvenlik belirteçlerini imzalamak için kullanılır. İkinci sertifika CN=localhost özne adı vardır ve hizmetin şifresini çözebilmek için bir sırrı şifrelemek için Güvenlik Belirteci Hizmeti tarafından kullanılır.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Gerekli sertifikaları oluşturmak için Setup.cmd dosyasını çalıştırın.  
  
2. Çözümü oluşturmak için, Windows [Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin. Çözümdeki tüm projelerin (Paylaşılan, RSTRSTR, Service, SecurityTokenService ve Client) inşa edildiklerinin sağlanması.  
  
3. Service.exe ve SecurityTokenService.exe'nin her ikisinin de yönetici ayrıcalıklarıyla birlikte çalışmasını sağlayın.  
  
4. Client.exe'yi çalıştırın.  
  
### <a name="to-clean-up-after-the-sample"></a>Örnekten sonra temizlemek için  
  
1. Örneği çalıştırmayı bitirdikten sonra örnekler klasöründe Cleanup.cmd'yi çalıştırın.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Security\DurableIssuedTokenProvider`  
