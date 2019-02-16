---
title: Güvenilir Görünüm Hizmeti
ms.date: 03/30/2017
ms.assetid: c34d1a8f-e45e-440b-a201-d143abdbac38
ms.openlocfilehash: e7e55cc9d4bc9f0f81ad0570b37d7a749e6fadc2
ms.sourcegitcommit: 0069cb3de8eed4e92b2195d29e5769a76111acdd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/16/2019
ms.locfileid: "56332448"
---
# <a name="trusted-facade-service"></a><span data-ttu-id="53ab3-102">Güvenilir Görünüm Hizmeti</span><span class="sxs-lookup"><span data-stu-id="53ab3-102">Trusted Facade Service</span></span>
<span data-ttu-id="53ab3-103">Bu senaryo örneği çağıranın kimlik bilgilerini bir hizmetten diğerine Windows Communication Foundation (WCF) kullanarak akış yapmayı gösteren güvenlik altyapısı.</span><span class="sxs-lookup"><span data-stu-id="53ab3-103">This scenario sample demonstrates how to flow caller's identity information from one service to another using Windows Communication Foundation (WCF) security infrastructure.</span></span>  
  
 <span data-ttu-id="53ab3-104">Bir cephe hizmeti kullanarak ortak ağ için bir hizmet tarafından sağlanan işlevselliği göstermek için bir ortak bir tasarım örüntüsüdür.</span><span class="sxs-lookup"><span data-stu-id="53ab3-104">It is a common design pattern to expose the functionality provided by a service to the public network using a façade service.</span></span> <span data-ttu-id="53ab3-105">Cephe hizmeti genellikle çevre ağındaki (DMZ, sivil bölge ve denetimli alt ağ olarak da bilinir) bulunur ve iş mantığını uygular ve iç verilere erişimi olan bir arka uç hizmetiyle iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="53ab3-105">The façade service typically resides in the perimeter network (also known as DMZ, demilitarized zone, and screened subnet) and communicates with a backend service that implements the business logic and has access to internal data.</span></span> <span data-ttu-id="53ab3-106">Cephe hizmeti ve arka uç hizmeti arasındaki iletişim kanalını bir güvenlik duvarı üzerinden geçer ve yalnızca tek bir amaç için genellikle sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="53ab3-106">The communication channel between the façade service and the backend service goes through a firewall and is usually limited for a single purpose only.</span></span>  
  
 <span data-ttu-id="53ab3-107">Bu örnek aşağıdaki bileşenlerden oluşur:</span><span class="sxs-lookup"><span data-stu-id="53ab3-107">This sample consists of the following components:</span></span>  
  
-   <span data-ttu-id="53ab3-108">Hesaplayıcı istemci</span><span class="sxs-lookup"><span data-stu-id="53ab3-108">Calculator client</span></span>  
  
-   <span data-ttu-id="53ab3-109">Hesaplayıcı cephe hizmeti</span><span class="sxs-lookup"><span data-stu-id="53ab3-109">Calculator façade service</span></span>  
  
