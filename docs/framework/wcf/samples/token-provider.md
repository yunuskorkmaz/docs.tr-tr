---
title: "Belirteç Sağlayıcı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 947986cf-9946-4987-84e5-a14678d96edb
caps.latest.revision: "22"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 975014007ed57cc7e4b1035972923f61753c6d4e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="token-provider"></a><span data-ttu-id="a8468-102">Belirteç Sağlayıcı</span><span class="sxs-lookup"><span data-stu-id="a8468-102">Token Provider</span></span>
<span data-ttu-id="a8468-103">Bu örnek, özel bir belirteç sağlayıcısını uygulamak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a8468-103">This sample demonstrates how to implement a custom token provider.</span></span> <span data-ttu-id="a8468-104">Bir belirteç sağlayıcısı [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] güvenlik altyapısı için kimlik bilgileri sağladığını için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a8468-104">A token provider in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] is used for supplying credentials to the security infrastructure.</span></span> <span data-ttu-id="a8468-105">Belirteç sağlayıcı genel hedef inceler ve böylece güvenlik altyapısı ileti güvenliğini sağlayabilirsiniz sorunları kimlik bilgileri gerekli.</span><span class="sxs-lookup"><span data-stu-id="a8468-105">The token provider in general examines the target and issues appropriate credentials so that the security infrastructure can secure the message.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="a8468-106">Varsayılan kimlik bilgileri Yöneticisi belirteç sağlayıcısı birlikte verilir.</span><span class="sxs-lookup"><span data-stu-id="a8468-106"> ships with the default Credential Manager Token Provider.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="a8468-107">Ayrıca birlikte bir [!INCLUDE[infocard](../../../../includes/infocard-md.md)] belirteç sağlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="a8468-107"> also ships with an [!INCLUDE[infocard](../../../../includes/infocard-md.md)] token provider.</span></span> <span data-ttu-id="a8468-108">Özel belirteç sağlayıcılarını aşağıdaki durumlarda yararlı olur:</span><span class="sxs-lookup"><span data-stu-id="a8468-108">Custom token providers are useful in the following cases:</span></span>  
  
-   <span data-ttu-id="a8468-109">Bu belirteci sağlayıcıları ile çalışamaz bir kimlik bilgisi deposu varsa.</span><span class="sxs-lookup"><span data-stu-id="a8468-109">If you have a credential store that these token providers cannot operate with.</span></span>  
  
