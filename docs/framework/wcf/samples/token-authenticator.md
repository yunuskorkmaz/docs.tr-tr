---
title: Belirteç Kimlik Doğrulayıcı
ms.date: 03/30/2017
ms.assetid: 84382f2c-f6b1-4c32-82fa-aebc8f6064db
ms.openlocfilehash: 198994acb322ece374ba0e04bc4d15cb2754f995
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48582651"
---
# <a name="token-authenticator"></a>Belirteç Kimlik Doğrulayıcı
Bu örnek nasıl özel bir belirteç kimlik doğrulayıcısı uygulanacağını gösterir. Belirteç kimlik doğrulayıcısı Windows Communication Foundation (WCF) ileti ile kullanılan belirteci doğrulamak için tutarlı ve kimlik doğrulama belirteciyle ilişkili doğrulama kullanılır.

 Özel belirteç Doğrulayıcı gibi çeşitli durumlarda kullanışlıdır:

-   Geçersiz bir belirteç ile ilişkili varsayılan kimlik doğrulama mekanizması istediğinizde.

-   Ne zaman özel bir simge oluşturuyorsunuz.

 Bu örnek aşağıdaki gösterir:

-   Nasıl bir istemci bir kullanıcı adı/parola çifti kullanarak kimlik doğrulaması yapabilir.

-   Sunucu, özel bir belirteç kimlik doğrulayıcısı kullanarak istemci kimlik bilgileri nasıl doğrulayabilirsiniz.

-   Nasıl özel bir belirteç kimlik doğrulayıcısı oturum WCF hizmet kodunun bağlar.

-   Sunucu, sunucunun X.509 sertifikası kullanılarak doğrulanabilir nasıl.

 Ayrıca bu örnek nasıl çağıranının kimliğini özel belirteç kimlik doğrulama işleminden sonra WCF erişilebilir gösterir.

 Hizmet, App.config yapılandırma dosyası kullanılarak tanımlanmış hizmet ile iletişim kurmak için tek bir uç noktayı kullanıma sunar. Uç nokta, adres, bağlama ve bir sözleşme oluşur. Bir standart yapılandırılmış bağlama `wsHttpBinding`, güvenlik modu iletiye - varsayılan modu ayarlandığında `wsHttpBinding`. Bu örnek, standart ayarlar `wsHttpBinding` istemci kullanıcı adı kimlik doğrulaması kullanmak için. Hizmet Ayrıca hizmet kullanarak sertifikayı yapılandırır `serviceCredentials` davranışı. `securityCredentials` Davranışı, bir hizmet sertifikası belirtmenize olanak sağlar. Bir hizmet sertifikası, hizmet kimlik doğrulaması ve ileti koruma sağlamak için bir istemci tarafından kullanılır. Aşağıdaki yapılandırmayı aşağıdaki Kurulum yönergelerinde açıklandığı gibi örnek Kurulum sırasında yüklenen localhost sertifikasına başvuruda bulunuyor.

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

 İstemci uç nokta yapılandırması mutlak bir adres için hizmet uç noktası, bağlama ve sözleşmenin bir yapılandırma adı oluşur. Bağlama istemcinin uygun olarak yapılandırıldığı `Mode` ve `clientCredentialType`.

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

 İstemci uygulaması, kullanıcı adını ve parolayı ayarlar.

```
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

1.  Özel bir belirteç kimlik doğrulayıcısı yazın.

     Örnek, kullanıcı adı geçerli bir e-posta biçiminde olduğunu doğrulama özel bir belirteç Doğrulayıcı uygular. Bunu türetilen <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator>. Bu sınıftaki en önemli yöntemdir <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator.ValidateUserNamePasswordCore%28System.String%2CSystem.String%29>. Bu yöntemde, Doğrulayıcı biçimini doğrular. kullanıcı adı ve bu da konak adı bir dolandırıcı etki alanına ait değil. Her iki koşullar sonra salt okunur bir koleksiyonunu döndürür <xref:System.IdentityModel.Policy.IAuthorizationPolicy> örnekleriyle sonra kullanıcı adı belirteci içinde depolanan bilgileri temsil eden talep sağlamak için kullanılır.

    ```
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

