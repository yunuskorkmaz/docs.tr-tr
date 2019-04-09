---
title: Belirteç Kimlik Doğrulayıcı
ms.date: 03/30/2017
ms.assetid: 84382f2c-f6b1-4c32-82fa-aebc8f6064db
ms.openlocfilehash: 027f6c55cb0390084f1a7926a5c79d8591090df6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59193414"
---
# <a name="token-authenticator"></a><span data-ttu-id="729a2-102">Belirteç Kimlik Doğrulayıcı</span><span class="sxs-lookup"><span data-stu-id="729a2-102">Token Authenticator</span></span>
<span data-ttu-id="729a2-103">Bu örnek nasıl özel bir belirteç kimlik doğrulayıcısı uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="729a2-103">This sample demonstrates how to implement a custom token authenticator.</span></span> <span data-ttu-id="729a2-104">Belirteç kimlik doğrulayıcısı Windows Communication Foundation (WCF) ileti ile kullanılan belirteci doğrulamak için tutarlı ve kimlik doğrulama belirteciyle ilişkili doğrulama kullanılır.</span><span class="sxs-lookup"><span data-stu-id="729a2-104">A token authenticator in Windows Communication Foundation (WCF) is used for validating the token used with the message, verifying that it is self-consistent, and authenticating the identity associated with the token.</span></span>

 <span data-ttu-id="729a2-105">Özel belirteç Doğrulayıcı gibi çeşitli durumlarda kullanışlıdır:</span><span class="sxs-lookup"><span data-stu-id="729a2-105">Custom token authenticators are useful in a variety of cases, such as:</span></span>

-   <span data-ttu-id="729a2-106">Geçersiz bir belirteç ile ilişkili varsayılan kimlik doğrulama mekanizması istediğinizde.</span><span class="sxs-lookup"><span data-stu-id="729a2-106">When you want to override the default authentication mechanism associated with a token.</span></span>

-   <span data-ttu-id="729a2-107">Ne zaman özel bir simge oluşturuyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="729a2-107">When you are building a custom token.</span></span>

 <span data-ttu-id="729a2-108">Bu örnek aşağıdaki gösterir:</span><span class="sxs-lookup"><span data-stu-id="729a2-108">This sample demonstrates the following:</span></span>

-   <span data-ttu-id="729a2-109">Nasıl bir istemci bir kullanıcı adı/parola çifti kullanarak kimlik doğrulaması yapabilir.</span><span class="sxs-lookup"><span data-stu-id="729a2-109">How a client can authenticate using a username/password pair.</span></span>

-   <span data-ttu-id="729a2-110">Sunucu, özel bir belirteç kimlik doğrulayıcısı kullanarak istemci kimlik bilgileri nasıl doğrulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="729a2-110">How the server can validate the client credentials using a custom token authenticator.</span></span>

-   <span data-ttu-id="729a2-111">Nasıl özel bir belirteç kimlik doğrulayıcısı oturum WCF hizmet kodunun bağlar.</span><span class="sxs-lookup"><span data-stu-id="729a2-111">How the WCF service code ties in with the custom token authenticator.</span></span>

