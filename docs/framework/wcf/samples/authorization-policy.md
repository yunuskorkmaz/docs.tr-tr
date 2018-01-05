---
title: "Yetkilendirme İlkesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1db325ec-85be-47d0-8b6e-3ba2fdf3dda0
caps.latest.revision: "38"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 98d39bdc366eb6b5d757057c3d0e519d81aedd43
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="authorization-policy"></a><span data-ttu-id="42262-102">Yetkilendirme İlkesi</span><span class="sxs-lookup"><span data-stu-id="42262-102">Authorization Policy</span></span>
<span data-ttu-id="42262-103">Bu örnek, bir özel talep yetkilendirme ilkesini ve ilişkili özel hizmet Yetkilendirme Yöneticisi uygulama gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="42262-103">This sample demonstrates how to implement a custom claim authorization policy and an associated custom service authorization manager.</span></span> <span data-ttu-id="42262-104">Bu, belirli hakları çağıran hizmet işlemlerine ve erişim denetimleri öncesinde talep tabanlı erişim denetimlerini hizmeti yapar verir durumunda faydalı olur.</span><span class="sxs-lookup"><span data-stu-id="42262-104">This is useful when the service makes claim-based access checks to service operations and prior to the access checks, grants the caller certain rights.</span></span> <span data-ttu-id="42262-105">Bu örnek talep sonlandırılmış kümesini karşı bir erişim denetimi yapmak için işlem yanı sıra talep ekleme işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="42262-105">This sample shows both the process of adding claims as well as the process for doing an access check against the finalized set of claims.</span></span> <span data-ttu-id="42262-106">İstemci ve sunucu arasındaki tüm uygulama iletileri imzalanır ve şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="42262-106">All application messages between the client and server are signed and encrypted.</span></span> <span data-ttu-id="42262-107">Varsayılan olarak `wsHttpBinding` bağlama, bir kullanıcı adı ve istemci tarafından sağlanan parola kullanılan oturum açmak için geçerli bir Windows NT hesabı.</span><span class="sxs-lookup"><span data-stu-id="42262-107">By default with the `wsHttpBinding` binding, a username and password supplied by the client are used to logon to a valid Windows NT account.</span></span> <span data-ttu-id="42262-108">Bu örnek, bir özel kullanmaya gösterilmiştir <!--zz <xref:System.IdentityModel.Selectors.UsernamePasswordValidator>--> `System.IdentityModel.Selectors.UsernamePasswordValidator` istemci kimlik doğrulaması için.</span><span class="sxs-lookup"><span data-stu-id="42262-108">This sample demonstrates how to utilize a custom <!--zz <xref:System.IdentityModel.Selectors.UsernamePasswordValidator>--> `System.IdentityModel.Selectors.UsernamePasswordValidator` to authenticate the client.</span></span> <span data-ttu-id="42262-109">Ayrıca bu örnek, bir X.509 sertifikası kullanarak hizmet kimlik doğrulaması istemci göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="42262-109">In addition this sample shows the client authenticating to the service using an X.509 certificate.</span></span> <span data-ttu-id="42262-110">Bu örnek uygulaması gösterir <xref:System.IdentityModel.Policy.IAuthorizationPolicy> ve <xref:System.ServiceModel.ServiceAuthorizationManager>, bunları aralarında hizmetinin belirli kullanıcılar için belirli yöntemler için erişim verin.</span><span class="sxs-lookup"><span data-stu-id="42262-110">This sample shows an implementation of <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and <xref:System.ServiceModel.ServiceAuthorizationManager>, which between them grant access to specific methods of the service for specific users.</span></span> <span data-ttu-id="42262-111">Bu örnek dayanır [ileti güvenliği kullanıcı adı](../../../../docs/framework/wcf/samples/message-security-user-name.md), ancak talep dönüştürmeyi öncesinde gerçekleştirmek nasıl gösteren <xref:System.ServiceModel.ServiceAuthorizationManager> çağrılan.</span><span class="sxs-lookup"><span data-stu-id="42262-111">This sample is based on the [Message Security User Name](../../../../docs/framework/wcf/samples/message-security-user-name.md), but demonstrates how to perform a claim transformation prior to the <xref:System.ServiceModel.ServiceAuthorizationManager> being called.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="42262-112">Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="42262-112">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="42262-113">Özet olarak, bu örnek gösterilmektedir nasıl:</span><span class="sxs-lookup"><span data-stu-id="42262-113">In summary, this sample demonstrates how:</span></span>  
  
