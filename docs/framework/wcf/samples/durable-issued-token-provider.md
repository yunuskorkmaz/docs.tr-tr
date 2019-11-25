---
title: Dayanıklı Verilen Belirteç Sağlayıcısı
ms.date: 03/30/2017
ms.assetid: 76fb27f5-8787-4b6a-bf4c-99b4be1d2e8b
ms.openlocfilehash: 52c4e99f8b2a834d7200c2d2c2383fbdb21bdd1a
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73978334"
---
# <a name="durable-issued-token-provider"></a>Dayanıklı Verilen Belirteç Sağlayıcısı
Bu örnek, özel bir istemci tarafından verilen belirteç sağlayıcısının nasıl uygulanacağını gösterir.  
  
## <a name="discussion"></a>Tartışma  
 Güvenlik altyapısına kimlik bilgilerini sağlamak için Windows Communication Foundation (WCF) içindeki bir belirteç sağlayıcısı kullanılır. Genel içindeki belirteç sağlayıcısı hedefi inceler ve güvenlik altyapısının iletiyi güvenli hale getirmek için uygun kimlik bilgilerini verir. WCF, bir CardSpace belirteç sağlayıcısıyla birlikte gelir. Özel belirteç sağlayıcıları aşağıdaki durumlarda faydalıdır:  
  
- Yerleşik belirteç sağlayıcısının birlikte çalışamamasının bir kimlik bilgisi deposu varsa.  
  
- Kullanıcı, WCF istemcisi kimlik bilgilerini kullandığında, kimlik bilgilerini bir noktadan dönüştürmek için kendi özel mekanizmanızı sağlamak istiyorsanız.  
  
- Özel bir belirteç oluşturuyorsanız.  
  
 Bu örnek, bir güvenlik belirteci hizmeti (STS) tarafından verilen belirteçleri önbelleğe alan özel bir belirteç sağlayıcısı oluşturmayı gösterir.  
  
 Özetlemek gerekirse, bu örnek şunları gösterir:  
  
- Bir istemcinin özel bir belirteç sağlayıcısıyla nasıl yapılandırılabileceğini.  
  
- Verilen belirteçlerin önbelleğe alınıp WCF istemcisine sağlanması.  
  
