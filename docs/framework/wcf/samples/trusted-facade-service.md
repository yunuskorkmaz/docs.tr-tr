---
title: Güvenilir Görünüm Hizmeti
ms.date: 03/30/2017
ms.assetid: c34d1a8f-e45e-440b-a201-d143abdbac38
ms.openlocfilehash: 4b02928224f1cb96a25dc71941273625e7d9e5e6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59091557"
---
# <a name="trusted-facade-service"></a>Güvenilir Görünüm Hizmeti
Bu senaryo örneği çağıranın kimlik bilgilerini bir hizmetten diğerine Windows Communication Foundation (WCF) kullanarak akış yapmayı gösteren güvenlik altyapısı.  
  
 Bir cephe hizmeti kullanarak ortak ağ için bir hizmet tarafından sağlanan işlevselliği göstermek için bir ortak bir tasarım örüntüsüdür. Cephe hizmeti genellikle çevre ağındaki (DMZ, sivil bölge ve denetimli alt ağ olarak da bilinir) bulunur ve iş mantığını uygular ve iç verilere erişimi olan bir arka uç hizmetiyle iletişim kurar. Cephe hizmeti ve arka uç hizmeti arasındaki iletişim kanalını bir güvenlik duvarı üzerinden geçer ve yalnızca tek bir amaç için genellikle sınırlıdır.  
  
 Bu örnek aşağıdaki bileşenlerden oluşur:  
  
-   Hesaplayıcı istemci  
  
-   Hesaplayıcı cephe hizmeti  
  
-   Hesaplayıcı arka uç hizmeti  
  
 İstek doğrulanıyor ve arayan kimlik doğrulaması için sorumlu cephe hizmetidir. Başarılı kimlik doğrulaması ve doğrulama sonra istek iç ağ çevre ağından denetimli iletişim kanalını kullanarak arka uç hizmetine iletir. Bu bilgiler, işleme, arka uç hizmetine kullanabilmesi iletilen isteğin bir parçası olarak cephe hizmet çağıranının kimliğini hakkında bilgi içerir. Çağıranının kimliğini kullanarak iletilen bir `Username` ileti içinde güvenlik belirteci `Security` başlığı. Örnek, iletme ve bu bilgileri ayıklamak için WCF güvenlik altyapısı kullanır. `Security` başlığı.  
  
> [!IMPORTANT]
>  Arayan kimliğini doğrulamak için cephe hizmet arka uç hizmetine güvenir. Bu nedenle, arka uç hizmeti çağıran yeniden kimlik doğrulamasını yapmaz; iletilen istek cephe hizmeti tarafından sağlanan kimlik bilgilerini kullanır. Bu güven ilişkisi nedeniyle, arka uç hizmetine yönlendirilmiş ileti güvenilir bir kaynaktan - bu durumda, cephe hizmet geldiğinden emin olmak için cephe hizmet kimlik doğrulaması gerekir.  
  
## <a name="implementation"></a>Uygulama  
 Bu örnekte iki iletişim yolları vardır. İlk istemci ile cephe hizmeti arasında cephe hizmeti ve arka uç hizmeti arasında saniyedir.  
  
### <a name="communication-path-between-client-and-faade-service"></a>Cephe hizmet ve istemci arasındaki iletişim yolunun  
 Cephe hizmet iletişimi yolu istemcinin kullandığı `wsHttpBinding` ile bir `UserName` istemci kimlik bilgisi türü. Bu, istemcinin kullandığı kullanıcı adı ve cephe hizmet ve cephe hizmet kimlik doğrulaması için parola, istemcinin kimliğini doğrulamak için X.509 sertifikası kullanır. anlamına gelir. Bağlama yapılandırması aşağıdaki örnekteki gibi görünür.  
  
