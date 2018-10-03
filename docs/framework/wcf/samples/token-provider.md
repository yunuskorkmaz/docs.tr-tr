---
title: Belirteç Sağlayıcı
ms.date: 03/30/2017
ms.assetid: 947986cf-9946-4987-84e5-a14678d96edb
author: BrucePerlerMS
ms.openlocfilehash: b7b7750b51450d3b5d31b8034a20317ba03c49a4
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48030148"
---
# <a name="token-provider"></a><span data-ttu-id="41cc1-102">Belirteç Sağlayıcı</span><span class="sxs-lookup"><span data-stu-id="41cc1-102">Token Provider</span></span>
<span data-ttu-id="41cc1-103">Bu örnek, özel bir belirteç sağlayıcısını uygulamak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="41cc1-103">This sample demonstrates how to implement a custom token provider.</span></span> <span data-ttu-id="41cc1-104">Windows Communication Foundation (WCF) bir belirteç sağlayıcısı güvenlik altyapısı için kimlik bilgilerini sağlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="41cc1-104">A token provider in Windows Communication Foundation (WCF) is used for supplying credentials to the security infrastructure.</span></span> <span data-ttu-id="41cc1-105">Belirteç sağlayıcı genel hedef inceler ve böylece ileti güvenlik altyapısı güvenli hale getirebilirsiniz, kimlik bilgileri sorunları uygun.</span><span class="sxs-lookup"><span data-stu-id="41cc1-105">The token provider in general examines the target and issues appropriate credentials so that the security infrastructure can secure the message.</span></span> <span data-ttu-id="41cc1-106">WCF varsayılan kimlik bilgileri Yöneticisi belirteç sağlayıcısı ile birlikte gelir.</span><span class="sxs-lookup"><span data-stu-id="41cc1-106">WCF ships with the default Credential Manager Token Provider.</span></span> <span data-ttu-id="41cc1-107">WCF ayrıca ile birlikte gelir bir [!INCLUDE[infocard](../../../../includes/infocard-md.md)] belirteç sağlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="41cc1-107">WCF also ships with an [!INCLUDE[infocard](../../../../includes/infocard-md.md)] token provider.</span></span> <span data-ttu-id="41cc1-108">Özel belirteç sağlayıcıları, aşağıdaki durumlarda kullanışlıdır:</span><span class="sxs-lookup"><span data-stu-id="41cc1-108">Custom token providers are useful in the following cases:</span></span>  
  
-   <span data-ttu-id="41cc1-109">Bu belirteci sağlayıcıları ile çalışamaz bir kimlik bilgisi deposu varsa.</span><span class="sxs-lookup"><span data-stu-id="41cc1-109">If you have a credential store that these token providers cannot operate with.</span></span>  
  
-   <span data-ttu-id="41cc1-110">Kullanıcı için WCF istemci framework kimlik bilgileri kullandığında ayrıntıları sağladığında noktadan kimlik dönüştürme için kendi özel mekanizması sağlamak istiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="41cc1-110">If you want to provide your own custom mechanism for transforming the credentials from the point when the user provides the details to when the WCF client framework uses the credentials.</span></span>  
  
-   <span data-ttu-id="41cc1-111">Özel belirteç oluşturuluyorsa.</span><span class="sxs-lookup"><span data-stu-id="41cc1-111">If you are building a custom token.</span></span>  
  
 <span data-ttu-id="41cc1-112">Bu örnek, kullanıcı girişini başka bir biçime dönüştürür özel bir belirteç sağlayıcısı oluşturmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="41cc1-112">This sample shows how to build a custom token provider that transforms the input from the user into a different format.</span></span>  
  
 <span data-ttu-id="41cc1-113">Özetlemek gerekirse, bu örnek aşağıdaki gösterir:</span><span class="sxs-lookup"><span data-stu-id="41cc1-113">To summarize, this sample demonstrates the following:</span></span>  
  
-   <span data-ttu-id="41cc1-114">Nasıl bir istemci bir kullanıcı adı/parola çifti kullanarak kimlik doğrulaması yapabilir.</span><span class="sxs-lookup"><span data-stu-id="41cc1-114">How a client can authenticate using a username/password pair.</span></span>  
  
