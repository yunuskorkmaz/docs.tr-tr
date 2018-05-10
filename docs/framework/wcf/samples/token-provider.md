---
title: Belirteç Sağlayıcı
ms.date: 03/30/2017
ms.assetid: 947986cf-9946-4987-84e5-a14678d96edb
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: d513ddd41d87da7274f961969d261724b49aab65
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
---
# <a name="token-provider"></a>Belirteç Sağlayıcı
Bu örnek, özel bir belirteç sağlayıcısını uygulamak gösterilmiştir. Bir belirteç sağlayıcısı Windows Communication Foundation (WCF) güvenlik altyapısı için kimlik bilgileri sağladığını için kullanılır. Belirteç sağlayıcı genel hedef inceler ve böylece güvenlik altyapısı ileti güvenliğini sağlayabilirsiniz sorunları kimlik bilgileri gerekli. WCF varsayılan kimlik bilgileri Yöneticisi belirteç sağlayıcısı ile birlikte gelir. WCF de gelir ile bir [!INCLUDE[infocard](../../../../includes/infocard-md.md)] belirteç sağlayıcısı. Özel belirteç sağlayıcılarını aşağıdaki durumlarda yararlı olur:  
  
-   Bu belirteci sağlayıcıları ile çalışamaz bir kimlik bilgisi deposu varsa.  
  
-   Kullanıcı için WCF istemci framework kimlik bilgileri kullandığında ayrıntılarını sağladığında kimlik bilgilerini noktadan dönüştürme için kendi özel mekanizması sağlamak istiyorsanız.  
  
-   Özel belirteç oluşturuluyorsa.  
  
 Bu örnek, kullanıcıdan girdi farklı bir biçime dönüştürür özel bir belirteç sağlayıcısı oluşturmak gösterilmiştir.  
  
 Özetlemek için bu örnek şunlar gösterilmektedir:  
  
-   Nasıl bir istemci bir kullanıcı adı/parola çifti kullanılarak doğrulanabilir.  
  
-   Nasıl bir istemci bir özel belirteç sağlayıcısı ile yapılandırılabilir.  
  
-   Sunucu ile özel bir parola kullanarak istemci kimlik bilgilerini nasıl doğrulayabilir <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> kullanıcı adı ve parola eşleştiğini doğrular.  
  
-   Sunucu sunucunun X.509 sertifikası kullanarak istemci tarafından kimlik doğrulamasının nasıl.  
  
 Bu örnek ayrıca nasıl çağıranının kimliğini özel belirteç kimlik doğrulama işleminden sonra erişilebilen gösterir.  
  
 Hizmet App.config yapılandırma dosyası kullanılarak tanımlanmış hizmet ile iletişim için tek bir uç noktasını kullanıma sunar. Uç nokta bir adresi, bağlama ve bir sözleşme oluşur. Bağlama ile standart bir yapılandırılmış `wsHttpBinding`, hangi kullanır, varsayılan olarak güvenlik iletisi. Bu örnek standart ayarlar `wsHttpBinding` istemci kullanıcı adı kimlik doğrulaması kullanmak için. Hizmet ayrıca serviceCredentials davranışını kullanarak hizmet sertifikası yapılandırır. ServiceCredentials davranış bir hizmet sertifikası yapılandırmanıza olanak sağlar. Bir hizmet sertifikası, hizmetin kimliğini doğrulamak ve ileti koruma sağlamak için bir istemci tarafından kullanılır. Aşağıdaki yapılandırma aşağıdaki Kurulum yönergelerde açıklandığı gibi örnek Kurulum sırasında yüklenen localhost sertifika başvurur.  
  
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
  
 Yapılandırma adı, hizmet uç noktası, bağlama ve sözleşme için mutlak bir adres, istemci uç nokta yapılandırması oluşur. Bağlama istemci uygun ile yapılandırılmış `Mode` ve ileti `clientCredentialType`.  
  
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
  
 Aşağıdaki adımlar, özel bir belirteç sağlayıcısı geliştirmek ve WCF güvenlik framework ile tümleştirmek nasıl gösterir:  
  
