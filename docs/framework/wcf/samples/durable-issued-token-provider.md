---
title: Dayanıklı Verilen Belirteç Sağlayıcısı
ms.date: 03/30/2017
ms.assetid: 76fb27f5-8787-4b6a-bf4c-99b4be1d2e8b
ms.openlocfilehash: 145faaae709119708240863f85eb5352fb2c5a1b
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33807557"
---
# <a name="durable-issued-token-provider"></a>Dayanıklı Verilen Belirteç Sağlayıcısı
Bu örnek, verilen belirteç sağlayıcısı özel bir istemci uygulaması gösterilmiştir.  
  
## <a name="discussion"></a>Tartışma  
 Bir belirteç sağlayıcısı Windows Communication Foundation (WCF) güvenlik altyapısı için kimlik bilgilerini sağlamak için kullanılır. Belirteç sağlayıcı genel hedef inceler ve böylece güvenlik altyapısı ileti güvenliğini sağlayabilirsiniz sorunları kimlik bilgileri gerekli. WCF ile birlikte gelen bir [!INCLUDE[infocard](../../../../includes/infocard-md.md)] belirteç sağlayıcısı. Özel belirteç sağlayıcılarını aşağıdaki durumlarda yararlı olur:  
  
-   Yerleşik belirteç sağlayıcısı ile çalışamaz bir kimlik bilgisi deposu varsa.  
  
-   Kullanıcı için WCF istemci kimlik bilgileri kullandığında ayrıntılarını sağladığında kimlik bilgilerini noktadan dönüştürme için kendi özel mekanizması sağlamak istiyorsanız.  
  
-   Özel belirteç oluşturuluyorsa.  
  
 Bu örnek bir güvenlik belirteci hizmeti (STS) tarafından yayınlanan belirteçleri önbelleğe alan özel bir belirteç sağlayıcısını nasıl oluşturulacağını gösterir.  
  
 Özetlemek için bu örnek şunlar gösterilmektedir:  
  
-   Nasıl bir istemci bir özel belirteç sağlayıcısı ile yapılandırılabilir.  
  
-   Verilen belirteçler önbelleğe ve WCF istemcisi sağlanan nasıl.  
  
-   Sunucu sunucunun X.509 sertifikası kullanarak istemci tarafından kimlik doğrulamasının nasıl.  
  
 Bu örnek, bir istemci konsol programı (Client.exe), bir güvenlik belirteci hizmeti konsol programı (Securitytokenservice.exe) ve hizmeti bir konsol programı (Service.exe) oluşur. Hizmet bir istek-yanıt iletişim deseni tanımlayan bir sözleşme uygular. Anlaşma tarafından tanımlanan `ICalculator` matematik işlemleri kullanıma sunan arabirim (eklemek, çıkarma, çarpma ve bölme). İstemci güvenlik belirteci hizmeti (STS) bir güvenlik belirtecini alır ve hizmet verilen matematik işlemi ve sonuç ile hizmet yanıtlar için eş zamanlı istekleri yapar. İstemci etkinliği konsol penceresinde görünür olur.  
  
