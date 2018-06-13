---
title: Destek Belirteçleri
ms.date: 03/30/2017
ms.assetid: 65a8905d-92cc-4ab0-b6ed-1f710e40784e
ms.openlocfilehash: 8d8ff3cf4d5a060d135cbcf40c043681ce72b6e0
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33808802"
---
# <a name="supporting-tokens"></a><span data-ttu-id="3e2eb-102">Destek Belirteçleri</span><span class="sxs-lookup"><span data-stu-id="3e2eb-102">Supporting Tokens</span></span>
<span data-ttu-id="3e2eb-103">Destek belirteçleri örnek WS güvenliği kullanan bir ileti için ek belirteçler ekleneceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-103">The Supporting Tokens sample demonstrates how to add additional tokens to a message that uses WS-Security.</span></span> <span data-ttu-id="3e2eb-104">Örnek, bir kullanıcı adı güvenlik belirteci yanı sıra bir X.509 ikili güvenlik belirteci ekler.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-104">The example adds an X.509 binary security token in addition to a username security token.</span></span> <span data-ttu-id="3e2eb-105">Belirtecin bir WS-güvenlik ileti üstbilgisinde istemciden hizmete geçirilir ve iletisinin bir parçası alıcısı X.509 sertifikası elinde kanıtlamak için X.509 güvenlik belirteci ile ilişkili özel anahtara sahip imzalanır.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-105">The token is passed in a WS-Security message header from the client to the service and part of the message is signed with the private key associated with the X.509 security token to prove the possession of the X.509 certificate to the receiver.</span></span> <span data-ttu-id="3e2eb-106">Kimlik doğrulaması veya gönderen yetkilendirmek için bir ileti ile ilişkili birden fazla talep olan bir gereksinimi olduğunda bu durumda yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-106">This is useful in the case when there is a requirement to have multiple claims associated with a message to authenticate or authorize the sender.</span></span> <span data-ttu-id="3e2eb-107">Hizmet bir istek-yanıt iletişim deseni tanımlayan bir sözleşme uygular.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-107">The service implements a contract that defines a request-reply communication pattern.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="3e2eb-108">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="3e2eb-108">Demonstrates</span></span>  
 <span data-ttu-id="3e2eb-109">Örnek gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="3e2eb-109">The sample demonstrates:</span></span>  
  
-   <span data-ttu-id="3e2eb-110">Nasıl bir istemci bir hizmete ek güvenlik belirteçleri geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-110">How a client can pass additional security tokens to a service.</span></span>  
  
-   <span data-ttu-id="3e2eb-111">Nasıl sunucu ek güvenlik belirteçleri ile ilişkili talep erişebilir.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-111">How the server can access claims associated with additional security tokens.</span></span>  
  