-   <span data-ttu-id="729a2-112">Sunucu, sunucunun X.509 sertifikası kullanılarak doğrulanabilir nasıl.</span><span class="sxs-lookup"><span data-stu-id="729a2-112">How the server can be authenticated using the server's X.509 certificate.</span></span>

 <span data-ttu-id="729a2-113">Ayrıca bu örnek nasıl çağıranının kimliğini özel belirteç kimlik doğrulama işleminden sonra WCF erişilebilir gösterir.</span><span class="sxs-lookup"><span data-stu-id="729a2-113">This sample also shows how the caller's identity is accessible from WCF after the custom token authentication process.</span></span>

 <span data-ttu-id="729a2-114">Hizmet, App.config yapılandırma dosyası kullanılarak tanımlanmış hizmet ile iletişim kurmak için tek bir uç noktayı kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="729a2-114">The service exposes a single endpoint for communicating with the service, defined using the App.config configuration file.</span></span> <span data-ttu-id="729a2-115">Uç nokta, adres, bağlama ve bir sözleşme oluşur.</span><span class="sxs-lookup"><span data-stu-id="729a2-115">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="729a2-116">Bir standart yapılandırılmış bağlama `wsHttpBinding`, güvenlik modu iletiye - varsayılan modu ayarlandığında `wsHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="729a2-116">The binding is configured with a standard `wsHttpBinding`, with the security mode set to message - the default mode of the `wsHttpBinding`.</span></span> <span data-ttu-id="729a2-117">Bu örnek, standart ayarlar `wsHttpBinding` istemci kullanıcı adı kimlik doğrulaması kullanmak için.</span><span class="sxs-lookup"><span data-stu-id="729a2-117">This sample sets the standard `wsHttpBinding` to use client username authentication.</span></span> <span data-ttu-id="729a2-118">Hizmet Ayrıca hizmet kullanarak sertifikayı yapılandırır `serviceCredentials` davranışı.</span><span class="sxs-lookup"><span data-stu-id="729a2-118">The service also configures the service certificate using `serviceCredentials` behavior.</span></span> <span data-ttu-id="729a2-119">`securityCredentials` Davranışı, bir hizmet sertifikası belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="729a2-119">The `securityCredentials` behavior allows you to specify a service certificate.</span></span> <span data-ttu-id="729a2-120">Bir hizmet sertifikası, hizmet kimlik doğrulaması ve ileti koruma sağlamak için bir istemci tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="729a2-120">A service certificate is used by a client to authenticate the service and provide message protection.</span></span> <span data-ttu-id="729a2-121">Aşağıdaki yapılandırmayı aşağıdaki Kurulum yönergelerinde açıklandığı gibi örnek Kurulum sırasında yüklenen localhost sertifikasına başvuruda bulunuyor.</span><span class="sxs-lookup"><span data-stu-id="729a2-121">The following configuration references the localhost certificate installed during the sample setup as described in the following setup instructions.</span></span>

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

 <span data-ttu-id="729a2-122">İstemci uç nokta yapılandırması mutlak bir adres için hizmet uç noktası, bağlama ve sözleşmenin bir yapılandırma adı oluşur.</span><span class="sxs-lookup"><span data-stu-id="729a2-122">The client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="729a2-123">Bağlama istemcinin uygun olarak yapılandırıldığı `Mode` ve `clientCredentialType`.</span><span class="sxs-lookup"><span data-stu-id="729a2-123">The client binding is configured with the appropriate `Mode` and `clientCredentialType`.</span></span>

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

 <span data-ttu-id="729a2-124">İstemci uygulaması, kullanıcı adını ve parolayı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="729a2-124">The client implementation sets the user name and password to use.</span></span>

```
static void Main()
{
     ...
     client.ClientCredentials.UserNamePassword.UserName = username;
     client.ClientCredentials.UserNamePassword.Password = password;
     ...
}
```

## <a name="custom-token-authenticator"></a><span data-ttu-id="729a2-125">Özel belirteç kimlik doğrulayıcısı</span><span class="sxs-lookup"><span data-stu-id="729a2-125">Custom Token Authenticator</span></span>
 <span data-ttu-id="729a2-126">Özel bir belirteç kimlik doğrulayıcısı oluşturmak için aşağıdaki adımları kullanın:</span><span class="sxs-lookup"><span data-stu-id="729a2-126">Use the following steps to create a custom token authenticator:</span></span>

1.  <span data-ttu-id="729a2-127">Özel bir belirteç kimlik doğrulayıcısı yazın.</span><span class="sxs-lookup"><span data-stu-id="729a2-127">Write a custom token authenticator.</span></span>

     <span data-ttu-id="729a2-128">Örnek, kullanıcı adı geçerli bir e-posta biçiminde olduğunu doğrulama özel bir belirteç Doğrulayıcı uygular.</span><span class="sxs-lookup"><span data-stu-id="729a2-128">The sample implements a custom token authenticator that validates that the username has a valid email format.</span></span> <span data-ttu-id="729a2-129">Bunu türetilen <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="729a2-129">It derives the <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator>.</span></span> <span data-ttu-id="729a2-130">Bu sınıftaki en önemli yöntemdir <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator.ValidateUserNamePasswordCore%28System.String%2CSystem.String%29>.</span><span class="sxs-lookup"><span data-stu-id="729a2-130">The most important method in this class is <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator.ValidateUserNamePasswordCore%28System.String%2CSystem.String%29>.</span></span> <span data-ttu-id="729a2-131">Bu yöntemde, Doğrulayıcı biçimini doğrular. kullanıcı adı ve bu da konak adı bir dolandırıcı etki alanına ait değil.</span><span class="sxs-lookup"><span data-stu-id="729a2-131">In this method, the authenticator validates the format of the username and also that the host name is not from a rogue domain.</span></span> <span data-ttu-id="729a2-132">Her iki koşullar sonra salt okunur bir koleksiyonunu döndürür <xref:System.IdentityModel.Policy.IAuthorizationPolicy> örnekleriyle sonra kullanıcı adı belirteci içinde depolanan bilgileri temsil eden talep sağlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="729a2-132">If both conditions are met, then it returns a read-only collection of <xref:System.IdentityModel.Policy.IAuthorizationPolicy> instances that is then used to provide claims that represent the information stored inside the username token.</span></span>

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

2.  <span data-ttu-id="729a2-133">Özel belirteç kimlik doğrulayıcısı tarafından döndürülen bir yetkilendirme ilkesi belirtin.</span><span class="sxs-lookup"><span data-stu-id="729a2-133">Provide an authorization policy that is returned by custom token authenticator.</span></span>

     <span data-ttu-id="729a2-134">Bu örnek, kendi uygulamasını sağlar <xref:System.IdentityModel.Policy.IAuthorizationPolicy> adlı `UnconditionalPolicy` talepler ve oluşturucusunda kendisine iletilmiş kimlikleri kümesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="729a2-134">This sample provides its own implementation of <xref:System.IdentityModel.Policy.IAuthorizationPolicy> called `UnconditionalPolicy` that returns set of claims and identities that were passed to it in its constructor.</span></span>

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

3.  <span data-ttu-id="729a2-135">Bir özel güvenlik belirteci Yöneticisi'ni yazın.</span><span class="sxs-lookup"><span data-stu-id="729a2-135">Write a custom security token manager.</span></span>

     <span data-ttu-id="729a2-136"><xref:System.IdentityModel.Selectors.SecurityTokenManager> Oluşturmak için kullanılan bir <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> belirli <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> kendisine geçirilen nesneleri `CreateSecurityTokenAuthenticator` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="729a2-136">The <xref:System.IdentityModel.Selectors.SecurityTokenManager> is used to create a <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> for specific <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> objects that are passed to it in the `CreateSecurityTokenAuthenticator` method.</span></span> <span data-ttu-id="729a2-137">Güvenlik belirteci Yöneticisi ayrıca belirteci sağlayıcıları ve belirteci seri hale getiricileri genişletme oluşturmak için kullanılır, ancak bunlar Bu örnek tarafından kapsanmaz.</span><span class="sxs-lookup"><span data-stu-id="729a2-137">The security token manager is also used to create token providers and token serializers, but those are not covered by this sample.</span></span> <span data-ttu-id="729a2-138">Bu örnekte, özel güvenlik belirteci yöneticisi devraldığı <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> sınıf ve geçersiz kılmaları `CreateSecurityTokenAuthenticator` geçirilen belirteci gereksinimleri, kullanıcı adı kimlik doğrulayıcı belirttiğinizde, özel kullanıcı adı belirteci kimlik doğrulayıcı döndürülecek yöntemi istendi.</span><span class="sxs-lookup"><span data-stu-id="729a2-138">In this sample, the custom security token manager inherits from <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> class and overrides the `CreateSecurityTokenAuthenticator` method to return custom username token authenticator when the passed token requirements indicate that username authenticator is requested.</span></span>

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

4.  <span data-ttu-id="729a2-139">Bir özel hizmet kimlik bilgilerini yazın.</span><span class="sxs-lookup"><span data-stu-id="729a2-139">Write a custom service credential.</span></span>

     <span data-ttu-id="729a2-140">Hizmet kimlik bilgilerini sınıfı, hizmet için yapılandırılmış kimlik bilgilerini temsil etmek için kullanılır ve bir güvenlik belirteci kimlik doğrulayıcılar, belirteç sağlayıcıları ve belirteci seri hale getiricileri genişletme elde etmek için kullanılan belirteci yöneticisi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="729a2-140">The service credentials class is used to represent the credentials that are configured for the service and creates a security token manager that is used to obtain token authenticators, token providers and token serializers.</span></span>

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

5.  <span data-ttu-id="729a2-141">Hizmetini özel hizmet kimlik bilgilerini kullanacak şekilde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="729a2-141">Configure the service to use the custom service credential.</span></span>

     <span data-ttu-id="729a2-142">Özel hizmet kimlik bilgisi kullanmak için hizmet için sırasıyla biz varsayılan hizmet kimlik bilgisi sınıfı zaten varsayılan hizmet kimlik bilgisi önceden yapılandırılmış olan hizmet sertifikası yakaladıktan sonra silin ve yeni hizmet kimlik bilgilerini yapılandırma önceden yapılandırılmış hizmet sertifikalarını kullanın ve bu yeni hizmet kimlik bilgisi örneği için hizmet davranışları eklemek için örneği.</span><span class="sxs-lookup"><span data-stu-id="729a2-142">In order for the service to use the custom service credential, we delete the default service credential class after capturing the service certificate that is already preconfigured in the default service credential, and configure the new service credential instance to use the preconfigured service certificates and add this new service credential instance to service behaviors.</span></span>

    ```
    ServiceCredentials sc = serviceHost.Credentials;
    X509Certificate2 cert = sc.ServiceCertificate.Certificate;
    MyUserNameCredential serviceCredential = new MyUserNameCredential();
    serviceCredential.ServiceCertificate.Certificate = cert;
    serviceHost.Description.Behaviors.Remove((typeof(ServiceCredentials)));
    serviceHost.Description.Behaviors.Add(serviceCredential);
    ```

 <span data-ttu-id="729a2-143">Arayanın bilgileri görüntülemek için kullanabileceğiniz <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="729a2-143">To display the caller's information, you can use the <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> as shown in the following code.</span></span> <span data-ttu-id="729a2-144"><xref:System.ServiceModel.ServiceSecurityContext.Current%2A> Talep geçerli arayanı hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="729a2-144">The <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> contains claims information about the current caller.</span></span>

```
static void DisplayIdentityInformation()
{
    Console.WriteLine("\t\tSecurity context identity  :  {0}",
            ServiceSecurityContext.Current.PrimaryIdentity.Name);
     return;
}
```

 <span data-ttu-id="729a2-145">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="729a2-145">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="729a2-146">İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="729a2-146">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="729a2-147">Kurulum toplu iş dosyası</span><span class="sxs-lookup"><span data-stu-id="729a2-147">Setup Batch File</span></span>
 <span data-ttu-id="729a2-148">Bu örnekle dahil Setup.bat toplu iş dosyası, sunucunun server gerektiren şirket içinde barındırılan bir uygulamayı çalıştırmak için ilgili sertifikalarla yapılandırmak için sertifika tabanlı güvenlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="729a2-148">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate based security.</span></span> <span data-ttu-id="729a2-149">Bu toplu iş dosyası bilgisayarlarda çalışmaya veya barındırılan olmayan bir durumda çalışması için değiştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="729a2-149">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>

 <span data-ttu-id="729a2-150">Aşağıda, böylece uygun yapılandırmasında çalıştırılacak değiştirilebilir toplu iş dosyaları farklı bölümlerini kısa bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="729a2-150">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in appropriate configuration.</span></span>

-   <span data-ttu-id="729a2-151">Sunucu sertifikası oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="729a2-151">Creating the server certificate.</span></span>

     <span data-ttu-id="729a2-152">Setup.bat toplu iş dosyasından aşağıdaki satırları kullanılacak sunucu sertifikası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="729a2-152">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="729a2-153">`%SERVER_NAME%` Değişkeni, sunucu adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="729a2-153">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="729a2-154">Kendi sunucu adını belirtmek için bu değişkeni değiştirin.</span><span class="sxs-lookup"><span data-stu-id="729a2-154">Change this variable to specify your own server name.</span></span> <span data-ttu-id="729a2-155">Bu toplu iş dosyasında localhost varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="729a2-155">The default in this batch file is localhost.</span></span>

    ```
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

