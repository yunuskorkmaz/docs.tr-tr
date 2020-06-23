---
title: 'Nasıl yapılır: Yönetilen Bir Uygulamada Bir WCF Hizmeti Barındırma'
description: Şirket içinde barındırılan bir hizmet oluşturarak ve test ederek, yönetilen bir uygulama içinde bir WCF hizmetini nasıl barındıracağınızı öğrenin.
ms.date: 09/17/2018
dev_langs:
- csharp
- vb
ms.assetid: 5eb29db0-b6dc-4e77-8c68-0a62f79d743b
ms.openlocfilehash: 7d1d61b683f60a6c643d2a2f03d367a6ae6c6c15
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246174"
---
# <a name="how-to-host-a-wcf-service-in-a-managed-app"></a><span data-ttu-id="d9fcd-103">Nasıl yapılır: yönetilen bir uygulamada bir WCF hizmetini barındırma</span><span class="sxs-lookup"><span data-stu-id="d9fcd-103">How to: Host a WCF service in a managed app</span></span>

<span data-ttu-id="d9fcd-104">Yönetilen bir uygulama içinde bir hizmeti barındırmak için, hizmetin kodunu yönetilen uygulama kodu içine ekleyin, hizmet için bir uç nokta tanımlayın, yapılandırma yoluyla veya varsayılan uç noktaları kullanarak, bir örneği oluşturun <xref:System.ServiceModel.ServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="d9fcd-104">To host a service inside a managed application, embed the code for the service inside the managed application code, define an endpoint for the service either imperatively in code, declaratively through configuration, or using default endpoints, and then create an instance of <xref:System.ServiceModel.ServiceHost>.</span></span>

<span data-ttu-id="d9fcd-105">İleti almaya başlamak için üzerinde öğesini <xref:System.ServiceModel.ICommunicationObject.Open%2A> çağırın <xref:System.ServiceModel.ServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="d9fcd-105">To start receiving messages, call <xref:System.ServiceModel.ICommunicationObject.Open%2A> on <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="d9fcd-106">Bu, hizmet için dinleyiciyi oluşturur ve açar.</span><span class="sxs-lookup"><span data-stu-id="d9fcd-106">This creates and opens the listener for the service.</span></span> <span data-ttu-id="d9fcd-107">Bir hizmetin bu şekilde barındırılması, yönetilen uygulama barındırma işinin kendisini yaptığından, genellikle "kendiliğinden barındırma" olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="d9fcd-107">Hosting a service in this way is often referred to as "self-hosting" because the managed application is doing the hosting work itself.</span></span> <span data-ttu-id="d9fcd-108">Hizmeti kapatmak için üzerinde öğesini çağırın <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> <xref:System.ServiceModel.ServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="d9fcd-108">To close the service, call <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> on <xref:System.ServiceModel.ServiceHost>.</span></span>

<span data-ttu-id="d9fcd-109">Bir hizmet Ayrıca, yönetilen bir Windows hizmetinde, Internet Information Services (IIS) veya Windows Işlem etkinleştirme hizmeti 'nde (WAS) barındırılabilir.</span><span class="sxs-lookup"><span data-stu-id="d9fcd-109">A service can also be hosted in a managed Windows service, in Internet Information Services (IIS), or in Windows Process Activation Service (WAS).</span></span> <span data-ttu-id="d9fcd-110">Bir hizmet için barındırma seçenekleri hakkında daha fazla bilgi için bkz. [barındırma hizmetleri](hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="d9fcd-110">For more information about hosting options for a service, see [Hosting Services](hosting-services.md).</span></span>

<span data-ttu-id="d9fcd-111">Dağıtım için en az altyapıyı gerektirdiğinden, yönetilen bir uygulamada bir hizmetin barındırılması en esnek seçenektir.</span><span class="sxs-lookup"><span data-stu-id="d9fcd-111">Hosting a service in a managed application is the most flexible option because it requires the least infrastructure to deploy.</span></span> <span data-ttu-id="d9fcd-112">Yönetilen uygulamalarda barındırma hizmetleri hakkında daha fazla bilgi için bkz. [yönetilen bir uygulamada barındırma](./feature-details/hosting-in-a-managed-application.md).</span><span class="sxs-lookup"><span data-stu-id="d9fcd-112">For more information about hosting services in managed applications, see [Hosting in a Managed Application](./feature-details/hosting-in-a-managed-application.md).</span></span>

