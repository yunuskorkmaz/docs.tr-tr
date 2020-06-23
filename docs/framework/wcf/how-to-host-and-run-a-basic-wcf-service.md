---
title: 'Öğretici: temel bir Windows Communication Foundation hizmetini barındırma ve çalıştırma'
description: WCF uygulaması oluşturmaya başlamanıza yardımcı olan bir makale serisinin parçası olarak bir WCF hizmetini bir konsol uygulamasında nasıl barındıracağınızı öğrenin.
ms.date: 03/19/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF services [WCF]
- WCF services [WCF], running
ms.assetid: 31774d36-923b-4e2d-812e-aa190127266f
ms.openlocfilehash: 5318991087e71430523681d601d3b38c4513027b
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246143"
---
# <a name="tutorial-host-and-run-a-basic-windows-communication-foundation-service"></a><span data-ttu-id="1c68b-103">Öğretici: temel bir Windows Communication Foundation hizmetini barındırma ve çalıştırma</span><span class="sxs-lookup"><span data-stu-id="1c68b-103">Tutorial: Host and run a basic Windows Communication Foundation service</span></span>

<span data-ttu-id="1c68b-104">Bu öğreticide, temel bir Windows Communication Foundation (WCF) uygulaması oluşturmak için gereken üçüncü beş görev açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1c68b-104">This tutorial describes the third of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="1c68b-105">Öğreticilere genel bakış için bkz. [öğretici: Windows Communication Foundation uygulamalarla çalışmaya başlama](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="1c68b-105">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="1c68b-106">WCF uygulaması oluşturmaya yönelik sonraki görev bir konsol uygulamasında bir WCF hizmeti barındırmanıza yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="1c68b-106">The next task for creating a WCF application is to host a WCF service in a console application.</span></span> <span data-ttu-id="1c68b-107">Bir WCF hizmeti, her biri bir veya daha fazla hizmet işlemi sunan bir veya daha fazla *uç nokta*sunar.</span><span class="sxs-lookup"><span data-stu-id="1c68b-107">A WCF service exposes one or more *endpoints*, each of which exposes one or more service operations.</span></span> <span data-ttu-id="1c68b-108">Hizmet uç noktası aşağıdaki bilgileri belirtir:</span><span class="sxs-lookup"><span data-stu-id="1c68b-108">A service endpoint specifies the following information:</span></span>

- <span data-ttu-id="1c68b-109">Hizmeti bulabileceğiniz bir adres.</span><span class="sxs-lookup"><span data-stu-id="1c68b-109">An address where you can find the service.</span></span>
- <span data-ttu-id="1c68b-110">İstemcinin hizmetle nasıl iletişim kurması gerektiğini açıklayan bilgileri içeren bir bağlama.</span><span class="sxs-lookup"><span data-stu-id="1c68b-110">A binding that contains the information that describes how a client must communicate with the service.</span></span>
- <span data-ttu-id="1c68b-111">Hizmetin istemcilerine sağladığı işlevselliği tanımlayan bir anlaşma.</span><span class="sxs-lookup"><span data-stu-id="1c68b-111">A contract that defines the functionality that the service provides to its clients.</span></span>

<span data-ttu-id="1c68b-112">Bu öğreticide aşağıdakilerin nasıl yapılacağını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="1c68b-112">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="1c68b-113">WCF hizmetini barındırmak için bir konsol uygulaması projesi oluşturun ve yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="1c68b-113">Create and configure a console app project for hosting a WCF service.</span></span>
> - <span data-ttu-id="1c68b-114">WCF hizmetini barındırmak için kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1c68b-114">Add code to host the WCF service.</span></span>
> - <span data-ttu-id="1c68b-115">Yapılandırma dosyasını güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="1c68b-115">Update the configuration file.</span></span>
> - <span data-ttu-id="1c68b-116">WCF hizmetini başlatın ve çalıştığını doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="1c68b-116">Start the WCF service and verify it's running.</span></span>

