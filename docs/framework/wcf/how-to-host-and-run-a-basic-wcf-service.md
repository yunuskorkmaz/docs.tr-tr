---
title: 'Öğretici: Temel bir Windows Communication Foundation hizmetini barındırın ve çalıştırın'
ms.date: 03/19/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF services [WCF]
- WCF services [WCF], running
ms.assetid: 31774d36-923b-4e2d-812e-aa190127266f
ms.openlocfilehash: 30eb86987b83427b94c6fff22755cde3d73dd9f0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184077"
---
# <a name="tutorial-host-and-run-a-basic-windows-communication-foundation-service"></a><span data-ttu-id="8183d-102">Öğretici: Temel bir Windows Communication Foundation hizmetini barındırın ve çalıştırın</span><span class="sxs-lookup"><span data-stu-id="8183d-102">Tutorial: Host and run a basic Windows Communication Foundation service</span></span>

<span data-ttu-id="8183d-103">Bu öğretici, temel bir Windows Communication Foundation (WCF) uygulaması oluşturmak için gereken beş görevin üçüncüsüni açıklar.</span><span class="sxs-lookup"><span data-stu-id="8183d-103">This tutorial describes the third of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="8183d-104">Öğreticilere genel bir bakış için [Bkz. Öğretici: Windows Communication Foundation uygulamalarıyla başlayın.](getting-started-tutorial.md)</span><span class="sxs-lookup"><span data-stu-id="8183d-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="8183d-105">WCF uygulaması oluşturmak için bir sonraki görev, bir konsol uygulamasında bir WCF hizmetini barındırmaktır.</span><span class="sxs-lookup"><span data-stu-id="8183d-105">The next task for creating a WCF application is to host a WCF service in a console application.</span></span> <span data-ttu-id="8183d-106">WCF hizmeti, her biri bir veya daha fazla hizmet operasyonunu ortaya çıkaran bir veya daha fazla *uç noktayı*ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="8183d-106">A WCF service exposes one or more *endpoints*, each of which exposes one or more service operations.</span></span> <span data-ttu-id="8183d-107">Hizmet bitiş noktası aşağıdaki bilgileri belirtir:</span><span class="sxs-lookup"><span data-stu-id="8183d-107">A service endpoint specifies the following information:</span></span>

- <span data-ttu-id="8183d-108">Hizmeti bulabileceğiniz bir adres.</span><span class="sxs-lookup"><span data-stu-id="8183d-108">An address where you can find the service.</span></span>
- <span data-ttu-id="8183d-109">İstemci hizmeti ile nasıl iletişim kurması gerektiğini açıklayan bilgileri içeren bir bağlayıcı.</span><span class="sxs-lookup"><span data-stu-id="8183d-109">A binding that contains the information that describes how a client must communicate with the service.</span></span>
- <span data-ttu-id="8183d-110">Hizmetin istemcilerine sağladığı işlevselliği tanımlayan sözleşme.</span><span class="sxs-lookup"><span data-stu-id="8183d-110">A contract that defines the functionality that the service provides to its clients.</span></span>

<span data-ttu-id="8183d-111">Bu öğreticide şunların nasıl yapıldığını öğrenirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8183d-111">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="8183d-112">Bir WCF hizmeti barındırmak için bir konsol uygulaması projesi oluşturun ve yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="8183d-112">Create and configure a console app project for hosting a WCF service.</span></span>
> - <span data-ttu-id="8183d-113">WCF hizmetini barındırmak için kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8183d-113">Add code to host the WCF service.</span></span>
> - <span data-ttu-id="8183d-114">Yapılandırma dosyasını güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="8183d-114">Update the configuration file.</span></span>
> - <span data-ttu-id="8183d-115">WCF hizmetini başlatın ve çalıştığını doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="8183d-115">Start the WCF service and verify it's running.</span></span>