-   <span data-ttu-id="53ab3-110">Hesaplayıcı arka uç hizmeti</span><span class="sxs-lookup"><span data-stu-id="53ab3-110">Calculator backend service</span></span>  
  
 <span data-ttu-id="53ab3-111">İstek doğrulanıyor ve arayan kimlik doğrulaması için sorumlu cephe hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="53ab3-111">The façade service is responsible for validating the request and authenticating the caller.</span></span> <span data-ttu-id="53ab3-112">Başarılı kimlik doğrulaması ve doğrulama sonra istek iç ağ çevre ağından denetimli iletişim kanalını kullanarak arka uç hizmetine iletir.</span><span class="sxs-lookup"><span data-stu-id="53ab3-112">After successful authentication and validation, it forwards the request to the backend service using the controlled communication channel from the perimeter network to the internal network.</span></span> <span data-ttu-id="53ab3-113">Bu bilgiler, işleme, arka uç hizmetine kullanabilmesi iletilen isteğin bir parçası olarak cephe hizmet çağıranının kimliğini hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="53ab3-113">As a part of the forwarded request, the façade service includes information about the caller's identity so that the backend service can use this information in its processing.</span></span> <span data-ttu-id="53ab3-114">Çağıranının kimliğini kullanarak iletilen bir `Username` ileti içinde güvenlik belirteci `Security` başlığı.</span><span class="sxs-lookup"><span data-stu-id="53ab3-114">The caller's identity is transmitted using a `Username` security token inside the message `Security` header.</span></span> <span data-ttu-id="53ab3-115">Örnek, iletme ve bu bilgileri ayıklamak için WCF güvenlik altyapısı kullanır. `Security` başlığı.</span><span class="sxs-lookup"><span data-stu-id="53ab3-115">The sample uses the WCF security infrastructure to transmit and extract this information from the `Security` header.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="53ab3-116">Arayan kimliğini doğrulamak için cephe hizmet arka uç hizmetine güvenir.</span><span class="sxs-lookup"><span data-stu-id="53ab3-116">The backend service trusts the façade service to authenticate the caller.</span></span> <span data-ttu-id="53ab3-117">Bu nedenle, arka uç hizmeti çağıran yeniden kimlik doğrulamasını yapmaz; iletilen istek cephe hizmeti tarafından sağlanan kimlik bilgilerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="53ab3-117">Because of this, the backend service does not authenticate the caller again; it uses the identity information provided by the façade service in the forwarded request.</span></span> <span data-ttu-id="53ab3-118">Bu güven ilişkisi nedeniyle, arka uç hizmetine yönlendirilmiş ileti güvenilir bir kaynaktan - bu durumda, cephe hizmet geldiğinden emin olmak için cephe hizmet kimlik doğrulaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="53ab3-118">Because of this trust relationship, the backend service must authenticate the façade service to ensure that the forwarded message comes from a trusted source - in this case, the façade service.</span></span>  
  
## <a name="implementation"></a><span data-ttu-id="53ab3-119">Uygulama</span><span class="sxs-lookup"><span data-stu-id="53ab3-119">Implementation</span></span>  
 <span data-ttu-id="53ab3-120">Bu örnekte iki iletişim yolları vardır.</span><span class="sxs-lookup"><span data-stu-id="53ab3-120">There are two communication paths in this sample.</span></span> <span data-ttu-id="53ab3-121">İlk istemci ile cephe hizmeti arasında cephe hizmeti ve arka uç hizmeti arasında saniyedir.</span><span class="sxs-lookup"><span data-stu-id="53ab3-121">First is between the client and the façade service, the second is between the façade service and the backend service.</span></span>  
  
### <a name="communication-path-between-client-and-faade-service"></a><span data-ttu-id="53ab3-122">Cephe hizmet ve istemci arasındaki iletişim yolunun</span><span class="sxs-lookup"><span data-stu-id="53ab3-122">Communication Path between Client and Façade Service</span></span>  
 <span data-ttu-id="53ab3-123">Cephe hizmet iletişimi yolu istemcinin kullandığı `wsHttpBinding` ile bir `UserName` istemci kimlik bilgisi türü.</span><span class="sxs-lookup"><span data-stu-id="53ab3-123">The client to the façade service communication path uses `wsHttpBinding` with a `UserName` client credential type.</span></span> <span data-ttu-id="53ab3-124">Bu, istemcinin kullandığı kullanıcı adı ve cephe hizmet ve cephe hizmet kimlik doğrulaması için parola, istemcinin kimliğini doğrulamak için X.509 sertifikası kullanır. anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="53ab3-124">This means that the client uses username and password to authenticate to the façade service and the façade service uses X.509 certificate to authenticate to the client.</span></span> <span data-ttu-id="53ab3-125">Bağlama yapılandırması aşağıdaki örnekteki gibi görünür.</span><span class="sxs-lookup"><span data-stu-id="53ab3-125">The binding configuration looks like the following example.</span></span>  
  
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
  
 <span data-ttu-id="53ab3-126">Cephe hizmeti çağıran özel kullanarak kimlik doğrulaması `UserNamePasswordValidator` uygulaması.</span><span class="sxs-lookup"><span data-stu-id="53ab3-126">The façade service authenticates the caller using custom `UserNamePasswordValidator` implementation.</span></span> <span data-ttu-id="53ab3-127">Tanıtım amacıyla, arayanın kullanıcıadı sunulan parolayla eşleşen kimlik doğrulaması yalnızca sağlar.</span><span class="sxs-lookup"><span data-stu-id="53ab3-127">For demonstration purposes, the authentication only ensures that the caller's username matches the presented password.</span></span> <span data-ttu-id="53ab3-128">Gerçek dünya durumda kullanıcı Active Directory veya özel ASP.NET üyelik sağlayıcıyı kullanarak büyük olasılıkla doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="53ab3-128">In the real world situation, the user is probably authenticated using Active Directory or custom ASP.NET Membership provider.</span></span> <span data-ttu-id="53ab3-129">Doğrulayıcı uygulama bulunan `FacadeService.cs` dosya.</span><span class="sxs-lookup"><span data-stu-id="53ab3-129">The validator implementation resides in `FacadeService.cs` file.</span></span>  
  
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
  
 <span data-ttu-id="53ab3-130">Özel Doğrulayıcı sağlayıcısı içinde kullanılmak üzere yapılandırılmış `serviceCredentials` cephe hizmet yapılandırma dosyasında bir davranış.</span><span class="sxs-lookup"><span data-stu-id="53ab3-130">The custom validator is configured to be used inside the `serviceCredentials` behavior in the façade service configuration file.</span></span> <span data-ttu-id="53ab3-131">Bu davranış, hizmetin X.509 sertifikası yapılandırmak için de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="53ab3-131">This behavior is also used to configure the service's X.509 certificate.</span></span>  
  
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
  