## <a name="create-and-configure-a-console-app-project-for-hosting-the-service"></a><span data-ttu-id="1c68b-117">Hizmeti barındırmak için bir konsol uygulaması projesi oluşturma ve yapılandırma</span><span class="sxs-lookup"><span data-stu-id="1c68b-117">Create and configure a console app project for hosting the service</span></span>

1. <span data-ttu-id="1c68b-118">Visual Studio 'da bir konsol uygulaması projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="1c68b-118">Create a console app project in Visual Studio:</span></span>

    1. <span data-ttu-id="1c68b-119">**Dosya** menüsünde **Open**  >  **Proje/çözüm** aç ' ı seçin ve daha önce oluşturduğunuz **gettingstarted** çözümüne (*gettingstarted. sln*) gidin.</span><span class="sxs-lookup"><span data-stu-id="1c68b-119">From the **File** menu, select **Open** > **Project/Solution** and browse to the **GettingStarted** solution you previously created (*GettingStarted.sln*).</span></span> <span data-ttu-id="1c68b-120">**Aç**'ı seçin.</span><span class="sxs-lookup"><span data-stu-id="1c68b-120">Select **Open**.</span></span>

    2. <span data-ttu-id="1c68b-121">**Görünüm** menüsünden **Çözüm Gezgini**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="1c68b-121">From the **View** menu, select **Solution Explorer**.</span></span>

    3. <span data-ttu-id="1c68b-122">**Çözüm Gezgini** penceresinde, **gettingstarted** çözümünü (üst düğüm) seçin ve sonra **Add**  >  kısayol menüsünden**Yeni proje** Ekle ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="1c68b-122">In the **Solution Explorer** window, select the **GettingStarted** solution (top node), and then select **Add** > **New Project** from the shortcut menu.</span></span>

    4. <span data-ttu-id="1c68b-123">**Yeni Proje Ekle** penceresinde, sol taraftaki **Visual C#** veya **Visual Basic**altındaki **Windows Masaüstü** kategorisini seçin.</span><span class="sxs-lookup"><span data-stu-id="1c68b-123">In the **Add New Project** window, on the left side, select the **Windows Desktop** category under **Visual C#** or **Visual Basic**.</span></span>

    5. <span data-ttu-id="1c68b-124">**Konsol uygulaması (.NET Framework)** şablonunu seçin ve **ad**Için *GettingStartedHost* yazın.</span><span class="sxs-lookup"><span data-stu-id="1c68b-124">Select the **Console App (.NET Framework)** template, and enter *GettingStartedHost* for the **Name**.</span></span> <span data-ttu-id="1c68b-125">**Tamam**’ı seçin.</span><span class="sxs-lookup"><span data-stu-id="1c68b-125">Select **OK**.</span></span>

2. <span data-ttu-id="1c68b-126">**GettingStartedHost** projesinde **GettingStartedLib** projesine bir başvuru ekleyin:</span><span class="sxs-lookup"><span data-stu-id="1c68b-126">Add a reference in the **GettingStartedHost** project to the **GettingStartedLib** project:</span></span>

    1. <span data-ttu-id="1c68b-127">**Çözüm Gezgini** penceresinde, **GettingStartedHost** projesi altındaki **Başvurular** klasörünü seçin ve sonra kısayol menüsünden **Başvuru Ekle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="1c68b-127">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedHost** project, and then select **Add Reference** from the shortcut menu.</span></span>

    2. <span data-ttu-id="1c68b-128">**Başvuru Ekle** iletişim kutusunda, pencerenin sol tarafındaki **Projeler** altında **çözüm**' ü seçin.</span><span class="sxs-lookup"><span data-stu-id="1c68b-128">In the **Add Reference** dialog, under **Projects** on the left side of the window, select **Solution**.</span></span>

    3. <span data-ttu-id="1c68b-129">Pencerenin orta bölümündeki **GettingStartedLib** ' i seçin ve ardından **Tamam**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="1c68b-129">Select **GettingStartedLib** in the center section of the window, and then select **OK**.</span></span>

       <span data-ttu-id="1c68b-130">Bu eylem, **GettingStartedLib** projesinde tanımlanan türlerin **GettingStartedHost** projesi için kullanılabilir olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="1c68b-130">This action makes the types defined in the **GettingStartedLib** project available to the **GettingStartedHost** project.</span></span>

