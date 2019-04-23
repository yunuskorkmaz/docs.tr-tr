---
title: Dayanıklı Verilen Belirteç Sağlayıcısı
ms.date: 03/30/2017
ms.assetid: 76fb27f5-8787-4b6a-bf4c-99b4be1d2e8b
ms.openlocfilehash: f91f603e91b1f640ebe97229a1a433446cddb0cf
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59771640"
---
# <a name="durable-issued-token-provider"></a>Dayanıklı Verilen Belirteç Sağlayıcısı
Bu örnek, verilen belirteç sağlayıcısı, özel bir istemci uygulama gösterilmiştir.  
  
## <a name="discussion"></a>Tartışma  
 Windows Communication Foundation (WCF) bir belirteç sağlayıcısı güvenlik altyapısı için kimlik bilgilerini sağlamak için kullanılır. Belirteç sağlayıcı genel hedef inceler ve böylece ileti güvenlik altyapısı güvenli hale getirebilirsiniz, kimlik bilgileri sorunları uygun. WCF ile birlikte gelir bir [!INCLUDE[infocard](../../../../includes/infocard-md.md)] belirteç sağlayıcısı. Özel belirteç sağlayıcıları, aşağıdaki durumlarda kullanışlıdır:  
  
-   Yerleşik belirteç sağlayıcısı ile çalışamaz bir kimlik bilgisi deposu varsa.  
  
-   Kullanıcı için WCF istemci kimlik bilgileri kullandığında ayrıntıları sağladığında noktadan kimlik dönüştürme için kendi özel mekanizması sağlamak istiyorsanız.  
  
-   Özel belirteç oluşturuluyorsa.  
  
 Bu örnek, bir güvenlik belirteci hizmeti (STS) tarafından verilen belirteçlere önbelleğe alan özel bir belirteç sağlayıcısı oluşturmak nasıl gösterir.  
  
 Özetlemek gerekirse, bu örnek aşağıdaki gösterir:  
  
-   Nasıl bir istemci özel bir belirteç sağlayıcısı ile yapılandırılabilir.  
  
-   Verilen belirteçleri önbelleğe alınmış ve WCF istemcisine sağlanan nasıl.  
  