1.  Özel bir belirteç sağlayıcısı yazma.  
  
     Örnek kullanıcı adı ve parola özel bir belirteç sağlayıcısını uygular. Parola, bu kullanıcı adı eşleşmelidir. Bu özel belirteç sağlayıcısı yalnızca tanıtım amaçlıdır ve için gerçek dünya dağıtım önerilmez.  
  
     Bu görevi gerçekleştirmek için özel belirteç sağlayıcı türetilen <xref:System.IdentityModel.Selectors.SecurityTokenProvider> sınıfı ve geçersiz kılmalar <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> yöntemi. Bu yöntem oluşturur ve yeni bir döndürür `UserNameSecurityToken`.  
  
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
  
2.  Özel güvenlik belirteci yöneticisi yazma.  
  
     <xref:System.IdentityModel.Selectors.SecurityTokenManager> Oluşturmak için kullanılan <xref:System.IdentityModel.Selectors.SecurityTokenProvider> belirli <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> kendisine geçirilen `CreateSecurityTokenProvider` yöntemi. Güvenlik belirteci Yöneticisi ayrıca belirteç kimlik doğrulayan ve belirteci seri hale getirici oluşturmak için kullanılır, ancak bunlar Bu örnek tarafından kapsanmayan. Bu örnekte, özel güvenlik belirteci yöneticisi devraldığı <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> sınıfı ve geçersiz kılmalar `CreateSecurityTokenProvider` geçirilen belirteci gereksinimleri, kullanıcı adı sağlayıcıyı belirttiğinizde özel kullanıcıadı belirteç sağlayıcısı döndürülecek yöntemi istendi.  
  
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
  
     İstemci kimlik bilgileri sınıfı istemci proxy için yapılandırılmış olan kimlik bilgilerini temsil etmek için kullanılır ve güvenlik belirteci Doğrulayıcı, belirteci sağlayıcıları ve belirteci seri hale getirici elde etmek için kullanılan belirteci yöneticisi oluşturur.  
  
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
  
4.  Özel istemci kimlik bilgisi kullanmak için istemciyi yapılandırın.  
  
     Özel istemci kimlik bilgisi kullanmak istemcinin sırasıyla örnek varsayılan istemci kimlik bilgisi sınıfını siler ve yeni istemci kimlik bilgisi sınıfını sağlar.  
  
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
  
 Arayanın bilgileri görüntülemek için hizmette kullanın <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> aşağıdaki kod örneğinde gösterildiği gibi. <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> Talep geçerli çağıran hakkında bilgi içerir.  
  
```  
static void DisplayIdentityInformation()  
{  
    Console.WriteLine("\t\tSecurity context identity  :  {0}",   
        ServiceSecurityContext.Current.PrimaryIdentity.Name);  
}  
```  
  
 Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir. İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.  
  
## <a name="setup-batch-file"></a>Toplu iş dosyası Kurulumu  
 Bu örnekle dahil Setup.bat toplu iş dosyası, sunucu sertifika tabanlı güvenlik gerektiren kendini barındıran bir uygulamayı çalıştırmak için ilgili sertifika ile sunucu yapılandırmanıza olanak sağlar. Bu toplu iş dosyası bilgisayarlar arasında iş ya da barındırılan olmayan bir durumda çalışması için değiştirilmesi gerekir.  
  
 Aşağıdakiler, böylece uygun yapılandırmada çalışacak biçimde değiştirilebilir toplu iş dosyaları farklı bölümlerini kısa bir genel bakış sağlar:  
  
-   Sunucu sertifikası oluşturuluyor.  
  
     Aşağıdaki satırları Setup.bat toplu iş dosyasından kullanılacak sunucu sertifikası oluşturun. `%SERVER_NAME%` Değişkeni, sunucu adını belirtir. Kendi sunucu adını belirtmek için bu değişkeni değiştirin. Localhost bu toplu iş dosyasında varsayılan değerdir.  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   Sunucu sertifikası istemcinin güvenilen sertifika deposuna yükleme:  
  
     İstemci güvenilir kişiler içine Setup.bat toplu dosya kopyalama sunucu sertifikasının aşağıdaki satırları depolar. MakeCert.exe tarafından oluşturulan sertifikaları örtük olarak istemci sistemi tarafından güvenilir değil çünkü bu adım gereklidir. Bir istemci güvenilen kök sertifikasını kökü belirtilmiş bir sertifikanız zaten varsa — örneğin, bir Microsoft verilen sertifika — sunucu sertifikasına sahip istemci sertifika deposunun doldurulması, bu adım gerekli değildir.  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
