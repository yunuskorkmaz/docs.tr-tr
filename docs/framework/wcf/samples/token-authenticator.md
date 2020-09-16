---
title: Belirteç Kimlik Doğrulayıcı
ms.date: 03/30/2017
ms.assetid: 84382f2c-f6b1-4c32-82fa-aebc8f6064db
ms.openlocfilehash: a493ea48d9d339c0bc1a4b191b084374ad5f2dc4
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90548598"
---
# <a name="token-authenticator"></a>Belirteç Kimlik Doğrulayıcı
Bu örnek, bir özel belirteç kimlik doğrulayıcısının nasıl uygulanacağını gösterir. Windows Communication Foundation (WCF) ' deki bir belirteç kimlik doğrulayıcısı, iletiyle kullanılan belirteci doğrulamak, kendinden tutarlı olduğunu doğrulamak ve belirteçle ilişkili kimliğin kimlik doğrulamasını yapmak için kullanılır.

 Özel belirteç kimlik doğrulayıcılar çeşitli durumlarda yararlı olur, örneğin:

- Bir belirteçle ilişkili varsayılan kimlik doğrulama mekanizmasını geçersiz kılmak istediğinizde.

- Özel bir belirteç oluştururken.

 Bu örnek şunları gösterir:

- Bir istemcinin Kullanıcı adı/parola çifti kullanarak kimlik doğrulaması yapabilir.

- Sunucu, özel bir belirteç kimlik doğrulayıcısı kullanarak istemci kimlik bilgilerini nasıl doğrulayabilirler.

- WCF hizmeti kodu, özel belirteç kimlik doğrulayıcısı ile nasıl bir şekilde yapılır.

- Sunucunun X. 509.440 sertifikası kullanılarak nasıl kimlik doğrulaması yapılabilir.

 Bu örnek ayrıca, özel belirteç kimlik doğrulama işleminden sonra arayanın kimliğinin WCF 'den nasıl erişilebilir olduğunu gösterir.

 Hizmet, App.config yapılandırma dosyası kullanılarak tanımlanan hizmetle iletişim kurmak için tek bir uç nokta sunar. Uç nokta bir adres, bağlama ve bir anlaşmada oluşur. Bağlama, `wsHttpBinding` güvenlik modunun ileti olarak ayarlandığı bir standart ile yapılandırılır. varsayılan modu `wsHttpBinding` . Bu örnek, standart `wsHttpBinding` istemci Kullanıcı adı kimlik doğrulamasını kullanmak için standardı ayarlar. Hizmet, davranışı kullanarak hizmet sertifikasını da yapılandırır `serviceCredentials` . `securityCredentials`Davranış, bir hizmet sertifikası belirtmenize olanak tanır. Hizmet sertifikası, istemci tarafından hizmetin kimliğini doğrulamak ve ileti koruması sağlamak için kullanılır. Aşağıdaki yapılandırma, aşağıdaki kurulum yönergelerinde açıklandığı gibi örnek kurulum sırasında yüklü olan localhost sertifikasına başvurur.

```xml
<system.serviceModel>
    <services>
      <service
          name="Microsoft.ServiceModel.Samples.CalculatorService"
          behaviorConfiguration="CalculatorServiceBehavior">
        <host>
          <baseAddresses>
            <!-- configure base address provided by host -->
            <add baseAddress ="http://localhost:8000/servicemodelsamples/service" />
          </baseAddresses>
        </host>
        <!-- use base address provided by host -->
        <endpoint address=""
                  binding="wsHttpBinding"
                  bindingConfiguration="Binding1"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />
      </service>
    </services>

    <bindings>
      <wsHttpBinding>
        <binding name="Binding1">
          <security mode="Message">
            <message clientCredentialType="UserName" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>

    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceDebug includeExceptionDetailInFaults="False" />
          <!--
          The serviceCredentials behavior allows one to define a service certificate.
          A service certificate is used by a client to authenticate the service and provide message protection.
          This configuration references the "localhost" certificate installed during the setup instructions.
....        -->
          <serviceCredentials>
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />
          </serviceCredentials>
        </behavior>
      </serviceBehaviors>
    </behaviors>

  </system.serviceModel>
```

 İstemci uç noktası yapılandırması, bir yapılandırma adından, hizmet uç noktası için mutlak bir adresten, bağlamaya ve sözleşmeyle oluşur. İstemci bağlama, uygun ve ile yapılandırılır `Mode` `clientCredentialType` .

```xml
<system.serviceModel>
    <client>
      <endpoint name=""
                address="http://localhost:8000/servicemodelsamples/service"
                binding="wsHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator">
      </endpoint>
    </client>

    <bindings>
      <wsHttpBinding>
        <binding name="Binding1">
          <security mode="Message">
            <message clientCredentialType="UserName" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
  </system.serviceModel>
```

 İstemci uygulama, kullanılacak kullanıcı adını ve parolayı ayarlar.

