---
title: 'Öğretici: Bir Windows Communication Foundation istemcisi oluşturma'
ms.date: 03/19/2019
helpviewer_keywords:
- clients [WCF], running
- WCF clients [WCF], running
ms.assetid: a67884cc-1c4b-416b-8c96-5c954099f19f
ms.openlocfilehash: 0f7f622221e6612ecdb0ea04084d81e923218a5c
ms.sourcegitcommit: d938c39afb9216db377d0f0ecdaa53936a851059
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/29/2019
ms.locfileid: "58634069"
---
# <a name="tutorial-create-a-windows-communication-foundation-client"></a><span data-ttu-id="473c2-102">Öğretici: Bir Windows Communication Foundation istemcisi oluşturma</span><span class="sxs-lookup"><span data-stu-id="473c2-102">Tutorial: Create a Windows Communication Foundation client</span></span>

<span data-ttu-id="473c2-103">Bu öğreticide, temel Windows Communication Foundation (WCF) uygulaması oluşturmak için gereken beş görev dördüncü açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="473c2-103">This tutorial describes the fourth of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="473c2-104">Öğreticiler genel bakış için bkz. [Öğreticisi: Windows Communication Foundation uygulamalarla çalışmaya başlama](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="473c2-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="473c2-105">WCF uygulaması oluşturmak için sonraki görev, bir WCF hizmetinden meta verileri alarak bir istemci oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="473c2-105">The next task for creating a WCF application is to create a client by retrieving metadata from a WCF service.</span></span> <span data-ttu-id="473c2-106">Meta verileri alır bu hizmetin MEX uç noktasından bir hizmet başvurusu eklemek için Visual Studio'yu kullanın.</span><span class="sxs-lookup"><span data-stu-id="473c2-106">You use Visual Studio to add a service reference, which gets the metadata from the service’s MEX endpoint.</span></span> <span data-ttu-id="473c2-107">Visual Studio ardından seçtiğiniz dilde bir istemci proxy'si için bir yönetilen kaynak kodu dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="473c2-107">Visual Studio then generates a managed source code file for a client proxy in the language you've chosen.</span></span> <span data-ttu-id="473c2-108">Ayrıca bir istemci yapılandırma dosyası oluşturur (*App.config*).</span><span class="sxs-lookup"><span data-stu-id="473c2-108">It also creates a client configuration file (*App.config*).</span></span> <span data-ttu-id="473c2-109">Bu dosya, istemci uygulamanın, bir uç nokta adresindeki hizmet bağlanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="473c2-109">This file enables the client application to connect to the service at an endpoint.</span></span> 

> [!NOTE]
> <span data-ttu-id="473c2-110">Visual Studio'da bir sınıf kitaplığı projesi bir WCF Hizmeti çağırmanıza kullanırsanız **hizmet Başvurusu Ekle** otomatik olarak bir ara sunucu ve ilişkili yapılandırma dosyasını oluşturmak için özellik.</span><span class="sxs-lookup"><span data-stu-id="473c2-110">If you call a WCF service from a class library project in Visual Studio, use the **Add Service Reference** feature to automatically generate a proxy and associated configuration file.</span></span> <span data-ttu-id="473c2-111">Bu yapılandırma dosyasını sınıf kitaplığı projeleri kullanmayın çünkü Bununla birlikte, oluşturulan yapılandırma dosyasındaki ayarları eklemek ihtiyacınız *App.config* sınıf kitaplığı çağıran yürütülebilir dosyası için dosya.</span><span class="sxs-lookup"><span data-stu-id="473c2-111">However, because class library projects don't use this configuration file, you need to add the settings in the generated configuration file to the *App.config* file for the executable that calls the class library.</span></span>

> [!NOTE]
> <span data-ttu-id="473c2-112">Alternatif olarak, kullanın [ServiceModel meta veri yardımcı programracı](#servicemodel-metadata-utility-tool) proxy sınıfı ve yapılandırma dosyası oluşturmak için Visual Studio yerine.</span><span class="sxs-lookup"><span data-stu-id="473c2-112">As an alternative, use the [ServiceModel Metadata Utility tool](#servicemodel-metadata-utility-tool) instead of Visual Studio to generate the proxy class and configuration file.</span></span>

<span data-ttu-id="473c2-113">İstemci uygulama hizmeti ile iletişim kurmak için oluşturulan proxy sınıfını kullanır.</span><span class="sxs-lookup"><span data-stu-id="473c2-113">The client application uses the generated proxy class to communicate with the service.</span></span> <span data-ttu-id="473c2-114">Bu yordamda açıklanan [Öğreticisi: Bir istemci kullanın](how-to-use-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="473c2-114">This procedure is described in [Tutorial: Use a client](how-to-use-a-wcf-client.md).</span></span>

<span data-ttu-id="473c2-115">Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="473c2-115">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="473c2-116">Oluşturun ve bir konsol uygulama projesi için WCF istemcisini yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="473c2-116">Create and configure a console app project for the WCF client.</span></span>
> - <span data-ttu-id="473c2-117">Bir proxy sınıfı ve yapılandırma dosyaları oluşturmak için WCF hizmetine hizmet başvurusu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="473c2-117">Add a service reference to the WCF service to generate the proxy class and configuration files.</span></span>


## <a name="create-a-windows-communication-foundation-client"></a><span data-ttu-id="473c2-118">Bir Windows Communication Foundation istemcisi oluşturma</span><span class="sxs-lookup"><span data-stu-id="473c2-118">Create a Windows Communication Foundation client</span></span>

1. <span data-ttu-id="473c2-119">Visual Studio'da konsol uygulaması projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="473c2-119">Create a console app project in Visual Studio:</span></span> 

    1. <span data-ttu-id="473c2-120">Gelen **dosya** menüsünde **açık** > **proje/çözüm** ve **GettingStarted** çözüm, daha önce oluşturduğunuz (*GettingStarted.sln*).</span><span class="sxs-lookup"><span data-stu-id="473c2-120">From the **File** menu, select **Open** > **Project/Solution** and browse to the **GettingStarted** solution you previously created (*GettingStarted.sln*).</span></span> <span data-ttu-id="473c2-121">**Aç**'ı seçin.</span><span class="sxs-lookup"><span data-stu-id="473c2-121">Select **Open**.</span></span>

    2. <span data-ttu-id="473c2-122">Gelen **görünümü** menüsünde **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="473c2-122">From the **View** menu, select **Solution Explorer**.</span></span>

    3. <span data-ttu-id="473c2-123">İçinde **Çözüm Gezgini** penceresinde **GettingStarted** çözüm (üst düğümü) ve ardından **Ekle** > **YeniProje** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="473c2-123">In the **Solution Explorer** window, select the **GettingStarted** solution (top node), and then select **Add** > **New Project** from the shortcut menu.</span></span> 
    
    4. <span data-ttu-id="473c2-124">İçinde **Yeni Proje Ekle** penceresinde, sol tarafta, select **Windows Masaüstü** kategorisi altında **Visual C#**  veya **Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="473c2-124">In the **Add New Project** window, on the left side, select the **Windows Desktop** category under **Visual C#** or **Visual Basic**.</span></span> 

    5. <span data-ttu-id="473c2-125">Seçin **konsol uygulaması (.NET Framework)** şablon girin *GettingStartedClient* için **adı**.</span><span class="sxs-lookup"><span data-stu-id="473c2-125">Select the **Console App (.NET Framework)** template, and enter *GettingStartedClient* for the **Name**.</span></span> <span data-ttu-id="473c2-126">**Tamam**’ı seçin.</span><span class="sxs-lookup"><span data-stu-id="473c2-126">Select **OK**.</span></span>

2. <span data-ttu-id="473c2-127">Başvuru ekleme **GettingStartedClient** için proje <xref:System.ServiceModel> derleme:</span><span class="sxs-lookup"><span data-stu-id="473c2-127">Add a reference in the **GettingStartedClient** project to the <xref:System.ServiceModel> assembly:</span></span> 

    1.  <span data-ttu-id="473c2-128">İçinde **Çözüm Gezgini** penceresinde **başvuruları** klasörü altında **GettingStartedClient** proje ve ardından **BaşvuruEkle** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="473c2-128">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedClient** project, and then select **Add Reference** from the shortcut menu.</span></span> 

    2. <span data-ttu-id="473c2-129">İçinde **Başvuru Ekle** penceresinin altında **derlemeleri** penceresinin sol taraftan **Framework**.</span><span class="sxs-lookup"><span data-stu-id="473c2-129">In the **Add Reference** window, under **Assemblies** on the left side of the window, select **Framework**.</span></span>
    
    3. <span data-ttu-id="473c2-130">Bulmak ve seçmek **System.ServiceModel**ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="473c2-130">Find and select **System.ServiceModel**, and then choose **OK**.</span></span> 

    4. <span data-ttu-id="473c2-131">Çözüm seçerek Kaydet **dosya** > **Tümünü Kaydet**.</span><span class="sxs-lookup"><span data-stu-id="473c2-131">Save the solution by selecting **File** > **Save All**.</span></span>

3. <span data-ttu-id="473c2-132">Bir hesap makinesi hizmetine hizmet Başvurusu Ekle:</span><span class="sxs-lookup"><span data-stu-id="473c2-132">Add a service reference to the calculator service:</span></span>

   1. <span data-ttu-id="473c2-133">İçinde **Çözüm Gezgini** penceresinde **başvuruları** klasörü altında **GettingStartedClient** proje ve ardından **hizmet Başvurusu Ekle**  kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="473c2-133">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedClient** project, and then select **Add Service Reference** from the shortcut menu.</span></span>

   2. <span data-ttu-id="473c2-134">İçinde **hizmet Başvurusu Ekle** penceresinde **bulma**.</span><span class="sxs-lookup"><span data-stu-id="473c2-134">In the **Add Service Reference** window, select **Discover**.</span></span>

      <span data-ttu-id="473c2-135">CalculatorService hizmeti başlatır ve Visual Studio içinde görüntüler **Hizmetleri** kutusu.</span><span class="sxs-lookup"><span data-stu-id="473c2-135">The CalculatorService service starts and Visual Studio displays it in the **Services** box.</span></span>

   3. <span data-ttu-id="473c2-136">Seçin **CalculatorService** genişletmek ve hizmeti tarafından uygulanan hizmet sözleşmelerini görüntülemek için.</span><span class="sxs-lookup"><span data-stu-id="473c2-136">Select **CalculatorService** to expand it and display the service contracts implemented by the service.</span></span> <span data-ttu-id="473c2-137">Varsayılan değeri bırakın **Namespace** ve **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="473c2-137">Leave the default **Namespace** and choose **OK**.</span></span>

      <span data-ttu-id="473c2-138">Visual Studio altında yeni bir öğe ekler **bağlı hizmetler** klasöründe **GettingStartedClient** proje.</span><span class="sxs-lookup"><span data-stu-id="473c2-138">Visual Studio adds a new item under the **Connected Services** folder in the **GettingStartedClient** project.</span></span> 


### <a name="servicemodel-metadata-utility-tool"></a><span data-ttu-id="473c2-139">ServiceModel meta veri yardımcı programracı</span><span class="sxs-lookup"><span data-stu-id="473c2-139">ServiceModel Metadata Utility tool</span></span>

<span data-ttu-id="473c2-140">Aşağıdaki örnekler, isteğe bağlı olarak kullanmayı göstermektedir [ServiceModel meta veri yardımcı programracı (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) proxy sınıfı dosyası oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="473c2-140">The following examples show how to optionally use the [ServiceModel Metadata Utility tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy class file.</span></span> <span data-ttu-id="473c2-141">Bu araç proxy sınıfı dosyası oluşturur ve *App.config* dosya.</span><span class="sxs-lookup"><span data-stu-id="473c2-141">This tool generates the proxy class file and the *App.config* file.</span></span> <span data-ttu-id="473c2-142">Aşağıdaki örnekler proxy oluşturma C# ve Visual Basic, sırasıyla:</span><span class="sxs-lookup"><span data-stu-id="473c2-142">The following examples show how to generate the proxy in C# and Visual Basic, respectively:</span></span>

```shell
svcutil.exe /language:cs /out:generatedProxy.cs /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

```shell
svcutil.exe /language:vb /out:generatedProxy.vb /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

### <a name="client-configuration-file"></a><span data-ttu-id="473c2-143">İstemci yapılandırma dosyası</span><span class="sxs-lookup"><span data-stu-id="473c2-143">Client configuration file</span></span>

<span data-ttu-id="473c2-144">İstemci oluşturduktan sonra Visual Studio oluşturur **App.config** yapılandırma dosyasında **GettingStartedClient** proje, aşağıdaki örneğe benzer olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="473c2-144">After you've created the client, Visual Studio creates the **App.config** configuration file in the **GettingStartedClient** project, which should be similar to the following example:</span></span>

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

<span data-ttu-id="473c2-145">Altında [ \<system.serviceModel >](../configure-apps/file-schema/wcf/system-servicemodel.md) bölümünde, fark [ \<uç noktası >](../configure-apps/file-schema/wcf/endpoint-element.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="473c2-145">Under the [\<system.serviceModel>](../configure-apps/file-schema/wcf/system-servicemodel.md) section, notice the [\<endpoint>](../configure-apps/file-schema/wcf/endpoint-element.md) element.</span></span> <span data-ttu-id="473c2-146">**&lt;Uç nokta&gt;** öğe istemcinin gibi hizmete erişmek için kullandığı uç nokta tanımlar:</span><span class="sxs-lookup"><span data-stu-id="473c2-146">The **&lt;endpoint&gt;** element defines the endpoint that the client uses to access the service as follows:</span></span>
- <span data-ttu-id="473c2-147">Adres: `http://localhost:8000/GettingStarted/CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="473c2-147">Address: `http://localhost:8000/GettingStarted/CalculatorService`.</span></span> <span data-ttu-id="473c2-148">Uç nokta adresi.</span><span class="sxs-lookup"><span data-stu-id="473c2-148">The address of the endpoint.</span></span>
- <span data-ttu-id="473c2-149">Hizmet sözleşmesi: `ServiceReference1.ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="473c2-149">Service contract: `ServiceReference1.ICalculator`.</span></span> <span data-ttu-id="473c2-150">Hizmet sözleşmesi WCF İstemcisi hizmeti arasındaki iletişimi gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="473c2-150">The service contract handles communication between the WCF client and the service.</span></span> <span data-ttu-id="473c2-151">Visual Studio, bu sözleşme, kullanıldığında oluşturulan kendi **hizmet Başvurusu Ekle** işlevi.</span><span class="sxs-lookup"><span data-stu-id="473c2-151">Visual Studio generated this contract when you used its **Add Service Reference** function.</span></span> <span data-ttu-id="473c2-152">Bu temelde GettingStartedLib projede tanımlanan sözleşme bir kopyasıdır.</span><span class="sxs-lookup"><span data-stu-id="473c2-152">It's essentially a copy of the contract that you defined in the GettingStartedLib project.</span></span> 
- <span data-ttu-id="473c2-153">Bağlama: <xref:System.ServiceModel.WSHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="473c2-153">Binding: <xref:System.ServiceModel.WSHttpBinding>.</span></span> <span data-ttu-id="473c2-154">Bağlama HTTP taşıma, birlikte çalışabilen güvenlik ve diğer yapılandırma ayrıntılarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="473c2-154">The binding specifies HTTP as the transport, interoperable security, and other configuration details.</span></span>

## <a name="next-steps"></a><span data-ttu-id="473c2-155">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="473c2-155">Next steps</span></span>

<span data-ttu-id="473c2-156">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="473c2-156">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="473c2-157">Oluşturun ve bir konsol uygulama projesi için WCF istemcisini yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="473c2-157">Create and configure a console app project for the WCF client.</span></span>
> - <span data-ttu-id="473c2-158">Bir istemci uygulaması proxy sınıfı ve yapılandırma dosyaları oluşturmak için WCF hizmetine hizmet başvurusu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="473c2-158">Add a service reference to the WCF service to generate the proxy class and configuration files for the client application.</span></span>

<span data-ttu-id="473c2-159">Oluşturulan istemciyi kullanma hakkında bilgi edinmek için sonraki öğreticiye ilerleyin.</span><span class="sxs-lookup"><span data-stu-id="473c2-159">Advance to the next tutorial to learn how to use the generated client.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="473c2-160">Öğretici: WCF istemci kullanma</span><span class="sxs-lookup"><span data-stu-id="473c2-160">Tutorial: Use a WCF client</span></span>](how-to-use-a-wcf-client.md)


