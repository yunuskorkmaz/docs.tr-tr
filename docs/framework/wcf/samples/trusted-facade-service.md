---
title: Güvenilir Görünüm Hizmeti
ms.date: 03/30/2017
ms.assetid: c34d1a8f-e45e-440b-a201-d143abdbac38
ms.openlocfilehash: d5a4cfe63f2fc6facbe4ce78d1c0047349e303fd
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
---
# <a name="trusted-facade-service"></a>Güvenilir Görünüm Hizmeti
Bu senaryo örneği başka bir Windows Communication Foundation (WCF) kullanarak bir hizmetten Arayanın kimlik bilgileri akış yapmayı gösteren güvenlik altyapısı.  
  
 Cephesi hizmetini kullanan bir ortak ağa hizmeti tarafından sağlanan işlevselliği kullanıma sunmak için ortak bir tasarım deseni değil. Cephesi hizmeti genellikle çevre ağındaki (DMZ, sivil bölge ve denetimli alt ağ olarak da bilinir) bulunur ve iş mantığını uygular ve iç verilere erişimi olan bir arka uç hizmeti ile iletişim kurar. Cephesi hizmeti ve arka uç hizmeti arasındaki iletişim kanalını bir güvenlik duvarı üzerinden gider ve yalnızca tek bir amaç için genellikle sınırlıdır.  
  
 Bu örnek aşağıdaki bileşenlerden oluşur:  
  
-   Hesaplayıcı istemci  
  
-   Hesaplayıcı cephesi hizmeti  
  
-   Hesaplayıcı arka uç hizmeti  
  
 Cephesi hizmet isteği doğrulanırken ve arayan kimlik doğrulaması için sorumludur. Başarılı kimlik doğrulama ve doğrulama sonra iç ağ çevre ağından denetimli iletişim kanalını kullanarak arka uç hizmeti isteği iletir. Bu bilgiler, işleme, arka uç hizmetine kullanabilmesi iletilen isteğin bir parçası olarak cephesi hizmeti arayanın kimliği hakkındaki bilgileri içerir. Arayanın Kimliği kullanılarak aktarılan bir `Username` güvenlik belirteci ileti içine `Security` üstbilgi. Örnek, iletme ve bu bilgileri ayıklamak için WCF güvenlik altyapısı kullanır. `Security` üstbilgi.  
  
> [!IMPORTANT]
>  Arka uç hizmetine arayan kimliğini doğrulamak için cephesi hizmet güvenir. Bu nedenle, arka uç hizmetine çağıran yeniden kimlik doğrulama kullanmaz; iletilen istek cephesi hizmeti tarafından sağlanan kimlik bilgilerini kullanır. Bu güven ilişkisinin bozulması nedeniyle, arka uç hizmetine yönlendirilmiş ileti güvenilir bir kaynaktan - bu durumda, cephesi hizmet geldiğinden emin olmak için cephesi hizmetinde kimlik doğrulaması gerekir.  
  
## <a name="implementation"></a>Uygulama  
 Bu örnekte iki iletişim yolları vardır. İlk istemci ve cephesi hizmeti arasındaki cephesi hizmeti ve arka uç hizmeti arasında saniyedir.  
  
### <a name="communication-path-between-client-and-faade-service"></a>Cephesi hizmet ve istemci arasındaki iletişim yolunun  
 Cephesi hizmet iletişimi yolu istemcinin kullandığı `wsHttpBinding` ile bir `UserName` istemci kimlik bilgisi türü. Bu kullanıcı adı istemci kullanır ve cephesi hizmeti ve cephesi hizmeti için kimlik doğrulaması için parola X.509 sertifikası istemcinin kimliğini doğrulamak için kullanır. anlamına gelir. Bağlama yapılandırması aşağıdaki gibi görünür.  
  
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
  
 Özel kullanarak arayana cephesi hizmeti kimlik doğrulaması `UserNamePasswordValidator` uygulaması. Tanıtım amacıyla, çağıranın kullanıcıadı sunulan parola eşleşen kimlik doğrulaması yalnızca sağlar. Gerçek dünya durumda kullanıcının büyük olasılıkla Active Directory veya özel ASP.NET üyelik sağlayıcısı kullanılarak kimliği doğrulanır. Doğrulayıcı uygulama bulunan `FacadeService.cs` dosya.  
  
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
  
 Özel Doğrulayıcı içinde kullanılmak üzere yapılandırılmış `serviceCredentials` cephesi hizmet yapılandırma dosyasında davranışı. Bu davranış, hizmetin X.509 sertifikası yapılandırmak için de kullanılır.  
  
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
  
