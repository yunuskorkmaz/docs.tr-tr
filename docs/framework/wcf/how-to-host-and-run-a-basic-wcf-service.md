---
title: 'Öğretici: Temel bir Windows Communication Foundation Hizmeti barındırma ve çalıştırma'
ms.date: 03/19/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF services [WCF]
- WCF services [WCF], running
ms.assetid: 31774d36-923b-4e2d-812e-aa190127266f
ms.openlocfilehash: 38fd9b89e2719be8ce4d33b1b50f68171d587369
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2019
ms.locfileid: "58410101"
---
# <a name="tutorial-host-and-run-a-basic-windows-communication-foundation-service"></a><span data-ttu-id="207d9-102">Öğretici: Temel bir Windows Communication Foundation Hizmeti barındırma ve çalıştırma</span><span class="sxs-lookup"><span data-stu-id="207d9-102">Tutorial: Host and run a basic Windows Communication Foundation service</span></span>

<span data-ttu-id="207d9-103">Bu öğreticide, temel Windows Communication Foundation (WCF) uygulaması oluşturmak için gereken beş görev üçüncü açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="207d9-103">This tutorial describes the third of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="207d9-104">Öğreticiler genel bakış için bkz. [Öğreticisi: Windows Communication Foundation uygulamalarla çalışmaya başlama](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="207d9-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="207d9-105">WCF uygulaması oluşturmak için sonraki görev, bir konsol uygulamasında bir WCF Hizmeti barındırma sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="207d9-105">The next task for creating a WCF application is to host a WCF service in a console application.</span></span> <span data-ttu-id="207d9-106">Bir WCF hizmeti bir veya daha fazla sunan *uç noktaları*, her biri bir veya daha fazla hizmet işlemleri sunar.</span><span class="sxs-lookup"><span data-stu-id="207d9-106">A WCF service exposes one or more *endpoints*, each of which exposes one or more service operations.</span></span> <span data-ttu-id="207d9-107">Hizmet uç noktası aşağıdaki bilgileri belirtir:</span><span class="sxs-lookup"><span data-stu-id="207d9-107">A service endpoint specifies the following information:</span></span> 
- <span data-ttu-id="207d9-108">Adres hizmetini bulabileceğiniz yerdir.</span><span class="sxs-lookup"><span data-stu-id="207d9-108">An address where you can find the service.</span></span>
- <span data-ttu-id="207d9-109">Bir istemci hizmeti ile nasıl iletişim kurması gereken açıklayan bilgileri içeren bir bağlama.</span><span class="sxs-lookup"><span data-stu-id="207d9-109">A binding that contains the information that describes how a client must communicate with the service.</span></span> 
- <span data-ttu-id="207d9-110">İstemcilere hizmet sağlayan işlevselliği tanımlayan bir sözleşme.</span><span class="sxs-lookup"><span data-stu-id="207d9-110">A contract that defines the functionality that the service provides to its clients.</span></span>

<span data-ttu-id="207d9-111">Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="207d9-111">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="207d9-112">Oluşturun ve bir WCF Hizmeti barındırma için bir konsol uygulama projesi yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="207d9-112">Create and configure a console app project for hosting a WCF service.</span></span>
> - <span data-ttu-id="207d9-113">WCF Hizmeti barındırma için kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="207d9-113">Add code to host the WCF service.</span></span>
> - <span data-ttu-id="207d9-114">Yapılandırma dosyasını güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="207d9-114">Update the configuration file.</span></span>
> - <span data-ttu-id="207d9-115">WCF hizmeti başlatın ve doğrulamak çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="207d9-115">Start the WCF service and verify it's running.</span></span>


## <a name="create-and-configure-a-console-app-project-for-hosting-the-service"></a><span data-ttu-id="207d9-116">Oluşturma ve barındırma hizmeti bir konsol uygulama projesi yapılandırma</span><span class="sxs-lookup"><span data-stu-id="207d9-116">Create and configure a console app project for hosting the service</span></span>

1. <span data-ttu-id="207d9-117">Visual Studio'da konsol uygulaması projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="207d9-117">Create a console app project in Visual Studio:</span></span> 
 
    1. <span data-ttu-id="207d9-118">Gelen **dosya** menüsünde **açık** > **proje/çözüm** ve **GettingStarted** çözüm, daha önce oluşturduğunuz (*GettingStarted.sln*).</span><span class="sxs-lookup"><span data-stu-id="207d9-118">From the **File** menu, select **Open** > **Project/Solution** and browse to the **GettingStarted** solution you previously created (*GettingStarted.sln*).</span></span> <span data-ttu-id="207d9-119">**Aç**'ı seçin.</span><span class="sxs-lookup"><span data-stu-id="207d9-119">Select **Open**.</span></span>

    2. <span data-ttu-id="207d9-120">Gelen **görünümü** menüsünde **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="207d9-120">From the **View** menu, select **Solution Explorer**.</span></span>
    
    3. <span data-ttu-id="207d9-121">İçinde **Çözüm Gezgini** penceresinde **GettingStarted** çözüm (üst düğümü) ve ardından **Ekle** > **YeniProje** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="207d9-121">In the **Solution Explorer** window, select the **GettingStarted** solution (top node), and then select **Add** > **New Project** from the shortcut menu.</span></span> 

    4. <span data-ttu-id="207d9-122">İçinde **Yeni Proje Ekle** penceresinde, sol tarafta, select **Windows Masaüstü** kategorisi altında **Visual C#**  veya **Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="207d9-122">In the **Add New Project** window, on the left side, select the **Windows Desktop** category under **Visual C#** or **Visual Basic**.</span></span> 

    5. <span data-ttu-id="207d9-123">Seçin **konsol uygulaması (.NET Framework)** şablon girin *GettingStartedHost* için **adı**.</span><span class="sxs-lookup"><span data-stu-id="207d9-123">Select the **Console App (.NET Framework)** template, and enter *GettingStartedHost* for the **Name**.</span></span> <span data-ttu-id="207d9-124">**Tamam**’ı seçin.</span><span class="sxs-lookup"><span data-stu-id="207d9-124">Select **OK**.</span></span>

2. <span data-ttu-id="207d9-125">Başvuru ekleme **GettingStartedHost** için proje **GettingStartedLib** proje:</span><span class="sxs-lookup"><span data-stu-id="207d9-125">Add a reference in the **GettingStartedHost** project to the **GettingStartedLib** project:</span></span> 

    1. <span data-ttu-id="207d9-126">İçinde **Çözüm Gezgini** penceresinde **başvuruları** klasörü altında **GettingStartedHost** proje ve ardından **BaşvuruEkle** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="207d9-126">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedHost** project, and then select **Add Reference** from the shortcut menu.</span></span> 

    2. <span data-ttu-id="207d9-127">İçinde **Başvuru Ekle** iletişim altında **projeleri** penceresinin sol taraftan **çözüm**.</span><span class="sxs-lookup"><span data-stu-id="207d9-127">In the **Add Reference** dialog, under **Projects** on the left side of the window, select **Solution**.</span></span> 
 
    3. <span data-ttu-id="207d9-128">Seçin **GettingStartedLib** penceresi tıklayın ve ardından Merkezi bölümünde **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="207d9-128">Select **GettingStartedLib** in the center section of the window, and then select **OK**.</span></span> 

       <span data-ttu-id="207d9-129">Bu eylem içinde tanımlanmış türlere yapar **GettingStartedLib** proje için kullanılabilir **GettingStartedHost** proje.</span><span class="sxs-lookup"><span data-stu-id="207d9-129">This action makes the types defined in the **GettingStartedLib** project available to the **GettingStartedHost** project.</span></span>

3. <span data-ttu-id="207d9-130">Başvuru ekleme **GettingStartedHost** için proje <xref:System.ServiceModel> derleme:</span><span class="sxs-lookup"><span data-stu-id="207d9-130">Add a reference in the **GettingStartedHost** project to the <xref:System.ServiceModel> assembly:</span></span> 

    1. <span data-ttu-id="207d9-131">İçinde **Çözüm Gezgini** penceresinde **başvuruları** klasörü altında **GettingStartedHost** proje ve ardından **BaşvuruEkle** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="207d9-131">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedHost** project, and then select **Add Reference** from the shortcut menu.</span></span>
    
    2. <span data-ttu-id="207d9-132">İçinde **Başvuru Ekle** penceresinin altında **derlemeleri** penceresinin sol taraftan **Framework**.</span><span class="sxs-lookup"><span data-stu-id="207d9-132">In the **Add Reference** window, under **Assemblies** on the left side of the window, select **Framework**.</span></span> 

    3. <span data-ttu-id="207d9-133">Seçin **System.ServiceModel**ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="207d9-133">Select **System.ServiceModel**, and then select **OK**.</span></span> 
    
    4. <span data-ttu-id="207d9-134">Çözüm seçerek Kaydet **dosya** > **Tümünü Kaydet**.</span><span class="sxs-lookup"><span data-stu-id="207d9-134">Save the solution by selecting **File** > **Save All**.</span></span>

## <a name="add-code-to-host-the-service"></a><span data-ttu-id="207d9-135">Hizmeti barındırmak için kod ekleyin</span><span class="sxs-lookup"><span data-stu-id="207d9-135">Add code to host the service</span></span>

<span data-ttu-id="207d9-136">Hizmeti barındırmak için aşağıdaki adımları uygulamak için kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="207d9-136">To host the service, you add code to do the following steps:</span></span> 
   1. <span data-ttu-id="207d9-137">Temel adres için URI oluşturma.</span><span class="sxs-lookup"><span data-stu-id="207d9-137">Create a URI for the base address.</span></span>
   2. <span data-ttu-id="207d9-138">Barındırma hizmeti için bir sınıf örneği oluşturun.</span><span class="sxs-lookup"><span data-stu-id="207d9-138">Create a class instance for hosting the service.</span></span>
   3. <span data-ttu-id="207d9-139">Hizmet uç noktası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="207d9-139">Create a service endpoint.</span></span>
   4. <span data-ttu-id="207d9-140">Meta veri değişimi etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="207d9-140">Enable metadata exchange.</span></span>
   5. <span data-ttu-id="207d9-141">Gelen iletileri dinlemek için hizmet ana bilgisayarı açın.</span><span class="sxs-lookup"><span data-stu-id="207d9-141">Open the service host to listen for incoming messages.</span></span>
  
<span data-ttu-id="207d9-142">Kodu aşağıdaki değişiklikleri yapın:</span><span class="sxs-lookup"><span data-stu-id="207d9-142">Make the following changes to the code:</span></span>

1. <span data-ttu-id="207d9-143">Açık **Program.cs** veya **Module1.vb** dosyası **GettingStartedHost** proje ve onun kodu aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="207d9-143">Open the **Program.cs** or **Module1.vb** file in the **GettingStartedHost** project and replace its code with the following code:</span></span>

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
    
    <span data-ttu-id="207d9-144">Bu kodu nasıl çalıştığı hakkında daha fazla bilgi için bkz: [hizmet programı adımları barındırma](#service-hosting-program-steps).</span><span class="sxs-lookup"><span data-stu-id="207d9-144">For information about how this code works, see [Service hosting program steps](#service-hosting-program-steps).</span></span>


2. <span data-ttu-id="207d9-145">Proje özelliklerini güncelleştirin:</span><span class="sxs-lookup"><span data-stu-id="207d9-145">Update the project properties:</span></span>

   1. <span data-ttu-id="207d9-146">İçinde **Çözüm Gezgini** penceresinde **GettingStartedHost** klasöre tıklayın ve ardından **özellikleri** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="207d9-146">In the **Solution Explorer** window, select the **GettingStartedHost** folder, and then select **Properties** from the shortcut menu.</span></span>

   2. <span data-ttu-id="207d9-147">Üzerinde **GettingStartedHost** özellikleri sayfasında **uygulama** sekmesinde:</span><span class="sxs-lookup"><span data-stu-id="207d9-147">On the **GettingStartedHost** properties page, select the **Application** tab:</span></span>

      - <span data-ttu-id="207d9-148">İçin C# projeleri, select **GettingStartedHost.Program** gelen **Başlangıç nesnesi** listesi.</span><span class="sxs-lookup"><span data-stu-id="207d9-148">For C# projects, select **GettingStartedHost.Program** from the **Startup object** list.</span></span>

      - <span data-ttu-id="207d9-149">Visual Basic projeleri için seçin **Service.Program** gelen **Başlangıç nesnesi** listesi.</span><span class="sxs-lookup"><span data-stu-id="207d9-149">For Visual Basic projects, select **Service.Program** from the **Startup object** list.</span></span>

   3. <span data-ttu-id="207d9-150">Gelen **dosya** menüsünde **Tümünü Kaydet**.</span><span class="sxs-lookup"><span data-stu-id="207d9-150">From the **File** menu, select **Save All**.</span></span>


## <a name="verify-the-service-is-working"></a><span data-ttu-id="207d9-151">Hizmetinin çalıştığını doğrulayın</span><span class="sxs-lookup"><span data-stu-id="207d9-151">Verify the service is working</span></span>

1. <span data-ttu-id="207d9-152">Çözümü derleyin ve çalıştırın **GettingStartedHost** Konsolu Visual Studio içinde uygulama.</span><span class="sxs-lookup"><span data-stu-id="207d9-152">Build the solution, and then run the **GettingStartedHost** console application from inside Visual Studio.</span></span> 

    <span data-ttu-id="207d9-153">Hizmet, yönetici ayrıcalıklarıyla çalıştırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="207d9-153">The service must be run with administrator privileges.</span></span> <span data-ttu-id="207d9-154">Programını çalıştırdığınızda, Visual Studio'nun yönetici ayrıcalıklarıyla açılan çünkü **GettingStartedHost** Visual Studio'da da yönetici ayrıcalıklarına sahip bir uygulama çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="207d9-154">Because you opened Visual Studio with administrator privileges, when you run **GettingStartedHost** in Visual Studio, the application is run with administrator privileges as well.</span></span> <span data-ttu-id="207d9-155">Alternatif olarak, yönetici olarak yeni bir komut istemi açın (seçin **daha fazla** > **yönetici olarak çalıştır** kısayol menüsünden) çalıştırıp **GettingStartedHost.exe**  içindeki.</span><span class="sxs-lookup"><span data-stu-id="207d9-155">As an alternative, you can open a new command prompt as an administrator (select **More** > **Run as administrator** from the shortcut menu) and run **GettingStartedHost.exe** within it.</span></span>

2. <span data-ttu-id="207d9-156">Bir web tarayıcısı açın ve hizmetin sayfasına göz atın `http://localhost:8000/GettingStarted/CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="207d9-156">Open a web browser and browse to the service's page at `http://localhost:8000/GettingStarted/CalculatorService`.</span></span>
   
   > [!NOTE]
   > <span data-ttu-id="207d9-157">Bunun gibi hizmetleri uygun HTTP adresleri dinlemek makinede kaydetme izni gerektirir.</span><span class="sxs-lookup"><span data-stu-id="207d9-157">Services such as this one require the proper permission to register HTTP addresses on the machine for listening.</span></span> <span data-ttu-id="207d9-158">Yönetim hesapları, bu izne sahiptir, ancak yönetici olmayan hesapların HTTP ad alanları için izin verilmelidir.</span><span class="sxs-lookup"><span data-stu-id="207d9-158">Administrator accounts have this permission, but non-administrator accounts must be granted permission for HTTP namespaces.</span></span> <span data-ttu-id="207d9-159">Ad alanı ayırmaları yapılandırma hakkında daha fazla bilgi için bkz. [yapılandırma HTTP ve HTTPS](feature-details/configuring-http-and-https.md).</span><span class="sxs-lookup"><span data-stu-id="207d9-159">For more information about how to configure namespace reservations, see [Configuring HTTP and HTTPS](feature-details/configuring-http-and-https.md).</span></span> 


## <a name="service-hosting-program-steps"></a><span data-ttu-id="207d9-160">Hizmet barındırma program adımları</span><span class="sxs-lookup"><span data-stu-id="207d9-160">Service hosting program steps</span></span>

<span data-ttu-id="207d9-161">Hizmet aşağıdaki gibi açıklandığı gibi ana bilgisayar için eklenen kodu adımları:</span><span class="sxs-lookup"><span data-stu-id="207d9-161">The steps in the code you added to host the service are described as follows:</span></span>

- <span data-ttu-id="207d9-162">**1. adım**: Bir örneğini oluşturmak `Uri` hizmetin taban adresi için sınıf.</span><span class="sxs-lookup"><span data-stu-id="207d9-162">**Step 1**: Create an instance of the `Uri` class to hold the base address of the service.</span></span> <span data-ttu-id="207d9-163">Temel adres içeren bir URL, bir hizmeti tanımlayan bir isteğe bağlı bir URI'ya sahip.</span><span class="sxs-lookup"><span data-stu-id="207d9-163">A URL that contains a base address has an optional URI that identifies a service.</span></span> <span data-ttu-id="207d9-164">Temel adres gibi biçimlendirilir: `<transport>://<machine-name or domain><:optional port #>/<optional URI segment>`.</span><span class="sxs-lookup"><span data-stu-id="207d9-164">The base address is formatted as follows: `<transport>://<machine-name or domain><:optional port #>/<optional URI segment>`.</span></span> <span data-ttu-id="207d9-165">HTTP taşıma, localhost, 8000 numaralı bağlantı noktasını ve GettingStarted URI segmenti hesaplayıcı hizmeti temel adresi kullanır.</span><span class="sxs-lookup"><span data-stu-id="207d9-165">The base address for the calculator service uses the HTTP transport, localhost, port 8000, and the URI segment, GettingStarted.</span></span>

- <span data-ttu-id="207d9-166">**2. adım**: Bir örneğini oluşturmak <xref:System.ServiceModel.ServiceHost> hizmeti barındırmak için kullanılan sınıf.</span><span class="sxs-lookup"><span data-stu-id="207d9-166">**Step 2**: Create an instance of the <xref:System.ServiceModel.ServiceHost> class, which you use to host the service.</span></span> <span data-ttu-id="207d9-167">Oluşturucu iki parametre alır: Hizmet sözleşmesi ve hizmetin taban adresi uygulayan sınıf türü.</span><span class="sxs-lookup"><span data-stu-id="207d9-167">The constructor takes two parameters: the type of the class that implements the service contract and the base address of the service.</span></span>

- <span data-ttu-id="207d9-168">**3. adım**: Oluşturma bir <xref:System.ServiceModel.Description.ServiceEndpoint> örneği.</span><span class="sxs-lookup"><span data-stu-id="207d9-168">**Step 3**: Create a <xref:System.ServiceModel.Description.ServiceEndpoint> instance.</span></span> <span data-ttu-id="207d9-169">Hizmet uç noktası bir adresi, bağlama ve hizmet sözleşmesi oluşur.</span><span class="sxs-lookup"><span data-stu-id="207d9-169">A service endpoint is composed of an address, a binding, and a service contract.</span></span> <span data-ttu-id="207d9-170"><xref:System.ServiceModel.Description.ServiceEndpoint> Oluşturucusu hizmet sözleşme arabirimi türü, bağlama ve bir adresi oluşur.</span><span class="sxs-lookup"><span data-stu-id="207d9-170">The <xref:System.ServiceModel.Description.ServiceEndpoint> constructor is composed of the service contract interface type, a binding, and an address.</span></span> <span data-ttu-id="207d9-171">Hizmet sözleşme `ICalculator`, tanımlanan ve hizmet türüne uygulayın.</span><span class="sxs-lookup"><span data-stu-id="207d9-171">The service contract is `ICalculator`, which you defined and implement in the service type.</span></span> <span data-ttu-id="207d9-172">Bu örnek için bağlama <xref:System.ServiceModel.WSHttpBinding>, yerleşik bir bağlamadır ve WS - için uygun uç noktalarına bağlayan \* belirtimleri.</span><span class="sxs-lookup"><span data-stu-id="207d9-172">The binding for this sample is <xref:System.ServiceModel.WSHttpBinding>, which is a built-in binding and connects to endpoints that conform to the WS-\* specifications.</span></span> <span data-ttu-id="207d9-173">WCF bağlamaları hakkında daha fazla bilgi için bkz: [WCF bağlamaları genel bakış](bindings-overview.md).</span><span class="sxs-lookup"><span data-stu-id="207d9-173">For more information about WCF bindings, see [WCF bindings overview](bindings-overview.md).</span></span> <span data-ttu-id="207d9-174">Uç noktayı tanımlamak için temel adres bir adres sonuna ekleyin.</span><span class="sxs-lookup"><span data-stu-id="207d9-174">You append the address to the base address to identify the endpoint.</span></span> <span data-ttu-id="207d9-175">Kod CalculatorService ve tam uç nokta adresi olarak adresini belirten `http://localhost:8000/GettingStarted/CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="207d9-175">The code specifies the address as CalculatorService and the fully qualified address for the endpoint as `http://localhost:8000/GettingStarted/CalculatorService`.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="207d9-176">.NET Framework sürüm 4 ve sonraki sürümlerinde, bir hizmet uç noktası eklemek isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="207d9-176">For .NET Framework Version 4 and later, adding a service endpoint is optional.</span></span> <span data-ttu-id="207d9-177">Kod veya yapılandırma, eklemezseniz bu sürümleri için WCF taban adresini ve sözleşme hizmeti tarafından uygulanan her bir birleşimi için bir varsayılan uç nokta ekler.</span><span class="sxs-lookup"><span data-stu-id="207d9-177">For these versions, if you don't add your code or configuration, WCF adds one default endpoint for each combination of base address and contract implemented by the service.</span></span> <span data-ttu-id="207d9-178">Varsayılan uç noktaları hakkında daha fazla bilgi için bkz. [bir uç nokta adresi belirtme](specifying-an-endpoint-address.md).</span><span class="sxs-lookup"><span data-stu-id="207d9-178">For more information about default endpoints, see [Specifying an endpoint address](specifying-an-endpoint-address.md).</span></span> <span data-ttu-id="207d9-179">Varsayılan uç noktaları, bağlamalar ve davranışları hakkında daha fazla bilgi için bkz. [Basitleştirilmiş yapılandırma](simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="207d9-179">For more information about default endpoints, bindings, and behaviors, see [Simplified configuration](simplified-configuration.md) and [Simplified configuration for WCF services](samples/simplified-configuration-for-wcf-services.md).</span></span>

- <span data-ttu-id="207d9-180">**4. adım**: Meta veri değişimi etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="207d9-180">**Step 4**: Enable metadata exchange.</span></span> <span data-ttu-id="207d9-181">İstemcileri, hizmet işlemleri çağırmak için proxy oluşturmak için meta veri değişimi kullanın.</span><span class="sxs-lookup"><span data-stu-id="207d9-181">Clients use metadata exchange to generate proxies for calling the service operations.</span></span> <span data-ttu-id="207d9-182">Meta veri değişimi etkinleştirmek için oluşturun bir <xref:System.ServiceModel.Description.ServiceMetadataBehavior> örnek olarak ayarlayın, <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled> özelliğini `true`ve ekleme `ServiceMetadataBehavior` nesnesini <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> koleksiyonunu <xref:System.ServiceModel.ServiceHost> örneği.</span><span class="sxs-lookup"><span data-stu-id="207d9-182">To enable metadata exchange, create a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance, set its <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled> property to `true`, and add the `ServiceMetadataBehavior` object to the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> collection of the <xref:System.ServiceModel.ServiceHost> instance.</span></span>

- <span data-ttu-id="207d9-183">**5. adım**: Açık <xref:System.ServiceModel.ServiceHost> gelen iletileri dinlemek için.</span><span class="sxs-lookup"><span data-stu-id="207d9-183">**Step 5**: Open <xref:System.ServiceModel.ServiceHost> to listen for incoming messages.</span></span> <span data-ttu-id="207d9-184">Uygulama, basmanızı bekler **Enter**.</span><span class="sxs-lookup"><span data-stu-id="207d9-184">The application waits for you to press **Enter**.</span></span> <span data-ttu-id="207d9-185">Uygulama örneğini oluşturur sonra <xref:System.ServiceModel.ServiceHost>, try/catch bloğu yürütür.</span><span class="sxs-lookup"><span data-stu-id="207d9-185">After the application instantiates <xref:System.ServiceModel.ServiceHost>, it executes a try/catch block.</span></span> <span data-ttu-id="207d9-186">Güvenli bir şekilde tarafından oluşturulan özel durumları yakalama hakkında daha fazla bilgi için <xref:System.ServiceModel.ServiceHost>, bkz: [kullanım Kapat ve iptal WCF istemci kaynaklar serbest bırakılacaksa](samples/use-close-abort-release-wcf-client-resources.md).</span><span class="sxs-lookup"><span data-stu-id="207d9-186">For more information about safely catching exceptions thrown by <xref:System.ServiceModel.ServiceHost>, see [Use Close and Abort to release WCF client resources](samples/use-close-abort-release-wcf-client-resources.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="207d9-187">Bir WCF hizmet kitaplığı eklediğinizde, hizmet ana bilgisayarı yeniden başlatarak hatalarını ayıklıyorsanız Visual Studio bunu sizin için barındırır.</span><span class="sxs-lookup"><span data-stu-id="207d9-187">When you add a WCF service library, Visual Studio hosts it for you if you debug it by starting a service host.</span></span> <span data-ttu-id="207d9-188">Çakışmaları önlemek için Visual Studio WCF hizmet kitaplığı barındırma veritabanından engelleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="207d9-188">To avoid conflicts, you can prevent Visual Studio from hosting the WCF service library.</span></span> 
> 1. <span data-ttu-id="207d9-189">Seçin **GettingStartedLib** projesi **Çözüm Gezgini** ve **özellikleri** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="207d9-189">Select the **GettingStartedLib** project in **Solution Explorer** and choose **Properties** from the shortcut menu.</span></span>
> 2. <span data-ttu-id="207d9-190">Seçin **WCF seçenekleri** kaldırın **Başlat WCF hizmet aynı çözümdeki başka bir proje hata ayıklama konağı**.</span><span class="sxs-lookup"><span data-stu-id="207d9-190">Select **WCF Options** and uncheck **Start WCF Service Host when debugging another project in the same solution**.</span></span>


## <a name="next-steps"></a><span data-ttu-id="207d9-191">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="207d9-191">Next steps</span></span>

<span data-ttu-id="207d9-192">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="207d9-192">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="207d9-193">Oluşturun ve bir WCF Hizmeti barındırma için bir konsol uygulama projesi yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="207d9-193">Create and configure a console app project for hosting a WCF service.</span></span>
> - <span data-ttu-id="207d9-194">WCF Hizmeti barındırma için kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="207d9-194">Add code to host the WCF service.</span></span>
> - <span data-ttu-id="207d9-195">Yapılandırma dosyasını güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="207d9-195">Update the configuration file.</span></span>
> - <span data-ttu-id="207d9-196">WCF hizmeti başlatın ve doğrulamak çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="207d9-196">Start the WCF service and verify it's running.</span></span>

<span data-ttu-id="207d9-197">Bir WCF istemcisi oluşturma hakkında bilgi edinmek için sonraki öğreticiye ilerleyin.</span><span class="sxs-lookup"><span data-stu-id="207d9-197">Advance to the next tutorial to learn how to create a WCF client.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="207d9-198">Öğretici: Bir WCF istemcisi oluşturma</span><span class="sxs-lookup"><span data-stu-id="207d9-198">Tutorial: Create a WCF client</span></span>](how-to-create-a-wcf-client.md)
