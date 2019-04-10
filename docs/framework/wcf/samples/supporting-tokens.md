---
title: Destek Belirteçleri
ms.date: 03/30/2017
ms.assetid: 65a8905d-92cc-4ab0-b6ed-1f710e40784e
ms.openlocfilehash: 5f2b1500f54f8ade3c4924e3eb22cd022c6800c0
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59334191"
---
# <a name="supporting-tokens"></a><span data-ttu-id="e0bfb-102">Destek Belirteçleri</span><span class="sxs-lookup"><span data-stu-id="e0bfb-102">Supporting Tokens</span></span>
<span data-ttu-id="e0bfb-103">WS-güvenlik kullanan bir iletiye ek belirteçler ekleme belirteçleri destekleyen örnek gösterir.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-103">The Supporting Tokens sample demonstrates how to add additional tokens to a message that uses WS-Security.</span></span> <span data-ttu-id="e0bfb-104">Örneğin, bir kullanıcı adı güvenlik belirteci yanı sıra bir X.509 ikili güvenlik belirteci ekler.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-104">The example adds an X.509 binary security token in addition to a username security token.</span></span> <span data-ttu-id="e0bfb-105">Belirteci bir WS-güvenlik uyarısı istemciden hizmete geçirilir ve iletisinin parçası X.509 sertifikası elinde alıcısına kanıtlamak için X.509 güvenlik belirteciyle ilişkili özel anahtarla imzalanır.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-105">The token is passed in a WS-Security message header from the client to the service and part of the message is signed with the private key associated with the X.509 security token to prove the possession of the X.509 certificate to the receiver.</span></span> <span data-ttu-id="e0bfb-106">Birden fazla talep kimlik doğrulaması veya yetkilendirme gönderen bir ileti ile ilişkili olan bir gereksinimi olduğunda bu durumda kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-106">This is useful in the case when there is a requirement to have multiple claims associated with a message to authenticate or authorize the sender.</span></span> <span data-ttu-id="e0bfb-107">Hizmet istek-yanıt iletişim deseni tanımlayan bir sözleşme uygular.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-107">The service implements a contract that defines a request-reply communication pattern.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="e0bfb-108">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="e0bfb-108">Demonstrates</span></span>
 <span data-ttu-id="e0bfb-109">Bir örnek göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="e0bfb-109">The sample demonstrates:</span></span>

-   <span data-ttu-id="e0bfb-110">Nasıl bir istemci bir hizmete ek güvenlik belirteçleri geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-110">How a client can pass additional security tokens to a service.</span></span>

-   <span data-ttu-id="e0bfb-111">Sunucu, ek güvenlik belirteçleri ile ilişkili talep nasıl erişebilir.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-111">How the server can access claims associated with additional security tokens.</span></span>

-   <span data-ttu-id="e0bfb-112">Sunucu X.509 sertifikasının nasıl ileti şifreleme ve imza için kullanılan simetrik anahtarı korumak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-112">How the server's X.509 certificate is used to protect the symmetric key used for message encryption and signature.</span></span>

> [!NOTE]
>  <span data-ttu-id="e0bfb-113">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-113">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