3. <span data-ttu-id="1c68b-131">**GettingStartedHost** projesinde derlemeye bir başvuru ekleyin <xref:System.ServiceModel> :</span><span class="sxs-lookup"><span data-stu-id="1c68b-131">Add a reference in the **GettingStartedHost** project to the <xref:System.ServiceModel> assembly:</span></span>

    1. <span data-ttu-id="1c68b-132">**Çözüm Gezgini** penceresinde, **GettingStartedHost** projesi altındaki **Başvurular** klasörünü seçin ve sonra kısayol menüsünden **Başvuru Ekle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="1c68b-132">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedHost** project, and then select **Add Reference** from the shortcut menu.</span></span>

    2. <span data-ttu-id="1c68b-133">**Başvuru Ekle** penceresinde pencerenin sol tarafındaki **derlemeler** altında **Framework**' ü seçin.</span><span class="sxs-lookup"><span data-stu-id="1c68b-133">In the **Add Reference** window, under **Assemblies** on the left side of the window, select **Framework**.</span></span>

    3. <span data-ttu-id="1c68b-134">**System. ServiceModel**' i seçin ve ardından **Tamam**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="1c68b-134">Select **System.ServiceModel**, and then select **OK**.</span></span>

    4. <span data-ttu-id="1c68b-135">**Dosya**  >  **Tümünü Kaydet**' i seçerek çözümü kaydedin.</span><span class="sxs-lookup"><span data-stu-id="1c68b-135">Save the solution by selecting **File** > **Save All**.</span></span>

## <a name="add-code-to-host-the-service"></a><span data-ttu-id="1c68b-136">Hizmeti barındırmak için kod ekleme</span><span class="sxs-lookup"><span data-stu-id="1c68b-136">Add code to host the service</span></span>

<span data-ttu-id="1c68b-137">Hizmeti barındırmak için aşağıdaki adımları uygulamak üzere kod ekleyin:</span><span class="sxs-lookup"><span data-stu-id="1c68b-137">To host the service, you add code to do the following steps:</span></span>

1. <span data-ttu-id="1c68b-138">Temel adres için bir URI oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1c68b-138">Create a URI for the base address.</span></span>
2. <span data-ttu-id="1c68b-139">Hizmeti barındırmak için bir sınıf örneği oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1c68b-139">Create a class instance for hosting the service.</span></span>
3. <span data-ttu-id="1c68b-140">Hizmet uç noktası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1c68b-140">Create a service endpoint.</span></span>
4. <span data-ttu-id="1c68b-141">Meta veri değişimini etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="1c68b-141">Enable metadata exchange.</span></span>
5. <span data-ttu-id="1c68b-142">Gelen iletileri dinlemek için hizmet ana bilgisayarını açın.</span><span class="sxs-lookup"><span data-stu-id="1c68b-142">Open the service host to listen for incoming messages.</span></span>
  
<span data-ttu-id="1c68b-143">Kodda aşağıdaki değişiklikleri yapın:</span><span class="sxs-lookup"><span data-stu-id="1c68b-143">Make the following changes to the code:</span></span>

