---
title: Güvenilir Görünüm Hizmeti
ms.date: 03/30/2017
ms.assetid: c34d1a8f-e45e-440b-a201-d143abdbac38
ms.openlocfilehash: e9459b4cc26ef85adcc59c308d92491fd2d3acba
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90544186"
---
# <a name="trusted-facade-service"></a><span data-ttu-id="44ef3-102">Güvenilir Görünüm Hizmeti</span><span class="sxs-lookup"><span data-stu-id="44ef3-102">Trusted Facade Service</span></span>
<span data-ttu-id="44ef3-103">Bu senaryo örneği, arayanın kimlik bilgilerinin bir hizmetten diğerine Windows Communication Foundation (WCF) güvenlik altyapısını kullanarak nasıl akabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="44ef3-103">This scenario sample demonstrates how to flow caller's identity information from one service to another using Windows Communication Foundation (WCF) security infrastructure.</span></span>  
  
 <span data-ttu-id="44ef3-104">Bir hizmet tarafından bir hizmet tarafından sunulan işlevselliği bir façlade hizmeti kullanılarak kullanıma sunmak için ortak bir tasarım modelidir.</span><span class="sxs-lookup"><span data-stu-id="44ef3-104">It is a common design pattern to expose the functionality provided by a service to the public network using a façade service.</span></span> <span data-ttu-id="44ef3-105">Façlade hizmeti genellikle çevre ağında (DMZ, sivil bölge ve denetimli alt ağ olarak da bilinir) bulunur ve iş mantığını uygulayan ve iç verilere erişim sağlayan bir arka uç hizmetiyle iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="44ef3-105">The façade service typically resides in the perimeter network (also known as DMZ, demilitarized zone, and screened subnet) and communicates with a backend service that implements the business logic and has access to internal data.</span></span> <span data-ttu-id="44ef3-106">Façlade hizmeti ile arka uç hizmeti arasındaki iletişim kanalı bir güvenlik duvarından geçer ve genellikle yalnızca tek bir amaçla sınırlandırılır.</span><span class="sxs-lookup"><span data-stu-id="44ef3-106">The communication channel between the façade service and the backend service goes through a firewall and is usually limited for a single purpose only.</span></span>  
  
 <span data-ttu-id="44ef3-107">Bu örnek aşağıdaki bileşenlerden oluşur:</span><span class="sxs-lookup"><span data-stu-id="44ef3-107">This sample consists of the following components:</span></span>  
  
- <span data-ttu-id="44ef3-108">Hesaplayıcı istemcisi</span><span class="sxs-lookup"><span data-stu-id="44ef3-108">Calculator client</span></span>  
  
- <span data-ttu-id="44ef3-109">Hesaplayıcı façlade hizmeti</span><span class="sxs-lookup"><span data-stu-id="44ef3-109">Calculator façade service</span></span>  
  
