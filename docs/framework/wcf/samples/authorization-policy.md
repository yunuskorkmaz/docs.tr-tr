---
title: Yetkilendirme İlkesi
ms.date: 03/30/2017
ms.assetid: 1db325ec-85be-47d0-8b6e-3ba2fdf3dda0
ms.openlocfilehash: 5b93f7e05261d9770650335160ddb56404aed94d
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84585512"
---
# <a name="authorization-policy"></a><span data-ttu-id="9f701-102">Yetkilendirme İlkesi</span><span class="sxs-lookup"><span data-stu-id="9f701-102">Authorization Policy</span></span>

<span data-ttu-id="9f701-103">Bu örnek, bir özel talep yetkilendirme ilkesinin ve ilişkili bir özel hizmet Yetkilendirme yöneticisinin nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9f701-103">This sample demonstrates how to implement a custom claim authorization policy and an associated custom service authorization manager.</span></span> <span data-ttu-id="9f701-104">Hizmet, hizmet işlemlerine talep tabanlı erişim denetimleri yaptığında ve erişim denetimlerinden önce, çağırana belirli haklar verdiğinde yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="9f701-104">This is useful when the service makes claim-based access checks to service operations and prior to the access checks, grants the caller certain rights.</span></span> <span data-ttu-id="9f701-105">Bu örnek, hem talep ekleme sürecini hem de son talep kümesinde erişim denetimi yapma işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="9f701-105">This sample shows both the process of adding claims as well as the process for doing an access check against the finalized set of claims.</span></span> <span data-ttu-id="9f701-106">İstemci ve sunucu arasındaki tüm uygulama iletileri imzalanır ve şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="9f701-106">All application messages between the client and server are signed and encrypted.</span></span> <span data-ttu-id="9f701-107">Varsayılan olarak `wsHttpBinding` , bağlama ile, istemci tarafından sağlanan bir Kullanıcı adı ve parola, geçerli bir WINDOWS NT hesabında oturum açmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9f701-107">By default with the `wsHttpBinding` binding, a username and password supplied by the client are used to logon to a valid Windows NT account.</span></span> <span data-ttu-id="9f701-108">Bu örnek <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> , istemcinin kimliğini doğrulamak için bir özel nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="9f701-108">This sample demonstrates how to utilize a custom <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> to authenticate the client.</span></span> <span data-ttu-id="9f701-109">Buna ek olarak, bir X. 509.440 sertifikası kullanarak hizmette kimlik doğrulaması yapan istemciyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="9f701-109">In addition this sample shows the client authenticating to the service using an X.509 certificate.</span></span> <span data-ttu-id="9f701-110">Bu örnek, ve ' nin bir uygulamasını gösterir <xref:System.IdentityModel.Policy.IAuthorizationPolicy> ve bu <xref:System.ServiceModel.ServiceAuthorizationManager> , belirli kullanıcılar için hizmetin belirli yöntemlerine erişim izni verir.</span><span class="sxs-lookup"><span data-stu-id="9f701-110">This sample shows an implementation of <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and <xref:System.ServiceModel.ServiceAuthorizationManager>, which between them grant access to specific methods of the service for specific users.</span></span> <span data-ttu-id="9f701-111">Bu örnek, [Ileti güvenliği Kullanıcı adına](message-security-user-name.md)dayalıdır, ancak çağrılmadan önce bir talep dönüşümünün nasıl gerçekleştirileceğini gösterir <xref:System.ServiceModel.ServiceAuthorizationManager> .</span><span class="sxs-lookup"><span data-stu-id="9f701-111">This sample is based on the [Message Security User Name](message-security-user-name.md), but demonstrates how to perform a claim transformation prior to the <xref:System.ServiceModel.ServiceAuthorizationManager> being called.</span></span>

> [!NOTE]
> <span data-ttu-id="9f701-112">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="9f701-112">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

 <span data-ttu-id="9f701-113">Özet bölümünde bu örnek şunları gösterir:</span><span class="sxs-lookup"><span data-stu-id="9f701-113">In summary, this sample demonstrates how:</span></span>

