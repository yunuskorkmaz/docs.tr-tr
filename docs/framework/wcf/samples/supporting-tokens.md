---
title: Destek Belirteçleri
ms.date: 03/30/2017
ms.assetid: 65a8905d-92cc-4ab0-b6ed-1f710e40784e
ms.openlocfilehash: ff46a2f5289bc72244ea586f01ea05504d628f69
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555204"
---
# <a name="supporting-tokens"></a><span data-ttu-id="3bc2d-102">Destek Belirteçleri</span><span class="sxs-lookup"><span data-stu-id="3bc2d-102">Supporting Tokens</span></span>
<span data-ttu-id="3bc2d-103">Destekleme belirteçleri örneği, WS-Security kullanan bir iletiye nasıl ek belirteç ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-103">The Supporting Tokens sample demonstrates how to add additional tokens to a message that uses WS-Security.</span></span> <span data-ttu-id="3bc2d-104">Örnek, bir Kullanıcı adı güvenlik belirtecinin yanı sıra bir X. 509.440 ikili güvenlik belirteci ekler.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-104">The example adds an X.509 binary security token in addition to a username security token.</span></span> <span data-ttu-id="3bc2d-105">Belirteç, istemciden hizmete bir WS-Security ileti üst bilgisine geçirilir ve iletinin bir bölümü x. 509.440 sertifikasının alıcıya sahip olduğunu kanıtlamak için X. 509.440 güvenlik belirteciyle ilişkili özel anahtarla imzalanır.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-105">The token is passed in a WS-Security message header from the client to the service and part of the message is signed with the private key associated with the X.509 security token to prove the possession of the X.509 certificate to the receiver.</span></span> <span data-ttu-id="3bc2d-106">Bu, gönderenin kimliğini doğrulamak veya yetkilendirmek için bir iletiyle ilişkilendirilmiş birden çok talebe sahip olması durumunda yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-106">This is useful in the case when there is a requirement to have multiple claims associated with a message to authenticate or authorize the sender.</span></span> <span data-ttu-id="3bc2d-107">Hizmet, istek-yanıt iletişim modelini tanımlayan bir sözleşme uygular.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-107">The service implements a contract that defines a request-reply communication pattern.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="3bc2d-108">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="3bc2d-108">Demonstrates</span></span>
 <span data-ttu-id="3bc2d-109">Örnek şunları gösterir:</span><span class="sxs-lookup"><span data-stu-id="3bc2d-109">The sample demonstrates:</span></span>

- <span data-ttu-id="3bc2d-110">Bir istemcinin bir hizmete nasıl ek güvenlik belirteçleri geçirebilirler.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-110">How a client can pass additional security tokens to a service.</span></span>

- <span data-ttu-id="3bc2d-111">Sunucunun ek güvenlik belirteçleriyle ilişkili taleplere erişme şekli.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-111">How the server can access claims associated with additional security tokens.</span></span>

- <span data-ttu-id="3bc2d-112">Sunucu X. 509.440 sertifikası ileti şifreleme ve imza için kullanılan simetrik anahtarı korumak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-112">How the server's X.509 certificate is used to protect the symmetric key used for message encryption and signature.</span></span>

> [!NOTE]
> <span data-ttu-id="3bc2d-113">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-113">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

