---
title: 'Öğretici: Windows Communication Foundation istemcisi oluşturma'
ms.date: 03/19/2019
helpviewer_keywords:
- clients [WCF], running
- WCF clients [WCF], running
ms.assetid: a67884cc-1c4b-416b-8c96-5c954099f19f
ms.openlocfilehash: bfa4cbacc5a947cb51d577503b5e46f9a5f8de39
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184110"
---
# <a name="tutorial-create-a-windows-communication-foundation-client"></a><span data-ttu-id="ef334-102">Öğretici: Windows Communication Foundation istemcisi oluşturma</span><span class="sxs-lookup"><span data-stu-id="ef334-102">Tutorial: Create a Windows Communication Foundation client</span></span>

<span data-ttu-id="ef334-103">Bu öğretici, temel bir Windows Communication Foundation (WCF) uygulaması oluşturmak için gereken beş görevin dördüncüsünün açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ef334-103">This tutorial describes the fourth of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="ef334-104">Öğreticilere genel bir bakış için [Bkz. Öğretici: Windows Communication Foundation uygulamalarıyla başlayın.](getting-started-tutorial.md)</span><span class="sxs-lookup"><span data-stu-id="ef334-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="ef334-105">WCF uygulaması oluşturmak için bir sonraki görev, bir WCF hizmetinden meta veri alarak bir istemci oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="ef334-105">The next task for creating a WCF application is to create a client by retrieving metadata from a WCF service.</span></span> <span data-ttu-id="ef334-106">Hizmetin MEX bitiş noktasından meta verileri alan bir hizmet başvurusu eklemek için Visual Studio'yu kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="ef334-106">You use Visual Studio to add a service reference, which gets the metadata from the service’s MEX endpoint.</span></span> <span data-ttu-id="ef334-107">Visual Studio daha sonra seçtiğiniz dilde bir istemci proxy için yönetilen bir kaynak kodu dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ef334-107">Visual Studio then generates a managed source code file for a client proxy in the language you've chosen.</span></span> <span data-ttu-id="ef334-108">Ayrıca bir istemci yapılandırma dosyası *(App.config)* oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ef334-108">It also creates a client configuration file (*App.config*).</span></span> <span data-ttu-id="ef334-109">Bu dosya, istemci uygulamasının hizmete bitiş noktasında bağlanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="ef334-109">This file enables the client application to connect to the service at an endpoint.</span></span>

> [!NOTE]
> <span data-ttu-id="ef334-110">Visual Studio'daki bir sınıf kitaplığı projesinden wcf hizmeti çağırırsanız, proxy ve ilişkili yapılandırma dosyası oluşturmak için **Hizmet Başvurusu Ekle** özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="ef334-110">If you call a WCF service from a class library project in Visual Studio, use the **Add Service Reference** feature to automatically generate a proxy and associated configuration file.</span></span> <span data-ttu-id="ef334-111">Ancak, sınıf kitaplığı projeleri bu yapılandırma dosyasını kullanmadığından, sınıf kitaplığını çağıran yürütülebilir dosya için oluşturulan yapılandırma dosyasındaki ayarları *App.config* dosyasına eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ef334-111">However, because class library projects don't use this configuration file, you need to add the settings in the generated configuration file to the *App.config* file for the executable that calls the class library.</span></span>