-   <span data-ttu-id="a8468-110">Kullanıcı ayrıntılarını geldiğinde sağladığında kimlik bilgilerini noktadan dönüştürme için kendi özel mekanizması sağlamak istiyorsanız [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci framework kimlik bilgilerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="a8468-110">If you want to provide your own custom mechanism for transforming the credentials from the point when the user provides the details to when the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client framework uses the credentials.</span></span>  
  
-   <span data-ttu-id="a8468-111">Özel belirteç oluşturuluyorsa.</span><span class="sxs-lookup"><span data-stu-id="a8468-111">If you are building a custom token.</span></span>  
  
 <span data-ttu-id="a8468-112">Bu örnek, kullanıcıdan girdi farklı bir biçime dönüştürür özel bir belirteç sağlayıcısı oluşturmak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a8468-112">This sample shows how to build a custom token provider that transforms the input from the user into a different format.</span></span>  
  
 <span data-ttu-id="a8468-113">Özetlemek için bu örnek şunlar gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="a8468-113">To summarize, this sample demonstrates the following:</span></span>  
  
-   <span data-ttu-id="a8468-114">Nasıl bir istemci bir kullanıcı adı/parola çifti kullanılarak doğrulanabilir.</span><span class="sxs-lookup"><span data-stu-id="a8468-114">How a client can authenticate using a username/password pair.</span></span>  
  
-   <span data-ttu-id="a8468-115">Nasıl bir istemci bir özel belirteç sağlayıcısı ile yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="a8468-115">How a client can be configured with a custom token provider.</span></span>  
  
-   <span data-ttu-id="a8468-116">Sunucu ile özel bir parola kullanarak istemci kimlik bilgilerini nasıl doğrulayabilir <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> kullanıcı adı ve parola eşleştiğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="a8468-116">How the server can validate the client credentials using a password with a custom <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> that validates that the username and password match.</span></span>  
  
-   <span data-ttu-id="a8468-117">Sunucu sunucunun X.509 sertifikası kullanarak istemci tarafından kimlik doğrulamasının nasıl.</span><span class="sxs-lookup"><span data-stu-id="a8468-117">How the server is authenticated by the client using the server's X.509 certificate.</span></span>  
  
 <span data-ttu-id="a8468-118">Bu örnek ayrıca nasıl çağıranının kimliğini özel belirteç kimlik doğrulama işleminden sonra erişilebilen gösterir.</span><span class="sxs-lookup"><span data-stu-id="a8468-118">This sample also shows how the caller's identity is accessible after the custom token authentication process.</span></span>  
  
 <span data-ttu-id="a8468-119">Hizmet App.config yapılandırma dosyası kullanılarak tanımlanmış hizmet ile iletişim için tek bir uç noktasını kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="a8468-119">The service exposes a single endpoint for communicating with the service, defined using the App.config configuration file.</span></span> <span data-ttu-id="a8468-120">Uç nokta bir adresi, bağlama ve bir sözleşme oluşur.</span><span class="sxs-lookup"><span data-stu-id="a8468-120">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="a8468-121">Bağlama ile standart bir yapılandırılmış `wsHttpBinding`, hangi kullanır, varsayılan olarak güvenlik iletisi.</span><span class="sxs-lookup"><span data-stu-id="a8468-121">The binding is configured with a standard `wsHttpBinding`, which uses message security by default.</span></span> <span data-ttu-id="a8468-122">Bu örnek standart ayarlar `wsHttpBinding` istemci kullanıcı adı kimlik doğrulaması kullanmak için.</span><span class="sxs-lookup"><span data-stu-id="a8468-122">This sample sets the standard `wsHttpBinding` to use client username authentication.</span></span> <span data-ttu-id="a8468-123">Hizmet ayrıca serviceCredentials davranışını kullanarak hizmet sertifikası yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="a8468-123">The service also configures the service certificate using the serviceCredentials behavior.</span></span> <span data-ttu-id="a8468-124">ServiceCredentials davranış bir hizmet sertifikası yapılandırmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="a8468-124">The serviceCredentials behavior allows you to configure a service certificate.</span></span> <span data-ttu-id="a8468-125">Bir hizmet sertifikası, hizmetin kimliğini doğrulamak ve ileti koruma sağlamak için bir istemci tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a8468-125">A service certificate is used by a client to authenticate the service and provide message protection.</span></span> <span data-ttu-id="a8468-126">Aşağıdaki yapılandırma aşağıdaki Kurulum yönergelerde açıklandığı gibi örnek Kurulum sırasında yüklenen localhost sertifika başvurur.</span><span class="sxs-lookup"><span data-stu-id="a8468-126">The following configuration references the localhost certificate installed during the sample setup as described in the following setup instructions.</span></span>  
  
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
  
 <span data-ttu-id="a8468-127">Yapılandırma adı, hizmet uç noktası, bağlama ve sözleşme için mutlak bir adres, istemci uç nokta yapılandırması oluşur.</span><span class="sxs-lookup"><span data-stu-id="a8468-127">The client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="a8468-128">Bağlama istemci uygun ile yapılandırılmış `Mode` ve ileti `clientCredentialType`.</span><span class="sxs-lookup"><span data-stu-id="a8468-128">The client binding is configured with the appropriate `Mode` and message `clientCredentialType`.</span></span>  
  
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
  
 <span data-ttu-id="a8468-129">Aşağıdaki adımlar, özel bir belirteç sağlayıcısı geliştirmek ve ile tümleştirmek nasıl gösterir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] security çerçevesi:</span><span class="sxs-lookup"><span data-stu-id="a8468-129">The following steps show how to develop a custom token provider and integrate it with the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] security framework:</span></span>  
  
