---
title: Güvenilir Görünüm Hizmeti
ms.date: 03/30/2017
ms.assetid: c34d1a8f-e45e-440b-a201-d143abdbac38
ms.openlocfilehash: 17901b7a68d4701287d02bc7ee3174683e777fd1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143752"
---
# <a name="trusted-facade-service"></a>Güvenilir Görünüm Hizmeti
Bu senaryo örneği, Windows Communication Foundation (WCF) güvenlik altyapısını kullanarak arayanın kimlik bilgilerinin bir hizmetten diğerine nasıl aklanacağını gösterir.  
  
 Bir hizmet tarafından sağlanan işlevselliği bir cephe hizmeti kullanarak ortak ağa ifa etmek için yaygın bir tasarım desenidir. Cephe hizmeti genellikle çevre ağında (DMZ, askerden arındırılmış bölge ve ekranlı alt ağ olarak da bilinir) bulunur ve iş mantığını uygulayan ve dahili verilere erişimi olan bir arka uç hizmetiyle iletişim kurar. Cephe hizmeti ile arka uç hizmeti arasındaki iletişim kanalı bir güvenlik duvarından geçer ve genellikle yalnızca tek bir amaç için sınırlıdır.  
  
 Bu örnek aşağıdaki bileşenlerden oluşur:  
  
- Hesap makinesi istemcisi  
  
- Hesap makinesi cephe hizmeti  
  
- Hesap makinesi arka uç hizmeti  
  
 Cephe hizmeti, isteği doğrulamaktan ve arayan kişinin kimliğini doğrulamaktan sorumludur. Başarılı kimlik doğrulama ve doğrulamadan sonra, çevre ağından dahili ağa kontrollü iletişim kanalını kullanarak isteği arka uç hizmetine iletir. İlerleyen isteğin bir parçası olarak, ön cephe hizmeti, arka uç hizmetinin bu bilgileri işlenmesinde kullanabilmesi için arayanın kimliği yle ilgili bilgileri içerir. Arayanın kimliği ileti `Username` `Security` üstbilgisinin içindeki güvenlik belirteci kullanılarak iletilir. Örnek, bu bilgileri üstbilgiden iletmek ve ayıklamak için WCF güvenlik altyapısını `Security` kullanır.  
  
> [!IMPORTANT]
> Arka uç hizmeti, arayanın kimliğini doğrulamak için ön cephe hizmetine güvenir. Bu nedenle, arka uç hizmeti arayana yeniden doğrulamıyor; iletme talebinde cephe hizmeti tarafından sağlanan kimlik bilgilerini kullanır. Bu güven ilişkisi nedeniyle, iletilen iletinin güvenilir bir kaynaktan geldiğinden emin olmak için arka uç hizmetinin cephe hizmetini doğrulaması gerekir - bu durumda, cephe hizmeti.  
  
## <a name="implementation"></a>Uygulama  
 Bu örnekte iki iletişim yolu vardır. Birincisi müşteri ile cephe hizmeti arasında, ikincisi cephe hizmeti ile arka uç servisi arasındadır.  
  
### <a name="communication-path-between-client-and-faade-service"></a>Müşteri ve Cephe Hizmeti Arasındaki İletişim Yolu  
 Cephe hizmet iletişim yoluna istemci `wsHttpBinding` `UserName` bir istemci kimlik tipi ile kullanır. Bu, istemcinin cephe hizmetine kimlik doğrulamak için kullanıcı adı ve parola kullandığı ve cephe hizmetinin istemciye kimlik doğrulamak için X.509 sertifikası kullandığı anlamına gelir. Bağlama yapılandırması aşağıdaki örnek gibi görünür.  
  
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
  
 Cephe hizmeti, özel `UserNamePasswordValidator` uygulama kullanarak arayanın kimliğini doğrular. Tanıtım amacıyla, kimlik doğrulaması yalnızca arayanın kullanıcı adının sunulan parolayla eşleşmesini sağlar. Gerçek dünyada, kullanıcı büyük olasılıkla Active Directory veya özel ASP.NET Üyelik sağlayıcısı kullanılarak doğrulanır. Doğrulayıcı uygulaması dosyada `FacadeService.cs` bulunur.  
  
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
  
 Özel doğrulayıcı, cephe hizmeti yapılandırma dosyasındaki `serviceCredentials` davranış içinde kullanılacak şekilde yapılandırılır. Bu davranış, hizmetin X.509 sertifikasını yapılandırmak için de kullanılır.  
  
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
  