2.  Özel belirteç kimlik doğrulayıcısı tarafından döndürülen bir yetkilendirme ilkesi belirtin.

     Bu örnek, kendi uygulamasını sağlar <xref:System.IdentityModel.Policy.IAuthorizationPolicy> adlı `UnconditionalPolicy` talepler ve oluşturucusunda kendisine iletilmiş kimlikleri kümesi döndürür.

    ```
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

3.  Bir özel güvenlik belirteci Yöneticisi'ni yazın.

     <xref:System.IdentityModel.Selectors.SecurityTokenManager> Oluşturmak için kullanılan bir <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> belirli <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> kendisine geçirilen nesneleri `CreateSecurityTokenAuthenticator` yöntemi. Güvenlik belirteci Yöneticisi ayrıca belirteci sağlayıcıları ve belirteci seri hale getiricileri genişletme oluşturmak için kullanılır, ancak bunlar Bu örnek tarafından kapsanmaz. Bu örnekte, özel güvenlik belirteci yöneticisi devraldığı <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> sınıf ve geçersiz kılmaları `CreateSecurityTokenAuthenticator` geçirilen belirteci gereksinimleri, kullanıcı adı kimlik doğrulayıcı belirttiğinizde, özel kullanıcı adı belirteci kimlik doğrulayıcı döndürülecek yöntemi istendi.

    ```
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

4.  Bir özel hizmet kimlik bilgilerini yazın.

     Hizmet kimlik bilgilerini sınıfı, hizmet için yapılandırılmış kimlik bilgilerini temsil etmek için kullanılır ve bir güvenlik belirteci kimlik doğrulayıcılar, belirteç sağlayıcıları ve belirteci seri hale getiricileri genişletme elde etmek için kullanılan belirteci yöneticisi oluşturur.

    ```
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

5.  Hizmetini özel hizmet kimlik bilgilerini kullanacak şekilde yapılandırın.

     Özel hizmet kimlik bilgisi kullanmak için hizmet için sırasıyla biz varsayılan hizmet kimlik bilgisi sınıfı zaten varsayılan hizmet kimlik bilgisi önceden yapılandırılmış olan hizmet sertifikası yakaladıktan sonra silin ve yeni hizmet kimlik bilgilerini yapılandırma önceden yapılandırılmış hizmet sertifikalarını kullanın ve bu yeni hizmet kimlik bilgisi örneği için hizmet davranışları eklemek için örneği.

    ```
    ServiceCredentials sc = serviceHost.Credentials;
    X509Certificate2 cert = sc.ServiceCertificate.Certificate;
    MyUserNameCredential serviceCredential = new MyUserNameCredential();
    serviceCredential.ServiceCertificate.Certificate = cert;
    serviceHost.Description.Behaviors.Remove((typeof(ServiceCredentials)));
    serviceHost.Description.Behaviors.Add(serviceCredential);
    ```

 Arayanın bilgileri görüntülemek için kullanabileceğiniz <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> aşağıdaki kodda gösterildiği gibi. <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> Talep geçerli arayanı hakkında bilgi içerir.

```
static void DisplayIdentityInformation()
{
    Console.WriteLine("\t\tSecurity context identity  :  {0}",
            ServiceSecurityContext.Current.PrimaryIdentity.Name);
     return;
}
```

 Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir. İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.

## <a name="setup-batch-file"></a>Kurulum toplu iş dosyası
 Bu örnekle dahil Setup.bat toplu iş dosyası, sunucunun server gerektiren şirket içinde barındırılan bir uygulamayı çalıştırmak için ilgili sertifikalarla yapılandırmak için sertifika tabanlı güvenlik sağlar. Bu toplu iş dosyası bilgisayarlarda çalışmaya veya barındırılan olmayan bir durumda çalışması için değiştirilmesi gerekir.

 Aşağıda, böylece uygun yapılandırmasında çalıştırılacak değiştirilebilir toplu iş dosyaları farklı bölümlerini kısa bir genel bakış sağlar.

-   Sunucu sertifikası oluşturuluyor.

     Setup.bat toplu iş dosyasından aşağıdaki satırları kullanılacak sunucu sertifikası oluşturun. `%SERVER_NAME%` Değişkeni, sunucu adını belirtir. Kendi sunucu adını belirtmek için bu değişkeni değiştirin. Bu toplu iş dosyasında localhost varsayılandır.

    ```
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

