---
title: Belirteç Sağlayıcı
ms.date: 03/30/2017
ms.assetid: 947986cf-9946-4987-84e5-a14678d96edb
ms.openlocfilehash: 9f008204c6ff8d3d134dbb17fc445b460f757f13
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038745"
---
# <a name="token-provider"></a><span data-ttu-id="4aefe-102">Belirteç Sağlayıcı</span><span class="sxs-lookup"><span data-stu-id="4aefe-102">Token Provider</span></span>
<span data-ttu-id="4aefe-103">Bu örnek, bir özel belirteç sağlayıcısının nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4aefe-103">This sample demonstrates how to implement a custom token provider.</span></span> <span data-ttu-id="4aefe-104">Güvenlik altyapısına kimlik bilgileri sağlamak için Windows Communication Foundation (WCF) içindeki bir belirteç sağlayıcısı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4aefe-104">A token provider in Windows Communication Foundation (WCF) is used for supplying credentials to the security infrastructure.</span></span> <span data-ttu-id="4aefe-105">Genel içindeki belirteç sağlayıcısı hedefi inceler ve güvenlik altyapısının iletiyi güvenli hale getirmek için uygun kimlik bilgilerini verir.</span><span class="sxs-lookup"><span data-stu-id="4aefe-105">The token provider in general examines the target and issues appropriate credentials so that the security infrastructure can secure the message.</span></span> <span data-ttu-id="4aefe-106">WCF varsayılan kimlik bilgileri Yöneticisi belirteç sağlayıcısıyla birlikte gelir.</span><span class="sxs-lookup"><span data-stu-id="4aefe-106">WCF ships with the default Credential Manager Token Provider.</span></span> <span data-ttu-id="4aefe-107">WCF Ayrıca bir CardSpace belirteç sağlayıcısıyla birlikte gelir.</span><span class="sxs-lookup"><span data-stu-id="4aefe-107">WCF also ships with a CardSpace token provider.</span></span> <span data-ttu-id="4aefe-108">Özel belirteç sağlayıcıları aşağıdaki durumlarda faydalıdır:</span><span class="sxs-lookup"><span data-stu-id="4aefe-108">Custom token providers are useful in the following cases:</span></span>

- <span data-ttu-id="4aefe-109">Bu belirteç sağlayıcılarının ile çalışamadığınız bir kimlik bilgisi depoluğiniz varsa.</span><span class="sxs-lookup"><span data-stu-id="4aefe-109">If you have a credential store that these token providers cannot operate with.</span></span>

- <span data-ttu-id="4aefe-110">Kullanıcı, WCF istemci çerçevesi kimlik bilgilerini kullandığında, kimlik bilgilerini bir noktadan dönüştürmek için kendi özel mekanizmanızı sağlamak istiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="4aefe-110">If you want to provide your own custom mechanism for transforming the credentials from the point when the user provides the details to when the WCF client framework uses the credentials.</span></span>

- <span data-ttu-id="4aefe-111">Özel bir belirteç oluşturuyorsanız.</span><span class="sxs-lookup"><span data-stu-id="4aefe-111">If you are building a custom token.</span></span>

 <span data-ttu-id="4aefe-112">Bu örnek, kullanıcıdan girişi farklı bir biçime dönüştüren özel bir belirteç sağlayıcısı oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="4aefe-112">This sample shows how to build a custom token provider that transforms the input from the user into a different format.</span></span>

 <span data-ttu-id="4aefe-113">Özetlemek gerekirse, bu örnek şunları gösterir:</span><span class="sxs-lookup"><span data-stu-id="4aefe-113">To summarize, this sample demonstrates the following:</span></span>

- <span data-ttu-id="4aefe-114">Bir istemcinin Kullanıcı adı/parola çifti kullanarak kimlik doğrulaması yapabilir.</span><span class="sxs-lookup"><span data-stu-id="4aefe-114">How a client can authenticate using a username/password pair.</span></span>

- <span data-ttu-id="4aefe-115">Bir istemcinin özel bir belirteç sağlayıcısıyla nasıl yapılandırılabileceğini.</span><span class="sxs-lookup"><span data-stu-id="4aefe-115">How a client can be configured with a custom token provider.</span></span>

- <span data-ttu-id="4aefe-116">Sunucunun, Kullanıcı adının ve parolanın eşleştiğini doğrulayan özel <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> bir parola kullanarak istemci kimlik bilgilerini nasıl doğrulayabileceğiniz.</span><span class="sxs-lookup"><span data-stu-id="4aefe-116">How the server can validate the client credentials using a password with a custom <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> that validates that the username and password match.</span></span>

