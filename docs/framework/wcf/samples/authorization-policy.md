---
title: Yetkilendirme İlkesi
ms.date: 03/30/2017
ms.assetid: 1db325ec-85be-47d0-8b6e-3ba2fdf3dda0
ms.openlocfilehash: 36ec1029c8fed57957eb463808de442e74abdf9c
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463942"
---
# <a name="authorization-policy"></a><span data-ttu-id="bf163-102">Yetkilendirme İlkesi</span><span class="sxs-lookup"><span data-stu-id="bf163-102">Authorization Policy</span></span>

<span data-ttu-id="bf163-103">Bu örnek, özel talep yetkilendirme ilkesi nin ve ilişkili bir özel hizmet yetkilendirme yöneticisinin nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="bf163-103">This sample demonstrates how to implement a custom claim authorization policy and an associated custom service authorization manager.</span></span> <span data-ttu-id="bf163-104">Bu, hizmet işlemlerine talep tabanlı erişim denetimleri yaptığında ve erişim denetimlerinden önce arayana belirli haklar verdiğinde yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="bf163-104">This is useful when the service makes claim-based access checks to service operations and prior to the access checks, grants the caller certain rights.</span></span> <span data-ttu-id="bf163-105">Bu örnek, hem talep ekleme işlemini hem de kesinleşen talep kümesine karşı bir erişim denetimi yapma işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="bf163-105">This sample shows both the process of adding claims as well as the process for doing an access check against the finalized set of claims.</span></span> <span data-ttu-id="bf163-106">İstemci ve sunucu arasındaki tüm uygulama iletileri imzalanır ve şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="bf163-106">All application messages between the client and server are signed and encrypted.</span></span> <span data-ttu-id="bf163-107">Varsayılan `wsHttpBinding` olarak bağlama ile, istemci tarafından sağlanan bir kullanıcı adı ve parola geçerli bir Windows NT hesabına oturum açmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bf163-107">By default with the `wsHttpBinding` binding, a username and password supplied by the client are used to logon to a valid Windows NT account.</span></span> <span data-ttu-id="bf163-108">Bu örnek, istemcinin kimliğini <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> doğrulamak için bir özelin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="bf163-108">This sample demonstrates how to utilize a custom <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> to authenticate the client.</span></span> <span data-ttu-id="bf163-109">Ayrıca bu örnek, X.509 sertifikası kullanarak hizmete kimlik doğrulayan istemciyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="bf163-109">In addition this sample shows the client authenticating to the service using an X.509 certificate.</span></span> <span data-ttu-id="bf163-110">Bu örnek, aralarında <xref:System.IdentityModel.Policy.IAuthorizationPolicy> <xref:System.ServiceModel.ServiceAuthorizationManager>belirli kullanıcılar için hizmetin belirli yöntemlerine erişim sağlayan bir uygulama gösterir.</span><span class="sxs-lookup"><span data-stu-id="bf163-110">This sample shows an implementation of <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and <xref:System.ServiceModel.ServiceAuthorizationManager>, which between them grant access to specific methods of the service for specific users.</span></span> <span data-ttu-id="bf163-111">Bu örnek İleti [Güvenliği Kullanıcı Adını](../../../../docs/framework/wcf/samples/message-security-user-name.md)temel alıyor, ancak çağrılmadan <xref:System.ServiceModel.ServiceAuthorizationManager> önce bir talep dönüştürmesinin nasıl gerçekleştiriltigerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="bf163-111">This sample is based on the [Message Security User Name](../../../../docs/framework/wcf/samples/message-security-user-name.md), but demonstrates how to perform a claim transformation prior to the <xref:System.ServiceModel.ServiceAuthorizationManager> being called.</span></span>

> [!NOTE]
> <span data-ttu-id="bf163-112">Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="bf163-112">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

 <span data-ttu-id="bf163-113">Özetle, bu örnek nasıl gösterir:</span><span class="sxs-lookup"><span data-stu-id="bf163-113">In summary, this sample demonstrates how:</span></span>

- <span data-ttu-id="bf163-114">İstemcinin kimliği bir kullanıcı adı parolası kullanılarak doğrulanabilir.</span><span class="sxs-lookup"><span data-stu-id="bf163-114">The client can be authenticated using a user name-password.</span></span>

- <span data-ttu-id="bf163-115">İstemci X.509 sertifikası kullanılarak kimlik doğrulanabilir.</span><span class="sxs-lookup"><span data-stu-id="bf163-115">The client can be authenticated using an X.509 certificate.</span></span>

- <span data-ttu-id="bf163-116">Sunucu, istemci kimlik bilgilerini özel `UsernamePassword` bir doğrulayıcıya karşı doğrular.</span><span class="sxs-lookup"><span data-stu-id="bf163-116">The server validates the client credentials against a custom `UsernamePassword` validator.</span></span>

- <span data-ttu-id="bf163-117">Sunucu, sunucunun X.509 sertifikası kullanılarak kimlik doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="bf163-117">The server is authenticated using the server's X.509 certificate.</span></span>

- <span data-ttu-id="bf163-118">Sunucu, hizmetteki belirli yöntemlere erişimi denetlemek için kullanabilir. <xref:System.ServiceModel.ServiceAuthorizationManager></span><span class="sxs-lookup"><span data-stu-id="bf163-118">The server can use <xref:System.ServiceModel.ServiceAuthorizationManager> to control access to certain methods in the service.</span></span>