- Sunucunun, sunucunun X. 509.440 sertifikasını kullanarak istemci tarafından nasıl doğrulandığını.  
  
 Bu örnek, bir istemci konsol programından (Client. exe), bir güvenlik belirteci hizmeti konsol programı (SecurityTokenService. exe) ve bir hizmet konsolu programından (Service. exe) oluşur. Hizmet, istek-yanıt iletişim modelini tanımlayan bir sözleşme uygular. Sözleşme, matematik işlemlerini (ekleme, çıkarma, çarpma ve bölme) sunan `ICalculator` arabirimi tarafından tanımlanır. İstemci, güvenlik belirteci hizmetinden (STS) bir güvenlik belirteci alır ve belirli bir matematik işlemi için hizmete zaman uyumlu istekler sağlar ve hizmet sonuçla yanıt verir. İstemci etkinliği konsol penceresinde görünür.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
 Bu örnek, [\<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)kullanarak ICAL, ıvestor sözleşmesini gösterir. İstemci üzerindeki bu bağlamanın yapılandırması aşağıdaki kodda gösterilmiştir.  
  
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
  
 `wsFederationHttpBinding``security` öğesinde `mode` değeri hangi güvenlik modunun kullanılması gerektiğini yapılandırır. Bu örnekte, ileti güvenliği kullanılıyor, bu neden `wsFederationHttpBinding` `message` öğesinin `wsFederationHttpBinding``security` öğesi içinde belirtilmiş. `wsFederationHttpBinding` `message` öğesi içindeki `wsFederationHttpBinding` `issuer` öğesi, istemcinin Hesaplayıcı hizmetinde kimlik doğrulaması yapabilmesi için istemciye bir güvenlik belirteci veren güvenlik belirteci hizmeti için adresi ve bağlamayı belirtir.  
  
 Hizmette Bu bağlamanın yapılandırması aşağıdaki kodda gösterilmiştir.  
  
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
  
 `wsFederationHttpBinding``security` öğesinde `mode` değeri hangi güvenlik modunun kullanılması gerektiğini yapılandırır. Bu örnekte, ileti güvenliği kullanılıyor, bu neden `wsFederationHttpBinding` `message` öğesinin `wsFederationHttpBinding``security` öğesi içinde belirtilmiş. `wsFederationHttpBinding` `message` öğesi içindeki `wsFederationHttpBinding` `issuerMetadata` öğesi, güvenlik belirteci hizmeti için meta verileri almak üzere kullanılabilecek bir uç noktanın adresini ve kimliğini belirtir.  
  
 Hizmet davranışı aşağıdaki kodda gösterilmiştir.  
  
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
  
 `serviceCredentials` öğesi içindeki `issuedTokenAuthentication` öğesi, hizmetin kimlik doğrulaması sırasında istemcilerin sunmalarına izin verdiği belirteçlerde kısıtlamalar belirtmesini sağlar. Bu yapılandırma, konu adı CN = STS olan bir sertifika tarafından imzalanmış belirteçlerin hizmet tarafından kabul edildiğini belirtir.  
  
 Güvenlik belirteci hizmeti, standart wsHttpBinding kullanarak tek bir uç nokta gösterir. Güvenlik belirteci hizmeti istemcilerden gelen istek için yanıt verir ve istemcinin bir Windows hesabı kullanarak kimlik doğrulaması yaptığı belirtilen belirteçte, istemcinin kullanıcı adını içeren bir belirteç yayınlar. Belirteç oluşturmanın bir parçası olarak, güvenlik belirteci hizmeti, CN = STS sertifikasıyla ilişkili özel anahtarı kullanarak belirteci imzalar. Ayrıca, bir simetrik anahtar oluşturur ve CN = localhost sertifikasıyla ilişkili ortak anahtarı kullanarak şifreler. Belirteci istemciye döndürürken, güvenlik belirteci hizmeti simetrik anahtarı da döndürür. İstemci, verilen belirteci Hesaplayıcı hizmetine sunar ve iletiyi bu anahtarla imzalayarak simetrik anahtarı bilir olduğunu kanıtlar.  
  
## <a name="custom-client-credentials-and-token-provider"></a>Özel Istemci kimlik bilgileri ve belirteç sağlayıcısı  
 Aşağıdaki adımlarda, verilen belirteçleri önbelleğe alan ve WCF: Security ile tümleştiren özel bir belirteç sağlayıcısının nasıl geliştirilmesi gösterilmektedir.  
  
### <a name="to-develop-a-custom-token-provider"></a>Özel bir belirteç sağlayıcısı geliştirmek için  
  
1. Özel bir belirteç sağlayıcısı yazın.  
  
     Örnek, bir önbellekten alınan güvenlik belirtecini döndüren özel bir belirteç sağlayıcısı uygular.  
  
     Bu görevi gerçekleştirmek için, özel belirteç sağlayıcı <xref:System.IdentityModel.Selectors.SecurityTokenProvider> sınıfını türetir ve <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> yöntemini geçersiz kılar. Bu yöntem önbellekten bir belirteç almaya çalışır veya önbellekte bir belirteç bulunamazsa, temeldeki sağlayıcıdan bir belirteç alır ve ardından bu belirteci önbelleğe alır. Her iki durumda da yöntem bir `SecurityToken`döndürür.  
  
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
  
2. Özel güvenlik belirteci Yöneticisi yazın.  
  
     <xref:System.IdentityModel.Selectors.SecurityTokenManager>, `CreateSecurityTokenProvider` yönteminde kendisine geçirilen belirli bir <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> için <xref:System.IdentityModel.Selectors.SecurityTokenProvider> oluşturmak üzere kullanılır. Güvenlik belirteci Yöneticisi ayrıca belirteç kimlik doğrulayıcılar ve belirteç serileştiricileri oluşturmak için kullanılır, ancak bunlar bu örnek tarafından kapsanmaz. Bu örnekte, özel güvenlik belirteci Yöneticisi <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> sınıfından devralır ve geçilen belirteç gereksinimleri verilen belirtecin istendiğini gösteriyorsa, özel belirteç sağlayıcısını döndürmek için `CreateSecurityTokenProvider` yöntemini geçersiz kılar.  
  
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
  
     İstemci ara sunucusu için yapılandırılan kimlik bilgilerini temsil eden istemci kimlik bilgileri sınıfı kullanılır ve belirteç kimlik doğrulaması, belirteç sağlayıcıları ve belirteç serileştiricileri elde etmek için kullanılan güvenlik belirteci yöneticisini oluşturur.  
  
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
  