-   <span data-ttu-id="42262-114">İstemci, bir kullanıcı adı parolası kullanılarak doğrulanabilir.</span><span class="sxs-lookup"><span data-stu-id="42262-114">The client can be authenticated using a user name-password.</span></span>  
  
-   <span data-ttu-id="42262-115">İstemci, bir X.509 sertifikası kullanılarak doğrulanabilir.</span><span class="sxs-lookup"><span data-stu-id="42262-115">The client can be authenticated using an X.509 certificate.</span></span>  
  
-   <span data-ttu-id="42262-116">Sunucu karşı özel bir istemci kimlik doğrulama `UsernamePassword` Doğrulayıcı.</span><span class="sxs-lookup"><span data-stu-id="42262-116">The server validates the client credentials against a custom `UsernamePassword` validator.</span></span>  
  
-   <span data-ttu-id="42262-117">Sunucu, sunucunun X.509 sertifikası kullanılarak doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="42262-117">The server is authenticated using the server's X.509 certificate.</span></span>  
  
-   <span data-ttu-id="42262-118">Sunucu kullanabilir <xref:System.ServiceModel.ServiceAuthorizationManager> hizmet belirli yöntemlerine erişimi denetleme.</span><span class="sxs-lookup"><span data-stu-id="42262-118">The server can use <xref:System.ServiceModel.ServiceAuthorizationManager> to control access to certain methods in the service.</span></span>  
  
-   <span data-ttu-id="42262-119">Nasıl uygulanacağını <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span><span class="sxs-lookup"><span data-stu-id="42262-119">How to implement <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span></span>  
  
 <span data-ttu-id="42262-120">Hizmet App.config yapılandırma dosyası kullanılarak tanımlanmış hizmet ile iletişim için iki uç noktalarını kullanıma sunar. Her uç nokta bir adresi, bağlama ve bir sözleşme oluşur.</span><span class="sxs-lookup"><span data-stu-id="42262-120">The service exposes two endpoints for communicating with the service, defined using the configuration file App.config. Each endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="42262-121">Bir standart ile yapılandırılmış bir bağlama `wsHttpBinding` bağlaması WS güvenliği ve istemci kullanıcı adı kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="42262-121">One binding is configured with a standard `wsHttpBinding` binding that uses WS-Security and client username authentication.</span></span> <span data-ttu-id="42262-122">Bir standart yapılandırılmış diğer bağlama `wsHttpBinding` bağlaması WS güvenliği ve istemci sertifikası kimlik doğrulaması kullanır.</span><span class="sxs-lookup"><span data-stu-id="42262-122">The other binding is configured with a standard `wsHttpBinding` binding that uses WS-Security and client certificate authentication.</span></span> <span data-ttu-id="42262-123">[ \<Davranışı >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) hizmet kimlik doğrulaması için kullanılacak olan kullanıcı kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="42262-123">The [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) specifies that the user credentials are to be used for service authentication.</span></span> <span data-ttu-id="42262-124">Sunucu sertifikası için aynı değeri içermelidir `SubjectName` özelliği olarak `findValue` özniteliğini [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="42262-124">The server certificate must contain the same value for the `SubjectName` property as the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span></span>  
  
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
  
 <span data-ttu-id="42262-125">Her istemci uç nokta yapılandırması yapılandırma adı, hizmet uç noktası, bağlama ve sözleşme için mutlak bir adres oluşur.</span><span class="sxs-lookup"><span data-stu-id="42262-125">Each client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="42262-126">Bağlama istemci belirtildiği gibi uygun güvenlik moduyla bu durumda yapılandırılan [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) ve `clientCredentialType` belirtilmiş [ \<ileti >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="42262-126">The client binding is configured with the appropriate security mode as specified in this case in the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) and `clientCredentialType` as specified in the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md).</span></span>  
  
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
  
 <span data-ttu-id="42262-127">Kullanıcı adı tabanlı uç noktası için istemci uygulaması kullanıcı adı ve parola ayarlar.</span><span class="sxs-lookup"><span data-stu-id="42262-127">For the user name-based endpoint, the client implementation sets the user name and password to use.</span></span>  
  