- <span data-ttu-id="9f701-114">İstemci, bir Kullanıcı adı-parolası kullanılarak kimlik doğrulaması yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="9f701-114">The client can be authenticated using a user name-password.</span></span>

- <span data-ttu-id="9f701-115">İstemcinin kimliği bir X. 509.440 sertifikası kullanılarak yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="9f701-115">The client can be authenticated using an X.509 certificate.</span></span>

- <span data-ttu-id="9f701-116">Sunucu, istemci kimlik bilgilerini özel bir doğrulayıcı ile doğrular `UsernamePassword` .</span><span class="sxs-lookup"><span data-stu-id="9f701-116">The server validates the client credentials against a custom `UsernamePassword` validator.</span></span>

- <span data-ttu-id="9f701-117">Sunucunun sunucu X. 509.440 sertifikası kullanılarak kimlik doğrulaması yapılır.</span><span class="sxs-lookup"><span data-stu-id="9f701-117">The server is authenticated using the server's X.509 certificate.</span></span>

- <span data-ttu-id="9f701-118">Sunucu, <xref:System.ServiceModel.ServiceAuthorizationManager> hizmette belirli yöntemlere erişimi denetlemek için kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="9f701-118">The server can use <xref:System.ServiceModel.ServiceAuthorizationManager> to control access to certain methods in the service.</span></span>

- <span data-ttu-id="9f701-119">Nasıl <xref:System.IdentityModel.Policy.IAuthorizationPolicy> uygulanır?</span><span class="sxs-lookup"><span data-stu-id="9f701-119">How to implement <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span></span>

<span data-ttu-id="9f701-120">Hizmet, App. config yapılandırma dosyası kullanılarak tanımlanan hizmetle iletişim kurmak için iki uç nokta sunar. Her uç nokta bir adres, bağlama ve bir anlaşmada oluşur.</span><span class="sxs-lookup"><span data-stu-id="9f701-120">The service exposes two endpoints for communicating with the service, defined using the configuration file App.config. Each endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="9f701-121">Bir bağlama, `wsHttpBinding` WS-Security ve istemci Kullanıcı adı kimlik doğrulaması kullanan standart bir bağlama ile yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="9f701-121">One binding is configured with a standard `wsHttpBinding` binding that uses WS-Security and client username authentication.</span></span> <span data-ttu-id="9f701-122">Diğer bağlama, `wsHttpBinding` WS-Security ve istemci sertifikası kimlik doğrulaması kullanan standart bir bağlama ile yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="9f701-122">The other binding is configured with a standard `wsHttpBinding` binding that uses WS-Security and client certificate authentication.</span></span> <span data-ttu-id="9f701-123">, [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) Kullanıcı kimlik bilgilerinin hizmet kimlik doğrulaması için kullanılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="9f701-123">The [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) specifies that the user credentials are to be used for service authentication.</span></span> <span data-ttu-id="9f701-124">Sunucu sertifikası `SubjectName` , özelliği için içindeki özniteliğiyle aynı değeri içermelidir `findValue` [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) .</span><span class="sxs-lookup"><span data-stu-id="9f701-124">The server certificate must contain the same value for the `SubjectName` property as the `findValue` attribute in the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span></span>

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

