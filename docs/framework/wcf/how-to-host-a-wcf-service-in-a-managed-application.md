---
title: 'Nasıl yapılır: Yönetilen Bir Uygulamada Bir WCF Hizmeti Barındırma'
ms.date: 09/17/2018
dev_langs:
- csharp
- vb
ms.assetid: 5eb29db0-b6dc-4e77-8c68-0a62f79d743b
ms.openlocfilehash: e3adcad6ba70aa64b797325cd45a043301d7e680
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320971"
---
# <a name="how-to-host-a-wcf-service-in-a-managed-app"></a><span data-ttu-id="f0edb-102">Nasıl yapılır: yönetilen bir uygulamada bir WCF hizmetini barındırma</span><span class="sxs-lookup"><span data-stu-id="f0edb-102">How to: Host a WCF service in a managed app</span></span>

<span data-ttu-id="f0edb-103">Yönetilen bir uygulama içinde bir hizmeti barındırmak için, hizmetin kodunu yönetilen uygulama kodu içine ekleyin, hizmet için bir uç nokta tanımlayın, yapılandırma yoluyla veya varsayılan uç noktaları kullanarak bir <xref:System.ServiceModel.ServiceHost>örneği oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f0edb-103">To host a service inside a managed application, embed the code for the service inside the managed application code, define an endpoint for the service either imperatively in code, declaratively through configuration, or using default endpoints, and then create an instance of <xref:System.ServiceModel.ServiceHost>.</span></span>

<span data-ttu-id="f0edb-104">İleti almaya başlamak için <xref:System.ServiceModel.ServiceHost><xref:System.ServiceModel.ICommunicationObject.Open%2A> çağırın.</span><span class="sxs-lookup"><span data-stu-id="f0edb-104">To start receiving messages, call <xref:System.ServiceModel.ICommunicationObject.Open%2A> on <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="f0edb-105">Bu, hizmet için dinleyiciyi oluşturur ve açar.</span><span class="sxs-lookup"><span data-stu-id="f0edb-105">This creates and opens the listener for the service.</span></span> <span data-ttu-id="f0edb-106">Bir hizmetin bu şekilde barındırılması, yönetilen uygulama barındırma işinin kendisini yaptığından, genellikle "kendiliğinden barındırma" olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="f0edb-106">Hosting a service in this way is often referred to as "self-hosting" because the managed application is doing the hosting work itself.</span></span> <span data-ttu-id="f0edb-107">Hizmeti kapatmak için <xref:System.ServiceModel.ServiceHost><xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> çağırın.</span><span class="sxs-lookup"><span data-stu-id="f0edb-107">To close the service, call <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> on <xref:System.ServiceModel.ServiceHost>.</span></span>

<span data-ttu-id="f0edb-108">Bir hizmet Ayrıca, yönetilen bir Windows hizmetinde, Internet Information Services (IIS) veya Windows Işlem etkinleştirme hizmeti 'nde (WAS) barındırılabilir.</span><span class="sxs-lookup"><span data-stu-id="f0edb-108">A service can also be hosted in a managed Windows service, in Internet Information Services (IIS), or in Windows Process Activation Service (WAS).</span></span> <span data-ttu-id="f0edb-109">Bir hizmet için barındırma seçenekleri hakkında daha fazla bilgi için bkz. [barındırma hizmetleri](hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="f0edb-109">For more information about hosting options for a service, see [Hosting Services](hosting-services.md).</span></span>

<span data-ttu-id="f0edb-110">Dağıtım için en az altyapıyı gerektirdiğinden, yönetilen bir uygulamada bir hizmetin barındırılması en esnek seçenektir.</span><span class="sxs-lookup"><span data-stu-id="f0edb-110">Hosting a service in a managed application is the most flexible option because it requires the least infrastructure to deploy.</span></span> <span data-ttu-id="f0edb-111">Yönetilen uygulamalarda barındırma hizmetleri hakkında daha fazla bilgi için bkz. [yönetilen bir uygulamada barındırma](./feature-details/hosting-in-a-managed-application.md).</span><span class="sxs-lookup"><span data-stu-id="f0edb-111">For more information about hosting services in managed applications, see [Hosting in a Managed Application](./feature-details/hosting-in-a-managed-application.md).</span></span>

