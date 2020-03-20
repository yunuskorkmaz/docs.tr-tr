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
# <a name="trusted-facade-service"></a><span data-ttu-id="03d53-102">Güvenilir Görünüm Hizmeti</span><span class="sxs-lookup"><span data-stu-id="03d53-102">Trusted Facade Service</span></span>
<span data-ttu-id="03d53-103">Bu senaryo örneği, Windows Communication Foundation (WCF) güvenlik altyapısını kullanarak arayanın kimlik bilgilerinin bir hizmetten diğerine nasıl aklanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="03d53-103">This scenario sample demonstrates how to flow caller's identity information from one service to another using Windows Communication Foundation (WCF) security infrastructure.</span></span>  
  
 <span data-ttu-id="03d53-104">Bir hizmet tarafından sağlanan işlevselliği bir cephe hizmeti kullanarak ortak ağa ifa etmek için yaygın bir tasarım desenidir.</span><span class="sxs-lookup"><span data-stu-id="03d53-104">It is a common design pattern to expose the functionality provided by a service to the public network using a façade service.</span></span> <span data-ttu-id="03d53-105">Cephe hizmeti genellikle çevre ağında (DMZ, askerden arındırılmış bölge ve ekranlı alt ağ olarak da bilinir) bulunur ve iş mantığını uygulayan ve dahili verilere erişimi olan bir arka uç hizmetiyle iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="03d53-105">The façade service typically resides in the perimeter network (also known as DMZ, demilitarized zone, and screened subnet) and communicates with a backend service that implements the business logic and has access to internal data.</span></span> <span data-ttu-id="03d53-106">Cephe hizmeti ile arka uç hizmeti arasındaki iletişim kanalı bir güvenlik duvarından geçer ve genellikle yalnızca tek bir amaç için sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="03d53-106">The communication channel between the façade service and the backend service goes through a firewall and is usually limited for a single purpose only.</span></span>  
  
 <span data-ttu-id="03d53-107">Bu örnek aşağıdaki bileşenlerden oluşur:</span><span class="sxs-lookup"><span data-stu-id="03d53-107">This sample consists of the following components:</span></span>  
  
- <span data-ttu-id="03d53-108">Hesap makinesi istemcisi</span><span class="sxs-lookup"><span data-stu-id="03d53-108">Calculator client</span></span>  
  
- <span data-ttu-id="03d53-109">Hesap makinesi cephe hizmeti</span><span class="sxs-lookup"><span data-stu-id="03d53-109">Calculator façade service</span></span>  
  
- <span data-ttu-id="03d53-110">Hesap makinesi arka uç hizmeti</span><span class="sxs-lookup"><span data-stu-id="03d53-110">Calculator backend service</span></span>  
  
 <span data-ttu-id="03d53-111">Cephe hizmeti, isteği doğrulamaktan ve arayan kişinin kimliğini doğrulamaktan sorumludur.</span><span class="sxs-lookup"><span data-stu-id="03d53-111">The façade service is responsible for validating the request and authenticating the caller.</span></span> <span data-ttu-id="03d53-112">Başarılı kimlik doğrulama ve doğrulamadan sonra, çevre ağından dahili ağa kontrollü iletişim kanalını kullanarak isteği arka uç hizmetine iletir.</span><span class="sxs-lookup"><span data-stu-id="03d53-112">After successful authentication and validation, it forwards the request to the backend service using the controlled communication channel from the perimeter network to the internal network.</span></span> <span data-ttu-id="03d53-113">İlerleyen isteğin bir parçası olarak, ön cephe hizmeti, arka uç hizmetinin bu bilgileri işlenmesinde kullanabilmesi için arayanın kimliği yle ilgili bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="03d53-113">As a part of the forwarded request, the façade service includes information about the caller's identity so that the backend service can use this information in its processing.</span></span> <span data-ttu-id="03d53-114">Arayanın kimliği ileti `Username` `Security` üstbilgisinin içindeki güvenlik belirteci kullanılarak iletilir.</span><span class="sxs-lookup"><span data-stu-id="03d53-114">The caller's identity is transmitted using a `Username` security token inside the message `Security` header.</span></span> <span data-ttu-id="03d53-115">Örnek, bu bilgileri üstbilgiden iletmek ve ayıklamak için WCF güvenlik altyapısını `Security` kullanır.</span><span class="sxs-lookup"><span data-stu-id="03d53-115">The sample uses the WCF security infrastructure to transmit and extract this information from the `Security` header.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="03d53-116">Arka uç hizmeti, arayanın kimliğini doğrulamak için ön cephe hizmetine güvenir.</span><span class="sxs-lookup"><span data-stu-id="03d53-116">The backend service trusts the façade service to authenticate the caller.</span></span> <span data-ttu-id="03d53-117">Bu nedenle, arka uç hizmeti arayana yeniden doğrulamıyor; iletme talebinde cephe hizmeti tarafından sağlanan kimlik bilgilerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="03d53-117">Because of this, the backend service does not authenticate the caller again; it uses the identity information provided by the façade service in the forwarded request.</span></span> <span data-ttu-id="03d53-118">Bu güven ilişkisi nedeniyle, iletilen iletinin güvenilir bir kaynaktan geldiğinden emin olmak için arka uç hizmetinin cephe hizmetini doğrulaması gerekir - bu durumda, cephe hizmeti.</span><span class="sxs-lookup"><span data-stu-id="03d53-118">Because of this trust relationship, the backend service must authenticate the façade service to ensure that the forwarded message comes from a trusted source - in this case, the façade service.</span></span>  
  