```csharp
static void Main()
{
     ...
     client.ClientCredentials.UserNamePassword.UserName = username;
     client.ClientCredentials.UserNamePassword.Password = password;
     ...
}
```

## <a name="custom-token-authenticator"></a>Özel belirteç kimlik doğrulayıcısı
 Özel bir belirteç kimlik doğrulayıcısı oluşturmak için aşağıdaki adımları kullanın:

1. Özel bir belirteç kimlik doğrulayıcısı yazın.

     Örnek, Kullanıcı adının geçerli bir e-posta biçimine sahip olduğunu doğrulayan bir özel belirteç Authenticator uygular. Türetir <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator> . Bu sınıftaki en önemli Yöntem <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator.ValidateUserNamePasswordCore%28System.String%2CSystem.String%29> . Bu yöntemde, Authenticator Kullanıcı adının biçimini doğrular ve ana bilgisayar adının sahte bir etki alanından olmaması gerekir. Her iki koşul de karşılanıyorsa, daha sonra <xref:System.IdentityModel.Policy.IAuthorizationPolicy> Kullanıcı adı belirtecinin içinde depolanan bilgileri temsil eden talepler sağlamak için kullanılan, salt okunurdur bir örnek koleksiyonu döndürür.

    ```csharp
    protected override ReadOnlyCollection<IAuthorizationPolicy> ValidateUserNamePasswordCore(string userName, string password)
    {
        if (!ValidateUserNameFormat(userName))
            throw new SecurityTokenValidationException("Incorrect UserName format");

        ClaimSet claimSet = new DefaultClaimSet(ClaimSet.System, new Claim(ClaimTypes.Name, userName, Rights.PossessProperty));
        List<IIdentity> identities = new List<IIdentity>(1);
        identities.Add(new GenericIdentity(userName));
        List<IAuthorizationPolicy> policies = new List<IAuthorizationPolicy>(1);
        policies.Add(new UnconditionalPolicy(ClaimSet.System, claimSet, DateTime.MaxValue.ToUniversalTime(), identities));
        return policies.AsReadOnly();
    }
    ```

2. Özel belirteç kimlik doğrulayıcısı tarafından döndürülen bir yetkilendirme ilkesi sağlayın.

     Bu örnek, <xref:System.IdentityModel.Policy.IAuthorizationPolicy> `UnconditionalPolicy` Oluşturucusu içinde kendisine geçirilmiş talepler ve kimlikler kümesi döndüren çağrılan öğesinin kendi uygulamasını sağlar.

    ```csharp
    class UnconditionalPolicy : IAuthorizationPolicy
    {
        String id = Guid.NewGuid().ToString();
        ClaimSet issuer;
        ClaimSet issuance;
        DateTime expirationTime;
        IList<IIdentity> identities;

        public UnconditionalPolicy(ClaimSet issuer, ClaimSet issuance, DateTime expirationTime, IList<IIdentity> identities)
        {
            if (issuer == null)
                throw new ArgumentNullException("issuer");
            if (issuance == null)
                throw new ArgumentNullException("issuance");

            this.issuer = issuer;
            this.issuance = issuance;
            this.identities = identities;
            this.expirationTime = expirationTime;
        }

        public string Id
        {
            get { return this.id; }
        }

        public ClaimSet Issuer
        {
            get { return this.issuer; }
        }

        public DateTime ExpirationTime
        {
            get { return this.expirationTime; }
        }

        public bool Evaluate(EvaluationContext evaluationContext, ref object state)
        {
            evaluationContext.AddToTarget(this, this.issuance);

            if (this.identities != null)
            {
                object value;
                IList<IIdentity> contextIdentities;
                if (!evaluationContext.Properties.TryGetValue("Identities", out value))
                {
                    contextIdentities = new List<IIdentity>(this.identities.Count);
                    evaluationContext.Properties.Add("Identities", contextIdentities);
                }
                else
                {
                    contextIdentities = value as IList<IIdentity>;
                }
                foreach (IIdentity identity in this.identities)
                {
                    contextIdentities.Add(identity);
                }
            }

            evaluationContext.RecordExpirationTime(this.expirationTime);
            return true;
        }
    }
    ```