1.  <span data-ttu-id="a8468-130">Özel bir belirteç sağlayıcısı yazma.</span><span class="sxs-lookup"><span data-stu-id="a8468-130">Write a custom token provider.</span></span>  
  
     <span data-ttu-id="a8468-131">Örnek kullanıcı adı ve parola özel bir belirteç sağlayıcısını uygular.</span><span class="sxs-lookup"><span data-stu-id="a8468-131">The sample implements a custom token provider that obtains the username and password.</span></span> <span data-ttu-id="a8468-132">Parola, bu kullanıcı adı eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="a8468-132">The password must match this username.</span></span> <span data-ttu-id="a8468-133">Bu özel belirteç sağlayıcısı yalnızca tanıtım amaçlıdır ve için gerçek dünya dağıtım önerilmez.</span><span class="sxs-lookup"><span data-stu-id="a8468-133">This custom token provider is for demonstration purposes only and is not recommended for real world deployment.</span></span>  
  
     <span data-ttu-id="a8468-134">Bu görevi gerçekleştirmek için özel belirteç sağlayıcı türetilen <xref:System.IdentityModel.Selectors.SecurityTokenProvider> sınıfı ve geçersiz kılmalar <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a8468-134">To perform this task, the custom token provider derives the <xref:System.IdentityModel.Selectors.SecurityTokenProvider> class and overrides the <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> method.</span></span> <span data-ttu-id="a8468-135">Bu yöntem oluşturur ve yeni bir döndürür `UserNameSecurityToken`.</span><span class="sxs-lookup"><span data-stu-id="a8468-135">This method creates and returns a new `UserNameSecurityToken`.</span></span>  
  
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
  
2.  <span data-ttu-id="a8468-136">Özel güvenlik belirteci yöneticisi yazma.</span><span class="sxs-lookup"><span data-stu-id="a8468-136">Write custom security token manager.</span></span>  
  
     <span data-ttu-id="a8468-137"><xref:System.IdentityModel.Selectors.SecurityTokenManager> Oluşturmak için kullanılan <xref:System.IdentityModel.Selectors.SecurityTokenProvider> belirli <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> kendisine geçirilen `CreateSecurityTokenProvider` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a8468-137">The <xref:System.IdentityModel.Selectors.SecurityTokenManager> is used to create <xref:System.IdentityModel.Selectors.SecurityTokenProvider> for specific <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> that is passed to it in `CreateSecurityTokenProvider` method.</span></span> <span data-ttu-id="a8468-138">Güvenlik belirteci Yöneticisi ayrıca belirteç kimlik doğrulayan ve belirteci seri hale getirici oluşturmak için kullanılır, ancak bunlar Bu örnek tarafından kapsanmayan.</span><span class="sxs-lookup"><span data-stu-id="a8468-138">Security token manager is also used to create token authenticators and a token serializer, but those are not covered by this sample.</span></span> <span data-ttu-id="a8468-139">Bu örnekte, özel güvenlik belirteci yöneticisi devraldığı <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> sınıfı ve geçersiz kılmalar `CreateSecurityTokenProvider` geçirilen belirteci gereksinimleri, kullanıcı adı sağlayıcıyı belirttiğinizde özel kullanıcıadı belirteç sağlayıcısı döndürülecek yöntemi istendi.</span><span class="sxs-lookup"><span data-stu-id="a8468-139">In this sample, the custom security token manager inherits from <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> class and overrides the `CreateSecurityTokenProvider` method to return custom username token provider when the passed token requirements indicate that username provider is requested.</span></span>  
  
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
  