<span data-ttu-id="f0edb-112">Aşağıdaki yordamda, bir konsol uygulamasında şirket içinde barındırılan bir hizmetin nasıl uygulanacağı gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f0edb-112">The following procedure demonstrates how to implement a self-hosted service in a console application.</span></span>

## <a name="create-a-self-hosted-service"></a><span data-ttu-id="f0edb-113">Şirket içinde barındırılan hizmet oluşturma</span><span class="sxs-lookup"><span data-stu-id="f0edb-113">Create a self-hosted service</span></span>

1. <span data-ttu-id="f0edb-114">Yeni bir konsol uygulaması oluşturun:</span><span class="sxs-lookup"><span data-stu-id="f0edb-114">Create a new console application:</span></span>

   1. <span data-ttu-id="f0edb-115">Visual Studio 'Yu açın ve **Dosya** menüsünden **Yeni** > **Proje** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="f0edb-115">Open Visual Studio and select **New** > **Project** from the **File** menu.</span></span>

   2. <span data-ttu-id="f0edb-116">**Yüklü şablonlar** listesinde, **görsel C#**  veya **Visual Basic**' yi seçin ve ardından **Windows Masaüstü**' nü seçin.</span><span class="sxs-lookup"><span data-stu-id="f0edb-116">In the **Installed Templates** list, select **Visual C#** or **Visual Basic**, and then select **Windows Desktop**.</span></span>

   3. <span data-ttu-id="f0edb-117">**Konsol uygulaması** şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="f0edb-117">Select the **Console App** template.</span></span> <span data-ttu-id="f0edb-118">**Ad** kutusuna `SelfHost` yazın ve ardından **Tamam**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="f0edb-118">Type `SelfHost` in the **Name** box and then choose **OK**.</span></span>

2. <span data-ttu-id="f0edb-119">**Çözüm Gezgini** ' de **Selfhost** ' a sağ tıklayın ve **Başvuru Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="f0edb-119">Right-click **SelfHost** in **Solution Explorer** and select **Add Reference**.</span></span> <span data-ttu-id="f0edb-120">**.Net** sekmesinden **System. ServiceModel** ' i seçin ve ardından **Tamam**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="f0edb-120">Select **System.ServiceModel** from the **.NET** tab and then choose **OK**.</span></span>

    > [!TIP]
    > <span data-ttu-id="f0edb-121">**Çözüm Gezgini** penceresi görünmüyorsa, **Görünüm** menüsünden **Çözüm Gezgini** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="f0edb-121">If the **Solution Explorer** window is not visible, select **Solution Explorer** from the **View** menu.</span></span>

