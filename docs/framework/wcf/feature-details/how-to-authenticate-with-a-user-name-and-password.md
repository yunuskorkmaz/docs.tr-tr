---
title: 'Nasıl yapılır: Kullanıcı Adı ve Parolayla Kimlik Doğrulama'
description: Örnek kodla bir Windows etki alanı Kullanıcı adı ve parolası kullanarak bir istemcinin kimliğini doğrulamak için bir WCF hizmetini nasıl etkinleştirebileceğinizi öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [WCF], user name and password
ms.assetid: a5415be2-0ef3-464c-9f76-c255cb8165a4
ms.openlocfilehash: 1f938f8041b2577b3705266948f29b42f23a6fd7
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247253"
---
# <a name="how-to-authenticate-with-a-user-name-and-password"></a><span data-ttu-id="746da-103">Nasıl yapılır: Kullanıcı Adı ve Parolayla Kimlik Doğrulama</span><span class="sxs-lookup"><span data-stu-id="746da-103">How to: Authenticate with a User Name and Password</span></span>

<span data-ttu-id="746da-104">Bu konu başlığı altında, bir Windows etki alanı Kullanıcı adı ve parolasıyla bir istemcinin kimliğini doğrulamak için bir Windows Communication Foundation (WCF) hizmetinin nasıl etkinleştirileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="746da-104">This topic demonstrates how to enable a Windows Communication Foundation (WCF) service to authenticate a client with a Windows domain username and password.</span></span> <span data-ttu-id="746da-105">Çalışan, kendine barındırılan bir WCF hizmetiniz olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="746da-105">It assumes you have a working, self-hosted WCF service.</span></span> <span data-ttu-id="746da-106">Temel bir şirket içinde barındırılan WCF hizmeti oluşturma hakkında bir örnek için bkz. [Başlangıç Öğreticisi](../getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="746da-106">For an example of creating a basic self-hosted WCF service see, [Getting Started Tutorial](../getting-started-tutorial.md).</span></span> <span data-ttu-id="746da-107">Bu konuda, hizmetin kodda yapılandırıldığı varsayılır.</span><span class="sxs-lookup"><span data-stu-id="746da-107">This topic assumes the service is configured in code.</span></span> <span data-ttu-id="746da-108">Yapılandırma dosyası kullanarak benzer bir hizmetin yapılandırılmasına ilişkin bir örnek görmek isterseniz, bkz. [Ileti güvenliği Kullanıcı adı](../samples/message-security-user-name.md).</span><span class="sxs-lookup"><span data-stu-id="746da-108">If you would like to see an example of configuring a similar service using a configuration file, see [Message Security User Name](../samples/message-security-user-name.md).</span></span>

<span data-ttu-id="746da-109">Windows etki alanı Kullanıcı adı ve parolaları kullanarak istemcilerinin kimliğini doğrulamak üzere bir hizmeti yapılandırmak için öğesini kullanın <xref:System.ServiceModel.WSHttpBinding> ve `Security.Mode` özelliğini olarak ayarlayın `Message` .</span><span class="sxs-lookup"><span data-stu-id="746da-109">To configure a service to authenticate its clients using Windows Domain username and passwords use the <xref:System.ServiceModel.WSHttpBinding> and set its `Security.Mode` property to `Message`.</span></span> <span data-ttu-id="746da-110">Ayrıca, istemciden hizmete gönderilirken Kullanıcı adı ve parola şifrelemek için kullanılacak bir x509 sertifikası belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="746da-110">In addition you must specify an X509 certificate that will be used to encrypt the username and password as they are sent from the client to the service.</span></span>

<span data-ttu-id="746da-111">İstemcide, kullanıcıdan Kullanıcı adı ve parola istemek ve WCF istemci proxy 'sinde kullanıcının kimlik bilgilerini belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="746da-111">On the client, you must prompt the user for the username and password and specify the user’s credentials on the WCF client proxy.</span></span>

## <a name="to-configure-a-wcf-service-to-authenticate-using-windows-domain-username-and-password"></a><span data-ttu-id="746da-112">Windows etki alanı Kullanıcı adı ve parolasını kullanarak kimlik doğrulaması yapacak bir WCF hizmetini yapılandırmak için</span><span class="sxs-lookup"><span data-stu-id="746da-112">To configure a WCF service to authenticate using Windows domain username and password</span></span>

1. <span data-ttu-id="746da-113">Öğesinin bir örneğini oluşturun, <xref:System.ServiceModel.WSHttpBinding> bağlamanın güvenlik modunu olarak ayarlayın <xref:System.ServiceModel.WSHttpSecurity.Message?displayProperty=nameWithType> , `ClientCredentialType` bağlama <xref:System.ServiceModel.MessageCredentialType.UserName?displayProperty=nameWithType> ' nın ' i ayarlayın ve aşağıdaki kodda gösterildiği gibi hizmet ana bilgisayarına yapılandırılmış bağlamayı kullanarak bir hizmet uç noktası ekleyin:</span><span class="sxs-lookup"><span data-stu-id="746da-113">Create an instance of the <xref:System.ServiceModel.WSHttpBinding>, set the security mode of the binding to <xref:System.ServiceModel.WSHttpSecurity.Message?displayProperty=nameWithType>, set the `ClientCredentialType` of the binding to <xref:System.ServiceModel.MessageCredentialType.UserName?displayProperty=nameWithType>, and add a service endpoint using the configured binding to the service host as shown in the following code:</span></span>

    ```csharp
    // ...
    var userNameBinding = new WSHttpBinding();
    userNameBinding.Security.Mode = SecurityMode.Message;
    userNameBinding.Security.Message.ClientCredentialType = MessageCredentialType.UserName;
    svcHost.AddServiceEndpoint(typeof(IService1), userNameBinding, "");
    // ...
    ```

2. <span data-ttu-id="746da-114">Kablo üzerinden gönderilen Kullanıcı adı ve parola bilgilerini şifrelemek için kullanılan sunucu sertifikasını belirtin.</span><span class="sxs-lookup"><span data-stu-id="746da-114">Specify the server certificate used to encrypt the username and password information sent over the wire.</span></span> <span data-ttu-id="746da-115">Bu kod, yukarıdaki kodu hemen izlemelidir.</span><span class="sxs-lookup"><span data-stu-id="746da-115">This code should immediately follow the code above.</span></span> <span data-ttu-id="746da-116">Aşağıdaki örnek [Ileti güvenliği Kullanıcı adı](../samples/message-security-user-name.md) örneğindeki setup.bat dosyası tarafından oluşturulan sertifikayı kullanır:</span><span class="sxs-lookup"><span data-stu-id="746da-116">The following example uses the certificate that is created by the setup.bat file from the [Message Security User Name](../samples/message-security-user-name.md) sample:</span></span>

    ```csharp
    // ...
    svcHost.Credentials.ServiceCertificate.SetCertificate(StoreLocation.LocalMachine, StoreName.My, X509FindType.FindBySubjectName, "localhost");
    // ...
    ```

    <span data-ttu-id="746da-117">Kendi sertifikanızı kullanabilirsiniz, kodunuzu yalnızca sertifikanıza başvuracak şekilde değiştirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="746da-117">You can use your own certificate, just modify the code to refer to your certificate.</span></span> <span data-ttu-id="746da-118">Sertifika oluşturma ve kullanma hakkında daha fazla bilgi için bkz. [sertifikalarla çalışma](working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="746da-118">For more information about creating and using certificates see [Working with Certificates](working-with-certificates.md).</span></span> <span data-ttu-id="746da-119">Sertifikanın, yerel makine için güvenilir kişiler sertifika deposunda olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="746da-119">Make sure the certificate is in the Trusted People certificate store for the Local Machine.</span></span> <span data-ttu-id="746da-120">Bunu mmc.exe çalıştırarak ve **Dosya**, **ek bileşen Ekle/Kaldır...** menü öğesini seçerek yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="746da-120">You can do this by running mmc.exe and selecting the **File**, **Add/Remove Snap-in...** menu item.</span></span> <span data-ttu-id="746da-121">**Ek bileşenleri Ekle veya Kaldır** Iletişim kutusunda **Sertifikalar ek bileşenini** seçin ve **Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="746da-121">In the **Add or Remove Snap-ins** dialog, select the **Certificates snap-in** and click **Add**.</span></span> <span data-ttu-id="746da-122">Sertifikalar ek bileşeni iletişim kutusunda **bilgisayar hesabı**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="746da-122">In the Certificates Snap-in dialog select **Computer account**.</span></span> <span data-ttu-id="746da-123">Varsayılan olarak, Ileti güvenliği Kullanıcı adı örneğinden oluşturulan sertifika Kişisel/Sertifikalar klasöründe yer alır.</span><span class="sxs-lookup"><span data-stu-id="746da-123">By default the certificate generated from the Message Security User name sample will be located in the Personal/Certificates folder.</span></span>  <span data-ttu-id="746da-124">Bu işlem, MMC penceresindeki verilen sütununda "localhost" olarak listelenecektir.</span><span class="sxs-lookup"><span data-stu-id="746da-124">It will be listed as "localhost" under the Issued to column in the MMC window.</span></span> <span data-ttu-id="746da-125">Sertifikayı sürükleyip **güvenilir kişiler** klasörüne bırakın.</span><span class="sxs-lookup"><span data-stu-id="746da-125">Drag and drop the certificate into the **Trusted People** folder.</span></span> <span data-ttu-id="746da-126">Bu, WCF 'nin kimlik doğrulama gerçekleştirirken sertifikayı güvenilir bir sertifika olarak ele almasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="746da-126">This will allow WCF to treat the certificate as a trusted certificate when performing authentication.</span></span>

## <a name="to-call-the-service-passing-username-and-password"></a><span data-ttu-id="746da-127">Kullanıcı adını ve parolayı geçen hizmeti çağırmak için</span><span class="sxs-lookup"><span data-stu-id="746da-127">To call the service passing username and password</span></span>

1. <span data-ttu-id="746da-128">İstemci uygulama kullanıcıdan Kullanıcı adı ve parola istemelidir.</span><span class="sxs-lookup"><span data-stu-id="746da-128">The client application must prompt the user for their username and password.</span></span> <span data-ttu-id="746da-129">Aşağıdaki kod kullanıcıdan Kullanıcı adı ve parola ister:</span><span class="sxs-lookup"><span data-stu-id="746da-129">The following code asks the user for username and password:</span></span>

    > [!WARNING]
    > <span data-ttu-id="746da-130">Parola girildiğinde görüntülenirken bu kod üretimde kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="746da-130">This code should not be used in production as the password is displayed while being entered.</span></span>

    ```csharp
    public static void GetPassword(out string username, out string password)
    {
        Console.WriteLine("Provide a valid machine or domain account. [domain\\user]");
        Console.WriteLine("   Enter username:");
        username = Console.ReadLine();
        Console.WriteLine("   Enter password:");
        password = Console.ReadLine();
    }
    ```

2. <span data-ttu-id="746da-131">Aşağıdaki kodda gösterildiği gibi istemcinin kimlik bilgilerini belirten istemci proxy 'sinin bir örneğini oluşturun:</span><span class="sxs-lookup"><span data-stu-id="746da-131">Create an instance of the client proxy specifying the client's credentials as shown in the following code:</span></span>

    ```csharp
    string username;
    string password;

    // Instantiate the proxy.
    var proxy = new Service1Client();

    // Prompt the user for username & password.
    GetPassword(out username, out password);

    // Set the user's credentials on the proxy.
    proxy.ClientCredentials.UserName.UserName = username;
    proxy.ClientCredentials.UserName.Password = password;

    // Treat the test certificate as trusted.
    proxy.ClientCredentials.ServiceCertificate.Authentication.CertificateValidationMode = System.ServiceModel.Security.X509CertificateValidationMode.PeerOrChainTrust;
    // Call the service operation using the proxy
    ```

## <a name="see-also"></a><span data-ttu-id="746da-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="746da-132">See also</span></span>

- <xref:System.ServiceModel.WSHttpBinding>
- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.SecurityMode>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.UserName%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.Password%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>
- <xref:System.ServiceModel.WSHttpSecurity.Mode%2A>
- <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A>
- [<span data-ttu-id="746da-133">Temel Kimlik Doğrulama ile Taşıma Güvenliği</span><span class="sxs-lookup"><span data-stu-id="746da-133">Transport Security with Basic Authentication</span></span>](transport-security-with-basic-authentication.md)
- [<span data-ttu-id="746da-134">Dağıtılan Uygulama Güvenliği</span><span class="sxs-lookup"><span data-stu-id="746da-134">Distributed Application Security</span></span>](distributed-application-security.md)
- [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md)