### <a name="communication-path-between-faade-service-and-backend-service"></a>Cephe Hizmeti ile Arka Uç Servisi Arasındaki İletişim Yolu  
 Arka uç hizmet iletişim yoluna cephe `customBinding` hizmeti birkaç bağlama öğeleri oluşan bir kullanır. Bu bağlama iki şeyi başarır. İletişimin güvenli olduğundan ve güvenilir bir kaynaktan geldiğinden emin olmak için cephe hizmetini ve arka uç hizmetini doğrular. Ayrıca, güvenlik belirteci içinde `Username` ilk arayanın kimliğini de iletir. Bu durumda, yalnızca ilk arayanın kullanıcı adı arka uç hizmetine aktarılır, parola iletiye dahil edilmez. Bunun nedeni, arka uç hizmetinin isteği ona iletmeden önce arayanın kimliğini doğrulamak için ön cephe hizmetine güvenmiş olmasıdır. Cephe hizmeti kendisini arka uç hizmetine doğruladığı için, arka uç hizmeti iletilen istekte yer alan bilgilere güvenebilir.  
  
 Aşağıda, bu iletişim yolu için bağlayıcı yapılandırma ve  
  
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
  
 [ \<Güvenlik>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) bağlama öğesi, ilk arayanın kullanıcı adı iletimi ve ayıklama ilgilenir. WindowsStreamSecurity>ve [ \<tcpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) cephe ve arka uç hizmetlerini ve ileti korumasını doğrulayan bir şekilde ilgilenir. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/windowsstreamsecurity.md)  
  
 İsteğin iletilmesi için, ön cephe hizmeti uygulamasının wcf güvenlik altyapısının bunu iletilen iletiye yerleştirebilmesi için ilk arayanın kullanıcı adını sağlaması gerekir. İlk arayanın kullanıcı adı, cephe hizmetinin arka uç `ClientCredentials` hizmetiyle iletişim kurmak için kullandığı istemci proxy örneğinde özellik te buna ayarlayarak cephe hizmeti uygulamasında sağlanır.  
  
 Aşağıdaki kod, `GetCallerIdentity` yöntemin cephe hizmetinde nasıl uygulandığını gösterir. Diğer yöntemler aynı deseni kullanır.  
  
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
  
 Önceki kodda gösterildiği gibi, parola `ClientCredentials` özellik üzerinde ayarlanmaz, yalnızca kullanıcı adı ayarlanır. WCF güvenlik altyapısı, bu durumda parolası olmayan bir kullanıcı adı güvenlik belirteci oluşturur ve bu senaryoda tam olarak gereken budur.  
  
 Arka uç hizmetinde, kullanıcı adı güvenlik belirtecinde bulunan bilgilerin kimlik doğrulaması yapılmalıdır. Varsayılan olarak, WCF güvenlik sağlanan parolayı kullanarak kullanıcıyı bir Windows hesabıyla eşlemeye çalışır. Bu durumda, sağlanan bir parola yoktur ve kimlik doğrulama zaten cephe hizmeti tarafından gerçekleştirilmişolduğundan kullanıcı adının kimlik doğrulaması için arka uç hizmeti gerekli değildir. WCF'de bu işlevselliği `UserNamePasswordValidator` uygulamak için, yalnızca belirteçte bir kullanıcı adının belirtildiğini ve ek kimlik doğrulaması gerçekleştirmediğini belirten bir özel sağlanır.  
  
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
  
 Özel doğrulayıcı, cephe hizmeti yapılandırma dosyasındaki `serviceCredentials` davranış içinde kullanılacak şekilde yapılandırılır.  
  
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
  
 Kullanıcı adı bilgi ve güvenilir cephe hizmet hesabı hakkında bilgi ayıklamak `ServiceSecurityContext` için, arka uç hizmeti uygulaması sınıfı kullanır. Aşağıdaki kod yöntemin `GetCallerIdentity` nasıl uygulandığını gösterir.  
  
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
  
 Cephe hizmeti hesap bilgileri `ServiceSecurityContext.Current.WindowsIdentity` özellik kullanılarak ayıklanır. İlk arayan hakkındaki bilgilere erişmek için arka `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` uç hizmeti özelliği kullanır. Bu tür `Name` `Identity` bir iddia arar. Bu talep, wcf güvenlik altyapısı tarafından güvenlik belirtecinde `Username` bulunan bilgilerden otomatik olarak oluşturulur.  
  
