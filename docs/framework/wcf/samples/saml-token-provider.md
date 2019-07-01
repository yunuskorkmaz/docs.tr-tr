---
title: SAML Belirteç Sağlayıcı
ms.date: 03/30/2017
ms.assetid: eb16e5e2-4c8d-4f61-a479-9c965fcec80c
ms.openlocfilehash: 19781b6b162034fb45587103d2a4af6684ab0fe1
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2019
ms.locfileid: "67487504"
---
# <a name="saml-token-provider"></a>SAML Belirteç Sağlayıcı
Bu örnek nasıl özel bir istemci SAML belirteç sağlayıcı uygulanacağını gösterir. Windows Communication Foundation (WCF) bir belirteç sağlayıcısı güvenlik altyapısı için kimlik bilgilerini sağlamak için kullanılır. Belirteç sağlayıcı genel hedef inceler ve böylece ileti güvenlik altyapısı güvenli hale getirebilirsiniz, kimlik bilgileri sorunları uygun. WCF varsayılan kimlik bilgileri Yöneticisi belirteç sağlayıcısı ile birlikte gelir. WCF ayrıca CardSpace belirteç sağlayıcısı ile birlikte gelir. Özel belirteç sağlayıcıları, aşağıdaki durumlarda kullanışlıdır:

- Bu belirteci sağlayıcıları ile çalışamaz bir kimlik bilgisi deposu varsa.

- Kullanıcı için WCF istemci framework kimlik bilgileri kullandığında ayrıntıları sağladığında noktadan kimlik dönüştürme için kendi özel mekanizması sağlamak istiyorsanız.

- Özel belirteç oluşturuluyorsa.

 Bu örnek nasıl kullanılacak WCF istemci framework dışında alınan bir SAML belirtecine izin veren özel bir belirteç sağlayıcısını oluşturulacağını gösterir.

 Özetlemek gerekirse, bu örnek aşağıdaki gösterir:

- Nasıl bir istemci özel bir belirteç sağlayıcısı ile yapılandırılabilir.

- SAML belirteci için özel istemci kimlik bilgilerini nasıl geçirilebilir.

- SAML belirteci WCF istemci framework nasıl sağlanmaktadır.

- Sunucu, sunucunun X.509 sertifikası kullanarak istemci tarafından nasıl doğrulanır.

 Hizmet, App.config yapılandırma dosyası kullanılarak tanımlanmış hizmet ile iletişim kurmak için iki uç noktalarını kullanıma sunar. Her uç nokta, adres, bağlama ve bir sözleşme oluşur. Bir standart yapılandırılmış bağlama `wsFederationHttpBinding`, ileti güvenliği kullanır. Bir uç nokta düzeltme simetrik anahtar diğer bir asimetrik sağlama anahtarı kullanan bir SAML belirteci kimlik doğrulaması için istemci beklediği sırada kullanan bir SAML belirteci ile kimlik doğrulaması için istemci bekliyor. Hizmet Ayrıca hizmet kullanarak sertifikayı yapılandırır `serviceCredentials` davranışı. `serviceCredentials` Davranışı bir hizmet sertifikası yapılandırmanıza olanak tanır. Bir hizmet sertifikası, hizmet kimlik doğrulaması ve ileti koruma sağlamak için bir istemci tarafından kullanılır. Aşağıdaki yapılandırma, bu konunun sonunda Kurulum yönergelerinde açıklandığı gibi örnek Kurulum sırasında yüklenen "localhost" sertifikanın başvuruyor. `serviceCredentials` Davranışı da SAML belirteçlerini imzalamak için güvenilen sertifikalar yapılandırmanıza olanak tanır. Aşağıdaki yapılandırma sırasında bir örnek yüklü 'Alice' sertifika başvuruyor.

