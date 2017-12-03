---
title: "Belirteç Kimlik Doğrulayıcı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 84382f2c-f6b1-4c32-82fa-aebc8f6064db
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7404087117ec45e09495897905094690c01fbaa8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="token-authenticator"></a><span data-ttu-id="abffa-102">Belirteç Kimlik Doğrulayıcı</span><span class="sxs-lookup"><span data-stu-id="abffa-102">Token Authenticator</span></span>
<span data-ttu-id="abffa-103">Bu örnek, özel bir belirteç kimlik doğrulayıcı uygulama gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="abffa-103">This sample demonstrates how to implement a custom token authenticator.</span></span> <span data-ttu-id="abffa-104">İçinde bir belirteç kimlik doğrulayıcısı [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] self tutarlı ve kimliğinin doğrulanması belirteçle ilişkili doğrulama ileti ile kullanılan belirteci doğrulamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="abffa-104">A token authenticator in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] is used for validating the token used with the message, verifying that it is self-consistent, and authenticating the identity associated with the token.</span></span>  
  
 <span data-ttu-id="abffa-105">Özel belirteç kimlik doğrulayan gibi çeşitli durumlarda yararlı olur:</span><span class="sxs-lookup"><span data-stu-id="abffa-105">Custom token authenticators are useful in a variety of cases, such as:</span></span>  
  
-   <span data-ttu-id="abffa-106">Ne zaman bir belirteçle ilişkilendirilen varsayılan kimlik doğrulama mekanizması geçersiz kılmak istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="abffa-106">When you want to override the default authentication mechanism associated with a token.</span></span>  
  
-   <span data-ttu-id="abffa-107">Ne zaman özel belirteç oluşturmakta olduğunuz.</span><span class="sxs-lookup"><span data-stu-id="abffa-107">When you are building a custom token.</span></span>  
  
 <span data-ttu-id="abffa-108">Bu örnek şunlar gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="abffa-108">This sample demonstrates the following:</span></span>  
  
-   <span data-ttu-id="abffa-109">Nasıl bir istemci bir kullanıcı adı/parola çifti kullanılarak doğrulanabilir.</span><span class="sxs-lookup"><span data-stu-id="abffa-109">How a client can authenticate using a username/password pair.</span></span>  
  
-   <span data-ttu-id="abffa-110">Sunucu özel belirteç kimlik doğrulayıcı kullanarak istemci kimlik bilgilerini nasıl doğrulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="abffa-110">How the server can validate the client credentials using a custom token authenticator.</span></span>  
  
-   <span data-ttu-id="abffa-111">Nasıl [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] servis kodu özel belirteç kimlik doğrulayıcı oturum bağlar.</span><span class="sxs-lookup"><span data-stu-id="abffa-111">How the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service code ties in with the custom token authenticator.</span></span>  
  