3.  <span data-ttu-id="a8468-140">Özel istemci kimlik bilgilerini yazın.</span><span class="sxs-lookup"><span data-stu-id="a8468-140">Write a custom client credential.</span></span>  
  
     <span data-ttu-id="a8468-141">İstemci kimlik bilgileri sınıfı istemci proxy için yapılandırılmış olan kimlik bilgilerini temsil etmek için kullanılır ve güvenlik belirteci Doğrulayıcı, belirteci sağlayıcıları ve belirteci seri hale getirici elde etmek için kullanılan belirteci yöneticisi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a8468-141">Client credentials class is used to represent the credentials that are configured for the client proxy and creates security token manager that is used to obtain token authenticators, token providers and a token serializer.</span></span>  
  
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
  
4.  <span data-ttu-id="a8468-142">Özel istemci kimlik bilgisi kullanmak için istemciyi yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="a8468-142">Configure the client to use the custom client credential.</span></span>  
  
     <span data-ttu-id="a8468-143">Özel istemci kimlik bilgisi kullanmak istemcinin sırasıyla örnek varsayılan istemci kimlik bilgisi sınıfını siler ve yeni istemci kimlik bilgisi sınıfını sağlar.</span><span class="sxs-lookup"><span data-stu-id="a8468-143">In order for the client to use the custom client credential, the sample deletes the default client credential class and supplies the new client credential class.</span></span>  
  
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
  
 <span data-ttu-id="a8468-144">Arayanın bilgileri görüntülemek için hizmette kullanın <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> aşağıdaki kod örneğinde gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="a8468-144">On the service, to display the caller's information, use the <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> as shown in the following code example.</span></span> <span data-ttu-id="a8468-145"><xref:System.ServiceModel.ServiceSecurityContext.Current%2A> Talep geçerli çağıran hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="a8468-145">The <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> contains claims information about the current caller.</span></span>  
  
```  
static void DisplayIdentityInformation()  
{  
    Console.WriteLine("\t\tSecurity context identity  :  {0}",   
        ServiceSecurityContext.Current.PrimaryIdentity.Name);  
}  
```  
  
 <span data-ttu-id="a8468-146">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="a8468-146">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="a8468-147">İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="a8468-147">Press ENTER in the client window to shut down the client.</span></span>  
  
## <a name="setup-batch-file"></a><span data-ttu-id="a8468-148">Toplu iş dosyası Kurulumu</span><span class="sxs-lookup"><span data-stu-id="a8468-148">Setup Batch File</span></span>  
 <span data-ttu-id="a8468-149">Bu örnekle dahil Setup.bat toplu iş dosyası, sunucu sertifika tabanlı güvenlik gerektiren kendini barındıran bir uygulamayı çalıştırmak için ilgili sertifika ile sunucu yapılandırmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="a8468-149">The Setup.bat batch file included with this sample allows you to configure the server with the relevant certificate to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="a8468-150">Bu toplu iş dosyası bilgisayarlar arasında iş ya da barındırılan olmayan bir durumda çalışması için değiştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="a8468-150">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>  
  
 <span data-ttu-id="a8468-151">Aşağıdakiler, böylece uygun yapılandırmada çalışacak biçimde değiştirilebilir toplu iş dosyaları farklı bölümlerini kısa bir genel bakış sağlar:</span><span class="sxs-lookup"><span data-stu-id="a8468-151">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration:</span></span>  
  
-   <span data-ttu-id="a8468-152">Sunucu sertifikası oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="a8468-152">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="a8468-153">Aşağıdaki satırları Setup.bat toplu iş dosyasından kullanılacak sunucu sertifikası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a8468-153">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="a8468-154">`%SERVER_NAME%` Değişkeni, sunucu adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a8468-154">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="a8468-155">Kendi sunucu adını belirtmek için bu değişkeni değiştirin.</span><span class="sxs-lookup"><span data-stu-id="a8468-155">Change this variable to specify your own server name.</span></span> <span data-ttu-id="a8468-156">Localhost bu toplu iş dosyasında varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="a8468-156">The default value in this batch file is localhost.</span></span>  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   <span data-ttu-id="a8468-157">Sunucu sertifikası istemcinin güvenilen sertifika deposuna yükleme:</span><span class="sxs-lookup"><span data-stu-id="a8468-157">Installing the server certificate into the client's trusted certificate store:</span></span>  
  
     <span data-ttu-id="a8468-158">İstemci güvenilir kişiler içine Setup.bat toplu dosya kopyalama sunucu sertifikasının aşağıdaki satırları depolar.</span><span class="sxs-lookup"><span data-stu-id="a8468-158">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="a8468-159">MakeCert.exe tarafından oluşturulan sertifikaları örtük olarak istemci sistemi tarafından güvenilir değil çünkü bu adım gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a8468-159">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="a8468-160">Bir istemci güvenilen kök sertifikasını kökü belirtilmiş bir sertifikanız zaten varsa — örneğin, bir Microsoft verilen sertifika — sunucu sertifikasına sahip istemci sertifika deposunun doldurulması, bu adım gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="a8468-160">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
