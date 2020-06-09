---
title: 'Nasıl yapılır: Kanal Güvenliği Kimlik Bilgilerini Belirtme'
ms.date: 03/30/2017
ms.assetid: f8e03f47-9c4f-4dd5-8f85-429e6d876119
ms.openlocfilehash: 45a13460ce94cbacae0465fede4b455a2833ce81
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596948"
---
# <a name="how-to-specify-channel-security-credentials"></a><span data-ttu-id="8de9c-102">Nasıl yapılır: Kanal Güvenliği Kimlik Bilgilerini Belirtme</span><span class="sxs-lookup"><span data-stu-id="8de9c-102">How to: Specify Channel Security Credentials</span></span>
<span data-ttu-id="8de9c-103">Windows Communication Foundation (WCF) hizmet bilinen adı, COM uygulamalarının WCF hizmetlerini çağırmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="8de9c-103">The Windows Communication Foundation (WCF) Service Moniker allows COM applications to call WCF services.</span></span> <span data-ttu-id="8de9c-104">Çoğu WCF hizmeti, istemcinin kimlik doğrulama ve yetkilendirme için kimlik bilgilerini belirtmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="8de9c-104">Most WCF services require the client to specify credentials for authentication and authorization.</span></span> <span data-ttu-id="8de9c-105">WCF istemcisinden bir WCF hizmetini çağırırken bu kimlik bilgilerini yönetilen kodda veya bir uygulama yapılandırma dosyasında belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8de9c-105">When calling a WCF service from a WCF client, you can specify these credentials in managed code or in an application configuration file.</span></span> <span data-ttu-id="8de9c-106">Bir WCF hizmetini bir COM uygulamasından çağırırken, <xref:System.ServiceModel.ComIntegration.IChannelCredentials> kimlik bilgilerini belirtmek için arabirimini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8de9c-106">When calling a WCF service from a COM application, you can use the <xref:System.ServiceModel.ComIntegration.IChannelCredentials> interface to specify credentials.</span></span> <span data-ttu-id="8de9c-107">Bu konu, arabirimi kullanarak kimlik bilgilerini belirtmek için çeşitli yollar gösterir <xref:System.ServiceModel.ComIntegration.IChannelCredentials> .</span><span class="sxs-lookup"><span data-stu-id="8de9c-107">This topic will illustrate various ways to specify credentials using the <xref:System.ServiceModel.ComIntegration.IChannelCredentials> interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8de9c-108"><xref:System.ServiceModel.ComIntegration.IChannelCredentials>, IDispatch tabanlı bir arabirimdir ve Visual Studio ortamında IntelliSense işlevselliği almaz.</span><span class="sxs-lookup"><span data-stu-id="8de9c-108"><xref:System.ServiceModel.ComIntegration.IChannelCredentials> is an IDispatch-based interface and you will not get IntelliSense functionality in the Visual Studio environment.</span></span>  
  
 <span data-ttu-id="8de9c-109">Bu makalede [Ileti güvenliği örneğinde](../samples/message-security-sample.md)tanımlanan WCF hizmeti kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="8de9c-109">This article will use the WCF service defined in the [Message Security Sample](../samples/message-security-sample.md).</span></span>  
  
### <a name="to-specify-a-client-certificate"></a><span data-ttu-id="8de9c-110">İstemci sertifikası belirtmek için</span><span class="sxs-lookup"><span data-stu-id="8de9c-110">To specify a client certificate</span></span>  
  
1. <span data-ttu-id="8de9c-111">Gerekli test sertifikalarını oluşturmak ve yüklemek için Ileti güvenlik dizininde Setup. bat dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="8de9c-111">Run the Setup.bat file in the Message Security directory to create and install the required test certificates.</span></span>  
  
2. <span data-ttu-id="8de9c-112">Ileti güvenliği projesini açın.</span><span class="sxs-lookup"><span data-stu-id="8de9c-112">Open the Message Security project.</span></span>  
  
3. <span data-ttu-id="8de9c-113">`[ServiceBehavior(Namespace="http://Microsoft.ServiceModel.Samples")]` `ICalculator` Arabirim tanımına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8de9c-113">Add `[ServiceBehavior(Namespace="http://Microsoft.ServiceModel.Samples")]` to the `ICalculator` interface definition.</span></span>  
  