## <a name="client-authenticates-with-username-token-and-supporting-x509-security-token"></a><span data-ttu-id="e0bfb-114">Kullanıcı adı belirteci ve X.509 güvenlik belirteci destekleyen istemci kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="e0bfb-114">Client Authenticates with Username Token and Supporting X.509 Security Token</span></span>
 <span data-ttu-id="e0bfb-115">Program aracılığıyla kullanarak oluşturduğunuz iletişim kurmak için tek bir uç nokta hizmetini sunar `BindingHelper` ve `EchoServiceHost` sınıfları.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-115">The service exposes a single endpoint for communicating that is programmatically created using the `BindingHelper` and `EchoServiceHost` classes.</span></span> <span data-ttu-id="e0bfb-116">Uç nokta, adres, bağlama ve bir sözleşme oluşur.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-116">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="e0bfb-117">Özel bağlama kullanma yapılandırılmış bağlama `SymmetricSecurityBindingElement` ve `HttpTransportBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-117">The binding is configured with a custom binding using `SymmetricSecurityBindingElement` and `HttpTransportBindingElement`.</span></span> <span data-ttu-id="e0bfb-118">Bu örnek ayarlar `SymmetricSecurityBindingElement` simetrik anahtar aktarım sırasında korumak ve geçirilecek hizmet X.509 sertifikası kullanmak için bir `UserNameToken` destekleyici birlikte `X509SecurityToken` WS-güvenlik ileti üstbilgisinde.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-118">This sample sets the `SymmetricSecurityBindingElement` to use a service X.509 certificate to protect the symmetric key during transmission and to pass a `UserNameToken` along with the supporting `X509SecurityToken` in a WS-Security message header.</span></span> <span data-ttu-id="e0bfb-119">Simetrik anahtar, ileti gövdesi ve kullanıcı adı güvenlik belirteci şifrelemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-119">The symmetric key is used to encrypt the message body and the username security token.</span></span> <span data-ttu-id="e0bfb-120">Destekleme belirteci, WS-güvenlik ileti üstbilgisinde bir ek ikili güvenlik belirteci olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-120">The supporting token is passed as an additional binary security token in the WS-Security message header.</span></span> <span data-ttu-id="e0bfb-121">Destekleyici X.509 güvenlik ile ilişkili özel anahtara sahip ileti parçası açarak destekleme belirteci kimlik doğrulaması belirteci sağlanır.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-121">The authenticity of the supporting token is proved by signing part of the message with the private key associated with the supporting X.509 security token.</span></span>

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

 <span data-ttu-id="e0bfb-122">Davranış, istemci kimlik doğrulaması ve ayrıca hizmet X.509 sertifikası hakkında daha fazla bilgi için kullanılacak hizmet kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-122">The behavior specifies the service credentials that are to be used for client authentication and also information about the service X.509 certificate.</span></span> <span data-ttu-id="e0bfb-123">Örnek kullanır `CN=localhost` hizmet X.509 sertifikasındaki konu adı.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-123">The sample uses `CN=localhost` as a subject name in the service X.509 certificate.</span></span>

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

 <span data-ttu-id="e0bfb-124">Hizmet kodu:</span><span class="sxs-lookup"><span data-stu-id="e0bfb-124">Service code:</span></span>

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

 <span data-ttu-id="e0bfb-125">İstemci uç noktası, hizmet uç noktası için benzer bir şekilde yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-125">The client endpoint is configured in a similar way to the service endpoint.</span></span> <span data-ttu-id="e0bfb-126">Aynı istemcinin kullandığı `BindingHelper` bağlama oluşturmak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-126">The client uses the same `BindingHelper` class to create a binding.</span></span> <span data-ttu-id="e0bfb-127">Kurulumu geri kalanını bulunan `Client` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-127">The rest of the setup is located in `Client` class.</span></span> <span data-ttu-id="e0bfb-128">İstemci, istemci uç nokta davranışları koleksiyon Kurulum kodu kullanıcı adı güvenlik belirteci, destekleyici X.509 güvenlik belirteci ve hizmet X.509 sertifikası hakkında bilgi hakkında bilgi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-128">The client sets information about the user name security token, the supporting X.509 security token and information about the service X.509 certificate in the setup code to the client endpoint behaviors collection.</span></span>

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

## <a name="displaying-callers-information"></a><span data-ttu-id="e0bfb-129">Çağıranlar bilgileri görüntüleme</span><span class="sxs-lookup"><span data-stu-id="e0bfb-129">Displaying Callers' Information</span></span>
 <span data-ttu-id="e0bfb-130">Arayanın bilgileri görüntülemek için kullanabileceğiniz `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-130">To display the caller's information, you can use the `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` as shown in the following code.</span></span> <span data-ttu-id="e0bfb-131">`ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` Geçerli arayanla ilişkili yetkilendirme talepleri içerir.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-131">The `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` contains authorization claims associated with the current caller.</span></span> <span data-ttu-id="e0bfb-132">Bu talep, otomatik olarak yer alan her bir belirteç için Windows Communication Foundation (WCF) tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-132">Those claims are supplied automatically by Windows Communication Foundation (WCF) for every token received in the message.</span></span>

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