- <span data-ttu-id="44ef3-110">Hesaplayıcı arka uç hizmeti</span><span class="sxs-lookup"><span data-stu-id="44ef3-110">Calculator backend service</span></span>  
  
 <span data-ttu-id="44ef3-111">Façlade hizmeti, isteği doğrulamadan ve arayanın kimliğini doğrulamaya sorumludur.</span><span class="sxs-lookup"><span data-stu-id="44ef3-111">The façade service is responsible for validating the request and authenticating the caller.</span></span> <span data-ttu-id="44ef3-112">Başarılı kimlik doğrulama ve doğrulamadan sonra, çevre ağdan iç ağa denetimli iletişim kanalını kullanarak isteği arka uç hizmetine iletir.</span><span class="sxs-lookup"><span data-stu-id="44ef3-112">After successful authentication and validation, it forwards the request to the backend service using the controlled communication channel from the perimeter network to the internal network.</span></span> <span data-ttu-id="44ef3-113">İletilen isteğin bir parçası olarak, façlade hizmeti çağıranın kimliği hakkında bilgiler içerir, böylece arka uç hizmeti bu bilgileri işlemede kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="44ef3-113">As a part of the forwarded request, the façade service includes information about the caller's identity so that the backend service can use this information in its processing.</span></span> <span data-ttu-id="44ef3-114">Arayanın kimliği, `Username` ileti üstbilgisinin içindeki bir güvenlik belirteci kullanılarak iletilir `Security` .</span><span class="sxs-lookup"><span data-stu-id="44ef3-114">The caller's identity is transmitted using a `Username` security token inside the message `Security` header.</span></span> <span data-ttu-id="44ef3-115">Örnek, bu bilgileri üst bilgiden iletmek ve ayıklamak için WCF güvenlik altyapısını kullanır `Security` .</span><span class="sxs-lookup"><span data-stu-id="44ef3-115">The sample uses the WCF security infrastructure to transmit and extract this information from the `Security` header.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="44ef3-116">Arka uç hizmeti, arayanın kimliğini doğrulamak için façlade hizmetine güvenir.</span><span class="sxs-lookup"><span data-stu-id="44ef3-116">The backend service trusts the façade service to authenticate the caller.</span></span> <span data-ttu-id="44ef3-117">Bu nedenle, arka uç hizmeti çağıranın kimliğini doğrulamaz; Bu, iletilen istekte façlade hizmeti tarafından sunulan kimlik bilgilerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="44ef3-117">Because of this, the backend service does not authenticate the caller again; it uses the identity information provided by the façade service in the forwarded request.</span></span> <span data-ttu-id="44ef3-118">Bu güven ilişkisi nedeniyle, arka uç hizmeti, iletilen iletinin güvenilen bir kaynaktan geldiğinden emin olmak için façlade hizmetinin kimliğini doğrulamalıdır; bu durumda façlade hizmeti.</span><span class="sxs-lookup"><span data-stu-id="44ef3-118">Because of this trust relationship, the backend service must authenticate the façade service to ensure that the forwarded message comes from a trusted source - in this case, the façade service.</span></span>  
  
## <a name="implementation"></a><span data-ttu-id="44ef3-119">Uygulama</span><span class="sxs-lookup"><span data-stu-id="44ef3-119">Implementation</span></span>  
 <span data-ttu-id="44ef3-120">Bu örnekte iki iletişim yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="44ef3-120">There are two communication paths in this sample.</span></span> <span data-ttu-id="44ef3-121">İlk olarak istemci ile façlade hizmeti arasında ikinci değer façlade hizmeti ve arka uç hizmeti arasındadır.</span><span class="sxs-lookup"><span data-stu-id="44ef3-121">First is between the client and the façade service, the second is between the façade service and the backend service.</span></span>  
  
### <a name="communication-path-between-client-and-faade-service"></a><span data-ttu-id="44ef3-122">Istemci ile Façlade hizmeti arasındaki iletişim yolu</span><span class="sxs-lookup"><span data-stu-id="44ef3-122">Communication Path between Client and Façade Service</span></span>  
 <span data-ttu-id="44ef3-123">Façlade hizmeti iletişim yolunun istemcisi `wsHttpBinding` `UserName` istemci kimlik bilgisi türü ile kullanır.</span><span class="sxs-lookup"><span data-stu-id="44ef3-123">The client to the façade service communication path uses `wsHttpBinding` with a `UserName` client credential type.</span></span> <span data-ttu-id="44ef3-124">Bu, istemcinin façlade hizmetinde kimlik doğrulamak için Kullanıcı adı ve parola kullandığı ve façlade hizmetinin istemcide kimlik doğrulamak için X. 509.440 sertifikası kullandığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="44ef3-124">This means that the client uses username and password to authenticate to the façade service and the façade service uses X.509 certificate to authenticate to the client.</span></span> <span data-ttu-id="44ef3-125">Bağlama yapılandırması aşağıdaki örneğe benzer şekilde görünür.</span><span class="sxs-lookup"><span data-stu-id="44ef3-125">The binding configuration looks like the following example.</span></span>  
  
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
  
 <span data-ttu-id="44ef3-126">Façlade hizmeti, özel uygulama kullanarak arayanın kimliğini doğrular `UserNamePasswordValidator` .</span><span class="sxs-lookup"><span data-stu-id="44ef3-126">The façade service authenticates the caller using custom `UserNamePasswordValidator` implementation.</span></span> <span data-ttu-id="44ef3-127">Tanıtım amacıyla, kimlik doğrulaması yalnızca arayanın Kullanıcı adının görüntülenen parolayla eşleşmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="44ef3-127">For demonstration purposes, the authentication only ensures that the caller's username matches the presented password.</span></span> <span data-ttu-id="44ef3-128">Gerçek dünyada, kullanıcının kimliği büyük olasılıkla Active Directory veya özel ASP.NET üyelik sağlayıcısı kullanılarak doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="44ef3-128">In the real world situation, the user is probably authenticated using Active Directory or custom ASP.NET Membership provider.</span></span> <span data-ttu-id="44ef3-129">Doğrulayıcı uygulama `FacadeService.cs` dosyasında bulunur.</span><span class="sxs-lookup"><span data-stu-id="44ef3-129">The validator implementation resides in `FacadeService.cs` file.</span></span>  
  
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
  
 <span data-ttu-id="44ef3-130">Özel Doğrulayıcı, `serviceCredentials` façlade hizmeti yapılandırma dosyasındaki davranış içinde kullanılmak üzere yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="44ef3-130">The custom validator is configured to be used inside the `serviceCredentials` behavior in the façade service configuration file.</span></span> <span data-ttu-id="44ef3-131">Bu davranış, hizmetin X. 509.440 sertifikasını yapılandırmak için de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="44ef3-131">This behavior is also used to configure the service's X.509 certificate.</span></span>  
  
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
  