-   <span data-ttu-id="3e2eb-112">Nasıl sunucu X.509 sertifikasının ileti şifreleme ve imza için kullanılan simetrik anahtarı korumak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-112">How the server's X.509 certificate is used to protect the symmetric key used for message encryption and signature.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3e2eb-113">Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-113">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="client-authenticates-with-username-token-and-supporting-x509-security-token"></a><span data-ttu-id="3e2eb-114">Kullanıcı adı belirteci ve X.509 güvenlik belirteci destekleyen istemci kimliğini doğrular</span><span class="sxs-lookup"><span data-stu-id="3e2eb-114">Client Authenticates with Username Token and Supporting X.509 Security Token</span></span>  
 <span data-ttu-id="3e2eb-115">Hizmet program aracılığıyla kullanarak oluşturduğunuz iletişim için bir tek uç noktasını kullanıma sunar `BindingHelper` ve `EchoServiceHost` sınıfları.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-115">The service exposes a single endpoint for communicating that is programmatically created using the `BindingHelper` and `EchoServiceHost` classes.</span></span> <span data-ttu-id="3e2eb-116">Uç nokta bir adresi, bağlama ve bir sözleşme oluşur.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-116">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="3e2eb-117">Özel bağlama kullanma bağlama yapılandırılmış `SymmetricSecurityBindingElement` ve `HttpTransportBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-117">The binding is configured with a custom binding using `SymmetricSecurityBindingElement` and `HttpTransportBindingElement`.</span></span> <span data-ttu-id="3e2eb-118">Bu örnek ayarlar `SymmetricSecurityBindingElement` iletim sırasında simetrik anahtar korumak ve geçirmek için bir hizmet X.509 sertifikası kullanmak üzere bir `UserNameToken` destekleyici birlikte `X509SecurityToken` WS-güvenlik ileti üstbilgisinde.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-118">This sample sets the `SymmetricSecurityBindingElement` to use a service X.509 certificate to protect the symmetric key during transmission and to pass a `UserNameToken` along with the supporting `X509SecurityToken` in a WS-Security message header.</span></span> <span data-ttu-id="3e2eb-119">Simetrik anahtar, ileti gövdesinin ve kullanıcı adı güvenlik belirteci şifrelemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-119">The symmetric key is used to encrypt the message body and the username security token.</span></span> <span data-ttu-id="3e2eb-120">WS güvenliği ileti üstbilgisinde bir ek ikili güvenlik belirteci olarak destekleme belirteci geçirildi.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-120">The supporting token is passed as an additional binary security token in the WS-Security message header.</span></span> <span data-ttu-id="3e2eb-121">Destekleme belirteci özgünlüğünü destekleyen X.509 güvenlikle ilişkili özel anahtara sahip ileti parçası imzalayarak belirteci sağlanır.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-121">The authenticity of the supporting token is proved by signing part of the message with the private key associated with the supporting X.509 security token.</span></span>  
  
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
  
 <span data-ttu-id="3e2eb-122">Davranış istemci kimlik doğrulaması ve ayrıca hizmet X.509 sertifikası hakkında bilgi için kullanılacak olan hizmet kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-122">The behavior specifies the service credentials that are to be used for client authentication and also information about the service X.509 certificate.</span></span> <span data-ttu-id="3e2eb-123">Örnek kullanır `CN=localhost` hizmet X.509 sertifikası bir konu adı olarak.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-123">The sample uses `CN=localhost` as a subject name in the service X.509 certificate.</span></span>  
  
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
  
 <span data-ttu-id="3e2eb-124">Hizmet kodu:</span><span class="sxs-lookup"><span data-stu-id="3e2eb-124">Service code:</span></span>  
  
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
  
 <span data-ttu-id="3e2eb-125">İstemci uç noktası, hizmet uç noktası benzer şekilde yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-125">The client endpoint is configured in a similar way to the service endpoint.</span></span> <span data-ttu-id="3e2eb-126">İstemci aynı kullanır `BindingHelper` sınıfı bir bağlama oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-126">The client uses the same `BindingHelper` class to create a binding.</span></span> <span data-ttu-id="3e2eb-127">Kurulumu geri kalanı bulunan `Client` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-127">The rest of the setup is located in `Client` class.</span></span> <span data-ttu-id="3e2eb-128">İstemci, istemci uç nokta davranışları koleksiyonuna Kurulum kodu kullanıcı adı güvenlik belirteci, destekleme X.509 güvenlik belirteci ve hizmet X.509 sertifikası hakkında bilgi hakkında bilgi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-128">The client sets information about the user name security token, the supporting X.509 security token and information about the service X.509 certificate in the setup code to the client endpoint behaviors collection.</span></span>  
  
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
  
## <a name="displaying-callers-information"></a><span data-ttu-id="3e2eb-129">Arayanlar bilgileri görüntüleme</span><span class="sxs-lookup"><span data-stu-id="3e2eb-129">Displaying Callers' Information</span></span>  
 <span data-ttu-id="3e2eb-130">Arayanın bilgileri görüntülemek için kullanabileceğiniz `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-130">To display the caller's information, you can use the `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` as shown in the following code.</span></span> <span data-ttu-id="3e2eb-131">`ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` Geçerli arayanla ilişkili yetkilendirme talepleri içerir.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-131">The `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` contains authorization claims associated with the current caller.</span></span> <span data-ttu-id="3e2eb-132">Bu talep iletide alınan her belirteci için Windows Communication Foundation (WCF) tarafından otomatik olarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-132">Those claims are supplied automatically by Windows Communication Foundation (WCF) for every token received in the message.</span></span>  
  
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
  
