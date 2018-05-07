---
title: SAML Belirteç Sağlayıcı
ms.date: 03/30/2017
ms.assetid: eb16e5e2-4c8d-4f61-a479-9c965fcec80c
ms.openlocfilehash: 56c432b0874f59fed87c0d892732422161d668ed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="saml-token-provider"></a>SAML Belirteç Sağlayıcı
Bu örnek, özel bir istemci SAML belirteç sağlayıcı uygulamak gösterilmiştir. Bir belirteç sağlayıcısı Windows Communication Foundation (WCF) güvenlik altyapısı için kimlik bilgileri sağladığını için kullanılır. Belirteç sağlayıcı genel hedef inceler ve böylece güvenlik altyapısı ileti güvenliğini sağlayabilirsiniz sorunları kimlik bilgileri gerekli. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Varsayılan kimlik bilgileri Yöneticisi belirteç sağlayıcısı birlikte verilir. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Ayrıca birlikte bir [!INCLUDE[infocard](../../../../includes/infocard-md.md)] belirteç sağlayıcısı. Özel belirteç sağlayıcılarını aşağıdaki durumlarda yararlı olur:  
  
-   Bu belirteci sağlayıcıları ile çalışamaz bir kimlik bilgisi deposu varsa.  
  
-   Kullanıcı ayrıntılarını geldiğinde sağladığında kimlik bilgilerini noktadan dönüştürme için kendi özel mekanizması sağlamak istiyorsanız [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci framework kimlik bilgilerini kullanır.  
  
-   Özel belirteç oluşturuluyorsa.  
  
 Bu örnek dışında alınan bir SAML belirtecine sağlayan özel bir belirteç sağlayıcısı oluşturmak nasıl göstermektedir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kullanılacak istemci framework.  
  
 Özetlemek için bu örnek şunlar gösterilmektedir:  
  
-   Nasıl bir istemci bir özel belirteç sağlayıcısı ile yapılandırılabilir.  
  
-   Nasıl bir SAML belirtecine için özel istemci kimlik bilgileri geçirilebilir.  
  
-   SAML belirteci için nasıl sağlandığını [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci framework.  
  
-   Sunucu sunucunun X.509 sertifikası kullanarak istemci tarafından kimlik doğrulamasının nasıl.  
  
 Hizmet App.config yapılandırma dosyası kullanılarak tanımlanmış hizmet ile iletişim için iki uç noktalarını kullanıma sunar. Her uç nokta bir adresi, bağlama ve bir sözleşme oluşur. Bağlama ile standart bir yapılandırılmış `wsFederationHttpBinding`, ileti güvenliği kullanır. Diğer asimetrik kanıtını anahtarı kullanan bir SAML belirteci ile kimlik doğrulaması için istemci beklediği sırada simetrik kanıt anahtarı kullanan bir SAML belirteci ile kimlik doğrulaması için istemci bir uç nokta bekler. Hizmetini kullanarak sertifika hizmetini de yapılandırır `serviceCredentials` davranışı. `serviceCredentials` Davranış bir hizmet sertifikası yapılandırmanıza olanak sağlar. Bir hizmet sertifikası, hizmetin kimliğini doğrulamak ve ileti koruma sağlamak için bir istemci tarafından kullanılır. Aşağıdaki yapılandırma, bu konunun sonunda kurulum yönergelerini açıklandığı gibi örnek Kurulum sırasında yüklü "localhost" Sertifika başvurur. `serviceCredentials` Davranışı de SAML belirteçleri imzalamak için güvenilir sertifikaları yapılandırmanıza olanak tanır. Aşağıdaki yapılandırma sırasında örnek yüklü 'Alice' sertifika başvurur.  
  
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
  
 Aşağıdaki adımlar, özel bir SAML belirteç sağlayıcı geliştirmek ve ile tümleştirmek nasıl gösterir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]: güvenlik framework:  
  
1.  Özel bir SAML belirteç sağlayıcı yazma.  
  
     Örnek oluşturma sırasında sağlanan bir SAML onayı temel alarak bir güvenlik belirteci verir bir özel SAML belirteç sağlayıcı uygular.  
  
     Bu görevi gerçekleştirmek için özel belirteç sağlayıcı türetildiği <xref:System.IdentityModel.Selectors.SecurityTokenProvider> sınıfı ve geçersiz kılmalar <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> yöntemi. Bu yöntem oluşturur ve yeni bir döndürür `SecurityToken`.  
  
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
  
2.  Özel güvenlik belirteci yöneticisi yazma.  
  
     <xref:System.IdentityModel.Selectors.SecurityTokenManager> Sınıfı oluşturmak için kullanılan <xref:System.IdentityModel.Selectors.SecurityTokenProvider> belirli <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> kendisine geçirilen `CreateSecurityTokenProvider` yöntemi. Bir güvenlik belirteci Yöneticisi ayrıca belirteç kimlik doğrulayan ve belirteci seri hale getirici oluşturmak için kullanılır, ancak bunlar Bu örnek tarafından kapsanmayan. Bu özel güvenlik belirteci yöneticisi devraldığı örnek <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> sınıfı ve geçersiz kılmalar `CreateSecurityTokenProvider` geçirilen belirteci gereksinimleri belirtmek özel SAML belirteç sağlayıcı SAML belirteci döndürülecek yöntemi istendi. İstemci kimlik bilgileri sınıfı (3. adıma bakın) bir onaylama belirtmediyse, güvenlik belirteci yöneticisi uygun bir örneğini oluşturur.  
  
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
  
3.  Özel istemci kimlik bilgilerini yazın.  
  
     İstemci kimlik bilgileri sınıfı istemci proxy için yapılandırılmış olan kimlik bilgilerini temsil etmek için kullanılır ve bir güvenlik belirteci Doğrulayıcı, belirteci sağlayıcıları ve belirteci seri hale getirici elde etmek için kullanılan belirteci yöneticisi oluşturur.  
  
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
  
4.  Özel istemci kimlik bilgisi kullanmak için istemciyi yapılandırın.  
  
     Örnek, varsayılan istemci kimlik bilgisi sınıfını siler ve istemci özel istemci kimlik bilgisi kullanabilmek için yeni istemci kimlik bilgisi sınıfını sağlar.  
  
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
  
 Hizmette arayanla ilişkili talep görüntülenir. Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir. İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.  
  
## <a name="setup-batch-file"></a>Toplu iş dosyası Kurulumu  
 Bu örnekle dahil Setup.bat toplu iş dosyası, sunucu sertifika tabanlı güvenlik gerektiren kendini barındıran bir uygulamayı çalıştırmak için ilgili sertifika ile sunucu yapılandırmanıza olanak sağlar. Bu toplu iş dosyası bilgisayarlar arasında iş ya da barındırılan olmayan bir durumda çalışması için değiştirilmesi gerekir.  
  
 Aşağıdakiler, böylece uygun yapılandırmada çalışacak biçimde değiştirilebilir toplu iş dosyaları farklı bölümlerini kısa bir genel bakış sağlar.  
  
-   Sunucu sertifikası oluşturuluyor:  
  
     Aşağıdaki satırları Setup.bat toplu iş dosyasından kullanılacak sunucu sertifikası oluşturun. `%SERVER_NAME%` Değişkeni, sunucu adını belirtir. Kendi sunucu adını belirtmek için bu değişkeni değiştirin. Localhost bu toplu iş dosyasında varsayılan değerdir.  
  
     Sertifika, LocalMachine depolama konumu altında (Kişisel) My deposunda saklanır.  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss My -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   Sunucu sertifikası istemcinin güvenilen sertifika deposuna yükleme:  
  
     İstemci güvenilir kişiler içine Setup.bat toplu dosya kopyalama sunucu sertifikasının aşağıdaki satırları depolar. MakeCert.exe tarafından oluşturulan sertifikaları örtük olarak istemci sistemi tarafından güvenilir değil çünkü bu adım gereklidir. Bir istemci güvenilen kök sertifikasını kökü belirtilmiş bir sertifikanız zaten varsa — örneğin, Microsoft tarafından verilen sertifika — sunucu sertifikasına sahip istemci sertifika deposunun doldurulması, bu adım gerekli değildir.  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r LocalMachine -s TrustedPeople  
    ```  
  
-   Sertifikayı veren sertifika oluşturuluyor.  
  
     Aşağıdaki satırları Setup.bat toplu iş dosyasından kullanılacak yayıncı sertifikası oluşturun. `%USER_NAME%` Değişkeni, sertifika veren adını belirtir. Kendi verenin adı belirtmek için bu değişkeni değiştirin. Alice bu toplu iş dosyasında varsayılan değerdir.  
  
     Sertifika Currentuser'a depolama konumu altında My deposunda saklanır.  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr CurrentUser -ss My -a sha1 -n CN=%USER_NAME% -sky exchange -pe  
    ```  
  
-   Sertifikayı sunucunun güvenilen sertifika deposuna yükleme.  
  
     İstemci güvenilir kişiler içine Setup.bat toplu dosya kopyalama sunucu sertifikasının aşağıdaki satırları depolar. MakeCert.exe tarafından oluşturulan sertifikaları örtük olarak istemci sistemi tarafından güvenilir değil çünkü bu adım gereklidir. Bir istemci güvenilen kök sertifikasını kökü belirtilmiş bir sertifikanız zaten varsa — örneğin, Microsoft tarafından verilen sertifika — sunucu sertifika depolama veren sertifika ile doldurma, bu adım gerekli değildir.  
  
    ```  
    certmgr.exe -add -r CurrentUser -s My -c -n %USER_NAME% -r LocalMachine -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-and-build-the-sample"></a>Ayarlamak ve örneği oluşturmak için  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözümü derlemek için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
> [!NOTE]
>  Bu örnek için yapılandırmayı yeniden oluşturmak için Svcutil.exe kullanırsanız, istemci kodu eşleşecek şekilde istemci yapılandırmasında uç nokta adı değiştirdiğinizden emin olun.  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a>Aynı bilgisayara örneği çalıştırmak için  
  
1.  Örnek yükleme klasöründen içinde Setup.bat çalıştırmak bir [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemini yönetici ayrıcalıklarıyla çalıştırın. Bu örneği çalıştırmak için gerekli tüm sertifikalar yükler.  
  
    > [!NOTE]
    >  Setup.bat toplu iş dosyası çalıştırılmak üzere tasarlanmış bir [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemi. İçinde PATH ortam değişkeni ayarlamak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemi Setup.bat komut dosyası için gereken yürütülebilir dosyalar içeren dizine işaret eder.  
  
2.  Service.exe service\bin başlatın.  
  
3.  Client.exe \client\bin başlatın. İstemci etkinliği istemci konsol uygulaması görüntülenir.  
  
4.  İstemci ve hizmet iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-run-the-sample-across-computers"></a>Bilgisayarlar arasında örneği çalıştırmak için  
  
1.  Hizmet ikili dosyaları hizmet bilgisayarda bir dizin oluşturun.  
  
2.  Hizmet program dosyalarını hizmeti bilgisayarında hizmet dizinine kopyalayın. Ayrıca Setup.bat ve Cleanup.bat dosyalarını hizmet bilgisayara kopyalayın.  
  
3.  Bilgisayarın tam etki alanı adını içeren konu adına sahip bir sunucu sertifikası olmalıdır. Service.exe.config dosyayı bu yeni sertifika adını yansıtacak şekilde güncelleştirmeniz gerekir. Sunucu sertifikası Setup.bat toplu iş dosyasını değiştirerek oluşturabilirsiniz. Setup.bat dosyasını yönetici ayrıcalıklarıyla açılmış bir Visual Studio komut istemi penceresinde çalıştırmanız gerektiğini unutmayın. Ayarlamalısınız `%SERVER_NAME%` değişken hizmet barındırmak için kullanılan bilgisayarın ana bilgisayar tam adı.  
  
4.  Sunucu sertifikası istemci Currentuser'a TrustedPeople depolama alanına kopyalayın. Sunucu sertifikasının güvenilen istemci veren tarafından verildiğinde bu adım gerekli değildir.  
  
5.  Hizmeti bilgisayarında Service.exe.config dosyasında localhost yerine bir tam bilgisayar adını belirtmek için taban adresi değerini değiştirin.  
  
6.  Hizmet bilgisayarda Service.exe bir komut isteminden çalıştırın.  
  
7.  İstemci program dosyaları \client\bin\ klasöründen dile özgü klasörü altında istemci bilgisayara kopyalayın.  
  
8.  İstemci bilgisayardaki Client.exe.config dosyasında yeni adresi hizmetinizin eşleştirmek için uç nokta adresi değerini değiştirin.  
  
9. İstemci bilgisayarda, başlatma `Client.exe` bir komut istemi penceresinden.  
  
10. İstemci ve hizmet iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-clean-up-after-the-sample"></a>Örnek sonra temizlemek için  
  
1.  Örnek çalıştıran tamamladıktan sonra Cleanup.bat samples klasöründen çalıştırın.  
  
## <a name="see-also"></a>Ayrıca Bkz.