```xml
<system.serviceModel>
 <services>
  <service
          name="Microsoft.ServiceModel.Samples.CalculatorService"
          behaviorConfiguration="CalculatorServiceBehavior">
   <host>
    <baseAddresses>
     <!-- configure base address provided by host -->
     <add
  baseAddress="http://localhost:8000/servicemodelsamples/service/" />
    </baseAddresses>
   </host>
   <!-- use base address provided by host -->
   <!-- Endpoint that expect SAML tokens with Symmetric proof keys -->
   <endpoint address="calc/symm"
             binding="wsFederationHttpBinding"
             bindingConfiguration="Binding1"
             contract="Microsoft.ServiceModel.Samples.ICalculator" />
   <!-- Endpoint that expect SAML tokens with Asymmetric proof keys -->
   <endpoint address="calc/asymm"
             binding="wsFederationHttpBinding"
             bindingConfiguration="Binding2"
             contract="Microsoft.ServiceModel.Samples.ICalculator" />
  </service>
 </services>

 <bindings>
  <wsFederationHttpBinding>
   <!-- Binding that expect SAML tokens with Symmetric proof keys -->
   <binding name="Binding1">
    <security mode="Message">
     <message negotiateServiceCredential ="false"
              issuedKeyType="SymmetricKey"
              issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1"  />
    </security>
   </binding>
   <!-- Binding that expect SAML tokens with Asymmetric proof keys -->
   <binding name="Binding2">
    <security mode="Message">
     <message negotiateServiceCredential ="false"
              issuedKeyType="AsymmetricKey"
              issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1"  />
    </security>
   </binding>
  </wsFederationHttpBinding>
 </bindings>

 <behaviors>
  <serviceBehaviors>
   <behavior name="CalculatorServiceBehavior">
    <!--
    The serviceCredentials behavior allows one to define a service certificate.
    A service certificate is used by a client to authenticate the service and provide message protection.
    This configuration references the "localhost" certificate installed during the setup instructions.
    -->
    <serviceCredentials>
     <!-- Set allowUntrustedRsaIssuers to true to allow self-signed, asymmetric key based SAML tokens -->
     <issuedTokenAuthentication allowUntrustedRsaIssuers ="true" >
      <!-- Add Alice to the list of certs trusted to issue SAML tokens -->
      <knownCertificates>
       <add storeLocation="LocalMachine"
            storeName="TrustedPeople"
            x509FindType="FindBySubjectName"
            findValue="Alice"/>
      </knownCertificates>
     </issuedTokenAuthentication>
     <serviceCertificate storeLocation="LocalMachine"
                         storeName="My"
                         x509FindType="FindBySubjectName"
                         findValue="localhost"  />
    </serviceCredentials>
   </behavior>
  </serviceBehaviors>
 </behaviors>

</system.serviceModel>
```

 Aşağıdaki adımlarda, bir özel SAML belirteç sağlayıcı geliştirin ve WCF ile tümleştirmek gösterilmektedir: güvenlik çerçevesi:

1. Bir özel SAML belirteç sağlayıcı yazma.

     Örnek oluşturma zamanında sağlanan bir SAML onaylama işlemi temel bir güvenlik belirteci döndüren bir özel SAML belirteç sağlayıcı uygular.

     Bu görevi gerçekleştirmek için özel belirteç sağlayıcısı türetilir <xref:System.IdentityModel.Selectors.SecurityTokenProvider> sınıf ve geçersiz kılmaları <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> yöntemi. Bu yöntem, oluşturur ve yeni bir `SecurityToken`.

    ```
    protected override SecurityToken GetTokenCore(TimeSpan timeout)
    {
     // Create a SamlSecurityToken from the provided assertion
     SamlSecurityToken samlToken = new SamlSecurityToken(assertion);

     // Create a SecurityTokenSerializer that will be used to
     // serialize the SamlSecurityToken
     WSSecurityTokenSerializer ser = new WSSecurityTokenSerializer();
     // Create a memory stream to write the serialized token into
     // Use an initial size of 64Kb
     MemoryStream s = new MemoryStream(UInt16.MaxValue);

     // Create an XmlWriter over the stream
     XmlWriter xw = XmlWriter.Create(s);

     // Write the SamlSecurityToken into the stream
     ser.WriteToken(xw, samlToken);

     // Seek back to the beginning of the stream
     s.Seek(0, SeekOrigin.Begin);

     // Load the serialized token into a DOM
     XmlDocument dom = new XmlDocument();
     dom.Load(s);

     // Create a KeyIdentifierClause for the SamlSecurityToken
     SamlAssertionKeyIdentifierClause samlKeyIdentifierClause = samlToken.CreateKeyIdentifierClause<SamlAssertionKeyIdentifierClause>();

    // Return a GenericXmlToken from the XML for the
    // SamlSecurityToken, the proof token, the valid from and valid
    // until times from the assertion and the key identifier clause
    // created above
    return new GenericXmlSecurityToken(dom.DocumentElement, proofToken, assertion.Conditions.NotBefore, assertion.Conditions.NotOnOrAfter, samlKeyIdentifierClause, samlKeyIdentifierClause, null);
    }
    ```

