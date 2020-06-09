---
title: Belirteç Kimlik Doğrulayıcı
ms.date: 03/30/2017
ms.assetid: 84382f2c-f6b1-4c32-82fa-aebc8f6064db
ms.openlocfilehash: f4b49edd3b5a2cecd203feed713c7694450f7497
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596558"
---
# <a name="token-authenticator"></a><span data-ttu-id="7fc80-102">Belirteç Kimlik Doğrulayıcı</span><span class="sxs-lookup"><span data-stu-id="7fc80-102">Token Authenticator</span></span>
<span data-ttu-id="7fc80-103">Bu örnek, bir özel belirteç kimlik doğrulayıcısının nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7fc80-103">This sample demonstrates how to implement a custom token authenticator.</span></span> <span data-ttu-id="7fc80-104">Windows Communication Foundation (WCF) ' deki bir belirteç kimlik doğrulayıcısı, iletiyle kullanılan belirteci doğrulamak, kendinden tutarlı olduğunu doğrulamak ve belirteçle ilişkili kimliğin kimlik doğrulamasını yapmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7fc80-104">A token authenticator in Windows Communication Foundation (WCF) is used for validating the token used with the message, verifying that it is self-consistent, and authenticating the identity associated with the token.</span></span>

 <span data-ttu-id="7fc80-105">Özel belirteç kimlik doğrulayıcılar çeşitli durumlarda yararlı olur, örneğin:</span><span class="sxs-lookup"><span data-stu-id="7fc80-105">Custom token authenticators are useful in a variety of cases, such as:</span></span>

- <span data-ttu-id="7fc80-106">Bir belirteçle ilişkili varsayılan kimlik doğrulama mekanizmasını geçersiz kılmak istediğinizde.</span><span class="sxs-lookup"><span data-stu-id="7fc80-106">When you want to override the default authentication mechanism associated with a token.</span></span>

- <span data-ttu-id="7fc80-107">Özel bir belirteç oluştururken.</span><span class="sxs-lookup"><span data-stu-id="7fc80-107">When you are building a custom token.</span></span>

 <span data-ttu-id="7fc80-108">Bu örnek şunları gösterir:</span><span class="sxs-lookup"><span data-stu-id="7fc80-108">This sample demonstrates the following:</span></span>

- <span data-ttu-id="7fc80-109">Bir istemcinin Kullanıcı adı/parola çifti kullanarak kimlik doğrulaması yapabilir.</span><span class="sxs-lookup"><span data-stu-id="7fc80-109">How a client can authenticate using a username/password pair.</span></span>

- <span data-ttu-id="7fc80-110">Sunucu, özel bir belirteç kimlik doğrulayıcısı kullanarak istemci kimlik bilgilerini nasıl doğrulayabilirler.</span><span class="sxs-lookup"><span data-stu-id="7fc80-110">How the server can validate the client credentials using a custom token authenticator.</span></span>

- <span data-ttu-id="7fc80-111">WCF hizmeti kodu, özel belirteç kimlik doğrulayıcısı ile nasıl bir şekilde yapılır.</span><span class="sxs-lookup"><span data-stu-id="7fc80-111">How the WCF service code ties in with the custom token authenticator.</span></span>