## <a name="implementation"></a><span data-ttu-id="03d53-119">Uygulama</span><span class="sxs-lookup"><span data-stu-id="03d53-119">Implementation</span></span>  
 <span data-ttu-id="03d53-120">Bu örnekte iki iletişim yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="03d53-120">There are two communication paths in this sample.</span></span> <span data-ttu-id="03d53-121">Birincisi müşteri ile cephe hizmeti arasında, ikincisi cephe hizmeti ile arka uç servisi arasındadır.</span><span class="sxs-lookup"><span data-stu-id="03d53-121">First is between the client and the façade service, the second is between the façade service and the backend service.</span></span>  
  
### <a name="communication-path-between-client-and-faade-service"></a><span data-ttu-id="03d53-122">Müşteri ve Cephe Hizmeti Arasındaki İletişim Yolu</span><span class="sxs-lookup"><span data-stu-id="03d53-122">Communication Path between Client and Façade Service</span></span>  
 <span data-ttu-id="03d53-123">Cephe hizmet iletişim yoluna istemci `wsHttpBinding` `UserName` bir istemci kimlik tipi ile kullanır.</span><span class="sxs-lookup"><span data-stu-id="03d53-123">The client to the façade service communication path uses `wsHttpBinding` with a `UserName` client credential type.</span></span> <span data-ttu-id="03d53-124">Bu, istemcinin cephe hizmetine kimlik doğrulamak için kullanıcı adı ve parola kullandığı ve cephe hizmetinin istemciye kimlik doğrulamak için X.509 sertifikası kullandığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="03d53-124">This means that the client uses username and password to authenticate to the façade service and the façade service uses X.509 certificate to authenticate to the client.</span></span> <span data-ttu-id="03d53-125">Bağlama yapılandırması aşağıdaki örnek gibi görünür.</span><span class="sxs-lookup"><span data-stu-id="03d53-125">The binding configuration looks like the following example.</span></span>  
  
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
  
 <span data-ttu-id="03d53-126">Cephe hizmeti, özel `UserNamePasswordValidator` uygulama kullanarak arayanın kimliğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="03d53-126">The façade service authenticates the caller using custom `UserNamePasswordValidator` implementation.</span></span> <span data-ttu-id="03d53-127">Tanıtım amacıyla, kimlik doğrulaması yalnızca arayanın kullanıcı adının sunulan parolayla eşleşmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="03d53-127">For demonstration purposes, the authentication only ensures that the caller's username matches the presented password.</span></span> <span data-ttu-id="03d53-128">Gerçek dünyada, kullanıcı büyük olasılıkla Active Directory veya özel ASP.NET Üyelik sağlayıcısı kullanılarak doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="03d53-128">In the real world situation, the user is probably authenticated using Active Directory or custom ASP.NET Membership provider.</span></span> <span data-ttu-id="03d53-129">Doğrulayıcı uygulaması dosyada `FacadeService.cs` bulunur.</span><span class="sxs-lookup"><span data-stu-id="03d53-129">The validator implementation resides in `FacadeService.cs` file.</span></span>  
  
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
  
 <span data-ttu-id="03d53-130">Özel doğrulayıcı, cephe hizmeti yapılandırma dosyasındaki `serviceCredentials` davranış içinde kullanılacak şekilde yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="03d53-130">The custom validator is configured to be used inside the `serviceCredentials` behavior in the façade service configuration file.</span></span> <span data-ttu-id="03d53-131">Bu davranış, hizmetin X.509 sertifikasını yapılandırmak için de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="03d53-131">This behavior is also used to configure the service's X.509 certificate.</span></span>  
  
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
  