-   <span data-ttu-id="729a2-156">Sunucu sertifikasını istemcinin güvenilen sertifika depolama alanına yükleniyor.</span><span class="sxs-lookup"><span data-stu-id="729a2-156">Installing the server certificate into client's trusted certificate store.</span></span>

     <span data-ttu-id="729a2-157">İstemci güvenilir kişiler uygulamasına Setup.bat toplu dosya kopyalama sunucu sertifikasının aşağıdaki satırları depolayın.</span><span class="sxs-lookup"><span data-stu-id="729a2-157">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="729a2-158">MakeCert.exe tarafından oluşturulan sertifikaları örtük olarak istemci sistemi tarafından güvenilir değildir çünkü bu adım gereklidir.</span><span class="sxs-lookup"><span data-stu-id="729a2-158">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="729a2-159">Bir istemci güvenilen kök sertifikayı kök erişim izni verilmiş bir sertifika zaten varsa — örneğin, Microsoft tarafından verilen sertifika — sunucu sertifikasında istemci sertifika deposunun doldurulması, bu adım gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="729a2-159">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

    > [!NOTE]
    >  <span data-ttu-id="729a2-160">Kurulum toplu iş dosyası, bir Windows SDK Komut İstemi'nden çalıştırılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="729a2-160">The setup batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="729a2-161">MSSDK ortam değişkeni'nın SDK'ın yüklendiği dizini gösterecek gerektiriyor.</span><span class="sxs-lookup"><span data-stu-id="729a2-161">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="729a2-162">Bu ortam değişkeni, bir Windows SDK komut istemi içinde otomatik olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="729a2-162">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span>