1. <span data-ttu-id="1c68b-144">**GettingStartedHost** projesinde **program.cs** veya **Module1. vb** dosyasını açın ve kodunu aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="1c68b-144">Open the **Program.cs** or **Module1.vb** file in the **GettingStartedHost** project and replace its code with the following code:</span></span>

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
                    selfHost.Description.Behaviors.Add(smb);

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

    <span data-ttu-id="1c68b-145">Bu kodun nasıl çalıştığı hakkında bilgi için bkz. [hizmet barındırma programı adımları](#service-hosting-program-steps).</span><span class="sxs-lookup"><span data-stu-id="1c68b-145">For information about how this code works, see [Service hosting program steps](#service-hosting-program-steps).</span></span>

2. <span data-ttu-id="1c68b-146">Proje özelliklerini güncelleştirin:</span><span class="sxs-lookup"><span data-stu-id="1c68b-146">Update the project properties:</span></span>

   1. <span data-ttu-id="1c68b-147">**Çözüm Gezgini** penceresinde **GettingStartedHost** klasörünü seçin ve sonra kısayol menüsünden **Özellikler** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="1c68b-147">In the **Solution Explorer** window, select the **GettingStartedHost** folder, and then select **Properties** from the shortcut menu.</span></span>

   2. <span data-ttu-id="1c68b-148">**GettingStartedHost** özellikleri sayfasında **uygulama** sekmesini seçin:</span><span class="sxs-lookup"><span data-stu-id="1c68b-148">On the **GettingStartedHost** properties page, select the **Application** tab:</span></span>

      - <span data-ttu-id="1c68b-149">C# projeleri için **Başlangıç nesne** listesinden **GettingStartedHost. program** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="1c68b-149">For C# projects, select **GettingStartedHost.Program** from the **Startup object** list.</span></span>

      - <span data-ttu-id="1c68b-150">Visual Basic projeleri için **Başlangıç nesne** listesinden **Service. program** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="1c68b-150">For Visual Basic projects, select **Service.Program** from the **Startup object** list.</span></span>

   3. <span data-ttu-id="1c68b-151">**Dosya** menüsünde **Tümünü Kaydet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="1c68b-151">From the **File** menu, select **Save All**.</span></span>

## <a name="verify-the-service-is-working"></a><span data-ttu-id="1c68b-152">Hizmetin çalıştığını doğrulama</span><span class="sxs-lookup"><span data-stu-id="1c68b-152">Verify the service is working</span></span>

1. <span data-ttu-id="1c68b-153">Çözümü derleyin ve ardından Visual Studio içinden **GettingStartedHost** konsol uygulamasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1c68b-153">Build the solution, and then run the **GettingStartedHost** console application from inside Visual Studio.</span></span>

    <span data-ttu-id="1c68b-154">Hizmetin yönetici ayrıcalıklarıyla çalıştırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1c68b-154">The service must be run with administrator privileges.</span></span> <span data-ttu-id="1c68b-155">Visual Studio 'Yu yönetici ayrıcalıklarıyla açtığınızdan, Visual Studio 'da **GettingStartedHost** çalıştırdığınızda uygulama da yönetici ayrıcalıklarıyla çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="1c68b-155">Because you opened Visual Studio with administrator privileges, when you run **GettingStartedHost** in Visual Studio, the application is run with administrator privileges as well.</span></span> <span data-ttu-id="1c68b-156">Alternatif olarak, yeni bir komut istemi 'ni yönetici olarak açabilirsiniz (kısayol menüsünden **daha fazla**  >  **Çalıştır Yöneticisi** ' ni seçin) ve içinde **GettingStartedHost.exe** çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1c68b-156">As an alternative, you can open a new command prompt as an administrator (select **More** > **Run as administrator** from the shortcut menu) and run **GettingStartedHost.exe** within it.</span></span>

2. <span data-ttu-id="1c68b-157">Bir Web tarayıcısı açın ve konumundaki hizmetin sayfasına gidin `http://localhost:8000/GettingStarted/CalculatorService` .</span><span class="sxs-lookup"><span data-stu-id="1c68b-157">Open a web browser and browse to the service's page at `http://localhost:8000/GettingStarted/CalculatorService`.</span></span>

   > [!NOTE]
   > <span data-ttu-id="1c68b-158">Bu gibi hizmetler, dinlemek üzere makineye HTTP adreslerini kaydetmek için uygun izni gerektirir.</span><span class="sxs-lookup"><span data-stu-id="1c68b-158">Services such as this one require the proper permission to register HTTP addresses on the machine for listening.</span></span> <span data-ttu-id="1c68b-159">Yönetici hesaplarında bu izin vardır ancak yönetici olmayan hesaplara HTTP ad alanları için izin verilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="1c68b-159">Administrator accounts have this permission, but non-administrator accounts must be granted permission for HTTP namespaces.</span></span> <span data-ttu-id="1c68b-160">Ad alanı ayırmalarını yapılandırma hakkında daha fazla bilgi için bkz. [http ve https yapılandırma](feature-details/configuring-http-and-https.md).</span><span class="sxs-lookup"><span data-stu-id="1c68b-160">For more information about how to configure namespace reservations, see [Configuring HTTP and HTTPS](feature-details/configuring-http-and-https.md).</span></span>

## <a name="service-hosting-program-steps"></a><span data-ttu-id="1c68b-161">Hizmet barındırma programı adımları</span><span class="sxs-lookup"><span data-stu-id="1c68b-161">Service hosting program steps</span></span>

<span data-ttu-id="1c68b-162">Hizmeti barındırmak için eklediğiniz koddaki adımlar aşağıdaki gibi açıklanmıştır:</span><span class="sxs-lookup"><span data-stu-id="1c68b-162">The steps in the code you added to host the service are described as follows:</span></span>

- <span data-ttu-id="1c68b-163">**1. adım**: `Uri` hizmetin temel adresini tutmak için sınıfın bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1c68b-163">**Step 1**: Create an instance of the `Uri` class to hold the base address of the service.</span></span> <span data-ttu-id="1c68b-164">Temel adresi içeren bir URL 'nin bir hizmeti tanımlayan isteğe bağlı bir URI 'SI vardır.</span><span class="sxs-lookup"><span data-stu-id="1c68b-164">A URL that contains a base address has an optional URI that identifies a service.</span></span> <span data-ttu-id="1c68b-165">Taban adresi şu şekilde biçimlendirilir: `<transport>://<machine-name or domain><:optional port #>/<optional URI segment>` .</span><span class="sxs-lookup"><span data-stu-id="1c68b-165">The base address is formatted as follows: `<transport>://<machine-name or domain><:optional port #>/<optional URI segment>`.</span></span> <span data-ttu-id="1c68b-166">Hesaplayıcı hizmeti için temel adres HTTP taşıması, localhost, bağlantı noktası 8000 ve URI segmentini, GettingStarted kullanır.</span><span class="sxs-lookup"><span data-stu-id="1c68b-166">The base address for the calculator service uses the HTTP transport, localhost, port 8000, and the URI segment, GettingStarted.</span></span>

- <span data-ttu-id="1c68b-167">**2. adım**: <xref:System.ServiceModel.ServiceHost> hizmeti barındırmak için kullandığınız sınıfının bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1c68b-167">**Step 2**: Create an instance of the <xref:System.ServiceModel.ServiceHost> class, which you use to host the service.</span></span> <span data-ttu-id="1c68b-168">Oluşturucu iki parametre alır: hizmet sözleşmesini uygulayan sınıfın türü ve hizmetin taban adresi.</span><span class="sxs-lookup"><span data-stu-id="1c68b-168">The constructor takes two parameters: the type of the class that implements the service contract and the base address of the service.</span></span>

- <span data-ttu-id="1c68b-169">**3. adım**: bir <xref:System.ServiceModel.Description.ServiceEndpoint> örnek oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1c68b-169">**Step 3**: Create a <xref:System.ServiceModel.Description.ServiceEndpoint> instance.</span></span> <span data-ttu-id="1c68b-170">Hizmet uç noktası bir adresten, bağlamaya ve hizmet sözleşmesinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="1c68b-170">A service endpoint is composed of an address, a binding, and a service contract.</span></span> <span data-ttu-id="1c68b-171"><xref:System.ServiceModel.Description.ServiceEndpoint>Oluşturucu, hizmet sözleşmesi arabirim türünden, bağlamalardan ve bir adresten oluşur.</span><span class="sxs-lookup"><span data-stu-id="1c68b-171">The <xref:System.ServiceModel.Description.ServiceEndpoint> constructor is composed of the service contract interface type, a binding, and an address.</span></span> <span data-ttu-id="1c68b-172">Hizmet sözleşmesi, `ICalculator` hizmet türünde tanımladığınız ve uyguladığınız hizmet sözleşmedir.</span><span class="sxs-lookup"><span data-stu-id="1c68b-172">The service contract is `ICalculator`, which you defined and implement in the service type.</span></span> <span data-ttu-id="1c68b-173">Bu örnek için bağlama, <xref:System.ServiceModel.WSHttpBinding> yerleşik bir bağlama ve WS-\* belirtimlerine uygun uç noktalara bağlanır.</span><span class="sxs-lookup"><span data-stu-id="1c68b-173">The binding for this sample is <xref:System.ServiceModel.WSHttpBinding>, which is a built-in binding and connects to endpoints that conform to the WS-\* specifications.</span></span> <span data-ttu-id="1c68b-174">WCF bağlamaları hakkında daha fazla bilgi için bkz. [WCF bağlamalarına genel bakış](bindings-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1c68b-174">For more information about WCF bindings, see [WCF bindings overview](bindings-overview.md).</span></span> <span data-ttu-id="1c68b-175">Uç noktayı tanımlamak için adresi temel adrese ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1c68b-175">You append the address to the base address to identify the endpoint.</span></span> <span data-ttu-id="1c68b-176">Kod, adresi Hesaplatorservice olarak ve uç noktanın tam adresini olarak belirtir `http://localhost:8000/GettingStarted/CalculatorService` .</span><span class="sxs-lookup"><span data-stu-id="1c68b-176">The code specifies the address as CalculatorService and the fully qualified address for the endpoint as `http://localhost:8000/GettingStarted/CalculatorService`.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="1c68b-177">.NET Framework sürüm 4 ve üzeri için bir hizmet uç noktası eklemek isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="1c68b-177">For .NET Framework Version 4 and later, adding a service endpoint is optional.</span></span> <span data-ttu-id="1c68b-178">Bu sürümler için, kodunuzu veya yapılandırmanızı eklememeniz durumunda WCF, hizmet tarafından uygulanan her temel adres ve sözleşmenin birleşimi için bir varsayılan uç nokta ekler.</span><span class="sxs-lookup"><span data-stu-id="1c68b-178">For these versions, if you don't add your code or configuration, WCF adds one default endpoint for each combination of base address and contract implemented by the service.</span></span> <span data-ttu-id="1c68b-179">Varsayılan uç noktalar hakkında daha fazla bilgi için bkz. [bir uç nokta adresi belirtme](specifying-an-endpoint-address.md).</span><span class="sxs-lookup"><span data-stu-id="1c68b-179">For more information about default endpoints, see [Specifying an endpoint address](specifying-an-endpoint-address.md).</span></span> <span data-ttu-id="1c68b-180">Varsayılan uç noktalar, bağlamalar ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="1c68b-180">For more information about default endpoints, bindings, and behaviors, see [Simplified configuration](simplified-configuration.md) and [Simplified configuration for WCF services](samples/simplified-configuration-for-wcf-services.md).</span></span>

- <span data-ttu-id="1c68b-181">**4. adım**: meta veri değişimini etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="1c68b-181">**Step 4**: Enable metadata exchange.</span></span> <span data-ttu-id="1c68b-182">İstemciler, hizmet işlemlerini çağırmak için proxy oluşturmak üzere meta veri değişimi kullanır.</span><span class="sxs-lookup"><span data-stu-id="1c68b-182">Clients use metadata exchange to generate proxies for calling the service operations.</span></span> <span data-ttu-id="1c68b-183">Meta veri değişimini etkinleştirmek için bir <xref:System.ServiceModel.Description.ServiceMetadataBehavior> örnek oluşturun, <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled> özelliğini olarak ayarlayın `true` ve `ServiceMetadataBehavior` nesneyi <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> örnek koleksiyonuna ekleyin <xref:System.ServiceModel.ServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="1c68b-183">To enable metadata exchange, create a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance, set its <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled> property to `true`, and add the `ServiceMetadataBehavior` object to the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> collection of the <xref:System.ServiceModel.ServiceHost> instance.</span></span>

- <span data-ttu-id="1c68b-184">**5. adım**: <xref:System.ServiceModel.ServiceHost> gelen iletileri dinlemek için açın.</span><span class="sxs-lookup"><span data-stu-id="1c68b-184">**Step 5**: Open <xref:System.ServiceModel.ServiceHost> to listen for incoming messages.</span></span> <span data-ttu-id="1c68b-185">Uygulama, **ENTER**tuşuna basmanız için bekler.</span><span class="sxs-lookup"><span data-stu-id="1c68b-185">The application waits for you to press **Enter**.</span></span> <span data-ttu-id="1c68b-186">Uygulama başlatıldıktan sonra <xref:System.ServiceModel.ServiceHost> bir try/catch bloğu yürütür.</span><span class="sxs-lookup"><span data-stu-id="1c68b-186">After the application instantiates <xref:System.ServiceModel.ServiceHost>, it executes a try/catch block.</span></span> <span data-ttu-id="1c68b-187">Tarafından oluşturulan özel durumları güvenli bir şekilde yakalama hakkında daha fazla bilgi için <xref:System.ServiceModel.ServiceHost> bkz. [Close ve Abort kullanarak WCF istemci kaynaklarını serbest bırakma](samples/use-close-abort-release-wcf-client-resources.md).</span><span class="sxs-lookup"><span data-stu-id="1c68b-187">For more information about safely catching exceptions thrown by <xref:System.ServiceModel.ServiceHost>, see [Use Close and Abort to release WCF client resources](samples/use-close-abort-release-wcf-client-resources.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1c68b-188">Bir WCF hizmet kitaplığı eklediğinizde, bir hizmet ana bilgisayarı başlatarak hata ayıklaması yaparsanız, Visual Studio bunu sizin için barındırır.</span><span class="sxs-lookup"><span data-stu-id="1c68b-188">When you add a WCF service library, Visual Studio hosts it for you if you debug it by starting a service host.</span></span> <span data-ttu-id="1c68b-189">Çakışmaları önlemek için, Visual Studio 'Nun WCF hizmeti kitaplığını barındırmasını engelleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1c68b-189">To avoid conflicts, you can prevent Visual Studio from hosting the WCF service library.</span></span>
>
> 1. <span data-ttu-id="1c68b-190">**Çözüm Gezgini** ' de **GettingStartedLib** projesini seçin ve kısayol menüsünden **Özellikler** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="1c68b-190">Select the **GettingStartedLib** project in **Solution Explorer** and choose **Properties** from the shortcut menu.</span></span>
> 2. <span data-ttu-id="1c68b-191">**WCF seçeneklerini** belirleyin ve **aynı çözümdeki başka bir projede hata ayıklarken WCF hizmeti ana bilgisayarının Başlat**seçimini kaldırın.</span><span class="sxs-lookup"><span data-stu-id="1c68b-191">Select **WCF Options** and uncheck **Start WCF Service Host when debugging another project in the same solution**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="1c68b-192">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="1c68b-192">Next steps</span></span>

<span data-ttu-id="1c68b-193">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="1c68b-193">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="1c68b-194">WCF hizmetini barındırmak için bir konsol uygulaması projesi oluşturun ve yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="1c68b-194">Create and configure a console app project for hosting a WCF service.</span></span>
> - <span data-ttu-id="1c68b-195">WCF hizmetini barındırmak için kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1c68b-195">Add code to host the WCF service.</span></span>
> - <span data-ttu-id="1c68b-196">Yapılandırma dosyasını güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="1c68b-196">Update the configuration file.</span></span>
> - <span data-ttu-id="1c68b-197">WCF hizmetini başlatın ve çalıştığını doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="1c68b-197">Start the WCF service and verify it's running.</span></span>

<span data-ttu-id="1c68b-198">Bir WCF istemcisi oluşturmayı öğrenmek için bir sonraki öğreticiye ilerleyin.</span><span class="sxs-lookup"><span data-stu-id="1c68b-198">Advance to the next tutorial to learn how to create a WCF client.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1c68b-199">Öğretici: WCF istemcisi oluşturma</span><span class="sxs-lookup"><span data-stu-id="1c68b-199">Tutorial: Create a WCF client</span></span>](how-to-create-a-wcf-client.md)