2. Özel güvenlik belirteci Yöneticisi'ni yazın.

     <xref:System.IdentityModel.Selectors.SecurityTokenManager> Sınıfı oluşturmak için kullanılan <xref:System.IdentityModel.Selectors.SecurityTokenProvider> belirli <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> kendisine geçirilen `CreateSecurityTokenProvider` yöntemi. Bir güvenlik belirteci Yöneticisi ayrıca belirteç Doğrulayıcı ve belirteç serializer özelliği oluşturmak için kullanılır, ancak bunlar Bu örnek tarafından kapsanmaz. Bu örnek özel güvenlik belirteci yöneticisi devraldığı <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> sınıf ve geçersiz kılmaları `CreateSecurityTokenProvider` geçirilen belirteci gereksinimleri belirttiğinizde, SAML belirteci özel SAML belirteç sağlayıcı döndürülecek yöntemi istendi. İstemci kimlik bilgileri sınıfı (3. adıma bakın) onaylama belirtilmemişse, güvenlik belirteci yöneticisi uygun bir örneğini oluşturur.

    ```
    public class SamlSecurityTokenManager :
     ClientCredentialsSecurityTokenManager
    {
     SamlClientCredentials samlClientCredentials;

     public SamlSecurityTokenManager ( SamlClientCredentials samlClientCredentials)
      : base(samlClientCredentials)
     {
      // Store the creating client credentials
      this.samlClientCredentials = samlClientCredentials;
     }

     public override SecurityTokenProvider CreateSecurityTokenProvider ( SecurityTokenRequirement tokenRequirement )
     {
      // If token requirement matches SAML token return the
      // custom SAML token provider
      if (tokenRequirement.TokenType == SecurityTokenTypes.Saml ||
          tokenRequirement.TokenType == "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1")
      {
       // Retrieve the SAML assertion and proof token from the
       // client credentials
       SamlAssertion assertion = this.samlClientCredentials.Assertion;
       SecurityToken prooftoken = this.samlClientCredentials.ProofToken;

       // If either the assertion of proof token is null...
       if (assertion == null || prooftoken == null)
       {
        // ...get the SecurityBindingElement and then the
        // specified algorithm suite
        SecurityBindingElement sbe = null;
        SecurityAlgorithmSuite sas = null;

        if ( tokenRequirement.TryGetProperty<SecurityBindingElement> ( "http://schemas.microsoft.com/ws/2006/05/servicemodel/securitytokenrequirement/SecurityBindingElement", out sbe))
        {
         sas = sbe.DefaultAlgorithmSuite;
        }

        // If the token requirement is for a SymmetricKey based token..
        if (tokenRequirement.KeyType == SecurityKeyType.SymmetricKey)
        {
         // Create a symmetric proof token
         prooftoken = SamlUtilities.CreateSymmetricProofToken ( tokenRequirement.KeySize );
         // and a corresponding assertion based on the claims specified in the client credentials
         assertion = SamlUtilities.CreateSymmetricKeyBasedAssertion ( this.samlClientCredentials.Claims, new X509SecurityToken ( samlClientCredentials.ClientCertificate.Certificate ), new X509SecurityToken ( samlClientCredentials.ServiceCertificate.DefaultCertificate ), (BinarySecretSecurityToken)prooftoken, sas);
        }
        // otherwise...
        else
        {
         // Create an asymmetric proof token
         prooftoken = SamlUtilities.CreateAsymmetricProofToken();
         // and a corresponding assertion based on the claims
         // specified in the client credentials
         assertion = SamlUtilities.CreateAsymmetricKeyBasedAssertion ( this.samlClientCredentials.Claims, prooftoken, sas );
        }
       }

       // Create a SamlSecurityTokenProvider based on the assertion and proof token
       return new SamlSecurityTokenProvider(assertion, prooftoken);
      }
      // otherwise use base implementation
      else
      {
       return base.CreateSecurityTokenProvider(tokenRequirement);
      }
    }
    ```

3. Özel istemci kimlik bilgilerini yazın.

     İstemci kimlik bilgileri sınıfı istemci proxy'si için yapılandırıldığında kimlik bilgilerini temsil etmek için kullanılır ve bir güvenlik belirteci kimlik doğrulayıcılar, belirteç sağlayıcıları ve belirteç serializer özelliği almak için kullanılan belirteci yöneticisi oluşturur.

    ```
    public class SamlClientCredentials : ClientCredentials
    {
     ClaimSet claims;
     SamlAssertion assertion;
     SecurityToken proofToken;

     public SamlClientCredentials() : base()
     {
      // Set SupportInteractive to false to suppress Cardspace UI
      base.SupportInteractive = false;
     }

     protected SamlClientCredentials(SamlClientCredentials other) : base ( other )
     {
      // Just do reference copy given sample nature
      this.assertion = other.assertion;
      this.claims = other.claims;
      this.proofToken = other.proofToken;
     }

     public SamlAssertion Assertion { get { return assertion; } set { assertion = value; } }

     public SecurityToken ProofToken { get { return proofToken; } set { proofToken = value; } }
     public ClaimSet Claims { get { return claims; } set { claims = value; } }

     protected override ClientCredentials CloneCore()
     {
      return new SamlClientCredentials(this);
     }

     public override SecurityTokenManager CreateSecurityTokenManager()
     {
      // return custom security token manager
      return new SamlSecurityTokenManager(this);
     }
    }
    ```