```xml  
<bindings>  
  <wsHttpBinding>  
    <binding name="Binding1">  
      <security mode="Message">  
        <message clientCredentialType="UserName"/>  
      </security>  
    </binding>  
  </wsHttpBinding>  
</bindings>  
```  
  
 Cephe hizmeti çağıran özel kullanarak kimlik doğrulaması `UserNamePasswordValidator` uygulaması. Tanıtım amacıyla, arayanın kullanıcıadı sunulan parolayla eşleşen kimlik doğrulaması yalnızca sağlar. Gerçek dünya durumda kullanıcı Active Directory veya özel ASP.NET üyelik sağlayıcıyı kullanarak büyük olasılıkla doğrulanır. Doğrulayıcı uygulama bulunan `FacadeService.cs` dosya.  
  
```  
public class MyUserNamePasswordValidator : UserNamePasswordValidator  
{  
    public override void Validate(string userName, string password)  
    {  
        // check that username matches password  
        if (null == userName || userName != password)  
        {  
            Console.WriteLine("Invalid username or password");  
            throw new SecurityTokenValidationException(  
                       "Invalid username or password");  
        }  
    }  
}  
```  
  
 Özel Doğrulayıcı sağlayıcısı içinde kullanılmak üzere yapılandırılmış `serviceCredentials` cephe hizmet yapılandırma dosyasında bir davranış. Bu davranış, hizmetin X.509 sertifikası yapılandırmak için de kullanılır.  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="FacadeServiceBehavior">  
      <!--The serviceCredentials behavior allows you to define -->  
      <!--a service certificate. -->  
      <!--A service certificate is used by the service to  -->  
      <!--authenticate itself to its clients and to provide  -->  
      <!--message protection. -->  
      <!--This configuration references the "localhost"  -->  
      <!--certificate installed during the setup instructions. -->  
      <serviceCredentials>  
        <serviceCertificate   
               findValue="localhost"   
               storeLocation="LocalMachine"   
               storeName="My"   
               x509FindType="FindBySubjectName" />  
        <userNameAuthentication userNamePasswordValidationMode="Custom"  
            customUserNamePasswordValidatorType=  
           "Microsoft.ServiceModel.Samples.MyUserNamePasswordValidator,  
            FacadeService"/>  
      </serviceCredentials>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
### <a name="communication-path-between-faade-service-and-backend-service"></a>Cephe hizmeti ve arka uç hizmeti arasındaki iletişim yolunun  
 Arka uç hizmeti iletişim yolunun cephe hizmete kullanan bir `customBinding` çeşitli bağlama öğelerinin oluşur. Bu bağlamanın iki şeyi gerçekleştirir. Cephe hizmeti ve iletişimi güvenli ve güvenilir bir kaynaktan geldiğine emin olmak için arka uç hizmeti kimliğini doğrular. Ayrıca, içinde ilk çağıranının kimliğini de iletir `Username` güvenlik belirteci. Bu durumda, yalnızca ilk çağrı sahibinin kullanıcı adı arka uç hizmetine aktarılır, parola iletisinde yer almaz. Çağıran, iletilmeden önce kimlik doğrulaması için cephe hizmet arka uç hizmetine güvenir olmasıdır. Cephe hizmetin kendisini arka uç hizmetine doğruladığından, arka uç hizmetine iletilmiş istekte yer alan bilgileri güvenebilir.  
  
 Bu iletişim yolunun bağlama yapılandırması aşağıda verilmiştir.  
  
```xml  
<bindings>  
  <customBinding>  
    <binding name="ClientBinding">  
      <security authenticationMode="UserNameOverTransport"/>  
      <windowsStreamSecurity/>  
      <tcpTransport/>  
    </binding>  
  </customBinding>  
</bindings>  
```  
  
 [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) bağlama öğesi, ilk çağrı sahibinin kullanıcı adı iletim ve ayıklama üstlenir. [ \<WindowsStreamSecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/windowsstreamsecurity.md) ve [ \<Connectionpoolsettings >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) cephe ve arka uç Hizmetleri kimlik doğrulaması dikkatli ve ileti koruma.  
  
 İsteği iletmek için cephe hizmet uygulaması, WCF güvenlik altyapısı bu yönlendirilmiş ileti yerleştirebilirsiniz için ilk çağrı sahibinin kullanıcı adı sağlamalısınız. İlk çağrı sahibinin kullanıcı adı olarak ayarlayarak cephe hizmet uygulamasında sağlanan `ClientCredentials` özelliği istemci proxy örneğinde cephe hizmet arka uç hizmetiyle iletişim kurmak için kullanır.  
  
 Aşağıdaki kodda gösterildiği nasıl `GetCallerIdentity` yöntemi cephe hizmette uygulanır. Aynı düzeni diğer yöntemleri kullanın.  
  
