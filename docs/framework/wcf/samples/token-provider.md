---
title: Belirteç Sağlayıcı
ms.date: 03/30/2017
ms.assetid: 947986cf-9946-4987-84e5-a14678d96edb
ms.openlocfilehash: a0d46419de71cb3504467d1b728fb05f3de0bf45
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59085771"
---
# <a name="token-provider"></a>Belirteç Sağlayıcı
Bu örnek, özel bir belirteç sağlayıcısını uygulamak nasıl gösterir. Windows Communication Foundation (WCF) bir belirteç sağlayıcısı güvenlik altyapısı için kimlik bilgilerini sağlamak için kullanılır. Belirteç sağlayıcı genel hedef inceler ve böylece ileti güvenlik altyapısı güvenli hale getirebilirsiniz, kimlik bilgileri sorunları uygun. WCF varsayılan kimlik bilgileri Yöneticisi belirteç sağlayıcısı ile birlikte gelir. WCF ayrıca ile birlikte gelir bir [!INCLUDE[infocard](../../../../includes/infocard-md.md)] belirteç sağlayıcısı. Özel belirteç sağlayıcıları, aşağıdaki durumlarda kullanışlıdır:

-   Bu belirteci sağlayıcıları ile çalışamaz bir kimlik bilgisi deposu varsa.

-   Kullanıcı için WCF istemci framework kimlik bilgileri kullandığında ayrıntıları sağladığında noktadan kimlik dönüştürme için kendi özel mekanizması sağlamak istiyorsanız.

-   Özel belirteç oluşturuluyorsa.

 Bu örnek, kullanıcı girişini başka bir biçime dönüştürür özel bir belirteç sağlayıcısı oluşturmak nasıl gösterir.

 Özetlemek gerekirse, bu örnek aşağıdaki gösterir:

-   Nasıl bir istemci bir kullanıcı adı/parola çifti kullanarak kimlik doğrulaması yapabilir.

-   Nasıl bir istemci özel bir belirteç sağlayıcısı ile yapılandırılabilir.

-   Sunucunun istemci kimlik bilgileri ile özel bir parola ile nasıl doğrulayabilirsiniz <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> kullanıcı adı ve parola eşleştiğini doğrular.

-   Sunucu, sunucunun X.509 sertifikası kullanarak istemci tarafından nasıl doğrulanır.

 Ayrıca bu örnek nasıl çağıranının kimliğini özel belirteç kimlik doğrulama işleminden sonra erişilebilir gösterir.

 Hizmet, App.config yapılandırma dosyası kullanılarak tanımlanmış hizmet ile iletişim kurmak için tek bir uç noktayı kullanıma sunar. Uç nokta, adres, bağlama ve bir sözleşme oluşur. Bir standart yapılandırılmış bağlama `wsHttpBinding`, hangi kullanır, varsayılan olarak güvenlik iletisi. Bu örnek, standart ayarlar `wsHttpBinding` istemci kullanıcı adı kimlik doğrulaması kullanmak için. Hizmet Ayrıca hizmet sertifikası serviceCredentials davranışını kullanarak yapılandırır. ServiceCredentials davranışı, bir hizmet sertifikası yapılandırmanıza olanak sağlar. Bir hizmet sertifikası, hizmet kimlik doğrulaması ve ileti koruma sağlamak için bir istemci tarafından kullanılır. Aşağıdaki yapılandırmayı aşağıdaki Kurulum yönergelerinde açıklandığı gibi örnek Kurulum sırasında yüklenen localhost sertifikasına başvuruda bulunuyor.

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

 İstemci uç nokta yapılandırması mutlak bir adres için hizmet uç noktası, bağlama ve sözleşmenin bir yapılandırma adı oluşur. Bağlama istemcinin uygun olarak yapılandırıldığı `Mode` ve ileti `clientCredentialType`.

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

 Aşağıdaki adımlarda, özel bir belirteç sağlayıcısını geliştirin ve WCF güvenlik çerçevesi ile tümleştirmek gösterilmektedir:

1.  Özel bir belirteç sağlayıcısını yazın.

     Örnek kullanıcı adı ve parola özel bir belirteç sağlayıcısını uygular. Bu kullanıcı adı parola eşleşmesi gerekir. Bu özel belirteç sağlayıcısı, yalnızca gösterim amaçlıdır ve gerçek dünya dağıtım önerilmez.

     Bu görevi gerçekleştirmek için özel belirteç sağlayıcısı türetilen <xref:System.IdentityModel.Selectors.SecurityTokenProvider> sınıf ve geçersiz kılmaları <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> yöntemi. Bu yöntem, oluşturur ve yeni bir `UserNameSecurityToken`.

    ```
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

2.  Özel güvenlik belirteci Yöneticisi'ni yazın.

     <xref:System.IdentityModel.Selectors.SecurityTokenManager> Oluşturmak için kullanılan <xref:System.IdentityModel.Selectors.SecurityTokenProvider> belirli <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> kendisine geçirilen `CreateSecurityTokenProvider` yöntemi. Güvenlik belirteci Yöneticisi ayrıca belirteç Doğrulayıcı ve belirteci seri hale getirici oluşturmak için kullanılır, ancak bunlar Bu örnek tarafından ele alınmamıştır. Bu örnekte, özel güvenlik belirteci yöneticisi devraldığı <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> sınıf ve geçersiz kılmaları `CreateSecurityTokenProvider` geçirilen belirteci gereksinimleri, kullanıcı adı sağlayıcı belirttiğinizde, özel kullanıcı adı belirteci sağlayıcısı döndürülecek yöntemi istendi.

    ```
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

3.  Özel istemci kimlik bilgilerini yazın.

     İstemci kimlik bilgileri sınıfı istemci proxy'si için yapılandırıldığında kimlik bilgilerini temsil etmek için kullanılır ve güvenlik belirteci kimlik doğrulayıcılar, belirteç sağlayıcıları ve belirteci serileştiriciye elde etmek için kullanılan belirteci yöneticisi oluşturur.

    ```
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

4.  Özel istemci kimlik bilgilerini kullanacak biçimde yapılandırın.

     Özel istemci kimlik bilgilerini kullanmak üzere istemciyi sırasıyla örneği, varsayılan istemci kimlik bilgisi sınıfını siler ve yeni istemci kimlik bilgisi sınıfını sağlar.

    ```
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

 Arayanın bilgileri görüntülemek için bu hizmeti üzerinde kullanan <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> aşağıdaki kod örneğinde gösterildiği gibi. <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> Talep geçerli arayanı hakkında bilgi içerir.

```
static void DisplayIdentityInformation()
{
    Console.WriteLine("\t\tSecurity context identity  :  {0}",
        ServiceSecurityContext.Current.PrimaryIdentity.Name);
}
```

 Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir. İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.

## <a name="setup-batch-file"></a>Kurulum toplu iş dosyası
 Bu örnekle dahil Setup.bat toplu iş dosyası, sunucu sertifika tabanlı güvenlik gerektiren şirket içinde barındırılan bir uygulamayı çalıştırmak için ilgili sertifika ile sunucu yapılandırmanıza olanak sağlar. Bu toplu iş dosyası bilgisayarlarda çalışmaya veya barındırılan olmayan bir durumda çalışması için değiştirilmesi gerekir.

 Aşağıda, böylece uygun yapılandırmasında çalıştırılacak değiştirilebilir toplu iş dosyaları farklı bölümlerini kısa bir genel bakış sağlar:

-   Sunucu sertifikası oluşturuluyor.

     Setup.bat toplu iş dosyasından aşağıdaki satırları kullanılacak sunucu sertifikası oluşturun. `%SERVER_NAME%` Değişkeni, sunucu adını belirtir. Kendi sunucu adını belirtmek için bu değişkeni değiştirin. Localhost bu toplu iş dosyasında varsayılan değerdir.

    ```
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

-   Sunucu sertifikasını istemcinin güvenilen sertifika depolama alanına yükleniyor:

     İstemci güvenilir kişiler uygulamasına Setup.bat toplu dosya kopyalama sunucu sertifikasının aşağıdaki satırları depolayın. MakeCert.exe tarafından oluşturulan sertifikaları örtük olarak istemci sistemi tarafından güvenilir değildir çünkü bu adım gereklidir. Bir istemci güvenilen kök sertifikayı kök erişim izni verilmiş bir sertifika zaten varsa — örneğin, Microsoft tarafından verilen sertifika — sunucu sertifikasında istemci sertifika deposunun doldurulması, bu adım gerekli değildir.

    ```
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