- <span data-ttu-id="4aefe-117">Sunucunun, sunucunun X. 509.440 sertifikasını kullanarak istemci tarafından nasıl doğrulandığını.</span><span class="sxs-lookup"><span data-stu-id="4aefe-117">How the server is authenticated by the client using the server's X.509 certificate.</span></span>

 <span data-ttu-id="4aefe-118">Bu örnek ayrıca, özel belirteç kimlik doğrulama işleminden sonra arayanın kimliğinin nasıl erişilebilir olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="4aefe-118">This sample also shows how the caller's identity is accessible after the custom token authentication process.</span></span>

 <span data-ttu-id="4aefe-119">Hizmet, App. config yapılandırma dosyası kullanılarak tanımlanan hizmetle iletişim kurmak için tek bir uç nokta sunar.</span><span class="sxs-lookup"><span data-stu-id="4aefe-119">The service exposes a single endpoint for communicating with the service, defined using the App.config configuration file.</span></span> <span data-ttu-id="4aefe-120">Uç nokta bir adres, bağlama ve bir anlaşmada oluşur.</span><span class="sxs-lookup"><span data-stu-id="4aefe-120">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="4aefe-121">Bağlama, varsayılan olarak ileti güvenliği kullanan `wsHttpBinding`bir standart ile yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="4aefe-121">The binding is configured with a standard `wsHttpBinding`, which uses message security by default.</span></span> <span data-ttu-id="4aefe-122">Bu örnek, standart istemci `wsHttpBinding` Kullanıcı adı kimlik doğrulamasını kullanmak için standardı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4aefe-122">This sample sets the standard `wsHttpBinding` to use client username authentication.</span></span> <span data-ttu-id="4aefe-123">Hizmet Ayrıca, serviceCredentials davranışını kullanarak hizmet sertifikasını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="4aefe-123">The service also configures the service certificate using the serviceCredentials behavior.</span></span> <span data-ttu-id="4aefe-124">ServiceCredentials davranışı bir hizmet sertifikası yapılandırmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="4aefe-124">The serviceCredentials behavior allows you to configure a service certificate.</span></span> <span data-ttu-id="4aefe-125">Hizmet sertifikası, istemci tarafından hizmetin kimliğini doğrulamak ve ileti koruması sağlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4aefe-125">A service certificate is used by a client to authenticate the service and provide message protection.</span></span> <span data-ttu-id="4aefe-126">Aşağıdaki yapılandırma, aşağıdaki kurulum yönergelerinde açıklandığı gibi örnek kurulum sırasında yüklü olan localhost sertifikasına başvurur.</span><span class="sxs-lookup"><span data-stu-id="4aefe-126">The following configuration references the localhost certificate installed during the sample setup as described in the following setup instructions.</span></span>

```xml
<system.serviceModel>
    <services>
      <service
          name="Microsoft.ServiceModel.Samples.CalculatorService"
          behaviorConfiguration="CalculatorServiceBehavior">
        <host>
          <baseAddresses>
            <!-- configure base address provided by host -->
            <add baseAddress ="http://localhost:8000/servicemodelsamples/service"/>
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
        -->
          <serviceCredentials>
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />
          </serviceCredentials>
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
```

 <span data-ttu-id="4aefe-127">İstemci uç noktası yapılandırması, bir yapılandırma adından, hizmet uç noktası için mutlak bir adresten, bağlamaya ve sözleşmeyle oluşur.</span><span class="sxs-lookup"><span data-stu-id="4aefe-127">The client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="4aefe-128">İstemci bağlama, uygun `Mode` ve ileti `clientCredentialType`ile yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="4aefe-128">The client binding is configured with the appropriate `Mode` and message `clientCredentialType`.</span></span>

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

 <span data-ttu-id="4aefe-129">Aşağıdaki adımlarda, özel bir belirteç sağlayıcısının nasıl geliştirilmesi ve WCF güvenlik çerçevesiyle tümleştirileceği gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="4aefe-129">The following steps show how to develop a custom token provider and integrate it with the WCF security framework:</span></span>