### <a name="communication-path-between-faade-service-and-backend-service"></a><span data-ttu-id="44ef3-132">Façlade hizmeti ile arka uç hizmeti arasındaki iletişim yolu</span><span class="sxs-lookup"><span data-stu-id="44ef3-132">Communication Path between Façade Service and Backend Service</span></span>  
 <span data-ttu-id="44ef3-133">Arka uç hizmeti iletişim yolunda façlade hizmeti, `customBinding` çeşitli bağlama öğelerinden oluşan bir kullanır.</span><span class="sxs-lookup"><span data-stu-id="44ef3-133">The façade service to the backend service communication path uses a `customBinding` that consists of several binding elements.</span></span> <span data-ttu-id="44ef3-134">Bu bağlama iki şeyi gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="44ef3-134">This binding accomplishes two things.</span></span> <span data-ttu-id="44ef3-135">İletişimin güvenli olduğundan ve güvenilen bir kaynaktan geldiğinden emin olmak için façlade hizmeti ve arka uç hizmeti 'nin kimliğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="44ef3-135">It authenticates the façade service and backend service to ensure that the communication is secure and is coming from a trusted source.</span></span> <span data-ttu-id="44ef3-136">Ayrıca, güvenlik belirtecinin içindeki ilk arayanın kimliğini de iletir `Username` .</span><span class="sxs-lookup"><span data-stu-id="44ef3-136">Additionally, it also transmits the initial caller's identity inside the `Username` security token.</span></span> <span data-ttu-id="44ef3-137">Bu durumda, yalnızca ilk arayanın Kullanıcı adı arka uç hizmetine iletilir, parola iletiye eklenmez.</span><span class="sxs-lookup"><span data-stu-id="44ef3-137">In this case, only the initial caller's username is transmitted to the backend service, the password is not included in the message.</span></span> <span data-ttu-id="44ef3-138">Bunun nedeni, arka uç hizmetinin isteği kendisine iletmeden önce arayanın kimliğini doğrulamak üzere façlade hizmetine güvenmesidir.</span><span class="sxs-lookup"><span data-stu-id="44ef3-138">This is because the backend service trusts the façade service to authenticate the caller before forwarding the request to it.</span></span> <span data-ttu-id="44ef3-139">Façlade hizmeti kendi arka uç hizmetinde kimliğini doğruladığından, arka uç hizmeti iletilen istekte bulunan bilgilere güvenebilirler.</span><span class="sxs-lookup"><span data-stu-id="44ef3-139">Because the façade service authenticates itself to the backend service, the backend service can trust the information contained in the forwarded request.</span></span>  
  
 <span data-ttu-id="44ef3-140">Bu iletişim yolu için bağlama yapılandırması aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="44ef3-140">The following is the binding configuration for this communication path.</span></span>  
  
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
  
 <span data-ttu-id="44ef3-141">[\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md)Bağlama öğesi, ilk çağıranın Kullanıcı adı iletimi ve ayıklama işlemini gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="44ef3-141">The [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) binding element takes care of the initial caller's username transmission and extraction.</span></span> <span data-ttu-id="44ef3-142">[\<windowsStreamSecurity>](../../configure-apps/file-schema/wcf/windowsstreamsecurity.md)Ve, [\<tcpTransport>](../../configure-apps/file-schema/wcf/tcptransport.md) façlade ve arka uç hizmetleri ile ileti korumasının kimlik doğrulamasını yapın.</span><span class="sxs-lookup"><span data-stu-id="44ef3-142">The [\<windowsStreamSecurity>](../../configure-apps/file-schema/wcf/windowsstreamsecurity.md) and [\<tcpTransport>](../../configure-apps/file-schema/wcf/tcptransport.md) take care of authenticating façade and backend services and message protection.</span></span>  
  
 <span data-ttu-id="44ef3-143">İsteği iletmek için, façlade Hizmeti uygulamasının ilk çağıranın Kullanıcı adını sağlaması gerekir, böylece WCF güvenlik altyapısı bunu iletilen iletiye yerleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="44ef3-143">To forward the request, the façade service implementation must provide the initial caller's username so that WCF security infrastructure can place this into the forwarded message.</span></span> <span data-ttu-id="44ef3-144">İlk arayanın Kullanıcı adı, façlade hizmeti 'nin `ClientCredentials` arka uç hizmetiyle iletişim kurmak için bir istemci ara sunucu örneğindeki özelliğinde ayarlanarak façlade hizmeti uygulamasında sağlanır.</span><span class="sxs-lookup"><span data-stu-id="44ef3-144">The initial caller's username is provided in the façade service implementation by setting it in the `ClientCredentials` property on the client proxy instance that façade service uses to communicate with the backend service.</span></span>  
  
 <span data-ttu-id="44ef3-145">Aşağıdaki kod, `GetCallerIdentity` yöntemin façlade hizmetinde nasıl uygulandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="44ef3-145">The following code shows how `GetCallerIdentity` method is implemented on the façade service.</span></span> <span data-ttu-id="44ef3-146">Diğer yöntemler aynı kalıbı kullanır.</span><span class="sxs-lookup"><span data-stu-id="44ef3-146">Other methods use the same pattern.</span></span>  
  
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
  
 <span data-ttu-id="44ef3-147">Önceki kodda gösterildiği gibi, bu, özelliği üzerinde de ayarlanır `ClientCredentials` , yalnızca Kullanıcı adı ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="44ef3-147">As shown in the previous code, the password is not set on the `ClientCredentials` property, only the username is set.</span></span> <span data-ttu-id="44ef3-148">WCF güvenlik altyapısı bu durumda bir parola olmadan bir Kullanıcı adı güvenlik belirteci oluşturur; Bu, tam olarak bu senaryoda gerekli olan şeydir.</span><span class="sxs-lookup"><span data-stu-id="44ef3-148">WCF security infrastructure creates a username security token without a password in this case, which is exactly what is required in this scenario.</span></span>  
  
 <span data-ttu-id="44ef3-149">Arka uç hizmetinde, Kullanıcı adı güvenlik belirtecinde bulunan bilgilerin kimliği doğrulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="44ef3-149">On the backend service, the information contained in the username security token must be authenticated.</span></span> <span data-ttu-id="44ef3-150">Varsayılan olarak, WCF güvenliği, belirtilen parolayı kullanarak kullanıcıyı bir Windows hesabıyla eşlemeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="44ef3-150">By default, WCF security attempts to map the user to a Windows account using the provided password.</span></span> <span data-ttu-id="44ef3-151">Bu durumda, kimlik doğrulaması façlade hizmeti tarafından zaten gerçekleştirildiğinden Kullanıcı adının kimliğini doğrulamak için bir parola sağlanmadı ve arka uç hizmeti gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="44ef3-151">In this case, there is no password provided and the backend service is not required to authenticate the username because the authentication was already performed by the façade service.</span></span> <span data-ttu-id="44ef3-152">WCF 'de bu işlevselliği uygulamak için, `UserNamePasswordValidator` yalnızca belirteçte bir kullanıcı adının belirtilmesini zorladığı ve ek kimlik doğrulama gerçekleştirmediğinden özel bir özel sağlanır.</span><span class="sxs-lookup"><span data-stu-id="44ef3-152">To implement this functionality in WCF, a custom `UserNamePasswordValidator` is provided that only enforces that a username is specified in the token and does not perform any additional authentication.</span></span>  
  
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
  
 <span data-ttu-id="44ef3-153">Özel Doğrulayıcı, `serviceCredentials` façlade hizmeti yapılandırma dosyasındaki davranış içinde kullanılmak üzere yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="44ef3-153">The custom validator is configured to be used inside the `serviceCredentials` behavior in the façade service configuration file.</span></span>  
  
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
  
 <span data-ttu-id="44ef3-154">Kullanıcı adı bilgilerini ve güvenilir façlade Hizmeti hesabıyla ilgili bilgileri ayıklamak için arka uç hizmet uygulamasının `ServiceSecurityContext` sınıfını kullanır.</span><span class="sxs-lookup"><span data-stu-id="44ef3-154">To extract the username information and information about the trusted façade service account, the backend service implementation uses the `ServiceSecurityContext` class.</span></span> <span data-ttu-id="44ef3-155">Aşağıdaki kod yöntemin nasıl uygulandığını gösterir `GetCallerIdentity` .</span><span class="sxs-lookup"><span data-stu-id="44ef3-155">The following code shows how the `GetCallerIdentity` method is implemented.</span></span>  
  
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
  
 <span data-ttu-id="44ef3-156">Façlade hizmeti hesap bilgileri, özelliği kullanılarak ayıklanır `ServiceSecurityContext.Current.WindowsIdentity` .</span><span class="sxs-lookup"><span data-stu-id="44ef3-156">The façade service account information is extracted using the `ServiceSecurityContext.Current.WindowsIdentity` property.</span></span> <span data-ttu-id="44ef3-157">İlk çağıran ile ilgili bilgilere erişmek için arka uç hizmeti `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` özelliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="44ef3-157">To access the information about the initial caller the backend service uses the `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` property.</span></span> <span data-ttu-id="44ef3-158">`Identity`Bir türü olan bir talep arar `Name` .</span><span class="sxs-lookup"><span data-stu-id="44ef3-158">It looks for an `Identity` claim with a type `Name`.</span></span> <span data-ttu-id="44ef3-159">Bu talep, güvenlik belirtecinde bulunan bilgilerden WCF güvenlik altyapısı tarafından otomatik olarak oluşturulur `Username` .</span><span class="sxs-lookup"><span data-stu-id="44ef3-159">This claim is automatically generated by WCF security infrastructure from the information contained in the `Username` security token.</span></span>  
  
