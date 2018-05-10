---
title: Destek Belirteçleri
ms.date: 03/30/2017
ms.assetid: 65a8905d-92cc-4ab0-b6ed-1f710e40784e
ms.openlocfilehash: 8d8ff3cf4d5a060d135cbcf40c043681ce72b6e0
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
---
# <a name="supporting-tokens"></a>Destek Belirteçleri
Destek belirteçleri örnek WS güvenliği kullanan bir ileti için ek belirteçler ekleneceği gösterilmektedir. Örnek, bir kullanıcı adı güvenlik belirteci yanı sıra bir X.509 ikili güvenlik belirteci ekler. Belirtecin bir WS-güvenlik ileti üstbilgisinde istemciden hizmete geçirilir ve iletisinin bir parçası alıcısı X.509 sertifikası elinde kanıtlamak için X.509 güvenlik belirteci ile ilişkili özel anahtara sahip imzalanır. Kimlik doğrulaması veya gönderen yetkilendirmek için bir ileti ile ilişkili birden fazla talep olan bir gereksinimi olduğunda bu durumda yararlıdır. Hizmet bir istek-yanıt iletişim deseni tanımlayan bir sözleşme uygular.  
  
## <a name="demonstrates"></a>Gösteriler  
 Örnek gösterilmektedir:  
  
-   Nasıl bir istemci bir hizmete ek güvenlik belirteçleri geçirebilirsiniz.  
  
-   Nasıl sunucu ek güvenlik belirteçleri ile ilişkili talep erişebilir.  
  
-   Nasıl sunucu X.509 sertifikasının ileti şifreleme ve imza için kullanılan simetrik anahtarı korumak için kullanılır.  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
## <a name="client-authenticates-with-username-token-and-supporting-x509-security-token"></a>Kullanıcı adı belirteci ve X.509 güvenlik belirteci destekleyen istemci kimliğini doğrular  
 Hizmet program aracılığıyla kullanarak oluşturduğunuz iletişim için bir tek uç noktasını kullanıma sunar `BindingHelper` ve `EchoServiceHost` sınıfları. Uç nokta bir adresi, bağlama ve bir sözleşme oluşur. Özel bağlama kullanma bağlama yapılandırılmış `SymmetricSecurityBindingElement` ve `HttpTransportBindingElement`. Bu örnek ayarlar `SymmetricSecurityBindingElement` iletim sırasında simetrik anahtar korumak ve geçirmek için bir hizmet X.509 sertifikası kullanmak üzere bir `UserNameToken` destekleyici birlikte `X509SecurityToken` WS-güvenlik ileti üstbilgisinde. Simetrik anahtar, ileti gövdesinin ve kullanıcı adı güvenlik belirteci şifrelemek için kullanılır. WS güvenliği ileti üstbilgisinde bir ek ikili güvenlik belirteci olarak destekleme belirteci geçirildi. Destekleme belirteci özgünlüğünü destekleyen X.509 güvenlikle ilişkili özel anahtara sahip ileti parçası imzalayarak belirteci sağlanır.  
  
```  
public static Binding CreateMultiFactorAuthenticationBinding()  
{  
    HttpTransportBindingElement httpTransport = new HttpTransportBindingElement();  
  
    // the message security binding element will be configured to require 2 tokens:  
    // 1) A username-password encrypted with the service token  
    // 2) A client certificate used to sign the message  
  
    // Instantiate a binding element that will require the username/password token in the message (encrypted with the server cert)  
    SymmetricSecurityBindingElement messageSecurity = SecurityBindingElement.CreateUserNameForCertificateBindingElement();  
  
    // Create supporting token parameters for the client X509 certificate.  
    X509SecurityTokenParameters clientX509SupportingTokenParameters = new X509SecurityTokenParameters();  
    // Specify that the supporting token is passed in message send by the client to the service  
    clientX509SupportingTokenParameters.InclusionMode = SecurityTokenInclusionMode.AlwaysToRecipient;  
    // Turn off derived keys  
    clientX509SupportingTokenParameters.RequireDerivedKeys = false;  
    // Augment the binding element to require the client's X509 certificate as an endorsing token in the message  
    messageSecurity.EndpointSupportingTokenParameters.Endorsing.Add(clientX509SupportingTokenParameters);  
  
    // Create a CustomBinding based on the constructed security binding element.  
    return new CustomBinding(messageSecurity, httpTransport);  
}  
```  
  
 Davranış istemci kimlik doğrulaması ve ayrıca hizmet X.509 sertifikası hakkında bilgi için kullanılacak olan hizmet kimlik bilgilerini belirtir. Örnek kullanır `CN=localhost` hizmet X.509 sertifikası bir konu adı olarak.  
  