## <a name="running-the-sample"></a><span data-ttu-id="e0bfb-133">Örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="e0bfb-133">Running the Sample</span></span>
 <span data-ttu-id="e0bfb-134">Örneği çalıştırdığınızda, istemci önce kullanıcı adı belirteci kullanıcı adı ve parola girmenizi ister.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-134">When you run the sample, the client first prompts you to provide user name and password for the user name token.</span></span> <span data-ttu-id="e0bfb-135">WCF hizmeti olarak sistem tarafından sağlanan kimlik kullanıcı adı belirteç sağlanan değerler eşlediğinden, sistem hesabı için doğru değerleri sağlayın emin olun.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-135">Be sure to provide correct values for your system account, because WCF on the service maps the values supplied in the user name token into the identity provided by the system.</span></span> <span data-ttu-id="e0bfb-136">Bundan sonra istemci hizmetinden gelen yanıt görüntüler.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-136">After that, the client displays the response from the service.</span></span> <span data-ttu-id="e0bfb-137">İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-137">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="e0bfb-138">Kurulum toplu iş dosyası</span><span class="sxs-lookup"><span data-stu-id="e0bfb-138">Setup Batch File</span></span>
 <span data-ttu-id="e0bfb-139">Bu örnekle dahil Setup.bat toplu iş dosyası ile ilgili sertifika sunucusu sertifika tabanlı güvenlik gerektiren Internet Information Services (IIS) barındırılan uygulamayı çalıştırmak için sunucu yapılandırmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-139">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run Internet Information Services (IIS) hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="e0bfb-140">Bu toplu iş dosyası makinelerde çalışmaya veya barındırılan olmayan bir durumda çalışması için değiştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-140">This batch file must be modified to work across machines or to work in a non-hosted case.</span></span>

 <span data-ttu-id="e0bfb-141">Aşağıda, böylece uygun yapılandırmasında çalıştırılacak değiştirilebilir toplu iş dosyaları farklı bölümlerini kısa bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-141">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in appropriate configuration.</span></span>

### <a name="creating-the-client-certificate"></a><span data-ttu-id="e0bfb-142">İstemci sertifikası oluşturma</span><span class="sxs-lookup"><span data-stu-id="e0bfb-142">Creating the Client Certificate</span></span>
 <span data-ttu-id="e0bfb-143">Setup.bat toplu iş dosyasından aşağıdaki satırları kullanılacak istemci sertifikası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-143">The following lines from the Setup.bat batch file create the client certificate to be used.</span></span> <span data-ttu-id="e0bfb-144">`%CLIENT_NAME%` Değişkeni, istemci sertifikasındaki konu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-144">The `%CLIENT_NAME%` variable specifies the subject of the client certificate.</span></span> <span data-ttu-id="e0bfb-145">Bu örnekte, konu adı olarak "client.com" kullanır.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-145">This sample uses "client.com" as the subject name.</span></span>

 <span data-ttu-id="e0bfb-146">Sertifika altında (Kişisel) My deposunda saklanır `CurrentUser` depolama konumu.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-146">The certificate is stored in My (Personal) store under the `CurrentUser` store location.</span></span>

```
echo ************
echo making client cert
echo ************
makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
```

### <a name="installing-the-client-certificate-into-the-servers-trusted-store"></a><span data-ttu-id="e0bfb-147">Sunucunun güvenilen Store istemci sertifikası yükleme</span><span class="sxs-lookup"><span data-stu-id="e0bfb-147">Installing the Client Certificate into the Server's Trusted Store</span></span>
 <span data-ttu-id="e0bfb-148">Setup.bat toplu iş dosyasında aşağıdaki satırı, istemci sertifikası sunucusunun güvenilir Kişiler deposuna kopyalar.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-148">The following line in the Setup.bat batch file copies the client certificate into the server’s trusted people store.</span></span> <span data-ttu-id="e0bfb-149">MakeCert.exe tarafından oluşturulan sertifika sunucunun sistem tarafından örtük olarak güvenilmeyen olduğundan bu adım gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-149">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the server’s system.</span></span> <span data-ttu-id="e0bfb-150">Bir istemci güvenilen kök sertifikayı kök erişim izni verilmiş bir sertifika zaten varsa — örneğin, Microsoft tarafından verilen sertifika — sunucu sertifikasında istemci sertifika deposunun doldurulması, bu adım gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-150">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