-   <span data-ttu-id="41cc1-115">Nasıl bir istemci özel bir belirteç sağlayıcısı ile yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="41cc1-115">How a client can be configured with a custom token provider.</span></span>  
  
-   <span data-ttu-id="41cc1-116">Sunucunun istemci kimlik bilgileri ile özel bir parola ile nasıl doğrulayabilirsiniz <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> kullanıcı adı ve parola eşleştiğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="41cc1-116">How the server can validate the client credentials using a password with a custom <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> that validates that the username and password match.</span></span>  
  
-   <span data-ttu-id="41cc1-117">Sunucu, sunucunun X.509 sertifikası kullanarak istemci tarafından nasıl doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="41cc1-117">How the server is authenticated by the client using the server's X.509 certificate.</span></span>  
  
 <span data-ttu-id="41cc1-118">Ayrıca bu örnek nasıl çağıranının kimliğini özel belirteç kimlik doğrulama işleminden sonra erişilebilir gösterir.</span><span class="sxs-lookup"><span data-stu-id="41cc1-118">This sample also shows how the caller's identity is accessible after the custom token authentication process.</span></span>  
  
 <span data-ttu-id="41cc1-119">Hizmet, App.config yapılandırma dosyası kullanılarak tanımlanmış hizmet ile iletişim kurmak için tek bir uç noktayı kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="41cc1-119">The service exposes a single endpoint for communicating with the service, defined using the App.config configuration file.</span></span> <span data-ttu-id="41cc1-120">Uç nokta, adres, bağlama ve bir sözleşme oluşur.</span><span class="sxs-lookup"><span data-stu-id="41cc1-120">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="41cc1-121">Bir standart yapılandırılmış bağlama `wsHttpBinding`, hangi kullanır, varsayılan olarak güvenlik iletisi.</span><span class="sxs-lookup"><span data-stu-id="41cc1-121">The binding is configured with a standard `wsHttpBinding`, which uses message security by default.</span></span> <span data-ttu-id="41cc1-122">Bu örnek, standart ayarlar `wsHttpBinding` istemci kullanıcı adı kimlik doğrulaması kullanmak için.</span><span class="sxs-lookup"><span data-stu-id="41cc1-122">This sample sets the standard `wsHttpBinding` to use client username authentication.</span></span> <span data-ttu-id="41cc1-123">Hizmet Ayrıca hizmet sertifikası serviceCredentials davranışını kullanarak yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="41cc1-123">The service also configures the service certificate using the serviceCredentials behavior.</span></span> <span data-ttu-id="41cc1-124">ServiceCredentials davranışı, bir hizmet sertifikası yapılandırmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="41cc1-124">The serviceCredentials behavior allows you to configure a service certificate.</span></span> <span data-ttu-id="41cc1-125">Bir hizmet sertifikası, hizmet kimlik doğrulaması ve ileti koruma sağlamak için bir istemci tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="41cc1-125">A service certificate is used by a client to authenticate the service and provide message protection.</span></span> <span data-ttu-id="41cc1-126">Aşağıdaki yapılandırmayı aşağıdaki Kurulum yönergelerinde açıklandığı gibi örnek Kurulum sırasında yüklenen localhost sertifikasına başvuruda bulunuyor.</span><span class="sxs-lookup"><span data-stu-id="41cc1-126">The following configuration references the localhost certificate installed during the sample setup as described in the following setup instructions.</span></span>  
  
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
  
 <span data-ttu-id="41cc1-127">İstemci uç nokta yapılandırması mutlak bir adres için hizmet uç noktası, bağlama ve sözleşmenin bir yapılandırma adı oluşur.</span><span class="sxs-lookup"><span data-stu-id="41cc1-127">The client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="41cc1-128">Bağlama istemcinin uygun olarak yapılandırıldığı `Mode` ve ileti `clientCredentialType`.</span><span class="sxs-lookup"><span data-stu-id="41cc1-128">The client binding is configured with the appropriate `Mode` and message `clientCredentialType`.</span></span>  
  
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
  
 <span data-ttu-id="41cc1-129">Aşağıdaki adımlarda, özel bir belirteç sağlayıcısını geliştirin ve WCF güvenlik çerçevesi ile tümleştirmek gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="41cc1-129">The following steps show how to develop a custom token provider and integrate it with the WCF security framework:</span></span>  
  