### <a name="communication-path-between-faade-service-and-backend-service"></a><span data-ttu-id="03d53-132">Cephe Hizmeti ile Arka Uç Servisi Arasındaki İletişim Yolu</span><span class="sxs-lookup"><span data-stu-id="03d53-132">Communication Path between Façade Service and Backend Service</span></span>  
 <span data-ttu-id="03d53-133">Arka uç hizmet iletişim yoluna cephe `customBinding` hizmeti birkaç bağlama öğeleri oluşan bir kullanır.</span><span class="sxs-lookup"><span data-stu-id="03d53-133">The façade service to the backend service communication path uses a `customBinding` that consists of several binding elements.</span></span> <span data-ttu-id="03d53-134">Bu bağlama iki şeyi başarır.</span><span class="sxs-lookup"><span data-stu-id="03d53-134">This binding accomplishes two things.</span></span> <span data-ttu-id="03d53-135">İletişimin güvenli olduğundan ve güvenilir bir kaynaktan geldiğinden emin olmak için cephe hizmetini ve arka uç hizmetini doğrular.</span><span class="sxs-lookup"><span data-stu-id="03d53-135">It authenticates the façade service and backend service to ensure that the communication is secure and is coming from a trusted source.</span></span> <span data-ttu-id="03d53-136">Ayrıca, güvenlik belirteci içinde `Username` ilk arayanın kimliğini de iletir.</span><span class="sxs-lookup"><span data-stu-id="03d53-136">Additionally, it also transmits the initial caller's identity inside the `Username` security token.</span></span> <span data-ttu-id="03d53-137">Bu durumda, yalnızca ilk arayanın kullanıcı adı arka uç hizmetine aktarılır, parola iletiye dahil edilmez.</span><span class="sxs-lookup"><span data-stu-id="03d53-137">In this case, only the initial caller's username is transmitted to the backend service, the password is not included in the message.</span></span> <span data-ttu-id="03d53-138">Bunun nedeni, arka uç hizmetinin isteği ona iletmeden önce arayanın kimliğini doğrulamak için ön cephe hizmetine güvenmiş olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="03d53-138">This is because the backend service trusts the façade service to authenticate the caller before forwarding the request to it.</span></span> <span data-ttu-id="03d53-139">Cephe hizmeti kendisini arka uç hizmetine doğruladığı için, arka uç hizmeti iletilen istekte yer alan bilgilere güvenebilir.</span><span class="sxs-lookup"><span data-stu-id="03d53-139">Because the façade service authenticates itself to the backend service, the backend service can trust the information contained in the forwarded request.</span></span>  
  
 <span data-ttu-id="03d53-140">Aşağıda, bu iletişim yolu için bağlayıcı yapılandırma ve</span><span class="sxs-lookup"><span data-stu-id="03d53-140">The following is the binding configuration for this communication path.</span></span>  
  
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
  
 <span data-ttu-id="03d53-141">[ \<Güvenlik>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) bağlama öğesi, ilk arayanın kullanıcı adı iletimi ve ayıklama ilgilenir.</span><span class="sxs-lookup"><span data-stu-id="03d53-141">The [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) binding element takes care of the initial caller's username transmission and extraction.</span></span> <span data-ttu-id="03d53-142">WindowsStreamSecurity>ve [ \<tcpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) cephe ve arka uç hizmetlerini ve ileti korumasını doğrulayan bir şekilde ilgilenir. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/windowsstreamsecurity.md)</span><span class="sxs-lookup"><span data-stu-id="03d53-142">The [\<windowsStreamSecurity>](../../../../docs/framework/configure-apps/file-schema/wcf/windowsstreamsecurity.md) and [\<tcpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) take care of authenticating façade and backend services and message protection.</span></span>  
  
 <span data-ttu-id="03d53-143">İsteğin iletilmesi için, ön cephe hizmeti uygulamasının wcf güvenlik altyapısının bunu iletilen iletiye yerleştirebilmesi için ilk arayanın kullanıcı adını sağlaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="03d53-143">To forward the request, the façade service implementation must provide the initial caller's username so that WCF security infrastructure can place this into the forwarded message.</span></span> <span data-ttu-id="03d53-144">İlk arayanın kullanıcı adı, cephe hizmetinin arka uç `ClientCredentials` hizmetiyle iletişim kurmak için kullandığı istemci proxy örneğinde özellik te buna ayarlayarak cephe hizmeti uygulamasında sağlanır.</span><span class="sxs-lookup"><span data-stu-id="03d53-144">The initial caller's username is provided in the façade service implementation by setting it in the `ClientCredentials` property on the client proxy instance that façade service uses to communicate with the backend service.</span></span>  
  
 <span data-ttu-id="03d53-145">Aşağıdaki kod, `GetCallerIdentity` yöntemin cephe hizmetinde nasıl uygulandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="03d53-145">The following code shows how `GetCallerIdentity` method is implemented on the façade service.</span></span> <span data-ttu-id="03d53-146">Diğer yöntemler aynı deseni kullanır.</span><span class="sxs-lookup"><span data-stu-id="03d53-146">Other methods use the same pattern.</span></span>  
  
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
  
 <span data-ttu-id="03d53-147">Önceki kodda gösterildiği gibi, parola `ClientCredentials` özellik üzerinde ayarlanmaz, yalnızca kullanıcı adı ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="03d53-147">As shown in the previous code, the password is not set on the `ClientCredentials` property, only the username is set.</span></span> <span data-ttu-id="03d53-148">WCF güvenlik altyapısı, bu durumda parolası olmayan bir kullanıcı adı güvenlik belirteci oluşturur ve bu senaryoda tam olarak gereken budur.</span><span class="sxs-lookup"><span data-stu-id="03d53-148">WCF security infrastructure creates a username security token without a password in this case, which is exactly what is required in this scenario.</span></span>  
  
 <span data-ttu-id="03d53-149">Arka uç hizmetinde, kullanıcı adı güvenlik belirtecinde bulunan bilgilerin kimlik doğrulaması yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="03d53-149">On the backend service, the information contained in the username security token must be authenticated.</span></span> <span data-ttu-id="03d53-150">Varsayılan olarak, WCF güvenlik sağlanan parolayı kullanarak kullanıcıyı bir Windows hesabıyla eşlemeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="03d53-150">By default, WCF security attempts to map the user to a Windows account using the provided password.</span></span> <span data-ttu-id="03d53-151">Bu durumda, sağlanan bir parola yoktur ve kimlik doğrulama zaten cephe hizmeti tarafından gerçekleştirilmişolduğundan kullanıcı adının kimlik doğrulaması için arka uç hizmeti gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="03d53-151">In this case, there is no password provided and the backend service is not required to authenticate the username because the authentication was already performed by the façade service.</span></span> <span data-ttu-id="03d53-152">WCF'de bu işlevselliği `UserNamePasswordValidator` uygulamak için, yalnızca belirteçte bir kullanıcı adının belirtildiğini ve ek kimlik doğrulaması gerçekleştirmediğini belirten bir özel sağlanır.</span><span class="sxs-lookup"><span data-stu-id="03d53-152">To implement this functionality in WCF, a custom `UserNamePasswordValidator` is provided that only enforces that a username is specified in the token and does not perform any additional authentication.</span></span>  
  
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
  
 <span data-ttu-id="03d53-153">Özel doğrulayıcı, cephe hizmeti yapılandırma dosyasındaki `serviceCredentials` davranış içinde kullanılacak şekilde yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="03d53-153">The custom validator is configured to be used inside the `serviceCredentials` behavior in the façade service configuration file.</span></span>  
  
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
  
 <span data-ttu-id="03d53-154">Kullanıcı adı bilgi ve güvenilir cephe hizmet hesabı hakkında bilgi ayıklamak `ServiceSecurityContext` için, arka uç hizmeti uygulaması sınıfı kullanır.</span><span class="sxs-lookup"><span data-stu-id="03d53-154">To extract the username information and information about the trusted façade service account, the backend service implementation uses the `ServiceSecurityContext` class.</span></span> <span data-ttu-id="03d53-155">Aşağıdaki kod yöntemin `GetCallerIdentity` nasıl uygulandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="03d53-155">The following code shows how the `GetCallerIdentity` method is implemented.</span></span>  
  
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
  
 <span data-ttu-id="03d53-156">Cephe hizmeti hesap bilgileri `ServiceSecurityContext.Current.WindowsIdentity` özellik kullanılarak ayıklanır.</span><span class="sxs-lookup"><span data-stu-id="03d53-156">The façade service account information is extracted using the `ServiceSecurityContext.Current.WindowsIdentity` property.</span></span> <span data-ttu-id="03d53-157">İlk arayan hakkındaki bilgilere erişmek için arka `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` uç hizmeti özelliği kullanır.</span><span class="sxs-lookup"><span data-stu-id="03d53-157">To access the information about the initial caller the backend service uses the `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` property.</span></span> <span data-ttu-id="03d53-158">Bu tür `Name` `Identity` bir iddia arar.</span><span class="sxs-lookup"><span data-stu-id="03d53-158">It looks for an `Identity` claim with a type `Name`.</span></span> <span data-ttu-id="03d53-159">Bu talep, wcf güvenlik altyapısı tarafından güvenlik belirtecinde `Username` bulunan bilgilerden otomatik olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="03d53-159">This claim is automatically generated by WCF security infrastructure from the information contained in the `Username` security token.</span></span>  
  