## <a name="create-and-configure-a-console-app-project-for-hosting-the-service"></a><span data-ttu-id="8183d-116">Hizmeti barındırmak için bir konsol uygulaması projesi oluşturma ve yapılandırma</span><span class="sxs-lookup"><span data-stu-id="8183d-116">Create and configure a console app project for hosting the service</span></span>

1. <span data-ttu-id="8183d-117">Visual Studio'da bir konsol uygulaması projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="8183d-117">Create a console app project in Visual Studio:</span></span>

    1. <span data-ttu-id="8183d-118">**Dosya** menüsünden**Proje/Çözüm** **Aç'ı** > seçin ve daha önce oluşturduğunuz **Başlangıç** çözümüne göz atın *(GettingStarted.sln).*</span><span class="sxs-lookup"><span data-stu-id="8183d-118">From the **File** menu, select **Open** > **Project/Solution** and browse to the **GettingStarted** solution you previously created (*GettingStarted.sln*).</span></span> <span data-ttu-id="8183d-119">**Aç**'ı seçin.</span><span class="sxs-lookup"><span data-stu-id="8183d-119">Select **Open**.</span></span>

    2. <span data-ttu-id="8183d-120">**Görünüm** menüsünden **Çözüm Gezgini'ni**seçin.</span><span class="sxs-lookup"><span data-stu-id="8183d-120">From the **View** menu, select **Solution Explorer**.</span></span>

    3. <span data-ttu-id="8183d-121">Çözüm **Gezgini** penceresinde, **Başlangıç** Çözümünü (üst düğüm) seçin ve ardından kısayol menüsünden**Yeni Proje** **Ekle'yi** > seçin.</span><span class="sxs-lookup"><span data-stu-id="8183d-121">In the **Solution Explorer** window, select the **GettingStarted** solution (top node), and then select **Add** > **New Project** from the shortcut menu.</span></span>

    4. <span data-ttu-id="8183d-122">Yeni **Proje Ekle** penceresinde, sol tarafta, **Visual C#** veya **Visual Basic**altında Windows **Masaüstü** kategorisini seçin.</span><span class="sxs-lookup"><span data-stu-id="8183d-122">In the **Add New Project** window, on the left side, select the **Windows Desktop** category under **Visual C#** or **Visual Basic**.</span></span>

    5. <span data-ttu-id="8183d-123">Konsol **Uygulaması (.NET Framework)** şablonunu seçin ve **Ad**için *GettingStartedHost'u* girin.</span><span class="sxs-lookup"><span data-stu-id="8183d-123">Select the **Console App (.NET Framework)** template, and enter *GettingStartedHost* for the **Name**.</span></span> <span data-ttu-id="8183d-124">**Tamam'ı**seçin.</span><span class="sxs-lookup"><span data-stu-id="8183d-124">Select **OK**.</span></span>

2. <span data-ttu-id="8183d-125">**GettingStartedLib** projesine **GettingStartedHost** projesine bir başvuru ekleyin:</span><span class="sxs-lookup"><span data-stu-id="8183d-125">Add a reference in the **GettingStartedHost** project to the **GettingStartedLib** project:</span></span>

    1. <span data-ttu-id="8183d-126">Çözüm **Gezgini** penceresinde, **GettingStartedHost** projesinin altındaki **Başvurular** klasörünü seçin ve ardından kısayol menüsünden **Başvuru Ekle'yi** seçin.</span><span class="sxs-lookup"><span data-stu-id="8183d-126">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedHost** project, and then select **Add Reference** from the shortcut menu.</span></span>

    2. <span data-ttu-id="8183d-127">Başvuru **Ekle** iletişim kutusunda, pencerenin sol tarafındaki **Projeler** altında **Çözüm'ü**seçin.</span><span class="sxs-lookup"><span data-stu-id="8183d-127">In the **Add Reference** dialog, under **Projects** on the left side of the window, select **Solution**.</span></span>

    3. <span data-ttu-id="8183d-128">Pencerenin orta bölümünde **GettingStartedLib'i** seçin ve ardından **Tamam'ı**seçin.</span><span class="sxs-lookup"><span data-stu-id="8183d-128">Select **GettingStartedLib** in the center section of the window, and then select **OK**.</span></span>

       <span data-ttu-id="8183d-129">Bu eylem, **GettingStartedLib** projesinde tanımlanan türleri **GettingStartedHost** projesiiçin kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="8183d-129">This action makes the types defined in the **GettingStartedLib** project available to the **GettingStartedHost** project.</span></span>

