---
title: 'Nasıl yapılır: Temel Bir Windows Communication Foundation Hizmeti Barındırma ve Çalıştırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF services [WCF]
- WCF services [WCF], running
ms.assetid: 31774d36-923b-4e2d-812e-aa190127266f
ms.openlocfilehash: e2bf16bd07c7ac9d918a4ae95d7f4aa185d436ec
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43741165"
---
# <a name="how-to-host-and-run-a-basic-windows-communication-foundation-service"></a><span data-ttu-id="a0fda-102">Nasıl yapılır: Temel Bir Windows Communication Foundation Hizmeti Barındırma ve Çalıştırma</span><span class="sxs-lookup"><span data-stu-id="a0fda-102">How to: Host and Run a Basic Windows Communication Foundation Service</span></span>
<span data-ttu-id="a0fda-103">Üçüncü altı görev bir Windows Communication Foundation (WCF) uygulaması oluşturmak için gereken budur.</span><span class="sxs-lookup"><span data-stu-id="a0fda-103">This is the third of six tasks required to create a Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="a0fda-104">Tüm altı görevleri genel bakış için bkz. [başlangıç Öğreticisi](../../../docs/framework/wcf/getting-started-tutorial.md) konu.</span><span class="sxs-lookup"><span data-stu-id="a0fda-104">For an overview of all six of the tasks, see the [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md) topic.</span></span>  
  
 <span data-ttu-id="a0fda-105">Bu konu, bir Windows Communication Foundation (WCF) hizmeti bir konsol uygulamasında barındırma açıklar.</span><span class="sxs-lookup"><span data-stu-id="a0fda-105">This topic describes how to host a Windows Communication Foundation (WCF) service in a console application.</span></span> <span data-ttu-id="a0fda-106">Bu yordam, aşağıdaki adımlardan oluşur:</span><span class="sxs-lookup"><span data-stu-id="a0fda-106">This procedure consists of the following steps:</span></span>  
  
-   <span data-ttu-id="a0fda-107">Hizmeti barındırmak için bir konsol uygulama projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a0fda-107">Create a console application project to host the service.</span></span>  
  
-   <span data-ttu-id="a0fda-108">Hizmet konak hizmeti oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a0fda-108">Create a service host for the service.</span></span>  
  
-   <span data-ttu-id="a0fda-109">Meta veri değişimi etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="a0fda-109">Enable metadata exchange.</span></span>  
  
-   <span data-ttu-id="a0fda-110">Hizmet ana bilgisayarı açın.</span><span class="sxs-lookup"><span data-stu-id="a0fda-110">Open the service host.</span></span>  
  
 <span data-ttu-id="a0fda-111">Bu görevde yazılan kodların tam listesi yordamdan örnekte sağlanır.</span><span class="sxs-lookup"><span data-stu-id="a0fda-111">A complete listing of the code written in this task is provided in the example following the procedure.</span></span>  
  
## <a name="to-create-a-new-console-application-to-host-the-service"></a><span data-ttu-id="a0fda-112">Hizmeti barındırmak için yeni bir konsol uygulaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="a0fda-112">To create a new console application to host the service</span></span>  
  
1.  <span data-ttu-id="a0fda-113">Başlarken çözümü seçerken üzerinde sağ tıklayarak yeni bir konsol uygulaması projesi oluşturma **Ekle**, **yeni proje**.</span><span class="sxs-lookup"><span data-stu-id="a0fda-113">Create a new Console Application project by right-clicking on the Getting Started solution, selecting, **Add**, **New Project**.</span></span> <span data-ttu-id="a0fda-114">İçinde **Yeni Proje Ekle** sol tarafındaki iletişim Seç iletişim **Windows** altında **C#** veya **VB**.</span><span class="sxs-lookup"><span data-stu-id="a0fda-114">In the **Add New Project** dialog on the left hand side of the dialog select **Windows** under **C#** or **VB**.</span></span> <span data-ttu-id="a0fda-115">İletişim kutusunun orta kısmını seçin **konsol uygulaması**.</span><span class="sxs-lookup"><span data-stu-id="a0fda-115">In the center section of the dialog select **Console Application**.</span></span> <span data-ttu-id="a0fda-116">GettingStartedHost projesini adlandırın.</span><span class="sxs-lookup"><span data-stu-id="a0fda-116">Name the project GettingStartedHost.</span></span>  
  
