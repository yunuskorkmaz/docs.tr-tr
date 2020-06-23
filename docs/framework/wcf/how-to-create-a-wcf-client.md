---
title: 'Öğretici: Windows Communication Foundation istemci oluşturma'
description: WCF uygulaması oluşturmaya başlamanıza yardımcı olan bir makale serisinin parçası olarak bir WCF hizmetinden meta verileri alarak istemci oluşturmayı öğrenin.
ms.date: 03/19/2019
helpviewer_keywords:
- clients [WCF], running
- WCF clients [WCF], running
ms.assetid: a67884cc-1c4b-416b-8c96-5c954099f19f
ms.openlocfilehash: d5a2a2b5175c9e34eaf1dbaff20ac57f34117c4e
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246330"
---
# <a name="tutorial-create-a-windows-communication-foundation-client"></a><span data-ttu-id="77162-103">Öğretici: Windows Communication Foundation istemci oluşturma</span><span class="sxs-lookup"><span data-stu-id="77162-103">Tutorial: Create a Windows Communication Foundation client</span></span>

<span data-ttu-id="77162-104">Bu öğreticide, temel bir Windows Communication Foundation (WCF) uygulaması oluşturmak için gereken dördüncü beş görev açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="77162-104">This tutorial describes the fourth of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="77162-105">Öğreticilere genel bakış için bkz. [öğretici: Windows Communication Foundation uygulamalarla çalışmaya başlama](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="77162-105">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="77162-106">WCF uygulaması oluşturmaya yönelik sonraki görev, bir WCF hizmetinden meta verileri alarak istemci oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="77162-106">The next task for creating a WCF application is to create a client by retrieving metadata from a WCF service.</span></span> <span data-ttu-id="77162-107">Hizmetin MEX uç noktasından meta verileri alan bir hizmet başvurusu eklemek için Visual Studio 'Yu kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="77162-107">You use Visual Studio to add a service reference, which gets the metadata from the service’s MEX endpoint.</span></span> <span data-ttu-id="77162-108">Daha sonra Visual Studio, seçtiğiniz dilde istemci proxy 'si için bir yönetilen kaynak kodu dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="77162-108">Visual Studio then generates a managed source code file for a client proxy in the language you've chosen.</span></span> <span data-ttu-id="77162-109">Ayrıca, bir istemci yapılandırma dosyası (*App.config*) oluşturur.</span><span class="sxs-lookup"><span data-stu-id="77162-109">It also creates a client configuration file (*App.config*).</span></span> <span data-ttu-id="77162-110">Bu dosya, istemci uygulamasının bir uç noktada hizmete bağlanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="77162-110">This file enables the client application to connect to the service at an endpoint.</span></span>

> [!NOTE]
> <span data-ttu-id="77162-111">Visual Studio 'da bir sınıf kitaplığı projesinden bir WCF hizmeti çağırırsanız, otomatik olarak bir proxy ve ilişkili yapılandırma dosyası oluşturmak için **hizmet başvurusu Ekle** özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="77162-111">If you call a WCF service from a class library project in Visual Studio, use the **Add Service Reference** feature to automatically generate a proxy and associated configuration file.</span></span> <span data-ttu-id="77162-112">Ancak, sınıf kitaplığı projeleri bu yapılandırma dosyasını kullanmadığından, oluşturulan yapılandırma dosyasındaki ayarları, sınıf kitaplığını çağıran yürütülebilir dosyanın *App.config* dosyasına eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="77162-112">However, because class library projects don't use this configuration file, you need to add the settings in the generated configuration file to the *App.config* file for the executable that calls the class library.</span></span>

> [!NOTE]
> <span data-ttu-id="77162-113">Alternatif olarak, proxy sınıfını ve yapılandırma dosyasını oluşturmak için Visual Studio yerine [ServiceModel meta veri yardımcı programı aracını](#servicemodel-metadata-utility-tool) kullanın.</span><span class="sxs-lookup"><span data-stu-id="77162-113">As an alternative, use the [ServiceModel Metadata Utility tool](#servicemodel-metadata-utility-tool) instead of Visual Studio to generate the proxy class and configuration file.</span></span>

<span data-ttu-id="77162-114">İstemci uygulaması, hizmetle iletişim kurmak için oluşturulan proxy sınıfını kullanır.</span><span class="sxs-lookup"><span data-stu-id="77162-114">The client application uses the generated proxy class to communicate with the service.</span></span> <span data-ttu-id="77162-115">Bu yordam [öğretici: Istemci kullanma](how-to-use-a-wcf-client.md)' da açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="77162-115">This procedure is described in [Tutorial: Use a client](how-to-use-a-wcf-client.md).</span></span>

<span data-ttu-id="77162-116">Bu öğreticide aşağıdakilerin nasıl yapılacağını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="77162-116">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="77162-117">WCF istemcisi için bir konsol uygulaması projesi oluşturun ve yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="77162-117">Create and configure a console app project for the WCF client.</span></span>
> - <span data-ttu-id="77162-118">Proxy sınıfı ve yapılandırma dosyalarını oluşturmak için WCF hizmetine bir hizmet başvurusu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="77162-118">Add a service reference to the WCF service to generate the proxy class and configuration files.</span></span>

## <a name="create-a-windows-communication-foundation-client"></a><span data-ttu-id="77162-119">Windows Communication Foundation istemcisi oluşturma</span><span class="sxs-lookup"><span data-stu-id="77162-119">Create a Windows Communication Foundation client</span></span>

1. <span data-ttu-id="77162-120">Visual Studio 'da bir konsol uygulaması projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="77162-120">Create a console app project in Visual Studio:</span></span>

    1. <span data-ttu-id="77162-121">**Dosya** menüsünde **Open**  >  **Proje/çözüm** aç ' ı seçin ve daha önce oluşturduğunuz **gettingstarted** çözümüne (*gettingstarted. sln*) gidin.</span><span class="sxs-lookup"><span data-stu-id="77162-121">From the **File** menu, select **Open** > **Project/Solution** and browse to the **GettingStarted** solution you previously created (*GettingStarted.sln*).</span></span> <span data-ttu-id="77162-122">**Aç**'ı seçin.</span><span class="sxs-lookup"><span data-stu-id="77162-122">Select **Open**.</span></span>

    2. <span data-ttu-id="77162-123">**Görünüm** menüsünden **Çözüm Gezgini**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="77162-123">From the **View** menu, select **Solution Explorer**.</span></span>

    3. <span data-ttu-id="77162-124">**Çözüm Gezgini** penceresinde, **gettingstarted** çözümünü (üst düğüm) seçin ve sonra **Add**  >  kısayol menüsünden**Yeni proje** Ekle ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="77162-124">In the **Solution Explorer** window, select the **GettingStarted** solution (top node), and then select **Add** > **New Project** from the shortcut menu.</span></span>

    4. <span data-ttu-id="77162-125">**Yeni Proje Ekle** penceresinde, sol taraftaki **Visual C#** veya **Visual Basic**altındaki **Windows Masaüstü** kategorisini seçin.</span><span class="sxs-lookup"><span data-stu-id="77162-125">In the **Add New Project** window, on the left side, select the **Windows Desktop** category under **Visual C#** or **Visual Basic**.</span></span>

    5. <span data-ttu-id="77162-126">**Konsol uygulaması (.NET Framework)** şablonunu seçin ve **ad**Için *GettingStartedClient* yazın.</span><span class="sxs-lookup"><span data-stu-id="77162-126">Select the **Console App (.NET Framework)** template, and enter *GettingStartedClient* for the **Name**.</span></span> <span data-ttu-id="77162-127">**Tamam**’ı seçin.</span><span class="sxs-lookup"><span data-stu-id="77162-127">Select **OK**.</span></span>

2. <span data-ttu-id="77162-128">**GettingStartedClient** projesinde derlemeye bir başvuru ekleyin <xref:System.ServiceModel> :</span><span class="sxs-lookup"><span data-stu-id="77162-128">Add a reference in the **GettingStartedClient** project to the <xref:System.ServiceModel> assembly:</span></span>

    1. <span data-ttu-id="77162-129">**Çözüm Gezgini** penceresinde, **GettingStartedClient** projesi altındaki **Başvurular** klasörünü seçin ve kısayol menüsünden **Başvuru Ekle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="77162-129">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedClient** project, and then select **Add Reference** from the shortcut menu.</span></span>

    2. <span data-ttu-id="77162-130">**Başvuru Ekle** penceresinde pencerenin sol tarafındaki **derlemeler** altında **Framework**' ü seçin.</span><span class="sxs-lookup"><span data-stu-id="77162-130">In the **Add Reference** window, under **Assemblies** on the left side of the window, select **Framework**.</span></span>

    3. <span data-ttu-id="77162-131">**System. ServiceModel**bulun ve seçin ve ardından **Tamam**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="77162-131">Find and select **System.ServiceModel**, and then choose **OK**.</span></span>

    4. <span data-ttu-id="77162-132">**Dosya**  >  **Tümünü Kaydet**' i seçerek çözümü kaydedin.</span><span class="sxs-lookup"><span data-stu-id="77162-132">Save the solution by selecting **File** > **Save All**.</span></span>

3. <span data-ttu-id="77162-133">Hesaplayıcı hizmetine bir hizmet başvurusu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="77162-133">Add a service reference to the calculator service:</span></span>

   1. <span data-ttu-id="77162-134">**Çözüm Gezgini** penceresinde, **GettingStartedClient** projesinin altındaki **References** klasörünü seçin ve sonra kısayol menüsünden **hizmet başvurusu Ekle** öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="77162-134">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedClient** project, and then select **Add Service Reference** from the shortcut menu.</span></span>

   2. <span data-ttu-id="77162-135">**Hizmet başvurusu Ekle** penceresinde **bul**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="77162-135">In the **Add Service Reference** window, select **Discover**.</span></span>

      <span data-ttu-id="77162-136">Hesaplatorservice hizmeti başlatılır ve Visual Studio bunu **Hizmetler** kutusunda görüntüler.</span><span class="sxs-lookup"><span data-stu-id="77162-136">The CalculatorService service starts and Visual Studio displays it in the **Services** box.</span></span>

   3. <span data-ttu-id="77162-137">Hesap ve hizmet tarafından uygulanan hizmet sözleşmelerini göstermek için **Hesaplatorservice** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="77162-137">Select **CalculatorService** to expand it and display the service contracts implemented by the service.</span></span> <span data-ttu-id="77162-138">Varsayılan **ad alanını** bırakın ve **Tamam**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="77162-138">Leave the default **Namespace** and choose **OK**.</span></span>

      <span data-ttu-id="77162-139">Visual Studio, **GettingStartedClient** projesindeki **bağlı hizmetler** klasörü altına yeni bir öğe ekler.</span><span class="sxs-lookup"><span data-stu-id="77162-139">Visual Studio adds a new item under the **Connected Services** folder in the **GettingStartedClient** project.</span></span>

### <a name="servicemodel-metadata-utility-tool"></a><span data-ttu-id="77162-140">ServiceModel meta veri yardımcı programı Aracı</span><span class="sxs-lookup"><span data-stu-id="77162-140">ServiceModel Metadata Utility tool</span></span>

<span data-ttu-id="77162-141">Aşağıdaki örneklerde, proxy sınıfı dosyasını oluşturmak için isteğe bağlı olarak [ServiceModel meta veri yardımcı programı aracının (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="77162-141">The following examples show how to optionally use the [ServiceModel Metadata Utility tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy class file.</span></span> <span data-ttu-id="77162-142">Bu araç, proxy sınıfı dosyasını ve *App.config* dosyasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="77162-142">This tool generates the proxy class file and the *App.config* file.</span></span> <span data-ttu-id="77162-143">Aşağıdaki örneklerde, sırasıyla C# ve Visual Basic proxy 'nin nasıl oluşturulacağı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="77162-143">The following examples show how to generate the proxy in C# and Visual Basic, respectively:</span></span>

```shell
svcutil.exe /language:cs /out:generatedProxy.cs /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

```shell
svcutil.exe /language:vb /out:generatedProxy.vb /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

### <a name="client-configuration-file"></a><span data-ttu-id="77162-144">İstemci yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="77162-144">Client configuration file</span></span>

<span data-ttu-id="77162-145">İstemciyi oluşturduktan sonra, Visual Studio, aşağıdaki örneğe benzer olması gereken **GettingStartedClient** projesinde **App.config** yapılandırma dosyasını oluşturur:</span><span class="sxs-lookup"><span data-stu-id="77162-145">After you've created the client, Visual Studio creates the **App.config** configuration file in the **GettingStartedClient** project, which should be similar to the following example:</span></span>

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

<span data-ttu-id="77162-146">Bölümünün altında, [\<system.serviceModel>](../configure-apps/file-schema/wcf/system-servicemodel.md) öğesine dikkat edin [\<endpoint>](../configure-apps/file-schema/wcf/endpoint-element.md) .</span><span class="sxs-lookup"><span data-stu-id="77162-146">Under the [\<system.serviceModel>](../configure-apps/file-schema/wcf/system-servicemodel.md) section, notice the [\<endpoint>](../configure-apps/file-schema/wcf/endpoint-element.md) element.</span></span> <span data-ttu-id="77162-147">\*\* &lt; Endpoint &gt; \*\* öğesi istemcinin hizmete erişmek için kullandığı uç noktayı şu şekilde tanımlar:</span><span class="sxs-lookup"><span data-stu-id="77162-147">The **&lt;endpoint&gt;** element defines the endpoint that the client uses to access the service as follows:</span></span>

- <span data-ttu-id="77162-148">Adres: `http://localhost:8000/GettingStarted/CalculatorService` .</span><span class="sxs-lookup"><span data-stu-id="77162-148">Address: `http://localhost:8000/GettingStarted/CalculatorService`.</span></span> <span data-ttu-id="77162-149">Uç noktanın adresi.</span><span class="sxs-lookup"><span data-stu-id="77162-149">The address of the endpoint.</span></span>
- <span data-ttu-id="77162-150">Hizmet Sözleşmesi: `ServiceReference1.ICalculator` .</span><span class="sxs-lookup"><span data-stu-id="77162-150">Service contract: `ServiceReference1.ICalculator`.</span></span> <span data-ttu-id="77162-151">Hizmet sözleşmesi, WCF istemcisiyle hizmet arasındaki iletişimi işler.</span><span class="sxs-lookup"><span data-stu-id="77162-151">The service contract handles communication between the WCF client and the service.</span></span> <span data-ttu-id="77162-152">Visual Studio, **hizmet başvurusu Ekle** işlevini kullandığınızda bu sözleşmeyi oluşturdu.</span><span class="sxs-lookup"><span data-stu-id="77162-152">Visual Studio generated this contract when you used its **Add Service Reference** function.</span></span> <span data-ttu-id="77162-153">Bu aslında, GettingStartedLib projesinde tanımladığınız sözleşmenin bir kopyasıdır.</span><span class="sxs-lookup"><span data-stu-id="77162-153">It's essentially a copy of the contract that you defined in the GettingStartedLib project.</span></span>
- <span data-ttu-id="77162-154">Bağlama: <xref:System.ServiceModel.WSHttpBinding> .</span><span class="sxs-lookup"><span data-stu-id="77162-154">Binding: <xref:System.ServiceModel.WSHttpBinding>.</span></span> <span data-ttu-id="77162-155">Bağlama, aktarım, birlikte çalışabilen güvenlik ve diğer yapılandırma ayrıntıları olarak HTTP 'yi belirtir.</span><span class="sxs-lookup"><span data-stu-id="77162-155">The binding specifies HTTP as the transport, interoperable security, and other configuration details.</span></span>

## <a name="next-steps"></a><span data-ttu-id="77162-156">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="77162-156">Next steps</span></span>

<span data-ttu-id="77162-157">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="77162-157">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="77162-158">WCF istemcisi için bir konsol uygulaması projesi oluşturun ve yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="77162-158">Create and configure a console app project for the WCF client.</span></span>
> - <span data-ttu-id="77162-159">İstemci uygulaması için proxy sınıfı ve yapılandırma dosyalarını oluşturmak üzere WCF hizmetine bir hizmet başvurusu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="77162-159">Add a service reference to the WCF service to generate the proxy class and configuration files for the client application.</span></span>

<span data-ttu-id="77162-160">Oluşturulan istemciyi nasıl kullanacağınızı öğrenmek için sonraki öğreticiye ilerleyin.</span><span class="sxs-lookup"><span data-stu-id="77162-160">Advance to the next tutorial to learn how to use the generated client.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="77162-161">Öğretici: WCF istemcisi kullanma</span><span class="sxs-lookup"><span data-stu-id="77162-161">Tutorial: Use a WCF client</span></span>](how-to-use-a-wcf-client.md)