<span data-ttu-id="9f701-125">Her istemci uç noktası yapılandırması, bir yapılandırma adından, hizmet uç noktası için mutlak bir adresten, bağlamaya ve sözleşmeyle oluşur.</span><span class="sxs-lookup"><span data-stu-id="9f701-125">Each client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="9f701-126">İstemci bağlama, ' de belirtildiği gibi, ve ' de belirtildiği gibi uygun güvenlik moduyla yapılandırılır [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md) `clientCredentialType` [\<message>](../../configure-apps/file-schema/wcf/message-of-wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="9f701-126">The client binding is configured with the appropriate security mode as specified in this case in the [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md) and `clientCredentialType` as specified in the [\<message>](../../configure-apps/file-schema/wcf/message-of-wshttpbinding.md).</span></span>

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

<span data-ttu-id="9f701-127">Kullanıcı adı tabanlı uç nokta için, istemci uygulama kullanılacak kullanıcı adını ve parolayı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9f701-127">For the user name-based endpoint, the client implementation sets the user name and password to use.</span></span>

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

<span data-ttu-id="9f701-128">Sertifika tabanlı uç nokta için istemci uygulama, kullanılacak istemci sertifikasını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9f701-128">For the certificate-based endpoint, the client implementation sets the client certificate to use.</span></span>

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

<span data-ttu-id="9f701-129">Bu örnek <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> , Kullanıcı adlarını ve parolalarını doğrulamak için özel bir kullanır.</span><span class="sxs-lookup"><span data-stu-id="9f701-129">This sample uses a custom <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> to validate user names and passwords.</span></span> <span data-ttu-id="9f701-130">Örnek `MyCustomUserNamePasswordValidator` , öğesinden türetilir <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> .</span><span class="sxs-lookup"><span data-stu-id="9f701-130">The sample implements `MyCustomUserNamePasswordValidator`, derived from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span></span> <span data-ttu-id="9f701-131"><xref:System.IdentityModel.Selectors.UserNamePasswordValidator>Daha fazla bilgi için belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="9f701-131">See the documentation about <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> for more information.</span></span> <span data-ttu-id="9f701-132">İle tümleştirmeyi gösterme amaçları doğrultusunda <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> , bu özel Doğrulayıcı örneği, <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> aşağıdaki kodda gösterildiği gibi kullanıcı adının parolayla eşleştiği Kullanıcı adı/parola çiftlerini kabul etmek için yöntemini uygular.</span><span class="sxs-lookup"><span data-stu-id="9f701-132">For the purposes of demonstrating the integration with the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>, this custom validator sample implements the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method to accept user name/password pairs where the user name matches the password as shown in the following code.</span></span>

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

<span data-ttu-id="9f701-133">Doğrulayıcı hizmet koduna uygulandıktan sonra, hizmet ana bilgisayarının kullanılacak Doğrulayıcı örneği hakkında bilgilendirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="9f701-133">Once the validator is implemented in service code, the service host must be informed about the validator instance to use.</span></span> <span data-ttu-id="9f701-134">Bu, aşağıdaki kod kullanılarak yapılır:</span><span class="sxs-lookup"><span data-stu-id="9f701-134">This is done using the following code:</span></span>

```csharp
Servicehost.Credentials.UserNameAuthentication.UserNamePasswordValidationMode = UserNamePasswordValidationMode.Custom;
serviceHost.Credentials.UserNameAuthentication.CustomUserNamePasswordValidator = new MyCustomUserNamePasswordValidatorProvider();
```

<span data-ttu-id="9f701-135">Ya da yapılandırmada aynı şeyi yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9f701-135">Or you can do the same thing in configuration:</span></span>

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

<span data-ttu-id="9f701-136">Windows Communication Foundation (WCF), erişim denetimleri gerçekleştirmek için zengin bir talep tabanlı model sağlar.</span><span class="sxs-lookup"><span data-stu-id="9f701-136">Windows Communication Foundation (WCF) provides a rich claims-based model for performing access checks.</span></span> <span data-ttu-id="9f701-137"><xref:System.ServiceModel.ServiceAuthorizationManager>Nesnesi, erişim denetimini gerçekleştirmek ve istemciyle ilişkili taleplerin hizmet yöntemine erişmek için gereken gereksinimleri karşılayıp karşılamadığını tespit etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9f701-137">The <xref:System.ServiceModel.ServiceAuthorizationManager> object is used to perform the access check and determine whether the claims associated with the client satisfy the requirements necessary to access the service method.</span></span>

<span data-ttu-id="9f701-138">Bu örnek, gösterim amaçları doğrultusunda, bir <xref:System.ServiceModel.ServiceAuthorizationManager> <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> kullanıcının, `http://example.com/claims/allowedoperation` değeri, çağrılmasına izin verilen işlemin işlem URI 'si olan türdeki taleplere göre yöntemlere erişimine izin vermek için metodunu uygulayan uygulamasının bir uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9f701-138">For the purposes of demonstration, this sample shows an implementation of <xref:System.ServiceModel.ServiceAuthorizationManager> that implements the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method to allow a user's access to methods based on claims of type `http://example.com/claims/allowedoperation` whose value is the Action URI of the operation that is allowed to be called.</span></span>

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

<span data-ttu-id="9f701-139">Özel uygulandıktan sonra <xref:System.ServiceModel.ServiceAuthorizationManager> , hizmet ana bilgisayarının kullanım hakkında bilgilendirilmesi gerekir <xref:System.ServiceModel.ServiceAuthorizationManager> .</span><span class="sxs-lookup"><span data-stu-id="9f701-139">Once the custom <xref:System.ServiceModel.ServiceAuthorizationManager> is implemented, the service host must be informed about the <xref:System.ServiceModel.ServiceAuthorizationManager> to use.</span></span> <span data-ttu-id="9f701-140">Bu, aşağıdaki kodda gösterildiği gibi yapılır.</span><span class="sxs-lookup"><span data-stu-id="9f701-140">This is done as shown in the following code.</span></span>

```xml
<behavior>
    ...
    <serviceAuthorization serviceAuthorizationManagerType="Microsoft.ServiceModel.Samples.MyServiceAuthorizationManager, service">
        ...
    </serviceAuthorization>
</behavior>
```

<span data-ttu-id="9f701-141">Uygulanacak birincil <xref:System.IdentityModel.Policy.IAuthorizationPolicy> Yöntem <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="9f701-141">The primary <xref:System.IdentityModel.Policy.IAuthorizationPolicy> method to implement is the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method.</span></span>

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

<span data-ttu-id="9f701-142">Önceki kod, <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> yönteminin işlemeyi etkileyen ve belirli talepler ekleyen hiçbir yeni talep bulunmadığını denetlemesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="9f701-142">The previous code shows how the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method checks that no new claims have been added that affect the processing and adds specific claims.</span></span> <span data-ttu-id="9f701-143">İzin verilen talepler, `GetAllowedOpList` kullanıcının gerçekleştirmesine izin verilen işlemlerin belirli bir listesini döndürmek için uygulanan yönteminden alınır.</span><span class="sxs-lookup"><span data-stu-id="9f701-143">The claims that are allowed are obtained from the `GetAllowedOpList` method, which is implemented to return a specific list of operations that the user is allowed to perform.</span></span> <span data-ttu-id="9f701-144">Yetkilendirme ilkesi, belirli bir işleme erişim taleplerini ekler.</span><span class="sxs-lookup"><span data-stu-id="9f701-144">The authorization policy adds claims for accessing the particular operation.</span></span> <span data-ttu-id="9f701-145">Bu daha sonra, <xref:System.ServiceModel.ServiceAuthorizationManager> erişim denetimi kararlarını gerçekleştirmek için tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9f701-145">This is later used by the <xref:System.ServiceModel.ServiceAuthorizationManager> to perform access check decisions.</span></span>

<span data-ttu-id="9f701-146">Özel uygulandıktan sonra <xref:System.IdentityModel.Policy.IAuthorizationPolicy> , hizmet ana bilgisayarının kullanılacak yetkilendirme ilkeleri hakkında bilgilendirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="9f701-146">Once the custom <xref:System.IdentityModel.Policy.IAuthorizationPolicy> is implemented, the service host must be informed about the authorization policies to use.</span></span>

```xml
<serviceAuthorization>
       <authorizationPolicies>
            <add policyType='Microsoft.ServiceModel.Samples.CustomAuthorizationPolicy.MyAuthorizationPolicy, PolicyLibrary' />
       </authorizationPolicies>
</serviceAuthorization>
```

<span data-ttu-id="9f701-147">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="9f701-147">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="9f701-148">İstemci, Ekle, çıkart ve birden çok yöntemi başarıyla çağırır ve bölme yöntemini çağırmaya çalışırken bir "erişim reddedildi" iletisi alır.</span><span class="sxs-lookup"><span data-stu-id="9f701-148">The client successfully calls the Add, Subtract and Multiple methods and gets an "Access is denied" message when trying to call the Divide method.</span></span> <span data-ttu-id="9f701-149">İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="9f701-149">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="9f701-150">Toplu Iş dosyası kurulumu</span><span class="sxs-lookup"><span data-stu-id="9f701-150">Setup Batch File</span></span>

<span data-ttu-id="9f701-151">Bu örneğe eklenen Setup. bat toplu iş dosyası, sunucu sertifika tabanlı güvenlik gerektiren şirket içinde barındırılan bir uygulamayı çalıştırmak için sunucuyu ilgili sertifikalarla yapılandırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="9f701-151">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate-based security.</span></span>

<span data-ttu-id="9f701-152">Aşağıdakiler, uygun yapılandırmada çalışacak şekilde değiştirilebilecek şekilde, toplu iş dosyalarının farklı bölümlerine kısa bir genel bakış sunar:</span><span class="sxs-lookup"><span data-stu-id="9f701-152">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration:</span></span>

- <span data-ttu-id="9f701-153">Sunucu sertifikası oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="9f701-153">Creating the server certificate.</span></span>

    <span data-ttu-id="9f701-154">Setup. bat toplu iş dosyasından aşağıdaki satırlar kullanılacak sunucu sertifikasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9f701-154">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="9f701-155">% SERVER_NAME% değişkeni sunucu adını belirtiyor.</span><span class="sxs-lookup"><span data-stu-id="9f701-155">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="9f701-156">Kendi sunucu adınızı belirtmek için bu değişkeni değiştirin.</span><span class="sxs-lookup"><span data-stu-id="9f701-156">Change this variable to specify your own server name.</span></span> <span data-ttu-id="9f701-157">Varsayılan değer localhost 'tur.</span><span class="sxs-lookup"><span data-stu-id="9f701-157">The default value is localhost.</span></span>

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="9f701-158">Sunucu sertifikasını istemcinin güvenilen sertifika deposuna yükleme.</span><span class="sxs-lookup"><span data-stu-id="9f701-158">Installing the server certificate into client's trusted certificate store.</span></span>

    <span data-ttu-id="9f701-159">Setup. bat toplu iş dosyası 'ndaki aşağıdaki satırlar, sunucu sertifikasını istemci güvenilir kişiler deposuna kopyalar.</span><span class="sxs-lookup"><span data-stu-id="9f701-159">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="9f701-160">Bu adım, MakeCert. exe tarafından oluşturulan sertifikalara istemci sistemi tarafından örtük olarak güvenilmediği için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="9f701-160">This step is required because certificates that are generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="9f701-161">İstemci tarafından güvenilen kök sertifikada kök sertifikaya sahip bir sertifikanız zaten varsa (örneğin, Microsoft tarafından verilen bir sertifika), istemci sertifikası deposunu sunucu sertifikasıyla doldurmanın bu adımı gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="9f701-161">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

- <span data-ttu-id="9f701-162">İstemci sertifikası oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="9f701-162">Creating the client certificate.</span></span>

    <span data-ttu-id="9f701-163">Setup. bat toplu iş dosyasından aşağıdaki satırlar kullanılacak istemci sertifikasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9f701-163">The following lines from the Setup.bat batch file create the client certificate to be used.</span></span> <span data-ttu-id="9f701-164">% USER_NAME% değişkeni sunucu adını belirtiyor.</span><span class="sxs-lookup"><span data-stu-id="9f701-164">The %USER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="9f701-165">Bu değer "test1" olarak ayarlanır çünkü bu ad, `IAuthorizationPolicy` için arama yapar.</span><span class="sxs-lookup"><span data-stu-id="9f701-165">This value is set to "test1" because this is the name the `IAuthorizationPolicy` looks for.</span></span> <span data-ttu-id="9f701-166">% USER_NAME değerini değiştirirseniz, yöntemde karşılık gelen değeri değiştirmeniz gerekir `IAuthorizationPolicy.Evaluate` .</span><span class="sxs-lookup"><span data-stu-id="9f701-166">If you change the value of %USER_NAME% you must change the corresponding value in the `IAuthorizationPolicy.Evaluate` method.</span></span>

    <span data-ttu-id="9f701-167">Sertifika, CurrentUser Store konumu altında (kişisel) deposunda depolanır.</span><span class="sxs-lookup"><span data-stu-id="9f701-167">The certificate is stored in My (Personal) store under the CurrentUser store location.</span></span>

    ```bat
    echo ************
    echo making client cert
    echo ************
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="9f701-168">İstemci sertifikası sunucunun Güvenilen sertifika deposuna yükleniyor.</span><span class="sxs-lookup"><span data-stu-id="9f701-168">Installing the client certificate into server's trusted certificate store.</span></span>

    <span data-ttu-id="9f701-169">Setup. bat toplu iş dosyası 'ndaki aşağıdaki satırlar, istemci sertifikasını güvenilir kişiler deposuna kopyalar.</span><span class="sxs-lookup"><span data-stu-id="9f701-169">The following lines in the Setup.bat batch file copy the client certificate into the trusted people store.</span></span> <span data-ttu-id="9f701-170">Bu adım, MakeCert. exe tarafından oluşturulan sertifikalara sunucu sistemi tarafından örtük olarak güvenilmediği için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="9f701-170">This step is required because certificates that are generated by Makecert.exe are not implicitly trusted by the server system.</span></span> <span data-ttu-id="9f701-171">Güvenilen kök sertifikada kök sertifikaya sahip bir sertifikanız zaten varsa (örneğin, Microsoft tarafından verilen bir sertifika), sunucu sertifika deposunu istemci sertifikası ile doldurmak için bu adım gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="9f701-171">If you already have a certificate that is rooted in a trusted root certificate—for example, a Microsoft issued certificate—this step of populating the server certificate store with the client certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
    ```

### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="9f701-172">Örneği ayarlamak ve derlemek için</span><span class="sxs-lookup"><span data-stu-id="9f701-172">To set up and build the sample</span></span>

1. <span data-ttu-id="9f701-173">Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="9f701-173">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

2. <span data-ttu-id="9f701-174">Örneği tek veya bir çoklu bilgisayar yapılandırmasında çalıştırmak için aşağıdaki yönergeleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="9f701-174">To run the sample in a single- or cross-computer configuration, use the following instructions.</span></span>

> [!NOTE]
> <span data-ttu-id="9f701-175">Bu örneğe yönelik yapılandırmayı yeniden oluşturmak için Svcutil. exe ' yi kullanırsanız, istemci yapılandırmasındaki uç nokta adını istemci koduyla eşleşecek şekilde değiştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="9f701-175">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>

### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="9f701-176">Örneği aynı bilgisayarda çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="9f701-176">To run the sample on the same computer</span></span>

1. <span data-ttu-id="9f701-177">Yönetici ayrıcalıklarıyla Visual Studio için Geliştirici Komut İstemi açın ve örnek yükleme klasöründen *Setup. bat* dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9f701-177">Open Developer Command Prompt for Visual Studio with administrator privileges and run *Setup.bat* from the sample install folder.</span></span> <span data-ttu-id="9f701-178">Bu, örneği çalıştırmak için gereken tüm sertifikaları kurar.</span><span class="sxs-lookup"><span data-stu-id="9f701-178">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="9f701-179">Setup. bat toplu iş dosyası, Visual Studio için Geliştirici Komut İstemi çalıştırılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="9f701-179">The Setup.bat batch file is designed to be run from Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="9f701-180">Visual Studio için Geliştirici Komut İstemi içinde ayarlanan yol ortamı değişkeni *Setup. bat* betiği için gereken yürütülebilir dosyaları içeren dizine işaret eder.</span><span class="sxs-lookup"><span data-stu-id="9f701-180">The PATH environment variable set within Developer Command Prompt for Visual Studio points to the directory that contains executables required by the *Setup.bat* script.</span></span>

1. <span data-ttu-id="9f701-181">*Service\bin*' den Service. exe ' yi başlatın.</span><span class="sxs-lookup"><span data-stu-id="9f701-181">Launch Service.exe from *service\bin*.</span></span>

1. <span data-ttu-id="9f701-182">*\Client\bin*adresinden Client. exe ' yi başlatın.</span><span class="sxs-lookup"><span data-stu-id="9f701-182">Launch Client.exe from *\client\bin*.</span></span> <span data-ttu-id="9f701-183">İstemci etkinliği istemci konsol uygulamasında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="9f701-183">Client activity is displayed on the client console application.</span></span>

<span data-ttu-id="9f701-184">İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="9f701-184">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>

### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="9f701-185">Örneği bilgisayarlar arasında çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="9f701-185">To run the sample across computers</span></span>

1. <span data-ttu-id="9f701-186">Hizmet bilgisayarında bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9f701-186">Create a directory on the service computer.</span></span>

2. <span data-ttu-id="9f701-187">Hizmet programı dosyalarını *\service\bin* konumundan hizmet bilgisayarındaki dizine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="9f701-187">Copy the service program files from *\service\bin* to the directory on the service computer.</span></span> <span data-ttu-id="9f701-188">Ayrıca Setup. bat, Cleanup. bat, GetComputerName. vbs ve ImportClientCert. bat dosyalarını hizmet bilgisayarına kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="9f701-188">Also copy the Setup.bat, Cleanup.bat, GetComputerName.vbs and ImportClientCert.bat files to the service computer.</span></span>

3. <span data-ttu-id="9f701-189">İstemci bilgisayarda istemci ikilileri için bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9f701-189">Create a directory on the client computer for the client binaries.</span></span>

4. <span data-ttu-id="9f701-190">İstemci programı dosyalarını istemci bilgisayardaki istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="9f701-190">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="9f701-191">Ayrıca Setup. bat, Cleanup. bat ve ImportServiceCert. bat dosyalarını istemciye kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="9f701-191">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>

5. <span data-ttu-id="9f701-192">Sunucusunda, `setup.bat service` yönetici ayrıcalıklarıyla açılan Visual Studio için geliştirici komut istemi ' de çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9f701-192">On the server, run `setup.bat service` in Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>

    <span data-ttu-id="9f701-193">`setup.bat`Bağımsız değişkeniyle birlikte çalıştırmak, `service` bilgisayarın tam etki alanı adına sahip bir hizmet sertifikası oluşturur ve hizmet sertifikasını *Service. cer*adlı bir dosyaya aktarır.</span><span class="sxs-lookup"><span data-stu-id="9f701-193">Running `setup.bat` with the `service` argument creates a service certificate with the fully qualified domain name of the computer, and exports the service certificate to a file named *Service.cer*.</span></span>

6. <span data-ttu-id="9f701-194">*Service. exe. config dosyasını* `findValue` , [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) bilgisayarın tam etki alanı adıyla aynı olan yeni sertifika adını (içindeki özniteliğinde) yansıtacak şekilde düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="9f701-194">Edit *Service.exe.config* to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully qualified domain name of the computer.</span></span> <span data-ttu-id="9f701-195">Ayrıca, öğesindeki **ComputerName** \<service> / \<baseAddresses> öğesini localhost 'dan hizmet bilgisayarınızın tam adıyla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="9f701-195">Also change the **computername** in the \<service>/\<baseAddresses> element from localhost to the fully qualified name of your service computer.</span></span>

7. <span data-ttu-id="9f701-196">Service *. cer* dosyasını hizmet dizininden istemci bilgisayarındaki istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="9f701-196">Copy the *Service.cer* file from the service directory to the client directory on the client computer.</span></span>

8. <span data-ttu-id="9f701-197">İstemcisinde, `setup.bat client` yönetici ayrıcalıklarıyla açılan Visual Studio için geliştirici komut istemi ' de çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9f701-197">On the client, run `setup.bat client` in Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>

    <span data-ttu-id="9f701-198">`setup.bat`Bağımsız değişkeniyle birlikte çalıştırmak, `client` **test1** adlı bir istemci sertifikası oluşturur ve istemci sertifikasını *Client. cer*adlı bir dosyaya aktarır.</span><span class="sxs-lookup"><span data-stu-id="9f701-198">Running `setup.bat` with the `client` argument creates a client certificate named **test1** and exports the client certificate to a file named *Client.cer*.</span></span>

9. <span data-ttu-id="9f701-199">İstemci bilgisayardaki *Client. exe. config* dosyasında, uç noktanın adres değerini hizmetinizin yeni adresiyle eşleşecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="9f701-199">In the *Client.exe.config* file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="9f701-200">**Localhost** 'u sunucunun tam etki alanı adıyla değiştirerek bunu yapın.</span><span class="sxs-lookup"><span data-stu-id="9f701-200">Do this by replacing **localhost** with the fully qualified domain name of the server.</span></span>

10. <span data-ttu-id="9f701-201">Client. cer dosyasını istemci dizininden sunucusundaki hizmet dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="9f701-201">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>

11. <span data-ttu-id="9f701-202">İstemcisinde, yönetici ayrıcalıklarıyla açılan Visual Studio için Geliştirici Komut İstemi 'de *ImportServiceCert. bat* dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9f701-202">On the client, run *ImportServiceCert.bat* in Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>

    <span data-ttu-id="9f701-203">Bu, hizmet sertifikasını Service. cer dosyasından **CurrentUser-Trustedkişiler** deposuna aktarır.</span><span class="sxs-lookup"><span data-stu-id="9f701-203">This imports the service certificate from the Service.cer file into the **CurrentUser - TrustedPeople** store.</span></span>

12. <span data-ttu-id="9f701-204">Sunucusunda, yönetici ayrıcalıklarıyla açılan Visual Studio için Geliştirici Komut İstemi 'de *ImportClientCert. bat* dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9f701-204">On the server, run *ImportClientCert.bat* in Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>

    <span data-ttu-id="9f701-205">Bu, istemci sertifikasını Client. cer dosyasından **LocalMachine-Trustedkişiler** deposuna aktarır.</span><span class="sxs-lookup"><span data-stu-id="9f701-205">This imports the client certificate from the Client.cer file into the **LocalMachine - TrustedPeople** store.</span></span>

13. <span data-ttu-id="9f701-206">Sunucu bilgisayarda, komut istemi penceresinden Service. exe ' yi başlatın.</span><span class="sxs-lookup"><span data-stu-id="9f701-206">On the server computer, launch Service.exe from the command prompt window.</span></span>

14. <span data-ttu-id="9f701-207">İstemci bilgisayarda, bir komut istemi penceresinden Client. exe ' yi başlatın.</span><span class="sxs-lookup"><span data-stu-id="9f701-207">On the client computer, launch Client.exe from a command prompt window.</span></span>

    <span data-ttu-id="9f701-208">İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="9f701-208">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>

### <a name="clean-up-after-the-sample"></a><span data-ttu-id="9f701-209">Örnekten sonra temizle</span><span class="sxs-lookup"><span data-stu-id="9f701-209">Clean up after the sample</span></span>

<span data-ttu-id="9f701-210">Örnekten sonra temizlemek için, örneği çalıştırmayı bitirdiğinizde Samples klasöründe *Cleanup. bat* dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9f701-210">To clean up after the sample, run *Cleanup.bat* in the samples folder when you have finished running the sample.</span></span> <span data-ttu-id="9f701-211">Bu, sunucu ve istemci sertifikalarını sertifika deposundan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9f701-211">This removes the server and client certificates from the certificate store.</span></span>

> [!NOTE]
> <span data-ttu-id="9f701-212">Bu betik, bilgisayarlar arasında bu örneği çalıştırırken bir istemcideki hizmet sertifikalarını kaldırmaz.</span><span class="sxs-lookup"><span data-stu-id="9f701-212">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="9f701-213">Bilgisayarlar arasında sertifika kullanan WCF örnekleri çalıştırırsanız, CurrentUser-Trustedkişiler deposuna yüklenmiş olan hizmet sertifikalarını temizlediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="9f701-213">If you have run WCF samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="9f701-214">Bunu yapmak için şu komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com` .</span><span class="sxs-lookup"><span data-stu-id="9f701-214">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>