-   Sunucu, sunucunun X.509 sertifikası kullanarak istemci tarafından nasıl doğrulanır.  
  
 Bu örnek, bir istemci konsol programı'nı (Client.exe), bir güvenlik belirteci hizmeti konsol programı (Securitytokenservice.exe) ve hizmeti bir konsol programı (Service.exe) oluşur. Hizmet istek-yanıt iletişim deseni tanımlayan bir sözleşme uygular. Anlaşma tarafından tanımlanan `ICalculator` matematik işlemlerinden sunan arabirimi (ekleme, çıkarma, çarpma ve bölme). İstemci güvenlik belirteci hizmeti (STS) gelen bir güvenlik belirteci alır ve hizmet verilen matematik işlemi ve sonuç ile hizmet verilen yanıtları için zaman uyumlu istekleri yapar. İstemci etkinliği konsol penceresinde görünür.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergeleri Bu konunun sonunda yer alır.  
  
 Sözleşme ICalculator kullanarak bu örnek gösterir [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md). Bu bağlamanın istemcide yapılandırma aşağıdaki kodda gösterilmiştir.  
  
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
  
 Üzerinde `security` öğesinin `wsFederationHttpBinding`, `mode` değeri yapılandırır hangi güvenlik modunda kullanılmalıdır. Bu örnekte, iletilerin güvenlik, neden olduğu kullanılıyor `message` öğesinin `wsFederationHttpBinding` içinde belirtilen `security` öğesinin `wsFederationHttpBinding`. `issuer` Öğesinin `wsFederationHttpBinding` içinde `message` öğesinin `wsFederationHttpBinding` güvenlik belirteci istemciye bir güvenlik belirteci verir ve böylece Hesaplayıcıya istemci kimlik doğrulaması hizmeti için bağlamasını ve adresini belirtir. hizmeti.  
  
 Bu bağlamanın hizmet yapılandırma aşağıdaki kodda gösterilmiştir.  
  
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
  
 Üzerinde `security` öğesinin `wsFederationHttpBinding`, `mode` değeri yapılandırır hangi güvenlik modunda kullanılmalıdır. Bu örnekte, iletilerin güvenlik, neden olduğu kullanılıyor `message` öğesinin `wsFederationHttpBinding` içinde belirtilen `security` öğesinin `wsFederationHttpBinding`. `issuerMetadata` Öğesinin `wsFederationHttpBinding` içinde `message` öğesinin `wsFederationHttpBinding` adresini ve kimlik için güvenlik belirteci hizmeti meta verilerini almak için kullanılan uç noktaya ilişkin belirtir.  
  
 Hizmet davranışı, aşağıdaki kodda gösterilir.  
  
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
  
 `issuedTokenAuthentication` Öğe içinde `serviceCredentials` öğesi istemcileri kimlik doğrulaması sırasında sunmak veren belirteçleri kısıtlamaları belirtmek bir hizmet sağlar. Bu yapılandırma, belirteçleri CN konu adı olan bir sertifika tarafından imzalanmış belirtir = STS hizmeti tarafından kabul edilir.  
  
 Güvenlik belirteci hizmeti standart wsHttpBinding kullanarak tek bir uç noktasını kullanıma sunar. Güvenlik belirteci hizmeti belirteçleri için istemcilerden isteğine yanıt vermeden ve sağlanan istemci kimlik doğrulaması kullanarak bir Windows hesabı verilen belirtecinde talep olarak istemcinin kullanıcı adını içeren bir belirteç verir. Belirteç, güvenlik belirteci hizmeti işaretleri CN ile ilişkili özel anahtarı kullanarak belirteci oluşturma işleminin parçası olarak STS sertifikasını =. Ayrıca, bir simetrik anahtar oluşturur ve CN ile ilişkili bir ortak anahtar kullanarak şifreler = localhost sertifikasına. Güvenlik belirteci hizmeti belirteci istemciye göndermeden, simetrik anahtarı da döndürür. İstemci, verilen belirteç hesaplayıcı hizmetine sunar ve, simetrik anahtarı bu anahtarla ileti açarak bilir kanıtlar.  
  
## <a name="custom-client-credentials-and-token-provider"></a>Özel istemci kimlik bilgileri ve belirteç sağlayıcısı  
 Aşağıdaki adımları verilen belirteçler önbellekler özel bir belirteç sağlayıcısını geliştirin ve WCF ile tümleştirme işlemini göstermektedir: güvenlik.  
  
#### <a name="to-develop-a-custom-token-provider"></a>Özel bir belirteç sağlayıcısını geliştirmek için  
  
1. Özel bir belirteç sağlayıcısını yazın.  
  
     Örnek bir önbellekten bir güvenlik belirteci döndüren özel bir belirteç sağlayıcısını uygular.  
  
     Bu görevi gerçekleştirmek için özel belirteç sağlayıcısı türetilen <xref:System.IdentityModel.Selectors.SecurityTokenProvider> sınıf ve geçersiz kılmaları <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> yöntemi. Bu yöntem önbellekten belirteç almak çalışır ve önbellekte bir belirteç bulunamazsa, temel alınan sağlayıcısından bir belirteç alır ve ardından bu belirteç önbelleğe alır. Her iki durumda da yöntem döndürür bir `SecurityToken`.  
  
    ```  
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
  
2. Özel güvenlik belirteci Yöneticisi'ni yazın.  
  
     <xref:System.IdentityModel.Selectors.SecurityTokenManager> Oluşturmak için kullanılan bir <xref:System.IdentityModel.Selectors.SecurityTokenProvider> belirli <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> kendisine geçirilen `CreateSecurityTokenProvider` yöntemi. Güvenlik belirteci Yöneticisi ayrıca belirteç Doğrulayıcı ve belirteci seri hale getiricileri genişletme oluşturmak için kullanılır, ancak bunlar Bu örnek tarafından ele alınmamıştır. Bu örnekte, özel güvenlik belirteci yöneticisi devraldığı <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> sınıf ve geçersiz kılmaları `CreateSecurityTokenProvider` yöntemi özel belirteç sağlayıcısı, geçirilen belirteci gereksinimleri belirttiğinizde, verilen bir belirteç geri dönmek için istendi.  
  
    ```  
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
        Else  
        {  
          return base.CreateSecurityTokenProvider(tokenRequirement);  
        }  
      }  
    }  
    ```  
  
3. Özel istemci kimlik bilgilerini yazın.  
  
     Bir istemci kimlik bilgileri sınıfı istemci proxy'si için yapılandırıldığında kimlik bilgilerini temsil etmek için kullanılır ve güvenlik belirteci kimlik doğrulayıcılar, belirteç sağlayıcıları ve belirteci seri hale getiricileri genişletme elde etmek için kullanılan belirteci yöneticisi oluşturur.  
  
    ```  
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
        Get  
        {  
          return this.cache;  
        }  
        Set  
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
  