### <a name="communication-path-between-faade-service-and-backend-service"></a><span data-ttu-id="53ab3-132">Cephe hizmeti ve arka uç hizmeti arasındaki iletişim yolunun</span><span class="sxs-lookup"><span data-stu-id="53ab3-132">Communication Path between Façade Service and Backend Service</span></span>  
 <span data-ttu-id="53ab3-133">Arka uç hizmeti iletişim yolunun cephe hizmete kullanan bir `customBinding` çeşitli bağlama öğelerinin oluşur.</span><span class="sxs-lookup"><span data-stu-id="53ab3-133">The façade service to the backend service communication path uses a `customBinding` that consists of several binding elements.</span></span> <span data-ttu-id="53ab3-134">Bu bağlamanın iki şeyi gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="53ab3-134">This binding accomplishes two things.</span></span> <span data-ttu-id="53ab3-135">Cephe hizmeti ve iletişimi güvenli ve güvenilir bir kaynaktan geldiğine emin olmak için arka uç hizmeti kimliğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="53ab3-135">It authenticates the façade service and backend service to ensure that the communication is secure and is coming from a trusted source.</span></span> <span data-ttu-id="53ab3-136">Ayrıca, içinde ilk çağıranının kimliğini de iletir `Username` güvenlik belirteci.</span><span class="sxs-lookup"><span data-stu-id="53ab3-136">Additionally, it also transmits the initial caller's identity inside the `Username` security token.</span></span> <span data-ttu-id="53ab3-137">Bu durumda, yalnızca ilk çağrı sahibinin kullanıcı adı arka uç hizmetine aktarılır, parola iletisinde yer almaz.</span><span class="sxs-lookup"><span data-stu-id="53ab3-137">In this case, only the initial caller's username is transmitted to the backend service, the password is not included in the message.</span></span> <span data-ttu-id="53ab3-138">Çağıran, iletilmeden önce kimlik doğrulaması için cephe hizmet arka uç hizmetine güvenir olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="53ab3-138">This is because the backend service trusts the façade service to authenticate the caller before forwarding the request to it.</span></span> <span data-ttu-id="53ab3-139">Cephe hizmetin kendisini arka uç hizmetine doğruladığından, arka uç hizmetine iletilmiş istekte yer alan bilgileri güvenebilir.</span><span class="sxs-lookup"><span data-stu-id="53ab3-139">Because the façade service authenticates itself to the backend service, the backend service can trust the information contained in the forwarded request.</span></span>  
  
 <span data-ttu-id="53ab3-140">Bu iletişim yolunun bağlama yapılandırması aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="53ab3-140">The following is the binding configuration for this communication path.</span></span>  
  
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
  
 <span data-ttu-id="53ab3-141">[ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) bağlama öğesi, ilk çağrı sahibinin kullanıcı adı iletim ve ayıklama üstlenir.</span><span class="sxs-lookup"><span data-stu-id="53ab3-141">The [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) binding element takes care of the initial caller's username transmission and extraction.</span></span> <span data-ttu-id="53ab3-142">[ \<WindowsStreamSecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/windowsstreamsecurity.md) ve [ \<Connectionpoolsettings >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) cephe ve arka uç Hizmetleri kimlik doğrulaması dikkatli ve ileti koruma.</span><span class="sxs-lookup"><span data-stu-id="53ab3-142">The [\<windowsStreamSecurity>](../../../../docs/framework/configure-apps/file-schema/wcf/windowsstreamsecurity.md) and [\<tcpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) take care of authenticating façade and backend services and message protection.</span></span>  
  
 <span data-ttu-id="53ab3-143">İsteği iletmek için cephe hizmet uygulaması, WCF güvenlik altyapısı bu yönlendirilmiş ileti yerleştirebilirsiniz için ilk çağrı sahibinin kullanıcı adı sağlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="53ab3-143">To forward the request, the façade service implementation must provide the initial caller's username so that WCF security infrastructure can place this into the forwarded message.</span></span> <span data-ttu-id="53ab3-144">İlk çağrı sahibinin kullanıcı adı olarak ayarlayarak cephe hizmet uygulamasında sağlanan `ClientCredentials` özelliği istemci proxy örneğinde cephe hizmet arka uç hizmetiyle iletişim kurmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="53ab3-144">The initial caller's username is provided in the façade service implementation by setting it in the `ClientCredentials` property on the client proxy instance that façade service uses to communicate with the backend service.</span></span>  
  
 <span data-ttu-id="53ab3-145">Aşağıdaki kodda gösterildiği nasıl `GetCallerIdentity` yöntemi cephe hizmette uygulanır.</span><span class="sxs-lookup"><span data-stu-id="53ab3-145">The following code shows how `GetCallerIdentity` method is implemented on the façade service.</span></span> <span data-ttu-id="53ab3-146">Aynı düzeni diğer yöntemleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="53ab3-146">Other methods use the same pattern.</span></span>  
  
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
  
 <span data-ttu-id="53ab3-147">Önceki kodda gösterildiği gibi parola üzerinde ayarlı değil `ClientCredentials` özelliği, yalnızca kullanıcı adı ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="53ab3-147">As shown in the previous code, the password is not set on the `ClientCredentials` property, only the username is set.</span></span> <span data-ttu-id="53ab3-148">WCF güvenlik altyapısı tam olarak bu senaryoda, gerekli olduğu bir kullanıcı adı güvenlik belirtecini bir parola olmadan bu durumda, oluşturur.</span><span class="sxs-lookup"><span data-stu-id="53ab3-148">WCF security infrastructure creates a username security token without a password in this case, which is exactly what is required in this scenario.</span></span>  
  
 <span data-ttu-id="53ab3-149">Kullanıcı adı güvenlik belirtecinde yer alan bilgileri üzerindeki arka uç hizmeti, kimliğinin doğrulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="53ab3-149">On the backend service, the information contained in the username security token must be authenticated.</span></span> <span data-ttu-id="53ab3-150">Varsayılan olarak, WCF güvenlik belirtilen parola kullanılarak bir Windows hesabı kullanıcı eşlemeyi dener.</span><span class="sxs-lookup"><span data-stu-id="53ab3-150">By default, WCF security attempts to map the user to a Windows account using the provided password.</span></span> <span data-ttu-id="53ab3-151">Bu durumda, sağlanan parolası yoktur ve arka uç hizmeti kimlik doğrulaması zaten cephe hizmeti tarafından gerçekleştirildiği için kullanıcı adı kimlik doğrulaması için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="53ab3-151">In this case, there is no password provided and the backend service is not required to authenticate the username because the authentication was already performed by the façade service.</span></span> <span data-ttu-id="53ab3-152">WCF'de özel bu işlevselliği uygulamak için `UserNamePasswordValidator` , yalnızca bir kullanıcı adı belirteci belirtilir ve herhangi ek bir kimlik doğrulaması gerçekleştirmez zorlar sağlanır.</span><span class="sxs-lookup"><span data-stu-id="53ab3-152">To implement this functionality in WCF, a custom `UserNamePasswordValidator` is provided that only enforces that a username is specified in the token and does not perform any additional authentication.</span></span>  
  
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
  
 <span data-ttu-id="53ab3-153">Özel Doğrulayıcı sağlayıcısı içinde kullanılmak üzere yapılandırılmış `serviceCredentials` cephe hizmet yapılandırma dosyasında bir davranış.</span><span class="sxs-lookup"><span data-stu-id="53ab3-153">The custom validator is configured to be used inside the `serviceCredentials` behavior in the façade service configuration file.</span></span>  
  
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
  
 <span data-ttu-id="53ab3-154">Güvenilen bir cephe hizmet hesabıyla ilgili bilgileri ve kullanıcı adı bilgileri ayıklamak için arka uç hizmeti uygulaması kullanan `ServiceSecurityContext` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="53ab3-154">To extract the username information and information about the trusted façade service account, the backend service implementation uses the `ServiceSecurityContext` class.</span></span> <span data-ttu-id="53ab3-155">Aşağıdaki kodda gösterildiği nasıl `GetCallerIdentity` yöntemi uygulanır.</span><span class="sxs-lookup"><span data-stu-id="53ab3-155">The following code shows how the `GetCallerIdentity` method is implemented.</span></span>  
  
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
  
 <span data-ttu-id="53ab3-156">Cephe hizmet hesabı bilgilerini kullanarak ayıkladığınız `ServiceSecurityContext.Current.WindowsIdentity` özelliği.</span><span class="sxs-lookup"><span data-stu-id="53ab3-156">The façade service account information is extracted using the `ServiceSecurityContext.Current.WindowsIdentity` property.</span></span> <span data-ttu-id="53ab3-157">Arka uç hizmeti kullandığı ilk çağrıda bulunanı hakkında bilgilere erişmek için `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` özelliği.</span><span class="sxs-lookup"><span data-stu-id="53ab3-157">To access the information about the initial caller the backend service uses the `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` property.</span></span> <span data-ttu-id="53ab3-158">Görünüşe göre yenisiniz bir `Identity` talep türü ile `Name`.</span><span class="sxs-lookup"><span data-stu-id="53ab3-158">It looks for an `Identity` claim with a type `Name`.</span></span> <span data-ttu-id="53ab3-159">Bu talep yer alan bilgileri WCF güvenlik altyapısı tarafından otomatik olarak oluşturulan `Username` güvenlik belirteci.</span><span class="sxs-lookup"><span data-stu-id="53ab3-159">This claim is automatically generated by WCF security infrastructure from the information contained in the `Username` security token.</span></span>  
  