-   <span data-ttu-id="abffa-112">Sunucu, sunucunun X.509 sertifikası kullanılarak doğrulanabilir nasıl.</span><span class="sxs-lookup"><span data-stu-id="abffa-112">How the server can be authenticated using the server's X.509 certificate.</span></span>  
  
 <span data-ttu-id="abffa-113">Bu örnek ayrıca nasıl çağıranının kimliğini erişilebilir gösterir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sonra özel belirteç kimlik doğrulama işlemi.</span><span class="sxs-lookup"><span data-stu-id="abffa-113">This sample also shows how the caller's identity is accessible from [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] after the custom token authentication process.</span></span>  
  
 <span data-ttu-id="abffa-114">Hizmet App.config yapılandırma dosyası kullanılarak tanımlanmış hizmet ile iletişim için tek bir uç noktasını kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="abffa-114">The service exposes a single endpoint for communicating with the service, defined using the App.config configuration file.</span></span> <span data-ttu-id="abffa-115">Uç nokta bir adresi, bağlama ve bir sözleşme oluşur.</span><span class="sxs-lookup"><span data-stu-id="abffa-115">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="abffa-116">Bağlama ile standart bir yapılandırılmış `wsHttpBinding`, güvenlik modu iletiye - varsayılan modu ayarlandığında `wsHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="abffa-116">The binding is configured with a standard `wsHttpBinding`, with the security mode set to message - the default mode of the `wsHttpBinding`.</span></span> <span data-ttu-id="abffa-117">Bu örnek standart ayarlar `wsHttpBinding` istemci kullanıcı adı kimlik doğrulaması kullanmak için.</span><span class="sxs-lookup"><span data-stu-id="abffa-117">This sample sets the standard `wsHttpBinding` to use client username authentication.</span></span> <span data-ttu-id="abffa-118">Hizmetini kullanarak sertifika hizmetini de yapılandırır `serviceCredentials` davranışı.</span><span class="sxs-lookup"><span data-stu-id="abffa-118">The service also configures the service certificate using `serviceCredentials` behavior.</span></span> <span data-ttu-id="abffa-119">`securityCredentials` Davranış bir hizmet sertifikası belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="abffa-119">The `securityCredentials` behavior allows you to specify a service certificate.</span></span> <span data-ttu-id="abffa-120">Bir hizmet sertifikası, hizmetin kimliğini doğrulamak ve ileti koruma sağlamak için bir istemci tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="abffa-120">A service certificate is used by a client to authenticate the service and provide message protection.</span></span> <span data-ttu-id="abffa-121">Aşağıdaki yapılandırma aşağıdaki Kurulum yönergelerde açıklandığı gibi örnek Kurulum sırasında yüklenen localhost sertifika başvurur.</span><span class="sxs-lookup"><span data-stu-id="abffa-121">The following configuration references the localhost certificate installed during the sample setup as described in the following setup instructions.</span></span>  
  
```xml  
<system.serviceModel>  
    <services>  
      <service   
          name="Microsoft.ServiceModel.Samples.CalculatorService"  
          behaviorConfiguration="CalculatorServiceBehavior">  
        <host>  
          <baseAddresses>  
            <!-- configure base address provided by host -->  
            <add baseAddress ="http://localhost:8000/servicemodelsamples/service" />  
          </baseAddresses>  
        </host>  
        <!-- use base address provided by host -->  
        <endpoint address=""  
                  binding="wsHttpBinding"  
                  bindingConfiguration="Binding1"   
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
      </service>  
    </services>  
  
    <bindings>  
      <wsHttpBinding>  
        <binding name="Binding1">  
          <security mode="Message">  
            <message clientCredentialType="UserName" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceDebug includeExceptionDetailInFaults="False" />  
          <!--   
          The serviceCredentials behavior allows one to define a service certificate.  
          A service certificate is used by a client to authenticate the service and provide message protection.  
          This configuration references the "localhost" certificate installed during the setup instructions.  
....        -->  
          <serviceCredentials>  
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
  </system.serviceModel>  
```  
  
 <span data-ttu-id="abffa-122">Yapılandırma adı, hizmet uç noktası, bağlama ve sözleşme için mutlak bir adres, istemci uç nokta yapılandırması oluşur.</span><span class="sxs-lookup"><span data-stu-id="abffa-122">The client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="abffa-123">Bağlama istemci uygun ile yapılandırılmış `Mode` ve `clientCredentialType`.</span><span class="sxs-lookup"><span data-stu-id="abffa-123">The client binding is configured with the appropriate `Mode` and `clientCredentialType`.</span></span>  
  
```xml  
<system.serviceModel>  
    <client>  
      <endpoint name=""  
                address="http://localhost:8000/servicemodelsamples/service"   
                binding="wsHttpBinding"   
                bindingConfiguration="Binding1"   
                contract="Microsoft.ServiceModel.Samples.ICalculator">  
      </endpoint>  
    </client>  
  
    <bindings>  
      <wsHttpBinding>  
        <binding name="Binding1">  
          <security mode="Message">  
            <message clientCredentialType="UserName" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
  </system.serviceModel>  