4. <span data-ttu-id="8de9c-114">`bindingNamespace="http://Microsoft.ServiceModel.Samples"`Hizmetin App. config dosyasındaki Endpoint etiketine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8de9c-114">Add `bindingNamespace="http://Microsoft.ServiceModel.Samples"` to the endpoint tag in the App.config for the service.</span></span>  
  
5. <span data-ttu-id="8de9c-115">Ileti güvenlik örneğini oluşturun ve Service. exe ' yi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="8de9c-115">Build the Message Security Sample and run Service.exe.</span></span> <span data-ttu-id="8de9c-116">Hizmetin çalıştığından emin olmak için Internet Explorer 'ı kullanın ve hizmetin URI 'sine ( `http://localhost:8000/ServiceModelSamples/Service` ) gidin.</span><span class="sxs-lookup"><span data-stu-id="8de9c-116">Use Internet Explorer and browse to the service's URI (`http://localhost:8000/ServiceModelSamples/Service`) to ensure that the service is working.</span></span>  
  
6. <span data-ttu-id="8de9c-117">Visual Basic 6,0 ' i açın ve yeni bir standart. exe dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8de9c-117">Open Visual Basic 6.0 and create a new Standard .exe file.</span></span> <span data-ttu-id="8de9c-118">Forma bir düğme ekleyin ve tıklama işleyicisine aşağıdaki kodu eklemek için düğmeye çift tıklayın:</span><span class="sxs-lookup"><span data-stu-id="8de9c-118">Add a button to the form and double-click the button to add the following code to the Click handler:</span></span>  
  
    ```vb  
        monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
        monString = monString + ", address=http://localhost:8000/ServiceModelSamples/Service"  
        monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
        monString = monString + ", binding=BasicHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
        Set monikerProxy = GetObject(monString)  
  
        'Set the Service Certificate.  
     monikerProxy.ChannelCredentials.SetServiceCertificateAuthentication "CurrentUser", "NoCheck", "PeerOrChainTrust"  
    monikerProxy.ChannelCredentials.SetDefaultServiceCertificateFromStore "CurrentUser", "TrustedPeople", "FindBySubjectName", "localhost"  
  
        'Set the Client Certificate.  
        monikerProxy.ChannelCredentials.SetClientCertificateFromStoreByName "CN=client.com", "CurrentUser", "My"  
        MsgBox monikerProxy.Add(3, 4)  
    ```  
  
7. <span data-ttu-id="8de9c-119">Visual Basic uygulamayı çalıştırın ve sonuçları doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="8de9c-119">Run the Visual Basic application and verify the results.</span></span>  
  
     <span data-ttu-id="8de9c-120">Visual Basic uygulama, Add (3, 4) çağırmanın sonucunu içeren bir ileti kutusu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="8de9c-120">The Visual Basic application will display a message box with the result from calling Add(3, 4).</span></span> <span data-ttu-id="8de9c-121"><xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromFile%28System.String%2CSystem.String%2CSystem.String%29><xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStoreByName%28System.String%2CSystem.String%2CSystem.String%29>Ayrıca, <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStore%28System.String%2CSystem.String%2CSystem.String%2CSystem.Object%29> istemci sertifikasını ayarlamak için yerinde de kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="8de9c-121"><xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromFile%28System.String%2CSystem.String%2CSystem.String%29> or <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStoreByName%28System.String%2CSystem.String%2CSystem.String%29> can also be used in place of <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStore%28System.String%2CSystem.String%2CSystem.String%2CSystem.Object%29> to set the Client Certificate:</span></span>  
  
    ```vb  
    monikerProxy.ChannelCredentials.SetClientCertificateFromFile "C:\MyClientCert.pfx", "password", "DefaultKeySet"  
    ```  
  
> [!NOTE]
> <span data-ttu-id="8de9c-122">Bu çağrının çalışması için, istemci sertifikasının, istemcinin üzerinde çalıştığı makinede güvenilir olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8de9c-122">For this call to work, the client certificate needs to be trusted on the machine the client is running on.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8de9c-123">Bilinen ad yanlış biçimlendirilmişse veya hizmet kullanılamıyorsa, çağrısı `GetObject` "geçersiz sözdizimi" belirten bir hata döndürür.</span><span class="sxs-lookup"><span data-stu-id="8de9c-123">If the moniker is malformed or if the service is unavailable, the call to `GetObject` will return an error saying "Invalid Syntax."</span></span> <span data-ttu-id="8de9c-124">Bu hatayı alırsanız, kullanmakta olduğunuz bilinen adın doğru olduğundan ve hizmetin kullanılabilir olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="8de9c-124">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
### <a name="to-specify-user-name-and-password"></a><span data-ttu-id="8de9c-125">Kullanıcı adı ve parola belirtmek için</span><span class="sxs-lookup"><span data-stu-id="8de9c-125">To specify user name and password</span></span>  
  