## <a name="running-the-sample"></a><span data-ttu-id="44ef3-160">Örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="44ef3-160">Running the sample</span></span>  
 <span data-ttu-id="44ef3-161">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="44ef3-161">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="44ef3-162">İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="44ef3-162">Press ENTER in the client window to shut down the client.</span></span> <span data-ttu-id="44ef3-163">Hizmeti kapatmak için façlade ve arka uç hizmeti konsol penceresinde ENTER tuşuna basabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44ef3-163">You can press ENTER in the façade and backend service console windows to shut down the services.</span></span>  
  
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
  
 <span data-ttu-id="44ef3-164">Güvenilir Faon yıl örneğine dahil olan Setup.bat Batch dosyası, istemci için kimlik doğrulaması yapmak üzere sertifika tabanlı güvenlik gerektiren façlade hizmetini çalıştırmak üzere sunucuyu ilgili sertifikayla yapılandırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="44ef3-164">The Setup.bat batch file included with the Trusted Facade scenario sample enables you to configure the server with a relevant certificate to run the façade service that requires certificate-based security to authenticate itself to the client.</span></span> <span data-ttu-id="44ef3-165">Ayrıntılar için bu konunun sonundaki Kurulum yordamına bakın.</span><span class="sxs-lookup"><span data-stu-id="44ef3-165">See the setup procedure at the end of this topic for details.</span></span>  
  
 <span data-ttu-id="44ef3-166">Aşağıdakiler, toplu iş dosyalarının farklı bölümlerine kısa bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="44ef3-166">The following provides a brief overview of the different sections of the batch files.</span></span>  
  
