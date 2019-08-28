---
title: 'Nasıl yapılır: Kullanıcı Adı ve Parolayla Kimlik Doğrulama'
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [WCF], user name and password
ms.assetid: a5415be2-0ef3-464c-9f76-c255cb8165a4
ms.openlocfilehash: e1db413dfdcfa18403e1b67361cea710b203fe5d
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045949"
---
# <a name="how-to-authenticate-with-a-user-name-and-password"></a><span data-ttu-id="995e0-102">Nasıl yapılır: Kullanıcı Adı ve Parolayla Kimlik Doğrulama</span><span class="sxs-lookup"><span data-stu-id="995e0-102">How to: Authenticate with a User Name and Password</span></span>

<span data-ttu-id="995e0-103">Bu konu başlığı altında, bir Windows etki alanı Kullanıcı adı ve parolasıyla bir istemcinin kimliğini doğrulamak için bir Windows Communication Foundation (WCF) hizmetinin nasıl etkinleştirileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="995e0-103">This topic demonstrates how to enable a Windows Communication Foundation (WCF) service to authenticate a client with a Windows domain username and password.</span></span> <span data-ttu-id="995e0-104">Çalışan, kendine barındırılan bir WCF hizmetiniz olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="995e0-104">It assumes you have a working, self-hosted WCF service.</span></span> <span data-ttu-id="995e0-105">Temel bir şirket içinde barındırılan WCF hizmeti oluşturma hakkında bir örnek için bkz. [Başlangıç Öğreticisi](../../../../docs/framework/wcf/getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="995e0-105">For an example of creating a basic self-hosted WCF service see, [Getting Started Tutorial](../../../../docs/framework/wcf/getting-started-tutorial.md).</span></span> <span data-ttu-id="995e0-106">Bu konuda, hizmetin kodda yapılandırıldığı varsayılır.</span><span class="sxs-lookup"><span data-stu-id="995e0-106">This topic assumes the service is configured in code.</span></span> <span data-ttu-id="995e0-107">Yapılandırma dosyası kullanarak benzer bir hizmetin yapılandırılmasına ilişkin bir örnek görmek isterseniz bkz. [Ileti güvenliği Kullanıcı adı](../../../../docs/framework/wcf/samples/message-security-user-name.md)</span><span class="sxs-lookup"><span data-stu-id="995e0-107">If you would like to see an example of configuring a similar service using a configuration file see [Message Security User Name](../../../../docs/framework/wcf/samples/message-security-user-name.md)</span></span>

<span data-ttu-id="995e0-108">Windows etki alanı Kullanıcı adı ve parolaları kullanarak istemcilerinin kimliğini doğrulamak üzere bir hizmeti yapılandırmak için <xref:System.ServiceModel.WSHttpBinding> öğesini kullanın ve `Security.Mode` özelliğini olarak `Message`ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="995e0-108">To configure a service to authenticate its clients using Windows Domain username and passwords use the <xref:System.ServiceModel.WSHttpBinding> and set its `Security.Mode` property to `Message`.</span></span> <span data-ttu-id="995e0-109">Ayrıca, istemciden hizmete gönderilirken Kullanıcı adı ve parola şifrelemek için kullanılacak bir x509 sertifikası belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="995e0-109">In addition you must specify an X509 certificate that will be used to encrypt the username and password as they are sent from the client to the service.</span></span>

<span data-ttu-id="995e0-110">İstemcide, kullanıcıdan Kullanıcı adı ve parola istemek ve WCF istemci proxy 'sinde kullanıcının kimlik bilgilerini belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="995e0-110">On the client, you must prompt the user for the username and password and specify the user’s credentials on the WCF client proxy.</span></span>

## <a name="to-configure-a-wcf-service-to-authenticate-using-windows-domain-username-and-password"></a><span data-ttu-id="995e0-111">Windows etki alanı Kullanıcı adı ve parolasını kullanarak kimlik doğrulaması yapacak bir WCF hizmetini yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="995e0-111">To configure a WCF service to authenticate using Windows domain username and password</span></span>

1. <span data-ttu-id="995e0-112">Öğesinin <xref:System.ServiceModel.WSHttpBinding>bir örneğini oluşturun, bağlamanın güvenlik modunu olarak <xref:System.ServiceModel.WSHttpSecurity.Message?displayProperty=nameWithType>ayarlayın, bağlama <xref:System.ServiceModel.MessageCredentialType.UserName?displayProperty=nameWithType>' `ClientCredentialType` nın ' i ayarlayın ve aşağıdaki kodda gösterildiği gibi hizmet ana bilgisayarına yapılandırılmış bağlamayı kullanarak bir hizmet uç noktası ekleyin:</span><span class="sxs-lookup"><span data-stu-id="995e0-112">Create an instance of the <xref:System.ServiceModel.WSHttpBinding>, set the security mode of the binding to <xref:System.ServiceModel.WSHttpSecurity.Message?displayProperty=nameWithType>, set the `ClientCredentialType` of the binding to <xref:System.ServiceModel.MessageCredentialType.UserName?displayProperty=nameWithType>, and add a service endpoint using the configured binding to the service host as shown in the following code:</span></span>

    ```csharp
    // ...
    WSHttpBinding userNameBinding = new WSHttpBinding();
    userNameBinding.Security.Mode = SecurityMode.Message;
    userNameBinding.Security.Message.ClientCredentialType = MessageCredentialType.UserName;
    svcHost.AddServiceEndpoint(typeof(IService1), userNameBinding, "");
    // ...
    ```

2. <span data-ttu-id="995e0-113">Kablo üzerinden gönderilen Kullanıcı adı ve parola bilgilerini şifrelemek için kullanılan sunucu sertifikasını belirtin.</span><span class="sxs-lookup"><span data-stu-id="995e0-113">Specify the server certificate used to encrypt the username and password information sent over the wire.</span></span> <span data-ttu-id="995e0-114">Bu kod, yukarıdaki kodu hemen izlemelidir.</span><span class="sxs-lookup"><span data-stu-id="995e0-114">This code should immediately follow the code above.</span></span> <span data-ttu-id="995e0-115">Aşağıdaki örnek, [Ileti güvenliği Kullanıcı adı](../../../../docs/framework/wcf/samples/message-security-user-name.md) örneğindeki Setup. bat dosyası tarafından oluşturulan sertifikayı kullanır:</span><span class="sxs-lookup"><span data-stu-id="995e0-115">The following example uses the certificate that is created by the setup.bat file from the [Message Security User Name](../../../../docs/framework/wcf/samples/message-security-user-name.md) sample:</span></span>

    ```csharp
    // ...
    svcHost.Credentials.ServiceCertificate.SetCertificate(StoreLocation.LocalMachine, StoreName.My, X509FindType.FindBySubjectName, "localhost");
    // ...
    ```

    <span data-ttu-id="995e0-116">Kendi sertifikanızı kullanabilirsiniz, kodunuzu yalnızca sertifikanıza başvuracak şekilde değiştirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="995e0-116">You can use your own certificate, just modify the code to refer to your certificate.</span></span> <span data-ttu-id="995e0-117">Sertifika oluşturma ve kullanma hakkında daha fazla bilgi için bkz. [sertifikalarla çalışma](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="995e0-117">For more information about creating and using certificates see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span> <span data-ttu-id="995e0-118">Sertifikanın, yerel makine için güvenilir kişiler sertifika deposunda olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="995e0-118">Make sure the certificate is in the Trusted People certificate store for the Local Machine.</span></span> <span data-ttu-id="995e0-119">Bunu, MMC. exe ' yi çalıştırarak ve **Dosya**, **ek bileşen Ekle/Kaldır...** menü öğesini seçerek yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="995e0-119">You can do this by running mmc.exe and selecting the **File**, **Add/Remove Snap-in...** menu item.</span></span> <span data-ttu-id="995e0-120">**Ek bileşenleri Ekle veya Kaldır** Iletişim kutusunda **Sertifikalar ek bileşenini** seçin ve **Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="995e0-120">In the **Add or Remove Snap-ins** dialog, select the **Certificates snap-in** and click **Add**.</span></span> <span data-ttu-id="995e0-121">Sertifikalar ek bileşeni iletişim kutusunda **bilgisayar hesabı**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="995e0-121">In the Certificates Snap-in dialog select **Computer account**.</span></span> <span data-ttu-id="995e0-122">Varsayılan olarak, Ileti güvenliği Kullanıcı adı örneğinden oluşturulan sertifika Kişisel/Sertifikalar klasöründe yer alır.</span><span class="sxs-lookup"><span data-stu-id="995e0-122">By default the certificate generated from the Message Security User name sample will be located in the Personal/Certificates folder.</span></span>  <span data-ttu-id="995e0-123">Bu işlem, MMC penceresindeki verilen sütununda "localhost" olarak listelenecektir.</span><span class="sxs-lookup"><span data-stu-id="995e0-123">It will be listed as "localhost" under the Issued to column in the MMC window.</span></span> <span data-ttu-id="995e0-124">Sertifikayı sürükleyip **güvenilir kişiler** klasörüne bırakın.</span><span class="sxs-lookup"><span data-stu-id="995e0-124">Drag and drop the certificate into the **Trusted People** folder.</span></span> <span data-ttu-id="995e0-125">Bu, WCF 'nin kimlik doğrulama gerçekleştirirken sertifikayı güvenilir bir sertifika olarak ele almasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="995e0-125">This will allow WCF to treat the certificate as a trusted certificate when performing authentication.</span></span>

## <a name="to-call-the-service-passing-username-and-password"></a><span data-ttu-id="995e0-126">Kullanıcı adını ve parolayı geçen hizmeti çağırmak için</span><span class="sxs-lookup"><span data-stu-id="995e0-126">To call the service passing username and password</span></span>

1. <span data-ttu-id="995e0-127">İstemci uygulama kullanıcıdan Kullanıcı adı ve parola istemelidir.</span><span class="sxs-lookup"><span data-stu-id="995e0-127">The client application must prompt the user for their username and password.</span></span> <span data-ttu-id="995e0-128">Aşağıdaki kod kullanıcıdan Kullanıcı adı ve parola ister.</span><span class="sxs-lookup"><span data-stu-id="995e0-128">The following code asks the user for username and password.</span></span>

    > [!WARNING]
    > <span data-ttu-id="995e0-129">Parola girildiğinde görüntülenirken bu kod üretimde kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="995e0-129">This code should not be used in production as the password is displayed while being entered.</span></span>

    ```csharp
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

2. <span data-ttu-id="995e0-130">Aşağıdaki kodda gösterildiği gibi istemcinin kimlik bilgilerini belirten istemci proxy 'sinin bir örneğini oluşturun:</span><span class="sxs-lookup"><span data-stu-id="995e0-130">Create an instance of the client proxy specifying the client’s credentials as shown in the following code:</span></span>

    ```csharp
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

## <a name="see-also"></a><span data-ttu-id="995e0-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="995e0-131">See also</span></span>

- <xref:System.ServiceModel.WSHttpBinding>
- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.SecurityMode>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.UserName%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.Password%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>
- <xref:System.ServiceModel.WSHttpSecurity.Mode%2A>
- <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A>
- [<span data-ttu-id="995e0-132">Temel Kimlik Doğrulama ile Aktarım Güvenliği</span><span class="sxs-lookup"><span data-stu-id="995e0-132">Transport Security with Basic Authentication</span></span>](../../../../docs/framework/wcf/feature-details/transport-security-with-basic-authentication.md)
- [<span data-ttu-id="995e0-133">Dağıtılan Uygulama Güvenliği</span><span class="sxs-lookup"><span data-stu-id="995e0-133">Distributed Application Security</span></span>](../../../../docs/framework/wcf/feature-details/distributed-application-security.md)
- [<span data-ttu-id="995e0-134">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="995e0-134">\<wsHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)