## <a name="running-the-sample"></a><span data-ttu-id="03d53-160">Örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="03d53-160">Running the sample</span></span>  
 <span data-ttu-id="03d53-161">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="03d53-161">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="03d53-162">İstemciyi kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="03d53-162">Press ENTER in the client window to shut down the client.</span></span> <span data-ttu-id="03d53-163">Hizmetleri kapatmak için ön cephe ve arka uç servis konsolu pencerelerinde ENTER tuşuna basabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="03d53-163">You can press ENTER in the façade and backend service console windows to shut down the services.</span></span>  
  
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
  
 <span data-ttu-id="03d53-164">Güvenilir Facade senaryo örneğinde yer alan Setup.bat toplu iş dosyası, istemciye kendini doğrulamak için sertifika tabanlı güvenlik gerektiren ön cephe hizmetini çalıştırmak için sunucuyu ilgili bir sertifikayla yapılandırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="03d53-164">The Setup.bat batch file included with the Trusted Facade scenario sample enables you to configure the server with a relevant certificate to run the façade service that requires certificate-based security to authenticate itself to the client.</span></span> <span data-ttu-id="03d53-165">Ayrıntılar için bu konunun sonundaki kurulum yordamına bakın.</span><span class="sxs-lookup"><span data-stu-id="03d53-165">See the setup procedure at the end of this topic for details.</span></span>  
  
 <span data-ttu-id="03d53-166">Aşağıda, toplu iş dosyalarının farklı bölümlerine kısa bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="03d53-166">The following provides a brief overview of the different sections of the batch files.</span></span>  
  