```  
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
  
 <span data-ttu-id="42262-128">Sertifika tabanlı uç noktası için istemci uygulaması istemci sertifikası kullanacak şekilde ayarlar.</span><span class="sxs-lookup"><span data-stu-id="42262-128">For the certificate-based endpoint, the client implementation sets the client certificate to use.</span></span>  
  
```  
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
  
 <span data-ttu-id="42262-129">Bu örnek, bir özel kullanmaktadır <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> kullanıcı adları ve parolalar doğrulanacak.</span><span class="sxs-lookup"><span data-stu-id="42262-129">This sample uses a custom <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> to validate user names and passwords.</span></span> <span data-ttu-id="42262-130">Örnek uygulayan `MyCustomUserNamePasswordValidator`, türetilmiş <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span><span class="sxs-lookup"><span data-stu-id="42262-130">The sample implements `MyCustomUserNamePasswordValidator`, derived from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span></span> <span data-ttu-id="42262-131">Belgelerine bakın <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="42262-131">See the documentation about <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> for more information.</span></span> <span data-ttu-id="42262-132">İle tümleştirme tanıtmak amacıyla <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>, bu özel Doğrulayıcı örnek uygulayan <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> burada belirtilen kullanıcı adıyla eşleşen parolayı aşağıdaki kodda gösterildiği gibi kullanıcı adı/parola çiftlerini kabul yöntemi.</span><span class="sxs-lookup"><span data-stu-id="42262-132">For the purposes of demonstrating the integration with the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>, this custom validator sample implements the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method to accept user name/password pairs where the user name matches the password as shown in the following code.</span></span>  
  
```  
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
  
 <span data-ttu-id="42262-133">Doğrulayıcı hizmet kodunda tamamlandıktan sonra hizmet ana bilgisayarı kullanmak için Doğrulayıcı örneği hakkında bilgi sahibi olmak gerekir.</span><span class="sxs-lookup"><span data-stu-id="42262-133">Once the validator is implemented in service code, the service host must be informed about the validator instance to use.</span></span> <span data-ttu-id="42262-134">Bu yapılır aşağıdaki kodu kullanarak.</span><span class="sxs-lookup"><span data-stu-id="42262-134">This is done using the following code.</span></span>  
  
```  
Servicehost.Credentials.UserNameAuthentication.UserNamePasswordValidationMode = UserNamePasswordValidationMode.Custom;  
serviceHost.Credentials.UserNameAuthentication.CustomUserNamePasswordValidator = new MyCustomUserNamePasswordValidatorProvider();  
```  
  
 <span data-ttu-id="42262-135">Veya yapılandırma aynı şeyi yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="42262-135">Or you can do the same thing in configuration.</span></span>  
  
```xml  
<behavior ...>  
    <serviceCredentials>  
      <!--   
      The serviceCredentials behavior allows one to specify a custom validator for username/password combinations.    
      -->  
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.MyCustomUserNameValidator, service" />  
    ...  
    </serviceCredentials>  