## <a name="running-the-sample"></a><span data-ttu-id="3e2eb-133">Örnek çalışıyor</span><span class="sxs-lookup"><span data-stu-id="3e2eb-133">Running the Sample</span></span>  
 <span data-ttu-id="3e2eb-134">Örneği çalıştırdığınızda, istemci önce kullanıcı adı ve parola için kullanıcı adı belirteci girmenizi ister.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-134">When you run the sample, the client first prompts you to provide user name and password for the user name token.</span></span> <span data-ttu-id="3e2eb-135">WCF hizmetine sistem tarafından sağlanan kimlik içine kullanıcı adı belirteç sağlanan değerler eşlendiğinden, sistem hesabı için doğru değerleri sağladığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-135">Be sure to provide correct values for your system account, because WCF on the service maps the values supplied in the user name token into the identity provided by the system.</span></span> <span data-ttu-id="3e2eb-136">Bundan sonra istemci hizmetinden gelen yanıt görüntüler.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-136">After that, the client displays the response from the service.</span></span> <span data-ttu-id="3e2eb-137">İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-137">Press ENTER in the client window to shut down the client.</span></span>  
  
## <a name="setup-batch-file"></a><span data-ttu-id="3e2eb-138">Toplu iş dosyası Kurulumu</span><span class="sxs-lookup"><span data-stu-id="3e2eb-138">Setup Batch File</span></span>  
 <span data-ttu-id="3e2eb-139">Bu örnekle dahil Setup.bat toplu iş dosyası, sunucu sertifika tabanlı güvenlik gerektiren Internet Information Services (IIS) barındırılan uygulamayı çalıştırmayı ilgili sertifikalarla sunucu yapılandırmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-139">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run Internet Information Services (IIS) hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="3e2eb-140">Bu toplu iş dosyası makinelerde çalışması için ya da barındırılan olmayan bir durumda çalışması için değiştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-140">This batch file must be modified to work across machines or to work in a non-hosted case.</span></span>  
  
 <span data-ttu-id="3e2eb-141">Aşağıdakiler, böylece uygun yapılandırmada çalışacak biçimde değiştirilebilir toplu iş dosyaları farklı bölümlerini kısa bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-141">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in appropriate configuration.</span></span>  
  
### <a name="creating-the-client-certificate"></a><span data-ttu-id="3e2eb-142">İstemci sertifikası oluşturma</span><span class="sxs-lookup"><span data-stu-id="3e2eb-142">Creating the Client Certificate</span></span>  
 <span data-ttu-id="3e2eb-143">Aşağıdaki satırları Setup.bat toplu iş dosyasından kullanılacak istemci sertifikası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-143">The following lines from the Setup.bat batch file create the client certificate to be used.</span></span> <span data-ttu-id="3e2eb-144">`%CLIENT_NAME%` Değişkeni, istemci sertifikası konu belirtir.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-144">The `%CLIENT_NAME%` variable specifies the subject of the client certificate.</span></span> <span data-ttu-id="3e2eb-145">Bu örnek konu adı olarak "client.com" kullanır.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-145">This sample uses "client.com" as the subject name.</span></span>  
  
 <span data-ttu-id="3e2eb-146">Sertifika altında (Kişisel) My deposunda saklanır `CurrentUser` depolama konumu.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-146">The certificate is stored in My (Personal) store under the `CurrentUser` store location.</span></span>  
  
```  
echo ************  
echo making client cert  
echo ************  
makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe  
```  
  
### <a name="installing-the-client-certificate-into-the-servers-trusted-store"></a><span data-ttu-id="3e2eb-147">Sunucu güvenilen deposuna istemci sertifikası yükleme</span><span class="sxs-lookup"><span data-stu-id="3e2eb-147">Installing the Client Certificate into the Server's Trusted Store</span></span>  
 <span data-ttu-id="3e2eb-148">Setup.bat toplu iş dosyasında aşağıdaki satırı istemci sertifikasını sunucusunun güvenilir Kişiler deposuna kopyalar.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-148">The following line in the Setup.bat batch file copies the client certificate into the server’s trusted people store.</span></span> <span data-ttu-id="3e2eb-149">MakeCert.exe tarafından oluşturulan sertifikaları örtük olarak sunucunun sistemi tarafından güvenilir değil çünkü bu adım gereklidir.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-149">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the server’s system.</span></span> <span data-ttu-id="3e2eb-150">Bir istemci güvenilen kök sertifikasını kökü belirtilmiş bir sertifikanız zaten varsa — örneğin, bir Microsoft verilen sertifika — sunucu sertifikasına sahip istemci sertifika deposunun doldurulması, bu adım gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-150">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