- <span data-ttu-id="bf163-119">Nasıl uygulanır. <xref:System.IdentityModel.Policy.IAuthorizationPolicy></span><span class="sxs-lookup"><span data-stu-id="bf163-119">How to implement <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span></span>

<span data-ttu-id="bf163-120">Hizmet, uygulama dosyası App.config kullanılarak tanımlanan hizmetle iletişim kurmak için iki uç noktayı ortaya çıkarır. Her bitiş noktası bir adres, bir bağlama ve sözleşmeden oluşur.</span><span class="sxs-lookup"><span data-stu-id="bf163-120">The service exposes two endpoints for communicating with the service, defined using the configuration file App.config. Each endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="bf163-121">Bir bağlama, WS-Security `wsHttpBinding` ve istemci kullanıcı adı kimlik doğrulaması kullanan standart bir bağlama ile yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="bf163-121">One binding is configured with a standard `wsHttpBinding` binding that uses WS-Security and client username authentication.</span></span> <span data-ttu-id="bf163-122">Diğer bağlama WS-Security ve `wsHttpBinding` istemci sertifikası kimlik doğrulaması kullanan standart bir bağlama ile yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="bf163-122">The other binding is configured with a standard `wsHttpBinding` binding that uses WS-Security and client certificate authentication.</span></span> <span data-ttu-id="bf163-123">[ \<Davranış>,](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) kullanıcı kimlik bilgilerinin hizmet kimlik doğrulaması için kullanılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="bf163-123">The [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) specifies that the user credentials are to be used for service authentication.</span></span> <span data-ttu-id="bf163-124">Sunucu sertifikası, `SubjectName` `findValue` [ \<hizmetSertifikası>'ndeki ](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)öznitelikile özellik için aynı değeri içermelidir.</span><span class="sxs-lookup"><span data-stu-id="bf163-124">The server certificate must contain the same value for the `SubjectName` property as the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span></span>

```xml
<system.serviceModel>
  <services>
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <host>
        <baseAddresses>
          <!-- configure base address provided by host -->
          <add baseAddress ="http://localhost:8001/servicemodelsamples/service"/>
        </baseAddresses>
      </host>
      <!-- use base address provided by host, provide two endpoints -->
      <endpoint address="username"
                binding="wsHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
      <endpoint address="certificate"
                binding="wsHttpBinding"
                bindingConfiguration="Binding2"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>

  <bindings>
    <wsHttpBinding>
      <!-- Username binding -->
      <binding name="Binding1">
        <security mode="Message">
    <message clientCredentialType="UserName" />
        </security>
      </binding>
      <!-- X509 certificate binding -->
      <binding name="Binding2">
        <security mode="Message">
          <message clientCredentialType="Certificate" />
        </security>
      </binding>
    </wsHttpBinding>
  </bindings>

  <behaviors>
    <serviceBehaviors>
      <behavior name="CalculatorServiceBehavior" >
        <serviceDebug includeExceptionDetailInFaults ="true" />
        <serviceCredentials>
          <!--
          The serviceCredentials behavior allows one to specify a custom validator for username/password combinations.
          -->
          <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.MyCustomUserNameValidator, service" />
          <!--
          The serviceCredentials behavior allows one to specify authentication constraints on client certificates.
          -->
          <clientCertificate>
            <!--
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate
            is in the user's Trusted People store, then it will be trusted without performing a
            validation of the certificate's issuer chain. This setting is used here for convenience so that the
            sample can be run without having to have certificates issued by a certification authority (CA).
            This setting is less secure than the default, ChainTrust. The security implications of this
            setting should be carefully considered before using PeerOrChainTrust in production code.
            -->
            <authentication certificateValidationMode="PeerOrChainTrust" />
          </clientCertificate>
          <!--
          The serviceCredentials behavior allows one to define a service certificate.
          A service certificate is used by a client to authenticate the service and provide message protection.
          This configuration references the "localhost" certificate installed during the setup instructions.
          -->
          <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />
        </serviceCredentials>
        <serviceAuthorization serviceAuthorizationManagerType="Microsoft.ServiceModel.Samples.MyServiceAuthorizationManager, service">
          <!--
          The serviceAuthorization behavior allows one to specify custom authorization policies.
          -->
          <authorizationPolicies>
            <add policyType="Microsoft.ServiceModel.Samples.CustomAuthorizationPolicy.MyAuthorizationPolicy, PolicyLibrary" />
          </authorizationPolicies>
        </serviceAuthorization>
      </behavior>
    </serviceBehaviors>
  </behaviors>

</system.serviceModel>
```

<span data-ttu-id="bf163-125">Her istemci uç nokta yapılandırması bir yapılandırma adı, hizmet bitiş noktası için mutlak bir adres, bağlama ve sözleşme oluşur.</span><span class="sxs-lookup"><span data-stu-id="bf163-125">Each client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="bf163-126">İstemci bağlama, [ \<güvenlik>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) bu durumda belirtildiği gibi uygun `clientCredentialType` güvenlik modu ile ve [ \<>iletide ](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md)belirtildiği gibi yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="bf163-126">The client binding is configured with the appropriate security mode as specified in this case in the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) and `clientCredentialType` as specified in the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md).</span></span>

