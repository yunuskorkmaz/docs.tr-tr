---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: Kanal güvenliği kimlik bilgilerini belirtme'
title: 'Nasıl yapılır: Kanal Güvenliği Kimlik Bilgilerini Belirtme'
ms.date: 03/30/2017
ms.assetid: f8e03f47-9c4f-4dd5-8f85-429e6d876119
ms.openlocfilehash: 18cbb1ea1113e5b31f5adb43556db03d91c618ba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99643156"
---
# <a name="how-to-specify-channel-security-credentials"></a><span data-ttu-id="129b3-103">Nasıl yapılır: Kanal Güvenliği Kimlik Bilgilerini Belirtme</span><span class="sxs-lookup"><span data-stu-id="129b3-103">How to: Specify Channel Security Credentials</span></span>

<span data-ttu-id="129b3-104">Windows Communication Foundation (WCF) hizmet bilinen adı, COM uygulamalarının WCF hizmetlerini çağırmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="129b3-104">The Windows Communication Foundation (WCF) Service Moniker allows COM applications to call WCF services.</span></span> <span data-ttu-id="129b3-105">Çoğu WCF hizmeti, istemcinin kimlik doğrulama ve yetkilendirme için kimlik bilgilerini belirtmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="129b3-105">Most WCF services require the client to specify credentials for authentication and authorization.</span></span> <span data-ttu-id="129b3-106">WCF istemcisinden bir WCF hizmetini çağırırken bu kimlik bilgilerini yönetilen kodda veya bir uygulama yapılandırma dosyasında belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="129b3-106">When calling a WCF service from a WCF client, you can specify these credentials in managed code or in an application configuration file.</span></span> <span data-ttu-id="129b3-107">Bir WCF hizmetini bir COM uygulamasından çağırırken, <xref:System.ServiceModel.ComIntegration.IChannelCredentials> kimlik bilgilerini belirtmek için arabirimini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="129b3-107">When calling a WCF service from a COM application, you can use the <xref:System.ServiceModel.ComIntegration.IChannelCredentials> interface to specify credentials.</span></span> <span data-ttu-id="129b3-108">Bu konu, arabirimi kullanarak kimlik bilgilerini belirtmek için çeşitli yollar gösterir <xref:System.ServiceModel.ComIntegration.IChannelCredentials> .</span><span class="sxs-lookup"><span data-stu-id="129b3-108">This topic will illustrate various ways to specify credentials using the <xref:System.ServiceModel.ComIntegration.IChannelCredentials> interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="129b3-109"><xref:System.ServiceModel.ComIntegration.IChannelCredentials> , IDispatch tabanlı bir arabirimdir ve Visual Studio ortamında IntelliSense işlevselliği almaz.</span><span class="sxs-lookup"><span data-stu-id="129b3-109"><xref:System.ServiceModel.ComIntegration.IChannelCredentials> is an IDispatch-based interface and you will not get IntelliSense functionality in the Visual Studio environment.</span></span>  
  
 <span data-ttu-id="129b3-110">Bu makalede [Ileti güvenliği örneğinde](../samples/message-security-sample.md)tanımlanan WCF hizmeti kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="129b3-110">This article will use the WCF service defined in the [Message Security Sample](../samples/message-security-sample.md).</span></span>  
  
### <a name="to-specify-a-client-certificate"></a><span data-ttu-id="129b3-111">İstemci sertifikası belirtmek için</span><span class="sxs-lookup"><span data-stu-id="129b3-111">To specify a client certificate</span></span>  
  
1. <span data-ttu-id="129b3-112">Gerekli test sertifikalarını oluşturmak ve yüklemek için Ileti güvenlik dizininde Setup.bat dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="129b3-112">Run the Setup.bat file in the Message Security directory to create and install the required test certificates.</span></span>  
  
2. <span data-ttu-id="129b3-113">Ileti güvenliği projesini açın.</span><span class="sxs-lookup"><span data-stu-id="129b3-113">Open the Message Security project.</span></span>  
  
3. <span data-ttu-id="129b3-114">`[ServiceBehavior(Namespace="http://Microsoft.ServiceModel.Samples")]` `ICalculator` Arabirim tanımına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="129b3-114">Add `[ServiceBehavior(Namespace="http://Microsoft.ServiceModel.Samples")]` to the `ICalculator` interface definition.</span></span>  
  
4. <span data-ttu-id="129b3-115">`bindingNamespace="http://Microsoft.ServiceModel.Samples"`Hizmetin App.config bitiş noktası etiketine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="129b3-115">Add `bindingNamespace="http://Microsoft.ServiceModel.Samples"` to the endpoint tag in the App.config for the service.</span></span>  
  
5. <span data-ttu-id="129b3-116">Ileti güvenlik örneğini oluşturun ve Service.exe çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="129b3-116">Build the Message Security Sample and run Service.exe.</span></span> <span data-ttu-id="129b3-117">Hizmetin çalıştığından emin olmak için Internet Explorer 'ı kullanın ve hizmetin URI 'sine ( `http://localhost:8000/ServiceModelSamples/Service` ) gidin.</span><span class="sxs-lookup"><span data-stu-id="129b3-117">Use Internet Explorer and browse to the service's URI (`http://localhost:8000/ServiceModelSamples/Service`) to ensure that the service is working.</span></span>  
  