4. Özel istemci kimlik bilgilerini kullanacak biçimde yapılandırın.

     Örnek, varsayılan istemci kimlik bilgisi sınıfını siler ve istemci özel bir istemci kimlik bilgileri kullanabilmeniz için yeni istemci kimlik bilgisi sınıfını sağlar.

    ```
    // Create new credentials class
    SamlClientCredentials samlCC = new SamlClientCredentials();

    // Set the client certificate. This is the cert that will be used to sign the SAML token in the symmetric proof key case
    samlCC.ClientCertificate.SetCertificate(StoreLocation.CurrentUser, StoreName.My, X509FindType.FindBySubjectName, "Alice");

    // Set the service certificate. This is the cert that will be used to encrypt the proof key in the symmetric proof key case
    samlCC.ServiceCertificate.SetDefaultCertificate(StoreLocation.CurrentUser, StoreName.TrustedPeople, X509FindType.FindBySubjectName, "localhost");

    // Create some claims to put in the SAML assertion
    IList<Claim> claims = new List<Claim>();
    claims.Add(Claim.CreateNameClaim(samlCC.ClientCertificate.Certificate.Subject));
    ClaimSet claimset = new DefaultClaimSet(claims);
    samlCC.Claims = claimset;

    // set new credentials
    client.ChannelFactory.Endpoint.Behaviors.Remove(typeof(ClientCredentials));
    client.ChannelFactory.Endpoint.Behaviors.Add(samlCC);
    ```

 Hizmet arayanla ilişkili talep görüntülenir. Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir. İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.

## <a name="setup-batch-file"></a>Kurulum toplu iş dosyası
 Bu örnekle dahil Setup.bat toplu iş dosyası, sunucu sertifika tabanlı güvenlik gerektiren şirket içinde barındırılan bir uygulamayı çalıştırmak için ilgili sertifika ile sunucu yapılandırmanıza olanak sağlar. Bu toplu iş dosyası bilgisayarlarda çalışmaya veya barındırılan olmayan bir durumda çalışması için değiştirilmesi gerekir.

 Aşağıda, böylece uygun yapılandırmasında çalıştırılacak değiştirilebilir toplu iş dosyaları farklı bölümlerini kısa bir genel bakış sağlar.