</behavior>  
```  
  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="42262-136">erişim denetimleri gerçekleştirmek için zengin talep tabanlı modeli sağlar.</span><span class="sxs-lookup"><span data-stu-id="42262-136"> provides a rich claims-based model for performing access checks.</span></span> <span data-ttu-id="42262-137"><xref:System.ServiceModel.ServiceAuthorizationManager> Nesne erişim denetimi gerçekleştirebilir ve istemciyle ilişkili talep hizmet yöntemi erişimi için gereken koşulları karşılamak olup olmadığını belirlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="42262-137">The <xref:System.ServiceModel.ServiceAuthorizationManager> object is used to perform the access check and determine whether the claims associated with the client satisfy the requirements necessary to access the service method.</span></span>  
  
 <span data-ttu-id="42262-138">Tanıtım amacıyla, bu örnek uygulaması gösterir <xref:System.ServiceModel.ServiceAuthorizationManager> uygulayan <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> yöntemleri kullanıcının erişmesine izin vermek için yöntemine temel değeri olan eylemi türü http://example.com/claims/allowedoperation talep üzerinde Çağrılacak izin işlemi URI'si.</span><span class="sxs-lookup"><span data-stu-id="42262-138">For the purposes of demonstration, this sample shows an implementation of <xref:System.ServiceModel.ServiceAuthorizationManager> that implements the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method to allow a user's access to methods based on claims of type http://example.com/claims/allowedoperation whose value is the Action URI of the operation that is allowed to be called.</span></span>  
  
```  
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
  
 <span data-ttu-id="42262-139">Özel <xref:System.ServiceModel.ServiceAuthorizationManager> olan uygulanan, hizmet ana bilgisayarı hakkında bilgi sahibi olmak gerekir <xref:System.ServiceModel.ServiceAuthorizationManager> kullanmak için.</span><span class="sxs-lookup"><span data-stu-id="42262-139">Once the custom <xref:System.ServiceModel.ServiceAuthorizationManager> is implemented, the service host must be informed about the <xref:System.ServiceModel.ServiceAuthorizationManager> to use.</span></span> <span data-ttu-id="42262-140">Bu aşağıdaki kodda gösterildiği gibi gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="42262-140">This is done as shown in the following code.</span></span>  
  
```xml  
<behavior ...>  
    ...  
    <serviceAuthorization serviceAuthorizationManagerType="Microsoft.ServiceModel.Samples.MyServiceAuthorizationManager, service">  
        ...  
    </serviceAuthorization>  
</behavior>  
```  
  
 <span data-ttu-id="42262-141">Birincil <xref:System.IdentityModel.Policy.IAuthorizationPolicy> uygulamak için yöntem <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="42262-141">The primary <xref:System.IdentityModel.Policy.IAuthorizationPolicy> method to implement is the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method.</span></span>  
  
```  
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
  
 <span data-ttu-id="42262-142">Önceki kodun gösterdiği nasıl <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> yöntemi denetler, işleme etkiler ve belirli talep ekler yeni bir talep eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="42262-142">The previous code shows how the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method checks that no new claims have been added that affect the processing and adds specific claims.</span></span> <span data-ttu-id="42262-143">İzin verilen talep elde edilen `GetAllowedOpList` belirli bir kullanıcının gerçekleştirmesine izin verilen işlemler listesini döndürmek için uygulanması yöntemi.</span><span class="sxs-lookup"><span data-stu-id="42262-143">The claims that are allowed are obtained from the `GetAllowedOpList` method, which is implemented to return a specific list of operations that the user is allowed to perform.</span></span> <span data-ttu-id="42262-144">Yetkilendirme İlkesi belirli bir işlemi erişmek için talep ekler.</span><span class="sxs-lookup"><span data-stu-id="42262-144">The authorization policy adds claims for accessing the particular operation.</span></span> <span data-ttu-id="42262-145">Bu daha sonra tarafından kullanılan <xref:System.ServiceModel.ServiceAuthorizationManager> erişim denetimi kararlarını gerçekleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="42262-145">This is later used by the <xref:System.ServiceModel.ServiceAuthorizationManager> to perform access check decisions.</span></span>  
  
 <span data-ttu-id="42262-146">Özel <xref:System.IdentityModel.Policy.IAuthorizationPolicy> , hizmet ana bilgisayarı Yetkilendirme İlkeleri hakkında bilgi sahibi olmak gerekir kullanmak için uygulanır.</span><span class="sxs-lookup"><span data-stu-id="42262-146">Once the custom <xref:System.IdentityModel.Policy.IAuthorizationPolicy> is implemented, the service host must be informed about the authorization policies to use.</span></span>  
  
```xml  
<serviceAuthorization ...>  
       <authorizationPolicies>   
            <add policyType='Microsoft.ServiceModel.Samples.CustomAuthorizationPolicy.MyAuthorizationPolicy, PolicyLibrary' />  
       </authorizationPolicies>   
