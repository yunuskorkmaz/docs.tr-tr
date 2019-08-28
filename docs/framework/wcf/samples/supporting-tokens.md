---
title: Destek Belirteçleri
ms.date: 03/30/2017
ms.assetid: 65a8905d-92cc-4ab0-b6ed-1f710e40784e
ms.openlocfilehash: 14cc7bed55d41352acd93d4443b20f8bda966263
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044623"
---
# <a name="supporting-tokens"></a>Destek Belirteçleri
Destekleme belirteçleri örneği, WS-Security kullanan bir iletiye nasıl ek belirteç ekleneceğini gösterir. Örnek, bir Kullanıcı adı güvenlik belirtecinin yanı sıra bir X. 509.440 ikili güvenlik belirteci ekler. Belirteç, istemciden hizmete bir WS-Security ileti üst bilgisine geçirilir ve iletinin bir bölümü x. 509.440 sertifikasının alıcıya sahip olduğunu kanıtlamak için X. 509.440 güvenlik belirteciyle ilişkili özel anahtarla imzalanır. Bu, gönderenin kimliğini doğrulamak veya yetkilendirmek için bir iletiyle ilişkilendirilmiş birden çok talebe sahip olması durumunda yararlıdır. Hizmet, istek-yanıt iletişim modelini tanımlayan bir sözleşme uygular.

## <a name="demonstrates"></a>Gösteriler
 Örnek şunları gösterir:

- Bir istemcinin bir hizmete nasıl ek güvenlik belirteçleri geçirebilirler.

- Sunucunun ek güvenlik belirteçleriyle ilişkili taleplere erişme şekli.

- Sunucu X. 509.440 sertifikası ileti şifreleme ve imza için kullanılan simetrik anahtarı korumak için kullanılır.

> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.

## <a name="client-authenticates-with-username-token-and-supporting-x509-security-token"></a>İstemci Kullanıcı adı belirteciyle kimliğini doğrular ve X. 509.440 güvenlik belirtecini destekler
 Hizmet, `BindingHelper` ve `EchoServiceHost` sınıfları kullanılarak programlı bir şekilde oluşturulan iletişim için tek bir uç nokta sunar. Uç nokta bir adres, bağlama ve bir anlaşmada oluşur. Bağlama, ve `SymmetricSecurityBindingElement` `HttpTransportBindingElement`kullanarak özel bir bağlama ile yapılandırılır. Bu örnek, `SymmetricSecurityBindingElement` iletim sırasında simetrik anahtarı korumak ve bir `UserNameToken` WS-Security ileti üstbilgisinde destekleyici `X509SecurityToken` ile geçiş yapmak için bir Service X. 509.952 sertifikası kullanmak üzere ayarlar. Simetrik anahtar, ileti gövdesini ve Kullanıcı adı güvenlik belirtecini şifrelemek için kullanılır. Destekleme belirteci, WS-Security ileti üstbilgisinde ek bir ikili güvenlik belirteci olarak geçirilir. Destekleyici belirtecin özgünlük belgesi, iletinin bir parçası destekleyici X. 509.440 güvenlik belirteci ile ilişkili özel anahtarla imzalanarak sağlanır.

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

 Davranış, istemci kimlik doğrulaması için kullanılacak hizmet kimlik bilgilerini ve ayrıca Service X. 509.440 sertifikası hakkındaki bilgileri belirtir. Örnek, Service `CN=localhost` X. 509.440 sertifikasında bir konu adı olarak kullanılır.

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
                // Try to find an X500DistinguishedName claim. This will
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

 İstemci uç noktası, hizmet uç noktasına benzer bir şekilde yapılandırılmıştır. İstemci, bir bağlama oluşturmak `BindingHelper` için aynı sınıfı kullanır. Kurulumun geri kalanı `Client` sınıfında bulunur. İstemci, istemci uç noktası davranışları koleksiyonuna, kurulum kodundaki Kullanıcı adı güvenlik belirteci ve hizmet X. 509.440 sertifikası hakkındaki bilgileri ayarlar.

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

## <a name="displaying-callers-information"></a>Arayanların bilgilerini görüntüleme
 Arayanın bilgilerini göstermek için aşağıdaki kodda gösterildiği `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` gibi kullanabilirsiniz. Geçerli çağıran ile ilişkili yetkilendirme taleplerini içerir.`ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` Bu talepler, iletide alınan her belirtecin Windows Communication Foundation (WCF) tarafından otomatik olarak sağlanır.

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
            //Try to find an X500DistinguishedName claim.
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

## <a name="running-the-sample"></a>Örnek çalıştırma
 Örneği çalıştırdığınızda, istemci önce Kullanıcı adı belirteci için Kullanıcı adı ve parola vermenizi ister. Hizmet üzerindeki WCF, Kullanıcı adı belirtecinde sağlanan değerleri sistem tarafından sağlanan kimliğe eşletiğinden, sistem hesabınız için doğru değerleri sağladığınızdan emin olun. Bundan sonra istemci, hizmetten yanıtı görüntüler. İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.