## <a name="client-authenticates-with-username-token-and-supporting-x509-security-token"></a><span data-ttu-id="3bc2d-114">İstemci Kullanıcı adı belirteciyle kimliğini doğrular ve X. 509.440 güvenlik belirtecini destekler</span><span class="sxs-lookup"><span data-stu-id="3bc2d-114">Client Authenticates with Username Token and Supporting X.509 Security Token</span></span>
 <span data-ttu-id="3bc2d-115">Hizmet, ve sınıfları kullanılarak programlı bir şekilde oluşturulan iletişim için tek bir uç nokta sunar `BindingHelper` `EchoServiceHost` .</span><span class="sxs-lookup"><span data-stu-id="3bc2d-115">The service exposes a single endpoint for communicating that is programmatically created using the `BindingHelper` and `EchoServiceHost` classes.</span></span> <span data-ttu-id="3bc2d-116">Uç nokta bir adres, bağlama ve bir anlaşmada oluşur.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-116">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="3bc2d-117">Bağlama, ve kullanarak özel bir bağlama ile yapılandırılır `SymmetricSecurityBindingElement` `HttpTransportBindingElement` .</span><span class="sxs-lookup"><span data-stu-id="3bc2d-117">The binding is configured with a custom binding using `SymmetricSecurityBindingElement` and `HttpTransportBindingElement`.</span></span> <span data-ttu-id="3bc2d-118">Bu örnek, `SymmetricSecurityBindingElement` iletim sırasında simetrik anahtarı korumak ve BIR `UserNameToken` `X509SecurityToken` WS-Security ileti üstbilgisinde destekleyici ile geçiş yapmak Için bir Service X. 509.952 sertifikası kullanmak üzere ayarlar.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-118">This sample sets the `SymmetricSecurityBindingElement` to use a service X.509 certificate to protect the symmetric key during transmission and to pass a `UserNameToken` along with the supporting `X509SecurityToken` in a WS-Security message header.</span></span> <span data-ttu-id="3bc2d-119">Simetrik anahtar, ileti gövdesini ve Kullanıcı adı güvenlik belirtecini şifrelemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-119">The symmetric key is used to encrypt the message body and the username security token.</span></span> <span data-ttu-id="3bc2d-120">Destekleme belirteci, WS-Security ileti üstbilgisinde ek bir ikili güvenlik belirteci olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-120">The supporting token is passed as an additional binary security token in the WS-Security message header.</span></span> <span data-ttu-id="3bc2d-121">Destekleyici belirtecin özgünlük belgesi, iletinin bir parçası destekleyici X. 509.440 güvenlik belirteci ile ilişkili özel anahtarla imzalanarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-121">The authenticity of the supporting token is proved by signing part of the message with the private key associated with the supporting X.509 security token.</span></span>

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

 <span data-ttu-id="3bc2d-122">Davranış, istemci kimlik doğrulaması için kullanılacak hizmet kimlik bilgilerini ve ayrıca Service X. 509.440 sertifikası hakkındaki bilgileri belirtir.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-122">The behavior specifies the service credentials that are to be used for client authentication and also information about the service X.509 certificate.</span></span> <span data-ttu-id="3bc2d-123">Örnek, `CN=localhost` Service X. 509.440 sertifikasında bir konu adı olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-123">The sample uses `CN=localhost` as a subject name in the service X.509 certificate.</span></span>

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

 <span data-ttu-id="3bc2d-124">Hizmet kodu:</span><span class="sxs-lookup"><span data-stu-id="3bc2d-124">Service code:</span></span>

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

 <span data-ttu-id="3bc2d-125">İstemci uç noktası, hizmet uç noktasına benzer bir şekilde yapılandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-125">The client endpoint is configured in a similar way to the service endpoint.</span></span> <span data-ttu-id="3bc2d-126">İstemci, `BindingHelper` bir bağlama oluşturmak için aynı sınıfı kullanır.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-126">The client uses the same `BindingHelper` class to create a binding.</span></span> <span data-ttu-id="3bc2d-127">Kurulumun geri kalanı `Client` sınıfında bulunur.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-127">The rest of the setup is located in `Client` class.</span></span> <span data-ttu-id="3bc2d-128">İstemci, istemci uç noktası davranışları koleksiyonuna, kurulum kodundaki Kullanıcı adı güvenlik belirteci ve hizmet X. 509.440 sertifikası hakkındaki bilgileri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-128">The client sets information about the user name security token, the supporting X.509 security token and information about the service X.509 certificate in the setup code to the client endpoint behaviors collection.</span></span>

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

## <a name="displaying-callers-information"></a><span data-ttu-id="3bc2d-129">Arayanların bilgilerini görüntüleme</span><span class="sxs-lookup"><span data-stu-id="3bc2d-129">Displaying Callers' Information</span></span>
 <span data-ttu-id="3bc2d-130">Arayanın bilgilerini göstermek için `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` aşağıdaki kodda gösterildiği gibi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-130">To display the caller's information, you can use the `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` as shown in the following code.</span></span> <span data-ttu-id="3bc2d-131">`ServiceSecurityContext.Current.AuthorizationContext.ClaimSets`Geçerli çağıran ile ilişkili yetkilendirme taleplerini içerir.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-131">The `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` contains authorization claims associated with the current caller.</span></span> <span data-ttu-id="3bc2d-132">Bu talepler, iletide alınan her belirtecin Windows Communication Foundation (WCF) tarafından otomatik olarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-132">Those claims are supplied automatically by Windows Communication Foundation (WCF) for every token received in the message.</span></span>

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