3. Özel bir güvenlik belirteci Yöneticisi yazın.

     , <xref:System.IdentityModel.Selectors.SecurityTokenManager> <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> Yöntemi içinde kendisine geçirilen belirli nesneler için bir oluşturmak için kullanılır `CreateSecurityTokenAuthenticator` . Güvenlik belirteci Yöneticisi ayrıca belirteç sağlayıcıları ve belirteç serileştiricileri oluşturmak için kullanılır, ancak bunlar bu örnek tarafından kapsanmaz. Bu örnekte, özel güvenlik belirteci Yöneticisi <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> sınıfından devralır ve `CreateSecurityTokenAuthenticator` geçilen belirteç gereksinimleri Kullanıcı adı Doğrulayıcı 'nın istendiğini gösteriyorsa özel Kullanıcı adı belirteç kimlik doğrulayıcısı döndürecek şekilde yöntemi geçersiz kılar.

    ```csharp
    public class MySecurityTokenManager : ServiceCredentialsSecurityTokenManager
    {
        MyUserNameCredential myUserNameCredential;

        public MySecurityTokenManager(MyUserNameCredential myUserNameCredential)
            : base(myUserNameCredential)
        {
            this.myUserNameCredential = myUserNameCredential;
        }

        public override SecurityTokenAuthenticator CreateSecurityTokenAuthenticator(SecurityTokenRequirement tokenRequirement, out SecurityTokenResolver outOfBandTokenResolver)
        {
            if (tokenRequirement.TokenType ==  SecurityTokenTypes.UserName)
            {
                outOfBandTokenResolver = null;
                return new MyTokenAuthenticator();
            }
            else
            {
                return base.CreateSecurityTokenAuthenticator(tokenRequirement, out outOfBandTokenResolver);
            }
        }
    }
    ```

4. Özel bir hizmet kimlik bilgisi yazın.

     Hizmet kimlik bilgileri sınıfı, hizmet için yapılandırılan kimlik bilgilerini temsil etmek için kullanılır ve belirteç doğrulayıcılar, belirteç sağlayıcıları ve belirteç serileştiricileri elde etmek için kullanılan bir güvenlik belirteci Yöneticisi oluşturur.

    ```csharp
    public class MyUserNameCredential : ServiceCredentials
    {

        public MyUserNameCredential()
            : base()
        {
        }

        protected override ServiceCredentials CloneCore()
        {
            return new MyUserNameCredential();
        }

        public override SecurityTokenManager CreateSecurityTokenManager()
        {
            return new MySecurityTokenManager(this);
        }

    }
    ```

5. Hizmeti özel hizmet kimlik bilgilerini kullanacak şekilde yapılandırın.

     Hizmetin özel hizmet kimlik bilgisini kullanabilmesi için varsayılan hizmet kimlik bilgilerinde önceden yapılandırılmış hizmet sertifikasını yakaladıktan sonra varsayılan hizmet kimlik bilgisi sınıfını siler ve yeni hizmet kimlik bilgisi örneğini önceden yapılandırılmış hizmet sertifikalarını kullanacak şekilde yapılandırır ve bu yeni hizmet kimlik bilgileri örneğini hizmet davranışlarına ekler.

    ```csharp
    ServiceCredentials sc = serviceHost.Credentials;
    X509Certificate2 cert = sc.ServiceCertificate.Certificate;
    MyUserNameCredential serviceCredential = new MyUserNameCredential();
    serviceCredential.ServiceCertificate.Certificate = cert;
    serviceHost.Description.Behaviors.Remove((typeof(ServiceCredentials)));
    serviceHost.Description.Behaviors.Add(serviceCredential);
    ```

 Arayanın bilgilerini göstermek için <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> aşağıdaki kodda gösterildiği gibi kullanabilirsiniz. , <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> Geçerli çağıran ile ilgili talep bilgilerini içerir.

```csharp
static void DisplayIdentityInformation()
{
    Console.WriteLine("\t\tSecurity context identity  :  {0}",
            ServiceSecurityContext.Current.PrimaryIdentity.Name);
     return;
}
```

 Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir. İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.

## <a name="setup-batch-file"></a>Toplu Iş dosyası kurulumu
 Bu örneğe eklenen Setup.bat Batch dosyası, sunucu sertifikası tabanlı güvenlik gerektiren şirket içinde barındırılan bir uygulamayı çalıştırmak için sunucuyu ilgili sertifikalarla yapılandırmanıza olanak tanır. Bu toplu iş dosyasının bilgisayarlarda çalışmak veya barındırılmayan bir durumda çalışması için değiştirilmesi gerekir.

 Aşağıdakiler, uygun yapılandırmada çalışacak şekilde değiştirilebilecek şekilde, toplu iş dosyalarının farklı bölümlerine kısa bir genel bakış sağlar.