## <a name="setup-batch-file"></a>Toplu Iş dosyası kurulumu
 Bu örneğe eklenen Setup. bat toplu iş dosyası, sunucu sertifika tabanlı güvenlik gerektiren Internet Information Services (IIS) barındırılan uygulamasını çalıştırmak için sunucuyu ilgili sertifikalarla yapılandırmanıza olanak tanır. Bu toplu iş dosyası makineler arasında çalışacak şekilde değiştirilmelidir veya barındırılmayan bir durumda çalışır.

 Aşağıdakiler, uygun yapılandırmada çalışacak şekilde değiştirilebilecek şekilde, toplu iş dosyalarının farklı bölümlerine kısa bir genel bakış sağlar.

### <a name="creating-the-client-certificate"></a>Istemci sertifikası oluşturma
 Setup. bat toplu iş dosyasından aşağıdaki satırlar kullanılacak istemci sertifikasını oluşturur. `%CLIENT_NAME%` Değişkeni, istemci sertifikasının konusunu belirtir. Bu örnek, konu adı olarak "client.com" kullanır.

 Sertifika, `CurrentUser` depolama konumu altında (kişisel) deposunda depolanır.

```
echo ************
echo making client cert
echo ************
makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
```

### <a name="installing-the-client-certificate-into-the-servers-trusted-store"></a>Istemci sertifikasını sunucunun güvenilen deposuna yükleme
 Setup. bat toplu iş dosyasının aşağıdaki satırı, istemci sertifikasını sunucunun güvenilir kişiler deposuna kopyalar. Bu adım, MakeCert. exe tarafından oluşturulan sertifikaların sunucu sistemi tarafından örtük olarak güvenilir olmadığından gereklidir. İstemci tarafından güvenilen kök sertifikada kök sertifikaya sahip bir sertifikanız zaten varsa (örneğin, Microsoft tarafından verilen bir sertifika), istemci sertifikası deposunu sunucu sertifikasıyla doldurmanın bu adımı gerektirmez.

```
echo ************
echo copying client cert to server's CurrentUserstore
echo ************
certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
```

### <a name="creating-the-server-certificate"></a>Sunucu sertifikası oluşturma
 Setup. bat toplu iş dosyasından aşağıdaki satırlar kullanılacak sunucu sertifikasını oluşturur. `%SERVER_NAME%` Değişken, sunucu adını belirtir. Kendi sunucu adınızı belirtmek için bu değişkeni değiştirin. Bu toplu iş dosyasındaki varsayılan değer localhost 'tur.

 Sertifika, LocalMachine depolama konumu altında (kişisel) deposunda depolanır. Sertifika, IIS tarafından barındırılan hizmetler için LocalMachine deposunda depolanır. Şirket içinde barındırılan hizmetler için, LocalMachine dizesini CurrentUser ile değiştirerek, sunucu sertifikasını geçerli kullanıcı deposu konumunda depolayacak şekilde toplu iş dosyasını değiştirmelisiniz.

```
echo ************
echo Server cert setup starting
echo %SERVER_NAME%
echo ************
echo making server cert
echo ************
makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
```

### <a name="installing-server-certificate-into-clients-trusted-certificate-store"></a>Sunucu sertifikasını Istemcinin güvenilen sertifika deposuna yükleme
 Setup. bat toplu iş dosyası 'ndaki aşağıdaki satırlar, sunucu sertifikasını istemci güvenilir kişiler deposuna kopyalar. Bu adım, MakeCert. exe tarafından oluşturulan sertifikaların istemci sistemi tarafından örtük olarak güvenilir olmadığından gereklidir. İstemci tarafından güvenilen kök sertifikada kök sertifikaya sahip bir sertifikanız zaten varsa (örneğin, Microsoft tarafından verilen bir sertifika), istemci sertifikası deposunu sunucu sertifikasıyla doldurmanın bu adımı gerektirmez.

```
echo ************
echo copying server cert to client's TrustedPeople store
echo ************certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
```

### <a name="enabling-access-to-the-certificates-private-key"></a>Sertifikanın özel anahtarına erişimi etkinleştirme
 IIS tarafından barındırılan hizmetten sertifika özel anahtarına erişimi etkinleştirmek için, IIS tarafından barındırılan işlemin çalıştığı kullanıcı hesabına özel anahtar için uygun izinler verilmelidir. Bu, Setup. bat betiğinin son adımları tarafından gerçekleştirilir.

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

##### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için

1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.

2. Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)bölümündeki yönergeleri izleyin.

3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için aşağıdaki yönergeleri kullanın.