2.  <span data-ttu-id="a0fda-117">GettingStartedHost projenin hedef çerçevesi sağ tıklanarak .NET Framework 4.5 olarak ayarlayın. **GettingStartedHost** Çözüm Gezgini'nde seçerek **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="a0fda-117">Set the target framework of the GettingStartedHost project to .NET Framework 4.5 by right clicking on **GettingStartedHost** in the Solution Explorer and selecting **Properties**.</span></span> <span data-ttu-id="a0fda-118">Açılan kutuda yer etiketli **hedef Framework'ü** seçin **.NET Framework 4.5**.</span><span class="sxs-lookup"><span data-stu-id="a0fda-118">In the dropdown box labeled **Target Framework** select **.NET Framework 4.5**.</span></span> <span data-ttu-id="a0fda-119">Hedef Framework'ü ayarı GettingStartedHost Proje Özellikleri iletişim kutusunda bir VB projesi biraz farklıdır, tıklayın **derleme** sekmesinde ekranın sol tarafındaki ve ardından **Gelişmiş derleme Seçenekleri** iletişim kutusunun sol alt köşesindeki düğme.</span><span class="sxs-lookup"><span data-stu-id="a0fda-119">Setting the target framework for a VB project is a little different, in the GettingStartedHost project properties dialog, click the **Compile** tab on the left-hand side of the screen, and then click the **Advanced Compile Options** button at the lower left-hand corner of the dialog.</span></span> <span data-ttu-id="a0fda-120">Ardından **.NET Framework 4.5** kutuda etiketli **hedef Framework'ü**.</span><span class="sxs-lookup"><span data-stu-id="a0fda-120">Then select **.NET Framework 4.5** in the dropdown box labeled **Target Framework**.</span></span>  
  
     <span data-ttu-id="a0fda-121">Hedef Framework'ü neden ayarı [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] çözümü yeniden yüklemek için basın **Tamam** istendiğinde.</span><span class="sxs-lookup"><span data-stu-id="a0fda-121">Setting the target framework will cause [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] to reload the solution, press **OK** when prompted.</span></span>  
  
3.  <span data-ttu-id="a0fda-122">Sağ tıklanarak GettingStartedHost projeye GettingStartedLib projeye bir başvuru eklemek **başvuruları** klasörü altında Çözüm Gezgini seçip GettingStartedHost proje **Başvuru Ekle** .</span><span class="sxs-lookup"><span data-stu-id="a0fda-122">Add a reference to the GettingStartedLib project to the GettingStartedHost project by right clicking on the **References** folder under the GettingStartedHost project in the solution explorer and select **Add Reference**.</span></span> <span data-ttu-id="a0fda-123">İçinde **Başvuru Ekle** iletişim kutusunda **çözüm** iletişim ve select GettingStartedLib tıklayın ve iletişim merkezi bölümünde sol tarafta **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="a0fda-123">In the **Add Reference** dialog, select **Solution** on the left-hand side of the dialog and select GettingStartedLib in the center section of the dialog and click **Add**.</span></span> <span data-ttu-id="a0fda-124">Bu, GettingStartedLib GettingStartedHost projesi için tanımlanan türleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="a0fda-124">This makes the types defined in GettingStartedLib available to the GettingStartedHost project.</span></span>  
  
4.  <span data-ttu-id="a0fda-125">System.ServiceModel başvuru GettingStartedHost projeye sağ tıklayarak ekleyin **başvuru** klasörü altında Çözüm Gezgini seçip GettingStartedHost proje **Ekle** Başvuru.</span><span class="sxs-lookup"><span data-stu-id="a0fda-125">Add a reference to System.ServiceModel to the GettingStartedHost project by right-clicking the **Reference** folder under the GettingStartedHost project in Solution Explorer and select **Add** Reference.</span></span> <span data-ttu-id="a0fda-126">İçinde **Başvuru Ekle** iletişim kutusunda **Framework** iletişim kutusunun sol taraftaki.</span><span class="sxs-lookup"><span data-stu-id="a0fda-126">In the **Add Reference** dialog select **Framework** on the left-hand side of the dialog.</span></span> <span data-ttu-id="a0fda-127">Derlemeleri arama metin kutusuna yazın `System.ServiceModel`.</span><span class="sxs-lookup"><span data-stu-id="a0fda-127">In the Search Assemblies textbox, type in `System.ServiceModel`.</span></span> <span data-ttu-id="a0fda-128">İletişim kutusunun orta kısmını seçin **System.ServiceModel**, tıklayın **Ekle** düğmesini **Kapat** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="a0fda-128">In the center section of the dialog select **System.ServiceModel**, click the **Add** button, and click the **Close** button.</span></span> <span data-ttu-id="a0fda-129">Ana menü altında Tümünü Kaydet düğmesine tıklayarak çözüm kaydedin.</span><span class="sxs-lookup"><span data-stu-id="a0fda-129">Save the solution by clicking the Save All button below the main menu.</span></span>  
  
