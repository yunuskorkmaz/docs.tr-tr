---
title: Belirteç Sağlayıcı
ms.date: 03/30/2017
ms.assetid: 947986cf-9946-4987-84e5-a14678d96edb
ms.openlocfilehash: e1520ef3e2faca88b06cc82ef5ab3035a857314a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969366"
---
# <a name="token-provider"></a>Belirteç Sağlayıcı
Bu örnek, bir özel belirteç sağlayıcısının nasıl uygulanacağını gösterir. Güvenlik altyapısına kimlik bilgileri sağlamak için Windows Communication Foundation (WCF) içindeki bir belirteç sağlayıcısı kullanılır. Genel içindeki belirteç sağlayıcısı hedefi inceler ve güvenlik altyapısının iletiyi güvenli hale getirmek için uygun kimlik bilgilerini verir. WCF varsayılan kimlik bilgileri Yöneticisi belirteç sağlayıcısıyla birlikte gelir. WCF Ayrıca bir CardSpace belirteç sağlayıcısıyla birlikte gelir. Özel belirteç sağlayıcıları aşağıdaki durumlarda faydalıdır:

- Bu belirteç sağlayıcılarının ile çalışamadığınız bir kimlik bilgisi depoluğiniz varsa.

- Kullanıcı, WCF istemci çerçevesi kimlik bilgilerini kullandığında, kimlik bilgilerini bir noktadan dönüştürmek için kendi özel mekanizmanızı sağlamak istiyorsanız.

- Özel bir belirteç oluşturuyorsanız.

 Bu örnek, kullanıcıdan girişi farklı bir biçime dönüştüren özel bir belirteç sağlayıcısı oluşturmayı gösterir.

 Özetlemek gerekirse, bu örnek şunları gösterir:

- Bir istemcinin Kullanıcı adı/parola çifti kullanarak kimlik doğrulaması yapabilir.

- Bir istemcinin özel bir belirteç sağlayıcısıyla nasıl yapılandırılabileceğini.

- Sunucunun, Kullanıcı adının ve parolanın eşleştiğini doğrulayan özel <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> bir parola kullanarak istemci kimlik bilgilerini nasıl doğrulayabileceğiniz.

- Sunucunun, sunucunun X. 509.440 sertifikasını kullanarak istemci tarafından nasıl doğrulandığını.

 Bu örnek ayrıca, özel belirteç kimlik doğrulama işleminden sonra arayanın kimliğinin nasıl erişilebilir olduğunu gösterir.

 Hizmet, App. config yapılandırma dosyası kullanılarak tanımlanan hizmetle iletişim kurmak için tek bir uç nokta sunar. Uç nokta bir adres, bağlama ve bir anlaşmada oluşur. Bağlama, varsayılan olarak ileti güvenliği kullanan `wsHttpBinding`bir standart ile yapılandırılır. Bu örnek, standart istemci `wsHttpBinding` Kullanıcı adı kimlik doğrulamasını kullanmak için standardı ayarlar. Hizmet Ayrıca, serviceCredentials davranışını kullanarak hizmet sertifikasını yapılandırır. ServiceCredentials davranışı bir hizmet sertifikası yapılandırmanıza olanak tanır. Hizmet sertifikası, istemci tarafından hizmetin kimliğini doğrulamak ve ileti koruması sağlamak için kullanılır. Aşağıdaki yapılandırma, aşağıdaki kurulum yönergelerinde açıklandığı gibi örnek kurulum sırasında yüklü olan localhost sertifikasına başvurur.

```xml
<system.serviceModel>
    <services>
      <service
          name="Microsoft.ServiceModel.Samples.CalculatorService"
          behaviorConfiguration="CalculatorServiceBehavior">
        <host>
          <baseAddresses>
            <!-- configure base address provided by host -->
            <add baseAddress ="http://localhost:8000/servicemodelsamples/service"/>
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
        -->
          <serviceCredentials>
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />
          </serviceCredentials>
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
```

 İstemci uç noktası yapılandırması, bir yapılandırma adından, hizmet uç noktası için mutlak bir adresten, bağlamaya ve sözleşmeyle oluşur. İstemci bağlama, uygun `Mode` ve ileti `clientCredentialType`ile yapılandırılır.

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

 Aşağıdaki adımlarda, özel bir belirteç sağlayıcısının nasıl geliştirilmesi ve WCF güvenlik çerçevesiyle tümleştirileceği gösterilmektedir:

1. Özel bir belirteç sağlayıcısı yazın.

     Örnek, Kullanıcı adını ve parolayı elde eden bir özel belirteç sağlayıcısı uygular. Parolanın bu kullanıcı adıyla eşleşmesi gerekir. Bu özel belirteç sağlayıcısı yalnızca tanıtım amaçlıdır ve gerçek dünya dağıtımı için önerilmez.

     Bu görevi gerçekleştirmek için özel belirteç sağlayıcısı <xref:System.IdentityModel.Selectors.SecurityTokenProvider> sınıfı türetir ve <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> yöntemini geçersiz kılar. Bu yöntem, oluşturur ve yeni `UserNameSecurityToken`bir döndürür.

    ```csharp
    protected override SecurityToken GetTokenCore(TimeSpan timeout)
    {
        // obtain username and password from the user using console window
        string username = GetUserName();
        string password = GetPassword();
        Console.WriteLine("username: {0}", username);

        // return new UserNameSecurityToken containing information obtained from user
        return new UserNameSecurityToken(username, password);
    }
    ```