> [!NOTE]
> <span data-ttu-id="ef334-112">Alternatif olarak, proxy sınıfı ve yapılandırma dosyasını oluşturmak için Visual Studio yerine [ServiceModel Metadata Utility aracını](#servicemodel-metadata-utility-tool) kullanın.</span><span class="sxs-lookup"><span data-stu-id="ef334-112">As an alternative, use the [ServiceModel Metadata Utility tool](#servicemodel-metadata-utility-tool) instead of Visual Studio to generate the proxy class and configuration file.</span></span>

<span data-ttu-id="ef334-113">İstemci uygulaması, hizmetle iletişim kurmak için oluşturulan proxy sınıfını kullanır.</span><span class="sxs-lookup"><span data-stu-id="ef334-113">The client application uses the generated proxy class to communicate with the service.</span></span> <span data-ttu-id="ef334-114">Bu yordam [Tutorial açıklanmıştır: Bir istemci kullanın.](how-to-use-a-wcf-client.md)</span><span class="sxs-lookup"><span data-stu-id="ef334-114">This procedure is described in [Tutorial: Use a client](how-to-use-a-wcf-client.md).</span></span>

<span data-ttu-id="ef334-115">Bu öğreticide şunların nasıl yapıldığını öğrenirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ef334-115">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="ef334-116">WCF istemcisi için bir konsol uygulaması projesi oluşturun ve yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="ef334-116">Create and configure a console app project for the WCF client.</span></span>
> - <span data-ttu-id="ef334-117">Proxy sınıfı ve yapılandırma dosyalarını oluşturmak için WCF hizmetine bir hizmet başvurusu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ef334-117">Add a service reference to the WCF service to generate the proxy class and configuration files.</span></span>

## <a name="create-a-windows-communication-foundation-client"></a><span data-ttu-id="ef334-118">Windows Communication Foundation istemcisi oluşturma</span><span class="sxs-lookup"><span data-stu-id="ef334-118">Create a Windows Communication Foundation client</span></span>

1. <span data-ttu-id="ef334-119">Visual Studio'da bir konsol uygulaması projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="ef334-119">Create a console app project in Visual Studio:</span></span>

    1. <span data-ttu-id="ef334-120">**Dosya** menüsünden**Proje/Çözüm** **Aç'ı** > seçin ve daha önce oluşturduğunuz **Başlangıç** çözümüne göz atın *(GettingStarted.sln).*</span><span class="sxs-lookup"><span data-stu-id="ef334-120">From the **File** menu, select **Open** > **Project/Solution** and browse to the **GettingStarted** solution you previously created (*GettingStarted.sln*).</span></span> <span data-ttu-id="ef334-121">**Aç**'ı seçin.</span><span class="sxs-lookup"><span data-stu-id="ef334-121">Select **Open**.</span></span>

    2. <span data-ttu-id="ef334-122">**Görünüm** menüsünden **Çözüm Gezgini'ni**seçin.</span><span class="sxs-lookup"><span data-stu-id="ef334-122">From the **View** menu, select **Solution Explorer**.</span></span>

    3. <span data-ttu-id="ef334-123">Çözüm **Gezgini** penceresinde, **Başlangıç** Çözümünü (üst düğüm) seçin ve ardından kısayol menüsünden**Yeni Proje** **Ekle'yi** > seçin.</span><span class="sxs-lookup"><span data-stu-id="ef334-123">In the **Solution Explorer** window, select the **GettingStarted** solution (top node), and then select **Add** > **New Project** from the shortcut menu.</span></span>

    4. <span data-ttu-id="ef334-124">Yeni **Proje Ekle** penceresinde, sol tarafta, **Visual C#** veya **Visual Basic**altında Windows **Masaüstü** kategorisini seçin.</span><span class="sxs-lookup"><span data-stu-id="ef334-124">In the **Add New Project** window, on the left side, select the **Windows Desktop** category under **Visual C#** or **Visual Basic**.</span></span>

    5. <span data-ttu-id="ef334-125">Konsol **Uygulaması (.NET Framework)** şablonunu seçin ve **Ad**için *GettingStartedClient'ı* girin.</span><span class="sxs-lookup"><span data-stu-id="ef334-125">Select the **Console App (.NET Framework)** template, and enter *GettingStartedClient* for the **Name**.</span></span> <span data-ttu-id="ef334-126">**Tamam'ı**seçin.</span><span class="sxs-lookup"><span data-stu-id="ef334-126">Select **OK**.</span></span>

2. <span data-ttu-id="ef334-127">**Derlemeye Başlangıç İstemci** projesinde <xref:System.ServiceModel> bir başvuru ekleyin:</span><span class="sxs-lookup"><span data-stu-id="ef334-127">Add a reference in the **GettingStartedClient** project to the <xref:System.ServiceModel> assembly:</span></span>

    1. <span data-ttu-id="ef334-128">Çözüm **Gezgini** penceresinde, **GettingStartedClient** projesinin altındaki **Başvurular** klasörünü seçin ve ardından kısayol menüsünden **Başvuru Ekle'yi** seçin.</span><span class="sxs-lookup"><span data-stu-id="ef334-128">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedClient** project, and then select **Add Reference** from the shortcut menu.</span></span>

    2. <span data-ttu-id="ef334-129">Başvuru **Ekle** penceresinde, pencerenin sol tarafındaki **Derlemeler** altında **Çerçeve'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="ef334-129">In the **Add Reference** window, under **Assemblies** on the left side of the window, select **Framework**.</span></span>

    3. <span data-ttu-id="ef334-130">**System.ServiceModel'i**bulun ve seçin ve ardından **Tamam'ı**seçin.</span><span class="sxs-lookup"><span data-stu-id="ef334-130">Find and select **System.ServiceModel**, and then choose **OK**.</span></span>

    4. <span data-ttu-id="ef334-131">**Tümünü Kaydet'i** > seçerek çözümü**kaydedin.**</span><span class="sxs-lookup"><span data-stu-id="ef334-131">Save the solution by selecting **File** > **Save All**.</span></span>

3. <span data-ttu-id="ef334-132">Hesap makinesi hizmetine bir hizmet başvurusu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="ef334-132">Add a service reference to the calculator service:</span></span>

   1. <span data-ttu-id="ef334-133">Çözüm **Gezgini** penceresinde, **GettingStartedClient** projesinin altındaki **Başvurular** klasörünü seçin ve ardından kısayol menüsünden **Hizmet Başvurusu Ekle'yi** seçin.</span><span class="sxs-lookup"><span data-stu-id="ef334-133">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedClient** project, and then select **Add Service Reference** from the shortcut menu.</span></span>

   2. <span data-ttu-id="ef334-134">Hizmet Başvurusu Ekle penceresinde **Keşfet'i**seçin. **Add Service Reference**</span><span class="sxs-lookup"><span data-stu-id="ef334-134">In the **Add Service Reference** window, select **Discover**.</span></span>

      <span data-ttu-id="ef334-135">CalculatorService hizmeti başlar ve Visual Studio bunu **Hizmetler** kutusunda görüntüler.</span><span class="sxs-lookup"><span data-stu-id="ef334-135">The CalculatorService service starts and Visual Studio displays it in the **Services** box.</span></span>

   3. <span data-ttu-id="ef334-136">Genişletmek ve hizmet tarafından uygulanan hizmet sözleşmelerini görüntülemek için **Hesap Makinesi Hizmetini** seçin.</span><span class="sxs-lookup"><span data-stu-id="ef334-136">Select **CalculatorService** to expand it and display the service contracts implemented by the service.</span></span> <span data-ttu-id="ef334-137">Varsayılan **Ad alanını** bırakın ve **Tamam'ı**seçin.</span><span class="sxs-lookup"><span data-stu-id="ef334-137">Leave the default **Namespace** and choose **OK**.</span></span>

      <span data-ttu-id="ef334-138">Visual **Studio, GettingStartedClient** projesinde **Bağlı Hizmetler** klasörüne yeni bir öğe ekler.</span><span class="sxs-lookup"><span data-stu-id="ef334-138">Visual Studio adds a new item under the **Connected Services** folder in the **GettingStartedClient** project.</span></span>

### <a name="servicemodel-metadata-utility-tool"></a><span data-ttu-id="ef334-139">ServiceModel Metadata Yardımcı araç</span><span class="sxs-lookup"><span data-stu-id="ef334-139">ServiceModel Metadata Utility tool</span></span>

<span data-ttu-id="ef334-140">Aşağıdaki örnekler, proxy sınıfı dosyasını oluşturmak için [ServiceModel Metadata Utility aracının (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) isteğe bağlı olarak nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ef334-140">The following examples show how to optionally use the [ServiceModel Metadata Utility tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy class file.</span></span> <span data-ttu-id="ef334-141">Bu araç proxy sınıf dosyası ve *App.config* dosyasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ef334-141">This tool generates the proxy class file and the *App.config* file.</span></span> <span data-ttu-id="ef334-142">Aşağıdaki örnekler, sırasıyla C# ve Visual Basic'te proxy'nin nasıl oluşturacağımı gösterir:</span><span class="sxs-lookup"><span data-stu-id="ef334-142">The following examples show how to generate the proxy in C# and Visual Basic, respectively:</span></span>

```shell
svcutil.exe /language:cs /out:generatedProxy.cs /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

```shell
svcutil.exe /language:vb /out:generatedProxy.vb /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

### <a name="client-configuration-file"></a><span data-ttu-id="ef334-143">İstemci yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="ef334-143">Client configuration file</span></span>

<span data-ttu-id="ef334-144">İstemciyi oluşturduktan sonra Visual Studio, **GettingStartedClient** projesinde aşağıdaki örneğe benzer olması gereken **App.config** yapılandırma dosyasını oluşturur:</span><span class="sxs-lookup"><span data-stu-id="ef334-144">After you've created the client, Visual Studio creates the **App.config** configuration file in the **GettingStartedClient** project, which should be similar to the following example:</span></span>

```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
        <startup>
            <!-- specifies the version of WCF to use-->
            <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6.1" />
        </startup>
        <system.serviceModel>
            <bindings>
                <!-- Uses wsHttpBinding-->
                <wsHttpBinding>
                    <binding name="WSHttpBinding_ICalculator" />
                </wsHttpBinding>
            </bindings>
            <client>
                <!-- specifies the endpoint to use when calling the service -->
                <endpoint address="http://localhost:8000/GettingStarted/CalculatorService"
                    binding="wsHttpBinding" bindingConfiguration="WSHttpBinding_ICalculator"
                    contract="ServiceReference1.ICalculator" name="WSHttpBinding_ICalculator">
                    <identity>
                        <dns value="localhost" />
                    </identity>
                </endpoint>
            </client>
        </system.serviceModel>
    </configuration>
```

<span data-ttu-id="ef334-145">System.serviceModel>bölümünde, [ \<bitiş noktası>](../configure-apps/file-schema/wcf/endpoint-element.md) öğesine dikkat edin. [ \<](../configure-apps/file-schema/wcf/system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="ef334-145">Under the [\<system.serviceModel>](../configure-apps/file-schema/wcf/system-servicemodel.md) section, notice the [\<endpoint>](../configure-apps/file-schema/wcf/endpoint-element.md) element.</span></span> <span data-ttu-id="ef334-146">\*\* &lt;Uç nokta&gt; \*\* öğesi, istemcinin hizmete erişmek için kullandığı bitiş noktasını aşağıdaki gibi tanımlar:</span><span class="sxs-lookup"><span data-stu-id="ef334-146">The **&lt;endpoint&gt;** element defines the endpoint that the client uses to access the service as follows:</span></span>

- <span data-ttu-id="ef334-147">Adres: `http://localhost:8000/GettingStarted/CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="ef334-147">Address: `http://localhost:8000/GettingStarted/CalculatorService`.</span></span> <span data-ttu-id="ef334-148">Bitiş noktasının adresi.</span><span class="sxs-lookup"><span data-stu-id="ef334-148">The address of the endpoint.</span></span>
- <span data-ttu-id="ef334-149">Hizmet sözleşmesi: `ServiceReference1.ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="ef334-149">Service contract: `ServiceReference1.ICalculator`.</span></span> <span data-ttu-id="ef334-150">Hizmet sözleşmesi, WCF istemcisi ile hizmet arasındaki iletişimi işler.</span><span class="sxs-lookup"><span data-stu-id="ef334-150">The service contract handles communication between the WCF client and the service.</span></span> <span data-ttu-id="ef334-151">Visual Studio, Hizmet Başvurusu **Ekle** işlevini kullandığınızda bu sözleşmeyi oluşturdu.</span><span class="sxs-lookup"><span data-stu-id="ef334-151">Visual Studio generated this contract when you used its **Add Service Reference** function.</span></span> <span data-ttu-id="ef334-152">Bu aslında GettingStartedLib projesinde tanımladığınız sözleşmenin bir kopyasıdır.</span><span class="sxs-lookup"><span data-stu-id="ef334-152">It's essentially a copy of the contract that you defined in the GettingStartedLib project.</span></span>
- <span data-ttu-id="ef334-153">Bağlama: <xref:System.ServiceModel.WSHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="ef334-153">Binding: <xref:System.ServiceModel.WSHttpBinding>.</span></span> <span data-ttu-id="ef334-154">Bağlama, HTTP'yi aktarım, birlikte çalışabilir güvenlik ve diğer yapılandırma ayrıntıları olarak belirtir.</span><span class="sxs-lookup"><span data-stu-id="ef334-154">The binding specifies HTTP as the transport, interoperable security, and other configuration details.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ef334-155">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="ef334-155">Next steps</span></span>

<span data-ttu-id="ef334-156">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="ef334-156">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="ef334-157">WCF istemcisi için bir konsol uygulaması projesi oluşturun ve yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="ef334-157">Create and configure a console app project for the WCF client.</span></span>
> - <span data-ttu-id="ef334-158">İstemci uygulaması için proxy sınıfı ve yapılandırma dosyaları oluşturmak için WCF hizmetine bir hizmet başvurusu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ef334-158">Add a service reference to the WCF service to generate the proxy class and configuration files for the client application.</span></span>

<span data-ttu-id="ef334-159">Oluşturulan istemciyi nasıl kullanacağınızı öğrenmek için bir sonraki öğreticiye ilerleyin.</span><span class="sxs-lookup"><span data-stu-id="ef334-159">Advance to the next tutorial to learn how to use the generated client.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ef334-160">Öğretici: WCF istemcisi kullanma</span><span class="sxs-lookup"><span data-stu-id="ef334-160">Tutorial: Use a WCF client</span></span>](how-to-use-a-wcf-client.md)