- Sunucu sertifikası oluşturuluyor:

     Setup.bat toplu iş dosyasından aşağıdaki satırları kullanılacak sunucu sertifikası oluşturun. `%SERVER_NAME%` Değişkeni, sunucu adını belirtir. Kendi sunucu adını belirtmek için bu değişkeni değiştirin. Localhost bu toplu iş dosyasında varsayılan değerdir.

     Sertifikayı LocalMachine depolama konumu altında (Kişisel) My deposunda depolanır.

    ```
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss My -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- Sunucu sertifikasını istemcinin güvenilen sertifika depolama alanına yükleniyor:

     İstemci güvenilir kişiler uygulamasına Setup.bat toplu dosya kopyalama sunucu sertifikasının aşağıdaki satırları depolayın. MakeCert.exe tarafından oluşturulan sertifikaları örtük olarak istemci sistemi tarafından güvenilir değildir çünkü bu adım gereklidir. Bir istemci güvenilen kök sertifikayı kök erişim izni verilmiş bir sertifika zaten varsa — örneğin, Microsoft tarafından verilen sertifika — sunucu sertifikasında istemci sertifika deposunun doldurulması, bu adım gerekli değildir.

    ```
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r LocalMachine -s TrustedPeople
    ```

- Verenin sertifika oluşturuluyor.

     Setup.bat toplu iş dosyasından aşağıdaki satırları kullanılacak sertifikayı oluşturun. `%USER_NAME%` Değişkeni sertifikayı verenin adını belirtir. Kendi verenin adı belirtmek için bu değişkeni değiştirin. Alice bu toplu iş dosyasında varsayılan değerdir.

     Sertifika CurrentUser depolama konumu altında My deposunda depolanır.

    ```
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr CurrentUser -ss My -a sha1 -n CN=%USER_NAME% -sky exchange -pe
    ```

- Sertifikayı sunucusunun güvenilen sertifika depolama alanına yükleniyor.

     İstemci güvenilir kişiler uygulamasına Setup.bat toplu dosya kopyalama sunucu sertifikasının aşağıdaki satırları depolayın. MakeCert.exe tarafından oluşturulan sertifikaları örtük olarak istemci sistemi tarafından güvenilir değildir çünkü bu adım gereklidir. Bir istemci güvenilen kök sertifikayı kök erişim izni verilmiş bir sertifika zaten varsa — örneğin, Microsoft tarafından verilen sertifika — sertifikayı ile sunucu sertifika deposuna yerleştirmek, bu adım gerekli değildir.

    ```
    certmgr.exe -add -r CurrentUser -s My -c -n %USER_NAME% -r LocalMachine -s TrustedPeople
    ```

#### <a name="to-set-up-and-build-the-sample"></a>Ayarlama ve örneği oluşturmak için

1. Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2. Çözümü derlemek için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).

> [!NOTE]
>  Bu örnek için yapılandırmayı yeniden üretmek için Svcutil.exe kullanma, istemci kodu eşleştirilecek istemci yapılandırmasında uç noktası adını değiştirmek emin olun.

#### <a name="to-run-the-sample-on-the-same-computer"></a>Örneği aynı bilgisayarda çalıştırmak için

1. Visual Studio 2012 komut istemini yönetici ayrıcalıklarıyla çalıştırın içinde örnek yükleme klasöründen Setup.bat çalıştırın. Bu örneği çalıştırmak için gerekli olan tüm sertifikaları yükler.

    > [!NOTE]
    >  Setup.bat toplu iş dosyası, bir Visual Studio 2012 komut isteminden çalıştırılması için tasarlanmıştır. PATH ortam değişkenine içinde Visual Studio 2012 komut istemi noktaları Setup.bat betiği tarafından gereken yürütülebilir dosyaları içeren dizine ayarlayın.  
  
2. Service.exe service\bin ' başlatın.  
  
3. Client.exe \client\bin başlatın. İstemci etkinliği istemci konsol uygulamasında görüntülenir.  
  
4. İstemci ve hizmet iletişim kurabildiğini bilmiyorsanız bkz [WCF örnekleri için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-run-the-sample-across-computers"></a>Bilgisayarlar arasında örneği çalıştırmak için  
  
1. Hizmet ikili dosyaları için hizmet bilgisayarda bir dizin oluşturun.  
  
2. Hizmet program dosyaları hizmeti bilgisayarında hizmet dizinine kopyalayın. Ayrıca Setup.bat ve Cleanup.bat dosyaları hizmet bilgisayara kopyalayın.  
  
3. Bilgisayarın tam etki alanı adını içeren konu adına sahip bir sunucu sertifikası olmalıdır. Service.exe.config dosyayı bu yeni sertifika adı yansıtacak şekilde güncelleştirilmesi gerekir. Setup.bat toplu iş dosyasını değiştirerek, sunucu sertifikası oluşturabilirsiniz. Geliştirici komut istemini yönetici ayrıcalıklarıyla açılan bir Visual Studio penceresinin setup.bat dosyasının çalıştırılması gerektiğini unutmayın. Ayarlamalısınız `%SERVER_NAME%` değişken hizmeti barındırmak için kullanılan bilgisayarın tam ana bilgisayar adı.  
  
4. Sunucu sertifikasını istemcinin CurrentUser TrustedPeople depoya kopyalayın. Sunucu sertifikası güvenilir istemci veren tarafından verildiğinde, bu adım gerekli değildir.  
  
5. Hizmet bilgisayarı Service.exe.config dosyada localhost yerine tam bilgisayar adını belirtmek için temel adresini değiştirin.  
  
6. Hizmet bilgisayarda Service.exe bir komut isteminden çalıştırın.  
  
7. İstemci program dosyaları \client\bin\ klasöründen dile özgü klasörünün altındaki istemci bilgisayara kopyalayın.  
  
8. İstemci bilgisayarda Client.exe.config dosyasında hizmetinizin yeni adresiyle eşleşecek şekilde uç nokta adresi değiştirin.  
  
9. İstemci bilgisayarda Başlat `Client.exe` bir komut istemi penceresinden.  
  
10. İstemci ve hizmet iletişim kurabildiğini bilmiyorsanız bkz [WCF örnekleri için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-clean-up-after-the-sample"></a>Sonra örnek temizlemek için  
  
1. Bu örneği çalıştırmadan tamamladıktan sonra Cleanup.bat samples klasöründe çalıştırın.  