> [!NOTE]
>  Kurulum yordam ve yapılandırma yönergeleri Bu örneği için bu konunun sonunda yer alır.  
  
 Bu örnek ICalculator sözleşme kullanarak gösterir [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md). Bu bağlama istemcide yapılandırmasını aşağıdaki kodda gösterilir.  
  
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
  
 Üzerinde `security` öğesinin `wsFederationHttpBinding`, `mode` değeri yapılandırır hangi güvenlik modunda kullanılmalıdır. Bu örnekte, iletilerin güvenlik, neden olduğu kullanılıyor `message` öğesinin `wsFederationHttpBinding` içinde belirtilen `security` öğesinin `wsFederationHttpBinding`. `issuer` Öğesinin `wsFederationHttpBinding` içinde `message` öğesinin `wsFederationHttpBinding` güvenlik belirteci istemciye bir güvenlik belirteci verir ve böylece istemci makinesine doğrulanabilir hizmeti için bağlama ve adresini belirtir hizmet.  
  
 Bu bağlama hizmetinin yapılandırmasını aşağıdaki kodda gösterilir.  
  
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
  
 Üzerinde `security` öğesinin `wsFederationHttpBinding`, `mode` değeri yapılandırır hangi güvenlik modunda kullanılmalıdır. Bu örnekte, iletilerin güvenlik, neden olduğu kullanılıyor `message` öğesinin `wsFederationHttpBinding` içinde belirtilen `security` öğesinin `wsFederationHttpBinding`. `issuerMetadata` Öğesinin `wsFederationHttpBinding` içinde `message` öğesinin `wsFederationHttpBinding` için güvenlik belirteci hizmeti meta verilerini almak için kullanılan bir uç nokta için kimlik ve adresini belirtir.  
  
 Hizmeti için davranış aşağıdaki kodda gösterilir.  
  
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
  
 `issuedTokenAuthentication` Öğesi içinde `serviceCredentials` öğesi kimlik doğrulaması sırasında sunmak istemcileri veren belirteçleri kısıtlamaları belirtmek hizmet sağlar. Bu yapılandırma belirteçleri konu adı olan CN sertifika tarafından imzalanan belirtir = STS hizmeti tarafından kabul edilir.  
  
 Güvenlik belirteci hizmeti standart wsHttpBinding kullanarak tek bir uç noktasını kullanıma sunar. Güvenlik belirteci hizmeti belirteçleri istemcilerden isteğine yanıt verir ve bir Windows hesabı kullanarak istemci kimlik doğrulaması sağlanan bir talep verilen belirteç olarak istemcinin kullanıcı adını içeren bir belirteç verir. Güvenlik belirteci hizmeti işaretlerini belirtecin CN ile ilişkili özel anahtarı kullanarak belirteci oluşturma bir parçası olarak STS sertifikası =. Ayrıca, bir simetrik anahtar oluşturur ve CN ile ilişkilendirilmiş ortak anahtar kullanarak şifreler localhost sertifika =. Belirteç istemciye göndermeden, güvenlik belirteci hizmeti simetrik anahtar da döndürür. İstemci hesaplayıcı hizmete verilen belirteç gösterir ve onu simetrik anahtar bu anahtarla ileti imzalayarak bilir kanıtlar.  
  
## <a name="custom-client-credentials-and-token-provider"></a>Özel istemci kimlik bilgileri ve belirteç sağlayıcı  
 Aşağıdaki adımları verilen belirteçler önbellekleri özel bir belirteç sağlayıcısı geliştirmek ve WCF ile tümleştirmek nasıl göster: güvenlik.  
  
#### <a name="to-develop-a-custom-token-provider"></a>Özel bir belirteç sağlayıcısı geliştirmek için  
  
1.  Özel bir belirteç sağlayıcısı yazma.  
  
     Örnek bir önbellekten alınan bir güvenlik belirteci verir özel bir belirteç sağlayıcısını uygular.  
  
     Bu görevi gerçekleştirmek için özel belirteç sağlayıcı türetilen <xref:System.IdentityModel.Selectors.SecurityTokenProvider> sınıfı ve geçersiz kılmalar <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> yöntemi. Bu yöntem önbellekten belirteç almak çalışır veya bir belirteç önbelleğinde bulunamazsa, temel alınan sağlayıcısından bir belirteç alır ve belirtecini önbelleğe alır. Her iki durumda da yöntem döndürür bir `SecurityToken`.  
  
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
  
2.  Özel güvenlik belirteci yöneticisi yazma.  
  
     <xref:System.IdentityModel.Selectors.SecurityTokenManager> Oluşturmak için kullanılan bir <xref:System.IdentityModel.Selectors.SecurityTokenProvider> belirli bir <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> kendisine geçirilen `CreateSecurityTokenProvider` yöntemi. Güvenlik belirteci Yöneticisi ayrıca belirteç kimlik doğrulayan ve belirteç serileştiricileri oluşturmak için kullanılır, ancak bunlar Bu örnek tarafından kapsanmayan. Bu örnekte, özel güvenlik belirteci yöneticisi devraldığı <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> sınıfı ve geçersiz kılmalar `CreateSecurityTokenProvider` geçirilen belirteci gereksinimleri belirtmek özel belirteç sağlayıcı verilen bir belirteç döndürülecek yöntemi istendi.  
  
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
  