- <span data-ttu-id="7fc80-112">Sunucunun X. 509.440 sertifikası kullanılarak nasıl kimlik doğrulaması yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="7fc80-112">How the server can be authenticated using the server's X.509 certificate.</span></span>

 <span data-ttu-id="7fc80-113">Bu örnek ayrıca, özel belirteç kimlik doğrulama işleminden sonra arayanın kimliğinin WCF 'den nasıl erişilebilir olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="7fc80-113">This sample also shows how the caller's identity is accessible from WCF after the custom token authentication process.</span></span>

 <span data-ttu-id="7fc80-114">Hizmet, App. config yapılandırma dosyası kullanılarak tanımlanan hizmetle iletişim kurmak için tek bir uç nokta sunar.</span><span class="sxs-lookup"><span data-stu-id="7fc80-114">The service exposes a single endpoint for communicating with the service, defined using the App.config configuration file.</span></span> <span data-ttu-id="7fc80-115">Uç nokta bir adres, bağlama ve bir anlaşmada oluşur.</span><span class="sxs-lookup"><span data-stu-id="7fc80-115">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="7fc80-116">Bağlama, `wsHttpBinding` güvenlik modunun ileti olarak ayarlandığı bir standart ile yapılandırılır. varsayılan modu `wsHttpBinding` .</span><span class="sxs-lookup"><span data-stu-id="7fc80-116">The binding is configured with a standard `wsHttpBinding`, with the security mode set to message - the default mode of the `wsHttpBinding`.</span></span> <span data-ttu-id="7fc80-117">Bu örnek, standart `wsHttpBinding` istemci Kullanıcı adı kimlik doğrulamasını kullanmak için standardı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="7fc80-117">This sample sets the standard `wsHttpBinding` to use client username authentication.</span></span> <span data-ttu-id="7fc80-118">Hizmet, davranışı kullanarak hizmet sertifikasını da yapılandırır `serviceCredentials` .</span><span class="sxs-lookup"><span data-stu-id="7fc80-118">The service also configures the service certificate using `serviceCredentials` behavior.</span></span> <span data-ttu-id="7fc80-119">`securityCredentials`Davranış, bir hizmet sertifikası belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="7fc80-119">The `securityCredentials` behavior allows you to specify a service certificate.</span></span> <span data-ttu-id="7fc80-120">Hizmet sertifikası, istemci tarafından hizmetin kimliğini doğrulamak ve ileti koruması sağlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7fc80-120">A service certificate is used by a client to authenticate the service and provide message protection.</span></span> <span data-ttu-id="7fc80-121">Aşağıdaki yapılandırma, aşağıdaki kurulum yönergelerinde açıklandığı gibi örnek kurulum sırasında yüklü olan localhost sertifikasına başvurur.</span><span class="sxs-lookup"><span data-stu-id="7fc80-121">The following configuration references the localhost certificate installed during the sample setup as described in the following setup instructions.</span></span>

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

 <span data-ttu-id="7fc80-122">İstemci uç noktası yapılandırması, bir yapılandırma adından, hizmet uç noktası için mutlak bir adresten, bağlamaya ve sözleşmeyle oluşur.</span><span class="sxs-lookup"><span data-stu-id="7fc80-122">The client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="7fc80-123">İstemci bağlama, uygun ve ile yapılandırılır `Mode` `clientCredentialType` .</span><span class="sxs-lookup"><span data-stu-id="7fc80-123">The client binding is configured with the appropriate `Mode` and `clientCredentialType`.</span></span>

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

 <span data-ttu-id="7fc80-124">İstemci uygulama, kullanılacak kullanıcı adını ve parolayı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="7fc80-124">The client implementation sets the user name and password to use.</span></span>

```csharp
static void Main()
{
     ...
     client.ClientCredentials.UserNamePassword.UserName = username;
     client.ClientCredentials.UserNamePassword.Password = password;
     ...
}
```

## <a name="custom-token-authenticator"></a><span data-ttu-id="7fc80-125">Özel belirteç kimlik doğrulayıcısı</span><span class="sxs-lookup"><span data-stu-id="7fc80-125">Custom Token Authenticator</span></span>
 <span data-ttu-id="7fc80-126">Özel bir belirteç kimlik doğrulayıcısı oluşturmak için aşağıdaki adımları kullanın:</span><span class="sxs-lookup"><span data-stu-id="7fc80-126">Use the following steps to create a custom token authenticator:</span></span>