```  
override protected void InitializeRuntime()  
{  
    // Extract the ServiceCredentials behavior or create one.  
    ServiceCredentials serviceCredentials =   
        this.Description.Behaviors.Find<ServiceCredentials>();  
    if (serviceCredentials == null)  
    {  
        serviceCredentials = new ServiceCredentials();  
        this.Description.Behaviors.Add(serviceCredentials);  
    }  
  
    // Set the service certificate  
    serviceCredentials.ServiceCertificate.SetCertificate(  
                                       "CN=localhost");  
  
/*  
Setting the CertificateValidationMode to PeerOrChainTrust means that if the certificate is in the Trusted People store, then it will be trusted without performing a validation of the certificate's issuer chain. This setting is used here for convenience so that the sample can be run without having to have certificates issued by a certification authority (CA).  
This setting is less secure than the default, ChainTrust. The security implications of this setting should be carefully considered before using PeerOrChainTrust in production code.  
*/  
    serviceCredentials.ClientCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.PeerOrChainTrust;  
  
    // Create the custom binding and add an endpoint to the service.  
    Binding multipleTokensBinding =  
         BindingHelper.CreateMultiFactorAuthenticationBinding();  
    this.AddServiceEndpoint(typeof(IEchoService),   
                          multipleTokensBinding, string.Empty);  
    base.InitializeRuntime();  
}  
```  
  
 Hizmet kodu:  
  
```  
[ServiceBehavior(IncludeExceptionDetailInFaults = true)]  
public class EchoService : IEchoService  
{  
    public string Echo()  
    {  
        string userName;  
        string certificateSubjectName;  
        GetCallerIdentities(  
            OperationContext.Current.ServiceSecurityContext,   
            out userName,   
            out certificateSubjectName);  
            return String.Format("Hello {0}, {1}",   
                    userName, certificateSubjectName);  
    }  
  
    public void Dispose()  
    {  
    }  
  
    bool TryGetClaimValue<TClaimResource>(ClaimSet claimSet,   
            string claimType, out TClaimResource resourceValue)  
            where TClaimResource : class  
    {  
        resourceValue = default(TClaimResource);  
        IEnumerable<Claim> matchingClaims =   
            claimSet.FindClaims(claimType, Rights.PossessProperty);  
        if(matchingClaims == null)  
            return false;  
        IEnumerator<Claim> enumerator = matchingClaims.GetEnumerator();  
        if (enumerator.MoveNext())  
        {  
            resourceValue =   
              (enumerator.Current.Resource == null) ? null :   
              (enumerator.Current.Resource as TClaimResource);  
            return true;  
        }  
        else  
        {  
            return false;  
        }  
    }  
  
    // Returns the username and certificate subject name provided by   
    //the client  
    void GetCallerIdentities(ServiceSecurityContext   
        callerSecurityContext,   
        out string userName, out string certificateSubjectName)  
    {  
        userName = null;  
        certificateSubjectName = null;  
  
       // Look in all the claimsets in the authorization context  
       foreach (ClaimSet claimSet in   
               callerSecurityContext.AuthorizationContext.ClaimSets)  
       {  
            if (claimSet is WindowsClaimSet)  
            {  
                // Try to find a Name claim. This will have been   
                // generated from the windows username.  
                string tmpName;  
                if (TryGetClaimValue<string>(claimSet, ClaimTypes.Name,   
                                                      out tmpName))  
                {  
                    userName = tmpName;  
                }  
            }  
            else if (claimSet is X509CertificateClaimSet)  
            {  
                // Try to find an X500DisinguishedName claim. This will   
                // have been generated from the client certificate.  
                X500DistinguishedName tmpDistinguishedName;  
                if (TryGetClaimValue<X500DistinguishedName>(claimSet,   
                               ClaimTypes.X500DistinguishedName,   
                               out tmpDistinguishedName))  
                {  
                    certificateSubjectName = tmpDistinguishedName.Name;  
                }  
            }  
        }  
    }  
}   
```  
  
 İstemci uç noktası, hizmet uç noktası benzer şekilde yapılandırılır. İstemci aynı kullanır `BindingHelper` sınıfı bir bağlama oluşturun. Kurulumu geri kalanı bulunan `Client` sınıfı. İstemci, istemci uç nokta davranışları koleksiyonuna Kurulum kodu kullanıcı adı güvenlik belirteci, destekleme X.509 güvenlik belirteci ve hizmet X.509 sertifikası hakkında bilgi hakkında bilgi ayarlar.  
  
