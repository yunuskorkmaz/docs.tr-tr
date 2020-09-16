---
title: SAML Belirteç Sağlayıcı
ms.date: 03/30/2017
ms.assetid: eb16e5e2-4c8d-4f61-a479-9c965fcec80c
ms.openlocfilehash: 4e371d518d7ef25152aba83fa00d79893397b07f
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554429"
---
# <a name="saml-token-provider"></a>SAML Belirteç Sağlayıcı
Bu örnek, özel bir istemci SAML belirteci sağlayıcısının nasıl uygulanacağını gösterir. Güvenlik altyapısına kimlik bilgileri sağlamak için Windows Communication Foundation (WCF) içindeki bir belirteç sağlayıcısı kullanılır. Genel içindeki belirteç sağlayıcısı hedefi inceler ve güvenlik altyapısının iletiyi güvenli hale getirmek için uygun kimlik bilgilerini verir. WCF varsayılan kimlik bilgileri Yöneticisi belirteç sağlayıcısıyla birlikte gelir. WCF Ayrıca bir CardSpace belirteç sağlayıcısıyla birlikte gelir. Özel belirteç sağlayıcıları aşağıdaki durumlarda faydalıdır:

- Bu belirteç sağlayıcılarının ile çalışamadığınız bir kimlik bilgisi depoluğiniz varsa.

- Kullanıcı, WCF istemci çerçevesi kimlik bilgilerini kullandığında, kimlik bilgilerini bir noktadan dönüştürmek için kendi özel mekanizmanızı sağlamak istiyorsanız.

- Özel bir belirteç oluşturuyorsanız.

 Bu örnek, WCF istemci çerçevesinin dışından alınan bir SAML belirtecinin kullanılmasına izin veren bir özel belirteç sağlayıcısı oluşturmayı gösterir.

 Özetlemek gerekirse, bu örnek şunları gösterir:

- Bir istemcinin özel bir belirteç sağlayıcısıyla nasıl yapılandırılabileceğini.

- Bir SAML belirtecinin özel istemci kimlik bilgilerine nasıl geçirilebileceğini.

- SAML belirtecinin WCF istemci çerçevesine nasıl sağlandığı.

- Sunucunun, sunucunun X. 509.440 sertifikasını kullanarak istemci tarafından nasıl doğrulandığını.

 Hizmet, App.config yapılandırma dosyası kullanılarak tanımlanan hizmetle iletişim kurmak için iki uç nokta sunar. Her uç nokta bir adres, bağlama ve bir anlaşmada oluşur. Bağlama, Ileti güvenliği kullanan bir standart ile yapılandırılır `wsFederationHttpBinding` . Bir uç nokta, istemcinin simetrik bir kanıt anahtar kullanan bir SAML belirteci ile kimlik doğrulamasını, diğeri ise asimetrik bir kanıt anahtar kullanan bir SAML belirteci ile kimlik doğrulaması yapmasını bekler. Hizmet, davranışı kullanarak hizmet sertifikasını da yapılandırır `serviceCredentials` . `serviceCredentials`Davranış, bir hizmet sertifikası yapılandırmanıza olanak tanır. Hizmet sertifikası, istemci tarafından hizmetin kimliğini doğrulamak ve ileti koruması sağlamak için kullanılır. Aşağıdaki yapılandırma, bu konunun sonundaki Kurulum yönergelerinde açıklandığı şekilde, örnek kurulum sırasında yüklenen "localhost" sertifikasına başvurur. `serviceCredentials`Davranış, SAML belirteçlerini imzalamak için güvenilen sertifikaları yapılandırmanıza de olanak tanır. Aşağıdaki yapılandırma, örnek sırasında yüklenen ' Gamze ' sertifikasına başvurur.

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

 Aşağıdaki adımlarda, özel bir SAML belirteci sağlayıcısının nasıl geliştirilmesi ve WCF: güvenlik çerçevesi ile tümleştirme gösterilmektedir:

1. Özel bir SAML belirteci sağlayıcısı yazın.

     Örnek, oluşturma zamanında sağlanmış bir SAML onaylama işlemi temel alınarak bir güvenlik belirteci döndüren özel bir SAML belirteci sağlayıcısı uygular.

     Bu görevi gerçekleştirmek için, özel belirteç sağlayıcısı <xref:System.IdentityModel.Selectors.SecurityTokenProvider> sınıfından türetilir ve yöntemi geçersiz kılar <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> . Bu yöntem, oluşturur ve yeni bir döndürür `SecurityToken` .

    ```csharp
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

2. Özel güvenlik belirteci Yöneticisi yazın.

     <xref:System.IdentityModel.Selectors.SecurityTokenManager>Sınıfı, <xref:System.IdentityModel.Selectors.SecurityTokenProvider> <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> metoduna öğesine geçirilen belirli bir oluşturmak için kullanılır `CreateSecurityTokenProvider` . Belirteç kimlik doğrulaması ve belirteç seri hale getirici oluşturmak için bir güvenlik belirteci Yöneticisi de kullanılır, ancak bunlar bu örnek kapsamında değildir. Bu örnekte, özel güvenlik belirteci Yöneticisi <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> sınıfından devralır ve `CreateSecurityTokenProvider` geçilen BELIRTEÇ gereksinimleri SAML belirtecinin istendiğini GÖSTERIYORSA özel SAML belirteci sağlayıcısını döndürmek için yöntemi geçersiz kılar. İstemci kimlik bilgileri sınıfı (bkz. Adım 3) bir onaylama belirtmediğinden, güvenlik belirteci Yöneticisi uygun bir örnek oluşturur.

    ```csharp
    public class SamlSecurityTokenManager : ClientCredentialsSecurityTokenManager
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

3. Özel bir istemci kimlik bilgisi yazın.

     İstemci kimlik bilgileri sınıfı, istemci ara sunucusu için yapılandırılan kimlik bilgilerini temsil etmek için kullanılır ve belirteç kimlik doğrulaması, belirteç sağlayıcıları ve belirteç serileştiricisini almak için kullanılan bir güvenlik belirteci Yöneticisi oluşturur.

    ```csharp
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

4. İstemciyi özel istemci kimlik bilgilerini kullanacak şekilde yapılandırın.

     Örnek, varsayılan istemci kimlik bilgisi sınıfını siler ve istemcinin özel istemci kimlik bilgisini kullanabilmesi için yeni istemci kimlik bilgisi sınıfını sağlar.

    ```csharp
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

 Hizmette, arayanla ilişkili talepler görüntülenir. Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir. İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.

## <a name="setup-batch-file"></a>Toplu Iş dosyası kurulumu
 Bu örneğe eklenen Setup.bat Batch dosyası, sunucu sertifika tabanlı güvenlik gerektiren şirket içinde barındırılan bir uygulamayı çalıştırmak için sunucuyu ilgili sertifikayla yapılandırmanızı sağlar. Bu toplu iş dosyasının bilgisayarlarda çalışmak veya barındırılmayan bir durumda çalışması için değiştirilmesi gerekir.

 Aşağıdakiler, uygun yapılandırmada çalışacak şekilde değiştirilebilecek şekilde, toplu iş dosyalarının farklı bölümlerine kısa bir genel bakış sağlar.

- Sunucu sertifikası oluşturuluyor:

     Setup.bat Batch dosyasından aşağıdaki satırlar kullanılacak sunucu sertifikasını oluşturur. `%SERVER_NAME%`Değişken, sunucu adını belirtir. Kendi sunucu adınızı belirtmek için bu değişkeni değiştirin. Bu toplu iş dosyasındaki varsayılan değer localhost 'tur.

     Sertifika, LocalMachine depolama konumu altında (kişisel) deposunda depolanır.

    ```console
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss My -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- Sunucu sertifikasını istemcinin güvenilen sertifika deposuna yükleme:

     Setup.bat Batch dosyasındaki aşağıdaki satırlar, sunucu sertifikasını istemci güvenilir kişiler deposuna kopyalar. Makecert.exe tarafından oluşturulan sertifikalara istemci sistemi tarafından örtük olarak güvenilmediğinden Bu adım gereklidir. İstemci tarafından güvenilen kök sertifikada kök sertifikaya sahip bir sertifikanız zaten varsa (örneğin, Microsoft tarafından verilen bir sertifika), istemci sertifikası deposunu sunucu sertifikasıyla doldurmanın bu adımı gerektirmez.

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r LocalMachine -s TrustedPeople
    ```

- Veren sertifikası oluşturuluyor.

     Setup.bat Batch dosyasından aşağıdaki satırlar kullanılacak veren sertifikasını oluşturur. `%USER_NAME%`Değişken, verenin adını belirtir. Kendi verenin adını belirtmek için bu değişkeni değiştirin. Bu toplu iş dosyasındaki varsayılan değer gamze 'dir.

     Sertifika, CurrentUser Store konumu altında My deposunda depolanır.

    ```console
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr CurrentUser -ss My -a sha1 -n CN=%USER_NAME% -sky exchange -pe
    ```