6. <span data-ttu-id="129b3-118">Visual Basic 6,0 ' i açın ve yeni bir standart. exe dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="129b3-118">Open Visual Basic 6.0 and create a new Standard .exe file.</span></span> <span data-ttu-id="129b3-119">Forma bir düğme ekleyin ve tıklama işleyicisine aşağıdaki kodu eklemek için düğmeye çift tıklayın:</span><span class="sxs-lookup"><span data-stu-id="129b3-119">Add a button to the form and double-click the button to add the following code to the Click handler:</span></span>  
  
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
  
7. <span data-ttu-id="129b3-120">Visual Basic uygulamayı çalıştırın ve sonuçları doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="129b3-120">Run the Visual Basic application and verify the results.</span></span>  
  
     <span data-ttu-id="129b3-121">Visual Basic uygulama, Add (3, 4) çağırmanın sonucunu içeren bir ileti kutusu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="129b3-121">The Visual Basic application will display a message box with the result from calling Add(3, 4).</span></span> <span data-ttu-id="129b3-122"><xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromFile%28System.String%2CSystem.String%2CSystem.String%29><xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStoreByName%28System.String%2CSystem.String%2CSystem.String%29>Ayrıca, <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStore%28System.String%2CSystem.String%2CSystem.String%2CSystem.Object%29> istemci sertifikasını ayarlamak için yerinde de kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="129b3-122"><xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromFile%28System.String%2CSystem.String%2CSystem.String%29> or <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStoreByName%28System.String%2CSystem.String%2CSystem.String%29> can also be used in place of <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStore%28System.String%2CSystem.String%2CSystem.String%2CSystem.Object%29> to set the Client Certificate:</span></span>  
  
    ```vb  
    monikerProxy.ChannelCredentials.SetClientCertificateFromFile "C:\MyClientCert.pfx", "password", "DefaultKeySet"  
    ```  
  
> [!NOTE]
> <span data-ttu-id="129b3-123">Bu çağrının çalışması için, istemci sertifikasının, istemcinin üzerinde çalıştığı makinede güvenilir olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="129b3-123">For this call to work, the client certificate needs to be trusted on the machine the client is running on.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="129b3-124">Bilinen ad yanlış biçimlendirilmişse veya hizmet kullanılamıyorsa, çağrısı `GetObject` "geçersiz sözdizimi" belirten bir hata döndürür.</span><span class="sxs-lookup"><span data-stu-id="129b3-124">If the moniker is malformed or if the service is unavailable, the call to `GetObject` will return an error saying "Invalid Syntax."</span></span> <span data-ttu-id="129b3-125">Bu hatayı alırsanız, kullanmakta olduğunuz bilinen adın doğru olduğundan ve hizmetin kullanılabilir olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="129b3-125">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
### <a name="to-specify-user-name-and-password"></a><span data-ttu-id="129b3-126">Kullanıcı adı ve parola belirtmek için</span><span class="sxs-lookup"><span data-stu-id="129b3-126">To specify user name and password</span></span>  
  
1. <span data-ttu-id="129b3-127">Service App.config dosyasını kullanacak şekilde değiştirin `wsHttpBinding` .</span><span class="sxs-lookup"><span data-stu-id="129b3-127">Modify the Service App.config file to use the `wsHttpBinding`.</span></span> <span data-ttu-id="129b3-128">Bu, Kullanıcı adı ve parola doğrulaması için gereklidir:</span><span class="sxs-lookup"><span data-stu-id="129b3-128">This is required for user name and password validation:</span></span>  

2. <span data-ttu-id="129b3-129">Şunu `clientCredentialType` Kullanıcı adı olarak ayarla:</span><span class="sxs-lookup"><span data-stu-id="129b3-129">Set the `clientCredentialType` to UserName:</span></span>  

3. <span data-ttu-id="129b3-130">Visual Basic 6,0 ' i açın ve yeni bir standart. exe dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="129b3-130">Open Visual Basic 6.0 and create a new Standard .exe file.</span></span> <span data-ttu-id="129b3-131">Forma bir düğme ekleyin ve tıklama işleyicisine aşağıdaki kodu eklemek için düğmeye çift tıklayın:</span><span class="sxs-lookup"><span data-stu-id="129b3-131">Add a button to the form and double-click the button to add the following code to the Click handler:</span></span>  
  
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
  
4. <span data-ttu-id="129b3-132">Visual Basic uygulamayı çalıştırın ve sonuçları doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="129b3-132">Run the Visual Basic application and verify the results.</span></span> <span data-ttu-id="129b3-133">Visual Basic uygulama, Add (3, 4) çağırmanın sonucunu içeren bir ileti kutusu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="129b3-133">The Visual Basic application will display a message box with the result from calling Add(3, 4).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="129b3-134">Bu örnekteki hizmet takma adı 'nda belirtilen bağlama WSHttpBinding_ICalculator olarak değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="129b3-134">The binding specified in the service moniker in this sample has been changed to WSHttpBinding_ICalculator.</span></span> <span data-ttu-id="129b3-135">Ayrıca, çağrısına, için geçerli bir Kullanıcı adı ve parola belirtmeniz gerektiğini unutmayın <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetUserNameCredential%28System.String%2CSystem.String%29> .</span><span class="sxs-lookup"><span data-stu-id="129b3-135">Also note that you must supply a valid user name and password in the call to <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetUserNameCredential%28System.String%2CSystem.String%29>.</span></span>  
  
