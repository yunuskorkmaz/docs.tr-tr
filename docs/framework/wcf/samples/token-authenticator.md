---
title: "Belirteç Kimlik Doğrulayıcı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 84382f2c-f6b1-4c32-82fa-aebc8f6064db
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d635a1d5122319e228feb4d8a362b7609129c9de
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="token-authenticator"></a>Belirteç Kimlik Doğrulayıcı
Bu örnek, özel bir belirteç kimlik doğrulayıcı uygulama gösterilmiştir. İçinde bir belirteç kimlik doğrulayıcısı [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] self tutarlı ve kimliğinin doğrulanması belirteçle ilişkili doğrulama ileti ile kullanılan belirteci doğrulamak için kullanılır.  
  
 Özel belirteç kimlik doğrulayan gibi çeşitli durumlarda yararlı olur:  
  
-   Ne zaman bir belirteçle ilişkilendirilen varsayılan kimlik doğrulama mekanizması geçersiz kılmak istiyorsunuz.  
  
-   Ne zaman özel belirteç oluşturmakta olduğunuz.  
  
 Bu örnek şunlar gösterilmektedir:  
  
-   Nasıl bir istemci bir kullanıcı adı/parola çifti kullanılarak doğrulanabilir.  
  
-   Sunucu özel belirteç kimlik doğrulayıcı kullanarak istemci kimlik bilgilerini nasıl doğrulayabilirsiniz.  
  
-   Nasıl [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] servis kodu özel belirteç kimlik doğrulayıcı oturum bağlar.  
  
-   Sunucu, sunucunun X.509 sertifikası kullanılarak doğrulanabilir nasıl.  
  
 Bu örnek ayrıca nasıl çağıranının kimliğini erişilebilir gösterir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sonra özel belirteç kimlik doğrulama işlemi.  
  
 Hizmet App.config yapılandırma dosyası kullanılarak tanımlanmış hizmet ile iletişim için tek bir uç noktasını kullanıma sunar. Uç nokta bir adresi, bağlama ve bir sözleşme oluşur. Bağlama ile standart bir yapılandırılmış `wsHttpBinding`, güvenlik modu iletiye - varsayılan modu ayarlandığında `wsHttpBinding`. Bu örnek standart ayarlar `wsHttpBinding` istemci kullanıcı adı kimlik doğrulaması kullanmak için. Hizmetini kullanarak sertifika hizmetini de yapılandırır `serviceCredentials` davranışı. `securityCredentials` Davranış bir hizmet sertifikası belirtmenize olanak sağlar. Bir hizmet sertifikası, hizmetin kimliğini doğrulamak ve ileti koruma sağlamak için bir istemci tarafından kullanılır. Aşağıdaki yapılandırma aşağıdaki Kurulum yönergelerde açıklandığı gibi örnek Kurulum sırasında yüklenen localhost sertifika başvurur.  
  
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
  
 Yapılandırma adı, hizmet uç noktası, bağlama ve sözleşme için mutlak bir adres, istemci uç nokta yapılandırması oluşur. Bağlama istemci uygun ile yapılandırılmış `Mode` ve `clientCredentialType`.  
  
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
  
 İstemci uygulama kullanıcı adı ve parola ayarlar.  
  
```  
static void Main()  
{  
     ...  
     client.ClientCredentials.UserNamePassword.UserName = username;  
     client.ClientCredentials.UserNamePassword.Password = password;  
     ...  
}  
```  
  
## <a name="custom-token-authenticator"></a>Özel belirteç kimlik doğrulayıcı  
 Özel bir belirteç kimlik doğrulayıcısı oluşturmak için aşağıdaki adımları kullanın:  
  
1.  Özel belirteç kimlik doğrulayıcı yazma.  
  
     Örnek kullanıcı adı geçerli bir e-posta biçiminde olduğunu doğrulayan bir özel belirteç kimlik doğrulayıcı uygular. Bunu türetilen <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator>. Bu sınıftaki en önemli bir yöntemdir <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator.ValidateUserNamePasswordCore%28System.String%2CSystem.String%29>. Bu yöntemde, Doğrulayıcı biçimini doğrular. kullanıcı adı ve bu da ana bilgisayar adı yanlış etki alanına ait değil. Her iki koşullar sonra salt okunur koleksiyonunu döndürür <xref:System.IdentityModel.Policy.IAuthorizationPolicy> sonra kullanıcı adı belirteci içine depolanan bilgileri temsil eden talepler sağlamak için kullanılan örnekleri.  
  
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
  