-   Sunucu sertifikasını istemcinin güvenilen sertifika depolama alanına yükleniyor.

     İstemci güvenilir kişiler uygulamasına Setup.bat toplu dosya kopyalama sunucu sertifikasının aşağıdaki satırları depolayın. MakeCert.exe tarafından oluşturulan sertifikaları örtük olarak istemci sistemi tarafından güvenilir değildir çünkü bu adım gereklidir. Bir istemci güvenilen kök sertifikayı kök erişim izni verilmiş bir sertifika zaten varsa — örneğin, Microsoft tarafından verilen sertifika — sunucu sertifikasında istemci sertifika deposunun doldurulması, bu adım gerekli değildir.

    ```
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

    > [!NOTE]
    >  Kurulum toplu iş dosyası, bir Windows SDK Komut İstemi'nden çalıştırılmak üzere tasarlanmıştır. MSSDK ortam değişkeni'nın SDK'ın yüklendiği dizini gösterecek gerektiriyor. Bu ortam değişkeni, bir Windows SDK komut istemi içinde otomatik olarak ayarlanır.

#### <a name="to-set-up-and-build-the-sample"></a>Ayarlama ve örneği oluşturmak için

1.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2.  Çözümü derlemek için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).

#### <a name="to-run-the-sample-on-the-same-computer"></a>Örneği aynı bilgisayarda çalıştırmak için

1.  Visual Studio 2012 komut istemini yönetici ayrıcalıklarıyla açılan içinde örnek yükleme klasöründen Setup.bat çalıştırın. Bu örneği çalıştırmak için gerekli olan tüm sertifikaları yükler.

    > [!NOTE]
    >  Setup.bat toplu iş dosyası, bir Visual Studio 2012 komut isteminden çalıştırılması için tasarlanmıştır. PATH ortam değişkenine içinde Visual Studio 2012 komut istemi noktaları Setup.bat betiği tarafından gereken yürütülebilir dosyaları içeren dizine ayarlayın.  
  
2.  Service.exe service\bin'nden başlatın.  
  
3.  Client.exe \client\bin'nden başlatın. İstemci etkinliği istemci konsol uygulamasında görüntülenir.  
  
4.  İstemci ve hizmet iletişim kurabildiğini bilmiyorsanız bkz [sorun giderme ipuçları](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-run-the-sample-across-computers"></a>Bilgisayarlar arasında örneği çalıştırmak için  
  
1.  Hizmet ikili dosyaları için hizmet bilgisayarda bir dizin oluşturun.  
  
2.  Hizmet program dosyaları hizmeti bilgisayarında hizmet dizinine kopyalayın. Ayrıca Setup.bat ve Cleanup.bat dosyaları hizmet bilgisayara kopyalayın.  
  
3.  Bilgisayarın tam etki alanı adını içeren konu adına sahip bir sunucu sertifikası olmalıdır. Hizmet App.config dosyası, bu yeni sertifika adı yansıtacak şekilde güncelleştirilmesi gerekir. Ayarlarsanız Setup.bat kullanarak bir tane oluşturabilirsiniz `%SERVER_NAME%` hizmet çalışacağı bilgisayarda tam ana bilgisayar adı için değişken. Setup.bat dosyasının yönetici ayrıcalıklarıyla açılan bir Visual Studio komut isteminden çalıştırmanız gerektiğini unutmayın.  
  
4.  Sunucu sertifikasını istemcinin CurrentUser TrustedPeople depoya kopyalayın. Sunucu sertifikası olduğunda istemci güvenilen veren tarafından verilen dışında bunu gerekmez.  
  
5.  Hizmet bilgisayarı App.config dosyasında localhost yerine tam bilgisayar adını belirtmek için temel adresini değiştirin.  
  
6.  Hizmet bilgisayarda service.exe bir komut isteminden çalıştırın.  
  
7.  İstemci program dosyaları \client\bin\ klasöründen dile özgü klasörünün altındaki istemci bilgisayara kopyalayın.  
  
8.  İstemci bilgisayarda Client.exe.config dosyasında hizmetinizin yeni adresiyle eşleşecek şekilde uç nokta adresi değiştirin.  
  
9. İstemci bilgisayarda bir komut istemi'nden Client.exe başlatın.  
  
10. İstemci ve hizmet iletişim kurabildiğini bilmiyorsanız bkz [sorun giderme ipuçları](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-clean-up-after-the-sample"></a>Sonra örnek temizlemek için  
  
1.  Bu örneği çalıştırmadan tamamladıktan sonra Cleanup.bat samples klasöründe çalıştırın.  
  
## <a name="see-also"></a>Ayrıca Bkz.