1. <span data-ttu-id="8de9c-126">Kullanmak için Service App. config dosyasını değiştirin `wsHttpBinding` .</span><span class="sxs-lookup"><span data-stu-id="8de9c-126">Modify the Service App.config file to use the `wsHttpBinding`.</span></span> <span data-ttu-id="8de9c-127">Bu, Kullanıcı adı ve parola doğrulaması için gereklidir:</span><span class="sxs-lookup"><span data-stu-id="8de9c-127">This is required for user name and password validation:</span></span>  

2. <span data-ttu-id="8de9c-128">Şunu `clientCredentialType` Kullanıcı adı olarak ayarla:</span><span class="sxs-lookup"><span data-stu-id="8de9c-128">Set the `clientCredentialType` to UserName:</span></span>  

3. <span data-ttu-id="8de9c-129">Visual Basic 6,0 ' i açın ve yeni bir standart. exe dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8de9c-129">Open Visual Basic 6.0 and create a new Standard .exe file.</span></span> <span data-ttu-id="8de9c-130">Forma bir düğme ekleyin ve tıklama işleyicisine aşağıdaki kodu eklemek için düğmeye çift tıklayın:</span><span class="sxs-lookup"><span data-stu-id="8de9c-130">Add a button to the form and double-click the button to add the following code to the Click handler:</span></span>  
  
    ```vb
    monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
    monString = monString + ", address=http://localhost:8000/ServiceModelSamples/Service"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
    Set monikerProxy = GetObject(monString)  
  
    monikerProxy.ChannelCredentials.SetServiceCertificateAuthentication "CurrentUser", "NoCheck", "PeerOrChainTrust"  
    monikerProxy.ChannelCredentials.SetUserNameCredential "username", "password"  
  
    MsgBox monikerProxy.Add(3, 4)  
    ```  
  
4. <span data-ttu-id="8de9c-131">Visual Basic uygulamayı çalıştırın ve sonuçları doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="8de9c-131">Run the Visual Basic application and verify the results.</span></span> <span data-ttu-id="8de9c-132">Visual Basic uygulama, Add (3, 4) çağırmanın sonucunu içeren bir ileti kutusu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="8de9c-132">The Visual Basic application will display a message box with the result from calling Add(3, 4).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="8de9c-133">Bu örnekteki hizmet takma adı 'nda belirtilen bağlama WSHttpBinding_ICalculator olarak değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="8de9c-133">The binding specified in the service moniker in this sample has been changed to WSHttpBinding_ICalculator.</span></span> <span data-ttu-id="8de9c-134">Ayrıca, çağrısına, için geçerli bir Kullanıcı adı ve parola belirtmeniz gerektiğini unutmayın <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetUserNameCredential%28System.String%2CSystem.String%29> .</span><span class="sxs-lookup"><span data-stu-id="8de9c-134">Also note that you must supply a valid user name and password in the call to <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetUserNameCredential%28System.String%2CSystem.String%29>.</span></span>  
  
### <a name="to-specify-windows-credentials"></a><span data-ttu-id="8de9c-135">Windows kimlik bilgilerini belirtmek için</span><span class="sxs-lookup"><span data-stu-id="8de9c-135">To specify Windows Credentials</span></span>  
  
1. <span data-ttu-id="8de9c-136">`clientCredentialType`Service App. config dosyasında Windows olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="8de9c-136">Set `clientCredentialType` to Windows in the Service App.config file:</span></span>  