```  
 static void Main()  
 {  
     // Create the custom binding and an endpoint address for   
     // the service.  
     Binding multipleTokensBinding =   
         BindingHelper.CreateMultiFactorAuthenticationBinding();  
         EndpointAddress serviceAddress = new EndpointAddress(  
         "http://localhost/servicemodelsamples/service.svc");  
       ChannelFactory<IEchoService> channelFactory = null;  
       IEchoService client = null;  
  
       Console.WriteLine("Username authentication required.");  
       Console.WriteLine(  
         "Provide a valid machine or domain account. [domain\\user]");  
       Console.WriteLine("   Enter username:");  
       string username = Console.ReadLine();  
       Console.WriteLine("   Enter password:");  
       string password = "";  
       ConsoleKeyInfo info = Console.ReadKey(true);  
       while (info.Key != ConsoleKey.Enter)  
       {  
           if (info.Key != ConsoleKey.Backspace)  
           {  
               if (info.KeyChar != '\0')  
               {  
                   password += info.KeyChar;  
                }  
                info = Console.ReadKey(true);  
            }  
            else if (info.Key == ConsoleKey.Backspace)  
            {  
                if (password != "")  
                {  
                    password =   
                       password.Substring(0, password.Length - 1);  
                }  
                info = Console.ReadKey(true);  
            }  
         }  
         for (int i = 0; i < password.Length; i++)  
            Console.Write("*");  
         Console.WriteLine();  
         try  
         {  
           // Create a proxy with the previously create binding and   
           // endpoint address  
              channelFactory =   
                 new ChannelFactory<IEchoService>(  
                     multipleTokensBinding, serviceAddress);  
           // configure the username credentials, the client   
           // certificate and the server certificate on the channel   
           // factory   
           channelFactory.Credentials.UserName.UserName = username;  
           channelFactory.Credentials.UserName.Password = password;  
           channelFactory.Credentials.ClientCertificate.SetCertificate(  
           "CN=client.com", StoreLocation.CurrentUser, StoreName.My);  
              channelFactory.Credentials.ServiceCertificate.SetDefaultCertificate(  
           "CN=localhost", StoreLocation.LocalMachine, StoreName.My);  
           client = channelFactory.CreateChannel();  
           Console.WriteLine("Echo service returned: {0}",   
                                           client.Echo());  
  
           ((IChannel)client).Close();  
           channelFactory.Close();  
        }  
        catch (CommunicationException e)  
        {  
         Abort((IChannel)client, channelFactory);  
         // if there is a fault then print it out  
         FaultException fe = null;  
         Exception tmp = e;  
         while (tmp != null)  
         {  
            fe = tmp as FaultException;  
            if (fe != null)  
            {  
                break;  
            }  
            tmp = tmp.InnerException;  
        }  
        if (fe != null)  
        {  
           Console.WriteLine("The server sent back a fault: {0}",   
         fe.CreateMessageFault().Reason.GetMatchingTranslation().Text);  
        }  
        else  
        {  
         Console.WriteLine("The request failed with exception: {0}",e);  
        }  
    }  
    catch (TimeoutException)  
    {  
        Abort((IChannel)client, channelFactory);  
        Console.WriteLine("The request timed out");  
    }  
    catch (Exception e)  
    {  
         Abort((IChannel)client, channelFactory);  
          Console.WriteLine(  
          "The request failed with unexpected exception: {0}", e);  
    }  
    Console.WriteLine();  
    Console.WriteLine("Press <ENTER> to terminate client.");  
    Console.ReadLine();  
}  
```  
  
