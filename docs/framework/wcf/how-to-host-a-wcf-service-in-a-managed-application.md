---
title: 'Nasıl yapılır: Yönetilen Bir Uygulamada Bir WCF Hizmeti Barındırma'
ms.date: 09/17/2018
dev_langs:
- csharp
- vb
ms.assetid: 5eb29db0-b6dc-4e77-8c68-0a62f79d743b
ms.openlocfilehash: 131d99457427e0818f78076d987f550a99ad7cf0
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47196859"
---
# <a name="how-to-host-a-wcf-service-in-a-managed-app"></a><span data-ttu-id="1171c-102">Nasıl yapılır: yönetilen bir uygulamada bir WCF Hizmeti barındırma</span><span class="sxs-lookup"><span data-stu-id="1171c-102">How to: Host a WCF service in a managed app</span></span>

<span data-ttu-id="1171c-103">Bir hizmet içinde yönetilen bir uygulamayı barındırmak için hizmet içinde yönetilen bir uygulama kodu için kod ekleme, hizmet için bir uç nokta kesin kodda, yapılandırma veya varsayılan uç nokta kullanarak aracılığıyla bildirimli olarak tanımlamanızı ve oluşturup bir örneğini <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="1171c-103">To host a service inside a managed application, embed the code for the service inside the managed application code, define an endpoint for the service either imperatively in code, declaratively through configuration, or using default endpoints, and then create an instance of <xref:System.ServiceModel.ServiceHost>.</span></span>

<span data-ttu-id="1171c-104">İletileri almaya başlaması için çağrı <xref:System.ServiceModel.ICommunicationObject.Open%2A> üzerinde <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="1171c-104">To start receiving messages, call <xref:System.ServiceModel.ICommunicationObject.Open%2A> on <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="1171c-105">Bu, oluşturur ve hizmet için dinleyici açılır.</span><span class="sxs-lookup"><span data-stu-id="1171c-105">This creates and opens the listener for the service.</span></span> <span data-ttu-id="1171c-106">Bu şekilde bir hizmet barındırma genellikle "yönetilen uygulamayı barındıran iş yapıyor çünkü kendi kendine barındırma olarak" adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="1171c-106">Hosting a service in this way is often referred to as "self-hosting" because the managed application is doing the hosting work itself.</span></span> <span data-ttu-id="1171c-107">Hizmeti kapatmak için çağrı <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> üzerinde <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="1171c-107">To close the service, call <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> on <xref:System.ServiceModel.ServiceHost>.</span></span>