> [!NOTE]
>  <span data-ttu-id="a8468-161">Setup.bat toplu iş dosyası, Windows SDK komut isteminden çalıştırılması için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="a8468-161">The Setup.bat batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="a8468-162">MSSDK ortam değişkeni SDK yüklendiği dizinine işaret gerektiriyor.</span><span class="sxs-lookup"><span data-stu-id="a8468-162">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="a8468-163">Bu ortam değişkeni, Windows SDK komut istemi içinde otomatik olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="a8468-163">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span>  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="a8468-164">Ayarlamak ve örneği oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="a8468-164">To set up and build the sample</span></span>  
  
1.  <span data-ttu-id="a8468-165">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a8468-165">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="a8468-166">Çözümü derlemek için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a8468-166">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="a8468-167">Aynı bilgisayara örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="a8468-167">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="a8468-168">Örnek yükleme klasöründen içinde Setup.bat çalıştırmak bir [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemini yönetici ayrıcalıklarıyla açılır.</span><span class="sxs-lookup"><span data-stu-id="a8468-168">Run Setup.bat from the sample installation folder inside a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] command prompt opened with administrator privileges.</span></span> <span data-ttu-id="a8468-169">Bu örneği çalıştırmak için gerekli tüm sertifikalar yükler.</span><span class="sxs-lookup"><span data-stu-id="a8468-169">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a8468-170">Setup.bat toplu iş dosyası çalıştırılmak üzere tasarlanmış bir [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemi.</span><span class="sxs-lookup"><span data-stu-id="a8468-170">The Setup.bat batch file is designed to be run from a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt.</span></span> <span data-ttu-id="a8468-171">İçinde PATH ortam değişkeni ayarlamak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] komut istemi Setup.bat komut dosyası için gereken yürütülebilir dosyalar içeren dizine işaret eder.</span><span class="sxs-lookup"><span data-stu-id="a8468-171">The PATH environment variable set within the [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2.  <span data-ttu-id="a8468-172">Service\bin gelen Service.exe başlatın.</span><span class="sxs-lookup"><span data-stu-id="a8468-172">Launch service.exe from service\bin.</span></span>  
  
3.  <span data-ttu-id="a8468-173">Client.exe \client\bin başlatın.</span><span class="sxs-lookup"><span data-stu-id="a8468-173">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="a8468-174">İstemci etkinliği istemci konsol uygulaması görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="a8468-174">Client activity is displayed on the client console application.</span></span>  
  
4.  <span data-ttu-id="a8468-175">Kullanıcı adı isteminde bir kullanıcı adı yazın.</span><span class="sxs-lookup"><span data-stu-id="a8468-175">At the username prompt, type a user name.</span></span>  
  
5.  <span data-ttu-id="a8468-176">Parola isteminde yazıldı aynı dize kullanıcıadı istem için kullanın.</span><span class="sxs-lookup"><span data-stu-id="a8468-176">At the password prompt, use the same string that was typed for the username prompt.</span></span>  
  