3.  Özel istemci kimlik bilgilerini yazın.  
  
     Bir istemci kimlik bilgileri sınıfı istemci proxy için yapılandırılmış olan kimlik bilgilerini temsil etmek için kullanılır ve güvenlik belirteci Doğrulayıcı, belirteci sağlayıcıları ve belirteç serileştiricileri elde etmek için kullanılan belirteci yöneticisi oluşturur.  
  
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
  
4.  Belirteç önbelleği uygulayın. Örnek uygulama üzerinden verilen belirteç önbelleği tüketicileri etkileşim Özet temel sınıf önbellek ile kullanır.  
  
    ```  
    public abstract class IssuedTokenCache  
    {  
      public abstract void AddToken ( GenericXmlSecurityToken token, EndpointAddress target, EndpointAddress issuer);  
      public abstract bool TryGetToken(EndpointAddress target, EndpointAddress issuer, out GenericXmlSecurityToken cachedToken);  
    }  
    Configure the client to use the custom client credential.  
    ```  
  
     Özel istemci kimlik bilgisi kullanmak istemcinin örnek varsayılan istemci kimlik bilgisi sınıfını siler ve yeni istemci kimlik bilgisi sınıfını sağlar.  
  
    ```  
    clientFactory.Endpoint.Behaviors.Remove<ClientCredentials>();  
    DurableIssuedTokenClientCredentials durableCreds = new DurableIssuedTokenClientCredentials();  
    durableCreds.IssuedTokenCache = cache;  
    durableCreds.ServiceCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.PeerOrChainTrust;  
    clientFactory.Endpoint.Behaviors.Add(durableCreds);  
    ```  
  
## <a name="running-the-sample"></a>Örnek çalışıyor  
 Örneği çalıştırmak için aşağıdaki yönergelere bakın. Örneği çalıştırdığınızda, istek güvenlik belirteci için güvenlik belirteci hizmeti konsol penceresinde gösterilir. İşlem istekleri ve yanıtları istemci ve hizmet Konsolu pencerelerinde görüntülenir. Herhangi bir windows konsol uygulamasını kapatmak için ENTER tuşuna basın.  
  
## <a name="the-setupcmd-batch-file"></a>Setup.cmd toplu iş dosyası  
 Bu örnekle dahil Setup.cmd toplu iş dosyası, sunucu ve güvenlik belirteci hizmeti ile ilgili sertifika kendini barındıran bir uygulamayı çalıştırmak için yapılandırmanıza olanak sağlar. Toplu iş dosyasını hem de Currentuser'a/TrustedPeople sertifika deposunu iki sertifikaları oluşturur. İlk sertifika CN bir konu adına sahip STS = ve güvenlik belirteci hizmeti tarafından istemcinin verdiği güvenlik belirteçleri imzalamak için kullanılır. İkinci sertifikanın CN bir konu adına sahip localhost = ve güvenlik belirteci hizmeti tarafından hizmet şifreyi böylece bir gizli anahtarı şifrelemek için kullanılır.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerekli sertifikaları oluşturmak için Setup.cmd dosyasını çalıştırın.  
  
2.  Çözümü derlemek için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md). Çözümdeki tüm projeleri (paylaşılan, RSTRSTR, hizmet, SecurityTokenService ve istemci) oluşturulan emin olun.  
  
3.  Service.exe ve SecurityTokenService.exe hem de yönetici ayrıcalıklarıyla çalıştığından emin olun.  
  
4.  Client.exe çalıştırın.  
  
#### <a name="to-clean-up-after-the-sample"></a>Örnek sonra temizlemek için  
  
1.  Örnek çalıştıran tamamladıktan sonra Cleanup.cmd samples klasöründen çalıştırın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Security\DurableIssuedTokenProvider`  
  
## <a name="see-also"></a>Ayrıca Bkz.