```  
public string GetCallerIdentity()  
{  
    CalculatorClient client = new CalculatorClient();  
    client.ClientCredentials.UserName.UserName = ServiceSecurityContext.Current.PrimaryIdentity.Name;  
    string result = client.GetCallerIdentity();  
    client.Close();  
    return result;  
}  
```  
  
 Önceki kodda gösterildiği gibi parola üzerinde ayarlı değil `ClientCredentials` özelliği, yalnızca kullanıcı adı ayarlanır. WCF güvenlik altyapısı tam olarak bu senaryoda, gerekli olduğu bir kullanıcı adı güvenlik belirtecini bir parola olmadan bu durumda, oluşturur.  
  
 Kullanıcı adı güvenlik belirtecinde yer alan bilgileri üzerindeki arka uç hizmeti, kimliğinin doğrulanması gerekir. Varsayılan olarak, WCF güvenlik belirtilen parola kullanılarak bir Windows hesabı kullanıcı eşlemeyi dener. Bu durumda, sağlanan parolası yoktur ve arka uç hizmeti kimlik doğrulaması zaten cephe hizmeti tarafından gerçekleştirildiği için kullanıcı adı kimlik doğrulaması için gerekli değildir. WCF'de özel bu işlevselliği uygulamak için `UserNamePasswordValidator` , yalnızca bir kullanıcı adı belirteci belirtilir ve herhangi ek bir kimlik doğrulaması gerçekleştirmez zorlar sağlanır.  
  
```  
public class MyUserNamePasswordValidator : UserNamePasswordValidator  
{  
    public override void Validate(string userName, string password)  
    {  
        // Ignore the password because it is empty,   
        // we trust the facade service to authenticate the client.  
        // Accept the username information here so that the   
        // application gets access to it.  
        if (null == userName)  
        {  
            Console.WriteLine("Invalid username");  
            throw new   
             SecurityTokenValidationException("Invalid username");  
        }  
    }  
}  
```  
  
 Özel Doğrulayıcı sağlayıcısı içinde kullanılmak üzere yapılandırılmış `serviceCredentials` cephe hizmet yapılandırma dosyasında bir davranış.  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="BackendServiceBehavior">  
      <serviceCredentials>  
        <userNameAuthentication userNamePasswordValidationMode="Custom"  
           customUserNamePasswordValidatorType=  
          "Microsoft.ServiceModel.Samples.MyUserNamePasswordValidator,   
           BackendService"/>  
      </serviceCredentials>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 Güvenilen bir cephe hizmet hesabıyla ilgili bilgileri ve kullanıcı adı bilgileri ayıklamak için arka uç hizmeti uygulaması kullanan `ServiceSecurityContext` sınıfı. Aşağıdaki kodda gösterildiği nasıl `GetCallerIdentity` yöntemi uygulanır.  
  