```  
echo ************  
echo copying client cert to server's CurrentUserstore  
echo ************  
certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople  
```  
  
### <a name="creating-the-server-certificate"></a><span data-ttu-id="3e2eb-151">Sunucu sertifikası oluşturma</span><span class="sxs-lookup"><span data-stu-id="3e2eb-151">Creating the Server Certificate</span></span>  
 <span data-ttu-id="3e2eb-152">Aşağıdaki satırları Setup.bat toplu iş dosyasından kullanılacak sunucu sertifikası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-152">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="3e2eb-153">`%SERVER_NAME%` Değişkeni, sunucu adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-153">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="3e2eb-154">Kendi sunucu adını belirtmek için bu değişkeni değiştirin.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-154">Change this variable to specify your own server name.</span></span> <span data-ttu-id="3e2eb-155">Bu toplu iş dosyasındaki localhost varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-155">The default in this batch file is localhost.</span></span>  
  
 <span data-ttu-id="3e2eb-156">Sertifika, LocalMachine depolama konumu altında (Kişisel) My deposunda saklanır.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-156">The certificate is stored in My (Personal) store under the LocalMachine store location.</span></span> <span data-ttu-id="3e2eb-157">Sertifika saklanır IIS tarafından barındırılan hizmetler için LocalMachine deposundaki.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-157">The certificate is stored in the LocalMachine store for the IIS-hosted services.</span></span> <span data-ttu-id="3e2eb-158">Kendini barındıran hizmetler için LocalMachine dize Currentuser'a ile değiştirerek Currentuser'a depolama konumu sunucu sertifikasının depolamak için toplu iş dosyasını değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-158">For self-hosted services, you should modify the batch file to store the server certificate in the CurrentUser store location by replacing the string LocalMachine with CurrentUser.</span></span>  
  
```  
echo ************  
echo Server cert setup starting  
echo %SERVER_NAME%  
echo ************  
echo making server cert  
echo ************  
makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
```  
  
### <a name="installing-server-certificate-into-clients-trusted-certificate-store"></a><span data-ttu-id="3e2eb-159">İstemcinin güvenilen sertifika deposuna sunucu sertifikası yükleme</span><span class="sxs-lookup"><span data-stu-id="3e2eb-159">Installing Server Certificate into Client's Trusted Certificate Store</span></span>  
 <span data-ttu-id="3e2eb-160">İstemci güvenilir kişiler içine Setup.bat toplu dosya kopyalama sunucu sertifikasının aşağıdaki satırları depolar.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-160">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="3e2eb-161">MakeCert.exe tarafından oluşturulan sertifikaları örtük olarak istemci sistemi tarafından güvenilir değil çünkü bu adım gereklidir.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-161">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="3e2eb-162">Bir istemci güvenilen kök sertifikasını kökü belirtilmiş bir sertifikanız zaten varsa — örneğin, bir Microsoft verilen sertifika — sunucu sertifikasına sahip istemci sertifika deposunun doldurulması, bu adım gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-162">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
```  
echo ************  
echo copying server cert to client's TrustedPeople store  
echo ************certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
```  
  
### <a name="enabling-access-to-the-certificates-private-key"></a><span data-ttu-id="3e2eb-163">Sertifikanın özel anahtar erişimi etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="3e2eb-163">Enabling Access to the Certificate's Private Key</span></span>  
 <span data-ttu-id="3e2eb-164">IIS barındırılan hizmeti sertifika özel anahtarına erişimi etkinleştirmek için IIS tarafından barındırılan işlemin altında çalıştığı hesabın özel anahtar için uygun izinleri verilmelidir.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-164">To enable access to the certificate private key from the IIS-hosted service, the user account under which the IIS-hosted process is running must be granted appropriate permissions for the private key.</span></span> <span data-ttu-id="3e2eb-165">Bu son adımda Setup.bat komut dosyası tarafından gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-165">This is accomplished by last steps in the Setup.bat script.</span></span>  
  
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
  
##### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3e2eb-166">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="3e2eb-166">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="3e2eb-167">Gerçekleştirilen mutlaka [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3e2eb-167">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="3e2eb-168">Çözümü derlemek için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3e2eb-168">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="3e2eb-169">Tek veya çapraz makine yapılandırmada örneği çalıştırmak için aşağıdaki yönergeleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-169">To run the sample in a single- or cross-machine configuration, use the following instructions.</span></span>  
  
##### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="3e2eb-170">Aynı makinede örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="3e2eb-170">To run the sample on the same machine</span></span>  
  
1.  <span data-ttu-id="3e2eb-171">İçinde örnek yükleme klasöründen Setup.bat çalıştırmak bir [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemini yönetici ayrıcalıklarıyla çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-171">Run Setup.bat from the sample install folder inside a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] command prompt run with administrator privileges.</span></span> <span data-ttu-id="3e2eb-172">Bu örneği çalıştırmak için gerekli tüm sertifikalar yükler.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-172">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3e2eb-173">Setup.bat toplu iş dosyası çalıştırılmak üzere tasarlanmış bir [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemi.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-173">The Setup.bat batch file is designed to be run from a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt.</span></span> <span data-ttu-id="3e2eb-174">İçinde PATH ortam değişkeni ayarlamak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemi Setup.bat komut dosyası için gereken yürütülebilir dosyalar içeren dizine işaret eder.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-174">The PATH environment variable set within the [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span> <span data-ttu-id="3e2eb-175">Örnekle bittiğinde Cleanup.bat çalıştırarak sertifikaları kaldırdığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-175">Be sure to remove the certificates by running Cleanup.bat when finished with the sample.</span></span> <span data-ttu-id="3e2eb-176">Diğer güvenlik örnekleri aynı sertifikaları kullanır.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-176">Other security samples use the same certificates.</span></span>  
  
2.  <span data-ttu-id="3e2eb-177">Client.exe \client\bin başlatın.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-177">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="3e2eb-178">İstemci etkinliği istemci konsol uygulaması görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-178">Client activity is displayed on the client console application.</span></span>  
  
3.  <span data-ttu-id="3e2eb-179">İstemci ve hizmet iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="3e2eb-179">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
##### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="3e2eb-180">Makine genelinde örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="3e2eb-180">To run the sample across machines</span></span>  
  
1.  <span data-ttu-id="3e2eb-181">Bir dizin hizmeti makinede oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-181">Create a directory on the service machine.</span></span> <span data-ttu-id="3e2eb-182">Internet Information Services (IIS) yönetim aracını kullanarak bu dizin için servicemodelsamples adlı bir sanal uygulama oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-182">Create a virtual application named servicemodelsamples for this directory using the Internet Information Services (IIS) management tool.</span></span>  
  
2.  <span data-ttu-id="3e2eb-183">Hizmet program dosyalarını \inetpub\wwwroot\servicemodelsamples hizmeti makinede sanal dizine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-183">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service machine.</span></span> <span data-ttu-id="3e2eb-184">\Bin alt dizinindeki dosyaları kopyalayın emin olun.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-184">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="3e2eb-185">Ayrıca hizmet makineye Setup.bat, Cleanup.bat ve ImportClientCert.bat dosyalarını kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-185">Also copy the Setup.bat, Cleanup.bat, and ImportClientCert.bat files to the service machine.</span></span>  
  
3.  <span data-ttu-id="3e2eb-186">İstemci ikili dosyalarının için istemci makinede bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-186">Create a directory on the client machine for the client binaries.</span></span>  
  
4.  <span data-ttu-id="3e2eb-187">İstemci makinesinde istemci dizinine istemci program dosyaları kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-187">Copy the client program files to the client directory on the client machine.</span></span> <span data-ttu-id="3e2eb-188">Ayrıca istemciye Setup.bat, Cleanup.bat ve ImportServiceCert.bat dosyalarını kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-188">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5.  <span data-ttu-id="3e2eb-189">Sunucu üzerinde çalışan `setup.bat service` yönetici ayrıcalıklarına sahip bir Visual Studio Komut İstemi'nde açılır.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-189">On the server, run `setup.bat service` in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="3e2eb-190">Çalışan `setup.bat` ile `service` bağımsız değişkeni makinenin tam etki alanı adı ile bir hizmet sertifikası oluşturur ve hizmet sertifikası Service.cer adlı bir dosyaya aktarır.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-190">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the machine and exports the service certificate to a file named Service.cer.</span></span>  
  
6.  <span data-ttu-id="3e2eb-191">Web.config dosyasını yeni sertifika yansıtacak şekilde düzenleyin (içinde `findValue` özniteliğini [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) makinenin tam etki alanı adı ile aynı olduğu.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-191">Edit Web.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully-qualified domain name of the machine.</span></span>  
  
7.  <span data-ttu-id="3e2eb-192">Service.cer dosya hizmeti dizininden istemci makinesinde istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-192">Copy the Service.cer file from the service directory to the client directory on the client machine.</span></span>  
  
8.  <span data-ttu-id="3e2eb-193">İstemci üzerinde çalışan `setup.bat client` yönetici ayrıcalıklarına sahip bir Visual Studio Komut İstemi'nde açılır.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-193">On the client, run `setup.bat client` in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="3e2eb-194">Çalışan `setup.bat` ile `client` bağımsız değişkeni client.com adlı bir istemci sertifikası oluşturur ve istemci sertifikasını Client.cer adlı bir dosyaya aktarır.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-194">Running `setup.bat` with the `client` argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
9. <span data-ttu-id="3e2eb-195">İstemci makinesinde Client.exe.config dosyasında yeni adresi hizmetinizin eşleştirmek için uç nokta adresi değerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-195">In the Client.exe.config file on the client machine, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="3e2eb-196">Sunucunun tam etki alanı adı ile localhost değiştirerek bunu.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-196">Do this by replacing localhost with the fully-qualified domain name of the server.</span></span>  
  
10. <span data-ttu-id="3e2eb-197">Client.cer dosyasını istemci dizininden sunucusunda hizmet dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-197">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
11. <span data-ttu-id="3e2eb-198">İstemcide ImportServiceCert.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-198">On the client, run ImportServiceCert.bat.</span></span> <span data-ttu-id="3e2eb-199">Bu hizmet sertifikası Service.cer dosyadan Currentuser'a - TrustedPeople deposunu alır.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-199">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="3e2eb-200">ImportClientCert.bat, çalıştıran sunucuda, bu istemci sertifikasını Client.cer dosyadan LocalMachine - TrustedPeople deposunu alır.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-200">On the server, run ImportClientCert.bat, This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
13. <span data-ttu-id="3e2eb-201">İstemci makinesinde, bir komut istemi penceresinden Client.exe başlatın.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-201">On the client machine, launch Client.exe from a command prompt window.</span></span> <span data-ttu-id="3e2eb-202">İstemci ve hizmet iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="3e2eb-202">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
##### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="3e2eb-203">Örnek sonra temizlemek için</span><span class="sxs-lookup"><span data-stu-id="3e2eb-203">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="3e2eb-204">Örnek çalıştıran tamamladıktan sonra Cleanup.bat samples klasöründen çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-204">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3e2eb-205">Bu komut dosyası, bu örnek makine genelinde çalıştırırken bir istemcide hizmet sertifikaları kaldırmaz.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-205">This script does not remove service certificates on a client when running this sample across machines.</span></span> <span data-ttu-id="3e2eb-206">Makine genelinde sertifikaları kullanan WCF örnekleri çalıştırırsanız, Currentuser'a - TrustedPeople deposu yüklü hizmet sertifikalarını temizlemek emin olun.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-206">If you have run WCF samples that use certificates across machines, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="3e2eb-207">Bunu yapmak için aşağıdaki komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-207">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e2eb-208">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3e2eb-208">See Also</span></span>