##### <a name="to-run-the-sample-on-the-same-machine"></a>Örneği aynı makinede çalıştırmak için

1. Visual Studio 2012 komut istemi içindeki örnek yükleme klasöründen Setup. bat dosyasını çalıştırarak yönetici ayrıcalıklarıyla çalıştırın. Bu, örneği çalıştırmak için gereken tüm sertifikaları kurar.

    > [!NOTE]
    > Setup. bat toplu iş dosyası bir Visual Studio 2012 komut Isteminden çalıştırılmak üzere tasarlanmıştır. Visual Studio 2012 komut Isteminde ayarlanan PATH ortam değişkeni Setup. bat betiği için gereken yürütülebilir dosyaları içeren dizine işaret eder. Örnek ile işiniz bittiğinde Cleanup. bat çalıştırarak sertifikaları kaldırmayı unutmayın. Diğer güvenlik örnekleri aynı sertifikaları kullanır.  
  
2. \Client\bin. adresinden Client. exe ' yi Başlat İstemci etkinliği istemci konsol uygulamasında görüntülenir.  
  
3. İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
##### <a name="to-run-the-sample-across-machines"></a>Örneği makineler arasında çalıştırmak için  
  
1. Hizmet makinesinde bir dizin oluşturun. Internet Information Services (IIS) yönetim aracını kullanarak bu dizin için servicemodelsamples adlı bir sanal uygulama oluşturun.  
  
2. Hizmet programı dosyalarını \inetpub\wwwroot\servicemodelsamples adresinden hizmet makinesindeki sanal dizine kopyalayın. Dosyaları \bin alt dizininde kopyalamadiğinizden emin olun. Ayrıca Setup. bat, Cleanup. bat ve ImportClientCert. bat dosyalarını hizmet makinesine kopyalayın.  
  
3. İstemci ikili dosyaları için istemci makinesinde bir dizin oluşturun.  
  
4. İstemci programı dosyalarını istemci makinesindeki istemci dizinine kopyalayın. Ayrıca Setup. bat, Cleanup. bat ve ImportServiceCert. bat dosyalarını istemciye kopyalayın.  
  
5. Sunucusunda, yönetici ayrıcalıklarıyla açılan `setup.bat service` bir Visual Studio için geliştirici komut istemi çalıştırın. Bağımsız`service` değişkeniyle birlikte çalıştırmak `setup.bat` makinenin tam etki alanı adına sahip bir hizmet sertifikası oluşturur ve hizmet sertifikasını Service. cer adlı bir dosyaya aktarır.  
  
6. Web. config dosyasını, makinenin tam etki alanı adıyla aynı olan yeni `findValue` sertifika adını ( [ \<ServiceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)özniteliğinde) yansıtacak şekilde düzenleyin.  
  
7. Service. cer dosyasını hizmet dizininden istemci makinesindeki istemci dizinine kopyalayın.  
  
8. İstemcisinde, yönetici ayrıcalıklarıyla açılan `setup.bat client` bir Visual Studio için geliştirici komut istemi çalıştırın. Bağımsız `setup.bat` değişkeniyle birlikte `client` çalıştırmak, Client.com adlı bir istemci sertifikası oluşturur ve istemci sertifikasını Client. cer adlı bir dosyaya aktarır.  
  
9. İstemci makinesindeki Client. exe. config dosyasında, uç noktanın adres değerini hizmetinizin yeni adresiyle eşleşecek şekilde değiştirin. Localhost 'u sunucunun tam etki alanı adıyla değiştirerek bunu yapın.  
  
10. Client. cer dosyasını istemci dizininden sunucusundaki hizmet dizinine kopyalayın.  
  
11. İstemcide ImportServiceCert. bat dosyasını çalıştırın. Bu, hizmet sertifikasını Service. cer dosyasından CurrentUser-Trustedkişiler deposuna aktarır.  
  
12. Sunucusunda ImportClientCert. bat dosyasını çalıştırın, bu, istemci sertifikasını Client. cer dosyasından LocalMachine-Trustedkişiler deposuna aktarır.  
  
13. İstemci makinesinde, bir komut istemi penceresinden Client. exe ' yi başlatın. İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
##### <a name="to-clean-up-after-the-sample"></a>Örnekten sonra temizlemek için  
  
- Örneği çalıştırmayı bitirdikten sonra Samples klasöründe Cleanup. bat dosyasını çalıştırın.  
  
> [!NOTE]
> Bu betik, makineler arasında bu örneği çalıştırırken bir istemcideki hizmet sertifikalarını kaldırmaz. Makinelerde sertifika kullanan WCF örnekleri çalıştırırsanız, CurrentUser-Trustedkişiler deposuna yüklenmiş olan hizmet sertifikalarını temizlediğinizden emin olun. Bunu yapmak için aşağıdaki komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`Örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.