```  
  
 <span data-ttu-id="abffa-124">İstemci uygulama kullanıcı adı ve parola ayarlar.</span><span class="sxs-lookup"><span data-stu-id="abffa-124">The client implementation sets the user name and password to use.</span></span>  
  
```  
static void Main()  
{  
     ...  
     client.ClientCredentials.UserNamePassword.UserName = username;  
     client.ClientCredentials.UserNamePassword.Password = password;  
     ...  
}  
```  
  
## <a name="custom-token-authenticator"></a><span data-ttu-id="abffa-125">Özel belirteç kimlik doğrulayıcı</span><span class="sxs-lookup"><span data-stu-id="abffa-125">Custom Token Authenticator</span></span>  
 <span data-ttu-id="abffa-126">Özel bir belirteç kimlik doğrulayıcısı oluşturmak için aşağıdaki adımları kullanın:</span><span class="sxs-lookup"><span data-stu-id="abffa-126">Use the following steps to create a custom token authenticator:</span></span>  
  
1.  <span data-ttu-id="abffa-127">Özel belirteç kimlik doğrulayıcı yazma.</span><span class="sxs-lookup"><span data-stu-id="abffa-127">Write a custom token authenticator.</span></span>  
  
     <span data-ttu-id="abffa-128">Örnek kullanıcı adı geçerli bir e-posta biçiminde olduğunu doğrulayan bir özel belirteç kimlik doğrulayıcı uygular.</span><span class="sxs-lookup"><span data-stu-id="abffa-128">The sample implements a custom token authenticator that validates that the username has a valid email format.</span></span> <span data-ttu-id="abffa-129">Bunu türetilen <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="abffa-129">It derives the <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator>.</span></span> <span data-ttu-id="abffa-130">Bu sınıftaki en önemli bir yöntemdir <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator.ValidateUserNamePasswordCore%28System.String%2CSystem.String%29>.</span><span class="sxs-lookup"><span data-stu-id="abffa-130">The most important method in this class is <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator.ValidateUserNamePasswordCore%28System.String%2CSystem.String%29>.</span></span> <span data-ttu-id="abffa-131">Bu yöntemde, Doğrulayıcı biçimini doğrular. kullanıcı adı ve bu da ana bilgisayar adı yanlış etki alanına ait değil.</span><span class="sxs-lookup"><span data-stu-id="abffa-131">In this method, the authenticator validates the format of the username and also that the host name is not from a rogue domain.</span></span> <span data-ttu-id="abffa-132">Her iki koşullar sonra salt okunur koleksiyonunu döndürür <xref:System.IdentityModel.Policy.IAuthorizationPolicy> sonra kullanıcı adı belirteci içine depolanan bilgileri temsil eden talepler sağlamak için kullanılan örnekleri.</span><span class="sxs-lookup"><span data-stu-id="abffa-132">If both conditions are met, then it returns a read-only collection of <xref:System.IdentityModel.Policy.IAuthorizationPolicy> instances that is then used to provide claims that represent the information stored inside the username token.</span></span>  
  
    ```  
    protected override ReadOnlyCollection<IAuthorizationPolicy> ValidateUserNamePasswordCore(string userName, string password)  
    {  
        if (!ValidateUserNameFormat(userName))  
            throw new SecurityTokenValidationException("Incorrect UserName format");  
  
        ClaimSet claimSet = new DefaultClaimSet(ClaimSet.System, new Claim(ClaimTypes.Name, userName, Rights.PossessProperty));  
        List<IIdentity> identities = new List<IIdentity>(1);  
        identities.Add(new GenericIdentity(userName));  
        List<IAuthorizationPolicy> policies = new List<IAuthorizationPolicy>(1);  
        policies.Add(new UnconditionalPolicy(ClaimSet.System, claimSet, DateTime.MaxValue.ToUniversalTime(), identities));  
        return policies.AsReadOnly();  
    }  
    ```  
  
2.  <span data-ttu-id="abffa-133">Özel belirteç kimlik doğrulayıcı tarafından döndürülen bir yetkilendirme ilkesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="abffa-133">Provide an authorization policy that is returned by custom token authenticator.</span></span>  
  
     <span data-ttu-id="abffa-134">Bu örnek, kendi uygulamasını sağlar <xref:System.IdentityModel.Policy.IAuthorizationPolicy> adlı `UnconditionalPolicy` talepler ve kendisine kurucusunda geçirilmiş kimlikleri kümesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="abffa-134">This sample provides its own implementation of <xref:System.IdentityModel.Policy.IAuthorizationPolicy> called `UnconditionalPolicy` that returns set of claims and identities that were passed to it in its constructor.</span></span>  
  
    ```  
    class UnconditionalPolicy : IAuthorizationPolicy  
    {  
        String id = Guid.NewGuid().ToString();  
        ClaimSet issuer;  
        ClaimSet issuance;  
        DateTime expirationTime;  
        IList<IIdentity> identities;  
  
        public UnconditionalPolicy(ClaimSet issuer, ClaimSet issuance, DateTime expirationTime, IList<IIdentity> identities)  
        {  
            if (issuer == null)  
                throw new ArgumentNullException("issuer");  
            if (issuance == null)  
                throw new ArgumentNullException("issuance");  
  
            this.issuer = issuer;  
            this.issuance = issuance;  
            this.identities = identities;  
            this.expirationTime = expirationTime;  
        }  
  
        public string Id  
        {  
            get { return this.id; }  
        }  
  
        public ClaimSet Issuer  
        {  
            get { return this.issuer; }  
        }  
  
        public DateTime ExpirationTime  
        {  
            get { return this.expirationTime; }  
        }  
  
        public bool Evaluate(EvaluationContext evaluationContext, ref object state)  
        {  
            evaluationContext.AddToTarget(this, this.issuance);  
  
            if (this.identities != null)  
            {  
                object value;  
                IList<IIdentity> contextIdentities;  
                if (!evaluationContext.Properties.TryGetValue("Identities", out value))  
                {  
                    contextIdentities = new List<IIdentity>(this.identities.Count);  
                    evaluationContext.Properties.Add("Identities", contextIdentities);  
                }  
                else  
                {  
                    contextIdentities = value as IList<IIdentity>;  
                }  
                foreach (IIdentity identity in this.identities)  
                {  
                    contextIdentities.Add(identity);  
                }  
            }  
  
            evaluationContext.RecordExpirationTime(this.expirationTime);  
            return true;  
        }  
    }  
    ```  
  
3.  <span data-ttu-id="abffa-135">Özel bir güvenlik belirteci yöneticisi yazma.</span><span class="sxs-lookup"><span data-stu-id="abffa-135">Write a custom security token manager.</span></span>  
  
     <span data-ttu-id="abffa-136"><xref:System.IdentityModel.Selectors.SecurityTokenManager> Oluşturmak için kullanılan bir <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> belirli <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> kendisine geçirilen nesneleri `CreateSecurityTokenAuthenticator` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="abffa-136">The <xref:System.IdentityModel.Selectors.SecurityTokenManager> is used to create a <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> for specific <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> objects that are passed to it in the `CreateSecurityTokenAuthenticator` method.</span></span> <span data-ttu-id="abffa-137">Güvenlik belirteci yöneticisi belirteci sağlayıcıları ve belirteç serileştiricileri oluşturmak için de kullanılır, ancak bunlar Bu örnek tarafından ele alınmamaktadır.</span><span class="sxs-lookup"><span data-stu-id="abffa-137">The security token manager is also used to create token providers and token serializers, but those are not covered by this sample.</span></span> <span data-ttu-id="abffa-138">Bu örnekte, özel güvenlik belirteci yöneticisi devraldığı <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> sınıfı ve geçersiz kılmalar `CreateSecurityTokenAuthenticator` geçirilen belirteç gereksinimlerini bu kullanıcı adı kimlik doğrulayıcı belirttiğinizde özel kullanıcıadı belirteç kimlik doğrulayıcı döndürülecek yöntemi istendi.</span><span class="sxs-lookup"><span data-stu-id="abffa-138">In this sample, the custom security token manager inherits from <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> class and overrides the `CreateSecurityTokenAuthenticator` method to return custom username token authenticator when the passed token requirements indicate that username authenticator is requested.</span></span>  
  
    ```  
    public class MySecurityTokenManager : ServiceCredentialsSecurityTokenManager  
    {  
        MyUserNameCredential myUserNameCredential;  
  
        public MySecurityTokenManager(MyUserNameCredential myUserNameCredential)  
            : base(myUserNameCredential)  
        {  
            this.myUserNameCredential = myUserNameCredential;  
        }  
  
        public override SecurityTokenAuthenticator CreateSecurityTokenAuthenticator(SecurityTokenRequirement tokenRequirement, out SecurityTokenResolver outOfBandTokenResolver)  
        {  
            if (tokenRequirement.TokenType ==  SecurityTokenTypes.UserName)  
            {  
                outOfBandTokenResolver = null;  
                return new MyTokenAuthenticator();  
            }  
            else  
            {  
                return base.CreateSecurityTokenAuthenticator(tokenRequirement, out outOfBandTokenResolver);  
            }  
        }  
    }  
    ```  
  
4.  <span data-ttu-id="abffa-139">Bir özel hizmet kimlik bilgilerini yazın.</span><span class="sxs-lookup"><span data-stu-id="abffa-139">Write a custom service credential.</span></span>  
  
     <span data-ttu-id="abffa-140">Hizmet kimlik bilgilerini sınıfı hizmet için yapılandırılan kimlik bilgileri temsil etmek için kullanılır ve bir güvenlik belirteci Doğrulayıcı, belirteci sağlayıcıları ve belirteç serileştiricileri elde etmek için kullanılan belirteci yöneticisi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="abffa-140">The service credentials class is used to represent the credentials that are configured for the service and creates a security token manager that is used to obtain token authenticators, token providers and token serializers.</span></span>  
  
    ```  
    public class MyUserNameCredential : ServiceCredentials  
    {  
  
        public MyUserNameCredential()  
            : base()  
        {  
        }  
  
        protected override ServiceCredentials CloneCore()  
        {  
            return new MyUserNameCredential();  
        }  
  
        public override SecurityTokenManager CreateSecurityTokenManager()  
        {  
            return new MySecurityTokenManager(this);  
        }  
  
    }  
    ```  
  
5.  <span data-ttu-id="abffa-141">Hizmetini özel hizmet kimlik bilgilerini kullanacak biçimde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="abffa-141">Configure the service to use the custom service credential.</span></span>  
  
     <span data-ttu-id="abffa-142">Özel hizmet kimlik bilgilerini kullanmak hizmet için sırasıyla biz varsayılan hizmet kimlik bilgisi sınıfını zaten varsayılan hizmet kimlik bilgisi önceden yapılandırılmış hizmet sertifikası yakalama sonra silin ve yeni hizmet kimlik bilgilerini yapılandırın önceden yapılandırılmış hizmet sertifikalarını kullanın ve bu yeni hizmet kimlik bilgisi örneği hizmet davranışları eklemek için örneği.</span><span class="sxs-lookup"><span data-stu-id="abffa-142">In order for the service to use the custom service credential, we delete the default service credential class after capturing the service certificate that is already preconfigured in the default service credential, and configure the new service credential instance to use the preconfigured service certificates and add this new service credential instance to service behaviors.</span></span>  
  
    ```  
    ServiceCredentials sc = serviceHost.Credentials;  
    X509Certificate2 cert = sc.ServiceCertificate.Certificate;  
    MyUserNameCredential serviceCredential = new MyUserNameCredential();  
    serviceCredential.ServiceCertificate.Certificate = cert;  
    serviceHost.Description.Behaviors.Remove((typeof(ServiceCredentials)));  
    serviceHost.Description.Behaviors.Add(serviceCredential);  
    ```  
  
 <span data-ttu-id="abffa-143">Arayanın bilgileri görüntülemek için kullanabileceğiniz <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="abffa-143">To display the caller's information, you can use the <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> as shown in the following code.</span></span> <span data-ttu-id="abffa-144"><xref:System.ServiceModel.ServiceSecurityContext.Current%2A> Talep geçerli çağıran hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="abffa-144">The <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> contains claims information about the current caller.</span></span>  
  
```  
static void DisplayIdentityInformation()  
{  
    Console.WriteLine("\t\tSecurity context identity  :  {0}",   
            ServiceSecurityContext.Current.PrimaryIdentity.Name);  
     return;  
}  
```  
  
 <span data-ttu-id="abffa-145">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="abffa-145">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="abffa-146">İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="abffa-146">Press ENTER in the client window to shut down the client.</span></span>  
  
## <a name="setup-batch-file"></a><span data-ttu-id="abffa-147">Toplu iş dosyası Kurulumu</span><span class="sxs-lookup"><span data-stu-id="abffa-147">Setup Batch File</span></span>  
 <span data-ttu-id="abffa-148">Bu örnekle dahil Setup.bat toplu iş dosyası ile ilgili sertifika sunucusu gerektirir kendini barındıran bir uygulamayı çalıştırmak için sunucuyu yapılandırmak için sertifika tabanlı güvenlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="abffa-148">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate based security.</span></span> <span data-ttu-id="abffa-149">Bu toplu iş dosyası bilgisayarlar arasında iş ya da barındırılan olmayan bir durumda çalışması için değiştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="abffa-149">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>  
  
 <span data-ttu-id="abffa-150">Aşağıdakiler, böylece uygun yapılandırmada çalışacak biçimde değiştirilebilir toplu iş dosyaları farklı bölümlerini kısa bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="abffa-150">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in appropriate configuration.</span></span>  
  
-   <span data-ttu-id="abffa-151">Sunucu sertifikası oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="abffa-151">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="abffa-152">Aşağıdaki satırları Setup.bat toplu iş dosyasından kullanılacak sunucu sertifikası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="abffa-152">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="abffa-153">`%SERVER_NAME%` Değişkeni, sunucu adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="abffa-153">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="abffa-154">Kendi sunucu adını belirtmek için bu değişkeni değiştirin.</span><span class="sxs-lookup"><span data-stu-id="abffa-154">Change this variable to specify your own server name.</span></span> <span data-ttu-id="abffa-155">Bu toplu iş dosyasındaki localhost varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="abffa-155">The default in this batch file is localhost.</span></span>  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   <span data-ttu-id="abffa-156">Sunucu sertifikası istemcinin güvenilen sertifika deposuna yükleme.</span><span class="sxs-lookup"><span data-stu-id="abffa-156">Installing the server certificate into client's trusted certificate store.</span></span>  
  
     <span data-ttu-id="abffa-157">İstemci güvenilir kişiler içine Setup.bat toplu dosya kopyalama sunucu sertifikasının aşağıdaki satırları depolar.</span><span class="sxs-lookup"><span data-stu-id="abffa-157">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="abffa-158">MakeCert.exe tarafından oluşturulan sertifikaları örtük olarak istemci sistemi tarafından güvenilir değil çünkü bu adım gereklidir.</span><span class="sxs-lookup"><span data-stu-id="abffa-158">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="abffa-159">Bir istemci güvenilen kök sertifikasını kökü belirtilmiş bir sertifikanız zaten varsa — örneğin, bir Microsoft verilen sertifika — sunucu sertifikasına sahip istemci sertifika deposunun doldurulması, bu adım gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="abffa-159">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="abffa-160">Kurulum toplu iş dosyası, Windows SDK komut isteminden çalıştırılması için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="abffa-160">The setup batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="abffa-161">MSSDK ortam değişkeni SDK yüklendiği dizinine işaret gerektiriyor.</span><span class="sxs-lookup"><span data-stu-id="abffa-161">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="abffa-162">Bu ortam değişkeni, Windows SDK komut istemi içinde otomatik olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="abffa-162">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span>  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="abffa-163">Ayarlamak ve örneği oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="abffa-163">To set up and build the sample</span></span>  
  
1.  <span data-ttu-id="abffa-164">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="abffa-164">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="abffa-165">Çözümü derlemek için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="abffa-165">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="abffa-166">Aynı bilgisayara örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="abffa-166">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="abffa-167">Örnek yükleme klasöründen içinde Setup.bat çalıştırmak bir [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemini yönetici ayrıcalıklarıyla açılır.</span><span class="sxs-lookup"><span data-stu-id="abffa-167">Run Setup.bat from the sample installation folder inside a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] command prompt opened with administrator privileges.</span></span> <span data-ttu-id="abffa-168">Bu örneği çalıştırmak için gerekli tüm sertifikalar yükler.</span><span class="sxs-lookup"><span data-stu-id="abffa-168">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="abffa-169">Setup.bat toplu iş dosyası çalıştırılmak üzere tasarlanmış bir [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemi.</span><span class="sxs-lookup"><span data-stu-id="abffa-169">The Setup.bat batch file is designed to be run from a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt.</span></span> <span data-ttu-id="abffa-170">İçinde PATH ortam değişkeni ayarlamak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemi Setup.bat komut dosyası için gereken yürütülebilir dosyalar içeren dizine işaret eder.</span><span class="sxs-lookup"><span data-stu-id="abffa-170">The PATH environment variable set within the [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2.  <span data-ttu-id="abffa-171">Service\bin gelen Service.exe başlatın.</span><span class="sxs-lookup"><span data-stu-id="abffa-171">Launch service.exe from service\bin.</span></span>  
  
3.  <span data-ttu-id="abffa-172">\Client\bin gelen Client.exe başlatın.</span><span class="sxs-lookup"><span data-stu-id="abffa-172">Launch client.exe from \client\bin.</span></span> <span data-ttu-id="abffa-173">İstemci etkinliği istemci konsol uygulaması görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="abffa-173">Client activity is displayed on the client console application.</span></span>  
  
4.  <span data-ttu-id="abffa-174">İstemci ve hizmet iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="abffa-174">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="abffa-175">Bilgisayarlar arasında örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="abffa-175">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="abffa-176">Hizmet ikili dosyaları hizmet bilgisayarda bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="abffa-176">Create a directory on the service computer for the service binaries.</span></span>  
  
2.  <span data-ttu-id="abffa-177">Hizmet program dosyalarını hizmeti bilgisayarında hizmet dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="abffa-177">Copy the service program files to the service directory on the service computer.</span></span> <span data-ttu-id="abffa-178">Ayrıca Setup.bat ve Cleanup.bat dosyalarını hizmet bilgisayara kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="abffa-178">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3.  <span data-ttu-id="abffa-179">Bilgisayarın tam etki alanı adını içeren konu adına sahip bir sunucu sertifikası olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="abffa-179">You must have a server certificate with the subject name that contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="abffa-180">Hizmet App.config dosyası bu yeni sertifika adını yansıtacak şekilde güncelleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="abffa-180">The service App.config file must be updated to reflect this new certificate name.</span></span> <span data-ttu-id="abffa-181">Ayarlarsanız Setup.bat kullanarak bir tane oluşturabilirsiniz `%SERVER_NAME%` hizmetin çalışacağı bilgisayarın tam ana bilgisayar adı için değişken.</span><span class="sxs-lookup"><span data-stu-id="abffa-181">You can create one by using the Setup.bat if you set the `%SERVER_NAME%` variable to fully-qualified host name of the computer on which the service will run.</span></span> <span data-ttu-id="abffa-182">Setup.bat dosyasını yönetici ayrıcalıklarıyla açılmış Visual Studio komut isteminden çalıştırmanız gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="abffa-182">Note that the setup.bat file must be run from a Visual Studio command prompt opened with administrator privileges.</span></span>  
  
4.  <span data-ttu-id="abffa-183">Sunucu sertifikası istemci Currentuser'a TrustedPeople depolama alanına kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="abffa-183">Copy the server certificate into the CurrentUser-TrustedPeople store of the client.</span></span> <span data-ttu-id="abffa-184">Sunucu sertifikası zaman istemcisi güvenilir veren tarafından verilen dışında bunu gerekmez.</span><span class="sxs-lookup"><span data-stu-id="abffa-184">You do not need to do this except when the server certificate is issued by a client trusted issuer.</span></span>  
  
5.  <span data-ttu-id="abffa-185">Hizmeti bilgisayarında App.config dosyasında localhost yerine bir tam bilgisayar adını belirtmek için taban adresi değerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="abffa-185">In the App.config file on the service computer, change the value of the base address to specify a fully-qualified computer name instead of localhost.</span></span>  
  
6.  <span data-ttu-id="abffa-186">Hizmet bilgisayarda service.exe bir komut isteminden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="abffa-186">On the service computer, run service.exe from a command prompt.</span></span>  
  
7.  <span data-ttu-id="abffa-187">İstemci program dosyaları \client\bin\ klasöründen dile özgü klasörü altında istemci bilgisayara kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="abffa-187">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
8.  <span data-ttu-id="abffa-188">İstemci bilgisayardaki Client.exe.config dosyasında yeni adresi hizmetinizin eşleştirmek için uç nokta adresi değerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="abffa-188">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="abffa-189">İstemci bilgisayarda bir komut isteminden Client.exe başlatın.</span><span class="sxs-lookup"><span data-stu-id="abffa-189">On the client computer, launch Client.exe from a command prompt.</span></span>  
  
10. <span data-ttu-id="abffa-190">İstemci ve hizmet iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="abffa-190">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="abffa-191">Örnek sonra temizlemek için</span><span class="sxs-lookup"><span data-stu-id="abffa-191">To clean up after the sample</span></span>  
  
1.  <span data-ttu-id="abffa-192">Örnek çalıştıran tamamladıktan sonra Cleanup.bat samples klasöründen çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="abffa-192">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abffa-193">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="abffa-193">See Also</span></span>
