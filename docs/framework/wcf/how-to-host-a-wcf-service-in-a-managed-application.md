---
title: "Nasıl yapılır: Yönetilen Bir Uygulamada Bir WCF Hizmeti Barındırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 5eb29db0-b6dc-4e77-8c68-0a62f79d743b
caps.latest.revision: "42"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6491faa6134c1e80e07294d8f888200c04fa8704
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-host-a-wcf-service-in-a-managed-application"></a><span data-ttu-id="9ecd6-102">Nasıl yapılır: Yönetilen Bir Uygulamada Bir WCF Hizmeti Barındırma</span><span class="sxs-lookup"><span data-stu-id="9ecd6-102">How to: Host a WCF Service in a Managed Application</span></span>
<span data-ttu-id="9ecd6-103">Yönetilen bir uygulama içinde bir hizmet barındırmak için hizmet içinde yönetilen uygulama kodu için kod ekleme, hizmet için bir uç nokta imperatively kodda, yapılandırma veya varsayılan uç noktalarını kullanarak aracılığıyla bildirimli olarak tanımlamanızı ve ardından oluşturmak bir örneği <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="9ecd6-103">To host a service inside a managed application, embed the code for the service inside the managed application code, define an endpoint for the service either imperatively in code, declaratively through configuration, or using default endpoints, and then create an instance of <xref:System.ServiceModel.ServiceHost>.</span></span>  
  
 <span data-ttu-id="9ecd6-104">İleti alma başlatmak için arama <xref:System.ServiceModel.ICommunicationObject.Open%2A> üzerinde <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="9ecd6-104">To start receiving messages, call <xref:System.ServiceModel.ICommunicationObject.Open%2A> on <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="9ecd6-105">Bu oluşturur ve hizmet için dinleyici açar.</span><span class="sxs-lookup"><span data-stu-id="9ecd6-105">This creates and opens the listener for the service.</span></span> <span data-ttu-id="9ecd6-106">Bu şekilde bir hizmet barındırma genellikle "yönetilen uygulamayı barındıran iş yaptığını çünkü kendi kendine barındırma olarak" adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="9ecd6-106">Hosting a service in this way is often referred to as "self-hosting" because the managed application is doing the hosting work itself.</span></span> <span data-ttu-id="9ecd6-107">Hizmeti kapatmak için çağrı <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> üzerinde <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="9ecd6-107">To close the service, call <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> on <xref:System.ServiceModel.ServiceHost>.</span></span>  
  
 <span data-ttu-id="9ecd6-108">Bir hizmet, yönetilen bir Windows hizmetinde, Internet Information Services (IIS) veya Windows İşlem Etkinleştirme Hizmeti (WAS) barındırılabilir.</span><span class="sxs-lookup"><span data-stu-id="9ecd6-108">A service can also be hosted in a managed Windows service, in Internet Information Services (IIS), or in Windows Process Activation Service (WAS).</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="9ecd6-109">bir hizmetin seçeneklerini barındırma, bkz: [barındırma hizmetleri](../../../docs/framework/wcf/hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="9ecd6-109"> hosting options for a service, see [Hosting Services](../../../docs/framework/wcf/hosting-services.md).</span></span>  
  
 <span data-ttu-id="9ecd6-110">Yönetilen bir uygulamada bir hizmet barındırma en esnek bir seçenektir; çünkü dağıtmak için en az altyapısı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="9ecd6-110">Hosting a service in a managed application is the most flexible option because it requires the least infrastructure to deploy.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="9ecd6-111">barındırma hizmetleri yönetilen uygulamalarda, bkz: [yönetilen bir uygulamada barındırma](../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md).</span><span class="sxs-lookup"><span data-stu-id="9ecd6-111"> hosting services in managed applications, see [Hosting in a Managed Application](../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md).</span></span>  
  
 <span data-ttu-id="9ecd6-112">Aşağıdaki yordam, bir konsol uygulamasında kendini barındıran hizmet uygulamak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="9ecd6-112">The following procedure demonstrates how to implement a self-hosted service in a console application.</span></span>  
  
### <a name="to-create-a-self-hosted-service"></a><span data-ttu-id="9ecd6-113">Kendini barındıran bir hizmet oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="9ecd6-113">To create a self-hosted service</span></span>  
  
1.  <span data-ttu-id="9ecd6-114">Açık [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] seçip **yeni**, **proje...**  gelen **dosya** menüsü.</span><span class="sxs-lookup"><span data-stu-id="9ecd6-114">Open [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] and select **New**, **Project...** from the **File** menu.</span></span>  
  
2.  <span data-ttu-id="9ecd6-115">İçinde **yüklü şablonlar** listesinde **Visual C#**, **Windows** veya **Visual Basic**, **Windows**.</span><span class="sxs-lookup"><span data-stu-id="9ecd6-115">In the **Installed Templates** list, select **Visual C#**, **Windows** or **Visual Basic**, **Windows**.</span></span> <span data-ttu-id="9ecd6-116">Bağlı olarak, [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] ayarları, birini veya bunların her ikisi de altında olabilir **diğer diller** düğümünde **yüklü şablonlar** listesi.</span><span class="sxs-lookup"><span data-stu-id="9ecd6-116">Depending on your [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] settings, one or both of these may be under the **Other Languages** node in the **Installed Templates** list.</span></span>  
  
3.  <span data-ttu-id="9ecd6-117">Seçin **konsol uygulaması** gelen **Windows** listesi.</span><span class="sxs-lookup"><span data-stu-id="9ecd6-117">Select **Console Application** from the **Windows** list.</span></span> <span data-ttu-id="9ecd6-118">Tür `SelfHost` içinde **adı** kutusuna ve tıklatın **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="9ecd6-118">Type `SelfHost` in the **Name** box and click **OK**.</span></span>  
  
4.  <span data-ttu-id="9ecd6-119">Sağ **SelfHost** içinde **Çözüm Gezgini** seçip **Başvuru Ekle...** . Seçin **System.ServiceModel** gelen **.NET** sekmesinde **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="9ecd6-119">Right-click **SelfHost** in **Solution Explorer** and select **Add Reference...**. Select **System.ServiceModel** from the **.NET** tab and click **OK**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="9ecd6-120">Varsa **Çözüm Gezgini** pencere görünür, select değil **Çözüm Gezgini** gelen **Görünüm** menüsü.</span><span class="sxs-lookup"><span data-stu-id="9ecd6-120">If the **Solution Explorer** window is not visible, select **Solution Explorer** from the **View** menu.</span></span>  
  
5.  <span data-ttu-id="9ecd6-121">Çift **Program.cs** veya **Module1.vb** içinde **Çözüm Gezgini** zaten açık değilse kod penceresinde açın.</span><span class="sxs-lookup"><span data-stu-id="9ecd6-121">Double-click **Program.cs** or **Module1.vb** in **Solution Explorer** to open it in the code window if it is not already open.</span></span> <span data-ttu-id="9ecd6-122">Dosyanın üst kısmında aşağıdaki deyimleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9ecd6-122">Add the following statements at the top of the file.</span></span>  
  
     [!code-csharp[CFX_SelfHost4#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#1)]
     [!code-vb[CFX_SelfHost4#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#1)]  
  
6.  <span data-ttu-id="9ecd6-123">Bir hizmet sözleşmesini uygulama ve tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="9ecd6-123">Define and implement a service contract.</span></span> <span data-ttu-id="9ecd6-124">Bu örnek tanımlayan bir `HelloWorldService` hizmetine giriş dayalı bir ileti döndürür.</span><span class="sxs-lookup"><span data-stu-id="9ecd6-124">This example defines a `HelloWorldService` that returns a message based on the input to the service.</span></span>  
  
     [!code-csharp[CFX_SelfHost4#2](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#2)]
     [!code-vb[CFX_SelfHost4#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#2)]  
  
    > [!NOTE]
    >  [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="9ecd6-125">tanımlamak ve bir hizmet arabirimini uygulayan bkz [nasıl yapılır: bir hizmet sözleşmesini tanımlama](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md) ve [nasıl yapılır: bir hizmet sözleşmesini uygulama](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md).</span><span class="sxs-lookup"><span data-stu-id="9ecd6-125"> how to define and implement a service interface, see [How to: Define a Service Contract](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md) and [How to: Implement a Service Contract](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md).</span></span>  
  
7.  <span data-ttu-id="9ecd6-126">Üstündeki `Main` yöntemi, bir örneğini oluşturmak <xref:System.Uri> hizmeti temel adresi ile sınıfı.</span><span class="sxs-lookup"><span data-stu-id="9ecd6-126">At the top of the `Main` method, create an instance of the <xref:System.Uri> class with the base address for the service.</span></span>  
  
     [!code-csharp[CFX_SelfHost4#3](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#3)]
     [!code-vb[CFX_SelfHost4#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#3)]  
  
8.  <span data-ttu-id="9ecd6-127">Bir örneğini oluşturmak <xref:System.ServiceModel.ServiceHost> geçirme sınıfı, bir <xref:System.Type> bu temsil Tekdüzen Kaynak Tanımlayıcısı (URI) için hizmet türü ve taban adresi <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Type%2CSystem.Uri%5B%5D%29>.</span><span class="sxs-lookup"><span data-stu-id="9ecd6-127">Create an instance of the <xref:System.ServiceModel.ServiceHost> class, passing a <xref:System.Type> that represents the service type and the base address Uniform Resource Identifier (URI) to the <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Type%2CSystem.Uri%5B%5D%29>.</span></span> <span data-ttu-id="9ecd6-128">Meta veri yayımlama etkinleştirin ve ardından arama <xref:System.ServiceModel.ICommunicationObject.Open%2A> yöntemi <xref:System.ServiceModel.ServiceHost> hizmeti başlatmak ve iletileri almak için hazırlayın.</span><span class="sxs-lookup"><span data-stu-id="9ecd6-128">Enable metadata publishing, and then call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method on the <xref:System.ServiceModel.ServiceHost> to initialize the service and prepare it to receive messages.</span></span>  
  
     [!code-csharp[CFX_SelfHost4#4](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#4)]
     [!code-vb[CFX_SelfHost4#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#4)]       
  
    > [!NOTE]
    >  <span data-ttu-id="9ecd6-129">Bu örnek varsayılan uç noktaları kullanır ve bu hizmet için herhangi bir yapılandırma dosyası gereklidir.</span><span class="sxs-lookup"><span data-stu-id="9ecd6-129">This example uses default endpoints, and no configuration file is required for this service.</span></span> <span data-ttu-id="9ecd6-130">Uç nokta yok yapılandırdıysanız, çalışma zamanı hizmeti tarafından uygulanan her hizmet sözleşmesi için her bir taban adresi için bir uç noktası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9ecd6-130">If no endpoints are configured, then the runtime creates one endpoint for each base address for each service contract implemented by the service.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="9ecd6-131">Varsayılan uç noktaları için bkz: [Basitleştirilmiş yapılandırma](../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="9ecd6-131"> default endpoints, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
9. <span data-ttu-id="9ecd6-132">Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="9ecd6-132">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
### <a name="to-test-the-service"></a><span data-ttu-id="9ecd6-133">Hizmeti sınamak için</span><span class="sxs-lookup"><span data-stu-id="9ecd6-133">To test the service</span></span>  
  
1.  <span data-ttu-id="9ecd6-134">Hizmetini çalıştırmak için Ctrl + F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="9ecd6-134">Press Ctrl + F5 to run the service.</span></span>  
  
2.  <span data-ttu-id="9ecd6-135">Açık **WCF Test istemcisi**.</span><span class="sxs-lookup"><span data-stu-id="9ecd6-135">Open **WCF Test Client**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="9ecd6-136">Açmak için **WCF Test istemcisi**, açık bir [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] komut istemi ve yürütme **WcfTestClient.exe**.</span><span class="sxs-lookup"><span data-stu-id="9ecd6-136">To open **WCF Test Client**, open a [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] command prompt and execute **WcfTestClient.exe**.</span></span>  
  
3.  <span data-ttu-id="9ecd6-137">Seçin **hizmeti Ekle...**  gelen **dosya** menüsü.</span><span class="sxs-lookup"><span data-stu-id="9ecd6-137">Select **Add Service...** from the **File** menu.</span></span>  
  
4.  <span data-ttu-id="9ecd6-138">Tür `http://localhost:8080/hello` tıklatın ve adres kutusuna içine **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="9ecd6-138">Type `http://localhost:8080/hello` into the address box and click **OK**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="9ecd6-139">Bu adım başarısız yoksa hizmetinin çalıştığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="9ecd6-139">Make sure the service is running or else this step fails.</span></span> <span data-ttu-id="9ecd6-140">Kodda taban adresi değiştiyse, değiştirilmiş taban adresi bu adımı kullanın.</span><span class="sxs-lookup"><span data-stu-id="9ecd6-140">If you have changed the base address in the code, then use the modified base address in this step.</span></span>  
  
5.  <span data-ttu-id="9ecd6-141">Çift **SayHello** altında **My hizmeti projeleri** düğümü.</span><span class="sxs-lookup"><span data-stu-id="9ecd6-141">Double-click **SayHello** under the **My Service Projects** node.</span></span> <span data-ttu-id="9ecd6-142">Adınızı içine yazın **değeri** sütununda **isteği** liste öğesini tıklatıp **Invoke**.</span><span class="sxs-lookup"><span data-stu-id="9ecd6-142">Type your name into the **Value** column in the **Request** list, and click **Invoke**.</span></span> <span data-ttu-id="9ecd6-143">Bir yanıt iletisi görünür **yanıt** listesi.</span><span class="sxs-lookup"><span data-stu-id="9ecd6-143">A reply message appears in the **Response** list.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ecd6-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="9ecd6-144">Example</span></span>  
 <span data-ttu-id="9ecd6-145">Aşağıdaki örnekte bir <xref:System.ServiceModel.ServiceHost> türünde bir hizmet barındırmak için nesne `HelloWorldService`ve ardından çağırır <xref:System.ServiceModel.ICommunicationObject.Open%2A> yöntemi <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="9ecd6-145">The following example creates a <xref:System.ServiceModel.ServiceHost> object to host a service of type `HelloWorldService`, and then calls the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method on <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="9ecd6-146">Temel adres kodunda sağlanır, meta veri yayımlama etkindir ve varsayılan uç noktaları kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9ecd6-146">A base address is provided in code, metadata publishing is enabled, and default endpoints are used.</span></span>  
  
 [!code-csharp[CFX_SelfHost4#5](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#5)]
 [!code-vb[CFX_SelfHost4#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="9ecd6-147">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9ecd6-147">See Also</span></span>  
 <xref:System.Uri>  
 <xref:System.Configuration.ConfigurationManager.AppSettings%2A>  
 <xref:System.Configuration.ConfigurationManager>  
 [<span data-ttu-id="9ecd6-148">Nasıl yapılır: IIS'de WCF Hizmeti Barındırma</span><span class="sxs-lookup"><span data-stu-id="9ecd6-148">How to: Host a WCF Service in IIS</span></span>](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)  
 [<span data-ttu-id="9ecd6-149">Kendini Barındırma</span><span class="sxs-lookup"><span data-stu-id="9ecd6-149">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)  
 [<span data-ttu-id="9ecd6-150">Barındırma Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="9ecd6-150">Hosting Services</span></span>](../../../docs/framework/wcf/hosting-services.md)  
 [<span data-ttu-id="9ecd6-151">Nasıl yapılır: Bir Hizmet Anlaşması Tanımlama</span><span class="sxs-lookup"><span data-stu-id="9ecd6-151">How to: Define a Service Contract</span></span>](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)  
 [<span data-ttu-id="9ecd6-152">Nasıl yapılır: Bir Hizmet Anlaşmasını Uygulama</span><span class="sxs-lookup"><span data-stu-id="9ecd6-152">How to: Implement a Service Contract</span></span>](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)  
 [<span data-ttu-id="9ecd6-153">ServiceModel Meta Veri Yardımcı Programı Aracı (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="9ecd6-153">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [<span data-ttu-id="9ecd6-154">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="9ecd6-154">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="9ecd6-155">Sistem Tarafından Sağlanan Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="9ecd6-155">System-Provided Bindings</span></span>](../../../docs/framework/wcf/system-provided-bindings.md)