<span data-ttu-id="d9fcd-113">Aşağıdaki yordamda, bir konsol uygulamasında şirket içinde barındırılan bir hizmetin nasıl uygulanacağı gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d9fcd-113">The following procedure demonstrates how to implement a self-hosted service in a console application.</span></span>

## <a name="create-a-self-hosted-service"></a><span data-ttu-id="d9fcd-114">Şirket içinde barındırılan hizmet oluşturma</span><span class="sxs-lookup"><span data-stu-id="d9fcd-114">Create a self-hosted service</span></span>

1. <span data-ttu-id="d9fcd-115">Yeni bir konsol uygulaması oluşturun:</span><span class="sxs-lookup"><span data-stu-id="d9fcd-115">Create a new console application:</span></span>

   1. <span data-ttu-id="d9fcd-116">Visual Studio 'yu açın ve **New**  >  **Dosya** menüsünden Yeni**Proje** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="d9fcd-116">Open Visual Studio and select **New** > **Project** from the **File** menu.</span></span>

   2. <span data-ttu-id="d9fcd-117">**Yüklü şablonlar** listesinde, **Visual C#** veya **Visual Basic**seçin ve ardından **Windows Masaüstü**' nü seçin.</span><span class="sxs-lookup"><span data-stu-id="d9fcd-117">In the **Installed Templates** list, select **Visual C#** or **Visual Basic**, and then select **Windows Desktop**.</span></span>

   3. <span data-ttu-id="d9fcd-118">**Konsol uygulaması** şablonunu seçin.</span><span class="sxs-lookup"><span data-stu-id="d9fcd-118">Select the **Console App** template.</span></span> <span data-ttu-id="d9fcd-119">`SelfHost` **Ad** kutusuna yazın ve ardından **Tamam**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="d9fcd-119">Type `SelfHost` in the **Name** box and then choose **OK**.</span></span>

2. <span data-ttu-id="d9fcd-120">**Çözüm Gezgini** ' de **Selfhost** ' a sağ tıklayın ve **Başvuru Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="d9fcd-120">Right-click **SelfHost** in **Solution Explorer** and select **Add Reference**.</span></span> <span data-ttu-id="d9fcd-121">**.Net** sekmesinden **System. ServiceModel** ' i seçin ve ardından **Tamam**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="d9fcd-121">Select **System.ServiceModel** from the **.NET** tab and then choose **OK**.</span></span>

    > [!TIP]
    > <span data-ttu-id="d9fcd-122">**Çözüm Gezgini** penceresi görünmüyorsa, **Görünüm** menüsünden **Çözüm Gezgini** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="d9fcd-122">If the **Solution Explorer** window is not visible, select **Solution Explorer** from the **View** menu.</span></span>

