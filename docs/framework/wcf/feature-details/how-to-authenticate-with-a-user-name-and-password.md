---
title: 'Nasıl yapılır: Bir kullanıcı adı ve parola ile kimlik doğrulaması'
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [WCF], user name and password
ms.assetid: a5415be2-0ef3-464c-9f76-c255cb8165a4
ms.openlocfilehash: f6939659249ea40e97f340771017d0587ec6a08f
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2019
ms.locfileid: "58412272"
---
# <a name="how-to-authenticate-with-a-user-name-and-password"></a><span data-ttu-id="27fdf-102">Nasıl yapılır: Bir kullanıcı adı ve parola ile kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="27fdf-102">How to: Authenticate with a User Name and Password</span></span>

<span data-ttu-id="27fdf-103">Bu konu, Windows etki alanı adı ve parola ile bir istemci kimlik doğrulaması bir Windows Communication Foundation (WCF) hizmetini etkinleştirmek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="27fdf-103">This topic demonstrates how to enable a Windows Communication Foundation (WCF) service to authenticate a client with a Windows domain username and password.</span></span> <span data-ttu-id="27fdf-104">Bu, bir çalışma, kendini barındıran WCF hizmetinde olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="27fdf-104">It assumes you have a working, self-hosted WCF service.</span></span> <span data-ttu-id="27fdf-105">Bir temel şirket içinde barındırılan WCF hizmet bkz oluşturma örneği için [başlangıç Öğreticisi](../../../../docs/framework/wcf/getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="27fdf-105">For an example of creating a basic self-hosted WCF service see, [Getting Started Tutorial](../../../../docs/framework/wcf/getting-started-tutorial.md).</span></span> <span data-ttu-id="27fdf-106">Bu konuda, kod içinde hizmet yapılandırılmış varsayılır.</span><span class="sxs-lookup"><span data-stu-id="27fdf-106">This topic assumes the service is configured in code.</span></span> <span data-ttu-id="27fdf-107">Bir yapılandırma dosyası kullanarak benzer bir hizmet yapılandırma örneği görmek istiyorsanız bkz [ileti güvenliği kullanıcı adı](../../../../docs/framework/wcf/samples/message-security-user-name.md)</span><span class="sxs-lookup"><span data-stu-id="27fdf-107">If you would like to see an example of configuring a similar service using a configuration file see [Message Security User Name](../../../../docs/framework/wcf/samples/message-security-user-name.md)</span></span>  
  
 <span data-ttu-id="27fdf-108">İstemcileri Windows etki alanı kullanıcı adı ve parolaları kullanarak kimlik doğrulaması için bir hizmeti yapılandırmak için <xref:System.ServiceModel.WSHttpBinding> ve kendi `Security.Mode` özelliğini `Message`.</span><span class="sxs-lookup"><span data-stu-id="27fdf-108">To configure a service to authenticate its clients using Windows Domain username and passwords use the <xref:System.ServiceModel.WSHttpBinding> and set its `Security.Mode` property to `Message`.</span></span> <span data-ttu-id="27fdf-109">Buna ek olarak, x X509 belirtmelisiniz, istemciden hizmete gönderilen kullanıcı adı ve parola şifrelemek için kullanılan sertifika.</span><span class="sxs-lookup"><span data-stu-id="27fdf-109">In addition you must specify an X509 certificate that will be used to encrypt the username and password as they are sent from the client to the service.</span></span>  
  
 <span data-ttu-id="27fdf-110">İstemcide, kullanıcı adı ve parola girmesini ve WCF istemci proxy kullanıcının kimlik bilgilerini belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="27fdf-110">On the client, you must prompt the user for the username and password and specify the user’s credentials on the WCF client proxy.</span></span>  
  
## <a name="to-configure-a-wcf-service-to-authenticate-using-windows-domain-username-and-password"></a><span data-ttu-id="27fdf-111">Windows etki alanı kullanıcı adı ve parola kullanarak kimlik doğrulaması için bir WCF hizmeti yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="27fdf-111">To configure a WCF service to authenticate using Windows domain username and password</span></span>
  
1.  <span data-ttu-id="27fdf-112">Bir örneğini oluşturmak <xref:System.ServiceModel.WSHttpBinding>, bağlamanın güvenlik modunu ayarlama <xref:System.ServiceModel.WSHttpSecurity.Message?displayProperty=nameWithType>ayarlayın `ClientCredentialType` bağlamanın <xref:System.ServiceModel.MessageCredentialType.UserName?displayProperty=nameWithType>, aşağıdaki kodda gösterildiği gibi hizmet ana bilgisayarı için yapılandırılmış bağlama kullanarak bir hizmet uç noktası ekleyin:</span><span class="sxs-lookup"><span data-stu-id="27fdf-112">Create an instance of the <xref:System.ServiceModel.WSHttpBinding>, set the security mode of the binding to <xref:System.ServiceModel.WSHttpSecurity.Message?displayProperty=nameWithType>, set the `ClientCredentialType` of the binding to <xref:System.ServiceModel.MessageCredentialType.UserName?displayProperty=nameWithType>, and add a service endpoint using the configured binding to the service host as shown in the following code:</span></span>  
  
    ```  
    // ...  
    WSHttpBinding userNameBinding = new WSHttpBinding();  
    userNameBinding.Security.Mode = SecurityMode.Message;  
    userNameBinding.Security.Message.ClientCredentialType = MessageCredentialType.UserName;  
    svcHost.AddServiceEndpoint(typeof(IService1), userNameBinding, "");  
    // ...  
    ```  
  
2.  <span data-ttu-id="27fdf-113">Kullanıcı adı şifrelemek için kullanılan sunucu sertifikası ve kablo üzerinden gönderilen parola bilgilerini belirtin.</span><span class="sxs-lookup"><span data-stu-id="27fdf-113">Specify the server certificate used to encrypt the username and password information sent over the wire.</span></span> <span data-ttu-id="27fdf-114">Bu kod, yukarıdaki kod hemen izlemelidir.</span><span class="sxs-lookup"><span data-stu-id="27fdf-114">This code should immediately follow the code above.</span></span> <span data-ttu-id="27fdf-115">Aşağıdaki örnek setup.bat dosyasından oluşturulan sertifikayı kullandığını [ileti güvenliği kullanıcı adı](../../../../docs/framework/wcf/samples/message-security-user-name.md) örnek:</span><span class="sxs-lookup"><span data-stu-id="27fdf-115">The following example uses the certificate that is created by the setup.bat file from the [Message Security User Name](../../../../docs/framework/wcf/samples/message-security-user-name.md) sample:</span></span>  
  
    ```  
    // ...  
    svcHost.Credentials.ServiceCertificate.SetCertificate(StoreLocation.LocalMachine, StoreName.My, X509FindType.FindBySubjectName, "localhost");  
    // ...  
    ```  
  
     <span data-ttu-id="27fdf-116">Sertifikanızı kullanabilir, yalnızca sertifikanıza başvurmak için kodu değiştirin.</span><span class="sxs-lookup"><span data-stu-id="27fdf-116">You can use your own certificate, just modify the code to refer to your certificate.</span></span> <span data-ttu-id="27fdf-117">Oluşturma ve sertifikaları kullanma hakkında daha fazla bilgi için bkz. [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="27fdf-117">For more information about creating and using certificates see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span> <span data-ttu-id="27fdf-118">Sertifika, yerel makinede güvenilir kişiler sertifika deposunda olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="27fdf-118">Make sure the certificate is in the Trusted People certificate store for the Local Machine.</span></span> <span data-ttu-id="27fdf-119">Mmc.exe çalıştıran ve seçerek bunu yapabilirsiniz **dosya**, **Ekle/Kaldır ek bileşenini...**  menü öğesi.</span><span class="sxs-lookup"><span data-stu-id="27fdf-119">You can do this by running mmc.exe and selecting the **File**, **Add/Remove Snap-in...** menu item.</span></span> <span data-ttu-id="27fdf-120">İçinde **ek bileşenler Ekle / Kaldır** iletişim kutusunda **Sertifikalar ek bileşenini** tıklatıp **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="27fdf-120">In the **Add or Remove Snap-ins** dialog, select the **Certificates snap-in** and click **Add**.</span></span> <span data-ttu-id="27fdf-121">Sertifikalar ek bileşenini iletişim kutusunda seçin **bilgisayar hesabı**.</span><span class="sxs-lookup"><span data-stu-id="27fdf-121">In the Certificates Snap-in dialog select **Computer account**.</span></span> <span data-ttu-id="27fdf-122">Varsayılan ileti güvenliği kullanıcı adı örnekten oluşturulan sertifika Kişisel/Sertifikalar klasöründe bulunur.</span><span class="sxs-lookup"><span data-stu-id="27fdf-122">By default the certificate generated from the Message Security User name sample will be located in the Personal/Certificates folder.</span></span>  <span data-ttu-id="27fdf-123">Verilen sütun MMC penceresinde altında "localhost" olarak listelenir.</span><span class="sxs-lookup"><span data-stu-id="27fdf-123">It will be listed as "localhost" under the Issued to column in the MMC window.</span></span> <span data-ttu-id="27fdf-124">Sürükle ve bırak sertifikayı **güvenilir kişiler** klasör.</span><span class="sxs-lookup"><span data-stu-id="27fdf-124">Drag and drop the certificate into the **Trusted People** folder.</span></span> <span data-ttu-id="27fdf-125">Bu, sertifikayı güvenilen bir sertifika kimlik doğrulaması yapılırken değerlendirilecek WCF olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="27fdf-125">This will allow WCF to treat the certificate as a trusted certificate when performing authentication.</span></span>  
  
## <a name="to-call-the-service-passing-username-and-password"></a><span data-ttu-id="27fdf-126">Kullanıcı adı ve parola geçirme hizmeti çağırmak için</span><span class="sxs-lookup"><span data-stu-id="27fdf-126">To call the service passing username and password</span></span>  
  
1.  <span data-ttu-id="27fdf-127">İstemci uygulaması için kullanıcı adı ve parola girmesini gerekir.</span><span class="sxs-lookup"><span data-stu-id="27fdf-127">The client application must prompt the user for their username and password.</span></span> <span data-ttu-id="27fdf-128">Aşağıdaki kod, kullanıcı adı ve parola için kullanıcıya sorar.</span><span class="sxs-lookup"><span data-stu-id="27fdf-128">The following code asks the user for username and password.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="27fdf-129">Bu kod, parola girilmesini sırasında görüntülenen üretim ortamında kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="27fdf-129">This code should not be used in production as the password is displayed while being entered.</span></span>  
  
    ```  
    public static void GetPassword(out string username, out string password)  
            {  
                Console.WriteLine("Provide a valid machine or domain account. [domain\\user]");  
                Console.WriteLine("   Enter username:");  
                username = Console.ReadLine();  
                Console.WriteLine("   Enter password:");  
                password = Console.ReadLine();             
                return;  
            }  
    ```  
  
2.  <span data-ttu-id="27fdf-130">Aşağıdaki kodda gösterildiği gibi istemcinin kimlik bilgilerinin belirtilmesi istemci proxy örneği oluşturun:</span><span class="sxs-lookup"><span data-stu-id="27fdf-130">Create an instance of the client proxy specifying the client’s credentials as shown in the following code:</span></span>  
  
    ```  
    string username;  
    string password;  
  
    // Instantiate the proxy  
    Service1Client proxy = new Service1Client();  
  
    // Prompt the user for username & password  
    GetPassword(out username, out password);  
  
    // Set the user’s credentials on the proxy  
    proxy.ClientCredentials.UserName.UserName = username;  
    proxy.ClientCredentials.UserName.Password = password;  
  
    // Treat the test certificate as trusted  
    proxy.ClientCredentials.ServiceCertificate.Authentication.CertificateValidationMode = System.ServiceModel.Security.X509CertificateValidationMode.PeerOrChainTrust;  
    // Call the service operation using the proxy  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="27fdf-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="27fdf-131">See also</span></span>
- <xref:System.ServiceModel.WSHttpBinding>
- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.SecurityMode>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.UserName%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.Password%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>
- <xref:System.ServiceModel.WSHttpSecurity.Mode%2A>
- <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A>
- [<span data-ttu-id="27fdf-132">Temel Kimlik Doğrulama ile Aktarım Güvenliği</span><span class="sxs-lookup"><span data-stu-id="27fdf-132">Transport Security with Basic Authentication</span></span>](../../../../docs/framework/wcf/feature-details/transport-security-with-basic-authentication.md)
- [<span data-ttu-id="27fdf-133">Dağıtılan Uygulama Güvenliği</span><span class="sxs-lookup"><span data-stu-id="27fdf-133">Distributed Application Security</span></span>](../../../../docs/framework/wcf/feature-details/distributed-application-security.md)
- [<span data-ttu-id="27fdf-134">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="27fdf-134">\<wsHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)