- <span data-ttu-id="03d53-167">Sunucu sertifikası oluşturma.</span><span class="sxs-lookup"><span data-stu-id="03d53-167">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="03d53-168">Setup.bat toplu dosyasından aşağıdaki satırlar kullanılacak sunucu sertifikasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="03d53-168">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span>  
  
    ```console  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     <span data-ttu-id="03d53-169">Değişken `%SERVER_NAME%` sunucu adını belirtir - varsayılan değer localhost'dur.</span><span class="sxs-lookup"><span data-stu-id="03d53-169">The `%SERVER_NAME%` variable specifies the server name - the default value is localhost.</span></span> <span data-ttu-id="03d53-170">Sertifika LocalMachine mağazasında depolanır.</span><span class="sxs-lookup"><span data-stu-id="03d53-170">The certificate is stored in the LocalMachine store.</span></span>  
  
- <span data-ttu-id="03d53-171">Cephe hizmetinin sertifikasını müşterinin güvenilir sertifika deposuna yüklemek.</span><span class="sxs-lookup"><span data-stu-id="03d53-171">Installing the façade service's certificate into the client's trusted certificate store.</span></span>  
  
     <span data-ttu-id="03d53-172">Aşağıdaki satır, cephe hizmetinin sertifikasını istemci güvenilir kişiler deposuna kopyalar.</span><span class="sxs-lookup"><span data-stu-id="03d53-172">The following line copies the façade service's certificate into the client trusted people store.</span></span> <span data-ttu-id="03d53-173">Makecert.exe tarafından oluşturulan sertifikalar istemci sistemi tarafından dolaylı olarak güvenilen olmadığından bu adım gereklidir.</span><span class="sxs-lookup"><span data-stu-id="03d53-173">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="03d53-174">İstemci tarafından güvenilen kök sertifikasına dayanan bir sertifikanız varsa (örneğin, Microsoft tarafından verilmiş bir sertifika- istemci sertifika deposunu sunucu sertifikasıyla doldurma adımı gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="03d53-174">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```console  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="03d53-175">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="03d53-175">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="03d53-176">Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.</span><span class="sxs-lookup"><span data-stu-id="03d53-176">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="03d53-177">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="03d53-177">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="03d53-178">Numuneyi aynı makinede çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="03d53-178">To run the sample on the same machine</span></span>  
  