```xml
<system.serviceModel>

    <client>
      <!-- Username based endpoint -->
      <endpoint name="Username"
            address="http://localhost:8001/servicemodelsamples/service/username"
    binding="wsHttpBinding"
    bindingConfiguration="Binding1"
                behaviorConfiguration="ClientCertificateBehavior"
                contract="Microsoft.ServiceModel.Samples.ICalculator" >
      </endpoint>
      <!-- X509 certificate based endpoint -->
      <endpoint name="Certificate"
                        address="http://localhost:8001/servicemodelsamples/service/certificate"
                binding="wsHttpBinding"
            bindingConfiguration="Binding2"
                behaviorConfiguration="ClientCertificateBehavior"
                contract="Microsoft.ServiceModel.Samples.ICalculator">
      </endpoint>
    </client>

    <bindings>
      <wsHttpBinding>
        <!-- Username binding -->
      <binding name="Binding1">
        <security mode="Message">
          <message clientCredentialType="UserName" />
        </security>
      </binding>
        <!-- X509 certificate binding -->
        <binding name="Binding2">
          <security mode="Message">
            <message clientCredentialType="Certificate" />
          </security>
        </binding>
    </wsHttpBinding>
    </bindings>

    <behaviors>
      <behavior name="ClientCertificateBehavior">
        <clientCredentials>
          <serviceCertificate>
            <!--
            Setting the certificateValidationMode to PeerOrChainTrust
            means that if the certificate
            is in the user's Trusted People store, then it will be
            trusted without performing a
            validation of the certificate's issuer chain. This setting
            is used here for convenience so that the
            sample can be run without having to have certificates
            issued by a certification authority (CA).
            This setting is less secure than the default, ChainTrust.
            The security implications of this
            setting should be carefully considered before using
            PeerOrChainTrust in production code.
            -->
            <authentication certificateValidationMode = "PeerOrChainTrust" />
          </serviceCertificate>
        </clientCredentials>
      </behavior>
    </behaviors>

  </system.serviceModel>
```

<span data-ttu-id="bf163-127">Kullanıcı adı tabanlı bitiş noktası için istemci uygulaması kullanılacak kullanıcı adını ve parolayı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bf163-127">For the user name-based endpoint, the client implementation sets the user name and password to use.</span></span>

```csharp
// Create a client with Username endpoint configuration
CalculatorClient client1 = new CalculatorClient("Username");

client1.ClientCredentials.UserName.UserName = "test1";
client1.ClientCredentials.UserName.Password = "1tset";

try
{
    // Call the Add service operation.
    double value1 = 100.00D;
    double value2 = 15.99D;
    double result = client1.Add(value1, value2);
    Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);
    ...
}
catch (Exception e)
{
    Console.WriteLine("Call failed : {0}", e.Message);
}

client1.Close();
```

<span data-ttu-id="bf163-128">Sertifika tabanlı bitiş noktası için istemci uygulaması istemci sertifikasını kullanacak şekilde ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bf163-128">For the certificate-based endpoint, the client implementation sets the client certificate to use.</span></span>

```csharp
// Create a client with Certificate endpoint configuration
CalculatorClient client2 = new CalculatorClient("Certificate");

client2.ClientCredentials.ClientCertificate.SetCertificate(StoreLocation.CurrentUser, StoreName.My, X509FindType.FindBySubjectName, "test1");

try
{
    // Call the Add service operation.
    double value1 = 100.00D;
    double value2 = 15.99D;
    double result = client2.Add(value1, value2);
    Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);
    ...
}
catch (Exception e)
{
    Console.WriteLine("Call failed : {0}", e.Message);
}

client2.Close();
```

<span data-ttu-id="bf163-129">Bu örnek, <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> kullanıcı adlarını ve parolaları doğrulamak için özel bir kullanır.</span><span class="sxs-lookup"><span data-stu-id="bf163-129">This sample uses a custom <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> to validate user names and passwords.</span></span> <span data-ttu-id="bf163-130">Örnek uygular `MyCustomUserNamePasswordValidator`, <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>türetilmiştir.</span><span class="sxs-lookup"><span data-stu-id="bf163-130">The sample implements `MyCustomUserNamePasswordValidator`, derived from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span></span> <span data-ttu-id="bf163-131">Daha fazla <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> bilgi için ilgili belgelere bakın.</span><span class="sxs-lookup"><span data-stu-id="bf163-131">See the documentation about <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> for more information.</span></span> <span data-ttu-id="bf163-132"><xref:System.IdentityModel.Selectors.UserNamePasswordValidator>Bu özel doğrulayıcı örnek, kullanıcı adının aşağıdaki kodda gösterildiği <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> parolayla eşleştiği kullanıcı adı/parola çiftlerini kabul etme yöntemini uygular.</span><span class="sxs-lookup"><span data-stu-id="bf163-132">For the purposes of demonstrating the integration with the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>, this custom validator sample implements the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method to accept user name/password pairs where the user name matches the password as shown in the following code.</span></span>