### <a name="communication-path-between-faade-service-and-backend-service"></a>Cephesi hizmeti ve arka uç hizmeti arasındaki iletişimi yol  
 Arka uç hizmeti iletişimi yolu cephesi hizmete kullanan bir `customBinding` birkaç bağlama öğelerden oluşur. Bu bağlamanın iki şey gerçekleştirir. Cephesi hizmeti ve iletişimin güvenli ve güvenilir bir kaynaktan geldiğinden emin olmak için arka uç hizmeti kimliğini doğrular. Ayrıca, içinde ilk çağıranının kimliğini de iletir `Username` güvenlik belirteci. Bu durumda yalnızca ilk arayanın kullanıcı adı arka uç hizmetine aktarılır, parola iletide yer almaz. Çağıran, iletilmeden önce kimlik doğrulaması için cephesi hizmet arka uç hizmetine güvenir olmasıdır. Cephesi hizmeti kendisini arka uç hizmetine kimlik doğrulaması için arka uç hizmetine iletilen istekte yer alan bilgileri güvenebilirsiniz.  
  
 Bu iletişim yolunun bağlama yapılandırması verilmiştir.  
  
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
  
 [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) bağlama öğesi ilk arayanın kullanıcıadı iletim ve ayıklama mvc'deki. [ \<WindowsStreamSecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/windowsstreamsecurity.md) ve [ \<Connectionpoolsettings >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) cephesi ve arka uç hizmetlerinin kimlik doğrulaması dikkatli ve ileti koruma.  
  
 İstek iletmek için cephesi hizmet uygulaması, WCF güvenlik altyapı bu yönlendirilmiş ileti koyabilirsiniz şekilde ilk arayanın kullanıcı adı sağlamalısınız. İlk arayanın adı ayarlayarak cephesi hizmet uygulamasında sağlanır `ClientCredentials` istemci proxy örneği özellikte cephesi hizmet arka uç hizmeti ile iletişim için kullanır.  
  
 Aşağıdaki kodda gösterildiği nasıl `GetCallerIdentity` yöntemi cephesi hizmette uygulanır. Diğer yöntemleri aynı düzeni kullanın.  
  
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
  
 Önceki kodda gösterildiği gibi parola ayarlanmamış `ClientCredentials` özelliği, yalnızca kullanıcı adı olarak ayarlanmış. WCF güvenlik altyapısı tam olarak bu senaryoda gerekli olduğu bir kullanıcı adı güvenlik belirteci parolasız bu durumda, oluşturur.  
  
 Arka uç hizmeti kullanıcıadı güvenlik belirtecinde yer alan bilgileri kimliğinin doğrulanması gerekir. Varsayılan olarak, WCF güvenlik belirtilen parola kullanılarak bir Windows hesabı kullanıcı eşlemeyi dener. Bu durumda, sağlanan parola yoktur ve arka uç hizmetine kimlik doğrulaması cephesi hizmeti tarafından zaten gerçekleştirildiği için kullanıcı kimlik doğrulaması için gerekli değildir. Bu işlevsellik, WCF, özel bir uygulamak için `UserNamePasswordValidator` , yalnızca bir kullanıcı adı belirteç belirtilir ve herhangi bir ek kimlik doğrulaması gerçekleştirmez zorlayan sağlanır.  
  
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
  
 Özel Doğrulayıcı içinde kullanılmak üzere yapılandırılmış `serviceCredentials` cephesi hizmet yapılandırma dosyasında davranışı.  
  
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
  
 Kullanıcı adı bilgileri ve güvenilir cephesi hizmet hesabı hakkındaki bilgileri ayıklamak için arka uç hizmeti uygulaması kullanır `ServiceSecurityContext` sınıfı. Aşağıdaki kodda gösterildiği nasıl `GetCallerIdentity` yöntemi uygulanır.  
  
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
  
 Cephesi hizmeti hesap bilgileri kullanılarak elde `ServiceSecurityContext.Current.WindowsIdentity` özelliği. İlk çağıran hakkında bilgi arka uç hizmeti kullandığı erişmek için `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` özelliği. Görünüyor bir `Identity` talep türü ile `Name`. Bu talep WCF güvenlik altyapısı içinde yer alan bilgileri tarafından otomatik olarak oluşturulan `Username` güvenlik belirteci.  
  
