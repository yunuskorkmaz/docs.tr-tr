---
title: 'Öğretici: Windows Communication Foundation istemcisi oluşturma'
ms.date: 03/19/2019
helpviewer_keywords:
- clients [WCF], running
- WCF clients [WCF], running
ms.assetid: a67884cc-1c4b-416b-8c96-5c954099f19f
ms.openlocfilehash: ddb5167c7f71a263377fb465ec44ee21057fbf4a
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928900"
---
# <a name="tutorial-create-a-windows-communication-foundation-client"></a><span data-ttu-id="83f36-102">Öğretici: Windows Communication Foundation istemcisi oluşturma</span><span class="sxs-lookup"><span data-stu-id="83f36-102">Tutorial: Create a Windows Communication Foundation client</span></span>

<span data-ttu-id="83f36-103">Bu öğreticide, temel bir Windows Communication Foundation (WCF) uygulaması oluşturmak için gereken dördüncü beş görev açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="83f36-103">This tutorial describes the fourth of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="83f36-104">Öğreticilere genel bakış için bkz [. Öğretici: Windows Communication Foundation uygulamaları](getting-started-tutorial.md)ile çalışmaya başlayın.</span><span class="sxs-lookup"><span data-stu-id="83f36-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="83f36-105">WCF uygulaması oluşturmaya yönelik sonraki görev, bir WCF hizmetinden meta verileri alarak istemci oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="83f36-105">The next task for creating a WCF application is to create a client by retrieving metadata from a WCF service.</span></span> <span data-ttu-id="83f36-106">Hizmetin MEX uç noktasından meta verileri alan bir hizmet başvurusu eklemek için Visual Studio 'Yu kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="83f36-106">You use Visual Studio to add a service reference, which gets the metadata from the service’s MEX endpoint.</span></span> <span data-ttu-id="83f36-107">Daha sonra Visual Studio, seçtiğiniz dilde istemci proxy 'si için bir yönetilen kaynak kodu dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="83f36-107">Visual Studio then generates a managed source code file for a client proxy in the language you've chosen.</span></span> <span data-ttu-id="83f36-108">Ayrıca, bir istemci yapılandırma dosyası (*app. config*) oluşturur.</span><span class="sxs-lookup"><span data-stu-id="83f36-108">It also creates a client configuration file (*App.config*).</span></span> <span data-ttu-id="83f36-109">Bu dosya, istemci uygulamasının bir uç noktada hizmete bağlanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="83f36-109">This file enables the client application to connect to the service at an endpoint.</span></span> 

> [!NOTE]
> <span data-ttu-id="83f36-110">Visual Studio 'da bir sınıf kitaplığı projesinden bir WCF hizmeti çağırırsanız, otomatik olarak bir proxy ve ilişkili yapılandırma dosyası oluşturmak için **hizmet başvurusu Ekle** özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="83f36-110">If you call a WCF service from a class library project in Visual Studio, use the **Add Service Reference** feature to automatically generate a proxy and associated configuration file.</span></span> <span data-ttu-id="83f36-111">Ancak, sınıf kitaplığı projeleri bu yapılandırma dosyasını kullanmadığından, oluşturulan yapılandırma dosyasındaki ayarları, sınıf kitaplığını çağıran yürütülebilir dosya için *app. config* dosyasına eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="83f36-111">However, because class library projects don't use this configuration file, you need to add the settings in the generated configuration file to the *App.config* file for the executable that calls the class library.</span></span>