## <a name="displaying-callers-information"></a>Arayanlar bilgileri görüntüleme  
 Arayanın bilgileri görüntülemek için kullanabileceğiniz `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` aşağıdaki kodda gösterildiği gibi. `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` Geçerli arayanla ilişkili yetkilendirme talepleri içerir. Bu talep iletide alınan her belirteci için Windows Communication Foundation (WCF) tarafından otomatik olarak sağlanır.  
  
```  
bool TryGetClaimValue<TClaimResource>(ClaimSet claimSet, string   
                         claimType, out TClaimResource resourceValue)  
    where TClaimResource : class  
{  
    resourceValue = default(TClaimResource);  
    IEnumerable<Claim> matchingClaims =   
    claimSet.FindClaims(claimType, Rights.PossessProperty);  
    if (matchingClaims == null)  
          return false;  
    IEnumerator<Claim> enumerator = matchingClaims.GetEnumerator();  
    if (enumerator.MoveNext())  
    {  
        resourceValue = (enumerator.Current.Resource == null) ? null : (enumerator.Current.Resource as TClaimResource);  
        return true;  
    }  
    else  
    {  
         return false;  
    }  
}  
  
// Returns the username and certificate subject name provided by the client  
void GetCallerIdentities(ServiceSecurityContext callerSecurityContext, out string userName, out string certificateSubjectName)  
{  
    userName = null;  
    certificateSubjectName = null;  
  
    // Look in all the claimsets in the authorization context  
    foreach (ClaimSet claimSet in   
      callerSecurityContext.AuthorizationContext.ClaimSets)  
    {  
        if (claimSet is WindowsClaimSet)  
        {  
            // Try to find a Name claim. This will have been generated   
            //from the windows username.  
            string tmpName;  
            if (TryGetClaimValue<string>(claimSet, ClaimTypes.Name,   
                                                     out tmpName))  
            {  
                userName = tmpName;  
            }  
        }  
        else if (claimSet is X509CertificateClaimSet)  
         {  
            //Try to find an X500DisinguishedName claim.   
            //This will have been generated from the client   
            //certificate.  
            X500DistinguishedName tmpDistinguishedName;  
            if (TryGetClaimValue<X500DistinguishedName>(claimSet,   
               ClaimTypes.X500DistinguishedName,   
               out tmpDistinguishedName))  
            {  
                    certificateSubjectName = tmpDistinguishedName.Name;  
            }  
        }  
    }  
}  
```  
  
## <a name="running-the-sample"></a>Örnek çalışıyor  
 Örneği çalıştırdığınızda, istemci önce kullanıcı adı ve parola için kullanıcı adı belirteci girmenizi ister. WCF hizmetine sistem tarafından sağlanan kimlik içine kullanıcı adı belirteç sağlanan değerler eşlendiğinden, sistem hesabı için doğru değerleri sağladığınızdan emin olun. Bundan sonra istemci hizmetinden gelen yanıt görüntüler. İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.  
  
## <a name="setup-batch-file"></a>Toplu iş dosyası Kurulumu  
 Bu örnekle dahil Setup.bat toplu iş dosyası, sunucu sertifika tabanlı güvenlik gerektiren Internet Information Services (IIS) barındırılan uygulamayı çalıştırmayı ilgili sertifikalarla sunucu yapılandırmanıza olanak sağlar. Bu toplu iş dosyası makinelerde çalışması için ya da barındırılan olmayan bir durumda çalışması için değiştirilmesi gerekir.  
  
 Aşağıdakiler, böylece uygun yapılandırmada çalışacak biçimde değiştirilebilir toplu iş dosyaları farklı bölümlerini kısa bir genel bakış sağlar.  
  
### <a name="creating-the-client-certificate"></a>İstemci sertifikası oluşturma  
 Aşağıdaki satırları Setup.bat toplu iş dosyasından kullanılacak istemci sertifikası oluşturun. `%CLIENT_NAME%` Değişkeni, istemci sertifikası konu belirtir. Bu örnek konu adı olarak "client.com" kullanır.  
  
 Sertifika altında (Kişisel) My deposunda saklanır `CurrentUser` depolama konumu.  
  
```  
echo ************  
echo making client cert  
echo ************  
makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe  
```  
  