1. <span data-ttu-id="7fc80-127">Özel bir belirteç kimlik doğrulayıcısı yazın.</span><span class="sxs-lookup"><span data-stu-id="7fc80-127">Write a custom token authenticator.</span></span>

     <span data-ttu-id="7fc80-128">Örnek, Kullanıcı adının geçerli bir e-posta biçimine sahip olduğunu doğrulayan bir özel belirteç Authenticator uygular.</span><span class="sxs-lookup"><span data-stu-id="7fc80-128">The sample implements a custom token authenticator that validates that the username has a valid email format.</span></span> <span data-ttu-id="7fc80-129">Türetir <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator> .</span><span class="sxs-lookup"><span data-stu-id="7fc80-129">It derives the <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator>.</span></span> <span data-ttu-id="7fc80-130">Bu sınıftaki en önemli Yöntem <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator.ValidateUserNamePasswordCore%28System.String%2CSystem.String%29> .</span><span class="sxs-lookup"><span data-stu-id="7fc80-130">The most important method in this class is <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator.ValidateUserNamePasswordCore%28System.String%2CSystem.String%29>.</span></span> <span data-ttu-id="7fc80-131">Bu yöntemde, Authenticator Kullanıcı adının biçimini doğrular ve ana bilgisayar adının sahte bir etki alanından olmaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="7fc80-131">In this method, the authenticator validates the format of the username and also that the host name is not from a rogue domain.</span></span> <span data-ttu-id="7fc80-132">Her iki koşul de karşılanıyorsa, daha sonra <xref:System.IdentityModel.Policy.IAuthorizationPolicy> Kullanıcı adı belirtecinin içinde depolanan bilgileri temsil eden talepler sağlamak için kullanılan, salt okunurdur bir örnek koleksiyonu döndürür.</span><span class="sxs-lookup"><span data-stu-id="7fc80-132">If both conditions are met, then it returns a read-only collection of <xref:System.IdentityModel.Policy.IAuthorizationPolicy> instances that is then used to provide claims that represent the information stored inside the username token.</span></span>

    ```csharp
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

2. <span data-ttu-id="7fc80-133">Özel belirteç kimlik doğrulayıcısı tarafından döndürülen bir yetkilendirme ilkesi sağlayın.</span><span class="sxs-lookup"><span data-stu-id="7fc80-133">Provide an authorization policy that is returned by custom token authenticator.</span></span>

     <span data-ttu-id="7fc80-134">Bu örnek, <xref:System.IdentityModel.Policy.IAuthorizationPolicy> `UnconditionalPolicy` Oluşturucusu içinde kendisine geçirilmiş talepler ve kimlikler kümesi döndüren çağrılan öğesinin kendi uygulamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="7fc80-134">This sample provides its own implementation of <xref:System.IdentityModel.Policy.IAuthorizationPolicy> called `UnconditionalPolicy` that returns set of claims and identities that were passed to it in its constructor.</span></span>

    ```csharp
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

3. <span data-ttu-id="7fc80-135">Özel bir güvenlik belirteci Yöneticisi yazın.</span><span class="sxs-lookup"><span data-stu-id="7fc80-135">Write a custom security token manager.</span></span>

     <span data-ttu-id="7fc80-136">, <xref:System.IdentityModel.Selectors.SecurityTokenManager> <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> Yöntemi içinde kendisine geçirilen belirli nesneler için bir oluşturmak için kullanılır `CreateSecurityTokenAuthenticator` .</span><span class="sxs-lookup"><span data-stu-id="7fc80-136">The <xref:System.IdentityModel.Selectors.SecurityTokenManager> is used to create a <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> for specific <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> objects that are passed to it in the `CreateSecurityTokenAuthenticator` method.</span></span> <span data-ttu-id="7fc80-137">Güvenlik belirteci Yöneticisi ayrıca belirteç sağlayıcıları ve belirteç serileştiricileri oluşturmak için kullanılır, ancak bunlar bu örnek tarafından kapsanmaz.</span><span class="sxs-lookup"><span data-stu-id="7fc80-137">The security token manager is also used to create token providers and token serializers, but those are not covered by this sample.</span></span> <span data-ttu-id="7fc80-138">Bu örnekte, özel güvenlik belirteci Yöneticisi <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> sınıfından devralır ve `CreateSecurityTokenAuthenticator` geçilen belirteç gereksinimleri Kullanıcı adı Doğrulayıcı 'nın istendiğini gösteriyorsa özel Kullanıcı adı belirteç kimlik doğrulayıcısı döndürecek şekilde yöntemi geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="7fc80-138">In this sample, the custom security token manager inherits from <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> class and overrides the `CreateSecurityTokenAuthenticator` method to return custom username token authenticator when the passed token requirements indicate that username authenticator is requested.</span></span>

    ```csharp
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

4. <span data-ttu-id="7fc80-139">Özel bir hizmet kimlik bilgisi yazın.</span><span class="sxs-lookup"><span data-stu-id="7fc80-139">Write a custom service credential.</span></span>

     <span data-ttu-id="7fc80-140">Hizmet kimlik bilgileri sınıfı, hizmet için yapılandırılan kimlik bilgilerini temsil etmek için kullanılır ve belirteç doğrulayıcılar, belirteç sağlayıcıları ve belirteç serileştiricileri elde etmek için kullanılan bir güvenlik belirteci Yöneticisi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7fc80-140">The service credentials class is used to represent the credentials that are configured for the service and creates a security token manager that is used to obtain token authenticators, token providers and token serializers.</span></span>

    ```csharp
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

