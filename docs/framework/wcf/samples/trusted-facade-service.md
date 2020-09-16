---
title: Güvenilir Görünüm Hizmeti
ms.date: 03/30/2017
ms.assetid: c34d1a8f-e45e-440b-a201-d143abdbac38
ms.openlocfilehash: e9459b4cc26ef85adcc59c308d92491fd2d3acba
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90544186"
---
# <a name="trusted-facade-service"></a>Güvenilir Görünüm Hizmeti
Bu senaryo örneği, arayanın kimlik bilgilerinin bir hizmetten diğerine Windows Communication Foundation (WCF) güvenlik altyapısını kullanarak nasıl akabileceğinizi gösterir.  
  
 Bir hizmet tarafından bir hizmet tarafından sunulan işlevselliği bir façlade hizmeti kullanılarak kullanıma sunmak için ortak bir tasarım modelidir. Façlade hizmeti genellikle çevre ağında (DMZ, sivil bölge ve denetimli alt ağ olarak da bilinir) bulunur ve iş mantığını uygulayan ve iç verilere erişim sağlayan bir arka uç hizmetiyle iletişim kurar. Façlade hizmeti ile arka uç hizmeti arasındaki iletişim kanalı bir güvenlik duvarından geçer ve genellikle yalnızca tek bir amaçla sınırlandırılır.  
  
 Bu örnek aşağıdaki bileşenlerden oluşur:  
  
- Hesaplayıcı istemcisi  
  
- Hesaplayıcı façlade hizmeti  
  
- Hesaplayıcı arka uç hizmeti  
  
 Façlade hizmeti, isteği doğrulamadan ve arayanın kimliğini doğrulamaya sorumludur. Başarılı kimlik doğrulama ve doğrulamadan sonra, çevre ağdan iç ağa denetimli iletişim kanalını kullanarak isteği arka uç hizmetine iletir. İletilen isteğin bir parçası olarak, façlade hizmeti çağıranın kimliği hakkında bilgiler içerir, böylece arka uç hizmeti bu bilgileri işlemede kullanabilir. Arayanın kimliği, `Username` ileti üstbilgisinin içindeki bir güvenlik belirteci kullanılarak iletilir `Security` . Örnek, bu bilgileri üst bilgiden iletmek ve ayıklamak için WCF güvenlik altyapısını kullanır `Security` .  
  
> [!IMPORTANT]
> Arka uç hizmeti, arayanın kimliğini doğrulamak için façlade hizmetine güvenir. Bu nedenle, arka uç hizmeti çağıranın kimliğini doğrulamaz; Bu, iletilen istekte façlade hizmeti tarafından sunulan kimlik bilgilerini kullanır. Bu güven ilişkisi nedeniyle, arka uç hizmeti, iletilen iletinin güvenilen bir kaynaktan geldiğinden emin olmak için façlade hizmetinin kimliğini doğrulamalıdır; bu durumda façlade hizmeti.  
  
## <a name="implementation"></a>Uygulama  
 Bu örnekte iki iletişim yolu vardır. İlk olarak istemci ile façlade hizmeti arasında ikinci değer façlade hizmeti ve arka uç hizmeti arasındadır.  
  
### <a name="communication-path-between-client-and-faade-service"></a>Istemci ile Façlade hizmeti arasındaki iletişim yolu  
 Façlade hizmeti iletişim yolunun istemcisi `wsHttpBinding` `UserName` istemci kimlik bilgisi türü ile kullanır. Bu, istemcinin façlade hizmetinde kimlik doğrulamak için Kullanıcı adı ve parola kullandığı ve façlade hizmetinin istemcide kimlik doğrulamak için X. 509.440 sertifikası kullandığı anlamına gelir. Bağlama yapılandırması aşağıdaki örneğe benzer şekilde görünür.  
  
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
  
 Façlade hizmeti, özel uygulama kullanarak arayanın kimliğini doğrular `UserNamePasswordValidator` . Tanıtım amacıyla, kimlik doğrulaması yalnızca arayanın Kullanıcı adının görüntülenen parolayla eşleşmesini sağlar. Gerçek dünyada, kullanıcının kimliği büyük olasılıkla Active Directory veya özel ASP.NET üyelik sağlayıcısı kullanılarak doğrulanır. Doğrulayıcı uygulama `FacadeService.cs` dosyasında bulunur.  
  