2. Özel güvenlik belirteci Yöneticisi yazın.

     , <xref:System.IdentityModel.Selectors.SecurityTokenManager> Yöntemi içinde <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> <xref:System.IdentityModel.Selectors.SecurityTokenProvider> kendisinegeçirilenbelirlibiroluşturmakiçinkullanılır`CreateSecurityTokenProvider` . Güvenlik belirteci Yöneticisi, belirteç doğrulayıcılar ve bir belirteç seri hale getirici oluşturmak için de kullanılır, ancak bunlar bu örnek tarafından kapsanmaz. Bu örnekte, özel güvenlik belirteci Yöneticisi <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> sınıfından devralır ve geçilen belirteç gereksinimleri Kullanıcı adı sağlayıcısının istendiğini gösteriyorsa özel Kullanıcı adı belirteci sağlayıcısını döndürecek şekilde `CreateSecurityTokenProvider` geçersiz kılar.

    ```csharp
    public class MyUserNameSecurityTokenManager : ClientCredentialsSecurityTokenManager
    {
        MyUserNameClientCredentials myUserNameClientCredentials;

        public MyUserNameSecurityTokenManager(MyUserNameClientCredentials myUserNameClientCredentials)
            : base(myUserNameClientCredentials)
        {
            this.myUserNameClientCredentials = myUserNameClientCredentials;
        }

        public override SecurityTokenProvider CreateSecurityTokenProvider(SecurityTokenRequirement tokenRequirement)
        {
            // if token requirement matches username token return custom username token provider
            // otherwise use base implementation
            if (tokenRequirement.TokenType == SecurityTokenTypes.UserName)
            {
                return new MyUserNameTokenProvider();
            }
            else
            {
                return base.CreateSecurityTokenProvider(tokenRequirement);
            }
        }
    }
    ```

3. Özel bir istemci kimlik bilgisi yazın.

     İstemci kimlik bilgileri sınıfı, istemci ara sunucusu için yapılandırılan kimlik bilgilerini temsil etmek için kullanılır ve belirteç doğrulayıcılar, belirteç sağlayıcıları ve bir belirteç serileştirici elde etmek için kullanılan güvenlik belirteci Yöneticisi oluşturur.

    ```csharp
    public class MyUserNameClientCredentials : ClientCredentials
    {
        public MyUserNameClientCredentials()
            : base()
        {
        }

        protected override ClientCredentials CloneCore()
        {
            return new MyUserNameClientCredentials();
        }

        public override SecurityTokenManager CreateSecurityTokenManager()
        {
            // return custom security token manager
            return new MyUserNameSecurityTokenManager(this);
        }
    }
    ```

4. İstemciyi özel istemci kimlik bilgilerini kullanacak şekilde yapılandırın.

     İstemcinin özel istemci kimlik bilgisini kullanabilmesi için, örnek varsayılan istemci kimlik bilgisi sınıfını siler ve yeni istemci kimlik bilgisi sınıfını sağlar.

    ```csharp
    static void Main()
    {
        // ...
           // Create a client with given client endpoint configuration
          CalculatorClient client = new CalculatorClient();

          // set new credentials
           client.ChannelFactory.Endpoint.Behaviors.Remove(typeof(ClientCredentials));
         client.ChannelFactory.Endpoint.Behaviors.Add(new MyUserNameClientCredentials());
       // ...
    }
    ```

 Hizmette, arayanın bilgilerini göstermek için, aşağıdaki kod örneğinde gösterildiği <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> gibi kullanın. , <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> Geçerli çağıran ile ilgili talep bilgilerini içerir.

```csharp
static void DisplayIdentityInformation()
{
    Console.WriteLine("\t\tSecurity context identity  :  {0}",
        ServiceSecurityContext.Current.PrimaryIdentity.Name);
}
```

 Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir. İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.

## <a name="setup-batch-file"></a>Toplu Iş dosyası kurulumu
 Bu örneğe eklenen Setup. bat toplu iş dosyası, sunucu sertifika tabanlı güvenlik gerektiren şirket içinde barındırılan bir uygulamayı çalıştırmak için sunucuyu ilgili sertifikayla yapılandırmanızı sağlar. Bu toplu iş dosyasının bilgisayarlarda çalışmak veya barındırılmayan bir durumda çalışması için değiştirilmesi gerekir.

 Aşağıdakiler, uygun yapılandırmada çalışacak şekilde değiştirilebilecek şekilde, toplu iş dosyalarının farklı bölümlerine kısa bir genel bakış sunar:

- Sunucu sertifikası oluşturuluyor.

     Setup. bat toplu iş dosyasından aşağıdaki satırlar kullanılacak sunucu sertifikasını oluşturur. `%SERVER_NAME%` Değişken, sunucu adını belirtir. Kendi sunucu adınızı belirtmek için bu değişkeni değiştirin. Bu toplu iş dosyasındaki varsayılan değer localhost 'tur.

    ```
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- Sunucu sertifikasını istemcinin güvenilen sertifika deposuna yükleme:

     Setup. bat toplu iş dosyası 'ndaki aşağıdaki satırlar, sunucu sertifikasını istemci güvenilir kişiler deposuna kopyalar. Bu adım, MakeCert. exe tarafından oluşturulan sertifikaların istemci sistemi tarafından örtük olarak güvenilir olmadığından gereklidir. İstemci tarafından güvenilen kök sertifikada kök sertifikaya sahip bir sertifikanız zaten varsa (örneğin, Microsoft tarafından verilen bir sertifika), istemci sertifikası deposunu sunucu sertifikasıyla doldurmanın bu adımı gerektirmez.

    ```
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

> [!NOTE]
> Setup. bat toplu iş dosyası bir Windows SDK komut Isteminden çalıştırılmak üzere tasarlanmıştır. MSSDK ortam değişkeninin, SDK 'nın yüklü olduğu dizine işaret olmasını gerektirir. Bu ortam değişkeni bir Windows SDK komut Istemi içinde otomatik olarak ayarlanır.

#### <a name="to-set-up-and-build-the-sample"></a>Örneği ayarlamak ve derlemek için

1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.

2. Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)bölümündeki yönergeleri izleyin.

#### <a name="to-run-the-sample-on-the-same-computer"></a>Örneği aynı bilgisayarda çalıştırmak için

1. Setup. bat dosyasını, bir Visual Studio 2012 komut istemi içindeki örnek yükleme klasöründen yönetici ayrıcalıklarıyla açılan bir şekilde çalıştırın. Bu, örneği çalıştırmak için gereken tüm sertifikaları kurar.

    > [!NOTE]
    >  Setup. bat toplu iş dosyası bir Visual Studio 2012 komut Isteminden çalıştırılmak üzere tasarlanmıştır. Visual Studio 2012 komut Isteminde ayarlanan PATH ortam değişkeni Setup. bat betiği için gereken yürütülebilir dosyaları içeren dizine işaret eder.  
  
2. Service\bin. adresinden Service. exe ' yi Başlat  
  
3. \Client\bin. adresinden Client. exe ' yi Başlat İstemci etkinliği istemci konsol uygulamasında görüntülenir.  
  
4. Kullanıcı adı istemine bir Kullanıcı adı yazın.  
  
5. Parola isteminde, Kullanıcı adı istemi için yazılan dizeyi kullanın.  
  
6. İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-run-the-sample-across-computers"></a>Örneği bilgisayarlar arasında çalıştırmak için  
  
1. Hizmet ikili dosyaları için hizmet bilgisayarında bir dizin oluşturun.  
  
2. Hizmet programı dosyalarını hizmet bilgisayarındaki hizmet dizinine kopyalayın. Ayrıca Setup. bat ve Cleanup. bat dosyalarını da hizmet bilgisayarına kopyalayın.  
  
3. Bilgisayarın tam etki alanı adını içeren konu adına sahip bir sunucu sertifikasına sahip olmanız gerekir. Service. exe. config dosyasının bu yeni sertifika adını yansıtması için güncelleştirilmeleri gerekir. Setup. bat toplu iş dosyasını değiştirerek sunucu sertifikası oluşturabilirsiniz. Setup. bat dosyasının, yönetici ayrıcalıklarıyla açılan bir Visual Studio için Geliştirici Komut İstemi çalıştırılması gerektiğini unutmayın. Değişkeni, hizmeti `%SERVER_NAME%` barındırmak için kullanılan bilgisayarın tam olarak nitelenmiş ana bilgisayar adına ayarlamanız gerekir.  
  
4. Sunucu sertifikasını istemcinin CurrentUser-Trustedkişilerim deposuna kopyalayın. Sunucu sertifikası, istemci güvenilir veren tarafından verildiğinde bunu yapmanız gerekmez.  
  
5. Hizmet bilgisayarındaki Service. exe. config dosyasında, temel adresin değerini localhost yerine tam nitelikli bir bilgisayar adı belirtecek şekilde değiştirin.  
  
6. Hizmet bilgisayarında, komut isteminden Service. exe ' yi çalıştırın.  
  
7. İstemci program dosyalarını dile özgü klasörün altındaki \client\bin\ klasöründen istemci bilgisayara kopyalayın.  
  
8. İstemci bilgisayardaki Client. exe. config dosyasında, uç noktanın adres değerini hizmetinizin yeni adresiyle eşleşecek şekilde değiştirin.  
  
9. İstemci bilgisayarda, bir komut istemi `Client.exe` penceresinden başlatın.  
  
10. İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-clean-up-after-the-sample"></a>Örnekten sonra temizlemek için  
  
1. Örneği çalıştırmayı bitirdikten sonra Samples klasöründe Cleanup. bat dosyasını çalıştırın.  