1. <span data-ttu-id="03d53-179">Yolun Makecert.exe'nin bulunduğu klasörü içerdiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="03d53-179">Ensure that the path includes the folder where Makecert.exe is located.</span></span>  
  
2. <span data-ttu-id="03d53-180">Setup.bat'ı örnek yükleme klasöründen çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="03d53-180">Run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="03d53-181">Bu, örneği çalıştırmak için gereken tüm sertifikaları yükler.</span><span class="sxs-lookup"><span data-stu-id="03d53-181">This installs all the certificates required for running the sample.</span></span>  
  
3. <span data-ttu-id="03d53-182">Ayrı bir konsol penceresinde \BackendService\bin dizininden BackendService.exe başlatın</span><span class="sxs-lookup"><span data-stu-id="03d53-182">Launch the BackendService.exe from \BackendService\bin directory in a separate console window</span></span>  
  
4. <span data-ttu-id="03d53-183">\FacadeService\bin dizininden FacadeService.exe'yi ayrı bir konsol penceresinde başlatın</span><span class="sxs-lookup"><span data-stu-id="03d53-183">Launch the FacadeService.exe from \FacadeService\bin directory in a separate console window</span></span>  
  
5. <span data-ttu-id="03d53-184">Client.exe'yi \client\bin'den başlatın.</span><span class="sxs-lookup"><span data-stu-id="03d53-184">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="03d53-185">İstemci etkinliği istemci konsoluygulamasında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="03d53-185">Client activity is displayed on the client console application.</span></span>  
  
6. <span data-ttu-id="03d53-186">İstemci ve hizmet iletişim kuramazsa, [WCF Örnekleri için Sorun Giderme İpuçları'na](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))bakın.</span><span class="sxs-lookup"><span data-stu-id="03d53-186">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="03d53-187">Örnekten sonra temizlemek için</span><span class="sxs-lookup"><span data-stu-id="03d53-187">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="03d53-188">Örneği çalıştırmayı bitirdikten sonra örnekler klasöründe Cleanup.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="03d53-188">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="03d53-189">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="03d53-189">The samples may already be installed on your machine.</span></span> <span data-ttu-id="03d53-190">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="03d53-190">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="03d53-191">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="03d53-191">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="03d53-192">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="03d53-192">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\TrustedFacade`  