```csharp
public class MyCustomUserNamePasswordValidator : UserNamePasswordValidator
{
  // This method validates users. It allows in two users,
  // test1 and test2 with passwords 1tset and 2tset respectively.
  // This code is for illustration purposes only and
  // MUST NOT be used in a production environment because it
  // is NOT secure.
  public override void Validate(string userName, string password)
  {
    if (null == userName || null == password)
    {
      throw new ArgumentNullException();
    }

    if (!(userName == "test1" && password == "1tset") && !(userName == "test2" && password == "2tset"))
    {
      throw new SecurityTokenException("Unknown Username or Password");
    }
  }
}
```

<span data-ttu-id="bf163-133">Geçerlilik hizmeti kodunda uygulandıktan sonra, hizmet barındırıcısı kullanılacak geçerlilik örneği hakkında bilgilendirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="bf163-133">Once the validator is implemented in service code, the service host must be informed about the validator instance to use.</span></span> <span data-ttu-id="bf163-134">Bu, aşağıdaki kod kullanılarak yapılır:</span><span class="sxs-lookup"><span data-stu-id="bf163-134">This is done using the following code:</span></span>

```csharp
Servicehost.Credentials.UserNameAuthentication.UserNamePasswordValidationMode = UserNamePasswordValidationMode.Custom;
serviceHost.Credentials.UserNameAuthentication.CustomUserNamePasswordValidator = new MyCustomUserNamePasswordValidatorProvider();
```

<span data-ttu-id="bf163-135">Veya yapılandırmada aynı şeyi yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="bf163-135">Or you can do the same thing in configuration:</span></span>

```xml
<behavior>
    <serviceCredentials>
      <!--
      The serviceCredentials behavior allows one to specify a custom validator for username/password combinations.
      -->
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.MyCustomUserNameValidator, service" />
    ...
    </serviceCredentials>
</behavior>
```

<span data-ttu-id="bf163-136">Windows Communication Foundation (WCF), erişim denetimleri gerçekleştirmek için zengin bir talep tabanlı model sağlar.</span><span class="sxs-lookup"><span data-stu-id="bf163-136">Windows Communication Foundation (WCF) provides a rich claims-based model for performing access checks.</span></span> <span data-ttu-id="bf163-137">Nesne, <xref:System.ServiceModel.ServiceAuthorizationManager> erişim denetimini gerçekleştirmek ve istemciyle ilişkili taleplerin hizmet yöntemine erişmek için gerekli gereksinimleri karşılayıp karşılamadığını belirlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bf163-137">The <xref:System.ServiceModel.ServiceAuthorizationManager> object is used to perform the access check and determine whether the claims associated with the client satisfy the requirements necessary to access the service method.</span></span>

<span data-ttu-id="bf163-138">Bu örnek, gösteri amacıyla, kullanıcının, <xref:System.ServiceModel.ServiceAuthorizationManager> <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> adı verilmesine izin verilen işlemin Eylem URI değeri `http://example.com/claims/allowedoperation` olan tür iddialarına dayalı yöntemlere erişimini sağlayan yöntemi uygulayan bir uygulama gösterir.</span><span class="sxs-lookup"><span data-stu-id="bf163-138">For the purposes of demonstration, this sample shows an implementation of <xref:System.ServiceModel.ServiceAuthorizationManager> that implements the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method to allow a user's access to methods based on claims of type `http://example.com/claims/allowedoperation` whose value is the Action URI of the operation that is allowed to be called.</span></span>

```csharp
public class MyServiceAuthorizationManager : ServiceAuthorizationManager
{
  protected override bool CheckAccessCore(OperationContext operationContext)
  {
    string action = operationContext.RequestContext.RequestMessage.Headers.Action;
    Console.WriteLine("action: {0}", action);
    foreach(ClaimSet cs in operationContext.ServiceSecurityContext.AuthorizationContext.ClaimSets)
    {
      if ( cs.Issuer == ClaimSet.System )
      {
        foreach (Claim c in cs.FindClaims("http://example.com/claims/allowedoperation", Rights.PossessProperty))
        {
          Console.WriteLine("resource: {0}", c.Resource.ToString());
          if (action == c.Resource.ToString())
            return true;
        }
      }
    }
    return false;
  }
}
```

<span data-ttu-id="bf163-139">Özel uygulama <xref:System.ServiceModel.ServiceAuthorizationManager> uygulandıktan sonra, hizmet ana bilgisayar <xref:System.ServiceModel.ServiceAuthorizationManager> kullanılacak hakkında bilgilendirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="bf163-139">Once the custom <xref:System.ServiceModel.ServiceAuthorizationManager> is implemented, the service host must be informed about the <xref:System.ServiceModel.ServiceAuthorizationManager> to use.</span></span> <span data-ttu-id="bf163-140">Bu, aşağıdaki kodda gösterildiği gibi yapılır.</span><span class="sxs-lookup"><span data-stu-id="bf163-140">This is done as shown in the following code.</span></span>

```xml
<behavior>
    ...
    <serviceAuthorization serviceAuthorizationManagerType="Microsoft.ServiceModel.Samples.MyServiceAuthorizationManager, service">
        ...
    </serviceAuthorization>
</behavior>
```