> [!NOTE]
>  Setup.bat toplu iş dosyası, Windows SDK komut isteminden çalıştırılması için tasarlanmıştır. MSSDK ortam değişkeni SDK yüklendiği dizinine işaret gerektiriyor. Bu ortam değişkeni, Windows SDK komut istemi içinde otomatik olarak ayarlanır.  
  
#### <a name="to-set-up-and-build-the-sample"></a>Ayarlamak ve örneği oluşturmak için  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözümü derlemek için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a>Aynı bilgisayara örneği çalıştırmak için  
  
1.  Örnek yükleme klasöründen içinde Setup.bat çalıştırmak bir [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemini yönetici ayrıcalıklarıyla açılır. Bu örneği çalıştırmak için gerekli tüm sertifikalar yükler.  
  
    > [!NOTE]
    >  Setup.bat toplu iş dosyası çalıştırılmak üzere tasarlanmış bir [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemi. İçinde PATH ortam değişkeni ayarlamak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemi Setup.bat komut dosyası için gereken yürütülebilir dosyalar içeren dizine işaret eder.  
  
2.  Service\bin gelen Service.exe başlatın.  
  
3.  Client.exe \client\bin başlatın. İstemci etkinliği istemci konsol uygulaması görüntülenir.  
  
4.  Kullanıcı adı isteminde bir kullanıcı adı yazın.  
  
5.  Parola isteminde yazıldı aynı dize kullanıcıadı istem için kullanın.  
  
6.  İstemci ve hizmet iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-run-the-sample-across-computers"></a>Bilgisayarlar arasında örneği çalıştırmak için  
  
1.  Hizmet ikili dosyaları hizmet bilgisayarda bir dizin oluşturun.  
  
2.  Hizmet program dosyalarını hizmeti bilgisayarında hizmet dizinine kopyalayın. Ayrıca Setup.bat ve Cleanup.bat dosyalarını hizmet bilgisayara kopyalayın.  
  
3.  Bilgisayarın tam etki alanı adını içeren konu adına sahip bir sunucu sertifikası olmalıdır. Service.exe.config dosyayı bu yeni sertifika adını yansıtacak şekilde güncelleştirmeniz gerekir. Sunucu sertifikası Setup.bat toplu iş dosyasını değiştirerek oluşturabilirsiniz. Setup.bat dosyasını yönetici ayrıcalıklarıyla açılmış Visual Studio komut isteminden çalıştırmanız gerektiğini unutmayın. Ayarlamalısınız `%SERVER_NAME%` hizmetini barındırmak için kullanılan bilgisayarın tam ana bilgisayar adı için değişken.  
  
4.  Sunucu sertifikası istemci Currentuser'a TrustedPeople depolama alanına kopyalayın. Sunucu sertifikasının güvenilen istemci veren tarafından verildiğinde Bunu yapmak gerekmez.  
  
5.  Hizmeti bilgisayarında Service.exe.config dosyasında localhost yerine bir tam bilgisayar adını belirtmek için taban adresi değerini değiştirin.  
  
6.  Hizmet bilgisayarda service.exe bir komut isteminden çalıştırın.  
  
7.  İstemci program dosyaları \client\bin\ klasöründen dile özgü klasörü altında istemci bilgisayara kopyalayın.  
  
8.  İstemci bilgisayardaki Client.exe.config dosyasında yeni adresi hizmetinizin eşleştirmek için uç nokta adresi değerini değiştirin.  
  
9. İstemci bilgisayarda, başlatma `Client.exe` bir komut istemi penceresinden.  
  
10. İstemci ve hizmet iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-clean-up-after-the-sample"></a>Örnek sonra temizlemek için  
  
1.  Örnek çalıştıran tamamladıktan sonra Cleanup.bat samples klasöründen çalıştırın.  
  
## <a name="see-also"></a>Ayrıca Bkz.