1. <span data-ttu-id="4aefe-130">Özel bir belirteç sağlayıcısı yazın.</span><span class="sxs-lookup"><span data-stu-id="4aefe-130">Write a custom token provider.</span></span>

     <span data-ttu-id="4aefe-131">Örnek, Kullanıcı adını ve parolayı elde eden bir özel belirteç sağlayıcısı uygular.</span><span class="sxs-lookup"><span data-stu-id="4aefe-131">The sample implements a custom token provider that obtains the username and password.</span></span> <span data-ttu-id="4aefe-132">Parolanın bu kullanıcı adıyla eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="4aefe-132">The password must match this username.</span></span> <span data-ttu-id="4aefe-133">Bu özel belirteç sağlayıcısı yalnızca tanıtım amaçlıdır ve gerçek dünya dağıtımı için önerilmez.</span><span class="sxs-lookup"><span data-stu-id="4aefe-133">This custom token provider is for demonstration purposes only and is not recommended for real world deployment.</span></span>

     <span data-ttu-id="4aefe-134">Bu görevi gerçekleştirmek için özel belirteç sağlayıcısı <xref:System.IdentityModel.Selectors.SecurityTokenProvider> sınıfı türetir ve <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> yöntemini geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="4aefe-134">To perform this task, the custom token provider derives the <xref:System.IdentityModel.Selectors.SecurityTokenProvider> class and overrides the <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> method.</span></span> <span data-ttu-id="4aefe-135">Bu yöntem, oluşturur ve yeni `UserNameSecurityToken`bir döndürür.</span><span class="sxs-lookup"><span data-stu-id="4aefe-135">This method creates and returns a new `UserNameSecurityToken`.</span></span>

    ```csharp
    protected override SecurityToken GetTokenCore(TimeSpan timeout)
    {
        // obtain username and password from the user using console window
        string username = GetUserName();
        string password = GetPassword();
        Console.WriteLine("username: {0}", username);

        // return new UserNameSecurityToken containing information obtained from user
        return new UserNameSecurityToken(username, password);
    }
    ```

2. <span data-ttu-id="4aefe-136">Özel güvenlik belirteci Yöneticisi yazın.</span><span class="sxs-lookup"><span data-stu-id="4aefe-136">Write custom security token manager.</span></span>

     <span data-ttu-id="4aefe-137">, <xref:System.IdentityModel.Selectors.SecurityTokenManager> Yöntemi içinde <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> <xref:System.IdentityModel.Selectors.SecurityTokenProvider> kendisinegeçirilenbelirlibiroluşturmakiçinkullanılır`CreateSecurityTokenProvider` .</span><span class="sxs-lookup"><span data-stu-id="4aefe-137">The <xref:System.IdentityModel.Selectors.SecurityTokenManager> is used to create <xref:System.IdentityModel.Selectors.SecurityTokenProvider> for specific <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> that is passed to it in `CreateSecurityTokenProvider` method.</span></span> <span data-ttu-id="4aefe-138">Güvenlik belirteci Yöneticisi, belirteç doğrulayıcılar ve bir belirteç seri hale getirici oluşturmak için de kullanılır, ancak bunlar bu örnek tarafından kapsanmaz.</span><span class="sxs-lookup"><span data-stu-id="4aefe-138">Security token manager is also used to create token authenticators and a token serializer, but those are not covered by this sample.</span></span> <span data-ttu-id="4aefe-139">Bu örnekte, özel güvenlik belirteci Yöneticisi <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> sınıfından devralır ve geçilen belirteç gereksinimleri Kullanıcı adı sağlayıcısının istendiğini gösteriyorsa özel Kullanıcı adı belirteci sağlayıcısını döndürecek şekilde `CreateSecurityTokenProvider` geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="4aefe-139">In this sample, the custom security token manager inherits from <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> class and overrides the `CreateSecurityTokenProvider` method to return custom username token provider when the passed token requirements indicate that username provider is requested.</span></span>

    ```csharp
    public class MyUserNameSecurityTokenManager : ClientCredentialsSecurityTokenManager
    {
        MyUserNameClientCredentials myUserNameClientCredentials;

        public MyUserNameSecurityTokenManager(MyUserNameClientCredentials myUserNameClientCredentials)
            : base(myUserNameClientCredentials)
        {
            this.myUserNameClientCredentials = myUserNameClientCredentials;
        }

        public override SecurityTokenProvider CreateSecurityTokenProvider(SecurityTokenRequirement tokenRequirement)
        {
            // if token requirement matches username token return custom username token provider
            // otherwise use base implementation
            if (tokenRequirement.TokenType == SecurityTokenTypes.UserName)
            {
                return new MyUserNameTokenProvider();
            }
            else
            {
                return base.CreateSecurityTokenProvider(tokenRequirement);
            }
        }
    }
    ```