- <span data-ttu-id="44ef3-167">Sunucu sertifikası oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="44ef3-167">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="44ef3-168">Setup.bat Batch dosyasından aşağıdaki satırlar kullanılacak sunucu sertifikasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="44ef3-168">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span>  
  
    ```console  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     <span data-ttu-id="44ef3-169">`%SERVER_NAME%`Değişken, sunucu adını belirtir; varsayılan değer localhost 'tur.</span><span class="sxs-lookup"><span data-stu-id="44ef3-169">The `%SERVER_NAME%` variable specifies the server name - the default value is localhost.</span></span> <span data-ttu-id="44ef3-170">Sertifika, LocalMachine deposunda depolanır.</span><span class="sxs-lookup"><span data-stu-id="44ef3-170">The certificate is stored in the LocalMachine store.</span></span>  
  
- <span data-ttu-id="44ef3-171">Façlade hizmetinin sertifikasını istemcinin güvenilen sertifika deposuna yükleme.</span><span class="sxs-lookup"><span data-stu-id="44ef3-171">Installing the façade service's certificate into the client's trusted certificate store.</span></span>  
  
     <span data-ttu-id="44ef3-172">Aşağıdaki satır façlade hizmeti sertifikasını istemci güvenilir kişiler deposuna kopyalar.</span><span class="sxs-lookup"><span data-stu-id="44ef3-172">The following line copies the façade service's certificate into the client trusted people store.</span></span> <span data-ttu-id="44ef3-173">Makecert.exe tarafından oluşturulan sertifikalara istemci sistemi tarafından örtük olarak güvenilmediğinden Bu adım gereklidir.</span><span class="sxs-lookup"><span data-stu-id="44ef3-173">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="44ef3-174">İstemci tarafından güvenilen kök sertifikada kök sertifikaya sahip bir sertifikanız zaten varsa (örneğin, Microsoft tarafından verilen bir sertifika), istemci sertifikası deposunu sunucu sertifikasıyla doldurmanın bu adımı gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="44ef3-174">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```console  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="44ef3-175">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="44ef3-175">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="44ef3-176">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="44ef3-176">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="44ef3-177">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="44ef3-177">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="44ef3-178">Örneği aynı makinede çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="44ef3-178">To run the sample on the same machine</span></span>  
  