<span data-ttu-id="bf163-141">Uygulanacak <xref:System.IdentityModel.Policy.IAuthorizationPolicy> birincil yöntem <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="bf163-141">The primary <xref:System.IdentityModel.Policy.IAuthorizationPolicy> method to implement is the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method.</span></span>

```csharp
public class MyAuthorizationPolicy : IAuthorizationPolicy
{
    string id;

    public MyAuthorizationPolicy()
    {
    id =  Guid.NewGuid().ToString();
    }

    public bool Evaluate(EvaluationContext evaluationContext,
                                            ref object state)
    {
        bool bRet = false;
        CustomAuthState customstate = null;

        if (state == null)
        {
            customstate = new CustomAuthState();
            state = customstate;
        }
        else
            customstate = (CustomAuthState)state;
        Console.WriteLine("In Evaluate");
        if (!customstate.ClaimsAdded)
        {
           IList<Claim> claims = new List<Claim>();

           foreach (ClaimSet cs in evaluationContext.ClaimSets)
              foreach (Claim c in cs.FindClaims(ClaimTypes.Name,
                                         Rights.PossessProperty))
                  foreach (string s in
                        GetAllowedOpList(c.Resource.ToString()))
                  {
                       claims.Add(new
               Claim("http://example.com/claims/allowedoperation",
                                    s, Rights.PossessProperty));
                            Console.WriteLine("Claim added {0}", s);
                      }
                   evaluationContext.AddClaimSet(this,
                           new DefaultClaimSet(this.Issuer,claims));
                   customstate.ClaimsAdded = true;
                   bRet = true;
                }
         else
         {
              bRet = true;
         }
         return bRet;
     }
...
}
```

<span data-ttu-id="bf163-142">Önceki kod, yöntemin <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> işlemi etkileyen yeni iddiaların eklenmediğini nasıl denetler ve belirli talepler ekler.</span><span class="sxs-lookup"><span data-stu-id="bf163-142">The previous code shows how the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method checks that no new claims have been added that affect the processing and adds specific claims.</span></span> <span data-ttu-id="bf163-143">İzin verilen talepler, kullanıcının `GetAllowedOpList` gerçekleştirmesine izin verilen belirli bir işlem listesini döndürmek için uygulanan yöntemden elde edilir.</span><span class="sxs-lookup"><span data-stu-id="bf163-143">The claims that are allowed are obtained from the `GetAllowedOpList` method, which is implemented to return a specific list of operations that the user is allowed to perform.</span></span> <span data-ttu-id="bf163-144">Yetkilendirme ilkesi, belirli bir işlem için talepler ekler.</span><span class="sxs-lookup"><span data-stu-id="bf163-144">The authorization policy adds claims for accessing the particular operation.</span></span> <span data-ttu-id="bf163-145">Bu daha sonra <xref:System.ServiceModel.ServiceAuthorizationManager> erişim denetimi kararları gerçekleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bf163-145">This is later used by the <xref:System.ServiceModel.ServiceAuthorizationManager> to perform access check decisions.</span></span>

<span data-ttu-id="bf163-146">Özel uygulama <xref:System.IdentityModel.Policy.IAuthorizationPolicy> uygulandıktan sonra, hizmet ana bilgisayar kullanılacak yetkilendirme ilkeleri hakkında bilgilendirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="bf163-146">Once the custom <xref:System.IdentityModel.Policy.IAuthorizationPolicy> is implemented, the service host must be informed about the authorization policies to use.</span></span>

```xml
<serviceAuthorization>
       <authorizationPolicies>
            <add policyType='Microsoft.ServiceModel.Samples.CustomAuthorizationPolicy.MyAuthorizationPolicy, PolicyLibrary' />
       </authorizationPolicies>
</serviceAuthorization>
```

<span data-ttu-id="bf163-147">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="bf163-147">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="bf163-148">İstemci, Ekle, Çıkarma ve Çoklu yöntemleri başarıyla çağırır ve Böl yöntemini çağırmaya çalışırken "Erişim reddedildi" iletisi alır.</span><span class="sxs-lookup"><span data-stu-id="bf163-148">The client successfully calls the Add, Subtract and Multiple methods and gets an "Access is denied" message when trying to call the Divide method.</span></span> <span data-ttu-id="bf163-149">İstemciyi kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="bf163-149">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="bf163-150">Kurulum Toplu Dosya</span><span class="sxs-lookup"><span data-stu-id="bf163-150">Setup Batch File</span></span>

<span data-ttu-id="bf163-151">Bu örnekte yer alan Setup.bat toplu dosyası, sunucu sertifikası tabanlı güvenlik gerektiren kendi kendine barındırılan bir uygulamayı çalıştırmak için sunucuyu ilgili sertifikalarla yapılandırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="bf163-151">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate-based security.</span></span>

<span data-ttu-id="bf163-152">Aşağıda, toplu iş dosyalarının uygun yapılandırmada çalışacak şekilde değiştirilebilmeleri için farklı bölümlerine kısa bir genel bakış sağlanacaktır:</span><span class="sxs-lookup"><span data-stu-id="bf163-152">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration:</span></span>