### <a name="to-specify-windows-credentials"></a><span data-ttu-id="129b3-136">Windows kimlik bilgilerini belirtmek için</span><span class="sxs-lookup"><span data-stu-id="129b3-136">To specify Windows Credentials</span></span>  
  
1. <span data-ttu-id="129b3-137">`clientCredentialType`Service App.config dosyasında Windows olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="129b3-137">Set `clientCredentialType` to Windows in the Service App.config file:</span></span>  

2. <span data-ttu-id="129b3-138">Visual Basic 6,0 ' i açın ve yeni bir standart. exe dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="129b3-138">Open Visual Basic 6.0 and create a new Standard .exe file.</span></span> <span data-ttu-id="129b3-139">Forma bir düğme ekleyin ve tıklama işleyicisine aşağıdaki kodu eklemek için düğmeye çift tıklayın:</span><span class="sxs-lookup"><span data-stu-id="129b3-139">Add a button to the form and double-click the button to add the following code to the Click handler:</span></span>  
  
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
  
3. <span data-ttu-id="129b3-140">Visual Basic uygulamayı çalıştırın ve sonuçları doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="129b3-140">Run the Visual Basic application and verify the results.</span></span> <span data-ttu-id="129b3-141">Visual Basic uygulama, Add (3, 4) çağırmanın sonucunu içeren bir ileti kutusu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="129b3-141">The Visual Basic application will display a message box with the result from calling Add(3, 4).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="129b3-142">"Domain", "UserID" ve "Password" değerlerini geçerli değerlerle değiştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="129b3-142">You must replace "domain", "userID", and "password" with valid values.</span></span>  
  
### <a name="to-specify-an-issue-token"></a><span data-ttu-id="129b3-143">Bir sorun belirteci belirtmek için</span><span class="sxs-lookup"><span data-stu-id="129b3-143">To specify an issue token</span></span>  
  
1. <span data-ttu-id="129b3-144">Sorun belirteçleri yalnızca Federe güvenlik kullanan uygulamalar için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="129b3-144">Issue tokens are used only for applications using federated security.</span></span> <span data-ttu-id="129b3-145">Federasyon güvenliği hakkında daha fazla bilgi için bkz. [Federasyon ve verilen belirteçler](federation-and-issued-tokens.md) ve [Federasyon örneği](../samples/federation-sample.md).</span><span class="sxs-lookup"><span data-stu-id="129b3-145">For more information about federated security, see [Federation and Issued Tokens](federation-and-issued-tokens.md) and [Federation Sample](../samples/federation-sample.md).</span></span>  
  
     <span data-ttu-id="129b3-146">Aşağıdaki Visual Basic kod örneği, yönteminin nasıl çağrılacağını göstermektedir <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29> :</span><span class="sxs-lookup"><span data-stu-id="129b3-146">The following Visual Basic code example illustrates how to call the <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29> method:</span></span>  
  
    ```vb
        monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
        monString = monString + ", address=http://localhost:8000/SomeService/Service"  
        monString = monString + ", contract=ICalculator, contractNamespace=http://SomeService.Samples"  
        monString = monString + ", binding=WSHttpBinding_ISomeContract, bindingNamespace=http://SomeService.Samples"  
  
        Set monikerProxy = GetObject(monString)  
    monikerProxy.SetIssuedToken("http://somemachine/sts", "bindingType", "binding")  
    ```  
  
     <span data-ttu-id="129b3-147">Bu yöntemin parametreleri hakkında daha fazla bilgi için bkz <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29> ..</span><span class="sxs-lookup"><span data-stu-id="129b3-147">For more information about the parameters for this method, see <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="129b3-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="129b3-148">See also</span></span>

- [<span data-ttu-id="129b3-149">Federasyon</span><span class="sxs-lookup"><span data-stu-id="129b3-149">Federation</span></span>](federation.md)
- [<span data-ttu-id="129b3-150">Nasıl yapılır: Federe Bir Hizmette Kimlik Bilgilerini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="129b3-150">How to: Configure Credentials on a Federation Service</span></span>](how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="129b3-151">Nasıl yapılır: Federe İstemci Oluşturma</span><span class="sxs-lookup"><span data-stu-id="129b3-151">How to: Create a Federated Client</span></span>](how-to-create-a-federated-client.md)
- [<span data-ttu-id="129b3-152">İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="129b3-152">Message Security</span></span>](message-security-in-wcf.md)
- [<span data-ttu-id="129b3-153">Bağlamalar ve Güvenlik</span><span class="sxs-lookup"><span data-stu-id="129b3-153">Bindings and Security</span></span>](bindings-and-security.md)