- Sunucu sertifikası oluşturuluyor.

     Setup.bat Batch dosyasından aşağıdaki satırlar kullanılacak sunucu sertifikasını oluşturur. `%SERVER_NAME%`Değişken, sunucu adını belirtir. Kendi sunucu adınızı belirtmek için bu değişkeni değiştirin. Bu toplu iş dosyasındaki varsayılan değer localhost 'tur.

    ```console
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- Sunucu sertifikasını istemcinin güvenilen sertifika deposuna yükleme.

     Setup.bat Batch dosyasındaki aşağıdaki satırlar, sunucu sertifikasını istemci güvenilir kişiler deposuna kopyalar. Makecert.exe tarafından oluşturulan sertifikalara istemci sistemi tarafından örtük olarak güvenilmediğinden Bu adım gereklidir. İstemci tarafından güvenilen kök sertifikada kök sertifikaya sahip bir sertifikanız zaten varsa (örneğin, Microsoft tarafından verilen bir sertifika), istemci sertifikası deposunu sunucu sertifikasıyla doldurmanın bu adımı gerektirmez.

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

    > [!NOTE]
    > Kurulum Batch dosyası bir Windows SDK komut Isteminden çalıştırılmak üzere tasarlanmıştır. MSSDK ortam değişkeninin, SDK 'nın yüklü olduğu dizine işaret olmasını gerektirir. Bu ortam değişkeni bir Windows SDK komut Istemi içinde otomatik olarak ayarlanır.

#### <a name="to-set-up-and-build-the-sample"></a>Örneği ayarlamak ve derlemek için

1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.

2. Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)bölümündeki yönergeleri izleyin.

#### <a name="to-run-the-sample-on-the-same-computer"></a>Örneği aynı bilgisayarda çalıştırmak için

1. Setup.bat, yönetici ayrıcalıklarıyla açılmış bir Visual Studio 2012 komut istemi içindeki örnek yükleme klasöründen çalıştırın. Bu, örneği çalıştırmak için gereken tüm sertifikaları kurar.

    > [!NOTE]
    > Setup.bat Batch dosyası bir Visual Studio 2012 komut Isteminden çalıştırılmak üzere tasarlanmıştır. Visual Studio 2012 komut Isteminde ayarlanan PATH ortam değişkeni, Setup.bat betiği için gereken yürütülebilir dosyaları içeren dizine işaret eder.  
  
2. Service\bin. 'den başlatma service.exe  
  
3. \Client\bin. 'den başlatma client.exe İstemci etkinliği istemci konsol uygulamasında görüntülenir.  
  
4. İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-run-the-sample-across-computers"></a>Örneği bilgisayarlar arasında çalıştırmak için  
  
1. Hizmet ikili dosyaları için hizmet bilgisayarında bir dizin oluşturun.  
  
2. Hizmet programı dosyalarını hizmet bilgisayarındaki hizmet dizinine kopyalayın. Ayrıca, Setup.bat ve Cleanup.bat dosyalarını hizmet bilgisayarına kopyalayın.  
  
3. Bilgisayarın tam etki alanı adını içeren konu adına sahip bir sunucu sertifikasına sahip olmanız gerekir. Service App.config dosyasının bu yeni sertifika adını yansıtması için güncelleştirilmeleri gerekir. `%SERVER_NAME%`Değişkeni Hizmetin çalıştırılacağı bilgisayarın tam ana bilgisayar adı olarak ayarlarsanız, Setup.bat kullanarak bir tane oluşturabilirsiniz. setup.bat dosyasının, yönetici ayrıcalıklarıyla açılan bir Visual Studio için Geliştirici Komut İstemi çalıştırılması gerektiğini unutmayın.  
  
4. Sunucu sertifikasını istemcinin CurrentUser-Trustedkişilerim deposuna kopyalayın. Sunucu sertifikasının, istemci güvenilir veren tarafından verildiği durumlar dışında bunu yapmanız gerekmez.  
  
5. Hizmet bilgisayarındaki App.config dosyasında, temel adresin değerini localhost yerine tam nitelikli bir bilgisayar adı belirtecek şekilde değiştirin.  
  
6. Hizmet bilgisayarında, komut isteminden service.exe çalıştırın.  
  
7. İstemci program dosyalarını dile özgü klasörün altındaki \client\bin\ klasöründen istemci bilgisayara kopyalayın.  
  
8. İstemci bilgisayardaki Client.exe.config dosyasında, uç noktanın adres değerini hizmetinizin yeni adresiyle eşleşecek şekilde değiştirin.  
  
9. İstemci bilgisayarda, bir komut isteminden Client.exe başlatın.  
  
10. İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-clean-up-after-the-sample"></a>Örnekten sonra temizlemek için  
  
1. Örneği çalıştırmayı bitirdikten sonra Samples klasöründe Cleanup.bat çalıştırın.