2. <span data-ttu-id="8de9c-137">Visual Basic 6,0 ' i açın ve yeni bir standart. exe dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8de9c-137">Open Visual Basic 6.0 and create a new Standard .exe file.</span></span> <span data-ttu-id="8de9c-138">Forma bir düğme ekleyin ve tıklama işleyicisine aşağıdaki kodu eklemek için düğmeye çift tıklayın:</span><span class="sxs-lookup"><span data-stu-id="8de9c-138">Add a button to the form and double-click the button to add the following code to the Click handler:</span></span>  
  
    ```vb
    monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
    monString = monString + ", address=http://localhost:8000/ServiceModelSamples/Service"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", upnidentity=domain\userID"  
  
    Set monikerProxy = GetObject(monString)  
     monikerProxy.ChannelCredentials.SetWindowsCredential "domain", "userID", "password", 1, True  
  
    MsgBox monikerProxy.Add(3, 4)  
    ```  
  
3. <span data-ttu-id="8de9c-139">Visual Basic uygulamayı çalıştırın ve sonuçları doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="8de9c-139">Run the Visual Basic application and verify the results.</span></span> <span data-ttu-id="8de9c-140">Visual Basic uygulama, Add (3, 4) çağırmanın sonucunu içeren bir ileti kutusu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="8de9c-140">The Visual Basic application will display a message box with the result from calling Add(3, 4).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="8de9c-141">"Domain", "UserID" ve "Password" değerlerini geçerli değerlerle değiştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="8de9c-141">You must replace "domain", "userID", and "password" with valid values.</span></span>  
  
### <a name="to-specify-an-issue-token"></a><span data-ttu-id="8de9c-142">Bir sorun belirteci belirtmek için</span><span class="sxs-lookup"><span data-stu-id="8de9c-142">To specify an issue token</span></span>  
  
1. <span data-ttu-id="8de9c-143">Sorun belirteçleri yalnızca Federe güvenlik kullanan uygulamalar için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8de9c-143">Issue tokens are used only for applications using federated security.</span></span> <span data-ttu-id="8de9c-144">Federasyon güvenliği hakkında daha fazla bilgi için bkz. [Federasyon ve verilen belirteçler](federation-and-issued-tokens.md) ve [Federasyon örneği](../samples/federation-sample.md).</span><span class="sxs-lookup"><span data-stu-id="8de9c-144">For more information about federated security, see [Federation and Issued Tokens](federation-and-issued-tokens.md) and [Federation Sample](../samples/federation-sample.md).</span></span>  
  
     <span data-ttu-id="8de9c-145">Aşağıdaki Visual Basic kod örneği, yönteminin nasıl çağrılacağını göstermektedir <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29> :</span><span class="sxs-lookup"><span data-stu-id="8de9c-145">The following Visual Basic code example illustrates how to call the <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29> method:</span></span>  
  
    ```vb
        monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
        monString = monString + ", address=http://localhost:8000/SomeService/Service"  
        monString = monString + ", contract=ICalculator, contractNamespace=http://SomeService.Samples"  
        monString = monString + ", binding=WSHttpBinding_ISomeContract, bindingNamespace=http://SomeService.Samples"  
  
        Set monikerProxy = GetObject(monString)  
    monikerProxy.SetIssuedToken("http://somemachine/sts", "bindingType", "binding")  
    ```  
  
     <span data-ttu-id="8de9c-146">Bu yöntemin parametreleri hakkında daha fazla bilgi için bkz <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29> ..</span><span class="sxs-lookup"><span data-stu-id="8de9c-146">For more information about the parameters for this method, see <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8de9c-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8de9c-147">See also</span></span>

- [<span data-ttu-id="8de9c-148">Federasyon</span><span class="sxs-lookup"><span data-stu-id="8de9c-148">Federation</span></span>](federation.md)
- [<span data-ttu-id="8de9c-149">Nasıl yapılır: Federe Bir Hizmette Kimlik Bilgilerini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="8de9c-149">How to: Configure Credentials on a Federation Service</span></span>](how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="8de9c-150">Nasıl yapılır: Federe İstemci Oluşturma</span><span class="sxs-lookup"><span data-stu-id="8de9c-150">How to: Create a Federated Client</span></span>](how-to-create-a-federated-client.md)
- [<span data-ttu-id="8de9c-151">İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="8de9c-151">Message Security</span></span>](message-security-in-wcf.md)
- [<span data-ttu-id="8de9c-152">Bağlamalar ve Güvenlik</span><span class="sxs-lookup"><span data-stu-id="8de9c-152">Bindings and Security</span></span>](bindings-and-security.md)
