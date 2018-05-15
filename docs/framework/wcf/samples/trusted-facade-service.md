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
# <a name="trusted-facade-service"></a><span data-ttu-id="a8f52-102">Güvenilir Görünüm Hizmeti</span><span class="sxs-lookup"><span data-stu-id="a8f52-102">Trusted Facade Service</span></span>
<span data-ttu-id="a8f52-103">Bu senaryo örneği başka bir Windows Communication Foundation (WCF) kullanarak bir hizmetten Arayanın kimlik bilgileri akış yapmayı gösteren güvenlik altyapısı.</span><span class="sxs-lookup"><span data-stu-id="a8f52-103">This scenario sample demonstrates how to flow caller's identity information from one service to another using Windows Communication Foundation (WCF) security infrastructure.</span></span>  
  
 <span data-ttu-id="a8f52-104">Cephesi hizmetini kullanan bir ortak ağa hizmeti tarafından sağlanan işlevselliği kullanıma sunmak için ortak bir tasarım deseni değil.</span><span class="sxs-lookup"><span data-stu-id="a8f52-104">It is a common design pattern to expose the functionality provided by a service to the public network using a façade service.</span></span> <span data-ttu-id="a8f52-105">Cephesi hizmeti genellikle çevre ağındaki (DMZ, sivil bölge ve denetimli alt ağ olarak da bilinir) bulunur ve iş mantığını uygular ve iç verilere erişimi olan bir arka uç hizmeti ile iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="a8f52-105">The façade service typically resides in the perimeter network (also known as DMZ, demilitarized zone, and screened subnet) and communicates with a backend service that implements the business logic and has access to internal data.</span></span> <span data-ttu-id="a8f52-106">Cephesi hizmeti ve arka uç hizmeti arasındaki iletişim kanalını bir güvenlik duvarı üzerinden gider ve yalnızca tek bir amaç için genellikle sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="a8f52-106">The communication channel between the façade service and the backend service goes through a firewall and is usually limited for a single purpose only.</span></span>  
  
 <span data-ttu-id="a8f52-107">Bu örnek aşağıdaki bileşenlerden oluşur:</span><span class="sxs-lookup"><span data-stu-id="a8f52-107">This sample consists of the following components:</span></span>  
  
-   <span data-ttu-id="a8f52-108">Hesaplayıcı istemci</span><span class="sxs-lookup"><span data-stu-id="a8f52-108">Calculator client</span></span>  
  
-   <span data-ttu-id="a8f52-109">Hesaplayıcı cephesi hizmeti</span><span class="sxs-lookup"><span data-stu-id="a8f52-109">Calculator façade service</span></span>  
  
-   <span data-ttu-id="a8f52-110">Hesaplayıcı arka uç hizmeti</span><span class="sxs-lookup"><span data-stu-id="a8f52-110">Calculator backend service</span></span>  
  
 <span data-ttu-id="a8f52-111">Cephesi hizmet isteği doğrulanırken ve arayan kimlik doğrulaması için sorumludur.</span><span class="sxs-lookup"><span data-stu-id="a8f52-111">The façade service is responsible for validating the request and authenticating the caller.</span></span> <span data-ttu-id="a8f52-112">Başarılı kimlik doğrulama ve doğrulama sonra iç ağ çevre ağından denetimli iletişim kanalını kullanarak arka uç hizmeti isteği iletir.</span><span class="sxs-lookup"><span data-stu-id="a8f52-112">After successful authentication and validation, it forwards the request to the backend service using the controlled communication channel from the perimeter network to the internal network.</span></span> <span data-ttu-id="a8f52-113">Bu bilgiler, işleme, arka uç hizmetine kullanabilmesi iletilen isteğin bir parçası olarak cephesi hizmeti arayanın kimliği hakkındaki bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="a8f52-113">As a part of the forwarded request, the façade service includes information about the caller's identity so that the backend service can use this information in its processing.</span></span> <span data-ttu-id="a8f52-114">Arayanın Kimliği kullanılarak aktarılan bir `Username` güvenlik belirteci ileti içine `Security` üstbilgi.</span><span class="sxs-lookup"><span data-stu-id="a8f52-114">The caller's identity is transmitted using a `Username` security token inside the message `Security` header.</span></span> <span data-ttu-id="a8f52-115">Örnek, iletme ve bu bilgileri ayıklamak için WCF güvenlik altyapısı kullanır. `Security` üstbilgi.</span><span class="sxs-lookup"><span data-stu-id="a8f52-115">The sample uses the WCF security infrastructure to transmit and extract this information from the `Security` header.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a8f52-116">Arka uç hizmetine arayan kimliğini doğrulamak için cephesi hizmet güvenir.</span><span class="sxs-lookup"><span data-stu-id="a8f52-116">The backend service trusts the façade service to authenticate the caller.</span></span> <span data-ttu-id="a8f52-117">Bu nedenle, arka uç hizmetine çağıran yeniden kimlik doğrulama kullanmaz; iletilen istek cephesi hizmeti tarafından sağlanan kimlik bilgilerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="a8f52-117">Because of this, the backend service does not authenticate the caller again; it uses the identity information provided by the façade service in the forwarded request.</span></span> <span data-ttu-id="a8f52-118">Bu güven ilişkisinin bozulması nedeniyle, arka uç hizmetine yönlendirilmiş ileti güvenilir bir kaynaktan - bu durumda, cephesi hizmet geldiğinden emin olmak için cephesi hizmetinde kimlik doğrulaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a8f52-118">Because of this trust relationship, the backend service must authenticate the façade service to ensure that the forwarded message comes from a trusted source - in this case, the façade service.</span></span>  
  
