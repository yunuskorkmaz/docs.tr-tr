---
title: 'Öğretici: temel bir Windows Communication Foundation hizmetini barındırma ve çalıştırma'
ms.date: 03/19/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF services [WCF]
- WCF services [WCF], running
ms.assetid: 31774d36-923b-4e2d-812e-aa190127266f
ms.openlocfilehash: 872844487578843492e05dd2abb87b50e0bec91c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291402"
---
# <a name="tutorial-host-and-run-a-basic-windows-communication-foundation-service"></a><span data-ttu-id="a993b-102">Öğretici: temel bir Windows Communication Foundation hizmetini barındırma ve çalıştırma</span><span class="sxs-lookup"><span data-stu-id="a993b-102">Tutorial: Host and run a basic Windows Communication Foundation service</span></span>

<span data-ttu-id="a993b-103">Bu öğreticide, temel bir Windows Communication Foundation (WCF) uygulaması oluşturmak için gereken üçüncü beş görev açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a993b-103">This tutorial describes the third of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="a993b-104">Öğreticilere genel bakış için bkz. [öğretici: Windows Communication Foundation uygulamalarla çalışmaya başlama](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="a993b-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="a993b-105">WCF uygulaması oluşturmaya yönelik sonraki görev bir konsol uygulamasında bir WCF hizmeti barındırmanıza yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="a993b-105">The next task for creating a WCF application is to host a WCF service in a console application.</span></span> <span data-ttu-id="a993b-106">Bir WCF hizmeti, her biri bir veya daha fazla hizmet işlemi sunan bir veya daha fazla *uç nokta*sunar.</span><span class="sxs-lookup"><span data-stu-id="a993b-106">A WCF service exposes one or more *endpoints*, each of which exposes one or more service operations.</span></span> <span data-ttu-id="a993b-107">Hizmet uç noktası aşağıdaki bilgileri belirtir:</span><span class="sxs-lookup"><span data-stu-id="a993b-107">A service endpoint specifies the following information:</span></span>

- <span data-ttu-id="a993b-108">Hizmeti bulabileceğiniz bir adres.</span><span class="sxs-lookup"><span data-stu-id="a993b-108">An address where you can find the service.</span></span>
- <span data-ttu-id="a993b-109">İstemcinin hizmetle nasıl iletişim kurması gerektiğini açıklayan bilgileri içeren bir bağlama.</span><span class="sxs-lookup"><span data-stu-id="a993b-109">A binding that contains the information that describes how a client must communicate with the service.</span></span>
- <span data-ttu-id="a993b-110">Hizmetin istemcilerine sağladığı işlevselliği tanımlayan bir anlaşma.</span><span class="sxs-lookup"><span data-stu-id="a993b-110">A contract that defines the functionality that the service provides to its clients.</span></span>

<span data-ttu-id="a993b-111">Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="a993b-111">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="a993b-112">WCF hizmetini barındırmak için bir konsol uygulaması projesi oluşturun ve yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="a993b-112">Create and configure a console app project for hosting a WCF service.</span></span>
> - <span data-ttu-id="a993b-113">WCF hizmetini barındırmak için kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a993b-113">Add code to host the WCF service.</span></span>
> - <span data-ttu-id="a993b-114">Yapılandırma dosyasını güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="a993b-114">Update the configuration file.</span></span>
> - <span data-ttu-id="a993b-115">WCF hizmetini başlatın ve çalıştığını doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="a993b-115">Start the WCF service and verify it's running.</span></span>

## <a name="create-and-configure-a-console-app-project-for-hosting-the-service"></a><span data-ttu-id="a993b-116">Hizmeti barındırmak için bir konsol uygulaması projesi oluşturma ve yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a993b-116">Create and configure a console app project for hosting the service</span></span>