2.  Özel belirteç kimlik doğrulayıcı tarafından döndürülen bir yetkilendirme ilkesi sağlar.  
  
     Bu örnek, kendi uygulamasını sağlar <xref:System.IdentityModel.Policy.IAuthorizationPolicy> adlı `UnconditionalPolicy` talepler ve kendisine kurucusunda geçirilmiş kimlikleri kümesini döndürür.  
  
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
  
3.  Özel bir güvenlik belirteci yöneticisi yazma.  
  
     <xref:System.IdentityModel.Selectors.SecurityTokenManager> Oluşturmak için kullanılan bir <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> belirli <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> kendisine geçirilen nesneleri `CreateSecurityTokenAuthenticator` yöntemi. Güvenlik belirteci yöneticisi belirteci sağlayıcıları ve belirteç serileştiricileri oluşturmak için de kullanılır, ancak bunlar Bu örnek tarafından ele alınmamaktadır. Bu örnekte, özel güvenlik belirteci yöneticisi devraldığı <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> sınıfı ve geçersiz kılmalar `CreateSecurityTokenAuthenticator` geçirilen belirteç gereksinimlerini bu kullanıcı adı kimlik doğrulayıcı belirttiğinizde özel kullanıcıadı belirteç kimlik doğrulayıcı döndürülecek yöntemi istendi.  
  
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
  
     Hizmet kimlik bilgilerini sınıfı hizmet için yapılandırılan kimlik bilgileri temsil etmek için kullanılır ve bir güvenlik belirteci Doğrulayıcı, belirteci sağlayıcıları ve belirteç serileştiricileri elde etmek için kullanılan belirteci yöneticisi oluşturur.  
  
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
  
5.  Hizmetini özel hizmet kimlik bilgilerini kullanacak biçimde yapılandırın.  
  
     Özel hizmet kimlik bilgilerini kullanmak hizmet için sırasıyla biz varsayılan hizmet kimlik bilgisi sınıfını zaten varsayılan hizmet kimlik bilgisi önceden yapılandırılmış hizmet sertifikası yakalama sonra silin ve yeni hizmet kimlik bilgilerini yapılandırın önceden yapılandırılmış hizmet sertifikalarını kullanın ve bu yeni hizmet kimlik bilgisi örneği hizmet davranışları eklemek için örneği.  
  
    ```  
    ServiceCredentials sc = serviceHost.Credentials;  
    X509Certificate2 cert = sc.ServiceCertificate.Certificate;  
    MyUserNameCredential serviceCredential = new MyUserNameCredential();  
    serviceCredential.ServiceCertificate.Certificate = cert;  
    serviceHost.Description.Behaviors.Remove((typeof(ServiceCredentials)));  
    serviceHost.Description.Behaviors.Add(serviceCredential);  
    ```  
  
 Arayanın bilgileri görüntülemek için kullanabileceğiniz <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> aşağıdaki kodda gösterildiği gibi. <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> Talep geçerli çağıran hakkında bilgi içerir.  
  
```  
static void DisplayIdentityInformation()  
{  
    Console.WriteLine("\t\tSecurity context identity  :  {0}",   
            ServiceSecurityContext.Current.PrimaryIdentity.Name);  
     return;  
}  
```  
  
 Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir. İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.  
  
## <a name="setup-batch-file"></a>Toplu iş dosyası Kurulumu  
 Bu örnekle dahil Setup.bat toplu iş dosyası ile ilgili sertifika sunucusu gerektirir kendini barındıran bir uygulamayı çalıştırmak için sunucuyu yapılandırmak için sertifika tabanlı güvenlik sağlar. Bu toplu iş dosyası bilgisayarlar arasında iş ya da barındırılan olmayan bir durumda çalışması için değiştirilmesi gerekir.  
  
 Aşağıdakiler, böylece uygun yapılandırmada çalışacak biçimde değiştirilebilir toplu iş dosyaları farklı bölümlerini kısa bir genel bakış sağlar.  
  