3. <span data-ttu-id="f0edb-122">Zaten açık değilse, kod penceresinde açmak için **Çözüm Gezgini** içinde **program.cs** veya **Module1. vb** öğesine çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f0edb-122">Double-click **Program.cs** or **Module1.vb** in **Solution Explorer** to open it in the code window, if it's not already open.</span></span> <span data-ttu-id="f0edb-123">Aşağıdaki deyimlerini dosyanın üst kısmına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f0edb-123">Add the following statements at the top of the file:</span></span>

     [!code-csharp[CFX_SelfHost4#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#1)]
     [!code-vb[CFX_SelfHost4#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#1)]

4. <span data-ttu-id="f0edb-124">Hizmet sözleşmesi tanımlama ve uygulama.</span><span class="sxs-lookup"><span data-stu-id="f0edb-124">Define and implement a service contract.</span></span> <span data-ttu-id="f0edb-125">Bu örnek, hizmete girişe dayalı bir ileti döndüren bir `HelloWorldService` tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f0edb-125">This example defines a `HelloWorldService` that returns a message based on the input to the service.</span></span>

     [!code-csharp[CFX_SelfHost4#2](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#2)]
     [!code-vb[CFX_SelfHost4#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#2)]

    > [!NOTE]
    > <span data-ttu-id="f0edb-126">Bir hizmet arabirimini tanımlama ve uygulama hakkında daha fazla bilgi için bkz. [nasıl yapılır: hizmet sözleşmesi tanımlama](how-to-define-a-wcf-service-contract.md) ve [nasıl yapılır: hizmet sözleşmesi uygulama](how-to-implement-a-wcf-contract.md).</span><span class="sxs-lookup"><span data-stu-id="f0edb-126">For more information about how to define and implement a service interface, see [How to: Define a Service Contract](how-to-define-a-wcf-service-contract.md) and [How to: Implement a Service Contract](how-to-implement-a-wcf-contract.md).</span></span>

5. <span data-ttu-id="f0edb-127">`Main` yönteminin en üstünde, hizmetin temel adresiyle <xref:System.Uri> sınıfının bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f0edb-127">At the top of the `Main` method, create an instance of the <xref:System.Uri> class with the base address for the service.</span></span>

     [!code-csharp[CFX_SelfHost4#3](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#3)]
     [!code-vb[CFX_SelfHost4#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#3)]

6. <span data-ttu-id="f0edb-128">Hizmet türünü ve temel adres Tekdüzen Kaynak tanımlayıcısı 'nı (URI) <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Type%2CSystem.Uri%5B%5D%29>temsil eden bir <xref:System.Type> geçirerek <xref:System.ServiceModel.ServiceHost> sınıfının bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f0edb-128">Create an instance of the <xref:System.ServiceModel.ServiceHost> class, passing a <xref:System.Type> that represents the service type and the base address Uniform Resource Identifier (URI) to the <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Type%2CSystem.Uri%5B%5D%29>.</span></span> <span data-ttu-id="f0edb-129">Meta veri yayımlamayı etkinleştirin ve sonra <xref:System.ServiceModel.ServiceHost> <xref:System.ServiceModel.ICommunicationObject.Open%2A> yöntemini çağırıp hizmeti başlatın ve iletiyi almak için hazırlayın.</span><span class="sxs-lookup"><span data-stu-id="f0edb-129">Enable metadata publishing, and then call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method on the <xref:System.ServiceModel.ServiceHost> to initialize the service and prepare it to receive messages.</span></span>

     [!code-csharp[CFX_SelfHost4#4](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#4)]
     [!code-vb[CFX_SelfHost4#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#4)]

    > [!NOTE]
    > <span data-ttu-id="f0edb-130">Bu örnek, varsayılan uç noktaları kullanır ve bu hizmet için hiçbir yapılandırma dosyası gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="f0edb-130">This example uses default endpoints, and no configuration file is required for this service.</span></span> <span data-ttu-id="f0edb-131">Hiçbir uç nokta yapılandırılmamışsa, çalışma zamanı, hizmet tarafından uygulanan her bir hizmet sözleşmesinin her bir temel adresi için bir uç nokta oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f0edb-131">If no endpoints are configured, then the runtime creates one endpoint for each base address for each service contract implemented by the service.</span></span> <span data-ttu-id="f0edb-132">Varsayılan uç noktalar hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](./samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="f0edb-132">For more information about default endpoints, see [Simplified Configuration](simplified-configuration.md) and [Simplified Configuration for WCF Services](./samples/simplified-configuration-for-wcf-services.md).</span></span>

7. <span data-ttu-id="f0edb-133">Çözümü derlemek için **Ctrl**+**SHIFT**+**B** tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="f0edb-133">Press **Ctrl**+**Shift**+**B** to build the solution.</span></span>

## <a name="test-the-service"></a><span data-ttu-id="f0edb-134">Hizmeti test etme</span><span class="sxs-lookup"><span data-stu-id="f0edb-134">Test the service</span></span>

1. <span data-ttu-id="f0edb-135">Hizmeti çalıştırmak için **Ctrl**+**F5** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="f0edb-135">Press **Ctrl**+**F5** to run the service.</span></span>

2. <span data-ttu-id="f0edb-136">**WCF Test istemcisi**'ni açın.</span><span class="sxs-lookup"><span data-stu-id="f0edb-136">Open **WCF Test Client**.</span></span>

    > [!TIP]
    > <span data-ttu-id="f0edb-137">**WCF test istemcisini**açmak Için, Visual Studio için geliştirici komut istemi açın ve **WcfTestClient. exe**dosyasını yürütün.</span><span class="sxs-lookup"><span data-stu-id="f0edb-137">To open **WCF Test Client**, open Developer Command Prompt for Visual Studio and execute **WcfTestClient.exe**.</span></span>

3. <span data-ttu-id="f0edb-138">**Dosya** menüsünden **Hizmet Ekle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="f0edb-138">Select **Add Service** from the **File** menu.</span></span>

4. <span data-ttu-id="f0edb-139">Adres kutusuna `http://localhost:8080/hello` yazın ve **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f0edb-139">Type `http://localhost:8080/hello` into the address box and click **OK**.</span></span>

    > [!TIP]
    > <span data-ttu-id="f0edb-140">Hizmetin çalıştığından emin olun, aksi takdirde bu adım başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="f0edb-140">Make sure the service is running or else this step fails.</span></span> <span data-ttu-id="f0edb-141">Koddaki temel adresi değiştirdiyseniz, bu adımda değiştirilen temel adresi kullanın.</span><span class="sxs-lookup"><span data-stu-id="f0edb-141">If you have changed the base address in the code, then use the modified base address in this step.</span></span>

5. <span data-ttu-id="f0edb-142">**Hizmet projeleri** düğümünün altında **SayHello** ' ya çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f0edb-142">Double-click **SayHello** under the **My Service Projects** node.</span></span> <span data-ttu-id="f0edb-143">**İstek** listesindeki **değer** sütununa adınızı yazın ve **çağır**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f0edb-143">Type your name into the **Value** column in the **Request** list, and click **Invoke**.</span></span>

   <span data-ttu-id="f0edb-144">**Yanıt** listesinde bir yanıt iletisi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="f0edb-144">A reply message appears in the **Response** list.</span></span>

## <a name="example"></a><span data-ttu-id="f0edb-145">Örnek</span><span class="sxs-lookup"><span data-stu-id="f0edb-145">Example</span></span>

<span data-ttu-id="f0edb-146">Aşağıdaki örnek, `HelloWorldService`türünde bir hizmeti barındırmak için bir <xref:System.ServiceModel.ServiceHost> nesnesi oluşturur ve sonra <xref:System.ServiceModel.ServiceHost>üzerinde <xref:System.ServiceModel.ICommunicationObject.Open%2A> yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="f0edb-146">The following example creates a <xref:System.ServiceModel.ServiceHost> object to host a service of type `HelloWorldService`, and then calls the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method on <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="f0edb-147">Kodda bir temel adres sağlanır, meta veri yayımlama etkindir ve varsayılan uç noktalar kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f0edb-147">A base address is provided in code, metadata publishing is enabled, and default endpoints are used.</span></span>

[!code-csharp[CFX_SelfHost4#5](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#5)]
[!code-vb[CFX_SelfHost4#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#5)]

## <a name="see-also"></a><span data-ttu-id="f0edb-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f0edb-148">See also</span></span>

- <xref:System.Uri>
- <xref:System.Configuration.ConfigurationManager.AppSettings%2A>
- <xref:System.Configuration.ConfigurationManager>
- [<span data-ttu-id="f0edb-149">Nasıl yapılır: IIS'de WCF Hizmeti Barındırma</span><span class="sxs-lookup"><span data-stu-id="f0edb-149">How to: Host a WCF Service in IIS</span></span>](./feature-details/how-to-host-a-wcf-service-in-iis.md)
- [<span data-ttu-id="f0edb-150">Kendini Barındırma</span><span class="sxs-lookup"><span data-stu-id="f0edb-150">Self-Host</span></span>](./samples/self-host.md)
- [<span data-ttu-id="f0edb-151">Barındırma Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="f0edb-151">Hosting Services</span></span>](hosting-services.md)
- [<span data-ttu-id="f0edb-152">Nasıl yapılır: Bir Hizmet Anlaşması Tanımlama</span><span class="sxs-lookup"><span data-stu-id="f0edb-152">How to: Define a Service Contract</span></span>](how-to-define-a-wcf-service-contract.md)
- [<span data-ttu-id="f0edb-153">Nasıl yapılır: Bir Hizmet Anlaşmasını Uygulama</span><span class="sxs-lookup"><span data-stu-id="f0edb-153">How to: Implement a Service Contract</span></span>](how-to-implement-a-wcf-contract.md)
- [<span data-ttu-id="f0edb-154">ServiceModel Meta Veri Yardımcı Programı Aracı (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="f0edb-154">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="f0edb-155">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="f0edb-155">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="f0edb-156">Sistem Tarafından Sağlanan Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="f0edb-156">System-Provided Bindings</span></span>](system-provided-bindings.md)