> [!NOTE]
> <span data-ttu-id="83f36-112">Alternatif olarak, proxy sınıfını ve yapılandırma dosyasını oluşturmak için Visual Studio yerine [ServiceModel meta veri yardımcı programı aracını](#servicemodel-metadata-utility-tool) kullanın.</span><span class="sxs-lookup"><span data-stu-id="83f36-112">As an alternative, use the [ServiceModel Metadata Utility tool](#servicemodel-metadata-utility-tool) instead of Visual Studio to generate the proxy class and configuration file.</span></span>

<span data-ttu-id="83f36-113">İstemci uygulaması, hizmetle iletişim kurmak için oluşturulan proxy sınıfını kullanır.</span><span class="sxs-lookup"><span data-stu-id="83f36-113">The client application uses the generated proxy class to communicate with the service.</span></span> <span data-ttu-id="83f36-114">Bu yordam öğretici 'de [açıklanmaktadır: İstemci](how-to-use-a-wcf-client.md)kullanın.</span><span class="sxs-lookup"><span data-stu-id="83f36-114">This procedure is described in [Tutorial: Use a client](how-to-use-a-wcf-client.md).</span></span>

<span data-ttu-id="83f36-115">Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="83f36-115">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="83f36-116">WCF istemcisi için bir konsol uygulaması projesi oluşturun ve yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="83f36-116">Create and configure a console app project for the WCF client.</span></span>
> - <span data-ttu-id="83f36-117">Proxy sınıfı ve yapılandırma dosyalarını oluşturmak için WCF hizmetine bir hizmet başvurusu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="83f36-117">Add a service reference to the WCF service to generate the proxy class and configuration files.</span></span>

## <a name="create-a-windows-communication-foundation-client"></a><span data-ttu-id="83f36-118">Windows Communication Foundation istemcisi oluşturma</span><span class="sxs-lookup"><span data-stu-id="83f36-118">Create a Windows Communication Foundation client</span></span>

1. <span data-ttu-id="83f36-119">Visual Studio 'da bir konsol uygulaması projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="83f36-119">Create a console app project in Visual Studio:</span></span> 

    1. <span data-ttu-id="83f36-120">**Dosya** menüsünde**Proje/çözüm** **Aç** > ' ı seçin ve daha önce oluşturduğunuz **gettingstarted** çözümüne (*gettingstarted. sln*) gidin.</span><span class="sxs-lookup"><span data-stu-id="83f36-120">From the **File** menu, select **Open** > **Project/Solution** and browse to the **GettingStarted** solution you previously created (*GettingStarted.sln*).</span></span> <span data-ttu-id="83f36-121">**Aç**'ı seçin.</span><span class="sxs-lookup"><span data-stu-id="83f36-121">Select **Open**.</span></span>

    2. <span data-ttu-id="83f36-122">**Görünüm** menüsünden **Çözüm Gezgini**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="83f36-122">From the **View** menu, select **Solution Explorer**.</span></span>

    3. <span data-ttu-id="83f36-123">**Çözüm Gezgini** penceresinde, **gettingstarted** çözümünü (üst düğüm) seçin ve sonra kısayol menüsünden**Yeni proje** **Ekle** > ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="83f36-123">In the **Solution Explorer** window, select the **GettingStarted** solution (top node), and then select **Add** > **New Project** from the shortcut menu.</span></span> 
    
    4. <span data-ttu-id="83f36-124">**Yeni Proje Ekle** penceresinde, sol taraftaki **Visual C#**  veya **Visual Basic**altında **Windows Masaüstü** kategorisini seçin.</span><span class="sxs-lookup"><span data-stu-id="83f36-124">In the **Add New Project** window, on the left side, select the **Windows Desktop** category under **Visual C#** or **Visual Basic**.</span></span> 

    5. <span data-ttu-id="83f36-125">**Konsol uygulaması (.NET Framework)** şablonunu seçin ve **ad**Için *GettingStartedClient* yazın.</span><span class="sxs-lookup"><span data-stu-id="83f36-125">Select the **Console App (.NET Framework)** template, and enter *GettingStartedClient* for the **Name**.</span></span> <span data-ttu-id="83f36-126">**Tamam**’ı seçin.</span><span class="sxs-lookup"><span data-stu-id="83f36-126">Select **OK**.</span></span>

2. <span data-ttu-id="83f36-127">**GettingStartedClient** projesinde <xref:System.ServiceModel> derlemeye bir başvuru ekleyin:</span><span class="sxs-lookup"><span data-stu-id="83f36-127">Add a reference in the **GettingStartedClient** project to the <xref:System.ServiceModel> assembly:</span></span> 

    1. <span data-ttu-id="83f36-128">**Çözüm Gezgini** penceresinde, **GettingStartedClient** projesi altındaki **Başvurular** klasörünü seçin ve kısayol menüsünden **Başvuru Ekle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="83f36-128">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedClient** project, and then select **Add Reference** from the shortcut menu.</span></span> 

    2. <span data-ttu-id="83f36-129">**Başvuru Ekle** penceresinde pencerenin sol tarafındaki **derlemeler** altında **Framework**' ü seçin.</span><span class="sxs-lookup"><span data-stu-id="83f36-129">In the **Add Reference** window, under **Assemblies** on the left side of the window, select **Framework**.</span></span>
    
    3. <span data-ttu-id="83f36-130">**System. ServiceModel**bulun ve seçin ve ardından **Tamam**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="83f36-130">Find and select **System.ServiceModel**, and then choose **OK**.</span></span> 

    4. <span data-ttu-id="83f36-131">**Dosya** > **Tümünü Kaydet**' i seçerek çözümü kaydedin.</span><span class="sxs-lookup"><span data-stu-id="83f36-131">Save the solution by selecting **File** > **Save All**.</span></span>

3. <span data-ttu-id="83f36-132">Hesaplayıcı hizmetine bir hizmet başvurusu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="83f36-132">Add a service reference to the calculator service:</span></span>

   1. <span data-ttu-id="83f36-133">**Çözüm Gezgini** penceresinde, **GettingStartedClient** projesinin altındaki **References** klasörünü seçin ve sonra kısayol menüsünden **hizmet başvurusu Ekle** öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="83f36-133">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedClient** project, and then select **Add Service Reference** from the shortcut menu.</span></span>

   2. <span data-ttu-id="83f36-134">**Hizmet başvurusu Ekle** penceresinde **bul**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="83f36-134">In the **Add Service Reference** window, select **Discover**.</span></span>

      <span data-ttu-id="83f36-135">Hesaplatorservice hizmeti başlatılır ve Visual Studio bunu **Hizmetler** kutusunda görüntüler.</span><span class="sxs-lookup"><span data-stu-id="83f36-135">The CalculatorService service starts and Visual Studio displays it in the **Services** box.</span></span>

   3. <span data-ttu-id="83f36-136">Hesap ve hizmet tarafından uygulanan hizmet sözleşmelerini göstermek için **Hesaplatorservice** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="83f36-136">Select **CalculatorService** to expand it and display the service contracts implemented by the service.</span></span> <span data-ttu-id="83f36-137">Varsayılan **ad alanını** bırakın ve **Tamam**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="83f36-137">Leave the default **Namespace** and choose **OK**.</span></span>

      <span data-ttu-id="83f36-138">Visual Studio, **GettingStartedClient** projesindeki **bağlı hizmetler** klasörü altına yeni bir öğe ekler.</span><span class="sxs-lookup"><span data-stu-id="83f36-138">Visual Studio adds a new item under the **Connected Services** folder in the **GettingStartedClient** project.</span></span> 

### <a name="servicemodel-metadata-utility-tool"></a><span data-ttu-id="83f36-139">ServiceModel meta veri yardımcı programı Aracı</span><span class="sxs-lookup"><span data-stu-id="83f36-139">ServiceModel Metadata Utility tool</span></span>

<span data-ttu-id="83f36-140">Aşağıdaki örneklerde, proxy sınıfı dosyasını oluşturmak için isteğe bağlı olarak [ServiceModel meta veri yardımcı programı aracının (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="83f36-140">The following examples show how to optionally use the [ServiceModel Metadata Utility tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy class file.</span></span> <span data-ttu-id="83f36-141">Bu araç, proxy sınıfı dosyasını ve *app. config* dosyasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="83f36-141">This tool generates the proxy class file and the *App.config* file.</span></span> <span data-ttu-id="83f36-142">Aşağıdaki örneklerde, C# ve sırasıyla Visual Basic proxy 'nin nasıl oluşturulacağı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="83f36-142">The following examples show how to generate the proxy in C# and Visual Basic, respectively:</span></span>

```shell
svcutil.exe /language:cs /out:generatedProxy.cs /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

```shell
svcutil.exe /language:vb /out:generatedProxy.vb /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

### <a name="client-configuration-file"></a><span data-ttu-id="83f36-143">İstemci yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="83f36-143">Client configuration file</span></span>

<span data-ttu-id="83f36-144">İstemciyi oluşturduktan sonra, Visual Studio, **GettingStartedClient** projesinde **app. config** yapılandırma dosyasını oluşturur; Bu, aşağıdaki örneğe benzer olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="83f36-144">After you've created the client, Visual Studio creates the **App.config** configuration file in the **GettingStartedClient** project, which should be similar to the following example:</span></span>

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

<span data-ttu-id="83f36-145">[System. ServiceModel > bölümünde uç nokta > öğesine dikkat edin. \<](../configure-apps/file-schema/wcf/system-servicemodel.md) [ \<](../configure-apps/file-schema/wcf/endpoint-element.md)</span><span class="sxs-lookup"><span data-stu-id="83f36-145">Under the [\<system.serviceModel>](../configure-apps/file-schema/wcf/system-servicemodel.md) section, notice the [\<endpoint>](../configure-apps/file-schema/wcf/endpoint-element.md) element.</span></span> <span data-ttu-id="83f36-146">Endpoint öğesi istemcinin hizmete erişmek için kullandığı uç noktayı şu şekilde tanımlar: **&lt;&gt;**</span><span class="sxs-lookup"><span data-stu-id="83f36-146">The **&lt;endpoint&gt;** element defines the endpoint that the client uses to access the service as follows:</span></span>

- <span data-ttu-id="83f36-147">Adres: `http://localhost:8000/GettingStarted/CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="83f36-147">Address: `http://localhost:8000/GettingStarted/CalculatorService`.</span></span> <span data-ttu-id="83f36-148">Uç noktanın adresi.</span><span class="sxs-lookup"><span data-stu-id="83f36-148">The address of the endpoint.</span></span>
- <span data-ttu-id="83f36-149">Hizmet Sözleşmesi: `ServiceReference1.ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="83f36-149">Service contract: `ServiceReference1.ICalculator`.</span></span> <span data-ttu-id="83f36-150">Hizmet sözleşmesi, WCF istemcisiyle hizmet arasındaki iletişimi işler.</span><span class="sxs-lookup"><span data-stu-id="83f36-150">The service contract handles communication between the WCF client and the service.</span></span> <span data-ttu-id="83f36-151">Visual Studio, **hizmet başvurusu Ekle** işlevini kullandığınızda bu sözleşmeyi oluşturdu.</span><span class="sxs-lookup"><span data-stu-id="83f36-151">Visual Studio generated this contract when you used its **Add Service Reference** function.</span></span> <span data-ttu-id="83f36-152">Bu aslında, GettingStartedLib projesinde tanımladığınız sözleşmenin bir kopyasıdır.</span><span class="sxs-lookup"><span data-stu-id="83f36-152">It's essentially a copy of the contract that you defined in the GettingStartedLib project.</span></span> 
- <span data-ttu-id="83f36-153">Bağlama: <xref:System.ServiceModel.WSHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="83f36-153">Binding: <xref:System.ServiceModel.WSHttpBinding>.</span></span> <span data-ttu-id="83f36-154">Bağlama, aktarım, birlikte çalışabilen güvenlik ve diğer yapılandırma ayrıntıları olarak HTTP 'yi belirtir.</span><span class="sxs-lookup"><span data-stu-id="83f36-154">The binding specifies HTTP as the transport, interoperable security, and other configuration details.</span></span>

## <a name="next-steps"></a><span data-ttu-id="83f36-155">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="83f36-155">Next steps</span></span>

<span data-ttu-id="83f36-156">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="83f36-156">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="83f36-157">WCF istemcisi için bir konsol uygulaması projesi oluşturun ve yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="83f36-157">Create and configure a console app project for the WCF client.</span></span>
> - <span data-ttu-id="83f36-158">İstemci uygulaması için proxy sınıfı ve yapılandırma dosyalarını oluşturmak üzere WCF hizmetine bir hizmet başvurusu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="83f36-158">Add a service reference to the WCF service to generate the proxy class and configuration files for the client application.</span></span>

<span data-ttu-id="83f36-159">Oluşturulan istemciyi nasıl kullanacağınızı öğrenmek için sonraki öğreticiye ilerleyin.</span><span class="sxs-lookup"><span data-stu-id="83f36-159">Advance to the next tutorial to learn how to use the generated client.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="83f36-160">Öğretici: WCF istemcisi kullanma</span><span class="sxs-lookup"><span data-stu-id="83f36-160">Tutorial: Use a WCF client</span></span>](how-to-use-a-wcf-client.md)