5. <span data-ttu-id="7fc80-141">Hizmeti özel hizmet kimlik bilgilerini kullanacak şekilde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="7fc80-141">Configure the service to use the custom service credential.</span></span>

     <span data-ttu-id="7fc80-142">Hizmetin özel hizmet kimlik bilgisini kullanabilmesi için varsayılan hizmet kimlik bilgilerinde önceden yapılandırılmış hizmet sertifikasını yakaladıktan sonra varsayılan hizmet kimlik bilgisi sınıfını siler ve yeni hizmet kimlik bilgisi örneğini önceden yapılandırılmış hizmet sertifikalarını kullanacak şekilde yapılandırır ve bu yeni hizmet kimlik bilgileri örneğini hizmet davranışlarına ekler.</span><span class="sxs-lookup"><span data-stu-id="7fc80-142">In order for the service to use the custom service credential, we delete the default service credential class after capturing the service certificate that is already preconfigured in the default service credential, and configure the new service credential instance to use the preconfigured service certificates and add this new service credential instance to service behaviors.</span></span>

    ```csharp
    ServiceCredentials sc = serviceHost.Credentials;
    X509Certificate2 cert = sc.ServiceCertificate.Certificate;
    MyUserNameCredential serviceCredential = new MyUserNameCredential();
    serviceCredential.ServiceCertificate.Certificate = cert;
    serviceHost.Description.Behaviors.Remove((typeof(ServiceCredentials)));
    serviceHost.Description.Behaviors.Add(serviceCredential);
    ```

 <span data-ttu-id="7fc80-143">Arayanın bilgilerini göstermek için <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> aşağıdaki kodda gösterildiği gibi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7fc80-143">To display the caller's information, you can use the <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> as shown in the following code.</span></span> <span data-ttu-id="7fc80-144">, <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> Geçerli çağıran ile ilgili talep bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="7fc80-144">The <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> contains claims information about the current caller.</span></span>

```csharp
static void DisplayIdentityInformation()
{
    Console.WriteLine("\t\tSecurity context identity  :  {0}",
            ServiceSecurityContext.Current.PrimaryIdentity.Name);
     return;
}
```

 <span data-ttu-id="7fc80-145">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="7fc80-145">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="7fc80-146">İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="7fc80-146">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="7fc80-147">Toplu Iş dosyası kurulumu</span><span class="sxs-lookup"><span data-stu-id="7fc80-147">Setup Batch File</span></span>
 <span data-ttu-id="7fc80-148">Bu örneğe eklenen Setup. bat toplu iş dosyası, sunucu sertifikası tabanlı güvenlik gerektiren şirket içinde barındırılan bir uygulamayı çalıştırmak için sunucuyu ilgili sertifikalarla yapılandırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="7fc80-148">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate based security.</span></span> <span data-ttu-id="7fc80-149">Bu toplu iş dosyasının bilgisayarlarda çalışmak veya barındırılmayan bir durumda çalışması için değiştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="7fc80-149">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>

 <span data-ttu-id="7fc80-150">Aşağıdakiler, uygun yapılandırmada çalışacak şekilde değiştirilebilecek şekilde, toplu iş dosyalarının farklı bölümlerine kısa bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="7fc80-150">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in appropriate configuration.</span></span>