1. <span data-ttu-id="a993b-117">Visual Studio 'da bir konsol uygulaması projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="a993b-117">Create a console app project in Visual Studio:</span></span>

    1. <span data-ttu-id="a993b-118">**Dosya** menüsünde **Open**  >  **Proje/çözüm** aç ' ı seçin ve daha önce oluşturduğunuz **gettingstarted** çözümüne (*gettingstarted. sln*) gidin.</span><span class="sxs-lookup"><span data-stu-id="a993b-118">From the **File** menu, select **Open** > **Project/Solution** and browse to the **GettingStarted** solution you previously created (*GettingStarted.sln*).</span></span> <span data-ttu-id="a993b-119">**Aç**'ı seçin.</span><span class="sxs-lookup"><span data-stu-id="a993b-119">Select **Open**.</span></span>

    2. <span data-ttu-id="a993b-120">**Görünüm** menüsünden **Çözüm Gezgini**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="a993b-120">From the **View** menu, select **Solution Explorer**.</span></span>

    3. <span data-ttu-id="a993b-121">**Çözüm Gezgini** penceresinde, **gettingstarted** çözümünü (üst düğüm) seçin ve sonra **Add**  >  kısayol menüsünden**Yeni proje** Ekle ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="a993b-121">In the **Solution Explorer** window, select the **GettingStarted** solution (top node), and then select **Add** > **New Project** from the shortcut menu.</span></span>

    4. <span data-ttu-id="a993b-122">**Yeni Proje Ekle** penceresinde, sol taraftaki **Visual C#** veya **Visual Basic**altındaki **Windows Masaüstü** kategorisini seçin.</span><span class="sxs-lookup"><span data-stu-id="a993b-122">In the **Add New Project** window, on the left side, select the **Windows Desktop** category under **Visual C#** or **Visual Basic**.</span></span>

    5. <span data-ttu-id="a993b-123">**Konsol uygulaması (.NET Framework)** şablonunu seçin ve **ad**Için *GettingStartedHost* yazın.</span><span class="sxs-lookup"><span data-stu-id="a993b-123">Select the **Console App (.NET Framework)** template, and enter *GettingStartedHost* for the **Name**.</span></span> <span data-ttu-id="a993b-124">**Tamam**’ı seçin.</span><span class="sxs-lookup"><span data-stu-id="a993b-124">Select **OK**.</span></span>

2. <span data-ttu-id="a993b-125">**GettingStartedHost** projesinde **GettingStartedLib** projesine bir başvuru ekleyin:</span><span class="sxs-lookup"><span data-stu-id="a993b-125">Add a reference in the **GettingStartedHost** project to the **GettingStartedLib** project:</span></span>

    1. <span data-ttu-id="a993b-126">**Çözüm Gezgini** penceresinde, **GettingStartedHost** projesi altındaki **Başvurular** klasörünü seçin ve sonra kısayol menüsünden **Başvuru Ekle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="a993b-126">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedHost** project, and then select **Add Reference** from the shortcut menu.</span></span>

    2. <span data-ttu-id="a993b-127">**Başvuru Ekle** iletişim kutusunda, pencerenin sol tarafındaki **Projeler** altında **çözüm**' ü seçin.</span><span class="sxs-lookup"><span data-stu-id="a993b-127">In the **Add Reference** dialog, under **Projects** on the left side of the window, select **Solution**.</span></span>

    3. <span data-ttu-id="a993b-128">Pencerenin orta bölümündeki **GettingStartedLib** ' i seçin ve ardından **Tamam**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="a993b-128">Select **GettingStartedLib** in the center section of the window, and then select **OK**.</span></span>

       <span data-ttu-id="a993b-129">Bu eylem, **GettingStartedLib** projesinde tanımlanan türlerin **GettingStartedHost** projesi için kullanılabilir olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="a993b-129">This action makes the types defined in the **GettingStartedLib** project available to the **GettingStartedHost** project.</span></span>