## <a name="implementation"></a><span data-ttu-id="a8f52-119">Uygulama</span><span class="sxs-lookup"><span data-stu-id="a8f52-119">Implementation</span></span>  
 <span data-ttu-id="a8f52-120">Bu örnekte iki iletişim yolları vardır.</span><span class="sxs-lookup"><span data-stu-id="a8f52-120">There are two communication paths in this sample.</span></span> <span data-ttu-id="a8f52-121">İlk istemci ve cephesi hizmeti arasındaki cephesi hizmeti ve arka uç hizmeti arasında saniyedir.</span><span class="sxs-lookup"><span data-stu-id="a8f52-121">First is between the client and the façade service, the second is between the façade service and the backend service.</span></span>  
  
### <a name="communication-path-between-client-and-faade-service"></a><span data-ttu-id="a8f52-122">Cephesi hizmet ve istemci arasındaki iletişim yolunun</span><span class="sxs-lookup"><span data-stu-id="a8f52-122">Communication Path between Client and Façade Service</span></span>  
 <span data-ttu-id="a8f52-123">Cephesi hizmet iletişimi yolu istemcinin kullandığı `wsHttpBinding` ile bir `UserName` istemci kimlik bilgisi türü.</span><span class="sxs-lookup"><span data-stu-id="a8f52-123">The client to the façade service communication path uses `wsHttpBinding` with a `UserName` client credential type.</span></span> <span data-ttu-id="a8f52-124">Bu kullanıcı adı istemci kullanır ve cephesi hizmeti ve cephesi hizmeti için kimlik doğrulaması için parola X.509 sertifikası istemcinin kimliğini doğrulamak için kullanır. anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a8f52-124">This means that the client uses username and password to authenticate to the façade service and the façade service uses X.509 certificate to authenticate to the client.</span></span> <span data-ttu-id="a8f52-125">Bağlama yapılandırması aşağıdaki gibi görünür.</span><span class="sxs-lookup"><span data-stu-id="a8f52-125">The binding configuration looks like the following example.</span></span>  
  
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
  
 <span data-ttu-id="a8f52-126">Özel kullanarak arayana cephesi hizmeti kimlik doğrulaması `UserNamePasswordValidator` uygulaması.</span><span class="sxs-lookup"><span data-stu-id="a8f52-126">The façade service authenticates the caller using custom `UserNamePasswordValidator` implementation.</span></span> <span data-ttu-id="a8f52-127">Tanıtım amacıyla, çağıranın kullanıcıadı sunulan parola eşleşen kimlik doğrulaması yalnızca sağlar.</span><span class="sxs-lookup"><span data-stu-id="a8f52-127">For demonstration purposes, the authentication only ensures that the caller's username matches the presented password.</span></span> <span data-ttu-id="a8f52-128">Gerçek dünya durumda kullanıcının büyük olasılıkla Active Directory veya özel ASP.NET üyelik sağlayıcısı kullanılarak kimliği doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="a8f52-128">In the real world situation, the user is probably authenticated using Active Directory or custom ASP.NET Membership provider.</span></span> <span data-ttu-id="a8f52-129">Doğrulayıcı uygulama bulunan `FacadeService.cs` dosya.</span><span class="sxs-lookup"><span data-stu-id="a8f52-129">The validator implementation resides in `FacadeService.cs` file.</span></span>  
  
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
  
 <span data-ttu-id="a8f52-130">Özel Doğrulayıcı içinde kullanılmak üzere yapılandırılmış `serviceCredentials` cephesi hizmet yapılandırma dosyasında davranışı.</span><span class="sxs-lookup"><span data-stu-id="a8f52-130">The custom validator is configured to be used inside the `serviceCredentials` behavior in the façade service configuration file.</span></span> <span data-ttu-id="a8f52-131">Bu davranış, hizmetin X.509 sertifikası yapılandırmak için de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a8f52-131">This behavior is also used to configure the service's X.509 certificate.</span></span>  
  
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
  