## <a name="running-the-sample"></a><span data-ttu-id="53ab3-160">Örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="53ab3-160">Running the sample</span></span>  
 <span data-ttu-id="53ab3-161">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="53ab3-161">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="53ab3-162">İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="53ab3-162">Press ENTER in the client window to shut down the client.</span></span> <span data-ttu-id="53ab3-163">Hizmetleri kapatılmaya için cephe ve arka uç hizmet Konsolu pencerelerinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="53ab3-163">You can press ENTER in the façade and backend service console windows to shut down the services.</span></span>  
  
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
  
 <span data-ttu-id="53ab3-164">Güvenilir görünüm senaryo örneği ile dahil Setup.bat toplu iş dosyasını kendisini istemcinin kimliğini doğrulamak için sertifika tabanlı güvenlik gerektiren bir cephe hizmeti çalıştırmak için ilgili bir sertifika ile sunucu yapılandırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="53ab3-164">The Setup.bat batch file included with the Trusted Facade scenario sample enables you to configure the server with a relevant certificate to run the façade service that requires certificate-based security to authenticate itself to the client.</span></span> <span data-ttu-id="53ab3-165">Ayrıntılar için bu konunun sonunda Kurulum yordamına bakın.</span><span class="sxs-lookup"><span data-stu-id="53ab3-165">See the setup procedure at the end of this topic for details.</span></span>  
  
 <span data-ttu-id="53ab3-166">Toplu iş dosyaları farklı bölümlerini kısa bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="53ab3-166">The following provides a brief overview of the different sections of the batch files.</span></span>  
  