## <a name="running-the-sample"></a>Örnek çalışıyor  
 Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir. İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın. Hizmetleri kapatılmaya için cephesi ve arka uç hizmet Konsolu pencerelerinde ENTER tuşuna basabilirsiniz.  
  
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
  
 Güvenilir görünüm senaryo örneği ile dahil Setup.bat toplu iş dosyası, sunucu istemciye kendi kimliğini doğrulamak için sertifika tabanlı güvenlik gerektiren cephesi hizmeti çalıştırmak için uygun bir sertifika ile yapılandırmak sağlar. Ayrıntılar için bu konunun sonundaki Kurulum yordamına bakın.  
  
 Toplu iş dosyaları farklı bölümlerini kısa bir genel bakış sağlar.  
  
-   Sunucu sertifikası oluşturuluyor.  
  
     Aşağıdaki satırları Setup.bat toplu iş dosyasından kullanılacak sunucu sertifikası oluşturun.  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     `%SERVER_NAME%` Değişkeni, sunucu adını belirtir - localhost varsayılan değerdir. Sertifika saklanır LocalMachine deposundaki.  
  
-   Cephesi hizmetin sertifikası istemcinin güvenilen sertifika deposuna yükleme.  
  
     Aşağıdaki satırı cephesi hizmetin sertifikası istemcinin güvenilir Kişiler deposuna kopyalar. MakeCert.exe tarafından oluşturulan sertifikaları örtük olarak istemci sistemi tarafından güvenilir değil çünkü bu adım gereklidir. Bir istemci güvenilen kök sertifikasını kökü belirtilmiş bir sertifikanız zaten varsa — örneğin, Microsoft tarafından verilen sertifika — sunucu sertifikasına sahip istemci sertifika deposunun doldurulması, bu adım gerekli değildir.  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a>Aynı makinede örneği çalıştırmak için  
  
1.  Yolun Makecert.exe bulunduğu klasörü içerdiğinden emin olun.  
  
2.  Setup.bat örnek yükleme klasöründen çalıştırın. Bu örneği çalıştırmak için gerekli tüm sertifikalar yükler.  
  
3.  Ayrı konsol penceresinde \BackendService\bin dizininden BackendService.exe başlatma  
  
4.  Ayrı konsol penceresinde \FacadeService\bin dizininden FacadeService.exe başlatma  
  
5.  Client.exe \client\bin başlatın. İstemci etkinliği istemci konsol uygulaması görüntülenir.  
  
6.  İstemci ve hizmet iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-clean-up-after-the-sample"></a>Örnek sonra temizlemek için  
  
1.  Örnek çalıştıran tamamladıktan sonra Cleanup.bat samples klasöründen çalıştırın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\TrustedFacade`  
  
## <a name="see-also"></a>Ayrıca Bkz.