```
echo ************
echo copying client cert to server's CurrentUserstore
echo ************
certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
```

### <a name="creating-the-server-certificate"></a><span data-ttu-id="e0bfb-151">Sunucu sertifikası oluşturma</span><span class="sxs-lookup"><span data-stu-id="e0bfb-151">Creating the Server Certificate</span></span>
 <span data-ttu-id="e0bfb-152">Setup.bat toplu iş dosyasından aşağıdaki satırları kullanılacak sunucu sertifikası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-152">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="e0bfb-153">`%SERVER_NAME%` Değişkeni, sunucu adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-153">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="e0bfb-154">Kendi sunucu adını belirtmek için bu değişkeni değiştirin.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-154">Change this variable to specify your own server name.</span></span> <span data-ttu-id="e0bfb-155">Bu toplu iş dosyasında localhost varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-155">The default in this batch file is localhost.</span></span>

 <span data-ttu-id="e0bfb-156">Sertifikayı LocalMachine depolama konumu altında (Kişisel) My deposunda depolanır.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-156">The certificate is stored in My (Personal) store under the LocalMachine store location.</span></span> <span data-ttu-id="e0bfb-157">Depolanmış bir sertifikayla IIS tarafından barındırılan hizmetleri LocalMachine deposunda.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-157">The certificate is stored in the LocalMachine store for the IIS-hosted services.</span></span> <span data-ttu-id="e0bfb-158">Şirket içinde barındırılan hizmetler için sunucu sertifikası LocalMachine dize CurrentUser ile değiştirerek CurrentUser deposu konumda depolamak için toplu iş dosyasını değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-158">For self-hosted services, you should modify the batch file to store the server certificate in the CurrentUser store location by replacing the string LocalMachine with CurrentUser.</span></span>

```
echo ************
echo Server cert setup starting
echo %SERVER_NAME%
echo ************
echo making server cert
echo ************
makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
```

### <a name="installing-server-certificate-into-clients-trusted-certificate-store"></a><span data-ttu-id="e0bfb-159">İstemcinin güvenilen sertifika Store sunucu sertifikası yükleme</span><span class="sxs-lookup"><span data-stu-id="e0bfb-159">Installing Server Certificate into Client's Trusted Certificate Store</span></span>
 <span data-ttu-id="e0bfb-160">İstemci güvenilir kişiler uygulamasına Setup.bat toplu dosya kopyalama sunucu sertifikasının aşağıdaki satırları depolayın.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-160">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="e0bfb-161">MakeCert.exe tarafından oluşturulan sertifikaları örtük olarak istemci sistemi tarafından güvenilir değildir çünkü bu adım gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-161">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="e0bfb-162">Bir istemci güvenilen kök sertifikayı kök erişim izni verilmiş bir sertifika zaten varsa — örneğin, Microsoft tarafından verilen sertifika — sunucu sertifikasında istemci sertifika deposunun doldurulması, bu adım gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-162">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

```
echo ************
echo copying server cert to client's TrustedPeople store
echo ************certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
```

### <a name="enabling-access-to-the-certificates-private-key"></a><span data-ttu-id="e0bfb-163">Sertifikanın özel anahtarı erişimini etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="e0bfb-163">Enabling Access to the Certificate's Private Key</span></span>
 <span data-ttu-id="e0bfb-164">IIS barındırılan hizmeti için sertifika özel anahtar erişimi etkinleştirmek için IIS tarafından barındırılan işlem altında çalıştığı hesabın özel anahtar için uygun izinleri verilmelidir.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-164">To enable access to the certificate private key from the IIS-hosted service, the user account under which the IIS-hosted process is running must be granted appropriate permissions for the private key.</span></span> <span data-ttu-id="e0bfb-165">Bu, son adımda Setup.bat betiği tarafından gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-165">This is accomplished by last steps in the Setup.bat script.</span></span>

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

##### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e0bfb-166">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="e0bfb-166">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="e0bfb-167">Gerçekleştirilen mutlaka [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e0bfb-167">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="e0bfb-168">Çözümü derlemek için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e0bfb-168">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="e0bfb-169">Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için aşağıdaki yönergeleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-169">To run the sample in a single- or cross-machine configuration, use the following instructions.</span></span>

##### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="e0bfb-170">Örneği aynı makinede çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="e0bfb-170">To run the sample on the same machine</span></span>

1. <span data-ttu-id="e0bfb-171">Visual Studio 2012 komut istemini yönetici ayrıcalıklarıyla çalıştırın içinde örnek yükleme klasöründen Setup.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-171">Run Setup.bat from the sample install folder inside a Visual Studio 2012 command prompt run with administrator privileges.</span></span> <span data-ttu-id="e0bfb-172">Bu örneği çalıştırmak için gerekli olan tüm sertifikaları yükler.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-172">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="e0bfb-173">Setup.bat toplu iş dosyası, bir Visual Studio 2012 komut isteminden çalıştırılması için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-173">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="e0bfb-174">PATH ortam değişkenine içinde Visual Studio 2012 komut istemi noktaları Setup.bat betiği tarafından gereken yürütülebilir dosyaları içeren dizine ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-174">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span> <span data-ttu-id="e0bfb-175">Sertifikaları örnek ile işiniz bittiğinde Cleanup.bat çalıştırarak kaldırmayı unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-175">Be sure to remove the certificates by running Cleanup.bat when finished with the sample.</span></span> <span data-ttu-id="e0bfb-176">Diğer güvenlik örnekleri aynı sertifikalarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-176">Other security samples use the same certificates.</span></span>  
  
2. <span data-ttu-id="e0bfb-177">Client.exe \client\bin başlatın.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-177">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="e0bfb-178">İstemci etkinliği istemci konsol uygulamasında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-178">Client activity is displayed on the client console application.</span></span>  
  