4. Belirteç önbelleği uygulayın. Örnek uygulamada, verilen bir belirteç önbelleği tüketicilerinin etkileşim soyut bir temel sınıf önbellek ile kullanır.  
  
    ```  
    public abstract class IssuedTokenCache  
    {  
      public abstract void AddToken ( GenericXmlSecurityToken token, EndpointAddress target, EndpointAddress issuer);  
      public abstract bool TryGetToken(EndpointAddress target, EndpointAddress issuer, out GenericXmlSecurityToken cachedToken);  
    }  
    Configure the client to use the custom client credential.  
    ```  
  
     Özel istemci kimlik bilgilerini kullanmak istemci örneği, varsayılan istemci kimlik bilgisi sınıfını siler ve yeni istemci kimlik bilgisi sınıfını sağlar.  
  
    ```  
    clientFactory.Endpoint.Behaviors.Remove<ClientCredentials>();  
    DurableIssuedTokenClientCredentials durableCreds = new DurableIssuedTokenClientCredentials();  
    durableCreds.IssuedTokenCache = cache;  
    durableCreds.ServiceCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.PeerOrChainTrust;  
    clientFactory.Endpoint.Behaviors.Add(durableCreds);  
    ```  
  
## <a name="running-the-sample"></a>Örneği çalıştırma  
 Örneği çalıştırmak için aşağıdaki yönergelere bakın. Örneği çalıştırdığında, güvenlik belirteci isteği güvenlik belirteci hizmeti konsol penceresinde gösterilir. İşlem istekleri ve yanıtları istemci ve hizmet Konsolu pencerelerinde görüntülenir. Uygulamayı kapatın, herhangi bir windows konsol ENTER tuşuna basın.  
  
## <a name="the-setupcmd-batch-file"></a>Setup.cmd toplu iş dosyası  
 Bu örnekle dahil Setup.cmd toplu iş dosyası, sunucu ve güvenlik belirteci hizmeti ile ilgili sertifika şirket içinde barındırılan bir uygulamayı çalıştırmak için yapılandırmanıza olanak sağlar. Toplu iş dosyası, iki sertifika hem de CurrentUser/TrustedPeople sertifika deposunu oluşturur. İlk sertifikayı sahip bir konu adı CN = STS ve güvenlik belirteci hizmeti tarafından istemciye verdiği güvenlik belirteçleri imzalamak için kullanılır. İkinci sertifikayı sahip bir konu adı CN = localhost ve güvenlik belirteci hizmeti tarafından hizmet şifresini şifrelemek için kullanılır.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1. Gerekli sertifikaları oluşturmak için Setup.cmd dosyasını çalıştırın.  
  
2. Çözümü derlemek için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md). Çözümdeki tüm projeleri (paylaşılan, RSTRSTR, hizmet, SecurityTokenService ve istemci) oluşturulan emin olun.  
  
3. Service.exe ve SecurityTokenService.exe hem de yönetici ayrıcalıklarıyla çalıştığından emin olun.  
  
4. Client.exe çalıştırın.  
  
#### <a name="to-clean-up-after-the-sample"></a>Sonra örnek temizlemek için  
  
1. Bu örneği çalıştırmadan tamamladıktan sonra Cleanup.cmd samples klasöründe çalıştırın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Security\DurableIssuedTokenProvider`  