<span data-ttu-id="1171c-108">Bir hizmet, yönetilen bir Windows hizmetinde, Internet Information Services (IIS) veya Windows İşlem Etkinleştirme Hizmeti (WAS) barındırılabilir.</span><span class="sxs-lookup"><span data-stu-id="1171c-108">A service can also be hosted in a managed Windows service, in Internet Information Services (IIS), or in Windows Process Activation Service (WAS).</span></span> <span data-ttu-id="1171c-109">Barındırma seçenekleri bir hizmet için hakkında daha fazla bilgi için bkz. [barındırma hizmetleri](../../../docs/framework/wcf/hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="1171c-109">For more information about hosting options for a service, see [Hosting Services](../../../docs/framework/wcf/hosting-services.md).</span></span>

<span data-ttu-id="1171c-110">Dağıtmak için en az bir altyapı gerektiğinden bir hizmeti yönetilen bir uygulamada barındırma en esnek seçenektir.</span><span class="sxs-lookup"><span data-stu-id="1171c-110">Hosting a service in a managed application is the most flexible option because it requires the least infrastructure to deploy.</span></span> <span data-ttu-id="1171c-111">Barındırma hizmetleri, yönetilen uygulamalar hakkında daha fazla bilgi için bkz. [yönetilen bir uygulamada barındırma](../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md).</span><span class="sxs-lookup"><span data-stu-id="1171c-111">For more information about hosting services in managed applications, see [Hosting in a Managed Application](../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md).</span></span>

<span data-ttu-id="1171c-112">Aşağıdaki yordam, şirket içinde barındırılan hizmeti bir konsol uygulamasında uygulama gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1171c-112">The following procedure demonstrates how to implement a self-hosted service in a console application.</span></span>

## <a name="create-a-self-hosted-service"></a><span data-ttu-id="1171c-113">Şirket içinde barındırılan bir hizmet oluşturma</span><span class="sxs-lookup"><span data-stu-id="1171c-113">Create a self-hosted service</span></span>

1. <span data-ttu-id="1171c-114">Yeni bir konsol uygulaması oluşturun:</span><span class="sxs-lookup"><span data-stu-id="1171c-114">Create a new console application:</span></span>

   1. <span data-ttu-id="1171c-115">Visual Studio açıp seçin **yeni** > **proje** gelen **dosya** menüsü.</span><span class="sxs-lookup"><span data-stu-id="1171c-115">Open Visual Studio and select **New** > **Project** from the **File** menu.</span></span>

   2. <span data-ttu-id="1171c-116">İçinde **yüklü şablonlar** listesinden **Visual C#** veya **Visual Basic**ve ardından **Windows Masaüstü**.</span><span class="sxs-lookup"><span data-stu-id="1171c-116">In the **Installed Templates** list, select **Visual C#** or **Visual Basic**, and then select **Windows Desktop**.</span></span>

   3. <span data-ttu-id="1171c-117">Seçin **konsol uygulaması** şablonu.</span><span class="sxs-lookup"><span data-stu-id="1171c-117">Select the **Console App** template.</span></span> <span data-ttu-id="1171c-118">Tür `SelfHost` içinde **adı** kutusuna ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="1171c-118">Type `SelfHost` in the **Name** box and then choose **OK**.</span></span>

2. <span data-ttu-id="1171c-119">Sağ **SelfHost** içinde **Çözüm Gezgini** seçip **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="1171c-119">Right-click **SelfHost** in **Solution Explorer** and select **Add Reference**.</span></span> <span data-ttu-id="1171c-120">Seçin **System.ServiceModel** gelen **.NET** sekmesine ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="1171c-120">Select **System.ServiceModel** from the **.NET** tab and then choose **OK**.</span></span>

    > [!TIP]
    > <span data-ttu-id="1171c-121">Varsa **Çözüm Gezgini** pencere görünür, select değil **Çözüm Gezgini** gelen **görünümü** menüsü.</span><span class="sxs-lookup"><span data-stu-id="1171c-121">If the **Solution Explorer** window is not visible, select **Solution Explorer** from the **View** menu.</span></span>

3. <span data-ttu-id="1171c-122">Çift **Program.cs** veya **Module1.vb** içinde **Çözüm Gezgini** zaten açık değilse kod penceresinde açmak için.</span><span class="sxs-lookup"><span data-stu-id="1171c-122">Double-click **Program.cs** or **Module1.vb** in **Solution Explorer** to open it in the code window, if it's not already open.</span></span> <span data-ttu-id="1171c-123">Dosyasının en üstüne aşağıdaki deyimleri ekleyin:</span><span class="sxs-lookup"><span data-stu-id="1171c-123">Add the following statements at the top of the file:</span></span>

     [!code-csharp[CFX_SelfHost4#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#1)]
     [!code-vb[CFX_SelfHost4#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#1)]

4. <span data-ttu-id="1171c-124">Bir hizmet sözleşmesini uygulama ve tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="1171c-124">Define and implement a service contract.</span></span> <span data-ttu-id="1171c-125">Bu örnekte tanımlayan bir `HelloWorldService` giriş hizmete göre bir ileti döndürür.</span><span class="sxs-lookup"><span data-stu-id="1171c-125">This example defines a `HelloWorldService` that returns a message based on the input to the service.</span></span>

     [!code-csharp[CFX_SelfHost4#2](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#2)]
     [!code-vb[CFX_SelfHost4#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#2)]

    > [!NOTE]
    > <span data-ttu-id="1171c-126">Tanımlaması ve hizmet arabirimi hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir hizmet sözleşmesini tanımlama](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md) ve [nasıl yapılır: bir hizmet sözleşmesini uygulama](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md).</span><span class="sxs-lookup"><span data-stu-id="1171c-126">For more information about how to define and implement a service interface, see [How to: Define a Service Contract](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md) and [How to: Implement a Service Contract](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md).</span></span>

5. <span data-ttu-id="1171c-127">Üst kısmındaki `Main` yöntemi, bir örneğini oluşturmak <xref:System.Uri> sınıfı ile hizmet için temel adres.</span><span class="sxs-lookup"><span data-stu-id="1171c-127">At the top of the `Main` method, create an instance of the <xref:System.Uri> class with the base address for the service.</span></span>

     [!code-csharp[CFX_SelfHost4#3](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#3)]
     [!code-vb[CFX_SelfHost4#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#3)]

6. <span data-ttu-id="1171c-128">Bir örneğini oluşturmak <xref:System.ServiceModel.ServiceHost> geçirme sınıfı, bir <xref:System.Type> temsil eden Tekdüzen Kaynak Tanımlayıcısı (URI) için hizmet türü ve temel adresi <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Type%2CSystem.Uri%5B%5D%29>.</span><span class="sxs-lookup"><span data-stu-id="1171c-128">Create an instance of the <xref:System.ServiceModel.ServiceHost> class, passing a <xref:System.Type> that represents the service type and the base address Uniform Resource Identifier (URI) to the <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Type%2CSystem.Uri%5B%5D%29>.</span></span> <span data-ttu-id="1171c-129">Meta veri yayımlamayı etkinleştirme ve ardından arama <xref:System.ServiceModel.ICommunicationObject.Open%2A> metodunda <xref:System.ServiceModel.ServiceHost> hizmeti başlatmak ve iletileri almak için hazırlamak üzere.</span><span class="sxs-lookup"><span data-stu-id="1171c-129">Enable metadata publishing, and then call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method on the <xref:System.ServiceModel.ServiceHost> to initialize the service and prepare it to receive messages.</span></span>

     [!code-csharp[CFX_SelfHost4#4](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#4)]
     [!code-vb[CFX_SelfHost4#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#4)]

    > [!NOTE]
    > <span data-ttu-id="1171c-130">Bu örnek, varsayılan uç noktaları kullanır ve bu hizmet için herhangi bir yapılandırma dosyası gereklidir.</span><span class="sxs-lookup"><span data-stu-id="1171c-130">This example uses default endpoints, and no configuration file is required for this service.</span></span> <span data-ttu-id="1171c-131">Uç nokta yapılandırıldıysa, çalışma zamanı hizmeti tarafından uygulanan her bir hizmet sözleşmesi için her bir temel adres için bir uç nokta oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1171c-131">If no endpoints are configured, then the runtime creates one endpoint for each base address for each service contract implemented by the service.</span></span> <span data-ttu-id="1171c-132">Varsayılan uç noktaları hakkında daha fazla bilgi için bkz. [Basitleştirilmiş yapılandırma](../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="1171c-132">For more information about default endpoints, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>

7. <span data-ttu-id="1171c-133">Tuşuna **Ctrl**+**Shift**+**B** çözümü derlemek için.</span><span class="sxs-lookup"><span data-stu-id="1171c-133">Press **Ctrl**+**Shift**+**B** to build the solution.</span></span>

## <a name="test-the-service"></a><span data-ttu-id="1171c-134">Test hizmeti</span><span class="sxs-lookup"><span data-stu-id="1171c-134">Test the service</span></span>

1. <span data-ttu-id="1171c-135">Tuşuna **Ctrl**+**F5** hizmeti çalıştırmak için.</span><span class="sxs-lookup"><span data-stu-id="1171c-135">Press **Ctrl**+**F5** to run the service.</span></span>

2. <span data-ttu-id="1171c-136">Açık **WCF Test istemcisi**.</span><span class="sxs-lookup"><span data-stu-id="1171c-136">Open **WCF Test Client**.</span></span>

    > [!TIP]
    > <span data-ttu-id="1171c-137">Açmak için **WCF Test istemcisi**, Visual Studio için geliştirici komut istemi açın ve yürütme **WcfTestClient.exe**.</span><span class="sxs-lookup"><span data-stu-id="1171c-137">To open **WCF Test Client**, open Developer Command Prompt for Visual Studio and execute **WcfTestClient.exe**.</span></span>

3. <span data-ttu-id="1171c-138">Seçin **Hizmet Ekle** gelen **dosya** menüsü.</span><span class="sxs-lookup"><span data-stu-id="1171c-138">Select **Add Service** from the **File** menu.</span></span>

4. <span data-ttu-id="1171c-139">Tür `http://localhost:8080/hello` içine tıklayın ve adres kutusuna **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="1171c-139">Type `http://localhost:8080/hello` into the address box and click **OK**.</span></span>

    > [!TIP]
    > <span data-ttu-id="1171c-140">Hizmet çalışıyor; Aksi takdirde bu adımı başarısız olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="1171c-140">Make sure the service is running or else this step fails.</span></span> <span data-ttu-id="1171c-141">Temel adres kodundaki değiştirdiyseniz, değiştirilmiş temel adresini bu adımı kullanın.</span><span class="sxs-lookup"><span data-stu-id="1171c-141">If you have changed the base address in the code, then use the modified base address in this step.</span></span>

5. <span data-ttu-id="1171c-142">Çift **SayHello** altında **hizmet Projelerim** düğümü.</span><span class="sxs-lookup"><span data-stu-id="1171c-142">Double-click **SayHello** under the **My Service Projects** node.</span></span> <span data-ttu-id="1171c-143">İçine adınızı yazın **değer** sütununda **istek** listesinde ve tıklayın **Invoke**.</span><span class="sxs-lookup"><span data-stu-id="1171c-143">Type your name into the **Value** column in the **Request** list, and click **Invoke**.</span></span>

   <span data-ttu-id="1171c-144">Bir yanıt iletisi görünür **yanıt** listesi.</span><span class="sxs-lookup"><span data-stu-id="1171c-144">A reply message appears in the **Response** list.</span></span>

## <a name="example"></a><span data-ttu-id="1171c-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="1171c-145">Example</span></span>

<span data-ttu-id="1171c-146">Aşağıdaki örnek, oluşturur bir <xref:System.ServiceModel.ServiceHost> türünde bir hizmet ana bilgisayar nesnesine `HelloWorldService`ve ardından çağırır <xref:System.ServiceModel.ICommunicationObject.Open%2A> metodunda <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="1171c-146">The following example creates a <xref:System.ServiceModel.ServiceHost> object to host a service of type `HelloWorldService`, and then calls the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method on <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="1171c-147">Temel adres kodunda sağlanır, meta veri yayımlama etkin ve varsayılan uç noktaları kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1171c-147">A base address is provided in code, metadata publishing is enabled, and default endpoints are used.</span></span>

[!code-csharp[CFX_SelfHost4#5](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#5)]
[!code-vb[CFX_SelfHost4#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#5)]

## <a name="see-also"></a><span data-ttu-id="1171c-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1171c-148">See also</span></span>

- <xref:System.Uri>
- <xref:System.Configuration.ConfigurationManager.AppSettings%2A>
- <xref:System.Configuration.ConfigurationManager>
- [<span data-ttu-id="1171c-149">Nasıl yapılır: IIS'de WCF Hizmeti Barındırma</span><span class="sxs-lookup"><span data-stu-id="1171c-149">How to: Host a WCF Service in IIS</span></span>](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)
- [<span data-ttu-id="1171c-150">Kendini Barındırma</span><span class="sxs-lookup"><span data-stu-id="1171c-150">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)
- [<span data-ttu-id="1171c-151">Barındırma Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="1171c-151">Hosting Services</span></span>](../../../docs/framework/wcf/hosting-services.md)
- [<span data-ttu-id="1171c-152">Nasıl yapılır: Bir Hizmet Anlaşması Tanımlama</span><span class="sxs-lookup"><span data-stu-id="1171c-152">How to: Define a Service Contract</span></span>](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)
- [<span data-ttu-id="1171c-153">Nasıl yapılır: Bir Hizmet Anlaşmasını Uygulama</span><span class="sxs-lookup"><span data-stu-id="1171c-153">How to: Implement a Service Contract</span></span>](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)
- [<span data-ttu-id="1171c-154">ServiceModel Meta Veri Yardımcı Programı Aracı (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="1171c-154">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="1171c-155">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="1171c-155">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="1171c-156">Sistem Tarafından Sağlanan Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="1171c-156">System-Provided Bindings</span></span>](../../../docs/framework/wcf/system-provided-bindings.md)