3. <span data-ttu-id="e0bfb-179">İstemci ve hizmet iletişim kurabildiğini bilmiyorsanız bkz [WCF örnekleri için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="e0bfb-179">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
##### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="e0bfb-180">Makineler arasında örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="e0bfb-180">To run the sample across machines</span></span>  
  
1. <span data-ttu-id="e0bfb-181">Bir dizin hizmeti makinede oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-181">Create a directory on the service machine.</span></span> <span data-ttu-id="e0bfb-182">Internet Information Services (IIS) yönetim aracını kullanarak bu dizin için servicemodelsamples adlı sanal bir uygulama oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-182">Create a virtual application named servicemodelsamples for this directory using the Internet Information Services (IIS) management tool.</span></span>  
  
2. <span data-ttu-id="e0bfb-183">Hizmet program dosyaları \inetpub\wwwroot\servicemodelsamples hizmeti makinede sanal dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-183">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service machine.</span></span> <span data-ttu-id="e0bfb-184">Dosyaları \bin alt dizinde kopyalama emin olun.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-184">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="e0bfb-185">Ayrıca hizmeti makineye Setup.bat Cleanup.bat ve ImportClientCert.bat dosyaları kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-185">Also copy the Setup.bat, Cleanup.bat, and ImportClientCert.bat files to the service machine.</span></span>  
  
3. <span data-ttu-id="e0bfb-186">İstemci ikili dosyaları için istemci makinede bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-186">Create a directory on the client machine for the client binaries.</span></span>  
  
4. <span data-ttu-id="e0bfb-187">İstemci makinesinde istemci dizinine istemci program dosyaları kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-187">Copy the client program files to the client directory on the client machine.</span></span> <span data-ttu-id="e0bfb-188">Aynı zamanda istemciye Setup.bat Cleanup.bat ve ImportServiceCert.bat dosyaları kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-188">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5. <span data-ttu-id="e0bfb-189">Sunucu üzerinde çalışan `setup.bat service` Geliştirici komut istemi için Visual Studio yönetici ayrıcalıklarıyla açılmış.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-189">On the server, run `setup.bat service` in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="e0bfb-190">Çalışan `setup.bat` ile `service` bağımsız değişkeni makinenin tam etki alanı adı ile bir hizmet sertifikası oluşturur ve hizmet sertifikası Service.cer adlı bir dosyaya dışarı aktarır.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-190">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the machine and exports the service certificate to a file named Service.cer.</span></span>  
  
6. <span data-ttu-id="e0bfb-191">Yeni sertifika adını yansıtacak şekilde Web.config'i düzenlemek (içinde `findValue` özniteliğini [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) makinesinin tam etki alanı adıyla aynı olduğu.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-191">Edit Web.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully-qualified domain name of the machine.</span></span>  
  
7. <span data-ttu-id="e0bfb-192">Service.cer dosya hizmeti dizininden istemci makine üzerinde istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-192">Copy the Service.cer file from the service directory to the client directory on the client machine.</span></span>  
  
8. <span data-ttu-id="e0bfb-193">Bir istemcide çalışmasına `setup.bat client` Geliştirici komut istemi için Visual Studio yönetici ayrıcalıklarıyla açılmış.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-193">On the client, run `setup.bat client` in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="e0bfb-194">Çalışan `setup.bat` ile `client` bağımsız değişkeni client.com adlı bir istemci sertifikası oluşturur ve istemci sertifikasını Client.cer adlı bir dosyaya dışarı aktarır.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-194">Running `setup.bat` with the `client` argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
9. <span data-ttu-id="e0bfb-195">İstemci makinesinde Client.exe.config dosyasında hizmetinizin yeni adresiyle eşleşecek şekilde uç nokta adresi değiştirin.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-195">In the Client.exe.config file on the client machine, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="e0bfb-196">Localhost sunucunun tam etki alanı adıyla değiştirerek bunu.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-196">Do this by replacing localhost with the fully-qualified domain name of the server.</span></span>  
  
10. <span data-ttu-id="e0bfb-197">Client.cer dosyayı istemci dizin sunucusundaki hizmet dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-197">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
11. <span data-ttu-id="e0bfb-198">İstemcide ImportServiceCert.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-198">On the client, run ImportServiceCert.bat.</span></span> <span data-ttu-id="e0bfb-199">Bu hizmet sertifikası Service.cer dosyasından CurrentUser - TrustedPeople deposuna aktarır.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-199">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="e0bfb-200">ImportClientCert.bat, çalıştıran sunucuda bu istemci sertifikasını Client.cer dosyasından LocalMachine - TrustedPeople deposu içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-200">On the server, run ImportClientCert.bat, This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
13. <span data-ttu-id="e0bfb-201">İstemci makinesinde bir komut istemi penceresinden Client.exe başlatın.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-201">On the client machine, launch Client.exe from a command prompt window.</span></span> <span data-ttu-id="e0bfb-202">İstemci ve hizmet iletişim kurabildiğini bilmiyorsanız bkz [WCF örnekleri için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="e0bfb-202">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
##### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="e0bfb-203">Sonra örnek temizlemek için</span><span class="sxs-lookup"><span data-stu-id="e0bfb-203">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="e0bfb-204">Bu örneği çalıştırmadan tamamladıktan sonra Cleanup.bat samples klasöründe çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-204">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e0bfb-205">Bu betik, bu örnek makinelerde çalışan hizmet sertifikaları bir istemci üzerinde kaldırmaz.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-205">This script does not remove service certificates on a client when running this sample across machines.</span></span> <span data-ttu-id="e0bfb-206">Makineler arasında sertifikaları kullanan WCF örnekleri çalıştırırsanız, CurrentUser - TrustedPeople deposu yüklü hizmet sertifikalarını Temizle emin olun.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-206">If you have run WCF samples that use certificates across machines, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="e0bfb-207">Bunu yapmak için aşağıdaki komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="e0bfb-207">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>