4. Belirteç önbelleğini uygulayın. Örnek uygulama, belirli bir belirteç önbelleğinin tüketicilerinin önbellek ile etkileşimde bulunduğu bir soyut temel sınıf kullanır.  
  
    ```csharp
    public abstract class IssuedTokenCache  
    {  
      public abstract void AddToken ( GenericXmlSecurityToken token, EndpointAddress target, EndpointAddress issuer);  
      public abstract bool TryGetToken(EndpointAddress target, EndpointAddress issuer, out GenericXmlSecurityToken cachedToken);  
    }  
    // Configure the client to use the custom client credential.  
    ```  
  
     İstemcinin özel istemci kimlik bilgisini kullanması için, örnek varsayılan istemci kimlik bilgisi sınıfını siler ve yeni istemci kimlik bilgisi sınıfını sağlar.  
  
    ```csharp
    clientFactory.Endpoint.Behaviors.Remove<ClientCredentials>();  
    DurableIssuedTokenClientCredentials durableCreds = new DurableIssuedTokenClientCredentials();  
    durableCreds.IssuedTokenCache = cache;  
    durableCreds.ServiceCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.PeerOrChainTrust;  
    clientFactory.Endpoint.Behaviors.Add(durableCreds);  
    ```  
  
## <a name="running-the-sample"></a>Örnek çalıştırma  
 Örneği çalıştırmak için aşağıdaki yönergelere bakın. Örneği çalıştırdığınızda, güvenlik belirteci isteği güvenlik belirteci hizmeti konsol penceresinde gösterilir. İşlem istekleri ve yanıtları istemci ve hizmet konsolu penceresinde görüntülenir. Uygulamayı kapatmak için konsol pencerelerinin herhangi birinde ENTER tuşuna basın.  
  
## <a name="the-setupcmd-batch-file"></a>Setup. cmd toplu Iş dosyası  
 Bu örneğe eklenen Setup. cmd toplu iş dosyası, şirket içinde barındırılan bir uygulamayı çalıştırmak için sunucu ve güvenlik belirteci hizmetini ilgili sertifikalarla yapılandırmanıza olanak tanır. Toplu iş dosyası, her ikisi de CurrentUser/Trustedkişileri sertifika deposunda iki sertifika oluşturur. İlk sertifika, CN = STS 'nin konu adına sahiptir ve güvenlik belirteci hizmeti tarafından, istemciye verdiği güvenlik belirteçlerini imzalamak için kullanılır. İkinci sertifika, CN = localhost konu adına sahiptir ve güvenlik belirteci hizmeti tarafından, hizmetin şifresini çözebilmesi için bir gizli dizi şifrelemek üzere kullanılır.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. Gerekli sertifikaları oluşturmak için Setup. cmd dosyasını çalıştırın.  
  
2. Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)bölümündeki yönergeleri izleyin. Çözümdeki tüm projelerin oluşturulduğundan emin olun (paylaşılan, RSTRSTR, hizmet, SecurityTokenService ve Istemci).  
  
3. Service. exe ve SecurityTokenService. exe ' nin her ikisinin de yönetici ayrıcalıklarıyla çalıştığından emin olun.  
  
4. Client. exe ' yi çalıştırın.  
  
### <a name="to-clean-up-after-the-sample"></a>Örnekten sonra temizlemek için  
  
1. Örneği çalıştırmayı bitirdikten sonra Samples klasöründe Cleanup. cmd ' i çalıştırın.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://go.microsoft.com/fwlink/?LinkId=150780) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Security\DurableIssuedTokenProvider`  