-   <span data-ttu-id="53ab3-167">Sunucu sertifikası oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="53ab3-167">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="53ab3-168">Setup.bat toplu iş dosyasından aşağıdaki satırları kullanılacak sunucu sertifikası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="53ab3-168">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span>  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     <span data-ttu-id="53ab3-169">`%SERVER_NAME%` Değişkeni, sunucu adını belirtir: localhost varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="53ab3-169">The `%SERVER_NAME%` variable specifies the server name - the default value is localhost.</span></span> <span data-ttu-id="53ab3-170">Depolanmış bir sertifikayla LocalMachine depolama.</span><span class="sxs-lookup"><span data-stu-id="53ab3-170">The certificate is stored in the LocalMachine store.</span></span>  
  
-   <span data-ttu-id="53ab3-171">Cephe hizmetin sertifika istemcinin güvenilen sertifika depolama alanına yükleniyor.</span><span class="sxs-lookup"><span data-stu-id="53ab3-171">Installing the façade service's certificate into the client's trusted certificate store.</span></span>  
  
     <span data-ttu-id="53ab3-172">Aşağıdaki satırı cephe hizmetin sertifika istemcisi güvenilir Kişiler deposuna kopyalar.</span><span class="sxs-lookup"><span data-stu-id="53ab3-172">The following line copies the façade service's certificate into the client trusted people store.</span></span> <span data-ttu-id="53ab3-173">MakeCert.exe tarafından oluşturulan sertifikaları örtük olarak istemci sistemi tarafından güvenilir değildir çünkü bu adım gereklidir.</span><span class="sxs-lookup"><span data-stu-id="53ab3-173">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="53ab3-174">Bir istemci güvenilen kök sertifikayı kök erişim izni verilmiş bir sertifika zaten varsa — örneğin, Microsoft tarafından verilen sertifika — sunucu sertifikasında istemci sertifika deposunun doldurulması, bu adım gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="53ab3-174">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="53ab3-175">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="53ab3-175">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="53ab3-176">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="53ab3-176">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="53ab3-177">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="53ab3-177">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="53ab3-178">Örneği aynı makinede çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="53ab3-178">To run the sample on the same machine</span></span>  
  