## <a name="running-the-sample"></a><span data-ttu-id="3bc2d-133">Örnek çalıştırma</span><span class="sxs-lookup"><span data-stu-id="3bc2d-133">Running the Sample</span></span>
 <span data-ttu-id="3bc2d-134">Örneği çalıştırdığınızda, istemci önce Kullanıcı adı belirteci için Kullanıcı adı ve parola vermenizi ister.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-134">When you run the sample, the client first prompts you to provide user name and password for the user name token.</span></span> <span data-ttu-id="3bc2d-135">Hizmet üzerindeki WCF, Kullanıcı adı belirtecinde sağlanan değerleri sistem tarafından sağlanan kimliğe eşletiğinden, sistem hesabınız için doğru değerleri sağladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-135">Be sure to provide correct values for your system account, because WCF on the service maps the values supplied in the user name token into the identity provided by the system.</span></span> <span data-ttu-id="3bc2d-136">Bundan sonra istemci, hizmetten yanıtı görüntüler.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-136">After that, the client displays the response from the service.</span></span> <span data-ttu-id="3bc2d-137">İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-137">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="3bc2d-138">Toplu Iş dosyası kurulumu</span><span class="sxs-lookup"><span data-stu-id="3bc2d-138">Setup Batch File</span></span>
 <span data-ttu-id="3bc2d-139">Bu örneğe eklenen Setup.bat Batch dosyası, sunucu sertifika tabanlı güvenlik gerektiren Internet Information Services (IIS) barındırılan uygulamasını çalıştırmak üzere sunucuyu ilgili sertifikalarla yapılandırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-139">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run Internet Information Services (IIS) hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="3bc2d-140">Bu toplu iş dosyası makineler arasında çalışacak şekilde değiştirilmelidir veya barındırılmayan bir durumda çalışır.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-140">This batch file must be modified to work across machines or to work in a non-hosted case.</span></span>

 <span data-ttu-id="3bc2d-141">Aşağıdakiler, uygun yapılandırmada çalışacak şekilde değiştirilebilecek şekilde, toplu iş dosyalarının farklı bölümlerine kısa bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-141">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in appropriate configuration.</span></span>

### <a name="creating-the-client-certificate"></a><span data-ttu-id="3bc2d-142">Istemci sertifikası oluşturma</span><span class="sxs-lookup"><span data-stu-id="3bc2d-142">Creating the Client Certificate</span></span>
 <span data-ttu-id="3bc2d-143">Setup.bat Batch dosyasından aşağıdaki satırlar kullanılacak istemci sertifikasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-143">The following lines from the Setup.bat batch file create the client certificate to be used.</span></span> <span data-ttu-id="3bc2d-144">`%CLIENT_NAME%`Değişkeni, istemci sertifikasının konusunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-144">The `%CLIENT_NAME%` variable specifies the subject of the client certificate.</span></span> <span data-ttu-id="3bc2d-145">Bu örnek, konu adı olarak "client.com" kullanır.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-145">This sample uses "client.com" as the subject name.</span></span>

 <span data-ttu-id="3bc2d-146">Sertifika, depolama konumu altında (kişisel) deposunda depolanır `CurrentUser` .</span><span class="sxs-lookup"><span data-stu-id="3bc2d-146">The certificate is stored in My (Personal) store under the `CurrentUser` store location.</span></span>

```console
echo ************
echo making client cert
echo ************
makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
```

### <a name="installing-the-client-certificate-into-the-servers-trusted-store"></a><span data-ttu-id="3bc2d-147">Istemci sertifikasını sunucunun güvenilen deposuna yükleme</span><span class="sxs-lookup"><span data-stu-id="3bc2d-147">Installing the Client Certificate into the Server's Trusted Store</span></span>
 <span data-ttu-id="3bc2d-148">Setup.bat Batch dosyasında aşağıdaki satır, istemci sertifikasını sunucunun güvenilir kişiler deposuna kopyalar.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-148">The following line in the Setup.bat batch file copies the client certificate into the server’s trusted people store.</span></span> <span data-ttu-id="3bc2d-149">Bu adım, Makecert.exe tarafından oluşturulan sertifikalara sunucunun sistemi tarafından örtük olarak güvenilmediği için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-149">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the server’s system.</span></span> <span data-ttu-id="3bc2d-150">İstemci tarafından güvenilen kök sertifikada kök sertifikaya sahip bir sertifikanız zaten varsa (örneğin, Microsoft tarafından verilen bir sertifika), istemci sertifikası deposunu sunucu sertifikasıyla doldurmanın bu adımı gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-150">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

