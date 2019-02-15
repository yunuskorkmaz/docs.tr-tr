---
title: Destek Belirteçleri
ms.date: 03/30/2017
ms.assetid: 65a8905d-92cc-4ab0-b6ed-1f710e40784e
ms.openlocfilehash: 899c6ecabafb1bd0487b989c6da8963dd07945cf
ms.sourcegitcommit: bef803e2025642df39f2f1e046767d89031e0304
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56304160"
---
# <a name="supporting-tokens"></a>Destek Belirteçleri
WS-güvenlik kullanan bir iletiye ek belirteçler ekleme belirteçleri destekleyen örnek gösterir. Örneğin, bir kullanıcı adı güvenlik belirteci yanı sıra bir X.509 ikili güvenlik belirteci ekler. Belirteci bir WS-güvenlik uyarısı istemciden hizmete geçirilir ve iletisinin parçası X.509 sertifikası elinde alıcısına kanıtlamak için X.509 güvenlik belirteciyle ilişkili özel anahtarla imzalanır. Birden fazla talep kimlik doğrulaması veya yetkilendirme gönderen bir ileti ile ilişkili olan bir gereksinimi olduğunda bu durumda kullanışlıdır. Hizmet istek-yanıt iletişim deseni tanımlayan bir sözleşme uygular.

## <a name="demonstrates"></a>Gösteriler
 Bir örnek göstermektedir:

-   Nasıl bir istemci bir hizmete ek güvenlik belirteçleri geçirebilirsiniz.

-   Sunucu, ek güvenlik belirteçleri ile ilişkili talep nasıl erişebilir.

-   Sunucu X.509 sertifikasının nasıl ileti şifreleme ve imza için kullanılan simetrik anahtarı korumak için kullanılır.

> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.

## <a name="client-authenticates-with-username-token-and-supporting-x509-security-token"></a>Kullanıcı adı belirteci ve X.509 güvenlik belirteci destekleyen istemci kimlik doğrulaması
 Program aracılığıyla kullanarak oluşturduğunuz iletişim kurmak için tek bir uç nokta hizmetini sunar `BindingHelper` ve `EchoServiceHost` sınıfları. Uç nokta, adres, bağlama ve bir sözleşme oluşur. Özel bağlama kullanma yapılandırılmış bağlama `SymmetricSecurityBindingElement` ve `HttpTransportBindingElement`. Bu örnek ayarlar `SymmetricSecurityBindingElement` simetrik anahtar aktarım sırasında korumak ve geçirilecek hizmet X.509 sertifikası kullanmak için bir `UserNameToken` destekleyici birlikte `X509SecurityToken` WS-güvenlik ileti üstbilgisinde. Simetrik anahtar, ileti gövdesi ve kullanıcı adı güvenlik belirteci şifrelemek için kullanılır. Destekleme belirteci, WS-güvenlik ileti üstbilgisinde bir ek ikili güvenlik belirteci olarak geçirilir. Destekleyici X.509 güvenlik ile ilişkili özel anahtara sahip ileti parçası açarak destekleme belirteci kimlik doğrulaması belirteci sağlanır.

```csharp
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

 Davranış, istemci kimlik doğrulaması ve ayrıca hizmet X.509 sertifikası hakkında daha fazla bilgi için kullanılacak hizmet kimlik bilgilerini belirtir. Örnek kullanır `CN=localhost` hizmet X.509 sertifikasındaki konu adı.

```csharp
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

```csharp
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
            return $"Hello {userName}, {certificateSubjectName}";
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

 İstemci uç noktası, hizmet uç noktası için benzer bir şekilde yapılandırılır. Aynı istemcinin kullandığı `BindingHelper` bağlama oluşturmak için sınıf. Kurulumu geri kalanını bulunan `Client` sınıfı. İstemci, istemci uç nokta davranışları koleksiyon Kurulum kodu kullanıcı adı güvenlik belirteci, destekleyici X.509 güvenlik belirteci ve hizmet X.509 sertifikası hakkında bilgi hakkında bilgi ayarlar.

```csharp
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

## <a name="displaying-callers-information"></a>Çağıranlar bilgileri görüntüleme
 Arayanın bilgileri görüntülemek için kullanabileceğiniz `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` aşağıdaki kodda gösterildiği gibi. `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` Geçerli arayanla ilişkili yetkilendirme talepleri içerir. Bu talep, otomatik olarak yer alan her bir belirteç için Windows Communication Foundation (WCF) tarafından sağlanır.