### <a name="installing-the-client-certificate-into-the-servers-trusted-store"></a>Sunucu güvenilen deposuna istemci sertifikası yükleme  
 Setup.bat toplu iş dosyasında aşağıdaki satırı istemci sertifikasını sunucusunun güvenilir Kişiler deposuna kopyalar. MakeCert.exe tarafından oluşturulan sertifikaları örtük olarak sunucunun sistemi tarafından güvenilir değil çünkü bu adım gereklidir. Bir istemci güvenilen kök sertifikasını kökü belirtilmiş bir sertifikanız zaten varsa — örneğin, bir Microsoft verilen sertifika — sunucu sertifikasına sahip istemci sertifika deposunun doldurulması, bu adım gerekli değildir.  
  
```  
echo ************  
echo copying client cert to server's CurrentUserstore  
echo ************  
certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople  
```  
  
### <a name="creating-the-server-certificate"></a>Sunucu sertifikası oluşturma  
 Aşağıdaki satırları Setup.bat toplu iş dosyasından kullanılacak sunucu sertifikası oluşturun. `%SERVER_NAME%` Değişkeni, sunucu adını belirtir. Kendi sunucu adını belirtmek için bu değişkeni değiştirin. Bu toplu iş dosyasındaki localhost varsayılandır.  
  
 Sertifika, LocalMachine depolama konumu altında (Kişisel) My deposunda saklanır. Sertifika saklanır IIS tarafından barındırılan hizmetler için LocalMachine deposundaki. Kendini barındıran hizmetler için LocalMachine dize Currentuser'a ile değiştirerek Currentuser'a depolama konumu sunucu sertifikasının depolamak için toplu iş dosyasını değiştirmeniz gerekir.  
  
```  
echo ************  
echo Server cert setup starting  
echo %SERVER_NAME%  
echo ************  
echo making server cert  
echo ************  
makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
```  
  
### <a name="installing-server-certificate-into-clients-trusted-certificate-store"></a>İstemcinin güvenilen sertifika deposuna sunucu sertifikası yükleme  
 İstemci güvenilir kişiler içine Setup.bat toplu dosya kopyalama sunucu sertifikasının aşağıdaki satırları depolar. MakeCert.exe tarafından oluşturulan sertifikaları örtük olarak istemci sistemi tarafından güvenilir değil çünkü bu adım gereklidir. Bir istemci güvenilen kök sertifikasını kökü belirtilmiş bir sertifikanız zaten varsa — örneğin, bir Microsoft verilen sertifika — sunucu sertifikasına sahip istemci sertifika deposunun doldurulması, bu adım gerekli değildir.  
  
```  
echo ************  
echo copying server cert to client's TrustedPeople store  
echo ************certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
```  
  
### <a name="enabling-access-to-the-certificates-private-key"></a>Sertifikanın özel anahtar erişimi etkinleştirme  
 IIS barındırılan hizmeti sertifika özel anahtarına erişimi etkinleştirmek için IIS tarafından barındırılan işlemin altında çalıştığı hesabın özel anahtar için uygun izinleri verilmelidir. Bu son adımda Setup.bat komut dosyası tarafından gerçekleştirilir.  
  
```  
echo ************  
echo setting privileges on server certificates  
echo ************  
for /F "delims=" %%i in ('"%ProgramFiles%\ServiceModelSampleTools\FindPrivateKey.exe" My LocalMachine -n CN^=%SERVER_NAME% -a') do set PRIVATE_KEY_FILE=%%i  
set WP_ACCOUNT=NT AUTHORITY\NETWORK SERVICE  
(ver | findstr /C:"5.1") && set WP_ACCOUNT=%COMPUTERNAME%\ASPNET  
echo Y|cacls.exe "%PRIVATE_KEY_FILE%" /E /G "%WP_ACCOUNT%":R  
iisreset  
```  
  
##### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirilen mutlaka [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözümü derlemek için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz makine yapılandırmada örneği çalıştırmak için aşağıdaki yönergeleri kullanın.  
  
##### <a name="to-run-the-sample-on-the-same-machine"></a>Aynı makinede örneği çalıştırmak için  
  