3. <span data-ttu-id="a993b-130">**GettingStartedHost** projesinde derlemeye bir başvuru ekleyin <xref:System.ServiceModel> :</span><span class="sxs-lookup"><span data-stu-id="a993b-130">Add a reference in the **GettingStartedHost** project to the <xref:System.ServiceModel> assembly:</span></span>

    1. <span data-ttu-id="a993b-131">**Çözüm Gezgini** penceresinde, **GettingStartedHost** projesi altındaki **Başvurular** klasörünü seçin ve sonra kısayol menüsünden **Başvuru Ekle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="a993b-131">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedHost** project, and then select **Add Reference** from the shortcut menu.</span></span>

    2. <span data-ttu-id="a993b-132">**Başvuru Ekle** penceresinde pencerenin sol tarafındaki **derlemeler** altında **Framework**' ü seçin.</span><span class="sxs-lookup"><span data-stu-id="a993b-132">In the **Add Reference** window, under **Assemblies** on the left side of the window, select **Framework**.</span></span>

    3. <span data-ttu-id="a993b-133">**System. ServiceModel**' i seçin ve ardından **Tamam**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="a993b-133">Select **System.ServiceModel**, and then select **OK**.</span></span>

    4. <span data-ttu-id="a993b-134">**Dosya**  >  **Tümünü Kaydet**' i seçerek çözümü kaydedin.</span><span class="sxs-lookup"><span data-stu-id="a993b-134">Save the solution by selecting **File** > **Save All**.</span></span>

## <a name="add-code-to-host-the-service"></a><span data-ttu-id="a993b-135">Hizmeti barındırmak için kod ekleme</span><span class="sxs-lookup"><span data-stu-id="a993b-135">Add code to host the service</span></span>

<span data-ttu-id="a993b-136">Hizmeti barındırmak için aşağıdaki adımları uygulamak üzere kod ekleyin:</span><span class="sxs-lookup"><span data-stu-id="a993b-136">To host the service, you add code to do the following steps:</span></span>

1. <span data-ttu-id="a993b-137">Temel adres için bir URI oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a993b-137">Create a URI for the base address.</span></span>
2. <span data-ttu-id="a993b-138">Hizmeti barındırmak için bir sınıf örneği oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a993b-138">Create a class instance for hosting the service.</span></span>
3. <span data-ttu-id="a993b-139">Hizmet uç noktası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a993b-139">Create a service endpoint.</span></span>
4. <span data-ttu-id="a993b-140">Meta veri değişimini etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="a993b-140">Enable metadata exchange.</span></span>
5. <span data-ttu-id="a993b-141">Gelen iletileri dinlemek için hizmet ana bilgisayarını açın.</span><span class="sxs-lookup"><span data-stu-id="a993b-141">Open the service host to listen for incoming messages.</span></span>
  
<span data-ttu-id="a993b-142">Kodda aşağıdaki değişiklikleri yapın:</span><span class="sxs-lookup"><span data-stu-id="a993b-142">Make the following changes to the code:</span></span>