- Verenin sertifikasını sunucunun Güvenilen sertifika deposuna yükleme.

     Setup.bat Batch dosyasındaki aşağıdaki satırlar, sunucu sertifikasını istemci güvenilir kişiler deposuna kopyalar. Makecert.exe tarafından oluşturulan sertifikalara istemci sistemi tarafından örtük olarak güvenilmediğinden Bu adım gereklidir. İstemci güvenilen kök sertifikasında kök sertifikaya sahip bir sertifikanız zaten varsa (örneğin, Microsoft tarafından verilen bir sertifika), sunucu sertifika deposunu veren sertifikaya doldurmanın bu adımı gerekli değildir.

    ```console
    certmgr.exe -add -r CurrentUser -s My -c -n %USER_NAME% -r LocalMachine -s TrustedPeople
    ```

#### <a name="to-set-up-and-build-the-sample"></a>Örneği ayarlamak ve derlemek için

1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.

2. Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)bölümündeki yönergeleri izleyin.

> [!NOTE]
> Bu örneğe yönelik yapılandırmayı yeniden oluşturmak için Svcutil.exe kullanıyorsanız, istemci yapılandırmasındaki uç nokta adını istemci koduyla eşleşecek şekilde değiştirdiğinizden emin olun.

#### <a name="to-run-the-sample-on-the-same-computer"></a>Örneği aynı bilgisayarda çalıştırmak için

1. Visual Studio 2012 komut isteminde örnek yükleme klasöründen yönetici ayrıcalıklarıyla Çalıştır Setup.bat çalıştırın. Bu, örneği çalıştırmak için gereken tüm sertifikaları kurar.

    > [!NOTE]
    > Setup.bat Batch dosyası bir Visual Studio 2012 komut Isteminden çalıştırılmak üzere tasarlanmıştır. Visual Studio 2012 komut Isteminde ayarlanan PATH ortam değişkeni, Setup.bat betiği için gereken yürütülebilir dosyaları içeren dizine işaret eder.  
  
2. Service\bin. 'den başlatma Service.exe  
  
3. \Client\bin. 'den başlatma Client.exe İstemci etkinliği istemci konsol uygulamasında görüntülenir.  
  
4. İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-run-the-sample-across-computers"></a>Örneği bilgisayarlar arasında çalıştırmak için  
  
1. Hizmet ikili dosyaları için hizmet bilgisayarında bir dizin oluşturun.  
  
2. Hizmet programı dosyalarını hizmet bilgisayarındaki hizmet dizinine kopyalayın. Ayrıca, Setup.bat ve Cleanup.bat dosyalarını hizmet bilgisayarına kopyalayın.  
  
3. Bilgisayarın tam etki alanı adını içeren konu adına sahip bir sunucu sertifikasına sahip olmanız gerekir. Service.exe.config dosyasının bu yeni sertifika adını yansıtması için güncelleştirilmeleri gerekir. Setup.bat Batch dosyasını değiştirerek sunucu sertifikası oluşturabilirsiniz. setup.bat dosyasının, yönetici ayrıcalıklarıyla açılmış bir Visual Studio için Geliştirici Komut İstemi çalıştırılması gerektiğini unutmayın. `%SERVER_NAME%`Değişkeni, hizmeti barındırmak için kullanılan bilgisayarın tam ana bilgisayar adına ayarlamanız gerekir.  
  
4. Sunucu sertifikasını istemcinin CurrentUser-Trustedkişilerim deposuna kopyalayın. Sunucu sertifikası, istemci güvenilir veren tarafından verildiğinde bu adım gerekli değildir.  
  
5. Hizmet bilgisayarındaki Service.exe.config dosyasında, temel adresin değerini localhost yerine tam nitelikli bir bilgisayar adı belirtecek şekilde değiştirin.  
  
6. Hizmet bilgisayarında, komut isteminden Service.exe çalıştırın.  
  
7. İstemci program dosyalarını dile özgü klasörün altındaki \client\bin\ klasöründen istemci bilgisayara kopyalayın.  
  
8. İstemci bilgisayardaki Client.exe.config dosyasında, uç noktanın adres değerini hizmetinizin yeni adresiyle eşleşecek şekilde değiştirin.  
  
9. İstemci bilgisayarda, `Client.exe` bir komut istemi penceresinden başlatın.  
  
10. İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-clean-up-after-the-sample"></a>Örnekten sonra temizlemek için  
  
1. Örneği çalıştırmayı bitirdikten sonra Samples klasöründe Cleanup.bat çalıştırın.