### <a name="communication-path-between-faade-service-and-backend-service"></a><span data-ttu-id="a8f52-132">Cephesi hizmeti ve arka uç hizmeti arasındaki iletişimi yol</span><span class="sxs-lookup"><span data-stu-id="a8f52-132">Communication Path between Façade Service and Backend Service</span></span>  
 <span data-ttu-id="a8f52-133">Arka uç hizmeti iletişimi yolu cephesi hizmete kullanan bir `customBinding` birkaç bağlama öğelerden oluşur.</span><span class="sxs-lookup"><span data-stu-id="a8f52-133">The façade service to the backend service communication path uses a `customBinding` that consists of several binding elements.</span></span> <span data-ttu-id="a8f52-134">Bu bağlamanın iki şey gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="a8f52-134">This binding accomplishes two things.</span></span> <span data-ttu-id="a8f52-135">Cephesi hizmeti ve iletişimin güvenli ve güvenilir bir kaynaktan geldiğinden emin olmak için arka uç hizmeti kimliğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="a8f52-135">It authenticates the façade service and backend service to ensure that the communication is secure and is coming from a trusted source.</span></span> <span data-ttu-id="a8f52-136">Ayrıca, içinde ilk çağıranının kimliğini de iletir `Username` güvenlik belirteci.</span><span class="sxs-lookup"><span data-stu-id="a8f52-136">Additionally, it also transmits the initial caller's identity inside the `Username` security token.</span></span> <span data-ttu-id="a8f52-137">Bu durumda yalnızca ilk arayanın kullanıcı adı arka uç hizmetine aktarılır, parola iletide yer almaz.</span><span class="sxs-lookup"><span data-stu-id="a8f52-137">In this case, only the initial caller's username is transmitted to the backend service, the password is not included in the message.</span></span> <span data-ttu-id="a8f52-138">Çağıran, iletilmeden önce kimlik doğrulaması için cephesi hizmet arka uç hizmetine güvenir olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="a8f52-138">This is because the backend service trusts the façade service to authenticate the caller before forwarding the request to it.</span></span> <span data-ttu-id="a8f52-139">Cephesi hizmeti kendisini arka uç hizmetine kimlik doğrulaması için arka uç hizmetine iletilen istekte yer alan bilgileri güvenebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a8f52-139">Because the façade service authenticates itself to the backend service, the backend service can trust the information contained in the forwarded request.</span></span>  
  
 <span data-ttu-id="a8f52-140">Bu iletişim yolunun bağlama yapılandırması verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a8f52-140">The following is the binding configuration for this communication path.</span></span>  
  
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
  
 <span data-ttu-id="a8f52-141">[ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) bağlama öğesi ilk arayanın kullanıcıadı iletim ve ayıklama mvc'deki.</span><span class="sxs-lookup"><span data-stu-id="a8f52-141">The [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) binding element takes care of the initial caller's username transmission and extraction.</span></span> <span data-ttu-id="a8f52-142">[ \<WindowsStreamSecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/windowsstreamsecurity.md) ve [ \<Connectionpoolsettings >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) cephesi ve arka uç hizmetlerinin kimlik doğrulaması dikkatli ve ileti koruma.</span><span class="sxs-lookup"><span data-stu-id="a8f52-142">The [\<windowsStreamSecurity>](../../../../docs/framework/configure-apps/file-schema/wcf/windowsstreamsecurity.md) and [\<tcpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) take care of authenticating façade and backend services and message protection.</span></span>  
  
 <span data-ttu-id="a8f52-143">İstek iletmek için cephesi hizmet uygulaması, WCF güvenlik altyapı bu yönlendirilmiş ileti koyabilirsiniz şekilde ilk arayanın kullanıcı adı sağlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="a8f52-143">To forward the request, the façade service implementation must provide the initial caller's username so that WCF security infrastructure can place this into the forwarded message.</span></span> <span data-ttu-id="a8f52-144">İlk arayanın adı ayarlayarak cephesi hizmet uygulamasında sağlanır `ClientCredentials` istemci proxy örneği özellikte cephesi hizmet arka uç hizmeti ile iletişim için kullanır.</span><span class="sxs-lookup"><span data-stu-id="a8f52-144">The initial caller's username is provided in the façade service implementation by setting it in the `ClientCredentials` property on the client proxy instance that façade service uses to communicate with the backend service.</span></span>  
  
 <span data-ttu-id="a8f52-145">Aşağıdaki kodda gösterildiği nasıl `GetCallerIdentity` yöntemi cephesi hizmette uygulanır.</span><span class="sxs-lookup"><span data-stu-id="a8f52-145">The following code shows how `GetCallerIdentity` method is implemented on the façade service.</span></span> <span data-ttu-id="a8f52-146">Diğer yöntemleri aynı düzeni kullanın.</span><span class="sxs-lookup"><span data-stu-id="a8f52-146">Other methods use the same pattern.</span></span>  
  
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
  
 <span data-ttu-id="a8f52-147">Önceki kodda gösterildiği gibi parola ayarlanmamış `ClientCredentials` özelliği, yalnızca kullanıcı adı olarak ayarlanmış.</span><span class="sxs-lookup"><span data-stu-id="a8f52-147">As shown in the previous code, the password is not set on the `ClientCredentials` property, only the username is set.</span></span> <span data-ttu-id="a8f52-148">WCF güvenlik altyapısı tam olarak bu senaryoda gerekli olduğu bir kullanıcı adı güvenlik belirteci parolasız bu durumda, oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a8f52-148">WCF security infrastructure creates a username security token without a password in this case, which is exactly what is required in this scenario.</span></span>  
  
 <span data-ttu-id="a8f52-149">Arka uç hizmeti kullanıcıadı güvenlik belirtecinde yer alan bilgileri kimliğinin doğrulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a8f52-149">On the backend service, the information contained in the username security token must be authenticated.</span></span> <span data-ttu-id="a8f52-150">Varsayılan olarak, WCF güvenlik belirtilen parola kullanılarak bir Windows hesabı kullanıcı eşlemeyi dener.</span><span class="sxs-lookup"><span data-stu-id="a8f52-150">By default, WCF security attempts to map the user to a Windows account using the provided password.</span></span> <span data-ttu-id="a8f52-151">Bu durumda, sağlanan parola yoktur ve arka uç hizmetine kimlik doğrulaması cephesi hizmeti tarafından zaten gerçekleştirildiği için kullanıcı kimlik doğrulaması için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="a8f52-151">In this case, there is no password provided and the backend service is not required to authenticate the username because the authentication was already performed by the façade service.</span></span> <span data-ttu-id="a8f52-152">Bu işlevsellik, WCF, özel bir uygulamak için `UserNamePasswordValidator` , yalnızca bir kullanıcı adı belirteç belirtilir ve herhangi bir ek kimlik doğrulaması gerçekleştirmez zorlayan sağlanır.</span><span class="sxs-lookup"><span data-stu-id="a8f52-152">To implement this functionality in WCF, a custom `UserNamePasswordValidator` is provided that only enforces that a username is specified in the token and does not perform any additional authentication.</span></span>  
  
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
  
 <span data-ttu-id="a8f52-153">Özel Doğrulayıcı içinde kullanılmak üzere yapılandırılmış `serviceCredentials` cephesi hizmet yapılandırma dosyasında davranışı.</span><span class="sxs-lookup"><span data-stu-id="a8f52-153">The custom validator is configured to be used inside the `serviceCredentials` behavior in the façade service configuration file.</span></span>  
  
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
  
 <span data-ttu-id="a8f52-154">Kullanıcı adı bilgileri ve güvenilir cephesi hizmet hesabı hakkındaki bilgileri ayıklamak için arka uç hizmeti uygulaması kullanır `ServiceSecurityContext` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a8f52-154">To extract the username information and information about the trusted façade service account, the backend service implementation uses the `ServiceSecurityContext` class.</span></span> <span data-ttu-id="a8f52-155">Aşağıdaki kodda gösterildiği nasıl `GetCallerIdentity` yöntemi uygulanır.</span><span class="sxs-lookup"><span data-stu-id="a8f52-155">The following code shows how the `GetCallerIdentity` method is implemented.</span></span>  
  
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
  
 <span data-ttu-id="a8f52-156">Cephesi hizmeti hesap bilgileri kullanılarak elde `ServiceSecurityContext.Current.WindowsIdentity` özelliği.</span><span class="sxs-lookup"><span data-stu-id="a8f52-156">The façade service account information is extracted using the `ServiceSecurityContext.Current.WindowsIdentity` property.</span></span> <span data-ttu-id="a8f52-157">İlk çağıran hakkında bilgi arka uç hizmeti kullandığı erişmek için `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` özelliği.</span><span class="sxs-lookup"><span data-stu-id="a8f52-157">To access the information about the initial caller the backend service uses the `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` property.</span></span> <span data-ttu-id="a8f52-158">Görünüyor bir `Identity` talep türü ile `Name`.</span><span class="sxs-lookup"><span data-stu-id="a8f52-158">It looks for an `Identity` claim with a type `Name`.</span></span> <span data-ttu-id="a8f52-159">Bu talep WCF güvenlik altyapısı içinde yer alan bilgileri tarafından otomatik olarak oluşturulan `Username` güvenlik belirteci.</span><span class="sxs-lookup"><span data-stu-id="a8f52-159">This claim is automatically generated by WCF security infrastructure from the information contained in the `Username` security token.</span></span>  
  