#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="729a2-163">Ayarlama ve örneği oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="729a2-163">To set up and build the sample</span></span>

1.  <span data-ttu-id="729a2-164">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="729a2-164">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2.  <span data-ttu-id="729a2-165">Çözümü derlemek için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="729a2-165">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="729a2-166">Örneği aynı bilgisayarda çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="729a2-166">To run the sample on the same computer</span></span>

1.  <span data-ttu-id="729a2-167">Visual Studio 2012 komut istemini yönetici ayrıcalıklarıyla açılan içinde örnek yükleme klasöründen Setup.bat çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="729a2-167">Run Setup.bat from the sample installation folder inside a Visual Studio 2012 command prompt opened with administrator privileges.</span></span> <span data-ttu-id="729a2-168">Bu örneği çalıştırmak için gerekli olan tüm sertifikaları yükler.</span><span class="sxs-lookup"><span data-stu-id="729a2-168">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="729a2-169">Setup.bat toplu iş dosyası, bir Visual Studio 2012 komut isteminden çalıştırılması için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="729a2-169">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="729a2-170">PATH ortam değişkenine içinde Visual Studio 2012 komut istemi noktaları Setup.bat betiği tarafından gereken yürütülebilir dosyaları içeren dizine ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="729a2-170">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2.  <span data-ttu-id="729a2-171">Service.exe service\bin'nden başlatın.</span><span class="sxs-lookup"><span data-stu-id="729a2-171">Launch service.exe from service\bin.</span></span>  
  