- <span data-ttu-id="bf163-153">Sunucu sertifikası oluşturma.</span><span class="sxs-lookup"><span data-stu-id="bf163-153">Creating the server certificate.</span></span>

    <span data-ttu-id="bf163-154">Setup.bat toplu dosyasından aşağıdaki satırlar kullanılacak sunucu sertifikasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bf163-154">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="bf163-155">%SERVER_NAME değişkeni sunucu adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="bf163-155">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="bf163-156">Kendi sunucu adınızı belirtmek için bu değişkeni değiştirin.</span><span class="sxs-lookup"><span data-stu-id="bf163-156">Change this variable to specify your own server name.</span></span> <span data-ttu-id="bf163-157">Varsayılan değer yerel ana bilgisayardır.</span><span class="sxs-lookup"><span data-stu-id="bf163-157">The default value is localhost.</span></span>

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="bf163-158">Sunucu sertifikasını istemcinin güvenilir sertifika deposuna yükleme.</span><span class="sxs-lookup"><span data-stu-id="bf163-158">Installing the server certificate into client's trusted certificate store.</span></span>

    <span data-ttu-id="bf163-159">Setup.bat toplu iş dosyasındaki aşağıdaki satırlar, sunucu sertifikasını istemcigüvenilir kişiler deposuna kopyalar.</span><span class="sxs-lookup"><span data-stu-id="bf163-159">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="bf163-160">Makecert.exe tarafından oluşturulan sertifikalar istemci sistemi tarafından dolaylı olarak güvenilen olmadığından bu adım gereklidir.</span><span class="sxs-lookup"><span data-stu-id="bf163-160">This step is required because certificates that are generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="bf163-161">Zaten istemci güvenilen bir kök sertifikası köklü bir sertifika varsa (örneğin, Microsoft tarafından verilmiş bir sertifika- sunucu sertifikası ile istemci sertifika deposu doldurma bu adım gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="bf163-161">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

- <span data-ttu-id="bf163-162">İstemci sertifikasıoluşturma.</span><span class="sxs-lookup"><span data-stu-id="bf163-162">Creating the client certificate.</span></span>

    <span data-ttu-id="bf163-163">Setup.bat toplu iş dosyasındaki aşağıdaki satırlar kullanılacak istemci sertifikasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bf163-163">The following lines from the Setup.bat batch file create the client certificate to be used.</span></span> <span data-ttu-id="bf163-164">%USER_NAME değişkeni sunucu adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="bf163-164">The %USER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="bf163-165">Bu değer "test1" olarak ayarlanır, çünkü `IAuthorizationPolicy` bu, aradığı addır.</span><span class="sxs-lookup"><span data-stu-id="bf163-165">This value is set to "test1" because this is the name the `IAuthorizationPolicy` looks for.</span></span> <span data-ttu-id="bf163-166">%USER_NAME değerini değiştirirseniz, `IAuthorizationPolicy.Evaluate` yöntemdeki karşılık gelen değeri değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="bf163-166">If you change the value of %USER_NAME% you must change the corresponding value in the `IAuthorizationPolicy.Evaluate` method.</span></span>

    <span data-ttu-id="bf163-167">Sertifika, CurrentUser mağazasının altında Benim (Kişisel) mağazamda depolanır.</span><span class="sxs-lookup"><span data-stu-id="bf163-167">The certificate is stored in My (Personal) store under the CurrentUser store location.</span></span>

    ```bat
    echo ************
    echo making client cert
    echo ************
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="bf163-168">İstemci sertifikasını sunucunun güvenilir sertifika deposuna yükleme.</span><span class="sxs-lookup"><span data-stu-id="bf163-168">Installing the client certificate into server's trusted certificate store.</span></span>

    <span data-ttu-id="bf163-169">Setup.bat toplu iş dosyasındaki aşağıdaki satırlar istemci sertifikasını güvenilir kişiler deposuna kopyalar.</span><span class="sxs-lookup"><span data-stu-id="bf163-169">The following lines in the Setup.bat batch file copy the client certificate into the trusted people store.</span></span> <span data-ttu-id="bf163-170">Makecert.exe tarafından oluşturulan sertifikalar sunucu sistemi tarafından dolaylı olarak güvenilen olmadığından bu adım gereklidir.</span><span class="sxs-lookup"><span data-stu-id="bf163-170">This step is required because certificates that are generated by Makecert.exe are not implicitly trusted by the server system.</span></span> <span data-ttu-id="bf163-171">Zaten güvenilir bir kök sertifikaya dayanan bir sertifikanız varsa (örneğin, Microsoft tarafından verilmiş bir sertifika- sunucu sertifikası deposunu istemci sertifikasıyla doldurma adımı gerekmez.</span><span class="sxs-lookup"><span data-stu-id="bf163-171">If you already have a certificate that is rooted in a trusted root certificate—for example, a Microsoft issued certificate—this step of populating the server certificate store with the client certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
    ```

### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="bf163-172">Örneği ayarlamak ve oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="bf163-172">To set up and build the sample</span></span>

1. <span data-ttu-id="bf163-173">Çözümü oluşturmak için, Windows [Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="bf163-173">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

2. <span data-ttu-id="bf163-174">Örneği tek veya bilgisayar lar arası yapılandırmada çalıştırmak için aşağıdaki yönergeleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="bf163-174">To run the sample in a single- or cross-computer configuration, use the following instructions.</span></span>

> [!NOTE]
> <span data-ttu-id="bf163-175">Bu örnek için yapılandırmayı yeniden oluşturmak için Svcutil.exe kullanıyorsanız, istemci yapılandırmasındaki uç nokta adını istemci koduyla eşleşecek şekilde değiştirdiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="bf163-175">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>

### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="bf163-176">Örneği aynı bilgisayarda çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="bf163-176">To run the sample on the same computer</span></span>

1. <span data-ttu-id="bf163-177">Yönetici ayrıcalıklarıyla Visual Studio için Geliştirici Komut Komut Ustem'i açın ve örnek yükleme klasöründen *Setup.bat* çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="bf163-177">Open Developer Command Prompt for Visual Studio with administrator privileges and run *Setup.bat* from the sample install folder.</span></span> <span data-ttu-id="bf163-178">Bu, örneği çalıştırmak için gereken tüm sertifikaları yükler.</span><span class="sxs-lookup"><span data-stu-id="bf163-178">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="bf163-179">Setup.bat toplu dosyası Visual Studio için Geliştirici Komut Komut Istem'den çalıştırılacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="bf163-179">The Setup.bat batch file is designed to be run from Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="bf163-180">Visual Studio için Geliştirici Komut İstemi'nde ayarlanan PATH ortamı değişkeni, *Setup.bat* komut dosyasının gerektirdiği yürütülebilir leri içeren dizine işaret eder.</span><span class="sxs-lookup"><span data-stu-id="bf163-180">The PATH environment variable set within Developer Command Prompt for Visual Studio points to the directory that contains executables required by the *Setup.bat* script.</span></span>

1. <span data-ttu-id="bf163-181">Service.exe'yi *service\bin'den*başlat.</span><span class="sxs-lookup"><span data-stu-id="bf163-181">Launch Service.exe from *service\bin*.</span></span>

1. <span data-ttu-id="bf163-182">*\client\bin'den*Client.exe'yi başlatın.</span><span class="sxs-lookup"><span data-stu-id="bf163-182">Launch Client.exe from *\client\bin*.</span></span> <span data-ttu-id="bf163-183">İstemci etkinliği istemci konsoluygulamasında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="bf163-183">Client activity is displayed on the client console application.</span></span>

<span data-ttu-id="bf163-184">İstemci ve hizmet iletişim kuramazsa, [WCF Örnekleri için Sorun Giderme İpuçları'na](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))bakın.</span><span class="sxs-lookup"><span data-stu-id="bf163-184">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>

### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="bf163-185">Örneği bilgisayarlarda çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="bf163-185">To run the sample across computers</span></span>

1. <span data-ttu-id="bf163-186">Hizmet bilgisayarında bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="bf163-186">Create a directory on the service computer.</span></span>

2. <span data-ttu-id="bf163-187">Hizmet programı dosyalarını *\service\bin'den* hizmet bilgisayarındaki dizine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="bf163-187">Copy the service program files from *\service\bin* to the directory on the service computer.</span></span> <span data-ttu-id="bf163-188">Ayrıca Setup.bat, Cleanup.bat, GetComputerName.vbs ve ImportClientCert.bat dosyalarını servis bilgisayarına kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="bf163-188">Also copy the Setup.bat, Cleanup.bat, GetComputerName.vbs and ImportClientCert.bat files to the service computer.</span></span>

3. <span data-ttu-id="bf163-189">İstemci ikilileri için istemci bilgisayarında bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="bf163-189">Create a directory on the client computer for the client binaries.</span></span>

4. <span data-ttu-id="bf163-190">İstemci programı dosyalarını istemci bilgisayarındaki istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="bf163-190">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="bf163-191">Ayrıca Setup.bat, Cleanup.bat ve ImportServiceCert.bat dosyalarını istemciye kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="bf163-191">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>

5. <span data-ttu-id="bf163-192">Sunucuda, Yönetici `setup.bat service` ayrıcalıkları ile açılan Visual Studio için Geliştirici Komut Komut Ustem'de çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="bf163-192">On the server, run `setup.bat service` in Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>

    <span data-ttu-id="bf163-193">Bağımsız değişkenle birlikte çalışmak, `setup.bat` bilgisayarın tam nitelikli etki alanı adı içeren bir hizmet sertifikası oluşturur ve hizmet sertifikasını *Service.cer*adlı bir dosyaya aktarın. `service`</span><span class="sxs-lookup"><span data-stu-id="bf163-193">Running `setup.bat` with the `service` argument creates a service certificate with the fully qualified domain name of the computer, and exports the service certificate to a file named *Service.cer*.</span></span>

6. <span data-ttu-id="bf163-194">Bilgisayarın tam nitelikli alan adı ile aynı olan yeni `findValue` sertifika adını [ \<(serviceCertificate>'daki ](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)öznitelikte) yansıtacak şekilde *Service.exe.config'i* edin.</span><span class="sxs-lookup"><span data-stu-id="bf163-194">Edit *Service.exe.config* to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully qualified domain name of the computer.</span></span> <span data-ttu-id="bf163-195">Ayrıca, hizmet>/\<baseAddresses> öğesindeki **bilgisayar adını** localhost'tan hizmet bilgisayarınızın tam nitelikli adına değiştirin. \<</span><span class="sxs-lookup"><span data-stu-id="bf163-195">Also change the **computername** in the \<service>/\<baseAddresses> element from localhost to the fully qualified name of your service computer.</span></span>

7. <span data-ttu-id="bf163-196">*Service.cer* dosyasını servis dizininden istemci bilgisayarındaki istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="bf163-196">Copy the *Service.cer* file from the service directory to the client directory on the client computer.</span></span>

8. <span data-ttu-id="bf163-197">İstemci de, Yönetici ayrıcalıkları ile açılan Visual Studio için Geliştirici Komut Komut Ustem'de çalıştırın. `setup.bat client`</span><span class="sxs-lookup"><span data-stu-id="bf163-197">On the client, run `setup.bat client` in Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>

    <span data-ttu-id="bf163-198">Bağımsız değişkenle birlikte çalışmak `setup.bat` **test1** adında bir istemci sertifikası oluşturur ve istemci sertifikasını *Client.cer*adlı bir dosyaya aktarın. `client`</span><span class="sxs-lookup"><span data-stu-id="bf163-198">Running `setup.bat` with the `client` argument creates a client certificate named **test1** and exports the client certificate to a file named *Client.cer*.</span></span>

9. <span data-ttu-id="bf163-199">İstemci bilgisayarındaki *Client.exe.config* dosyasında, hizmetinyeni adresiyle eşleşecek şekilde bitiş noktasının adres değerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="bf163-199">In the *Client.exe.config* file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="bf163-200">Bunu, **localhost'u** sunucunun tam nitelikli etki alanı adı ile değiştirerek yapın.</span><span class="sxs-lookup"><span data-stu-id="bf163-200">Do this by replacing **localhost** with the fully qualified domain name of the server.</span></span>

10. <span data-ttu-id="bf163-201">Client.cer dosyasını istemci dizininden sunucudaki servis dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="bf163-201">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>

11. <span data-ttu-id="bf163-202">İstemci de, Yönetici ayrıcalıkları ile açılan Visual Studio için Geliştirici Komut Komut Ustem'de *ImportServiceCert.bat* çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="bf163-202">On the client, run *ImportServiceCert.bat* in Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>

    <span data-ttu-id="bf163-203">Bu, hizmet sertifikasını Service.cer dosyasından **CurrentUser - Trusted People** deposuna aktarabilir.</span><span class="sxs-lookup"><span data-stu-id="bf163-203">This imports the service certificate from the Service.cer file into the **CurrentUser - TrustedPeople** store.</span></span>

12. <span data-ttu-id="bf163-204">Sunucuda, Yönetici ayrıcalıklarıyla açılan Visual Studio için Geliştirici Komut Komut Ustem'inde *ImportClientCert.bat* çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="bf163-204">On the server, run *ImportClientCert.bat* in Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>

    <span data-ttu-id="bf163-205">Bu, istemci sertifikasını Client.cer dosyasından **LocalMachine - Trusted People** deposuna aktarın.</span><span class="sxs-lookup"><span data-stu-id="bf163-205">This imports the client certificate from the Client.cer file into the **LocalMachine - TrustedPeople** store.</span></span>

13. <span data-ttu-id="bf163-206">Sunucu bilgisayarında Service.exe komut istemi penceresinden başlatın.</span><span class="sxs-lookup"><span data-stu-id="bf163-206">On the server computer, launch Service.exe from the command prompt window.</span></span>

14. <span data-ttu-id="bf163-207">İstemci bilgisayarında, komut istemi penceresinden Client.exe'yi başlatın.</span><span class="sxs-lookup"><span data-stu-id="bf163-207">On the client computer, launch Client.exe from a command prompt window.</span></span>

    <span data-ttu-id="bf163-208">İstemci ve hizmet iletişim kuramazsa, [WCF Örnekleri için Sorun Giderme İpuçları'na](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))bakın.</span><span class="sxs-lookup"><span data-stu-id="bf163-208">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>

### <a name="clean-up-after-the-sample"></a><span data-ttu-id="bf163-209">Örnekten sonra temizleme</span><span class="sxs-lookup"><span data-stu-id="bf163-209">Clean up after the sample</span></span>

<span data-ttu-id="bf163-210">Örnekten sonra temizlemek için, örneği çalıştırmayı bitirdiğinizde örnekler klasöründe *Cleanup.bat* çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="bf163-210">To clean up after the sample, run *Cleanup.bat* in the samples folder when you have finished running the sample.</span></span> <span data-ttu-id="bf163-211">Bu, sunucu ve istemci sertifikalarını sertifika deposundan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="bf163-211">This removes the server and client certificates from the certificate store.</span></span>

> [!NOTE]
> <span data-ttu-id="bf163-212">Bu komut dosyası, bu örneği bilgisayarlar da çalıştırırken istemcideki hizmet sertifikalarını kaldırmaz.</span><span class="sxs-lookup"><span data-stu-id="bf163-212">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="bf163-213">Bilgisayarlarda sertifika kullanan WCF örnekleri çalıştırdıysanız, CurrentUser - Trusted People mağazasında yüklenen hizmet sertifikalarını temizlediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="bf163-213">If you have run WCF samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="bf163-214">Bunu yapmak için aşağıdaki komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="bf163-214">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>