## <a name="running-the-sample"></a><span data-ttu-id="a8f52-160">Örnek çalışıyor</span><span class="sxs-lookup"><span data-stu-id="a8f52-160">Running the sample</span></span>  
 <span data-ttu-id="a8f52-161">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="a8f52-161">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="a8f52-162">İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="a8f52-162">Press ENTER in the client window to shut down the client.</span></span> <span data-ttu-id="a8f52-163">Hizmetleri kapatılmaya için cephesi ve arka uç hizmet Konsolu pencerelerinde ENTER tuşuna basabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a8f52-163">You can press ENTER in the façade and backend service console windows to shut down the services.</span></span>  
  
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
  
 <span data-ttu-id="a8f52-164">Güvenilir görünüm senaryo örneği ile dahil Setup.bat toplu iş dosyası, sunucu istemciye kendi kimliğini doğrulamak için sertifika tabanlı güvenlik gerektiren cephesi hizmeti çalıştırmak için uygun bir sertifika ile yapılandırmak sağlar.</span><span class="sxs-lookup"><span data-stu-id="a8f52-164">The Setup.bat batch file included with the Trusted Facade scenario sample enables you to configure the server with a relevant certificate to run the façade service that requires certificate-based security to authenticate itself to the client.</span></span> <span data-ttu-id="a8f52-165">Ayrıntılar için bu konunun sonundaki Kurulum yordamına bakın.</span><span class="sxs-lookup"><span data-stu-id="a8f52-165">See the setup procedure at the end of this topic for details.</span></span>  
  
 <span data-ttu-id="a8f52-166">Toplu iş dosyaları farklı bölümlerini kısa bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="a8f52-166">The following provides a brief overview of the different sections of the batch files.</span></span>  
  