## <a name="running-the-sample"></a>Örneği çalıştırma  
 Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir. İstemciyi kapatmak için istemci penceresinde ENTER tuşuna basın. Hizmetleri kapatmak için ön cephe ve arka uç servis konsolu pencerelerinde ENTER tuşuna basabilirsiniz.  
  
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
  
 Güvenilir Facade senaryo örneğinde yer alan Setup.bat toplu iş dosyası, istemciye kendini doğrulamak için sertifika tabanlı güvenlik gerektiren ön cephe hizmetini çalıştırmak için sunucuyu ilgili bir sertifikayla yapılandırmanızı sağlar. Ayrıntılar için bu konunun sonundaki kurulum yordamına bakın.  
  
 Aşağıda, toplu iş dosyalarının farklı bölümlerine kısa bir genel bakış sağlar.  
  
- Sunucu sertifikası oluşturma.  
  
     Setup.bat toplu dosyasından aşağıdaki satırlar kullanılacak sunucu sertifikasını oluşturur.  
  
    ```console  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     Değişken `%SERVER_NAME%` sunucu adını belirtir - varsayılan değer localhost'dur. Sertifika LocalMachine mağazasında depolanır.  
  
- Cephe hizmetinin sertifikasını müşterinin güvenilir sertifika deposuna yüklemek.  
  
     Aşağıdaki satır, cephe hizmetinin sertifikasını istemci güvenilir kişiler deposuna kopyalar. Makecert.exe tarafından oluşturulan sertifikalar istemci sistemi tarafından dolaylı olarak güvenilen olmadığından bu adım gereklidir. İstemci tarafından güvenilen kök sertifikasına dayanan bir sertifikanız varsa (örneğin, Microsoft tarafından verilmiş bir sertifika- istemci sertifika deposunu sunucu sertifikasıyla doldurma adımı gerekli değildir.  
  
    ```console  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a>Numuneyi aynı makinede çalıştırmak için  
  
1. Yolun Makecert.exe'nin bulunduğu klasörü içerdiğinden emin olun.  
  
2. Setup.bat'ı örnek yükleme klasöründen çalıştırın. Bu, örneği çalıştırmak için gereken tüm sertifikaları yükler.  
  
3. Ayrı bir konsol penceresinde \BackendService\bin dizininden BackendService.exe başlatın  
  
4. \FacadeService\bin dizininden FacadeService.exe'yi ayrı bir konsol penceresinde başlatın  
  
5. Client.exe'yi \client\bin'den başlatın. İstemci etkinliği istemci konsoluygulamasında görüntülenir.  
  
6. İstemci ve hizmet iletişim kuramazsa, [WCF Örnekleri için Sorun Giderme İpuçları'na](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))bakın.  
  
#### <a name="to-clean-up-after-the-sample"></a>Örnekten sonra temizlemek için  
  
1. Örneği çalıştırmayı bitirdikten sonra örnekler klasöründe Cleanup.bat çalıştırın.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\TrustedFacade`  