```csharp
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

## <a name="running-the-sample"></a>Örneği çalıştırma
 Örneği çalıştırdığınızda, istemci önce kullanıcı adı belirteci kullanıcı adı ve parola girmenizi ister. WCF hizmeti olarak sistem tarafından sağlanan kimlik kullanıcı adı belirteç sağlanan değerler eşlediğinden, sistem hesabı için doğru değerleri sağlayın emin olun. Bundan sonra istemci hizmetinden gelen yanıt görüntüler. İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.

## <a name="setup-batch-file"></a>Kurulum toplu iş dosyası
 Bu örnekle dahil Setup.bat toplu iş dosyası ile ilgili sertifika sunucusu sertifika tabanlı güvenlik gerektiren Internet Information Services (IIS) barındırılan uygulamayı çalıştırmak için sunucu yapılandırmanıza olanak sağlar. Bu toplu iş dosyası makinelerde çalışmaya veya barındırılan olmayan bir durumda çalışması için değiştirilmesi gerekir.

 Aşağıda, böylece uygun yapılandırmasında çalıştırılacak değiştirilebilir toplu iş dosyaları farklı bölümlerini kısa bir genel bakış sağlar.

### <a name="creating-the-client-certificate"></a>İstemci sertifikası oluşturma
 Setup.bat toplu iş dosyasından aşağıdaki satırları kullanılacak istemci sertifikası oluşturun. `%CLIENT_NAME%` Değişkeni, istemci sertifikasındaki konu belirtir. Bu örnekte, konu adı olarak "client.com" kullanır.

 Sertifika altında (Kişisel) My deposunda saklanır `CurrentUser` depolama konumu.

```
echo ************
echo making client cert
echo ************
makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
```

### <a name="installing-the-client-certificate-into-the-servers-trusted-store"></a>Sunucunun güvenilen Store istemci sertifikası yükleme
 Setup.bat toplu iş dosyasında aşağıdaki satırı, istemci sertifikası sunucusunun güvenilir Kişiler deposuna kopyalar. MakeCert.exe tarafından oluşturulan sertifika sunucunun sistem tarafından örtük olarak güvenilmeyen olduğundan bu adım gereklidir. Bir istemci güvenilen kök sertifikayı kök erişim izni verilmiş bir sertifika zaten varsa — örneğin, Microsoft tarafından verilen sertifika — sunucu sertifikasında istemci sertifika deposunun doldurulması, bu adım gerekli değildir.

```
echo ************
echo copying client cert to server's CurrentUserstore
echo ************
certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
```

### <a name="creating-the-server-certificate"></a>Sunucu sertifikası oluşturma
 Setup.bat toplu iş dosyasından aşağıdaki satırları kullanılacak sunucu sertifikası oluşturun. `%SERVER_NAME%` Değişkeni, sunucu adını belirtir. Kendi sunucu adını belirtmek için bu değişkeni değiştirin. Bu toplu iş dosyasında localhost varsayılandır.

 Sertifikayı LocalMachine depolama konumu altında (Kişisel) My deposunda depolanır. Depolanmış bir sertifikayla IIS tarafından barındırılan hizmetleri LocalMachine deposunda. Şirket içinde barındırılan hizmetler için sunucu sertifikası LocalMachine dize CurrentUser ile değiştirerek CurrentUser deposu konumda depolamak için toplu iş dosyasını değiştirmeniz gerekir.

```
echo ************
echo Server cert setup starting
echo %SERVER_NAME%
echo ************
echo making server cert
echo ************
makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
```

### <a name="installing-server-certificate-into-clients-trusted-certificate-store"></a>İstemcinin güvenilen sertifika Store sunucu sertifikası yükleme
 İstemci güvenilir kişiler uygulamasına Setup.bat toplu dosya kopyalama sunucu sertifikasının aşağıdaki satırları depolayın. MakeCert.exe tarafından oluşturulan sertifikaları örtük olarak istemci sistemi tarafından güvenilir değildir çünkü bu adım gereklidir. Bir istemci güvenilen kök sertifikayı kök erişim izni verilmiş bir sertifika zaten varsa — örneğin, Microsoft tarafından verilen sertifika — sunucu sertifikasında istemci sertifika deposunun doldurulması, bu adım gerekli değildir.

```
echo ************
echo copying server cert to client's TrustedPeople store
echo ************certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
```

### <a name="enabling-access-to-the-certificates-private-key"></a>Sertifikanın özel anahtarı erişimini etkinleştirme
 IIS barındırılan hizmeti için sertifika özel anahtar erişimi etkinleştirmek için IIS tarafından barındırılan işlem altında çalıştığı hesabın özel anahtar için uygun izinleri verilmelidir. Bu, son adımda Setup.bat betiği tarafından gerçekleştirilir.

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

##### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma

1.  Gerçekleştirilen mutlaka [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2.  Çözümü derlemek için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).

3.  Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için aşağıdaki yönergeleri kullanın.

##### <a name="to-run-the-sample-on-the-same-machine"></a>Örneği aynı makinede çalıştırmak için

1.  Visual Studio 2012 komut istemini yönetici ayrıcalıklarıyla çalıştırın içinde örnek yükleme klasöründen Setup.bat çalıştırın. Bu örneği çalıştırmak için gerekli olan tüm sertifikaları yükler.

    > [!NOTE]
    >  Setup.bat toplu iş dosyası, bir Visual Studio 2012 komut isteminden çalıştırılması için tasarlanmıştır. PATH ortam değişkenine içinde Visual Studio 2012 komut istemi noktaları Setup.bat betiği tarafından gereken yürütülebilir dosyaları içeren dizine ayarlayın. Sertifikaları örnek ile işiniz bittiğinde Cleanup.bat çalıştırarak kaldırmayı unutmayın. Diğer güvenlik örnekleri aynı sertifikalarını kullanın.  
  
2.  Client.exe \client\bin başlatın. İstemci etkinliği istemci konsol uygulamasında görüntülenir.  
  
3.  İstemci ve hizmet iletişim kurabildiğini bilmiyorsanız bkz [WCF örnekleri için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
##### <a name="to-run-the-sample-across-machines"></a>Makineler arasında örneği çalıştırmak için  
  
1.  Bir dizin hizmeti makinede oluşturun. Internet Information Services (IIS) yönetim aracını kullanarak bu dizin için servicemodelsamples adlı sanal bir uygulama oluşturun.  
  
2.  Hizmet program dosyaları \inetpub\wwwroot\servicemodelsamples hizmeti makinede sanal dizinine kopyalayın. Dosyaları \bin alt dizinde kopyalama emin olun. Ayrıca hizmeti makineye Setup.bat Cleanup.bat ve ImportClientCert.bat dosyaları kopyalayın.  
  
3.  İstemci ikili dosyaları için istemci makinede bir dizin oluşturun.  
  
4.  İstemci makinesinde istemci dizinine istemci program dosyaları kopyalayın. Aynı zamanda istemciye Setup.bat Cleanup.bat ve ImportServiceCert.bat dosyaları kopyalayın.  
  
5.  Sunucu üzerinde çalışan `setup.bat service` Geliştirici komut istemi için Visual Studio yönetici ayrıcalıklarıyla açılmış. Çalışan `setup.bat` ile `service` bağımsız değişkeni makinenin tam etki alanı adı ile bir hizmet sertifikası oluşturur ve hizmet sertifikası Service.cer adlı bir dosyaya dışarı aktarır.  
  
6.  Yeni sertifika adını yansıtacak şekilde Web.config'i düzenlemek (içinde `findValue` özniteliğini [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) makinesinin tam etki alanı adıyla aynı olduğu.  
  
7.  Service.cer dosya hizmeti dizininden istemci makine üzerinde istemci dizinine kopyalayın.  
  
8.  Bir istemcide çalışmasına `setup.bat client` Geliştirici komut istemi için Visual Studio yönetici ayrıcalıklarıyla açılmış. Çalışan `setup.bat` ile `client` bağımsız değişkeni client.com adlı bir istemci sertifikası oluşturur ve istemci sertifikasını Client.cer adlı bir dosyaya dışarı aktarır.  
  
9. İstemci makinesinde Client.exe.config dosyasında hizmetinizin yeni adresiyle eşleşecek şekilde uç nokta adresi değiştirin. Localhost sunucunun tam etki alanı adıyla değiştirerek bunu.  
  
10. Client.cer dosyayı istemci dizin sunucusundaki hizmet dizinine kopyalayın.  
  
11. İstemcide ImportServiceCert.bat çalıştırın. Bu hizmet sertifikası Service.cer dosyasından CurrentUser - TrustedPeople deposuna aktarır.  
  
12. ImportClientCert.bat, çalıştıran sunucuda bu istemci sertifikasını Client.cer dosyasından LocalMachine - TrustedPeople deposu içeri aktarır.  
  
13. İstemci makinesinde bir komut istemi penceresinden Client.exe başlatın. İstemci ve hizmet iletişim kurabildiğini bilmiyorsanız bkz [WCF örnekleri için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
##### <a name="to-clean-up-after-the-sample"></a>Sonra örnek temizlemek için  
  
-   Bu örneği çalıştırmadan tamamladıktan sonra Cleanup.bat samples klasöründe çalıştırın.  
  
> [!NOTE]
>  Bu betik, bu örnek makinelerde çalışan hizmet sertifikaları bir istemci üzerinde kaldırmaz. Makineler arasında sertifikaları kullanan WCF örnekleri çalıştırırsanız, CurrentUser - TrustedPeople deposu yüklü hizmet sertifikalarını Temizle emin olun. Bunu yapmak için aşağıdaki komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.

## <a name="see-also"></a>Ayrıca bkz.