1.  İçinde örnek yükleme klasöründen Setup.bat çalıştırmak bir [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemini yönetici ayrıcalıklarıyla çalıştırın. Bu örneği çalıştırmak için gerekli tüm sertifikalar yükler.  
  
    > [!NOTE]
    >  Setup.bat toplu iş dosyası çalıştırılmak üzere tasarlanmış bir [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemi. İçinde PATH ortam değişkeni ayarlamak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemi Setup.bat komut dosyası için gereken yürütülebilir dosyalar içeren dizine işaret eder. Örnekle bittiğinde Cleanup.bat çalıştırarak sertifikaları kaldırdığınızdan emin olun. Diğer güvenlik örnekleri aynı sertifikaları kullanır.  
  
2.  Client.exe \client\bin başlatın. İstemci etkinliği istemci konsol uygulaması görüntülenir.  
  
3.  İstemci ve hizmet iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
##### <a name="to-run-the-sample-across-machines"></a>Makine genelinde örneği çalıştırmak için  
  
1.  Bir dizin hizmeti makinede oluşturun. Internet Information Services (IIS) yönetim aracını kullanarak bu dizin için servicemodelsamples adlı bir sanal uygulama oluşturun.  
  
2.  Hizmet program dosyalarını \inetpub\wwwroot\servicemodelsamples hizmeti makinede sanal dizine kopyalayın. \Bin alt dizinindeki dosyaları kopyalayın emin olun. Ayrıca hizmet makineye Setup.bat, Cleanup.bat ve ImportClientCert.bat dosyalarını kopyalayın.  
  
3.  İstemci ikili dosyalarının için istemci makinede bir dizin oluşturun.  
  
4.  İstemci makinesinde istemci dizinine istemci program dosyaları kopyalayın. Ayrıca istemciye Setup.bat, Cleanup.bat ve ImportServiceCert.bat dosyalarını kopyalayın.  
  
5.  Sunucu üzerinde çalışan `setup.bat service` yönetici ayrıcalıklarına sahip bir Visual Studio Komut İstemi'nde açılır. Çalışan `setup.bat` ile `service` bağımsız değişkeni makinenin tam etki alanı adı ile bir hizmet sertifikası oluşturur ve hizmet sertifikası Service.cer adlı bir dosyaya aktarır.  
  
6.  Web.config dosyasını yeni sertifika yansıtacak şekilde düzenleyin (içinde `findValue` özniteliğini [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) makinenin tam etki alanı adı ile aynı olduğu.  
  
7.  Service.cer dosya hizmeti dizininden istemci makinesinde istemci dizinine kopyalayın.  
  
8.  İstemci üzerinde çalışan `setup.bat client` yönetici ayrıcalıklarına sahip bir Visual Studio Komut İstemi'nde açılır. Çalışan `setup.bat` ile `client` bağımsız değişkeni client.com adlı bir istemci sertifikası oluşturur ve istemci sertifikasını Client.cer adlı bir dosyaya aktarır.  
  
9. İstemci makinesinde Client.exe.config dosyasında yeni adresi hizmetinizin eşleştirmek için uç nokta adresi değerini değiştirin. Sunucunun tam etki alanı adı ile localhost değiştirerek bunu.  
  
10. Client.cer dosyasını istemci dizininden sunucusunda hizmet dizinine kopyalayın.  
  
11. İstemcide ImportServiceCert.bat çalıştırın. Bu hizmet sertifikası Service.cer dosyadan Currentuser'a - TrustedPeople deposunu alır.  
  
12. ImportClientCert.bat, çalıştıran sunucuda, bu istemci sertifikasını Client.cer dosyadan LocalMachine - TrustedPeople deposunu alır.  
  
13. İstemci makinesinde, bir komut istemi penceresinden Client.exe başlatın. İstemci ve hizmet iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
##### <a name="to-clean-up-after-the-sample"></a>Örnek sonra temizlemek için  
  
-   Örnek çalıştıran tamamladıktan sonra Cleanup.bat samples klasöründen çalıştırın.  
  
> [!NOTE]
>  Bu komut dosyası, bu örnek makine genelinde çalıştırırken bir istemcide hizmet sertifikaları kaldırmaz. Makine genelinde sertifikaları kullanan WCF örnekleri çalıştırırsanız, Currentuser'a - TrustedPeople deposu yüklü hizmet sertifikalarını temizlemek emin olun. Bunu yapmak için aşağıdaki komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
## <a name="see-also"></a>Ayrıca Bkz.
