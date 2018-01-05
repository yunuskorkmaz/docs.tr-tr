---
title: "Nasıl yapılır: Kanal Güvenliği Kimlik Bilgilerini Belirtme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f8e03f47-9c4f-4dd5-8f85-429e6d876119
caps.latest.revision: "18"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: e2aedb06ec694f6c7dfb12b70ab919ae23eed17e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-channel-security-credentials"></a><span data-ttu-id="d7f14-102">Nasıl yapılır: Kanal Güvenliği Kimlik Bilgilerini Belirtme</span><span class="sxs-lookup"><span data-stu-id="d7f14-102">How to: Specify Channel Security Credentials</span></span>
<span data-ttu-id="d7f14-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Hizmet bilinen adı verir çağırmak COM uygulamaları [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Hizmetleri.</span><span class="sxs-lookup"><span data-stu-id="d7f14-103">The [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Service Moniker allows COM applications to call [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services.</span></span> <span data-ttu-id="d7f14-104">Çoğu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Hizmetleri istemci kimlik doğrulaması ve yetkilendirme kimlik bilgilerini belirtmenizi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d7f14-104">Most [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services require the client to specify credentials for authentication and authorization.</span></span> <span data-ttu-id="d7f14-105">Çağrılırken bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] gelen hizmet bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci, bu kimlik bilgileri yönetilen kod veya uygulama yapılandırma dosyası belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d7f14-105">When calling a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service from a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client, you can specify these credentials in managed code or in an application configuration file.</span></span> <span data-ttu-id="d7f14-106">Çağrılırken bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmeti bir COM uygulamasından kullandığınız <xref:System.ServiceModel.ComIntegration.IChannelCredentials> kimlik bilgilerini belirtmek için arabirim.</span><span class="sxs-lookup"><span data-stu-id="d7f14-106">When calling a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service from a COM application, you can use the <xref:System.ServiceModel.ComIntegration.IChannelCredentials> interface to specify credentials.</span></span> <span data-ttu-id="d7f14-107">Bu konuda kullanarak kimlik bilgilerini belirtmek için çeşitli şekillerde gösterecektir <xref:System.ServiceModel.ComIntegration.IChannelCredentials> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="d7f14-107">This topic will illustrate various ways to specify credentials using the <xref:System.ServiceModel.ComIntegration.IChannelCredentials> interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d7f14-108"><xref:System.ServiceModel.ComIntegration.IChannelCredentials>IDispatch tabanlı bir arabirim ve Visual Studio ortamında IntelliSense işlevselliği almazsınız.</span><span class="sxs-lookup"><span data-stu-id="d7f14-108"><xref:System.ServiceModel.ComIntegration.IChannelCredentials> is an IDispatch-based interface and you will not get IntelliSense functionality in the Visual Studio environment.</span></span>  
  
 <span data-ttu-id="d7f14-109">Bu makalede kullanacağı [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tanımlanan hizmet [ileti güvenliği örneği](../../../../docs/framework/wcf/samples/message-security-sample.md).</span><span class="sxs-lookup"><span data-stu-id="d7f14-109">This article will use the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service defined in the [Message Security Sample](../../../../docs/framework/wcf/samples/message-security-sample.md).</span></span>  
  
### <a name="to-specify-a-client-certificate"></a><span data-ttu-id="d7f14-110">Bir istemci sertifikasını belirtmek için</span><span class="sxs-lookup"><span data-stu-id="d7f14-110">To specify a client certificate</span></span>  
  
1.  <span data-ttu-id="d7f14-111">Setup.bat dosya oluşturmak ve gerekli test sertifikaları yüklemek için ileti güvenliği dizininde çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d7f14-111">Run the Setup.bat file in the Message Security directory to create and install the required test certificates.</span></span>  
  
2.  <span data-ttu-id="d7f14-112">İleti güvenliği projesini açın.</span><span class="sxs-lookup"><span data-stu-id="d7f14-112">Open the Message Security project.</span></span>  
  
3.  <span data-ttu-id="d7f14-113">Ekleme `[ServiceBehavior(Namespace=``http://Microsoft.ServiceModel.Samples``)]` için `ICalculator` arabirim tanımı.</span><span class="sxs-lookup"><span data-stu-id="d7f14-113">Add `[ServiceBehavior(Namespace=``http://Microsoft.ServiceModel.Samples``)]` to the `ICalculator` interface definition.</span></span>  
  
4.  <span data-ttu-id="d7f14-114">Ekleme `bindingNamespace=``http://Microsoft.ServiceModel.Samples` App.config hizmeti için uç nokta etiketinde için.</span><span class="sxs-lookup"><span data-stu-id="d7f14-114">Add `bindingNamespace=``http://Microsoft.ServiceModel.Samples` to the endpoint tag in the App.config for the service.</span></span>  
  
5.  <span data-ttu-id="d7f14-115">İleti güvenliği örneği oluşturun ve Service.exe çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d7f14-115">Build the Message Security Sample and run Service.exe.</span></span> <span data-ttu-id="d7f14-116">Internet Explorer'ı kullanın ve hizmetin çalıştığından emin olmak için hizmetin URI (8000/ServiceModelSamples/hizmet) göz atın.</span><span class="sxs-lookup"><span data-stu-id="d7f14-116">Use Internet Explorer and browse to the service's URI (http://localhost:8000/ServiceModelSamples/Service) to ensure that the service is working.</span></span>  
  
6.  <span data-ttu-id="d7f14-117">Visual Basic 6.0 açın ve yeni bir standart .exe dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d7f14-117">Open Visual Basic 6.0 and create a new Standard .exe file.</span></span> <span data-ttu-id="d7f14-118">Aşağıdaki kod tıklatın işleyicisine eklemek için düğmesini çift tıklayın ve forma düğme ekleme:</span><span class="sxs-lookup"><span data-stu-id="d7f14-118">Add a button to the form and double-click the button to add the following code to the Click handler:</span></span>  
  
    ```  
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
  
7.  <span data-ttu-id="d7f14-119">Visual Basic uygulamasını çalıştırın ve sonuçları doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="d7f14-119">Run the Visual Basic application and verify the results.</span></span>  
  
     <span data-ttu-id="d7f14-120">Visual Basic uygulama Ekle (3, 4) çağırma gelen sonuç içeren bir ileti kutusu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d7f14-120">The Visual Basic application will display a message box with the result from calling Add(3, 4).</span></span> <span data-ttu-id="d7f14-121"><xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromFile%28System.String%2CSystem.String%2CSystem.String%29>veya <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStoreByName%28System.String%2CSystem.String%2CSystem.String%29> de yerine kullanılabilir <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStore%28System.String%2CSystem.String%2CSystem.String%2CSystem.Object%29> istemci sertifikasını ayarlamak için:</span><span class="sxs-lookup"><span data-stu-id="d7f14-121"><xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromFile%28System.String%2CSystem.String%2CSystem.String%29> or <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStoreByName%28System.String%2CSystem.String%2CSystem.String%29> can also be used in place of <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetClientCertificateFromStore%28System.String%2CSystem.String%2CSystem.String%2CSystem.Object%29> to set the Client Certificate:</span></span>  
  
    ```  
    monikerProxy.ChannelCredentials.SetClientCertificateFromFile "C:\MyClientCert.pfx", "password", "DefaultKeySet"  
    ```  
  
> [!NOTE]
>  <span data-ttu-id="d7f14-122">Bu çağrı çalışması istemci sertifikası istemci çalıştıran makinede güvenilir olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d7f14-122">For this call to work, the client certificate needs to be trusted on the machine the client is running on.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d7f14-123">Ad hatalı veya hizmet kullanılamıyor çağrısı `GetObject` "Geçersiz sözdizimi." bildiren bir hata döndürür</span><span class="sxs-lookup"><span data-stu-id="d7f14-123">If the moniker is malformed or if the service is unavailable, the call to `GetObject` will return an error saying "Invalid Syntax."</span></span> <span data-ttu-id="d7f14-124">Bu hatayı alırsanız, kullanmakta olduğunuz adının doğru olduğundan ve hizmet kullanılabilir olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="d7f14-124">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
### <a name="to-specify-user-name-and-password"></a><span data-ttu-id="d7f14-125">Kullanıcı adı ve parola belirtmek için</span><span class="sxs-lookup"><span data-stu-id="d7f14-125">To specify user name and password</span></span>  
  
1.  <span data-ttu-id="d7f14-126">Kullanılacak hizmet App.config dosyasını değiştirmek `wsHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="d7f14-126">Modify the Service App.config file to use the `wsHttpBinding`.</span></span> <span data-ttu-id="d7f14-127">Bu, kullanıcı adı ve parola doğrulamasını gereklidir:</span><span class="sxs-lookup"><span data-stu-id="d7f14-127">This is required for user name and password validation:</span></span>  
  
  
  
2.  <span data-ttu-id="d7f14-128">Ayarlama `clientCredentialType` kullanıcı adı için:</span><span class="sxs-lookup"><span data-stu-id="d7f14-128">Set the `clientCredentialType` to UserName:</span></span>  
  
  
  
3.  <span data-ttu-id="d7f14-129">Visual Basic 6.0 açın ve yeni bir standart .exe dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d7f14-129">Open Visual Basic 6.0 and create a new Standard .exe file.</span></span> <span data-ttu-id="d7f14-130">Aşağıdaki kod tıklatın işleyicisine eklemek için düğmesini çift tıklayın ve forma düğme ekleme:</span><span class="sxs-lookup"><span data-stu-id="d7f14-130">Add a button to the form and double-click the button to add the following code to the Click handler:</span></span>  
  
    ```  
    monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
    monString = monString + ", address=http://localhost:8000/ServiceModelSamples/Service"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
    Set monikerProxy = GetObject(monString)  
  
    monikerProxy.ChannelCredentials.SetServiceCertificateAuthentication "CurrentUser", "NoCheck", "PeerOrChainTrust"  
    monikerProxy.ChannelCredentials.SetUserNameCredential "username", "password"  
  
    MsgBox monikerProxy.Add(3, 4)  
    ```  
  
4.  <span data-ttu-id="d7f14-131">Visual Basic uygulamasını çalıştırın ve sonuçları doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="d7f14-131">Run the Visual Basic application and verify the results.</span></span> <span data-ttu-id="d7f14-132">Visual Basic uygulama Ekle (3, 4) çağırma gelen sonuç içeren bir ileti kutusu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d7f14-132">The Visual Basic application will display a message box with the result from calling Add(3, 4).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d7f14-133">Bu örnekte hizmet bilinen adı belirtilen bağlama için WSHttpBinding_ICalculator değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="d7f14-133">The binding specified in the service moniker in this sample has been changed to WSHttpBinding_ICalculator.</span></span> <span data-ttu-id="d7f14-134">Geçerli bir kullanıcı adı ve parola çağrısında sağlamanız gerektiğini de unutmayın <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetUserNameCredential%28System.String%2CSystem.String%29>.</span><span class="sxs-lookup"><span data-stu-id="d7f14-134">Also note that you must supply a valid user name and password in the call to <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetUserNameCredential%28System.String%2CSystem.String%29>.</span></span>  
  
### <a name="to-specify-windows-credentials"></a><span data-ttu-id="d7f14-135">Windows kimlik bilgilerini belirtmek için</span><span class="sxs-lookup"><span data-stu-id="d7f14-135">To specify Windows Credentials</span></span>  
  
1.  <span data-ttu-id="d7f14-136">Ayarlama `clientCredentialType` Windows hizmeti App.config dosyasında:</span><span class="sxs-lookup"><span data-stu-id="d7f14-136">Set `clientCredentialType` to Windows in the Service App.config file:</span></span>  
  
  
  
2.  <span data-ttu-id="d7f14-137">Visual Basic 6.0 açın ve yeni bir standart .exe dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d7f14-137">Open Visual Basic 6.0 and create a new Standard .exe file.</span></span> <span data-ttu-id="d7f14-138">Aşağıdaki kod tıklatın işleyicisine eklemek için düğmesini çift tıklayın ve forma düğme ekleme:</span><span class="sxs-lookup"><span data-stu-id="d7f14-138">Add a button to the form and double-click the button to add the following code to the Click handler:</span></span>  
  
    ```  
    monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
    monString = monString + ", address=http://localhost:8000/ServiceModelSamples/Service"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", upnidentity=domain\userID"  
  
    Set monikerProxy = GetObject(monString)  
     monikerProxy.ChannelCredentials.SetWindowsCredential "domain", "userID", "password", 1, True  
  
    MsgBox monikerProxy.Add(3, 4)  
    ```  
  
3.  <span data-ttu-id="d7f14-139">Visual Basic uygulamasını çalıştırın ve sonuçları doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="d7f14-139">Run the Visual Basic application and verify the results.</span></span> <span data-ttu-id="d7f14-140">Visual Basic uygulama Ekle (3, 4) çağırma gelen sonuç içeren bir ileti kutusu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d7f14-140">The Visual Basic application will display a message box with the result from calling Add(3, 4).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d7f14-141">"Etki alanı", "userID" ve "parola" geçerli değerlerle değiştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="d7f14-141">You must replace "domain", "userID", and "password" with valid values.</span></span>  
  
### <a name="to-specify-an-issue-token"></a><span data-ttu-id="d7f14-142">Bir sorun belirteci belirtmek için</span><span class="sxs-lookup"><span data-stu-id="d7f14-142">To specify an issue token</span></span>  
  
1.  <span data-ttu-id="d7f14-143">Sorunu belirteçleri federe güvenlik kullanan uygulamalar için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d7f14-143">Issue tokens are used only for applications using federated security.</span></span> <span data-ttu-id="d7f14-144">Federasyon güvenliği hakkında daha fazla bilgi için bkz: [Federasyon ve verilen belirteçleri](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md) ve [Federasyon örnek](../../../../docs/framework/wcf/samples/federation-sample.md).</span><span class="sxs-lookup"><span data-stu-id="d7f14-144">For more information about federated security, see [Federation and Issued Tokens](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md) and [Federation Sample](../../../../docs/framework/wcf/samples/federation-sample.md).</span></span>  
  
     <span data-ttu-id="d7f14-145">Aşağıdaki Visual Basic kod örneği nasıl çağrılacağını gösterir <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29> yöntemi:</span><span class="sxs-lookup"><span data-stu-id="d7f14-145">The following Visual Basic code example illustrates how to call the <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29> method:</span></span>  
  
    ```  
        monString = "service:mexAddress=http://localhost:8000/ServiceModelSamples/Service?wsdl"  
        monString = monString + ", address=http://localhost:8000/SomeService/Service"  
        monString = monString + ", contract=ICalculator, contractNamespace=http://SomeService.Samples"  
        monString = monString + ", binding=WSHttpBinding_ISomeContract, bindingNamespace=http://SomeService.Samples"  
  
        Set monikerProxy = GetObject(monString)  
    monikerProxy.SetIssuedToken("http://somemachine/sts", "bindingType", "binding")  
    ```  
  
     <span data-ttu-id="d7f14-146">Bu yöntem için parametreler hakkında daha fazla bilgi için bkz: <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29>.</span><span class="sxs-lookup"><span data-stu-id="d7f14-146">For more information about the parameters for this method, see <xref:System.ServiceModel.ComIntegration.IChannelCredentials.SetIssuedToken%28System.String%2CSystem.String%2CSystem.String%29>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7f14-147">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d7f14-147">See Also</span></span>  
 [<span data-ttu-id="d7f14-148">Federasyon</span><span class="sxs-lookup"><span data-stu-id="d7f14-148">Federation</span></span>](../../../../docs/framework/wcf/feature-details/federation.md)  
 [<span data-ttu-id="d7f14-149">Nasıl yapılır: Federe Bir Hizmette Kimlik Bilgilerini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d7f14-149">How to: Configure Credentials on a Federation Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 [<span data-ttu-id="d7f14-150">Nasıl yapılır: Federe İstemci Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d7f14-150">How to: Create a Federated Client</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="d7f14-151">İleti Güvenliği</span><span class="sxs-lookup"><span data-stu-id="d7f14-151">Message Security</span></span>](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)  
 [<span data-ttu-id="d7f14-152">Bağlamalar ve Güvenlik</span><span class="sxs-lookup"><span data-stu-id="d7f14-152">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)