1.  <span data-ttu-id="41cc1-130">Özel bir belirteç sağlayıcısını yazın.</span><span class="sxs-lookup"><span data-stu-id="41cc1-130">Write a custom token provider.</span></span>  
  
     <span data-ttu-id="41cc1-131">Örnek kullanıcı adı ve parola özel bir belirteç sağlayıcısını uygular.</span><span class="sxs-lookup"><span data-stu-id="41cc1-131">The sample implements a custom token provider that obtains the username and password.</span></span> <span data-ttu-id="41cc1-132">Bu kullanıcı adı parola eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="41cc1-132">The password must match this username.</span></span> <span data-ttu-id="41cc1-133">Bu özel belirteç sağlayıcısı, yalnızca gösterim amaçlıdır ve gerçek dünya dağıtım önerilmez.</span><span class="sxs-lookup"><span data-stu-id="41cc1-133">This custom token provider is for demonstration purposes only and is not recommended for real world deployment.</span></span>  
  
     <span data-ttu-id="41cc1-134">Bu görevi gerçekleştirmek için özel belirteç sağlayıcısı türetilen <xref:System.IdentityModel.Selectors.SecurityTokenProvider> sınıf ve geçersiz kılmaları <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="41cc1-134">To perform this task, the custom token provider derives the <xref:System.IdentityModel.Selectors.SecurityTokenProvider> class and overrides the <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> method.</span></span> <span data-ttu-id="41cc1-135">Bu yöntem, oluşturur ve yeni bir `UserNameSecurityToken`.</span><span class="sxs-lookup"><span data-stu-id="41cc1-135">This method creates and returns a new `UserNameSecurityToken`.</span></span>  
  
    ```  
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
  
2.  <span data-ttu-id="41cc1-136">Özel güvenlik belirteci Yöneticisi'ni yazın.</span><span class="sxs-lookup"><span data-stu-id="41cc1-136">Write custom security token manager.</span></span>  
  
     <span data-ttu-id="41cc1-137"><xref:System.IdentityModel.Selectors.SecurityTokenManager> Oluşturmak için kullanılan <xref:System.IdentityModel.Selectors.SecurityTokenProvider> belirli <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> kendisine geçirilen `CreateSecurityTokenProvider` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="41cc1-137">The <xref:System.IdentityModel.Selectors.SecurityTokenManager> is used to create <xref:System.IdentityModel.Selectors.SecurityTokenProvider> for specific <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> that is passed to it in `CreateSecurityTokenProvider` method.</span></span> <span data-ttu-id="41cc1-138">Güvenlik belirteci Yöneticisi ayrıca belirteç Doğrulayıcı ve belirteci seri hale getirici oluşturmak için kullanılır, ancak bunlar Bu örnek tarafından ele alınmamıştır.</span><span class="sxs-lookup"><span data-stu-id="41cc1-138">Security token manager is also used to create token authenticators and a token serializer, but those are not covered by this sample.</span></span> <span data-ttu-id="41cc1-139">Bu örnekte, özel güvenlik belirteci yöneticisi devraldığı <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> sınıf ve geçersiz kılmaları `CreateSecurityTokenProvider` geçirilen belirteci gereksinimleri, kullanıcı adı sağlayıcı belirttiğinizde, özel kullanıcı adı belirteci sağlayıcısı döndürülecek yöntemi istendi.</span><span class="sxs-lookup"><span data-stu-id="41cc1-139">In this sample, the custom security token manager inherits from <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> class and overrides the `CreateSecurityTokenProvider` method to return custom username token provider when the passed token requirements indicate that username provider is requested.</span></span>  
  
    ```  
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
  