6.  <span data-ttu-id="a8468-177">İstemci ve hizmet iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="a8468-177">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="a8468-178">Bilgisayarlar arasında örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="a8468-178">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="a8468-179">Hizmet ikili dosyaları hizmet bilgisayarda bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a8468-179">Create a directory on the service computer for the service binaries.</span></span>  
  
2.  <span data-ttu-id="a8468-180">Hizmet program dosyalarını hizmeti bilgisayarında hizmet dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="a8468-180">Copy the service program files to the service directory on the service computer.</span></span> <span data-ttu-id="a8468-181">Ayrıca Setup.bat ve Cleanup.bat dosyalarını hizmet bilgisayara kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="a8468-181">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3.  <span data-ttu-id="a8468-182">Bilgisayarın tam etki alanı adını içeren konu adına sahip bir sunucu sertifikası olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a8468-182">You must have a server certificate with the subject name that contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="a8468-183">Service.exe.config dosyayı bu yeni sertifika adını yansıtacak şekilde güncelleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a8468-183">The Service.exe.config file must be updated to reflect this new certificate name.</span></span> <span data-ttu-id="a8468-184">Sunucu sertifikası Setup.bat toplu iş dosyasını değiştirerek oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a8468-184">You can create server certificate by modifying the Setup.bat batch file.</span></span> <span data-ttu-id="a8468-185">Setup.bat dosyasını yönetici ayrıcalıklarıyla açılmış Visual Studio komut isteminden çalıştırmanız gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a8468-185">Note that the setup.bat file must be run from a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="a8468-186">Ayarlamalısınız `%SERVER_NAME%` hizmetini barındırmak için kullanılan bilgisayarın tam ana bilgisayar adı için değişken.</span><span class="sxs-lookup"><span data-stu-id="a8468-186">You must set `%SERVER_NAME%` variable to fully-qualified host name of the computer that is used to host the service.</span></span>  
  
4.  <span data-ttu-id="a8468-187">Sunucu sertifikası istemci Currentuser'a TrustedPeople depolama alanına kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="a8468-187">Copy the server certificate into the CurrentUser-TrustedPeople store of the client.</span></span> <span data-ttu-id="a8468-188">Sunucu sertifikasının güvenilen istemci veren tarafından verildiğinde Bunu yapmak gerekmez.</span><span class="sxs-lookup"><span data-stu-id="a8468-188">You do not need to do this when the server certificate is issued by a client trusted issuer.</span></span>  
  
5.  <span data-ttu-id="a8468-189">Hizmeti bilgisayarında Service.exe.config dosyasında localhost yerine bir tam bilgisayar adını belirtmek için taban adresi değerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="a8468-189">In the Service.exe.config file on the service computer, change the value of the base address to specify a fully-qualified computer name instead of localhost.</span></span>  
  
6.  <span data-ttu-id="a8468-190">Hizmet bilgisayarda service.exe bir komut isteminden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a8468-190">On the service computer, run service.exe from a command prompt.</span></span>  
  
7.  <span data-ttu-id="a8468-191">İstemci program dosyaları \client\bin\ klasöründen dile özgü klasörü altında istemci bilgisayara kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="a8468-191">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
8.  <span data-ttu-id="a8468-192">İstemci bilgisayardaki Client.exe.config dosyasında yeni adresi hizmetinizin eşleştirmek için uç nokta adresi değerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="a8468-192">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="a8468-193">İstemci bilgisayarda, başlatma `Client.exe` bir komut istemi penceresinden.</span><span class="sxs-lookup"><span data-stu-id="a8468-193">On the client computer, launch `Client.exe` from a command prompt window.</span></span>  
  
10. <span data-ttu-id="a8468-194">İstemci ve hizmet iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="a8468-194">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="a8468-195">Örnek sonra temizlemek için</span><span class="sxs-lookup"><span data-stu-id="a8468-195">To clean up after the sample</span></span>  
  
1.  <span data-ttu-id="a8468-196">Örnek çalıştıran tamamladıktan sonra Cleanup.bat samples klasöründen çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a8468-196">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8468-197">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a8468-197">See Also</span></span>