### <a name="to-host-the-service"></a><span data-ttu-id="a0fda-130">Ana bilgisayar hizmeti</span><span class="sxs-lookup"><span data-stu-id="a0fda-130">To host the service</span></span>  
  
-   <span data-ttu-id="a0fda-131">Program.cs veya Module.vb dosyasını açın ve aşağıdaki kodu girin:</span><span class="sxs-lookup"><span data-stu-id="a0fda-131">Open the Program.cs or Module.vb file and enter the following code:</span></span>  
  
    ```csharp
    // program.cs  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using System.ServiceModel;  
    using GettingStartedLib;  
    using System.ServiceModel.Description;   
  
    namespace GettingStartedHost  
    {  
        class Program  
        {  
            static void Main(string[] args)  
            {  
                // Step 1 Create a URI to serve as the base address.  
                Uri baseAddress = new Uri("http://localhost:8000/GettingStarted/");  
  
                // Step 2 Create a ServiceHost instance  
                ServiceHost selfHost = new ServiceHost(typeof(CalculatorService), baseAddress);  
  
                try  
                {  
                    // Step 3 Add a service endpoint.  
                    selfHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), "CalculatorService");  
  
                    // Step 4 Enable metadata exchange.  
                    ServiceMetadataBehavior smb = new ServiceMetadataBehavior();  
                    smb.HttpGetEnabled = true;  
                    selfHost.Description.Behaviors.Add(smb);  
  
                    // Step 5 Start the service.  
                    selfHost.Open();  
                    Console.WriteLine("The service is ready.");  
                    Console.WriteLine("Press <ENTER> to terminate service.");  
                    Console.WriteLine();  
                    Console.ReadLine();  
  
                    // Close the ServiceHostBase to shutdown the service.  
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
    'Module1.vb  
    Imports System  
    Imports System.ServiceModel  
    Imports System.ServiceModel.Description  
    Imports GettingStartedLibVB.GettingStartedLib  
  
    Module Service  
  
        Class Program  
            Shared Sub Main()  
                ' Step 1 Create a URI to serve as the base address  
                Dim baseAddress As New Uri("http://localhost:8000/ServiceModelSamples/Service")  
  
                ' Step 2 Create a ServiceHost instance  
                Dim selfHost As New ServiceHost(GetType(CalculatorService), baseAddress)  
                Try  
  
                    ' Step 3 Add a service endpoint  
                    ' Add a service endpoint  
                    selfHost.AddServiceEndpoint( _  
                        GetType(ICalculator), _  
                        New WSHttpBinding(), _  
                        "CalculatorService")  
  
                    ' Step 4 Enable metadata exchange.  
                    Dim smb As New ServiceMetadataBehavior()  
                    smb.HttpGetEnabled = True  
                    selfHost.Description.Behaviors.Add(smb)  
  
                    ' Step 5 Start the service  
                    selfHost.Open()  
                    Console.WriteLine("The service is ready.")  
                    Console.WriteLine("Press <ENTER> to terminate service.")  
                    Console.WriteLine()  
                    Console.ReadLine()  
  
                    ' Close the ServiceHostBase to shutdown the service.  
                    selfHost.Close()  
                Catch ce As CommunicationException  
                    Console.WriteLine("An exception occurred: {0}", ce.Message)  
                    selfHost.Abort()  
                End Try  
            End Sub  
        End Class  
  
    End Module  
    ```  
  
    1.  <span data-ttu-id="a0fda-132">1. adım - hizmet temel adresini tutacak URI sınıfının bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a0fda-132">Step 1 - Creates an instance of the Uri class to hold the base address of the service.</span></span> <span data-ttu-id="a0fda-133">Hizmetleri, bir taban adresi içeren bir URL ve isteğe bağlı bir URI tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="a0fda-133">Services are identified by a URL which contains a base address and an optional URI.</span></span> <span data-ttu-id="a0fda-134">Temel adres gibi biçimlendirilir: [aktarım] :// [makine adı veya etki alanı] [: isteğe bağlı bağlantı noktası #] / [isteğe bağlı URI segmenti] HTTP aktarımı hesaplayıcı hizmeti temel adresi kullanır, segment "GettingStarted" localhost, 8000 numaralı bağlantı noktasını ve URI</span><span class="sxs-lookup"><span data-stu-id="a0fda-134">The base address is formatted as follows:[transport]://[machine-name or domain][:optional port #]/[optional URI segment]The base address for the calculator service uses the HTTP transport, localhost, port 8000, and the URI segment "GettingStarted"</span></span>  
  
    2.  <span data-ttu-id="a0fda-135">Adım 2 – bir örneğini oluşturur / <xref:System.ServiceModel.ServiceHost> Hizmeti'ni barındıracak şekilde sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a0fda-135">Step 2 – Creates an instance of the <xref:System.ServiceModel.ServiceHost> class to host the service.</span></span> <span data-ttu-id="a0fda-136">Oluşturucu, iki parametre, hizmet sözleşmesi uygulayan sınıf türünü ve hizmetin taban adresi alır.</span><span class="sxs-lookup"><span data-stu-id="a0fda-136">The constructor takes two parameters, the type of the class that implements the service contract, and the base address of the service.</span></span>  
  
    3.  <span data-ttu-id="a0fda-137">Adım 3 – oluşturur bir <xref:System.ServiceModel.Description.ServiceEndpoint> örneği.</span><span class="sxs-lookup"><span data-stu-id="a0fda-137">Step 3 – Creates a <xref:System.ServiceModel.Description.ServiceEndpoint> instance.</span></span> <span data-ttu-id="a0fda-138">Hizmet uç noktası bir adresi, bağlama ve hizmet sözleşmesi oluşur.</span><span class="sxs-lookup"><span data-stu-id="a0fda-138">A service endpoint is composed of an address, a binding, and a service contract.</span></span> <span data-ttu-id="a0fda-139"><xref:System.ServiceModel.Description.ServiceEndpoint> Oluşturucusu bu nedenle hizmet sözleşme arabirimi türü, bağlama ve bir adresi alır.</span><span class="sxs-lookup"><span data-stu-id="a0fda-139">The <xref:System.ServiceModel.Description.ServiceEndpoint> constructor therefore takes the service contract interface type, a binding, and an address.</span></span> <span data-ttu-id="a0fda-140">Hizmet sözleşme `ICalculator`, tanımlanan ve hizmet türüne uygulayın.</span><span class="sxs-lookup"><span data-stu-id="a0fda-140">The service contract is `ICalculator`, which you defined and implement in the service type.</span></span> <span data-ttu-id="a0fda-141">Bu örnekte kullanılan bağlamanın <xref:System.ServiceModel.WSHttpBinding> WS - için uygun uç noktalarına bağlamak için kullanılan yerleşik bir bağlama olduğu \* belirtimleri.</span><span class="sxs-lookup"><span data-stu-id="a0fda-141">The binding used in this sample is <xref:System.ServiceModel.WSHttpBinding> which is a built-in binding that is used for connecting to endpoints that conform to the WS-\* specifications.</span></span> <span data-ttu-id="a0fda-142">WCF bağlamaları hakkında daha fazla bilgi için bkz: [WCF bağlamaları genel bakış](../../../docs/framework/wcf/bindings-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a0fda-142">For more information about WCF bindings, see [WCF Bindings Overview](../../../docs/framework/wcf/bindings-overview.md).</span></span> <span data-ttu-id="a0fda-143">Adres, uç noktayı tanımlamak için taban adresi olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="a0fda-143">The address is appended to the base address to identify the endpoint.</span></span> <span data-ttu-id="a0fda-144">Tam uç nokta adresi "CalculatorService" Bu kodu belirtilen adresi olduğundan `"http://localhost:8000/GettingStarted/CalculatorService"`.</span><span class="sxs-lookup"><span data-stu-id="a0fda-144">The address specified in this code is "CalculatorService" so the fully qualified address for the endpoint is `"http://localhost:8000/GettingStarted/CalculatorService"`.</span></span>  
  
        > [!IMPORTANT]
        >  <span data-ttu-id="a0fda-145">.NET Framework 4 kullanırken, isteğe bağlı veya üzeri bir hizmet uç noktası ekleniyor.</span><span class="sxs-lookup"><span data-stu-id="a0fda-145">Adding a service endpoint is optional when using .NET Framework 4 or later.</span></span> <span data-ttu-id="a0fda-146">Kod veya yapılandırma, uç nokta eklenirse bu sürümlerde WCF taban adresini ve sözleşme hizmeti tarafından uygulanan her bir birleşimi için bir varsayılan uç nokta ekler.</span><span class="sxs-lookup"><span data-stu-id="a0fda-146">In these versions, if no endpoints are added in code or configuration, WCF adds one default endpoint for each combination of base address and contract implemented by the service.</span></span> <span data-ttu-id="a0fda-147">Uç noktaları varsayılan hakkında daha fazla bilgi için bkz: [bir uç nokta adresi belirtme](../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span><span class="sxs-lookup"><span data-stu-id="a0fda-147">For more information about default endpoints see [Specifying an Endpoint Address](../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span></span> <span data-ttu-id="a0fda-148">Varsayılan uç noktaları, bağlamalar ve davranışları hakkında daha fazla bilgi için bkz. [Basitleştirilmiş yapılandırma](../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="a0fda-148">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
    4.  <span data-ttu-id="a0fda-149">4. adım – etkin meta veri değişimi.</span><span class="sxs-lookup"><span data-stu-id="a0fda-149">Step 4 – Enable metadata exchange.</span></span> <span data-ttu-id="a0fda-150">İstemciler, meta veri değişimi, hizmet işlemlerini aramak için kullanılacak proxy üretmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="a0fda-150">Clients will use metadata exchange to generate proxies that will be used to call the service operations.</span></span> <span data-ttu-id="a0fda-151">Etkinleştirmek için meta veri değişimi oluşturma bir <xref:System.ServiceModel.Description.ServiceMetadataBehavior> ayarlayın, örnek 's <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> özelliğini `true`ve davranışların eklenmesi <!--zz <xref:System.ServiceModel.ServiceHost.Behaviors%2A>  --> `System.ServiceModel.ServiceHost.Behaviors%2A` koleksiyonunu <xref:System.ServiceModel.ServiceHost> örneği.</span><span class="sxs-lookup"><span data-stu-id="a0fda-151">To enable metadata exchange create a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance, set it’s <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> property to `true`, and add the behavior to the <!--zz <xref:System.ServiceModel.ServiceHost.Behaviors%2A>  -->`System.ServiceModel.ServiceHost.Behaviors%2A` collection of the <xref:System.ServiceModel.ServiceHost> instance.</span></span>  
  
    5.  <span data-ttu-id="a0fda-152">Adım 5-açık <xref:System.ServiceModel.ServiceHost> gelen iletileri dinlemek için.</span><span class="sxs-lookup"><span data-stu-id="a0fda-152">Step 5 – Open the <xref:System.ServiceModel.ServiceHost> to listen for incoming messages.</span></span> <span data-ttu-id="a0fda-153">Uyarı kodunu kullanıcının isabet bekler girin.</span><span class="sxs-lookup"><span data-stu-id="a0fda-153">Notice the code waits for the user to hit enter.</span></span> <span data-ttu-id="a0fda-154">Bunu yaparsanız, uygulamayı hemen kapatmak ve hizmet kapanır. Bir try/catch bloğu kullanılan dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="a0fda-154">If you do not do this, the app will close immediately and the service will shut down.Also notice a  try/catch block used.</span></span> <span data-ttu-id="a0fda-155">Sonra <xref:System.ServiceModel.ServiceHost> olmuştur örneği, diğer tüm kod bir try/catch bloğu içinde yer alır.</span><span class="sxs-lookup"><span data-stu-id="a0fda-155">After the <xref:System.ServiceModel.ServiceHost> has been instantiated, all other code is placed in a try/catch block.</span></span> <span data-ttu-id="a0fda-156">Güvenli bir şekilde tarafından oluşturulan özel durumları yakalama hakkında daha fazla bilgi için <xref:System.ServiceModel.ServiceHost>, bkz: [Using deyimi sorunlarını önleme](../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md)</span><span class="sxs-lookup"><span data-stu-id="a0fda-156">For more information about safely catching exceptions thrown by <xref:System.ServiceModel.ServiceHost>, see [Avoiding Problems with the Using Statement](../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md)</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a0fda-157">App.config dosyasında GettingStartedLib kodunda yaptığınız değişiklikleri yansıtacak şekilde düzenleyin:</span><span class="sxs-lookup"><span data-stu-id="a0fda-157">Edit App.config in GettingStartedLib to reflect the changes made in code:</span></span> 
> 1. <span data-ttu-id="a0fda-158">14. satır için değiştirin `<service name="GettingStartedLib.CalculatorService">`</span><span class="sxs-lookup"><span data-stu-id="a0fda-158">Change line 14 to `<service name="GettingStartedLib.CalculatorService">`</span></span>
> 2. <span data-ttu-id="a0fda-159">17 satırına değiştirme `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span><span class="sxs-lookup"><span data-stu-id="a0fda-159">Change line 17 to `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span></span>
> 3. <span data-ttu-id="a0fda-160">Satır 22 için değiştirin `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`</span><span class="sxs-lookup"><span data-stu-id="a0fda-160">Change line 22 to `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`</span></span>
        
### <a name="to-verify-the-service-is-working"></a><span data-ttu-id="a0fda-161">Hizmetin çalıştığını doğrulamak için</span><span class="sxs-lookup"><span data-stu-id="a0fda-161">To verify the service is working</span></span>  
  
1.  <span data-ttu-id="a0fda-162">GettingStartedHost konsol üzerinden içinde çalışan [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a0fda-162">Run the GettingStartedHost console application from inside [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].</span></span> <span data-ttu-id="a0fda-163">Çalışırken [!INCLUDE[wv](../../../includes/wv-md.md)] ve sonraki işletim sistemleri, hizmet yönetici ayrıcalıklarıyla çalıştırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a0fda-163">When running on [!INCLUDE[wv](../../../includes/wv-md.md)] and later operating systems, the service must be run with administrator privileges.</span></span> <span data-ttu-id="a0fda-164">Visual Studio'yu yönetici ayrıcalıklarıyla çalıştığından, GettingStartedHost da yönetici ayrıcalıklarıyla çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a0fda-164">Because Visual Studio was run with Administrator privileges, GettingStartedHost is also run with Administrator privileges.</span></span> <span data-ttu-id="a0fda-165">Ayrıca, yönetici ayrıcalıklarıyla çalışan yeni bir komut istemi başlatın ve içerdiği service.exe çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a0fda-165">You can also start a new command prompt running it with Administrator privileges and run service.exe within it.</span></span>  
  
2.  <span data-ttu-id="a0fda-166">Açık Internet Explorer ve göz atma hizmetin hata ayıklama sayfasında `http://localhost:8000/GettingStarted/CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="a0fda-166">Open Internet Explorer and browse to the service's debug page at `http://localhost:8000/GettingStarted/CalculatorService`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0fda-167">Örnek</span><span class="sxs-lookup"><span data-stu-id="a0fda-167">Example</span></span>  
 <span data-ttu-id="a0fda-168">Aşağıdaki örnek, hizmet sözleşmesini ve önceki adımdan öğreticide içerir ve hizmeti bir konsol uygulamasında barındırır.</span><span class="sxs-lookup"><span data-stu-id="a0fda-168">The following example includes the service contract and implementation from previous steps in the tutorial and hosts the service in a console application.</span></span>  
  
 <span data-ttu-id="a0fda-169">Bu komut satırı derleyicisi ile derlemek için Iservice1.cs ve Service1.cs bir sınıf kitaplığı başvuran içine derleme `System.ServiceModel.dll`.</span><span class="sxs-lookup"><span data-stu-id="a0fda-169">To compile this with a command-line compiler, compile IService1.cs and Service1.cs into a class library referencing `System.ServiceModel.dll`.</span></span> <span data-ttu-id="a0fda-170">Ve Program.cs için bir konsol uygulaması derleme.</span><span class="sxs-lookup"><span data-stu-id="a0fda-170">And compile Program.cs to a console application.</span></span>  
  
```csharp
// IService1.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.Text;  
  
namespace GettingStartedLib  
{  
        [ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
        public interface ICalculator  
        {  
            [OperationContract]  
            double Add(double n1, double n2);  
            [OperationContract]  
            double Subtract(double n1, double n2);  
            [OperationContract]  
            double Multiply(double n1, double n2);  
            [OperationContract]  
            double Divide(double n1, double n2);  
        }  
}  
```  
  
```csharp
// Service1.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.Text;  
  
namespace GettingStartedLib  
{  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            double result = n1 + n2;  
            Console.WriteLine("Received Add({0},{1})", n1, n2);  
            // Code added to write output to the console window.  
            Console.WriteLine("Return: {0}", result);  
            return result;  
        }  
  
        public double Subtract(double n1, double n2)  
        {  
            double result = n1 - n2;  
            Console.WriteLine("Received Subtract({0},{1})", n1, n2);  
            Console.WriteLine("Return: {0}", result);  
            return result;  
        }  
  
        public double Multiply(double n1, double n2)  
        {  
            double result = n1 * n2;  
            Console.WriteLine("Received Multiply({0},{1})", n1, n2);  
            Console.WriteLine("Return: {0}", result);  
            return result;  
        }  
  
        public double Divide(double n1, double n2)  
        {  
            double result = n1 / n2;  
            Console.WriteLine("Received Divide({0},{1})", n1, n2);  
            Console.WriteLine("Return: {0}", result);  
            return result;  
        }  
    }  
}  
```  
  
```csharp
//Program.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.ServiceModel;  
using GettingStartedLib;  
using System.ServiceModel.Description;   
  
namespace GettingStartedHost  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // Step 1 of the address configuration procedure: Create a URI to serve as the base address.  
            Uri baseAddress = new Uri("http://localhost:8000/ServiceModelSamples/Service");  
  
            // Step 2 of the hosting procedure: Create ServiceHost  
            ServiceHost selfHost = new ServiceHost(typeof(CalculatorService), baseAddress);  
  
            try  
            {  
                // Step 3 of the hosting procedure: Add a service endpoint.  
                selfHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), "CalculatorService");  
  
                // Step 4 of the hosting procedure: Enable metadata exchange.  
                ServiceMetadataBehavior smb = new ServiceMetadataBehavior();  
                smb.HttpGetEnabled = true;  
                selfHost.Description.Behaviors.Add(smb);  
  
                // Step 5 of the hosting procedure: Start (and then stop) the service.  
                selfHost.Open();  
                Console.WriteLine("The service is ready.");  
                Console.WriteLine("Press <ENTER> to terminate service.");  
                Console.WriteLine();  
                Console.ReadLine();  
  
                // Close the ServiceHostBase to shutdown the service.  
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
'IService1.vb  
Imports System  
Imports System.ServiceModel  
  
Namespace GettingStartedLib  
  
    <ServiceContract(Namespace:="http://Microsoft.ServiceModel.Samples")> _  
    Public Interface ICalculator  
  
        <OperationContract()> _  
        Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double  
        <OperationContract()> _  
        Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double  
        <OperationContract()> _  
        Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double  
        <OperationContract()> _  
        Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double  
    End Interface  
End Namespace  
```  
  
```vb
'Service1.vb  
Imports System  
Imports System.ServiceModel  
  
Namespace GettingStartedLib  
  
    Public Class CalculatorService  
        Implements ICalculator  
  
        Public Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Add  
            Dim result As Double = n1 + n2  
            ' Code added to write output to the console window.  
            Console.WriteLine("Received Add({0},{1})", n1, n2)  
            Console.WriteLine("Return: {0}", result)  
            Return result  
        End Function  
  
        Public Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Subtract  
            Dim result As Double = n1 - n2  
            Console.WriteLine("Received Subtract({0},{1})", n1, n2)  
            Console.WriteLine("Return: {0}", result)  
            Return result  
  
        End Function  
  
        Public Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Multiply  
            Dim result As Double = n1 * n2  
            Console.WriteLine("Received Multiply({0},{1})", n1, n2)  
            Console.WriteLine("Return: {0}", result)  
            Return result  
  
        End Function  
  
        Public Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Divide  
            Dim result As Double = n1 / n2  
            Console.WriteLine("Received Divide({0},{1})", n1, n2)  
            Console.WriteLine("Return: {0}", result)  
            Return result  
  
        End Function  
    End Class  
End Namespace  
```  
  
```vb
'Module1.vb  
Imports System  
Imports System.ServiceModel  
Imports System.ServiceModel.Description  
Imports GettingStartedLibVB.GettingStartedLib  
  
Module Service  
  
    Class Program  
        Shared Sub Main()  
            ' Step 1 of the address configuration procedure: Create a URI to serve as the base address.  
            Dim baseAddress As New Uri("http://localhost:8000/ServiceModelSamples/Service")  
  
            ' Step 2 of the hosting procedure: Create ServiceHost  
            Dim selfHost As New ServiceHost(GetType(CalculatorService), baseAddress)  
            Try  
  
                ' Step 3 of the hosting procedure: Add a service endpoint.  
                ' Add a service endpoint  
                selfHost.AddServiceEndpoint( _  
                    GetType(ICalculator), _  
                    New WSHttpBinding(), _  
                    "CalculatorService")  
  
                ' Step 4 of the hosting procedure: Enable metadata exchange.  
                ' Enable metadata exchange  
                Dim smb As New ServiceMetadataBehavior()  
                smb.HttpGetEnabled = True  
                selfHost.Description.Behaviors.Add(smb)  
  
                ' Step 5 of the hosting procedure: Start (and then stop) the service.  
                selfHost.Open()  
                Console.WriteLine("The service is ready.")  
                Console.WriteLine("Press <ENTER> to terminate service.")  
                Console.WriteLine()  
                Console.ReadLine()  
  
                ' Close the ServiceHostBase to shutdown the service.  
                selfHost.Close()  
            Catch ce As CommunicationException  
                Console.WriteLine("An exception occurred: {0}", ce.Message)  
                selfHost.Abort()  
            End Try  
        End Sub  
    End Class  
  
End Module  
```  
  
> [!NOTE]
>  <span data-ttu-id="a0fda-171">Bu gibi hizmetlere HTTP adresleri dinlemek makinede kaydetme izni gerektirir.</span><span class="sxs-lookup"><span data-stu-id="a0fda-171">Services such as this one require permission to register HTTP addresses on the machine for listening.</span></span> <span data-ttu-id="a0fda-172">Yönetim hesapları, bu izne sahiptir, ancak yönetici olmayan hesapların HTTP ad alanları için izin verilmelidir.</span><span class="sxs-lookup"><span data-stu-id="a0fda-172">Administrator accounts have this permission, but non-administrator accounts must be granted permission for HTTP namespaces.</span></span> <span data-ttu-id="a0fda-173">Ad alanı ayırmaları yapılandırma hakkında daha fazla bilgi için bkz. [yapılandırma HTTP ve HTTPS](../../../docs/framework/wcf/feature-details/configuring-http-and-https.md).</span><span class="sxs-lookup"><span data-stu-id="a0fda-173">For more information about how to configure namespace reservations, see [Configuring HTTP and HTTPS](../../../docs/framework/wcf/feature-details/configuring-http-and-https.md).</span></span> <span data-ttu-id="a0fda-174">Visual Studio altında çalışırken, service.exe yönetici ayrıcalıklarıyla çalıştırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a0fda-174">When running under Visual Studio, the service.exe must be run with administrator privileges.</span></span>  
  
 <span data-ttu-id="a0fda-175">Artık hizmeti çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="a0fda-175">Now the service is running.</span></span> <span data-ttu-id="a0fda-176">Devam [nasıl yapılır: istemci oluşturma](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="a0fda-176">Proceed to [How to: Create a Client](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span> <span data-ttu-id="a0fda-177">Sorun giderme bilgileri için bkz: [Başlarken Öğreticisi sorun giderme](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="a0fda-177">For troubleshooting information, see [Troubleshooting the Getting Started Tutorial](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0fda-178">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a0fda-178">See Also</span></span>  
 [<span data-ttu-id="a0fda-179">Başlarken</span><span class="sxs-lookup"><span data-stu-id="a0fda-179">Getting Started</span></span>](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [<span data-ttu-id="a0fda-180">Kendini Barındırma</span><span class="sxs-lookup"><span data-stu-id="a0fda-180">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)