```console
echo ************
echo copying client cert to server's CurrentUserstore
echo ************
certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
```

### <a name="creating-the-server-certificate"></a><span data-ttu-id="3bc2d-151">Sunucu sertifikası oluşturma</span><span class="sxs-lookup"><span data-stu-id="3bc2d-151">Creating the Server Certificate</span></span>
 <span data-ttu-id="3bc2d-152">Setup.bat Batch dosyasından aşağıdaki satırlar kullanılacak sunucu sertifikasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-152">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="3bc2d-153">`%SERVER_NAME%`Değişken, sunucu adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-153">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="3bc2d-154">Kendi sunucu adınızı belirtmek için bu değişkeni değiştirin.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-154">Change this variable to specify your own server name.</span></span> <span data-ttu-id="3bc2d-155">Bu toplu iş dosyasındaki varsayılan değer localhost 'tur.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-155">The default in this batch file is localhost.</span></span>

 <span data-ttu-id="3bc2d-156">Sertifika, LocalMachine depolama konumu altında (kişisel) deposunda depolanır.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-156">The certificate is stored in My (Personal) store under the LocalMachine store location.</span></span> <span data-ttu-id="3bc2d-157">Sertifika, IIS tarafından barındırılan hizmetler için LocalMachine deposunda depolanır.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-157">The certificate is stored in the LocalMachine store for the IIS-hosted services.</span></span> <span data-ttu-id="3bc2d-158">Şirket içinde barındırılan hizmetler için, LocalMachine dizesini CurrentUser ile değiştirerek, sunucu sertifikasını geçerli kullanıcı deposu konumunda depolayacak şekilde toplu iş dosyasını değiştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-158">For self-hosted services, you should modify the batch file to store the server certificate in the CurrentUser store location by replacing the string LocalMachine with CurrentUser.</span></span>

```console
echo ************
echo Server cert setup starting
echo %SERVER_NAME%
echo ************
echo making server cert
echo ************
makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
```

### <a name="installing-server-certificate-into-clients-trusted-certificate-store"></a><span data-ttu-id="3bc2d-159">Sunucu sertifikasını Istemcinin güvenilen sertifika deposuna yükleme</span><span class="sxs-lookup"><span data-stu-id="3bc2d-159">Installing Server Certificate into Client's Trusted Certificate Store</span></span>
 <span data-ttu-id="3bc2d-160">Setup.bat Batch dosyasındaki aşağıdaki satırlar, sunucu sertifikasını istemci güvenilir kişiler deposuna kopyalar.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-160">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="3bc2d-161">Makecert.exe tarafından oluşturulan sertifikalara istemci sistemi tarafından örtük olarak güvenilmediğinden Bu adım gereklidir.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-161">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="3bc2d-162">İstemci tarafından güvenilen kök sertifikada kök sertifikaya sahip bir sertifikanız zaten varsa (örneğin, Microsoft tarafından verilen bir sertifika), istemci sertifikası deposunu sunucu sertifikasıyla doldurmanın bu adımı gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-162">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

```console
echo ************
echo copying server cert to client's TrustedPeople store
echo ************certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
```

### <a name="enabling-access-to-the-certificates-private-key"></a><span data-ttu-id="3bc2d-163">Sertifikanın özel anahtarına erişimi etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="3bc2d-163">Enabling Access to the Certificate's Private Key</span></span>
 <span data-ttu-id="3bc2d-164">IIS tarafından barındırılan hizmetten sertifika özel anahtarına erişimi etkinleştirmek için, IIS tarafından barındırılan işlemin çalıştığı kullanıcı hesabına özel anahtar için uygun izinler verilmelidir.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-164">To enable access to the certificate private key from the IIS-hosted service, the user account under which the IIS-hosted process is running must be granted appropriate permissions for the private key.</span></span> <span data-ttu-id="3bc2d-165">Bu, Setup.bat betikteki son adımlar tarafından gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-165">This is accomplished by last steps in the Setup.bat script.</span></span>