1.  <span data-ttu-id="53ab3-179">Yolun Makecert.exe bulunduğu klasörü içerdiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="53ab3-179">Ensure that the path includes the folder where Makecert.exe is located.</span></span>  
  
2.  <span data-ttu-id="53ab3-180">Setup.bat örnek yükleme klasöründen çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="53ab3-180">Run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="53ab3-181">Bu örneği çalıştırmak için gerekli olan tüm sertifikaları yükler.</span><span class="sxs-lookup"><span data-stu-id="53ab3-181">This installs all the certificates required for running the sample.</span></span>  
  
3.  <span data-ttu-id="53ab3-182">Ayrı konsol penceresinde \BackendService\bin dizinden BackendService.exe başlatın</span><span class="sxs-lookup"><span data-stu-id="53ab3-182">Launch the BackendService.exe from \BackendService\bin directory in a separate console window</span></span>  
  
4.  <span data-ttu-id="53ab3-183">Ayrı konsol penceresinde \FacadeService\bin dizinden FacadeService.exe başlatın</span><span class="sxs-lookup"><span data-stu-id="53ab3-183">Launch the FacadeService.exe from \FacadeService\bin directory in a separate console window</span></span>  
  
5.  <span data-ttu-id="53ab3-184">Client.exe \client\bin başlatın.</span><span class="sxs-lookup"><span data-stu-id="53ab3-184">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="53ab3-185">İstemci etkinliği istemci konsol uygulamasında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="53ab3-185">Client activity is displayed on the client console application.</span></span>  
  
6.  <span data-ttu-id="53ab3-186">İstemci ve hizmet iletişim kurabildiğini bilmiyorsanız bkz [WCF örnekleri için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="53ab3-186">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="53ab3-187">Sonra örnek temizlemek için</span><span class="sxs-lookup"><span data-stu-id="53ab3-187">To clean up after the sample</span></span>  
  
1.  <span data-ttu-id="53ab3-188">Bu örneği çalıştırmadan tamamladıktan sonra Cleanup.bat samples klasöründe çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="53ab3-188">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="53ab3-189">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="53ab3-189">The samples may already be installed on your machine.</span></span> <span data-ttu-id="53ab3-190">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="53ab3-190">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="53ab3-191">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="53ab3-191">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="53ab3-192">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="53ab3-192">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\TrustedFacade`  
  
## <a name="see-also"></a><span data-ttu-id="53ab3-193">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="53ab3-193">See also</span></span>