-   Sunucu sertifikası oluşturuluyor.  
  
     Aşağıdaki satırları Setup.bat toplu iş dosyasından kullanılacak sunucu sertifikası oluşturun. `%SERVER_NAME%` Değişkeni, sunucu adını belirtir. Kendi sunucu adını belirtmek için bu değişkeni değiştirin. Bu toplu iş dosyasındaki localhost varsayılandır.  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   Sunucu sertifikası istemcinin güvenilen sertifika deposuna yükleme.  
  
     İstemci güvenilir kişiler içine Setup.bat toplu dosya kopyalama sunucu sertifikasının aşağıdaki satırları depolar. MakeCert.exe tarafından oluşturulan sertifikaları örtük olarak istemci sistemi tarafından güvenilir değil çünkü bu adım gereklidir. Bir istemci güvenilen kök sertifikasını kökü belirtilmiş bir sertifikanız zaten varsa — örneğin, bir Microsoft verilen sertifika — sunucu sertifikasına sahip istemci sertifika deposunun doldurulması, bu adım gerekli değildir.  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
    > [!NOTE]
    >  Kurulum toplu iş dosyası, Windows SDK komut isteminden çalıştırılması için tasarlanmıştır. MSSDK ortam değişkeni SDK yüklendiği dizinine işaret gerektiriyor. Bu ortam değişkeni, Windows SDK komut istemi içinde otomatik olarak ayarlanır.  
  
#### <a name="to-set-up-and-build-the-sample"></a>Ayarlamak ve örneği oluşturmak için  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözümü derlemek için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a>Aynı bilgisayara örneği çalıştırmak için  
  
1.  Örnek yükleme klasöründen içinde Setup.bat çalıştırmak bir [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemini yönetici ayrıcalıklarıyla açılır. Bu örneği çalıştırmak için gerekli tüm sertifikalar yükler.  
  
    > [!NOTE]
    >  Setup.bat toplu iş dosyası çalıştırılmak üzere tasarlanmış bir [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemi. İçinde PATH ortam değişkeni ayarlamak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemi Setup.bat komut dosyası için gereken yürütülebilir dosyalar içeren dizine işaret eder.  
  
2.  Service\bin gelen Service.exe başlatın.  
  
3.  \Client\bin gelen Client.exe başlatın. İstemci etkinliği istemci konsol uygulaması görüntülenir.  
  
4.  İstemci ve hizmet iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-run-the-sample-across-computers"></a>Bilgisayarlar arasında örneği çalıştırmak için  
  
1.  Hizmet ikili dosyaları hizmet bilgisayarda bir dizin oluşturun.  
  
2.  Hizmet program dosyalarını hizmeti bilgisayarında hizmet dizinine kopyalayın. Ayrıca Setup.bat ve Cleanup.bat dosyalarını hizmet bilgisayara kopyalayın.  
  
3.  Bilgisayarın tam etki alanı adını içeren konu adına sahip bir sunucu sertifikası olmalıdır. Hizmet App.config dosyası bu yeni sertifika adını yansıtacak şekilde güncelleştirmeniz gerekir. Ayarlarsanız Setup.bat kullanarak bir tane oluşturabilirsiniz `%SERVER_NAME%` hizmetin çalışacağı bilgisayarın tam ana bilgisayar adı için değişken. Setup.bat dosyasını yönetici ayrıcalıklarıyla açılmış Visual Studio komut isteminden çalıştırmanız gerektiğini unutmayın.  
  
4.  Sunucu sertifikası istemci Currentuser'a TrustedPeople depolama alanına kopyalayın. Sunucu sertifikası zaman istemcisi güvenilir veren tarafından verilen dışında bunu gerekmez.  
  
5.  Hizmeti bilgisayarında App.config dosyasında localhost yerine bir tam bilgisayar adını belirtmek için taban adresi değerini değiştirin.  
  
6.  Hizmet bilgisayarda service.exe bir komut isteminden çalıştırın.  
  
7.  İstemci program dosyaları \client\bin\ klasöründen dile özgü klasörü altında istemci bilgisayara kopyalayın.  
  
8.  İstemci bilgisayardaki Client.exe.config dosyasında yeni adresi hizmetinizin eşleştirmek için uç nokta adresi değerini değiştirin.  
  
9. İstemci bilgisayarda bir komut isteminden Client.exe başlatın.  
  
10. İstemci ve hizmet iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-clean-up-after-the-sample"></a>Örnek sonra temizlemek için  
  
1.  Örnek çalıştıran tamamladıktan sonra Cleanup.bat samples klasöründen çalıştırın.  
  
## <a name="see-also"></a>Ayrıca Bkz.