```console
echo ************
echo setting privileges on server certificates
echo ************
for /F "delims=" %%i in ('"%ProgramFiles%\ServiceModelSampleTools\FindPrivateKey.exe" My LocalMachine -n CN^=%SERVER_NAME% -a') do set PRIVATE_KEY_FILE=%%i
set WP_ACCOUNT=NT AUTHORITY\NETWORK SERVICE
(ver | findstr /C:"5.1") && set WP_ACCOUNT=%COMPUTERNAME%\ASPNET
echo Y|cacls.exe "%PRIVATE_KEY_FILE%" /E /G "%WP_ACCOUNT%":R
iisreset
```

##### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3bc2d-166">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="3bc2d-166">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="3bc2d-167">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-167">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="3bc2d-168">Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-168">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="3bc2d-169">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için aşağıdaki yönergeleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-169">To run the sample in a single- or cross-machine configuration, use the following instructions.</span></span>

##### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="3bc2d-170">Örneği aynı makinede çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="3bc2d-170">To run the sample on the same machine</span></span>

1. <span data-ttu-id="3bc2d-171">Visual Studio 2012 komut isteminde örnek install klasöründen Setup.bat çalıştırın yönetici ayrıcalıklarıyla çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-171">Run Setup.bat from the sample install folder inside a Visual Studio 2012 command prompt run with administrator privileges.</span></span> <span data-ttu-id="3bc2d-172">Bu, örneği çalıştırmak için gereken tüm sertifikaları kurar.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-172">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="3bc2d-173">Setup.bat Batch dosyası bir Visual Studio 2012 komut Isteminden çalıştırılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-173">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="3bc2d-174">Visual Studio 2012 komut Isteminde ayarlanan PATH ortam değişkeni, Setup.bat betiği için gereken yürütülebilir dosyaları içeren dizine işaret eder.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-174">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span> <span data-ttu-id="3bc2d-175">Örnek ile işiniz bittiğinde Cleanup.bat çalıştırarak sertifikaları kaldırmayı unutmayın.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-175">Be sure to remove the certificates by running Cleanup.bat when finished with the sample.</span></span> <span data-ttu-id="3bc2d-176">Diğer güvenlik örnekleri aynı sertifikaları kullanır.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-176">Other security samples use the same certificates.</span></span>  
  
2. <span data-ttu-id="3bc2d-177">\Client\bin. 'den başlatma Client.exe</span><span class="sxs-lookup"><span data-stu-id="3bc2d-177">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="3bc2d-178">İstemci etkinliği istemci konsol uygulamasında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-178">Client activity is displayed on the client console application.</span></span>  
  
3. <span data-ttu-id="3bc2d-179">İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="3bc2d-179">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
##### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="3bc2d-180">Örneği makineler arasında çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="3bc2d-180">To run the sample across machines</span></span>  
  
1. <span data-ttu-id="3bc2d-181">Hizmet makinesinde bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-181">Create a directory on the service machine.</span></span> <span data-ttu-id="3bc2d-182">Internet Information Services (IIS) yönetim aracını kullanarak bu dizin için servicemodelsamples adlı bir sanal uygulama oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-182">Create a virtual application named servicemodelsamples for this directory using the Internet Information Services (IIS) management tool.</span></span>  
  
2. <span data-ttu-id="3bc2d-183">Hizmet programı dosyalarını \inetpub\wwwroot\servicemodelsamples adresinden hizmet makinesindeki sanal dizine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-183">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service machine.</span></span> <span data-ttu-id="3bc2d-184">Dosyaları \bin alt dizininde kopyalamadiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-184">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="3bc2d-185">Ayrıca, Setup.bat, Cleanup.bat ve ImportClientCert.bat dosyalarını da hizmet makinesine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-185">Also copy the Setup.bat, Cleanup.bat, and ImportClientCert.bat files to the service machine.</span></span>  
  
3. <span data-ttu-id="3bc2d-186">İstemci ikili dosyaları için istemci makinesinde bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-186">Create a directory on the client machine for the client binaries.</span></span>  
  