1. <span data-ttu-id="a993b-143">**GettingStartedHost** projesinde **program.cs** veya **Module1. vb** dosyasını açın ve kodunu aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="a993b-143">Open the **Program.cs** or **Module1.vb** file in the **GettingStartedHost** project and replace its code with the following code:</span></span>

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

    <span data-ttu-id="a993b-144">Bu kodun nasıl çalıştığı hakkında bilgi için bkz. [hizmet barındırma programı adımları](#service-hosting-program-steps).</span><span class="sxs-lookup"><span data-stu-id="a993b-144">For information about how this code works, see [Service hosting program steps](#service-hosting-program-steps).</span></span>

2. <span data-ttu-id="a993b-145">Proje özelliklerini güncelleştirin:</span><span class="sxs-lookup"><span data-stu-id="a993b-145">Update the project properties:</span></span>

   1. <span data-ttu-id="a993b-146">**Çözüm Gezgini** penceresinde **GettingStartedHost** klasörünü seçin ve sonra kısayol menüsünden **Özellikler** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="a993b-146">In the **Solution Explorer** window, select the **GettingStartedHost** folder, and then select **Properties** from the shortcut menu.</span></span>

   2. <span data-ttu-id="a993b-147">**GettingStartedHost** özellikleri sayfasında **uygulama** sekmesini seçin:</span><span class="sxs-lookup"><span data-stu-id="a993b-147">On the **GettingStartedHost** properties page, select the **Application** tab:</span></span>

      - <span data-ttu-id="a993b-148">C# projeleri için **Başlangıç nesne** listesinden **GettingStartedHost. program** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="a993b-148">For C# projects, select **GettingStartedHost.Program** from the **Startup object** list.</span></span>

      - <span data-ttu-id="a993b-149">Visual Basic projeleri için **Başlangıç nesne** listesinden **Service. program** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="a993b-149">For Visual Basic projects, select **Service.Program** from the **Startup object** list.</span></span>

   3. <span data-ttu-id="a993b-150">**Dosya** menüsünde **Tümünü Kaydet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="a993b-150">From the **File** menu, select **Save All**.</span></span>

## <a name="verify-the-service-is-working"></a><span data-ttu-id="a993b-151">Hizmetin çalıştığını doğrulama</span><span class="sxs-lookup"><span data-stu-id="a993b-151">Verify the service is working</span></span>

1. <span data-ttu-id="a993b-152">Çözümü derleyin ve ardından Visual Studio içinden **GettingStartedHost** konsol uygulamasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a993b-152">Build the solution, and then run the **GettingStartedHost** console application from inside Visual Studio.</span></span>

    <span data-ttu-id="a993b-153">Hizmetin yönetici ayrıcalıklarıyla çalıştırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a993b-153">The service must be run with administrator privileges.</span></span> <span data-ttu-id="a993b-154">Visual Studio 'Yu yönetici ayrıcalıklarıyla açtığınızdan, Visual Studio 'da **GettingStartedHost** çalıştırdığınızda uygulama da yönetici ayrıcalıklarıyla çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="a993b-154">Because you opened Visual Studio with administrator privileges, when you run **GettingStartedHost** in Visual Studio, the application is run with administrator privileges as well.</span></span> <span data-ttu-id="a993b-155">Alternatif olarak, yeni bir komut istemi 'ni yönetici olarak açabilirsiniz (kısayol menüsünden **daha fazla**  >  **Çalıştır Yöneticisi** ' ni seçin) ve içinde **GettingStartedHost. exe** ' yi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a993b-155">As an alternative, you can open a new command prompt as an administrator (select **More** > **Run as administrator** from the shortcut menu) and run **GettingStartedHost.exe** within it.</span></span>

2. <span data-ttu-id="a993b-156">Bir Web tarayıcısı açın ve konumundaki hizmetin sayfasına gidin `http://localhost:8000/GettingStarted/CalculatorService` .</span><span class="sxs-lookup"><span data-stu-id="a993b-156">Open a web browser and browse to the service's page at `http://localhost:8000/GettingStarted/CalculatorService`.</span></span>

   > [!NOTE]
   > <span data-ttu-id="a993b-157">Bu gibi hizmetler, dinlemek üzere makineye HTTP adreslerini kaydetmek için uygun izni gerektirir.</span><span class="sxs-lookup"><span data-stu-id="a993b-157">Services such as this one require the proper permission to register HTTP addresses on the machine for listening.</span></span> <span data-ttu-id="a993b-158">Yönetici hesaplarında bu izin vardır ancak yönetici olmayan hesaplara HTTP ad alanları için izin verilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="a993b-158">Administrator accounts have this permission, but non-administrator accounts must be granted permission for HTTP namespaces.</span></span> <span data-ttu-id="a993b-159">Ad alanı ayırmalarını yapılandırma hakkında daha fazla bilgi için bkz. [http ve https yapılandırma](feature-details/configuring-http-and-https.md).</span><span class="sxs-lookup"><span data-stu-id="a993b-159">For more information about how to configure namespace reservations, see [Configuring HTTP and HTTPS](feature-details/configuring-http-and-https.md).</span></span>

## <a name="service-hosting-program-steps"></a><span data-ttu-id="a993b-160">Hizmet barındırma programı adımları</span><span class="sxs-lookup"><span data-stu-id="a993b-160">Service hosting program steps</span></span>

<span data-ttu-id="a993b-161">Hizmeti barındırmak için eklediğiniz koddaki adımlar aşağıdaki gibi açıklanmıştır:</span><span class="sxs-lookup"><span data-stu-id="a993b-161">The steps in the code you added to host the service are described as follows:</span></span>

- <span data-ttu-id="a993b-162">**1. adım**: `Uri` hizmetin temel adresini tutmak için sınıfın bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a993b-162">**Step 1**: Create an instance of the `Uri` class to hold the base address of the service.</span></span> <span data-ttu-id="a993b-163">Temel adresi içeren bir URL 'nin bir hizmeti tanımlayan isteğe bağlı bir URI 'SI vardır.</span><span class="sxs-lookup"><span data-stu-id="a993b-163">A URL that contains a base address has an optional URI that identifies a service.</span></span> <span data-ttu-id="a993b-164">Taban adresi şu şekilde biçimlendirilir: `<transport>://<machine-name or domain><:optional port #>/<optional URI segment>` .</span><span class="sxs-lookup"><span data-stu-id="a993b-164">The base address is formatted as follows: `<transport>://<machine-name or domain><:optional port #>/<optional URI segment>`.</span></span> <span data-ttu-id="a993b-165">Hesaplayıcı hizmeti için temel adres HTTP taşıması, localhost, bağlantı noktası 8000 ve URI segmentini, GettingStarted kullanır.</span><span class="sxs-lookup"><span data-stu-id="a993b-165">The base address for the calculator service uses the HTTP transport, localhost, port 8000, and the URI segment, GettingStarted.</span></span>

- <span data-ttu-id="a993b-166">**2. adım**: <xref:System.ServiceModel.ServiceHost> hizmeti barındırmak için kullandığınız sınıfının bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a993b-166">**Step 2**: Create an instance of the <xref:System.ServiceModel.ServiceHost> class, which you use to host the service.</span></span> <span data-ttu-id="a993b-167">Oluşturucu iki parametre alır: hizmet sözleşmesini uygulayan sınıfın türü ve hizmetin taban adresi.</span><span class="sxs-lookup"><span data-stu-id="a993b-167">The constructor takes two parameters: the type of the class that implements the service contract and the base address of the service.</span></span>

- <span data-ttu-id="a993b-168">**3. adım**: bir <xref:System.ServiceModel.Description.ServiceEndpoint> örnek oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a993b-168">**Step 3**: Create a <xref:System.ServiceModel.Description.ServiceEndpoint> instance.</span></span> <span data-ttu-id="a993b-169">Hizmet uç noktası bir adresten, bağlamaya ve hizmet sözleşmesinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="a993b-169">A service endpoint is composed of an address, a binding, and a service contract.</span></span> <span data-ttu-id="a993b-170"><xref:System.ServiceModel.Description.ServiceEndpoint>Oluşturucu, hizmet sözleşmesi arabirim türünden, bağlamalardan ve bir adresten oluşur.</span><span class="sxs-lookup"><span data-stu-id="a993b-170">The <xref:System.ServiceModel.Description.ServiceEndpoint> constructor is composed of the service contract interface type, a binding, and an address.</span></span> <span data-ttu-id="a993b-171">Hizmet sözleşmesi, `ICalculator` hizmet türünde tanımladığınız ve uyguladığınız hizmet sözleşmedir.</span><span class="sxs-lookup"><span data-stu-id="a993b-171">The service contract is `ICalculator`, which you defined and implement in the service type.</span></span> <span data-ttu-id="a993b-172">Bu örnek için bağlama, <xref:System.ServiceModel.WSHttpBinding> yerleşik bir bağlama ve WS-\* belirtimlerine uygun uç noktalara bağlanır.</span><span class="sxs-lookup"><span data-stu-id="a993b-172">The binding for this sample is <xref:System.ServiceModel.WSHttpBinding>, which is a built-in binding and connects to endpoints that conform to the WS-\* specifications.</span></span> <span data-ttu-id="a993b-173">WCF bağlamaları hakkında daha fazla bilgi için bkz. [WCF bağlamalarına genel bakış](bindings-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a993b-173">For more information about WCF bindings, see [WCF bindings overview](bindings-overview.md).</span></span> <span data-ttu-id="a993b-174">Uç noktayı tanımlamak için adresi temel adrese ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a993b-174">You append the address to the base address to identify the endpoint.</span></span> <span data-ttu-id="a993b-175">Kod, adresi Hesaplatorservice olarak ve uç noktanın tam adresini olarak belirtir `http://localhost:8000/GettingStarted/CalculatorService` .</span><span class="sxs-lookup"><span data-stu-id="a993b-175">The code specifies the address as CalculatorService and the fully qualified address for the endpoint as `http://localhost:8000/GettingStarted/CalculatorService`.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="a993b-176">.NET Framework sürüm 4 ve üzeri için bir hizmet uç noktası eklemek isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="a993b-176">For .NET Framework Version 4 and later, adding a service endpoint is optional.</span></span> <span data-ttu-id="a993b-177">Bu sürümler için, kodunuzu veya yapılandırmanızı eklememeniz durumunda WCF, hizmet tarafından uygulanan her temel adres ve sözleşmenin birleşimi için bir varsayılan uç nokta ekler.</span><span class="sxs-lookup"><span data-stu-id="a993b-177">For these versions, if you don't add your code or configuration, WCF adds one default endpoint for each combination of base address and contract implemented by the service.</span></span> <span data-ttu-id="a993b-178">Varsayılan uç noktalar hakkında daha fazla bilgi için bkz. [bir uç nokta adresi belirtme](specifying-an-endpoint-address.md).</span><span class="sxs-lookup"><span data-stu-id="a993b-178">For more information about default endpoints, see [Specifying an endpoint address](specifying-an-endpoint-address.md).</span></span> <span data-ttu-id="a993b-179">Varsayılan uç noktalar, bağlamalar ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="a993b-179">For more information about default endpoints, bindings, and behaviors, see [Simplified configuration](simplified-configuration.md) and [Simplified configuration for WCF services](samples/simplified-configuration-for-wcf-services.md).</span></span>

- <span data-ttu-id="a993b-180">**4. adım**: meta veri değişimini etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="a993b-180">**Step 4**: Enable metadata exchange.</span></span> <span data-ttu-id="a993b-181">İstemciler, hizmet işlemlerini çağırmak için proxy oluşturmak üzere meta veri değişimi kullanır.</span><span class="sxs-lookup"><span data-stu-id="a993b-181">Clients use metadata exchange to generate proxies for calling the service operations.</span></span> <span data-ttu-id="a993b-182">Meta veri değişimini etkinleştirmek için bir <xref:System.ServiceModel.Description.ServiceMetadataBehavior> örnek oluşturun, <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled> özelliğini olarak ayarlayın `true` ve `ServiceMetadataBehavior` nesneyi <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> örnek koleksiyonuna ekleyin <xref:System.ServiceModel.ServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="a993b-182">To enable metadata exchange, create a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance, set its <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled> property to `true`, and add the `ServiceMetadataBehavior` object to the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> collection of the <xref:System.ServiceModel.ServiceHost> instance.</span></span>

- <span data-ttu-id="a993b-183">**5. adım**: <xref:System.ServiceModel.ServiceHost> gelen iletileri dinlemek için açın.</span><span class="sxs-lookup"><span data-stu-id="a993b-183">**Step 5**: Open <xref:System.ServiceModel.ServiceHost> to listen for incoming messages.</span></span> <span data-ttu-id="a993b-184">Uygulama, **ENTER**tuşuna basmanız için bekler.</span><span class="sxs-lookup"><span data-stu-id="a993b-184">The application waits for you to press **Enter**.</span></span> <span data-ttu-id="a993b-185">Uygulama başlatıldıktan sonra <xref:System.ServiceModel.ServiceHost> bir try/catch bloğu yürütür.</span><span class="sxs-lookup"><span data-stu-id="a993b-185">After the application instantiates <xref:System.ServiceModel.ServiceHost>, it executes a try/catch block.</span></span> <span data-ttu-id="a993b-186">Tarafından oluşturulan özel durumları güvenli bir şekilde yakalama hakkında daha fazla bilgi için <xref:System.ServiceModel.ServiceHost> bkz. [Close ve Abort kullanarak WCF istemci kaynaklarını serbest bırakma](samples/use-close-abort-release-wcf-client-resources.md).</span><span class="sxs-lookup"><span data-stu-id="a993b-186">For more information about safely catching exceptions thrown by <xref:System.ServiceModel.ServiceHost>, see [Use Close and Abort to release WCF client resources](samples/use-close-abort-release-wcf-client-resources.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a993b-187">Bir WCF hizmet kitaplığı eklediğinizde, bir hizmet ana bilgisayarı başlatarak hata ayıklaması yaparsanız, Visual Studio bunu sizin için barındırır.</span><span class="sxs-lookup"><span data-stu-id="a993b-187">When you add a WCF service library, Visual Studio hosts it for you if you debug it by starting a service host.</span></span> <span data-ttu-id="a993b-188">Çakışmaları önlemek için, Visual Studio 'Nun WCF hizmeti kitaplığını barındırmasını engelleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a993b-188">To avoid conflicts, you can prevent Visual Studio from hosting the WCF service library.</span></span>
>
> 1. <span data-ttu-id="a993b-189">**Çözüm Gezgini** ' de **GettingStartedLib** projesini seçin ve kısayol menüsünden **Özellikler** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="a993b-189">Select the **GettingStartedLib** project in **Solution Explorer** and choose **Properties** from the shortcut menu.</span></span>
> 2. <span data-ttu-id="a993b-190">**WCF seçeneklerini** belirleyin ve **aynı çözümdeki başka bir projede hata ayıklarken WCF hizmeti ana bilgisayarının Başlat**seçimini kaldırın.</span><span class="sxs-lookup"><span data-stu-id="a993b-190">Select **WCF Options** and uncheck **Start WCF Service Host when debugging another project in the same solution**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="a993b-191">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="a993b-191">Next steps</span></span>

<span data-ttu-id="a993b-192">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="a993b-192">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="a993b-193">WCF hizmetini barındırmak için bir konsol uygulaması projesi oluşturun ve yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="a993b-193">Create and configure a console app project for hosting a WCF service.</span></span>
> - <span data-ttu-id="a993b-194">WCF hizmetini barındırmak için kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a993b-194">Add code to host the WCF service.</span></span>
> - <span data-ttu-id="a993b-195">Yapılandırma dosyasını güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="a993b-195">Update the configuration file.</span></span>
> - <span data-ttu-id="a993b-196">WCF hizmetini başlatın ve çalıştığını doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="a993b-196">Start the WCF service and verify it's running.</span></span>

<span data-ttu-id="a993b-197">Bir WCF istemcisi oluşturmayı öğrenmek için bir sonraki öğreticiye ilerleyin.</span><span class="sxs-lookup"><span data-stu-id="a993b-197">Advance to the next tutorial to learn how to create a WCF client.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a993b-198">Öğretici: WCF istemcisi oluşturma</span><span class="sxs-lookup"><span data-stu-id="a993b-198">Tutorial: Create a WCF client</span></span>](how-to-create-a-wcf-client.md)