- <span data-ttu-id="7fc80-151">Sunucu sertifikası oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="7fc80-151">Creating the server certificate.</span></span>

     <span data-ttu-id="7fc80-152">Setup. bat toplu iş dosyasından aşağıdaki satırlar kullanılacak sunucu sertifikasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7fc80-152">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="7fc80-153">`%SERVER_NAME%`Değişken, sunucu adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="7fc80-153">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="7fc80-154">Kendi sunucu adınızı belirtmek için bu değişkeni değiştirin.</span><span class="sxs-lookup"><span data-stu-id="7fc80-154">Change this variable to specify your own server name.</span></span> <span data-ttu-id="7fc80-155">Bu toplu iş dosyasındaki varsayılan değer localhost 'tur.</span><span class="sxs-lookup"><span data-stu-id="7fc80-155">The default in this batch file is localhost.</span></span>

    ```console
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="7fc80-156">Sunucu sertifikasını istemcinin güvenilen sertifika deposuna yükleme.</span><span class="sxs-lookup"><span data-stu-id="7fc80-156">Installing the server certificate into client's trusted certificate store.</span></span>

     <span data-ttu-id="7fc80-157">Setup. bat toplu iş dosyası 'ndaki aşağıdaki satırlar, sunucu sertifikasını istemci güvenilir kişiler deposuna kopyalar.</span><span class="sxs-lookup"><span data-stu-id="7fc80-157">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="7fc80-158">Bu adım, MakeCert. exe tarafından oluşturulan sertifikaların istemci sistemi tarafından örtük olarak güvenilir olmadığından gereklidir.</span><span class="sxs-lookup"><span data-stu-id="7fc80-158">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="7fc80-159">İstemci tarafından güvenilen kök sertifikada kök sertifikaya sahip bir sertifikanız zaten varsa (örneğin, Microsoft tarafından verilen bir sertifika), istemci sertifikası deposunu sunucu sertifikasıyla doldurmanın bu adımı gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="7fc80-159">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

    > [!NOTE]
    > <span data-ttu-id="7fc80-160">Kurulum Batch dosyası bir Windows SDK komut Isteminden çalıştırılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="7fc80-160">The setup batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="7fc80-161">MSSDK ortam değişkeninin, SDK 'nın yüklü olduğu dizine işaret olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="7fc80-161">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="7fc80-162">Bu ortam değişkeni bir Windows SDK komut Istemi içinde otomatik olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="7fc80-162">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span>

#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="7fc80-163">Örneği ayarlamak ve derlemek için</span><span class="sxs-lookup"><span data-stu-id="7fc80-163">To set up and build the sample</span></span>

1. <span data-ttu-id="7fc80-164">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="7fc80-164">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="7fc80-165">Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="7fc80-165">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="7fc80-166">Örneği aynı bilgisayarda çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="7fc80-166">To run the sample on the same computer</span></span>

1. <span data-ttu-id="7fc80-167">Setup. bat dosyasını, bir Visual Studio 2012 komut istemi içindeki örnek yükleme klasöründen yönetici ayrıcalıklarıyla açılan bir şekilde çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7fc80-167">Run Setup.bat from the sample installation folder inside a Visual Studio 2012 command prompt opened with administrator privileges.</span></span> <span data-ttu-id="7fc80-168">Bu, örneği çalıştırmak için gereken tüm sertifikaları kurar.</span><span class="sxs-lookup"><span data-stu-id="7fc80-168">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="7fc80-169">Setup. bat toplu iş dosyası bir Visual Studio 2012 komut Isteminden çalıştırılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="7fc80-169">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="7fc80-170">Visual Studio 2012 komut Isteminde ayarlanan PATH ortam değişkeni Setup. bat betiği için gereken yürütülebilir dosyaları içeren dizine işaret eder.</span><span class="sxs-lookup"><span data-stu-id="7fc80-170">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2. <span data-ttu-id="7fc80-171">Service\bin. adresinden Service. exe ' yi Başlat</span><span class="sxs-lookup"><span data-stu-id="7fc80-171">Launch service.exe from service\bin.</span></span>  
  
3. <span data-ttu-id="7fc80-172">\Client\bin. adresinden Client. exe ' yi Başlat</span><span class="sxs-lookup"><span data-stu-id="7fc80-172">Launch client.exe from \client\bin.</span></span> <span data-ttu-id="7fc80-173">İstemci etkinliği istemci konsol uygulamasında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="7fc80-173">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="7fc80-174">İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="7fc80-174">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="7fc80-175">Örneği bilgisayarlar arasında çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="7fc80-175">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="7fc80-176">Hizmet ikili dosyaları için hizmet bilgisayarında bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7fc80-176">Create a directory on the service computer for the service binaries.</span></span>  
  
2. <span data-ttu-id="7fc80-177">Hizmet programı dosyalarını hizmet bilgisayarındaki hizmet dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="7fc80-177">Copy the service program files to the service directory on the service computer.</span></span> <span data-ttu-id="7fc80-178">Ayrıca Setup. bat ve Cleanup. bat dosyalarını da hizmet bilgisayarına kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="7fc80-178">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="7fc80-179">Bilgisayarın tam etki alanı adını içeren konu adına sahip bir sunucu sertifikasına sahip olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7fc80-179">You must have a server certificate with the subject name that contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="7fc80-180">Service App. config dosyasının bu yeni sertifika adını yansıtması için güncelleştirilmeleri gerekir.</span><span class="sxs-lookup"><span data-stu-id="7fc80-180">The service App.config file must be updated to reflect this new certificate name.</span></span> <span data-ttu-id="7fc80-181">`%SERVER_NAME%`Değişkenini Hizmetin çalıştırılacağı bilgisayarın tam ana bilgisayar adı olarak ayarlarsanız Setup. bat kullanarak bir tane oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7fc80-181">You can create one by using the Setup.bat if you set the `%SERVER_NAME%` variable to fully-qualified host name of the computer on which the service will run.</span></span> <span data-ttu-id="7fc80-182">Setup. bat dosyasının, yönetici ayrıcalıklarıyla açılan bir Visual Studio için Geliştirici Komut İstemi çalıştırılması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="7fc80-182">Note that the setup.bat file must be run from a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>  
  
4. <span data-ttu-id="7fc80-183">Sunucu sertifikasını istemcinin CurrentUser-Trustedkişilerim deposuna kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="7fc80-183">Copy the server certificate into the CurrentUser-TrustedPeople store of the client.</span></span> <span data-ttu-id="7fc80-184">Sunucu sertifikasının, istemci güvenilir veren tarafından verildiği durumlar dışında bunu yapmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="7fc80-184">You do not need to do this except when the server certificate is issued by a client trusted issuer.</span></span>  
  
5. <span data-ttu-id="7fc80-185">Hizmet bilgisayarındaki App. config dosyasında, temel adresin değerini localhost yerine tam nitelikli bir bilgisayar adı belirtecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="7fc80-185">In the App.config file on the service computer, change the value of the base address to specify a fully-qualified computer name instead of localhost.</span></span>  
  
6. <span data-ttu-id="7fc80-186">Hizmet bilgisayarında, komut isteminden Service. exe ' yi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7fc80-186">On the service computer, run service.exe from a command prompt.</span></span>  
  
7. <span data-ttu-id="7fc80-187">İstemci program dosyalarını dile özgü klasörün altındaki \client\bin\ klasöründen istemci bilgisayara kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="7fc80-187">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
8. <span data-ttu-id="7fc80-188">İstemci bilgisayardaki Client. exe. config dosyasında, uç noktanın adres değerini hizmetinizin yeni adresiyle eşleşecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="7fc80-188">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="7fc80-189">İstemci bilgisayarda, bir komut isteminden Client. exe ' yi başlatın.</span><span class="sxs-lookup"><span data-stu-id="7fc80-189">On the client computer, launch Client.exe from a command prompt.</span></span>  
  
10. <span data-ttu-id="7fc80-190">İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="7fc80-190">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="7fc80-191">Örnekten sonra temizlemek için</span><span class="sxs-lookup"><span data-stu-id="7fc80-191">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="7fc80-192">Örneği çalıştırmayı bitirdikten sonra Samples klasöründe Cleanup. bat dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7fc80-192">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