3.  <span data-ttu-id="729a2-172">Client.exe \client\bin'nden başlatın.</span><span class="sxs-lookup"><span data-stu-id="729a2-172">Launch client.exe from \client\bin.</span></span> <span data-ttu-id="729a2-173">İstemci etkinliği istemci konsol uygulamasında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="729a2-173">Client activity is displayed on the client console application.</span></span>  
  
4.  <span data-ttu-id="729a2-174">İstemci ve hizmet iletişim kurabildiğini bilmiyorsanız bkz [WCF örnekleri için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="729a2-174">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="729a2-175">Bilgisayarlar arasında örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="729a2-175">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="729a2-176">Hizmet ikili dosyaları için hizmet bilgisayarda bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="729a2-176">Create a directory on the service computer for the service binaries.</span></span>  
  
2.  <span data-ttu-id="729a2-177">Hizmet program dosyaları hizmeti bilgisayarında hizmet dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="729a2-177">Copy the service program files to the service directory on the service computer.</span></span> <span data-ttu-id="729a2-178">Ayrıca Setup.bat ve Cleanup.bat dosyaları hizmet bilgisayara kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="729a2-178">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3.  <span data-ttu-id="729a2-179">Bilgisayarın tam etki alanı adını içeren konu adına sahip bir sunucu sertifikası olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="729a2-179">You must have a server certificate with the subject name that contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="729a2-180">Hizmet App.config dosyası, bu yeni sertifika adı yansıtacak şekilde güncelleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="729a2-180">The service App.config file must be updated to reflect this new certificate name.</span></span> <span data-ttu-id="729a2-181">Ayarlarsanız Setup.bat kullanarak bir tane oluşturabilirsiniz `%SERVER_NAME%` hizmet çalışacağı bilgisayarda tam ana bilgisayar adı için değişken.</span><span class="sxs-lookup"><span data-stu-id="729a2-181">You can create one by using the Setup.bat if you set the `%SERVER_NAME%` variable to fully-qualified host name of the computer on which the service will run.</span></span> <span data-ttu-id="729a2-182">Setup.bat dosyasının Visual Studio için geliştirici komut isteminden çalıştırılmalıdır Not yönetici ayrıcalıklarıyla açılan.</span><span class="sxs-lookup"><span data-stu-id="729a2-182">Note that the setup.bat file must be run from a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>  
  
4.  <span data-ttu-id="729a2-183">Sunucu sertifikasını istemcinin CurrentUser TrustedPeople depoya kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="729a2-183">Copy the server certificate into the CurrentUser-TrustedPeople store of the client.</span></span> <span data-ttu-id="729a2-184">Sunucu sertifikası olduğunda istemci güvenilen veren tarafından verilen dışında bunu gerekmez.</span><span class="sxs-lookup"><span data-stu-id="729a2-184">You do not need to do this except when the server certificate is issued by a client trusted issuer.</span></span>  
  
5.  <span data-ttu-id="729a2-185">Hizmet bilgisayarı App.config dosyasında localhost yerine tam bilgisayar adını belirtmek için temel adresini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="729a2-185">In the App.config file on the service computer, change the value of the base address to specify a fully-qualified computer name instead of localhost.</span></span>  
  
6.  <span data-ttu-id="729a2-186">Hizmet bilgisayarda service.exe bir komut isteminden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="729a2-186">On the service computer, run service.exe from a command prompt.</span></span>  
  
7.  <span data-ttu-id="729a2-187">İstemci program dosyaları \client\bin\ klasöründen dile özgü klasörünün altındaki istemci bilgisayara kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="729a2-187">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
8.  <span data-ttu-id="729a2-188">İstemci bilgisayarda Client.exe.config dosyasında hizmetinizin yeni adresiyle eşleşecek şekilde uç nokta adresi değiştirin.</span><span class="sxs-lookup"><span data-stu-id="729a2-188">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="729a2-189">İstemci bilgisayarda bir komut istemi'nden Client.exe başlatın.</span><span class="sxs-lookup"><span data-stu-id="729a2-189">On the client computer, launch Client.exe from a command prompt.</span></span>  
  
10. <span data-ttu-id="729a2-190">İstemci ve hizmet iletişim kurabildiğini bilmiyorsanız bkz [WCF örnekleri için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="729a2-190">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="729a2-191">Sonra örnek temizlemek için</span><span class="sxs-lookup"><span data-stu-id="729a2-191">To clean up after the sample</span></span>  
  
1.  <span data-ttu-id="729a2-192">Bu örneği çalıştırmadan tamamladıktan sonra Cleanup.bat samples klasöründe çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="729a2-192">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