```csharp  
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
  
 Özel Doğrulayıcı, `serviceCredentials` façlade hizmeti yapılandırma dosyasındaki davranış içinde kullanılmak üzere yapılandırılır. Bu davranış, hizmetin X. 509.440 sertifikasını yapılandırmak için de kullanılır.  
  
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
  
### <a name="communication-path-between-faade-service-and-backend-service"></a>Façlade hizmeti ile arka uç hizmeti arasındaki iletişim yolu  
 Arka uç hizmeti iletişim yolunda façlade hizmeti, `customBinding` çeşitli bağlama öğelerinden oluşan bir kullanır. Bu bağlama iki şeyi gerçekleştirir. İletişimin güvenli olduğundan ve güvenilen bir kaynaktan geldiğinden emin olmak için façlade hizmeti ve arka uç hizmeti 'nin kimliğini doğrular. Ayrıca, güvenlik belirtecinin içindeki ilk arayanın kimliğini de iletir `Username` . Bu durumda, yalnızca ilk arayanın Kullanıcı adı arka uç hizmetine iletilir, parola iletiye eklenmez. Bunun nedeni, arka uç hizmetinin isteği kendisine iletmeden önce arayanın kimliğini doğrulamak üzere façlade hizmetine güvenmesidir. Façlade hizmeti kendi arka uç hizmetinde kimliğini doğruladığından, arka uç hizmeti iletilen istekte bulunan bilgilere güvenebilirler.  
  
 Bu iletişim yolu için bağlama yapılandırması aşağıda verilmiştir.  
  
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
  
 [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md)Bağlama öğesi, ilk çağıranın Kullanıcı adı iletimi ve ayıklama işlemini gerçekleştirir. [\<windowsStreamSecurity>](../../configure-apps/file-schema/wcf/windowsstreamsecurity.md)Ve, [\<tcpTransport>](../../configure-apps/file-schema/wcf/tcptransport.md) façlade ve arka uç hizmetleri ile ileti korumasının kimlik doğrulamasını yapın.  
  
 İsteği iletmek için, façlade Hizmeti uygulamasının ilk çağıranın Kullanıcı adını sağlaması gerekir, böylece WCF güvenlik altyapısı bunu iletilen iletiye yerleştirebilir. İlk arayanın Kullanıcı adı, façlade hizmeti 'nin `ClientCredentials` arka uç hizmetiyle iletişim kurmak için bir istemci ara sunucu örneğindeki özelliğinde ayarlanarak façlade hizmeti uygulamasında sağlanır.  
  
 Aşağıdaki kod, `GetCallerIdentity` yöntemin façlade hizmetinde nasıl uygulandığını gösterir. Diğer yöntemler aynı kalıbı kullanır.  
  
```csharp  
public string GetCallerIdentity()  
{  
    CalculatorClient client = new CalculatorClient();  
    client.ClientCredentials.UserName.UserName = ServiceSecurityContext.Current.PrimaryIdentity.Name;  
    string result = client.GetCallerIdentity();  
    client.Close();  
    return result;  
}  
```  
  
 Önceki kodda gösterildiği gibi, bu, özelliği üzerinde de ayarlanır `ClientCredentials` , yalnızca Kullanıcı adı ayarlanır. WCF güvenlik altyapısı bu durumda bir parola olmadan bir Kullanıcı adı güvenlik belirteci oluşturur; Bu, tam olarak bu senaryoda gerekli olan şeydir.  
  
 Arka uç hizmetinde, Kullanıcı adı güvenlik belirtecinde bulunan bilgilerin kimliği doğrulanmalıdır. Varsayılan olarak, WCF güvenliği, belirtilen parolayı kullanarak kullanıcıyı bir Windows hesabıyla eşlemeye çalışır. Bu durumda, kimlik doğrulaması façlade hizmeti tarafından zaten gerçekleştirildiğinden Kullanıcı adının kimliğini doğrulamak için bir parola sağlanmadı ve arka uç hizmeti gerekli değildir. WCF 'de bu işlevselliği uygulamak için, `UserNamePasswordValidator` yalnızca belirteçte bir kullanıcı adının belirtilmesini zorladığı ve ek kimlik doğrulama gerçekleştirmediğinden özel bir özel sağlanır.  
  
```csharp  
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
  
 Özel Doğrulayıcı, `serviceCredentials` façlade hizmeti yapılandırma dosyasındaki davranış içinde kullanılmak üzere yapılandırılır.  
  
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
  
 Kullanıcı adı bilgilerini ve güvenilir façlade Hizmeti hesabıyla ilgili bilgileri ayıklamak için arka uç hizmet uygulamasının `ServiceSecurityContext` sınıfını kullanır. Aşağıdaki kod yöntemin nasıl uygulandığını gösterir `GetCallerIdentity` .  
  