1. <span data-ttu-id="44ef3-179">Yolun Makecert.exe bulunduğu klasörü içerdiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="44ef3-179">Ensure that the path includes the folder where Makecert.exe is located.</span></span>  
  
2. <span data-ttu-id="44ef3-180">Örnek yüklemesi klasöründen Setup.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="44ef3-180">Run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="44ef3-181">Bu, örneği çalıştırmak için gereken tüm sertifikaları kurar.</span><span class="sxs-lookup"><span data-stu-id="44ef3-181">This installs all the certificates required for running the sample.</span></span>  
  
3. <span data-ttu-id="44ef3-182">\BackendService\bin dizininden BackendService.exe ayrı bir konsol penceresinde başlatın</span><span class="sxs-lookup"><span data-stu-id="44ef3-182">Launch the BackendService.exe from \BackendService\bin directory in a separate console window</span></span>  
  
4. <span data-ttu-id="44ef3-183">Ayrı bir konsol penceresinde \FacadeService\bin dizininden FacadeService.exe başlatın</span><span class="sxs-lookup"><span data-stu-id="44ef3-183">Launch the FacadeService.exe from \FacadeService\bin directory in a separate console window</span></span>  
  
5. <span data-ttu-id="44ef3-184">\Client\bin. 'den başlatma Client.exe</span><span class="sxs-lookup"><span data-stu-id="44ef3-184">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="44ef3-185">İstemci etkinliği istemci konsol uygulamasında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="44ef3-185">Client activity is displayed on the client console application.</span></span>  
  
6. <span data-ttu-id="44ef3-186">İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="44ef3-186">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="44ef3-187">Örnekten sonra temizlemek için</span><span class="sxs-lookup"><span data-stu-id="44ef3-187">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="44ef3-188">Örneği çalıştırmayı bitirdikten sonra Samples klasöründe Cleanup.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="44ef3-188">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="44ef3-189">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="44ef3-189">The samples may already be installed on your machine.</span></span> <span data-ttu-id="44ef3-190">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="44ef3-190">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="44ef3-191">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="44ef3-191">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="44ef3-192">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="44ef3-192">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\TrustedFacade`