```  
public string GetCallerIdentity()  
{  
    // Facade service is authenticated using Windows authentication.  
    //Its identity is accessible.  
    // On ServiceSecurityContext.Current.WindowsIdentity.  
    string facadeServiceIdentityName =   
          ServiceSecurityContext.Current.WindowsIdentity.Name;  
  
    // The client name is transmitted using Username authentication on   
    //the message level without the password  
    // using a supporting encrypted UserNameToken.  
    // Claims extracted from this supporting token are available in   
    // ServiceSecurityContext.Current.AuthorizationContext.ClaimSets   
    // collection.  
    string clientName = null;  
    foreach (ClaimSet claimSet in   
        ServiceSecurityContext.Current.AuthorizationContext.ClaimSets)  
    {  
        foreach (Claim claim in claimSet)  
        {  
            if (claim.ClaimType == ClaimTypes.Name &&   
                                   claim.Right == Rights.Identity)  
            {  
                clientName = (string)claim.Resource;  
                break;  
            }  
        }  
    }  
    if (clientName == null)  
    {  
        // In case there was no UserNameToken attached to the request.  
        // In the real world implementation the service should reject   
        // this request.  
        return "Anonymous caller via " + facadeServiceIdentityName;  
    }  
  
    return clientName + " via " + facadeServiceIdentityName;  
}  
```  
  
 Cephe hizmet hesabı bilgilerini kullanarak ayıkladığınız `ServiceSecurityContext.Current.WindowsIdentity` özelliği. Arka uç hizmeti kullandığı ilk çağrıda bulunanı hakkında bilgilere erişmek için `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` özelliği. Görünüşe göre yenisiniz bir `Identity` talep türü ile `Name`. Bu talep yer alan bilgileri WCF güvenlik altyapısı tarafından otomatik olarak oluşturulan `Username` güvenlik belirteci.  
  
## <a name="running-the-sample"></a>Örneği çalıştırma  
 Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir. İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın. Hizmetleri kapatılmaya için cephe ve arka uç hizmet Konsolu pencerelerinde ENTER tuşuna basın.  
  
```  
Username authentication required.  
Provide a valid machine or domain ac  
   Enter username:  
user  
   Enter password:  
****  
user via MyMachine\testaccount  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 Güvenilir görünüm senaryo örneği ile dahil Setup.bat toplu iş dosyasını kendisini istemcinin kimliğini doğrulamak için sertifika tabanlı güvenlik gerektiren bir cephe hizmeti çalıştırmak için ilgili bir sertifika ile sunucu yapılandırmanızı sağlar. Ayrıntılar için bu konunun sonunda Kurulum yordamına bakın.  
  
 Toplu iş dosyaları farklı bölümlerini kısa bir genel bakış sağlar.  
  
-   Sunucu sertifikası oluşturuluyor.  
  
     Setup.bat toplu iş dosyasından aşağıdaki satırları kullanılacak sunucu sertifikası oluşturun.  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     `%SERVER_NAME%` Değişkeni, sunucu adını belirtir: localhost varsayılan değerdir. Depolanmış bir sertifikayla LocalMachine depolama.  
  
-   Cephe hizmetin sertifika istemcinin güvenilen sertifika depolama alanına yükleniyor.  
  
     Aşağıdaki satırı cephe hizmetin sertifika istemcisi güvenilir Kişiler deposuna kopyalar. MakeCert.exe tarafından oluşturulan sertifikaları örtük olarak istemci sistemi tarafından güvenilir değildir çünkü bu adım gereklidir. Bir istemci güvenilen kök sertifikayı kök erişim izni verilmiş bir sertifika zaten varsa — örneğin, Microsoft tarafından verilen sertifika — sunucu sertifikasında istemci sertifika deposunun doldurulması, bu adım gerekli değildir.  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a>Örneği aynı makinede çalıştırmak için  
  
1.  Yolun Makecert.exe bulunduğu klasörü içerdiğinden emin olun.  
  
2.  Setup.bat örnek yükleme klasöründen çalıştırın. Bu örneği çalıştırmak için gerekli olan tüm sertifikaları yükler.  
  
3.  Ayrı konsol penceresinde \BackendService\bin dizinden BackendService.exe başlatın  
  
4.  Ayrı konsol penceresinde \FacadeService\bin dizinden FacadeService.exe başlatın  
  
5.  Client.exe \client\bin başlatın. İstemci etkinliği istemci konsol uygulamasında görüntülenir.  
  
6.  İstemci ve hizmet iletişim kurabildiğini bilmiyorsanız bkz [WCF örnekleri için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-clean-up-after-the-sample"></a>Sonra örnek temizlemek için  
  
1.  Bu örneği çalıştırmadan tamamladıktan sonra Cleanup.bat samples klasöründe çalıştırın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\TrustedFacade`  