3. <span data-ttu-id="4aefe-140">Özel bir istemci kimlik bilgisi yazın.</span><span class="sxs-lookup"><span data-stu-id="4aefe-140">Write a custom client credential.</span></span>

     <span data-ttu-id="4aefe-141">İstemci kimlik bilgileri sınıfı, istemci ara sunucusu için yapılandırılan kimlik bilgilerini temsil etmek için kullanılır ve belirteç doğrulayıcılar, belirteç sağlayıcıları ve bir belirteç serileştirici elde etmek için kullanılan güvenlik belirteci Yöneticisi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4aefe-141">Client credentials class is used to represent the credentials that are configured for the client proxy and creates security token manager that is used to obtain token authenticators, token providers and a token serializer.</span></span>

    ```csharp
    public class MyUserNameClientCredentials : ClientCredentials
    {
        public MyUserNameClientCredentials()
            : base()
        {
        }

        protected override ClientCredentials CloneCore()
        {
            return new MyUserNameClientCredentials();
        }

        public override SecurityTokenManager CreateSecurityTokenManager()
        {
            // return custom security token manager
            return new MyUserNameSecurityTokenManager(this);
        }
    }
    ```

4. <span data-ttu-id="4aefe-142">İstemciyi özel istemci kimlik bilgilerini kullanacak şekilde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="4aefe-142">Configure the client to use the custom client credential.</span></span>

     <span data-ttu-id="4aefe-143">İstemcinin özel istemci kimlik bilgisini kullanabilmesi için, örnek varsayılan istemci kimlik bilgisi sınıfını siler ve yeni istemci kimlik bilgisi sınıfını sağlar.</span><span class="sxs-lookup"><span data-stu-id="4aefe-143">In order for the client to use the custom client credential, the sample deletes the default client credential class and supplies the new client credential class.</span></span>

    ```csharp
    static void Main()
    {
        // ...
           // Create a client with given client endpoint configuration
          CalculatorClient client = new CalculatorClient();

          // set new credentials
           client.ChannelFactory.Endpoint.Behaviors.Remove(typeof(ClientCredentials));
         client.ChannelFactory.Endpoint.Behaviors.Add(new MyUserNameClientCredentials());
       // ...
    }
    ```

 <span data-ttu-id="4aefe-144">Hizmette, arayanın bilgilerini göstermek için, aşağıdaki kod örneğinde gösterildiği <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> gibi kullanın.</span><span class="sxs-lookup"><span data-stu-id="4aefe-144">On the service, to display the caller's information, use the <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> as shown in the following code example.</span></span> <span data-ttu-id="4aefe-145">, <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> Geçerli çağıran ile ilgili talep bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="4aefe-145">The <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> contains claims information about the current caller.</span></span>

```csharp
static void DisplayIdentityInformation()
{
    Console.WriteLine("\t\tSecurity context identity  :  {0}",
        ServiceSecurityContext.Current.PrimaryIdentity.Name);
}
```

 <span data-ttu-id="4aefe-146">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="4aefe-146">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="4aefe-147">İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="4aefe-147">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="4aefe-148">Toplu Iş dosyası kurulumu</span><span class="sxs-lookup"><span data-stu-id="4aefe-148">Setup Batch File</span></span>
 <span data-ttu-id="4aefe-149">Bu örneğe eklenen Setup. bat toplu iş dosyası, sunucu sertifika tabanlı güvenlik gerektiren şirket içinde barındırılan bir uygulamayı çalıştırmak için sunucuyu ilgili sertifikayla yapılandırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="4aefe-149">The Setup.bat batch file included with this sample allows you to configure the server with the relevant certificate to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="4aefe-150">Bu toplu iş dosyasının bilgisayarlarda çalışmak veya barındırılmayan bir durumda çalışması için değiştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="4aefe-150">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>

 <span data-ttu-id="4aefe-151">Aşağıdakiler, uygun yapılandırmada çalışacak şekilde değiştirilebilecek şekilde, toplu iş dosyalarının farklı bölümlerine kısa bir genel bakış sunar:</span><span class="sxs-lookup"><span data-stu-id="4aefe-151">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration:</span></span>