3. <span data-ttu-id="8183d-130">**Derlemeye GettingStartedHost** projesinde <xref:System.ServiceModel> bir başvuru ekleyin:</span><span class="sxs-lookup"><span data-stu-id="8183d-130">Add a reference in the **GettingStartedHost** project to the <xref:System.ServiceModel> assembly:</span></span>

    1. <span data-ttu-id="8183d-131">Çözüm **Gezgini** penceresinde, **GettingStartedHost** projesinin altındaki **Başvurular** klasörünü seçin ve ardından kısayol menüsünden **Başvuru Ekle'yi** seçin.</span><span class="sxs-lookup"><span data-stu-id="8183d-131">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedHost** project, and then select **Add Reference** from the shortcut menu.</span></span>

    2. <span data-ttu-id="8183d-132">Başvuru **Ekle** penceresinde, pencerenin sol tarafındaki **Derlemeler** altında **Çerçeve'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="8183d-132">In the **Add Reference** window, under **Assemblies** on the left side of the window, select **Framework**.</span></span>

    3. <span data-ttu-id="8183d-133">**System.ServiceModel'i**seçin ve ardından **Tamam'ı**seçin.</span><span class="sxs-lookup"><span data-stu-id="8183d-133">Select **System.ServiceModel**, and then select **OK**.</span></span>

    4. <span data-ttu-id="8183d-134">**Tümünü Kaydet'i** > seçerek çözümü**kaydedin.**</span><span class="sxs-lookup"><span data-stu-id="8183d-134">Save the solution by selecting **File** > **Save All**.</span></span>

## <a name="add-code-to-host-the-service"></a><span data-ttu-id="8183d-135">Hizmeti barındırmak için kod ekleme</span><span class="sxs-lookup"><span data-stu-id="8183d-135">Add code to host the service</span></span>

<span data-ttu-id="8183d-136">Hizmeti barındırmak için aşağıdaki adımları yapmak için kod eklersiniz:</span><span class="sxs-lookup"><span data-stu-id="8183d-136">To host the service, you add code to do the following steps:</span></span>

1. <span data-ttu-id="8183d-137">Temel adres için bir URI oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8183d-137">Create a URI for the base address.</span></span>
2. <span data-ttu-id="8183d-138">Hizmeti barındırmak için bir sınıf örneği oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8183d-138">Create a class instance for hosting the service.</span></span>
3. <span data-ttu-id="8183d-139">Bir hizmet bitiş noktası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8183d-139">Create a service endpoint.</span></span>
4. <span data-ttu-id="8183d-140">Meta veri alışverişini etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="8183d-140">Enable metadata exchange.</span></span>
5. <span data-ttu-id="8183d-141">Gelen iletileri dinlemek için servis ana bilgisayarını açın.</span><span class="sxs-lookup"><span data-stu-id="8183d-141">Open the service host to listen for incoming messages.</span></span>
  
<span data-ttu-id="8183d-142">Kodda aşağıdaki değişiklikleri yapın:</span><span class="sxs-lookup"><span data-stu-id="8183d-142">Make the following changes to the code:</span></span>