3.  <span data-ttu-id="41cc1-140">Özel istemci kimlik bilgilerini yazın.</span><span class="sxs-lookup"><span data-stu-id="41cc1-140">Write a custom client credential.</span></span>  
  
     <span data-ttu-id="41cc1-141">İstemci kimlik bilgileri sınıfı istemci proxy'si için yapılandırıldığında kimlik bilgilerini temsil etmek için kullanılır ve güvenlik belirteci kimlik doğrulayıcılar, belirteç sağlayıcıları ve belirteci serileştiriciye elde etmek için kullanılan belirteci yöneticisi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="41cc1-141">Client credentials class is used to represent the credentials that are configured for the client proxy and creates security token manager that is used to obtain token authenticators, token providers and a token serializer.</span></span>  
  
    ```  
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
  
4.  <span data-ttu-id="41cc1-142">Özel istemci kimlik bilgilerini kullanacak biçimde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="41cc1-142">Configure the client to use the custom client credential.</span></span>  
  
     <span data-ttu-id="41cc1-143">Özel istemci kimlik bilgilerini kullanmak üzere istemciyi sırasıyla örneği, varsayılan istemci kimlik bilgisi sınıfını siler ve yeni istemci kimlik bilgisi sınıfını sağlar.</span><span class="sxs-lookup"><span data-stu-id="41cc1-143">In order for the client to use the custom client credential, the sample deletes the default client credential class and supplies the new client credential class.</span></span>  
  
    ```  
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
  
 <span data-ttu-id="41cc1-144">Arayanın bilgileri görüntülemek için bu hizmeti üzerinde kullanan <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> aşağıdaki kod örneğinde gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="41cc1-144">On the service, to display the caller's information, use the <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> as shown in the following code example.</span></span> <span data-ttu-id="41cc1-145"><xref:System.ServiceModel.ServiceSecurityContext.Current%2A> Talep geçerli arayanı hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="41cc1-145">The <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> contains claims information about the current caller.</span></span>  
  
```  
static void DisplayIdentityInformation()  
{  
    Console.WriteLine("\t\tSecurity context identity  :  {0}",   
        ServiceSecurityContext.Current.PrimaryIdentity.Name);  
}  
```  
  
 <span data-ttu-id="41cc1-146">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="41cc1-146">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="41cc1-147">İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="41cc1-147">Press ENTER in the client window to shut down the client.</span></span>  
  
## <a name="setup-batch-file"></a><span data-ttu-id="41cc1-148">Kurulum toplu iş dosyası</span><span class="sxs-lookup"><span data-stu-id="41cc1-148">Setup Batch File</span></span>  
 <span data-ttu-id="41cc1-149">Bu örnekle dahil Setup.bat toplu iş dosyası, sunucu sertifika tabanlı güvenlik gerektiren şirket içinde barındırılan bir uygulamayı çalıştırmak için ilgili sertifika ile sunucu yapılandırmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="41cc1-149">The Setup.bat batch file included with this sample allows you to configure the server with the relevant certificate to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="41cc1-150">Bu toplu iş dosyası bilgisayarlarda çalışmaya veya barındırılan olmayan bir durumda çalışması için değiştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="41cc1-150">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>  
  
 <span data-ttu-id="41cc1-151">Aşağıda, böylece uygun yapılandırmasında çalıştırılacak değiştirilebilir toplu iş dosyaları farklı bölümlerini kısa bir genel bakış sağlar:</span><span class="sxs-lookup"><span data-stu-id="41cc1-151">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration:</span></span>  
  
-   <span data-ttu-id="41cc1-152">Sunucu sertifikası oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="41cc1-152">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="41cc1-153">Setup.bat toplu iş dosyasından aşağıdaki satırları kullanılacak sunucu sertifikası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="41cc1-153">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="41cc1-154">`%SERVER_NAME%` Değişkeni, sunucu adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="41cc1-154">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="41cc1-155">Kendi sunucu adını belirtmek için bu değişkeni değiştirin.</span><span class="sxs-lookup"><span data-stu-id="41cc1-155">Change this variable to specify your own server name.</span></span> <span data-ttu-id="41cc1-156">Localhost bu toplu iş dosyasında varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="41cc1-156">The default value in this batch file is localhost.</span></span>  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   <span data-ttu-id="41cc1-157">Sunucu sertifikasını istemcinin güvenilen sertifika depolama alanına yükleniyor:</span><span class="sxs-lookup"><span data-stu-id="41cc1-157">Installing the server certificate into the client's trusted certificate store:</span></span>  
  
     <span data-ttu-id="41cc1-158">İstemci güvenilir kişiler uygulamasına Setup.bat toplu dosya kopyalama sunucu sertifikasının aşağıdaki satırları depolayın.</span><span class="sxs-lookup"><span data-stu-id="41cc1-158">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="41cc1-159">MakeCert.exe tarafından oluşturulan sertifikaları örtük olarak istemci sistemi tarafından güvenilir değildir çünkü bu adım gereklidir.</span><span class="sxs-lookup"><span data-stu-id="41cc1-159">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="41cc1-160">Bir istemci güvenilen kök sertifikayı kök erişim izni verilmiş bir sertifika zaten varsa — örneğin, Microsoft tarafından verilen sertifika — sunucu sertifikasında istemci sertifika deposunun doldurulması, bu adım gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="41cc1-160">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