3. <span data-ttu-id="d9fcd-123">Zaten açık değilse, kod penceresinde açmak için **Çözüm Gezgini** içinde **program.cs** veya **Module1. vb** öğesine çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d9fcd-123">Double-click **Program.cs** or **Module1.vb** in **Solution Explorer** to open it in the code window, if it's not already open.</span></span> <span data-ttu-id="d9fcd-124">Aşağıdaki deyimlerini dosyanın üst kısmına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="d9fcd-124">Add the following statements at the top of the file:</span></span>

     [!code-csharp[CFX_SelfHost4#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#1)]
     [!code-vb[CFX_SelfHost4#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#1)]

4. <span data-ttu-id="d9fcd-125">Hizmet sözleşmesi tanımlama ve uygulama.</span><span class="sxs-lookup"><span data-stu-id="d9fcd-125">Define and implement a service contract.</span></span> <span data-ttu-id="d9fcd-126">Bu örnek, `HelloWorldService` hizmete girişe dayalı bir ileti döndüren bir tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d9fcd-126">This example defines a `HelloWorldService` that returns a message based on the input to the service.</span></span>

     [!code-csharp[CFX_SelfHost4#2](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#2)]
     [!code-vb[CFX_SelfHost4#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#2)]

    > [!NOTE]
    > <span data-ttu-id="d9fcd-127">Bir hizmet arabirimini tanımlama ve uygulama hakkında daha fazla bilgi için bkz. [nasıl yapılır: hizmet sözleşmesi tanımlama](how-to-define-a-wcf-service-contract.md) ve [nasıl yapılır: hizmet sözleşmesi uygulama](how-to-implement-a-wcf-contract.md).</span><span class="sxs-lookup"><span data-stu-id="d9fcd-127">For more information about how to define and implement a service interface, see [How to: Define a Service Contract](how-to-define-a-wcf-service-contract.md) and [How to: Implement a Service Contract](how-to-implement-a-wcf-contract.md).</span></span>

5. <span data-ttu-id="d9fcd-128">Yönteminin en üstünde `Main` , <xref:System.Uri> hizmetin temel adresiyle sınıfının bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d9fcd-128">At the top of the `Main` method, create an instance of the <xref:System.Uri> class with the base address for the service.</span></span>

     [!code-csharp[CFX_SelfHost4#3](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#3)]
     [!code-vb[CFX_SelfHost4#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#3)]

6. <span data-ttu-id="d9fcd-129">Sınıfının bir örneğini oluşturun <xref:System.ServiceModel.ServiceHost> <xref:System.Type> ve hizmet türünü ve temel adres Tekdüzen Kaynak tanımlayıcısını (URI) temsil eder <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Type%2CSystem.Uri%5B%5D%29> .</span><span class="sxs-lookup"><span data-stu-id="d9fcd-129">Create an instance of the <xref:System.ServiceModel.ServiceHost> class, passing a <xref:System.Type> that represents the service type and the base address Uniform Resource Identifier (URI) to the <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Type%2CSystem.Uri%5B%5D%29>.</span></span> <span data-ttu-id="d9fcd-130">Meta veri yayımlamayı etkinleştirin ve sonra <xref:System.ServiceModel.ICommunicationObject.Open%2A> <xref:System.ServiceModel.ServiceHost> hizmeti başlatmak ve iletiyi almak üzere hazırlamak için üzerinde yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="d9fcd-130">Enable metadata publishing, and then call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method on the <xref:System.ServiceModel.ServiceHost> to initialize the service and prepare it to receive messages.</span></span>

     [!code-csharp[CFX_SelfHost4#4](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#4)]
     [!code-vb[CFX_SelfHost4#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#4)]

    > [!NOTE]
    > <span data-ttu-id="d9fcd-131">Bu örnek, varsayılan uç noktaları kullanır ve bu hizmet için hiçbir yapılandırma dosyası gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="d9fcd-131">This example uses default endpoints, and no configuration file is required for this service.</span></span> <span data-ttu-id="d9fcd-132">Hiçbir uç nokta yapılandırılmamışsa, çalışma zamanı, hizmet tarafından uygulanan her bir hizmet sözleşmesinin her bir temel adresi için bir uç nokta oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d9fcd-132">If no endpoints are configured, then the runtime creates one endpoint for each base address for each service contract implemented by the service.</span></span> <span data-ttu-id="d9fcd-133">Varsayılan uç noktalar hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](./samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="d9fcd-133">For more information about default endpoints, see [Simplified Configuration](simplified-configuration.md) and [Simplified Configuration for WCF Services](./samples/simplified-configuration-for-wcf-services.md).</span></span>

7. <span data-ttu-id="d9fcd-134">**Ctrl** + **Shift** + Çözümü derlemek için CTRL SHIFT**B** tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="d9fcd-134">Press **Ctrl**+**Shift**+**B** to build the solution.</span></span>

## <a name="test-the-service"></a><span data-ttu-id="d9fcd-135">Hizmeti test etme</span><span class="sxs-lookup"><span data-stu-id="d9fcd-135">Test the service</span></span>

1. <span data-ttu-id="d9fcd-136">**Ctrl** + Hizmeti çalıştırmak için CTRL**F5** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="d9fcd-136">Press **Ctrl**+**F5** to run the service.</span></span>

2. <span data-ttu-id="d9fcd-137">**WCF Test istemcisi**'ni açın.</span><span class="sxs-lookup"><span data-stu-id="d9fcd-137">Open **WCF Test Client**.</span></span>

    > [!TIP]
    > <span data-ttu-id="d9fcd-138">**WCF test istemcisini**açmak Için, Visual Studio için geliştirici komut istemi açın ve **WcfTestClient.exe**yürütün.</span><span class="sxs-lookup"><span data-stu-id="d9fcd-138">To open **WCF Test Client**, open Developer Command Prompt for Visual Studio and execute **WcfTestClient.exe**.</span></span>

3. <span data-ttu-id="d9fcd-139">**Dosya** menüsünden **Hizmet Ekle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="d9fcd-139">Select **Add Service** from the **File** menu.</span></span>

4. <span data-ttu-id="d9fcd-140">`http://localhost:8080/hello`Adres kutusuna yazın ve **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d9fcd-140">Type `http://localhost:8080/hello` into the address box and click **OK**.</span></span>

    > [!TIP]
    > <span data-ttu-id="d9fcd-141">Hizmetin çalıştığından emin olun, aksi takdirde bu adım başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="d9fcd-141">Make sure the service is running or else this step fails.</span></span> <span data-ttu-id="d9fcd-142">Koddaki temel adresi değiştirdiyseniz, bu adımda değiştirilen temel adresi kullanın.</span><span class="sxs-lookup"><span data-stu-id="d9fcd-142">If you have changed the base address in the code, then use the modified base address in this step.</span></span>

5. <span data-ttu-id="d9fcd-143">**Hizmet projeleri** düğümünün altında **SayHello** ' ya çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d9fcd-143">Double-click **SayHello** under the **My Service Projects** node.</span></span> <span data-ttu-id="d9fcd-144">**İstek** listesindeki **değer** sütununa adınızı yazın ve **çağır**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d9fcd-144">Type your name into the **Value** column in the **Request** list, and click **Invoke**.</span></span>

   <span data-ttu-id="d9fcd-145">**Yanıt** listesinde bir yanıt iletisi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d9fcd-145">A reply message appears in the **Response** list.</span></span>

## <a name="example"></a><span data-ttu-id="d9fcd-146">Örnek</span><span class="sxs-lookup"><span data-stu-id="d9fcd-146">Example</span></span>

<span data-ttu-id="d9fcd-147">Aşağıdaki örnek <xref:System.ServiceModel.ServiceHost> , türünde bir hizmeti barındırmak için bir nesnesi oluşturur `HelloWorldService` ve sonra <xref:System.ServiceModel.ICommunicationObject.Open%2A> yöntemi ' de çağırır <xref:System.ServiceModel.ServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="d9fcd-147">The following example creates a <xref:System.ServiceModel.ServiceHost> object to host a service of type `HelloWorldService`, and then calls the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method on <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="d9fcd-148">Kodda bir temel adres sağlanır, meta veri yayımlama etkindir ve varsayılan uç noktalar kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d9fcd-148">A base address is provided in code, metadata publishing is enabled, and default endpoints are used.</span></span>

[!code-csharp[CFX_SelfHost4#5](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#5)]
[!code-vb[CFX_SelfHost4#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#5)]

## <a name="see-also"></a><span data-ttu-id="d9fcd-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d9fcd-149">See also</span></span>

- <xref:System.Uri>
- <xref:System.Configuration.ConfigurationManager.AppSettings%2A>
- <xref:System.Configuration.ConfigurationManager>
- [<span data-ttu-id="d9fcd-150">Nasıl yapılır: IIS'de WCF Hizmeti Barındırma</span><span class="sxs-lookup"><span data-stu-id="d9fcd-150">How to: Host a WCF Service in IIS</span></span>](./feature-details/how-to-host-a-wcf-service-in-iis.md)
- [<span data-ttu-id="d9fcd-151">Kendini Barındırma</span><span class="sxs-lookup"><span data-stu-id="d9fcd-151">Self-Host</span></span>](./samples/self-host.md)
- [<span data-ttu-id="d9fcd-152">Barındırma Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="d9fcd-152">Hosting Services</span></span>](hosting-services.md)
- [<span data-ttu-id="d9fcd-153">Nasıl yapılır: Bir Hizmet Anlaşması Tanımlama</span><span class="sxs-lookup"><span data-stu-id="d9fcd-153">How to: Define a Service Contract</span></span>](how-to-define-a-wcf-service-contract.md)
- [<span data-ttu-id="d9fcd-154">Nasıl yapılır: Bir Hizmet Anlaşmasını Uygulama</span><span class="sxs-lookup"><span data-stu-id="d9fcd-154">How to: Implement a Service Contract</span></span>](how-to-implement-a-wcf-contract.md)
- [<span data-ttu-id="d9fcd-155">ServiceModel Meta Veri Yardımcı Programracı (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="d9fcd-155">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="d9fcd-156">Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma</span><span class="sxs-lookup"><span data-stu-id="d9fcd-156">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="d9fcd-157">Sistem tarafından sağlanmış bağlamalar</span><span class="sxs-lookup"><span data-stu-id="d9fcd-157">System-Provided Bindings</span></span>](system-provided-bindings.md)