</serviceAuthorization>  
```  
  
 <span data-ttu-id="42262-147">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="42262-147">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="42262-148">İstemci başarıyla ekleme ve çıkarma birden çok yöntemi çağırır ve bölme yöntemini çağırmak çalışırken bir "Erişim engellendi" iletisi alır.</span><span class="sxs-lookup"><span data-stu-id="42262-148">The client successfully calls the Add, Subtract and Multiple methods and gets an "Access is denied" message when trying to call the Divide method.</span></span> <span data-ttu-id="42262-149">İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="42262-149">Press ENTER in the client window to shut down the client.</span></span>  
  
## <a name="setup-batch-file"></a><span data-ttu-id="42262-150">Toplu iş dosyası Kurulumu</span><span class="sxs-lookup"><span data-stu-id="42262-150">Setup Batch File</span></span>  
 <span data-ttu-id="42262-151">Bu örnekle dahil Setup.bat toplu iş dosyası, sunucu sertifika tabanlı güvenlik gerektiren kendini barındıran bir uygulamayı çalıştırmak için ilgili sertifikalarla sunucu yapılandırmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="42262-151">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate-based security.</span></span>  
  
 <span data-ttu-id="42262-152">Aşağıdakiler, böylece uygun yapılandırmada çalışacak biçimde değiştirilebilir toplu iş dosyaları farklı bölümlerini kısa bir genel bakış sağlar:</span><span class="sxs-lookup"><span data-stu-id="42262-152">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration:</span></span>  
  
-   <span data-ttu-id="42262-153">Sunucu sertifikası oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="42262-153">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="42262-154">Aşağıdaki satırları Setup.bat toplu iş dosyasından kullanılacak sunucu sertifikası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="42262-154">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="42262-155">% Sunucu_adı % değişkeni sunucusunun adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="42262-155">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="42262-156">Kendi sunucu adını belirtmek için bu değişkeni değiştirin.</span><span class="sxs-lookup"><span data-stu-id="42262-156">Change this variable to specify your own server name.</span></span> <span data-ttu-id="42262-157">Localhost varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="42262-157">The default value is localhost.</span></span>  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   <span data-ttu-id="42262-158">Sunucu sertifikası istemcinin güvenilen sertifika deposuna yükleme.</span><span class="sxs-lookup"><span data-stu-id="42262-158">Installing the server certificate into client's trusted certificate store.</span></span>  
  
     <span data-ttu-id="42262-159">İstemci güvenilir kişiler içine Setup.bat toplu dosya kopyalama sunucu sertifikasının aşağıdaki satırları depolar.</span><span class="sxs-lookup"><span data-stu-id="42262-159">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="42262-160">Makecert.exe tarafından oluşturulan sertifikalarını örtük olarak istemci sistemi tarafından güvenilir değil çünkü bu adım gereklidir.</span><span class="sxs-lookup"><span data-stu-id="42262-160">This step is required because certificates that are generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="42262-161">Bir istemci güvenilen kök sertifikasını kökü belirtilmiş bir sertifikanız zaten varsa — örneğin, bir Microsoft verilen sertifika — sunucu sertifikasına sahip istemci sertifika deposunun doldurulması, bu adım gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="42262-161">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
-   <span data-ttu-id="42262-162">İstemci sertifikası oluşturma.</span><span class="sxs-lookup"><span data-stu-id="42262-162">Creating the client certificate.</span></span>  
  
     <span data-ttu-id="42262-163">Aşağıdaki satırları Setup.bat toplu iş dosyasından kullanılacak istemci sertifikası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="42262-163">The following lines from the Setup.bat batch file create the client certificate to be used.</span></span> <span data-ttu-id="42262-164">% USER_NAME % değişkeni sunucusunun adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="42262-164">The %USER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="42262-165">Bu ad olduğu için bu değer "test1" ayarlanır `IAuthorizationPolicy` arar.</span><span class="sxs-lookup"><span data-stu-id="42262-165">This value is set to "test1" because this is the name the `IAuthorizationPolicy` looks for.</span></span> <span data-ttu-id="42262-166">USER_NAME % değerini değiştirirseniz, karşılık gelen değer değiştirmelisiniz `IAuthorizationPolicy.Evaluate` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="42262-166">If you change the value of %USER_NAME% you must change the corresponding value in the `IAuthorizationPolicy.Evaluate` method.</span></span>  
  
     <span data-ttu-id="42262-167">Sertifika Currentuser'a depolama konumu altında (Kişisel) My deposunda saklanır.</span><span class="sxs-lookup"><span data-stu-id="42262-167">The certificate is stored in My (Personal) store under the CurrentUser store location.</span></span>  
  
    ```  
    echo ************  
    echo making client cert  
    echo ************  
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe  
    ```  
  
-   <span data-ttu-id="42262-168">İstemci sertifikası sunucunun güvenilen sertifika deposuna yükleme.</span><span class="sxs-lookup"><span data-stu-id="42262-168">Installing the client certificate into server's trusted certificate store.</span></span>  
  
     <span data-ttu-id="42262-169">Setup.bat toplu iş dosyası aşağıdaki satırları istemci sertifikası güvenilir Kişiler deposuna kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="42262-169">The following lines in the Setup.bat batch file copy the client certificate into the trusted people store.</span></span> <span data-ttu-id="42262-170">Makecert.exe tarafından oluşturulan sertifikalarını örtük olarak sunucu sistemi tarafından güvenilir değil çünkü bu adım gereklidir.</span><span class="sxs-lookup"><span data-stu-id="42262-170">This step is required because certificates that are generated by Makecert.exe are not implicitly trusted by the server system.</span></span> <span data-ttu-id="42262-171">Bir güvenilen kök sertifika kökü belirtilmiş bir sertifikanız zaten varsa — örneğin, bir Microsoft verilen sertifika — istemci sertifikası ile sunucu sertifika depolama doldurma, bu adım gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="42262-171">If you already have a certificate that is rooted in a trusted root certificate—for example, a Microsoft issued certificate—this step of populating the server certificate store with the client certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="42262-172">Ayarlamak ve örneği oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="42262-172">To set up and build the sample</span></span>  
  
1.  <span data-ttu-id="42262-173">Çözümü derlemek için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="42262-173">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="42262-174">Tek veya çapraz bilgisayar yapılandırmasında örneği çalıştırmak için aşağıdaki yönergeleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="42262-174">To run the sample in a single- or cross-computer configuration, use the following instructions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="42262-175">Bu örnek için yapılandırmayı yeniden oluşturmak için Svcutil.exe kullanırsanız, istemci kodu eşleşecek şekilde istemci yapılandırmasında uç nokta adı değiştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="42262-175">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="42262-176">Aynı bilgisayara örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="42262-176">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="42262-177">Açık bir [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] örnek yükleme klasöründen çalıştırma Setup.bat ve yönetici ayrıcalıkları ile komut istemi penceresi.</span><span class="sxs-lookup"><span data-stu-id="42262-177">Open a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt window with administrator privileges and run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="42262-178">Bu örneği çalıştırmak için gerekli tüm sertifikalar yükler.</span><span class="sxs-lookup"><span data-stu-id="42262-178">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="42262-179">Setup.bat toplu iş dosyası çalıştırılmak üzere tasarlanmış bir [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemi.</span><span class="sxs-lookup"><span data-stu-id="42262-179">The Setup.bat batch file is designed to be run from a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt.</span></span> <span data-ttu-id="42262-180">İçinde PATH ortam değişkeni ayarlamak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemi Setup.bat komut dosyası için gereken yürütülebilir dosyalar içeren dizine işaret eder.</span><span class="sxs-lookup"><span data-stu-id="42262-180">The PATH environment variable set within the [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2.  <span data-ttu-id="42262-181">Visual Studio'da Setup.bat çalıştırmak örnekten yönetici ayrıcalıklarıyla açılmış bir komut istemi yükleme klasörü.</span><span class="sxs-lookup"><span data-stu-id="42262-181">Run Setup.bat in a Visual Studio command prompt opened with administrator privileges from the sample install folder.</span></span> <span data-ttu-id="42262-182">Bu örneği çalıştırmak için gerekli tüm sertifikalar yükler.</span><span class="sxs-lookup"><span data-stu-id="42262-182">This installs all the certificates required for running the sample.</span></span>  
  
3.  <span data-ttu-id="42262-183">Service.exe service\bin başlatın.</span><span class="sxs-lookup"><span data-stu-id="42262-183">Launch Service.exe from service\bin.</span></span>  
  
4.  <span data-ttu-id="42262-184">Client.exe \client\bin başlatın.</span><span class="sxs-lookup"><span data-stu-id="42262-184">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="42262-185">İstemci etkinliği istemci konsol uygulaması görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="42262-185">Client activity is displayed on the client console application.</span></span>  
  
5.  <span data-ttu-id="42262-186">İstemci ve hizmet iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="42262-186">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="42262-187">Bilgisayarlar arasında örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="42262-187">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="42262-188">Hizmet bilgisayarda bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="42262-188">Create a directory on the service computer.</span></span>  
  
2.  <span data-ttu-id="42262-189">Hizmet program dosyalarını \service\bin hizmeti bilgisayarında dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="42262-189">Copy the service program files from \service\bin to the directory on the service computer.</span></span> <span data-ttu-id="42262-190">Ayrıca Setup.bat, Cleanup.bat, GetComputerName.vbs ve ImportClientCert.bat dosyaları hizmet bilgisayara kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="42262-190">Also copy the Setup.bat, Cleanup.bat, GetComputerName.vbs and ImportClientCert.bat files to the service computer.</span></span>  
  
3.  <span data-ttu-id="42262-191">Bir dizin üzerinde istemci computerfor istemci ikili dosyalarının oluşturun.</span><span class="sxs-lookup"><span data-stu-id="42262-191">Create a directory on the client computerfor the client binaries.</span></span>  
  
4.  <span data-ttu-id="42262-192">İstemci program dosyaları istemci bilgisayarda istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="42262-192">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="42262-193">Ayrıca istemciye Setup.bat, Cleanup.bat ve ImportServiceCert.bat dosyalarını kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="42262-193">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5.  <span data-ttu-id="42262-194">Sunucu üzerinde çalışan `setup.bat service` yönetici ayrıcalıklarına sahip bir Visual Studio Komut İstemi'nde açılır.</span><span class="sxs-lookup"><span data-stu-id="42262-194">On the server, run `setup.bat service` in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="42262-195">Çalışan `setup.bat` ile `service` bağımsız değişkeni computerand dışarı tam etki alanı adı ile bir hizmet sertifikası Service.cer adlı bir dosyaya hizmet sertifikası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="42262-195">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computerand exports the service certificate to a file named Service.cer.</span></span>  
  
6.  <span data-ttu-id="42262-196">Yeni sertifika yansıtacak şekilde Service.exe.config Düzenle (içinde `findValue` özniteliğini [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) bilgisayarın tam etki alanı adı ile aynı olduğu.</span><span class="sxs-lookup"><span data-stu-id="42262-196">Edit Service.exe.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="42262-197">Ayrıca, computername değiştirmek \<hizmet > /\<baseAddresses > localhost öğesine hizmeti bilgisayarın tam adı.</span><span class="sxs-lookup"><span data-stu-id="42262-197">Also change the computername in the \<service>/\<baseAddresses> element from localhost to the fully-qualified name of your service computer.</span></span>  
  
7.  <span data-ttu-id="42262-198">Service.cer dosya hizmeti dizininden istemci bilgisayarda istemci dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="42262-198">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8.  <span data-ttu-id="42262-199">İstemci üzerinde çalışan `setup.bat client` yönetici ayrıcalıklarına sahip bir Visual Studio Komut İstemi'nde açılır.</span><span class="sxs-lookup"><span data-stu-id="42262-199">On the client, run `setup.bat client` in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="42262-200">Çalışan `setup.bat` ile `client` bağımsız değişkeni test1 adlı bir istemci sertifikası oluşturur ve istemci sertifikasını Client.cer adlı bir dosyaya aktarır.</span><span class="sxs-lookup"><span data-stu-id="42262-200">Running `setup.bat` with the `client` argument creates a client certificate named test1 and exports the client certificate to a file named Client.cer.</span></span>  
  
9. <span data-ttu-id="42262-201">İstemci bilgisayardaki Client.exe.config dosyasında yeni adresi hizmetinizin eşleştirmek için uç nokta adresi değerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="42262-201">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="42262-202">Sunucunun tam etki alanı adı ile localhost değiştirerek bunu.</span><span class="sxs-lookup"><span data-stu-id="42262-202">Do this by replacing localhost with the fully-qualified domain name of the server.</span></span>  
  
10. <span data-ttu-id="42262-203">Client.cer dosyasını istemci dizininden sunucusunda hizmet dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="42262-203">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
11. <span data-ttu-id="42262-204">İstemci üzerinde yönetici ayrıcalıklarına sahip açılan bir Visual Studio komut istemi ImportServiceCert.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="42262-204">On the client, run ImportServiceCert.bat in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="42262-205">Bu hizmet sertifikası Service.cer dosyadan Currentuser'a - TrustedPeople deposunu alır.</span><span class="sxs-lookup"><span data-stu-id="42262-205">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="42262-206">Sunucu üzerinde yönetici ayrıcalıklarına sahip açılan bir Visual Studio komut istemi ImportClientCert.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="42262-206">On the server, run ImportClientCert.bat in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="42262-207">Bu istemci sertifikası LocalMachine - TrustedPeople deposunda Client.cer dosyadan alır.</span><span class="sxs-lookup"><span data-stu-id="42262-207">This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
13. <span data-ttu-id="42262-208">Sunucu bilgisayarda komut istemi penceresinden Service.exe başlatın.</span><span class="sxs-lookup"><span data-stu-id="42262-208">On the server computer, launch Service.exe from the command prompt window.</span></span>  
  
14. <span data-ttu-id="42262-209">İstemci bilgisayarda bir komut istemi penceresinden Client.exe başlatın.</span><span class="sxs-lookup"><span data-stu-id="42262-209">On the client computer, launch Client.exe from a command prompt window.</span></span> <span data-ttu-id="42262-210">İstemci ve hizmet iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="42262-210">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="42262-211">Örnek sonra temizlemek için</span><span class="sxs-lookup"><span data-stu-id="42262-211">To clean up after the sample</span></span>  
  
1.  <span data-ttu-id="42262-212">Örnek çalıştıran tamamladıktan sonra Cleanup.bat samples klasöründen çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="42262-212">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span> <span data-ttu-id="42262-213">Bu sunucu ve istemci sertifikaları sertifika deposundan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="42262-213">This removes the server and client certificates from the certificate store.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="42262-214">Bu komut, bu örnek bilgisayarlar arasında çalıştırırken bir istemcide hizmet sertifikaları kaldırmaz.</span><span class="sxs-lookup"><span data-stu-id="42262-214">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="42262-215">Çalıştırırsanız [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bilgisayarlar arasında sertifikaları kullanma örnekleri Currentuser'a - TrustedPeople deposu yüklü hizmet sertifikalarını temizlemek emin olun.</span><span class="sxs-lookup"><span data-stu-id="42262-215">If you have run [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="42262-216">Bunu yapmak için aşağıdaki komutu kullanın: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` örneğin: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="42262-216">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42262-217">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="42262-217">See Also</span></span>