- <span data-ttu-id="4aefe-152">Sunucu sertifikası oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="4aefe-152">Creating the server certificate.</span></span>

     <span data-ttu-id="4aefe-153">Setup. bat toplu iş dosyasından aşağıdaki satırlar kullanılacak sunucu sertifikasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4aefe-153">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="4aefe-154">`%SERVER_NAME%` Değişken, sunucu adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4aefe-154">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="4aefe-155">Kendi sunucu adınızı belirtmek için bu değişkeni değiştirin.</span><span class="sxs-lookup"><span data-stu-id="4aefe-155">Change this variable to specify your own server name.</span></span> <span data-ttu-id="4aefe-156">Bu toplu iş dosyasındaki varsayılan değer localhost 'tur.</span><span class="sxs-lookup"><span data-stu-id="4aefe-156">The default value in this batch file is localhost.</span></span>

    ```
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="4aefe-157">Sunucu sertifikasını istemcinin güvenilen sertifika deposuna yükleme:</span><span class="sxs-lookup"><span data-stu-id="4aefe-157">Installing the server certificate into the client's trusted certificate store:</span></span>

     <span data-ttu-id="4aefe-158">Setup. bat toplu iş dosyası 'ndaki aşağıdaki satırlar, sunucu sertifikasını istemci güvenilir kişiler deposuna kopyalar.</span><span class="sxs-lookup"><span data-stu-id="4aefe-158">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="4aefe-159">Bu adım, MakeCert. exe tarafından oluşturulan sertifikaların istemci sistemi tarafından örtük olarak güvenilir olmadığından gereklidir.</span><span class="sxs-lookup"><span data-stu-id="4aefe-159">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="4aefe-160">İstemci tarafından güvenilen kök sertifikada kök sertifikaya sahip bir sertifikanız zaten varsa (örneğin, Microsoft tarafından verilen bir sertifika), istemci sertifikası deposunu sunucu sertifikasıyla doldurmanın bu adımı gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="4aefe-160">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

> [!NOTE]
> <span data-ttu-id="4aefe-161">Setup. bat toplu iş dosyası bir Windows SDK komut Isteminden çalıştırılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="4aefe-161">The Setup.bat batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="4aefe-162">MSSDK ortam değişkeninin, SDK 'nın yüklü olduğu dizine işaret olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="4aefe-162">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="4aefe-163">Bu ortam değişkeni bir Windows SDK komut Istemi içinde otomatik olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="4aefe-163">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span>

#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="4aefe-164">Örneği ayarlamak ve derlemek için</span><span class="sxs-lookup"><span data-stu-id="4aefe-164">To set up and build the sample</span></span>

1. <span data-ttu-id="4aefe-165">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="4aefe-165">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="4aefe-166">Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="4aefe-166">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="4aefe-167">Örneği aynı bilgisayarda çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="4aefe-167">To run the sample on the same computer</span></span>

1. <span data-ttu-id="4aefe-168">Setup. bat dosyasını, bir Visual Studio 2012 komut istemi içindeki örnek yükleme klasöründen yönetici ayrıcalıklarıyla açılan bir şekilde çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="4aefe-168">Run Setup.bat from the sample installation folder inside a Visual Studio 2012 command prompt opened with administrator privileges.</span></span> <span data-ttu-id="4aefe-169">Bu, örneği çalıştırmak için gereken tüm sertifikaları kurar.</span><span class="sxs-lookup"><span data-stu-id="4aefe-169">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="4aefe-170">Setup. bat toplu iş dosyası bir Visual Studio 2012 komut Isteminden çalıştırılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="4aefe-170">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="4aefe-171">Visual Studio 2012 komut Isteminde ayarlanan PATH ortam değişkeni Setup. bat betiği için gereken yürütülebilir dosyaları içeren dizine işaret eder.</span><span class="sxs-lookup"><span data-stu-id="4aefe-171">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2. <span data-ttu-id="4aefe-172">Service\bin. adresinden Service. exe ' yi Başlat</span><span class="sxs-lookup"><span data-stu-id="4aefe-172">Launch service.exe from service\bin.</span></span>  
  
3. <span data-ttu-id="4aefe-173">\Client\bin. adresinden Client. exe ' yi Başlat</span><span class="sxs-lookup"><span data-stu-id="4aefe-173">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="4aefe-174">İstemci etkinliği istemci konsol uygulamasında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="4aefe-174">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="4aefe-175">Kullanıcı adı istemine bir Kullanıcı adı yazın.</span><span class="sxs-lookup"><span data-stu-id="4aefe-175">At the username prompt, type a user name.</span></span>  
  
5. <span data-ttu-id="4aefe-176">Parola isteminde, Kullanıcı adı istemi için yazılan dizeyi kullanın.</span><span class="sxs-lookup"><span data-stu-id="4aefe-176">At the password prompt, use the same string that was typed for the username prompt.</span></span>  
  
6. <span data-ttu-id="4aefe-177">İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="4aefe-177">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="4aefe-178">Örneği bilgisayarlar arasında çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="4aefe-178">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="4aefe-179">Hizmet ikili dosyaları için hizmet bilgisayarında bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="4aefe-179">Create a directory on the service computer for the service binaries.</span></span>  
  
2. <span data-ttu-id="4aefe-180">Hizmet programı dosyalarını hizmet bilgisayarındaki hizmet dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="4aefe-180">Copy the service program files to the service directory on the service computer.</span></span> <span data-ttu-id="4aefe-181">Ayrıca Setup. bat ve Cleanup. bat dosyalarını da hizmet bilgisayarına kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="4aefe-181">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="4aefe-182">Bilgisayarın tam etki alanı adını içeren konu adına sahip bir sunucu sertifikasına sahip olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4aefe-182">You must have a server certificate with the subject name that contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="4aefe-183">Service. exe. config dosyasının bu yeni sertifika adını yansıtması için güncelleştirilmeleri gerekir.</span><span class="sxs-lookup"><span data-stu-id="4aefe-183">The Service.exe.config file must be updated to reflect this new certificate name.</span></span> <span data-ttu-id="4aefe-184">Setup. bat toplu iş dosyasını değiştirerek sunucu sertifikası oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4aefe-184">You can create server certificate by modifying the Setup.bat batch file.</span></span> <span data-ttu-id="4aefe-185">Setup. bat dosyasının, yönetici ayrıcalıklarıyla açılan bir Visual Studio için Geliştirici Komut İstemi çalıştırılması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="4aefe-185">Note that the setup.bat file must be run from a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="4aefe-186">Değişkeni, hizmeti `%SERVER_NAME%` barındırmak için kullanılan bilgisayarın tam olarak nitelenmiş ana bilgisayar adına ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4aefe-186">You must set `%SERVER_NAME%` variable to fully-qualified host name of the computer that is used to host the service.</span></span>  
  
4. <span data-ttu-id="4aefe-187">Sunucu sertifikasını istemcinin CurrentUser-Trustedkişilerim deposuna kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="4aefe-187">Copy the server certificate into the CurrentUser-TrustedPeople store of the client.</span></span> <span data-ttu-id="4aefe-188">Sunucu sertifikası, istemci güvenilir veren tarafından verildiğinde bunu yapmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="4aefe-188">You do not need to do this when the server certificate is issued by a client trusted issuer.</span></span>  
  
5. <span data-ttu-id="4aefe-189">Hizmet bilgisayarındaki Service. exe. config dosyasında, temel adresin değerini localhost yerine tam nitelikli bir bilgisayar adı belirtecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="4aefe-189">In the Service.exe.config file on the service computer, change the value of the base address to specify a fully-qualified computer name instead of localhost.</span></span>  
  
6. <span data-ttu-id="4aefe-190">Hizmet bilgisayarında, komut isteminden Service. exe ' yi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="4aefe-190">On the service computer, run service.exe from a command prompt.</span></span>  
  
7. <span data-ttu-id="4aefe-191">İstemci program dosyalarını dile özgü klasörün altındaki \client\bin\ klasöründen istemci bilgisayara kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="4aefe-191">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
8. <span data-ttu-id="4aefe-192">İstemci bilgisayardaki Client. exe. config dosyasında, uç noktanın adres değerini hizmetinizin yeni adresiyle eşleşecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="4aefe-192">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="4aefe-193">İstemci bilgisayarda, bir komut istemi `Client.exe` penceresinden başlatın.</span><span class="sxs-lookup"><span data-stu-id="4aefe-193">On the client computer, launch `Client.exe` from a command prompt window.</span></span>  
  
10. <span data-ttu-id="4aefe-194">İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="4aefe-194">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="4aefe-195">Örnekten sonra temizlemek için</span><span class="sxs-lookup"><span data-stu-id="4aefe-195">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="4aefe-196">Örneği çalıştırmayı bitirdikten sonra Samples klasöründe Cleanup. bat dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="4aefe-196">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