4. <span data-ttu-id="3bc2d-187">İstemci programı dosyalarını istemci makinesindeki istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-187">Copy the client program files to the client directory on the client machine.</span></span> <span data-ttu-id="3bc2d-188">Ayrıca Setup.bat, Cleanup.bat ve ImportServiceCert.bat dosyalarını istemciye kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-188">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5. <span data-ttu-id="3bc2d-189">Sunucusunda, `setup.bat service` yönetici ayrıcalıklarıyla açılan bir Visual Studio için geliştirici komut istemi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-189">On the server, run `setup.bat service` in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="3bc2d-190">`setup.bat` `service` Bağımsız değişkeniyle birlikte çalıştırmak makinenin tam etki alanı adına sahip bir hizmet sertifikası oluşturur ve hizmet sertifikasını Service. cer adlı bir dosyaya aktarır.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-190">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the machine and exports the service certificate to a file named Service.cer.</span></span>  
  
6. <span data-ttu-id="3bc2d-191">Web.config, `findValue` [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) makinenin tam etki alanı adıyla aynı olan yeni sertifika adını (içindeki özniteliğinde) yansıtacak şekilde düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-191">Edit Web.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully-qualified domain name of the machine.</span></span>  
  
7. <span data-ttu-id="3bc2d-192">Service. cer dosyasını hizmet dizininden istemci makinesindeki istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-192">Copy the Service.cer file from the service directory to the client directory on the client machine.</span></span>  
  
8. <span data-ttu-id="3bc2d-193">İstemcisinde, `setup.bat client` yönetici ayrıcalıklarıyla açılan bir Visual Studio için geliştirici komut istemi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-193">On the client, run `setup.bat client` in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="3bc2d-194">`setup.bat`Bağımsız değişkeniyle birlikte çalıştırmak, `client` Client.com adlı bir istemci sertifikası oluşturur ve Istemci sertifikasını Client. cer adlı bir dosyaya aktarır.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-194">Running `setup.bat` with the `client` argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
9. <span data-ttu-id="3bc2d-195">İstemci makinesindeki Client.exe.config dosyasında, bitiş noktasının adres değerini hizmetinizin yeni adresiyle eşleşecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-195">In the Client.exe.config file on the client machine, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="3bc2d-196">Localhost 'u sunucunun tam etki alanı adıyla değiştirerek bunu yapın.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-196">Do this by replacing localhost with the fully-qualified domain name of the server.</span></span>  
  
10. <span data-ttu-id="3bc2d-197">Client. cer dosyasını istemci dizininden sunucusundaki hizmet dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-197">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
11. <span data-ttu-id="3bc2d-198">İstemcisinde ImportServiceCert.bat ' yi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-198">On the client, run ImportServiceCert.bat.</span></span> <span data-ttu-id="3bc2d-199">Bu, hizmet sertifikasını Service. cer dosyasından CurrentUser-Trustedkişiler deposuna aktarır.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-199">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="3bc2d-200">Sunucusunda ImportClientCert.bat çalıştırın, bu, istemci sertifikasını Client. cer dosyasından LocalMachine-Trustedkişiler deposuna aktarır.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-200">On the server, run ImportClientCert.bat, This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
13. <span data-ttu-id="3bc2d-201">İstemci makinesinde, bir komut istemi penceresinden Client.exe başlatın.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-201">On the client machine, launch Client.exe from a command prompt window.</span></span> <span data-ttu-id="3bc2d-202">İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="3bc2d-202">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
##### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="3bc2d-203">Örnekten sonra temizlemek için</span><span class="sxs-lookup"><span data-stu-id="3bc2d-203">To clean up after the sample</span></span>  
  
- <span data-ttu-id="3bc2d-204">Örneği çalıştırmayı bitirdikten sonra Samples klasöründe Cleanup.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-204">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3bc2d-205">Bu betik, makineler arasında bu örneği çalıştırırken bir istemcideki hizmet sertifikalarını kaldırmaz.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-205">This script does not remove service certificates on a client when running this sample across machines.</span></span> <span data-ttu-id="3bc2d-206">Makinelerde sertifika kullanan WCF örnekleri çalıştırırsanız, CurrentUser-Trustedkişiler deposuna yüklenmiş olan hizmet sertifikalarını temizlediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="3bc2d-206">If you have run WCF samples that use certificates across machines, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="3bc2d-207">Bunu yapmak için şu komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com` .</span><span class="sxs-lookup"><span data-stu-id="3bc2d-207">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>