```csharp  
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
  
 Façlade hizmeti hesap bilgileri, özelliği kullanılarak ayıklanır `ServiceSecurityContext.Current.WindowsIdentity` . İlk çağıran ile ilgili bilgilere erişmek için arka uç hizmeti `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` özelliğini kullanır. `Identity`Bir türü olan bir talep arar `Name` . Bu talep, güvenlik belirtecinde bulunan bilgilerden WCF güvenlik altyapısı tarafından otomatik olarak oluşturulur `Username` .  
  
## <a name="running-the-sample"></a>Örneği çalıştırma  
 Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir. İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın. Hizmeti kapatmak için façlade ve arka uç hizmeti konsol penceresinde ENTER tuşuna basabilirsiniz.  
  
```console  
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
  
 Güvenilir Faon yıl örneğine dahil olan Setup.bat Batch dosyası, istemci için kimlik doğrulaması yapmak üzere sertifika tabanlı güvenlik gerektiren façlade hizmetini çalıştırmak üzere sunucuyu ilgili sertifikayla yapılandırmanızı sağlar. Ayrıntılar için bu konunun sonundaki Kurulum yordamına bakın.  
  
 Aşağıdakiler, toplu iş dosyalarının farklı bölümlerine kısa bir genel bakış sağlar.  
  
- Sunucu sertifikası oluşturuluyor.  
  
     Setup.bat Batch dosyasından aşağıdaki satırlar kullanılacak sunucu sertifikasını oluşturur.  
  
    ```console  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     `%SERVER_NAME%`Değişken, sunucu adını belirtir; varsayılan değer localhost 'tur. Sertifika, LocalMachine deposunda depolanır.  
  
- Façlade hizmetinin sertifikasını istemcinin güvenilen sertifika deposuna yükleme.  
  
     Aşağıdaki satır façlade hizmeti sertifikasını istemci güvenilir kişiler deposuna kopyalar. Makecert.exe tarafından oluşturulan sertifikalara istemci sistemi tarafından örtük olarak güvenilmediğinden Bu adım gereklidir. İstemci tarafından güvenilen kök sertifikada kök sertifikaya sahip bir sertifikanız zaten varsa (örneğin, Microsoft tarafından verilen bir sertifika), istemci sertifikası deposunu sunucu sertifikasıyla doldurmanın bu adımı gerektirmez.  
  
    ```console  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a>Örneği aynı makinede çalıştırmak için  
  
1. Yolun Makecert.exe bulunduğu klasörü içerdiğinden emin olun.  
  
2. Örnek yüklemesi klasöründen Setup.bat çalıştırın. Bu, örneği çalıştırmak için gereken tüm sertifikaları kurar.  
  
3. \BackendService\bin dizininden BackendService.exe ayrı bir konsol penceresinde başlatın  
  
4. Ayrı bir konsol penceresinde \FacadeService\bin dizininden FacadeService.exe başlatın  
  
5. \Client\bin. 'den başlatma Client.exe İstemci etkinliği istemci konsol uygulamasında görüntülenir.  
  
6. İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-clean-up-after-the-sample"></a>Örnekten sonra temizlemek için  
  
1. Örneği çalıştırmayı bitirdikten sonra Samples klasöründe Cleanup.bat çalıştırın.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\TrustedFacade`