> [!NOTE]
>  <span data-ttu-id="41cc1-161">Setup.bat toplu iş dosyası, bir Windows SDK Komut İstemi'nden çalıştırılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="41cc1-161">The Setup.bat batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="41cc1-162">MSSDK ortam değişkeni'nın SDK'ın yüklendiği dizini gösterecek gerektiriyor.</span><span class="sxs-lookup"><span data-stu-id="41cc1-162">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="41cc1-163">Bu ortam değişkeni, bir Windows SDK komut istemi içinde otomatik olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="41cc1-163">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span>  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="41cc1-164">Ayarlama ve örneği oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="41cc1-164">To set up and build the sample</span></span>  
  
1.  <span data-ttu-id="41cc1-165">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="41cc1-165">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="41cc1-166">Çözümü derlemek için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="41cc1-166">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="41cc1-167">Örneği aynı bilgisayarda çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="41cc1-167">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="41cc1-168">Setup.bat içinde örnek yükleme klasöründen çalıştırın bir [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemini yönetici ayrıcalıklarıyla açılmış.</span><span class="sxs-lookup"><span data-stu-id="41cc1-168">Run Setup.bat from the sample installation folder inside a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] command prompt opened with administrator privileges.</span></span> <span data-ttu-id="41cc1-169">Bu örneği çalıştırmak için gerekli olan tüm sertifikaları yükler.</span><span class="sxs-lookup"><span data-stu-id="41cc1-169">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="41cc1-170">Setup.bat toplu iş dosyası çalıştırılmak üzere tasarlanmış bir [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemi.</span><span class="sxs-lookup"><span data-stu-id="41cc1-170">The Setup.bat batch file is designed to be run from a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt.</span></span> <span data-ttu-id="41cc1-171">İçinde PATH ortam değişkenini ayarlamak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemi Setup.bat betiği tarafından gereken yürütülebilir dosyaları içeren dizine işaret eder.</span><span class="sxs-lookup"><span data-stu-id="41cc1-171">The PATH environment variable set within the [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2.  <span data-ttu-id="41cc1-172">Service.exe service\bin'nden başlatın.</span><span class="sxs-lookup"><span data-stu-id="41cc1-172">Launch service.exe from service\bin.</span></span>  
  
3.  <span data-ttu-id="41cc1-173">Client.exe \client\bin başlatın.</span><span class="sxs-lookup"><span data-stu-id="41cc1-173">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="41cc1-174">İstemci etkinliği istemci konsol uygulamasında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="41cc1-174">Client activity is displayed on the client console application.</span></span>  
  
4.  <span data-ttu-id="41cc1-175">Kullanıcı adı isteminde bir kullanıcı adı yazın.</span><span class="sxs-lookup"><span data-stu-id="41cc1-175">At the username prompt, type a user name.</span></span>  
  
5.  <span data-ttu-id="41cc1-176">Parola isteminde yazıldı aynı dize için kullanıcı adı istemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="41cc1-176">At the password prompt, use the same string that was typed for the username prompt.</span></span>  
  
6.  <span data-ttu-id="41cc1-177">İstemci ve hizmet iletişim kurabildiğini bilmiyorsanız bkz [sorun giderme ipuçları](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="41cc1-177">If the client and service are not able to communicate, see [Troubleshooting Tips](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="41cc1-178">Bilgisayarlar arasında örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="41cc1-178">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="41cc1-179">Hizmet ikili dosyaları için hizmet bilgisayarda bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="41cc1-179">Create a directory on the service computer for the service binaries.</span></span>  
  
2.  <span data-ttu-id="41cc1-180">Hizmet program dosyaları hizmeti bilgisayarında hizmet dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="41cc1-180">Copy the service program files to the service directory on the service computer.</span></span> <span data-ttu-id="41cc1-181">Ayrıca Setup.bat ve Cleanup.bat dosyaları hizmet bilgisayara kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="41cc1-181">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3.  <span data-ttu-id="41cc1-182">Bilgisayarın tam etki alanı adını içeren konu adına sahip bir sunucu sertifikası olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="41cc1-182">You must have a server certificate with the subject name that contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="41cc1-183">Service.exe.config dosyayı bu yeni sertifika adı yansıtacak şekilde güncelleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="41cc1-183">The Service.exe.config file must be updated to reflect this new certificate name.</span></span> <span data-ttu-id="41cc1-184">Setup.bat toplu iş dosyasını değiştirerek, sunucu sertifikası oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="41cc1-184">You can create server certificate by modifying the Setup.bat batch file.</span></span> <span data-ttu-id="41cc1-185">Setup.bat dosyasının yönetici ayrıcalıklarıyla açılan bir Visual Studio komut isteminden çalıştırmanız gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="41cc1-185">Note that the setup.bat file must be run from a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="41cc1-186">Ayarlamalısınız `%SERVER_NAME%` hizmeti barındırmak için kullanılan bilgisayarın tam ana bilgisayar adı için değişken.</span><span class="sxs-lookup"><span data-stu-id="41cc1-186">You must set `%SERVER_NAME%` variable to fully-qualified host name of the computer that is used to host the service.</span></span>  
  
4.  <span data-ttu-id="41cc1-187">Sunucu sertifikasını istemcinin CurrentUser TrustedPeople depoya kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="41cc1-187">Copy the server certificate into the CurrentUser-TrustedPeople store of the client.</span></span> <span data-ttu-id="41cc1-188">Sunucu sertifikası güvenilir istemci veren tarafından verildiğinde Bunu yapmak gerekmez.</span><span class="sxs-lookup"><span data-stu-id="41cc1-188">You do not need to do this when the server certificate is issued by a client trusted issuer.</span></span>  
  
5.  <span data-ttu-id="41cc1-189">Hizmet bilgisayarı Service.exe.config dosyada localhost yerine tam bilgisayar adını belirtmek için temel adresini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="41cc1-189">In the Service.exe.config file on the service computer, change the value of the base address to specify a fully-qualified computer name instead of localhost.</span></span>  
  
6.  <span data-ttu-id="41cc1-190">Hizmet bilgisayarda service.exe bir komut isteminden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="41cc1-190">On the service computer, run service.exe from a command prompt.</span></span>  
  
7.  <span data-ttu-id="41cc1-191">İstemci program dosyaları \client\bin\ klasöründen dile özgü klasörünün altındaki istemci bilgisayara kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="41cc1-191">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
8.  <span data-ttu-id="41cc1-192">İstemci bilgisayarda Client.exe.config dosyasında hizmetinizin yeni adresiyle eşleşecek şekilde uç nokta adresi değiştirin.</span><span class="sxs-lookup"><span data-stu-id="41cc1-192">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="41cc1-193">İstemci bilgisayarda Başlat `Client.exe` bir komut istemi penceresinden.</span><span class="sxs-lookup"><span data-stu-id="41cc1-193">On the client computer, launch `Client.exe` from a command prompt window.</span></span>  
  
10. <span data-ttu-id="41cc1-194">İstemci ve hizmet iletişim kurabildiğini bilmiyorsanız bkz [sorun giderme ipuçları](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="41cc1-194">If the client and service are not able to communicate, see [Troubleshooting Tips](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="41cc1-195">Sonra örnek temizlemek için</span><span class="sxs-lookup"><span data-stu-id="41cc1-195">To clean up after the sample</span></span>  
  
1.  <span data-ttu-id="41cc1-196">Bu örneği çalıştırmadan tamamladıktan sonra Cleanup.bat samples klasöründe çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="41cc1-196">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41cc1-197">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="41cc1-197">See Also</span></span>