1. <span data-ttu-id="8183d-143">**GettingStartedHost** projesinde **Program.cs** veya **Module1.vb** dosyasını açın ve kodunu aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="8183d-143">Open the **Program.cs** or **Module1.vb** file in the **GettingStartedHost** project and replace its code with the following code:</span></span>

    ```csharp
    using System;
    using System.ServiceModel;
    using System.ServiceModel.Description;
    using GettingStartedLib;

    namespace GettingStartedHost
    {
        class Program
        {
            static void Main(string[] args)
            {
                // Step 1: Create a URI to serve as the base address.
                Uri baseAddress = new Uri("http://localhost:8000/GettingStarted/");

                // Step 2: Create a ServiceHost instance.
                ServiceHost selfHost = new ServiceHost(typeof(CalculatorService), baseAddress);

                try
                {
                    // Step 3: Add a service endpoint.
                    selfHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), "CalculatorService");

                    // Step 4: Enable metadata exchange.
                    ServiceMetadataBehavior smb = new ServiceMetadataBehavior();
                    smb.HttpGetEnabled = true;
                    selfHost.Description.Behaviors.Add(smb)    ;

                    // Step 5: Start the service.
                    selfHost.Open();
                    Console.WriteLine("The service is ready.");

                    // Close the ServiceHost to stop the service.
                    Console.WriteLine("Press <Enter> to terminate the service.");
                    Console.WriteLine();
                    Console.ReadLine();
                    selfHost.Close();
                }
                catch (CommunicationException ce)
                {
                    Console.WriteLine("An exception occurred: {0}", ce.Message);
                    selfHost.Abort();
                }
            }
        }
    }
    ```

    ```vb
    Imports System.ServiceModel
    Imports System.ServiceModel.Description
    Imports GettingStartedLib.GettingStartedLib

    Module Service

        Class Program
            Shared Sub Main()
                ' Step 1: Create a URI to serve as the base address.
                Dim baseAddress As New Uri("http://localhost:8000/GettingStarted/")

                ' Step 2: Create a ServiceHost instance.
                Dim selfHost As New ServiceHost(GetType(CalculatorService), baseAddress)
               Try

                    ' Step 3: Add a service endpoint.
                    selfHost.AddServiceEndpoint( _
                        GetType(ICalculator), _
                        New WSHttpBinding(), _
                        "CalculatorService")

                    ' Step 4: Enable metadata exchange.
                    Dim smb As New ServiceMetadataBehavior()
                    smb.HttpGetEnabled = True
                    selfHost.Description.Behaviors.Add(smb)

                    ' Step 5: Start the service.
                    selfHost.Open()
                    Console.WriteLine("The service is ready.")

                    ' Close the ServiceHost to stop the service.
                    Console.WriteLine("Press <Enter> to terminate the service.")
                    Console.WriteLine()
                    Console.ReadLine()
                    selfHost.Close()

                Catch ce As CommunicationException
                    Console.WriteLine("An exception occurred: {0}", ce.Message)
                    selfHost.Abort()
                End Try
            End Sub
        End Class

    End Module
    ```

    <span data-ttu-id="8183d-144">Bu kodun nasıl çalıştığı hakkında bilgi için [Hizmet barındırma programı adımlarını](#service-hosting-program-steps)görün.</span><span class="sxs-lookup"><span data-stu-id="8183d-144">For information about how this code works, see [Service hosting program steps](#service-hosting-program-steps).</span></span>

2. <span data-ttu-id="8183d-145">Proje özelliklerini güncelleştirin:</span><span class="sxs-lookup"><span data-stu-id="8183d-145">Update the project properties:</span></span>

   1. <span data-ttu-id="8183d-146">Solution **Explorer** penceresinde, **GettingStartedHost** klasörünü seçin ve ardından kısayol menüsünden **Özellikler'i** seçin.</span><span class="sxs-lookup"><span data-stu-id="8183d-146">In the **Solution Explorer** window, select the **GettingStartedHost** folder, and then select **Properties** from the shortcut menu.</span></span>

   2. <span data-ttu-id="8183d-147">**GettingStartedHost** özellikleri sayfasında **Uygulama** sekmesini seçin:</span><span class="sxs-lookup"><span data-stu-id="8183d-147">On the **GettingStartedHost** properties page, select the **Application** tab:</span></span>

      - <span data-ttu-id="8183d-148">C# projeleri için **Başlangıç nesne** listesinden **GettingStartedHost.Program'ı** seçin.</span><span class="sxs-lookup"><span data-stu-id="8183d-148">For C# projects, select **GettingStartedHost.Program** from the **Startup object** list.</span></span>

      - <span data-ttu-id="8183d-149">Visual Basic projeleri için **Başlangıç nesne** listesinden **Service.Program'ı** seçin.</span><span class="sxs-lookup"><span data-stu-id="8183d-149">For Visual Basic projects, select **Service.Program** from the **Startup object** list.</span></span>

   3. <span data-ttu-id="8183d-150">**Dosya** menüsünden **Tümünü Kaydet'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="8183d-150">From the **File** menu, select **Save All**.</span></span>

## <a name="verify-the-service-is-working"></a><span data-ttu-id="8183d-151">Hizmetin çalıştığını doğrulayın</span><span class="sxs-lookup"><span data-stu-id="8183d-151">Verify the service is working</span></span>

1. <span data-ttu-id="8183d-152">Çözümü oluşturun ve Ardından Visual Studio'nun içinden **GettingStartedHost** konsol uygulamasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="8183d-152">Build the solution, and then run the **GettingStartedHost** console application from inside Visual Studio.</span></span>

    <span data-ttu-id="8183d-153">Hizmet yönetici ayrıcalıkları ile çalıştırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8183d-153">The service must be run with administrator privileges.</span></span> <span data-ttu-id="8183d-154">Visual Studio'yu yönetici ayrıcalıklarıyla açtığınız için, **Visual Studio'da GettingStartedHost'u** çalıştırdığınızda, uygulama yönetici ayrıcalıklarıyla da çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="8183d-154">Because you opened Visual Studio with administrator privileges, when you run **GettingStartedHost** in Visual Studio, the application is run with administrator privileges as well.</span></span> <span data-ttu-id="8183d-155">Alternatif olarak, yönetici olarak yeni bir komut istemi açabilir (kısayol menüsünden yönetici olarak **Daha Fazla** > **Çalıştır'ı** seçin) ve içinde **GettingStartedHost.exe'yi** çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8183d-155">As an alternative, you can open a new command prompt as an administrator (select **More** > **Run as administrator** from the shortcut menu) and run **GettingStartedHost.exe** within it.</span></span>

2. <span data-ttu-id="8183d-156">Bir web tarayıcısı açın ve hizmetin `http://localhost:8000/GettingStarted/CalculatorService`sayfasına 'da göz atın.</span><span class="sxs-lookup"><span data-stu-id="8183d-156">Open a web browser and browse to the service's page at `http://localhost:8000/GettingStarted/CalculatorService`.</span></span>

   > [!NOTE]
   > <span data-ttu-id="8183d-157">Bu gibi hizmetler dinlemek için makineye HTTP adresleri kaydetmek için uygun izni gerektirir.</span><span class="sxs-lookup"><span data-stu-id="8183d-157">Services such as this one require the proper permission to register HTTP addresses on the machine for listening.</span></span> <span data-ttu-id="8183d-158">Yönetici hesaplarıbu izne sahiptir, ancak yönetici olmayan hesaplara HTTP ad alanları için izin verilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="8183d-158">Administrator accounts have this permission, but non-administrator accounts must be granted permission for HTTP namespaces.</span></span> <span data-ttu-id="8183d-159">Ad alanı rezervasyonlarını yapılandırma hakkında daha fazla bilgi için [http ve HTTPS yapılandırma](feature-details/configuring-http-and-https.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="8183d-159">For more information about how to configure namespace reservations, see [Configuring HTTP and HTTPS](feature-details/configuring-http-and-https.md).</span></span>

## <a name="service-hosting-program-steps"></a><span data-ttu-id="8183d-160">Hizmet barındırma programı adımları</span><span class="sxs-lookup"><span data-stu-id="8183d-160">Service hosting program steps</span></span>

<span data-ttu-id="8183d-161">Hizmeti barındırmak için eklediğiniz koddaki adımlar aşağıdaki gibi açıklanmıştır:</span><span class="sxs-lookup"><span data-stu-id="8183d-161">The steps in the code you added to host the service are described as follows:</span></span>

- <span data-ttu-id="8183d-162">**Adım 1**: Hizmetin `Uri` temel adresini tutmak için sınıfın bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8183d-162">**Step 1**: Create an instance of the `Uri` class to hold the base address of the service.</span></span> <span data-ttu-id="8183d-163">Temel adres içeren bir URL'de, hizmeti tanımlayan isteğe bağlı bir URI vardır.</span><span class="sxs-lookup"><span data-stu-id="8183d-163">A URL that contains a base address has an optional URI that identifies a service.</span></span> <span data-ttu-id="8183d-164">Temel adres aşağıdaki gibi biçimlendirilir: `<transport>://<machine-name or domain><:optional port #>/<optional URI segment>`.</span><span class="sxs-lookup"><span data-stu-id="8183d-164">The base address is formatted as follows: `<transport>://<machine-name or domain><:optional port #>/<optional URI segment>`.</span></span> <span data-ttu-id="8183d-165">Hesap makinesi hizmetinin temel adresi HTTP transport, localhost, port 8000 ve URI segmenti Olan GettingStarted'ı kullanır.</span><span class="sxs-lookup"><span data-stu-id="8183d-165">The base address for the calculator service uses the HTTP transport, localhost, port 8000, and the URI segment, GettingStarted.</span></span>

- <span data-ttu-id="8183d-166">**Adım 2**: Hizmeti <xref:System.ServiceModel.ServiceHost> barındırmak için kullandığınız sınıfın bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8183d-166">**Step 2**: Create an instance of the <xref:System.ServiceModel.ServiceHost> class, which you use to host the service.</span></span> <span data-ttu-id="8183d-167">Oluşturucu iki parametre alır: hizmet sözleşmesini uygulayan sınıfın türü ve hizmetin temel adresi.</span><span class="sxs-lookup"><span data-stu-id="8183d-167">The constructor takes two parameters: the type of the class that implements the service contract and the base address of the service.</span></span>

- <span data-ttu-id="8183d-168">**Adım 3**: <xref:System.ServiceModel.Description.ServiceEndpoint> Bir örnek oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8183d-168">**Step 3**: Create a <xref:System.ServiceModel.Description.ServiceEndpoint> instance.</span></span> <span data-ttu-id="8183d-169">Hizmet bitiş noktası bir adres, bağlama ve hizmet sözleşmesinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="8183d-169">A service endpoint is composed of an address, a binding, and a service contract.</span></span> <span data-ttu-id="8183d-170">Oluşturucu, <xref:System.ServiceModel.Description.ServiceEndpoint> hizmet sözleşmesi arabirim türü, bir bağlama ve bir adresten oluşur.</span><span class="sxs-lookup"><span data-stu-id="8183d-170">The <xref:System.ServiceModel.Description.ServiceEndpoint> constructor is composed of the service contract interface type, a binding, and an address.</span></span> <span data-ttu-id="8183d-171">Hizmet sözleşmesi, `ICalculator`hizmet türünde tanımladığınız ve uyguladığınız sözleşmedir.</span><span class="sxs-lookup"><span data-stu-id="8183d-171">The service contract is `ICalculator`, which you defined and implement in the service type.</span></span> <span data-ttu-id="8183d-172">Bu örnek için <xref:System.ServiceModel.WSHttpBinding>bağlayıcı, yerleşik bir bağlama ve WS-\* belirtimlerine uygun uç noktalara bağlanır.</span><span class="sxs-lookup"><span data-stu-id="8183d-172">The binding for this sample is <xref:System.ServiceModel.WSHttpBinding>, which is a built-in binding and connects to endpoints that conform to the WS-\* specifications.</span></span> <span data-ttu-id="8183d-173">WCF ciltleri hakkında daha fazla bilgi için [WCF bağlamalarına genel bakış](bindings-overview.md)alabın.</span><span class="sxs-lookup"><span data-stu-id="8183d-173">For more information about WCF bindings, see [WCF bindings overview](bindings-overview.md).</span></span> <span data-ttu-id="8183d-174">Bitiş noktasını belirlemek için adresi temel adrese eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="8183d-174">You append the address to the base address to identify the endpoint.</span></span> <span data-ttu-id="8183d-175">Kod, adresi Hesap Makinesi Hizmeti olarak ve bitiş noktası için `http://localhost:8000/GettingStarted/CalculatorService`tam nitelikli adresi olarak belirtir.</span><span class="sxs-lookup"><span data-stu-id="8183d-175">The code specifies the address as CalculatorService and the fully qualified address for the endpoint as `http://localhost:8000/GettingStarted/CalculatorService`.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="8183d-176">.NET Framework Version 4 ve sonraki sürümler için bir hizmet bitiş noktası eklemek isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="8183d-176">For .NET Framework Version 4 and later, adding a service endpoint is optional.</span></span> <span data-ttu-id="8183d-177">Bu sürümler için, kodunuzu veya yapılandırmanızı eklemezseniz, WCF hizmet tarafından uygulanan her temel adres ve sözleşme kombinasyonu için bir varsayılan bitiş noktası ekler.</span><span class="sxs-lookup"><span data-stu-id="8183d-177">For these versions, if you don't add your code or configuration, WCF adds one default endpoint for each combination of base address and contract implemented by the service.</span></span> <span data-ttu-id="8183d-178">Varsayılan uç noktalar hakkında daha fazla bilgi için [bkz.](specifying-an-endpoint-address.md)</span><span class="sxs-lookup"><span data-stu-id="8183d-178">For more information about default endpoints, see [Specifying an endpoint address](specifying-an-endpoint-address.md).</span></span> <span data-ttu-id="8183d-179">Varsayılan uç noktalar, bağlamalar ve davranışlar hakkında daha fazla bilgi için WCF hizmetleri için [Basitleştirilmiş yapılandırma](simplified-configuration.md) ve [Basitleştirilmiş yapılandırmaya](samples/simplified-configuration-for-wcf-services.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="8183d-179">For more information about default endpoints, bindings, and behaviors, see [Simplified configuration](simplified-configuration.md) and [Simplified configuration for WCF services](samples/simplified-configuration-for-wcf-services.md).</span></span>

- <span data-ttu-id="8183d-180">**Adım 4**: Meta veri alışverişini etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="8183d-180">**Step 4**: Enable metadata exchange.</span></span> <span data-ttu-id="8183d-181">İstemciler, hizmet işlemlerini çağırmak için yakınlık oluşturmak için meta veri alışverişini kullanır.</span><span class="sxs-lookup"><span data-stu-id="8183d-181">Clients use metadata exchange to generate proxies for calling the service operations.</span></span> <span data-ttu-id="8183d-182">Meta veri alışverişini <xref:System.ServiceModel.Description.ServiceMetadataBehavior> etkinleştirmek için, `true`bir örnek `ServiceMetadataBehavior` oluşturun, <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> özelliğini <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled> <xref:System.ServiceModel.ServiceHost> "" olarak ayarlayın ve nesneyi örnek koleksiyonuna ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8183d-182">To enable metadata exchange, create a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance, set its <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled> property to `true`, and add the `ServiceMetadataBehavior` object to the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> collection of the <xref:System.ServiceModel.ServiceHost> instance.</span></span>

- <span data-ttu-id="8183d-183">**Adım 5** <xref:System.ServiceModel.ServiceHost> : Gelen iletileri dinlemek için açın.</span><span class="sxs-lookup"><span data-stu-id="8183d-183">**Step 5**: Open <xref:System.ServiceModel.ServiceHost> to listen for incoming messages.</span></span> <span data-ttu-id="8183d-184">Uygulama **Enter**tuşuna basmanızı bekler.</span><span class="sxs-lookup"><span data-stu-id="8183d-184">The application waits for you to press **Enter**.</span></span> <span data-ttu-id="8183d-185">Uygulama instantiates <xref:System.ServiceModel.ServiceHost>sonra, bir try /catch bloğu yürütür.</span><span class="sxs-lookup"><span data-stu-id="8183d-185">After the application instantiates <xref:System.ServiceModel.ServiceHost>, it executes a try/catch block.</span></span> <span data-ttu-id="8183d-186">Tarafından atılan özel durumları güvenli bir <xref:System.ServiceModel.ServiceHost>şekilde yakalamak hakkında daha fazla bilgi [için WCF istemci kaynaklarını serbest bırakmak için Kapat ve İptal'i kullan'a](samples/use-close-abort-release-wcf-client-resources.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="8183d-186">For more information about safely catching exceptions thrown by <xref:System.ServiceModel.ServiceHost>, see [Use Close and Abort to release WCF client resources](samples/use-close-abort-release-wcf-client-resources.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8183d-187">Bir WCF hizmet kitaplığı eklediğinizde, bir hizmet ana bilgisayar başlatarak hata ayıklama nız durumunda Visual Studio, bu kitap sizin için barındırır.</span><span class="sxs-lookup"><span data-stu-id="8183d-187">When you add a WCF service library, Visual Studio hosts it for you if you debug it by starting a service host.</span></span> <span data-ttu-id="8183d-188">Çakışmaları önlemek için Visual Studio'nun WCF hizmet kitaplığını barındırmasını engelleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8183d-188">To avoid conflicts, you can prevent Visual Studio from hosting the WCF service library.</span></span>
>
> 1. <span data-ttu-id="8183d-189">**Solution Explorer'da** **GettingStartedLib** projesini seçin ve kısayol menüsünden **Özellikler'i** seçin.</span><span class="sxs-lookup"><span data-stu-id="8183d-189">Select the **GettingStartedLib** project in **Solution Explorer** and choose **Properties** from the shortcut menu.</span></span>
> 2. <span data-ttu-id="8183d-190">Aynı çözümde başka bir projehataayıklarken **WCF Seçenekleri'ni** seçin ve **WCF Hizmet Ana Bilgisayarını Başlat'ın denetimini**kaldırın.</span><span class="sxs-lookup"><span data-stu-id="8183d-190">Select **WCF Options** and uncheck **Start WCF Service Host when debugging another project in the same solution**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="8183d-191">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="8183d-191">Next steps</span></span>

<span data-ttu-id="8183d-192">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="8183d-192">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="8183d-193">Bir WCF hizmeti barındırmak için bir konsol uygulaması projesi oluşturun ve yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="8183d-193">Create and configure a console app project for hosting a WCF service.</span></span>
> - <span data-ttu-id="8183d-194">WCF hizmetini barındırmak için kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8183d-194">Add code to host the WCF service.</span></span>
> - <span data-ttu-id="8183d-195">Yapılandırma dosyasını güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="8183d-195">Update the configuration file.</span></span>
> - <span data-ttu-id="8183d-196">WCF hizmetini başlatın ve çalıştığını doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="8183d-196">Start the WCF service and verify it's running.</span></span>

<span data-ttu-id="8183d-197">WCF istemcisi oluşturmayı öğrenmek için bir sonraki öğreticiye ilerleyin.</span><span class="sxs-lookup"><span data-stu-id="8183d-197">Advance to the next tutorial to learn how to create a WCF client.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8183d-198">Öğretici: WCF istemcisi oluşturma</span><span class="sxs-lookup"><span data-stu-id="8183d-198">Tutorial: Create a WCF client</span></span>](how-to-create-a-wcf-client.md)