-   <span data-ttu-id="a8f52-167">Sunucu sertifikası oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="a8f52-167">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="a8f52-168">Aşağıdaki satırları Setup.bat toplu iş dosyasından kullanılacak sunucu sertifikası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a8f52-168">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span>  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     <span data-ttu-id="a8f52-169">`%SERVER_NAME%` Değişkeni, sunucu adını belirtir - localhost varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="a8f52-169">The `%SERVER_NAME%` variable specifies the server name - the default value is localhost.</span></span> <span data-ttu-id="a8f52-170">Sertifika saklanır LocalMachine deposundaki.</span><span class="sxs-lookup"><span data-stu-id="a8f52-170">The certificate is stored in the LocalMachine store.</span></span>  
  
-   <span data-ttu-id="a8f52-171">Cephesi hizmetin sertifikası istemcinin güvenilen sertifika deposuna yükleme.</span><span class="sxs-lookup"><span data-stu-id="a8f52-171">Installing the façade service's certificate into the client's trusted certificate store.</span></span>  
  
     <span data-ttu-id="a8f52-172">Aşağıdaki satırı cephesi hizmetin sertifikası istemcinin güvenilir Kişiler deposuna kopyalar.</span><span class="sxs-lookup"><span data-stu-id="a8f52-172">The following line copies the façade service's certificate into the client trusted people store.</span></span> <span data-ttu-id="a8f52-173">MakeCert.exe tarafından oluşturulan sertifikaları örtük olarak istemci sistemi tarafından güvenilir değil çünkü bu adım gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a8f52-173">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="a8f52-174">Bir istemci güvenilen kök sertifikasını kökü belirtilmiş bir sertifikanız zaten varsa — örneğin, Microsoft tarafından verilen sertifika — sunucu sertifikasına sahip istemci sertifika deposunun doldurulması, bu adım gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="a8f52-174">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a8f52-175">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="a8f52-175">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="a8f52-176">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a8f52-176">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="a8f52-177">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a8f52-177">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="a8f52-178">Aynı makinede örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="a8f52-178">To run the sample on the same machine</span></span>  
  