> [!NOTE]
>  Setup.bat toplu iş dosyası, bir Windows SDK Komut İstemi'nden çalıştırılmak üzere tasarlanmıştır. MSSDK ortam değişkeni'nın SDK'ın yüklendiği dizini gösterecek gerektiriyor. Bu ortam değişkeni, bir Windows SDK komut istemi içinde otomatik olarak ayarlanır.

#### <a name="to-set-up-and-build-the-sample"></a>Ayarlama ve örneği oluşturmak için

1.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2.  Çözümü derlemek için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).

#### <a name="to-run-the-sample-on-the-same-computer"></a>Örneği aynı bilgisayarda çalıştırmak için

1.  Visual Studio 2012 komut istemini yönetici ayrıcalıklarıyla açılan içinde örnek yükleme klasöründen Setup.bat çalıştırın. Bu örneği çalıştırmak için gerekli olan tüm sertifikaları yükler.

    > [!NOTE]
    >  Setup.bat toplu iş dosyası, bir Visual Studio 2012 komut isteminden çalıştırılması için tasarlanmıştır. PATH ortam değişkenine içinde Visual Studio 2012 komut istemi noktaları Setup.bat betiği tarafından gereken yürütülebilir dosyaları içeren dizine ayarlayın.  
  
2.  Service.exe service\bin'nden başlatın.  
  
3.  Client.exe \client\bin başlatın. İstemci etkinliği istemci konsol uygulamasında görüntülenir.  
  
4.  Kullanıcı adı isteminde bir kullanıcı adı yazın.  
  
5.  Parola isteminde yazıldı aynı dize için kullanıcı adı istemi kullanın.  
  
6.  İstemci ve hizmet iletişim kurabildiğini bilmiyorsanız bkz [WCF örnekleri için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-run-the-sample-across-computers"></a>Bilgisayarlar arasında örneği çalıştırmak için  
  
1.  Hizmet ikili dosyaları için hizmet bilgisayarda bir dizin oluşturun.  
  
2.  Hizmet program dosyaları hizmeti bilgisayarında hizmet dizinine kopyalayın. Ayrıca Setup.bat ve Cleanup.bat dosyaları hizmet bilgisayara kopyalayın.  
  
3.  Bilgisayarın tam etki alanı adını içeren konu adına sahip bir sunucu sertifikası olmalıdır. Service.exe.config dosyayı bu yeni sertifika adı yansıtacak şekilde güncelleştirilmesi gerekir. Setup.bat toplu iş dosyasını değiştirerek, sunucu sertifikası oluşturabilirsiniz. Setup.bat dosyasının Visual Studio için geliştirici komut isteminden çalıştırılmalıdır Not yönetici ayrıcalıklarıyla açılan. Ayarlamalısınız `%SERVER_NAME%` hizmeti barındırmak için kullanılan bilgisayarın tam ana bilgisayar adı için değişken.  
  
4.  Sunucu sertifikasını istemcinin CurrentUser TrustedPeople depoya kopyalayın. Sunucu sertifikası güvenilir istemci veren tarafından verildiğinde Bunu yapmak gerekmez.  
  
5.  Hizmet bilgisayarı Service.exe.config dosyada localhost yerine tam bilgisayar adını belirtmek için temel adresini değiştirin.  
  
6.  Hizmet bilgisayarda service.exe bir komut isteminden çalıştırın.  
  
7.  İstemci program dosyaları \client\bin\ klasöründen dile özgü klasörünün altındaki istemci bilgisayara kopyalayın.  
  
8.  İstemci bilgisayarda Client.exe.config dosyasında hizmetinizin yeni adresiyle eşleşecek şekilde uç nokta adresi değiştirin.  
  
9. İstemci bilgisayarda Başlat `Client.exe` bir komut istemi penceresinden.  
  
10. İstemci ve hizmet iletişim kurabildiğini bilmiyorsanız bkz [WCF örnekleri için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-clean-up-after-the-sample"></a>Sonra örnek temizlemek için  
  
1.  Bu örneği çalıştırmadan tamamladıktan sonra Cleanup.bat samples klasöründe çalıştırın.  