1.  <span data-ttu-id="a8f52-179">Yolun Makecert.exe bulunduğu klasörü içerdiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="a8f52-179">Ensure that the path includes the folder where Makecert.exe is located.</span></span>  
  
2.  <span data-ttu-id="a8f52-180">Setup.bat örnek yükleme klasöründen çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a8f52-180">Run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="a8f52-181">Bu örneği çalıştırmak için gerekli tüm sertifikalar yükler.</span><span class="sxs-lookup"><span data-stu-id="a8f52-181">This installs all the certificates required for running the sample.</span></span>  
  
3.  <span data-ttu-id="a8f52-182">Ayrı konsol penceresinde \BackendService\bin dizininden BackendService.exe başlatma</span><span class="sxs-lookup"><span data-stu-id="a8f52-182">Launch the BackendService.exe from \BackendService\bin directory in a separate console window</span></span>  
  
4.  <span data-ttu-id="a8f52-183">Ayrı konsol penceresinde \FacadeService\bin dizininden FacadeService.exe başlatma</span><span class="sxs-lookup"><span data-stu-id="a8f52-183">Launch the FacadeService.exe from \FacadeService\bin directory in a separate console window</span></span>  
  
5.  <span data-ttu-id="a8f52-184">Client.exe \client\bin başlatın.</span><span class="sxs-lookup"><span data-stu-id="a8f52-184">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="a8f52-185">İstemci etkinliği istemci konsol uygulaması görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="a8f52-185">Client activity is displayed on the client console application.</span></span>  
  
6.  <span data-ttu-id="a8f52-186">İstemci ve hizmet iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="a8f52-186">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="a8f52-187">Örnek sonra temizlemek için</span><span class="sxs-lookup"><span data-stu-id="a8f52-187">To clean up after the sample</span></span>  
  
1.  <span data-ttu-id="a8f52-188">Örnek çalıştıran tamamladıktan sonra Cleanup.bat samples klasöründen çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a8f52-188">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a8f52-189">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="a8f52-189">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a8f52-190">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="a8f52-190">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a8f52-191">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="a8f52-191">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a8f52-192">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="a8f52-192">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\TrustedFacade`  
  
## <a name="see-also"></a><span data-ttu-id="a8f52-193">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a8f52-193">See Also</span></span>
