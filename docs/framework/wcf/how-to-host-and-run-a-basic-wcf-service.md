---
title: 'Nasıl Yapılır: Barındırma ve çalıştırma temel Windows Communication Foundation servisi'
ms.date: 09/14/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF services [WCF]
- WCF services [WCF], running
ms.assetid: 31774d36-923b-4e2d-812e-aa190127266f
ms.openlocfilehash: 710ccd69d7b0f8cd8cd3e04729fd952308a3fb4a
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53129382"
---
# <a name="how-to-host-and-run-a-basic-windows-communication-foundation-service"></a><span data-ttu-id="78045-102">Nasıl Yapılır: Barındırma ve çalıştırma temel Windows Communication Foundation servisi</span><span class="sxs-lookup"><span data-stu-id="78045-102">How to: Host and Run a Basic Windows Communication Foundation Service</span></span>

<span data-ttu-id="78045-103">Üçüncü altı görev bir Windows Communication Foundation (WCF) uygulaması oluşturmak için gereken budur.</span><span class="sxs-lookup"><span data-stu-id="78045-103">This is the third of six tasks required to create a Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="78045-104">Tüm altı görevleri genel bakış için bkz. [başlangıç Öğreticisi](../../../docs/framework/wcf/getting-started-tutorial.md) konu.</span><span class="sxs-lookup"><span data-stu-id="78045-104">For an overview of all six of the tasks, see the [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md) topic.</span></span>

<span data-ttu-id="78045-105">Bu konu, bir Windows Communication Foundation (WCF) hizmeti bir konsol uygulamasında barındırma açıklar.</span><span class="sxs-lookup"><span data-stu-id="78045-105">This topic describes how to host a Windows Communication Foundation (WCF) service in a console application.</span></span> <span data-ttu-id="78045-106">Bu yordam, aşağıdaki adımlardan oluşur:</span><span class="sxs-lookup"><span data-stu-id="78045-106">This procedure consists of the following steps:</span></span>

- <span data-ttu-id="78045-107">Hizmeti barındırmak için bir konsol uygulama projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="78045-107">Create a console application project to host the service.</span></span>

- <span data-ttu-id="78045-108">Hizmet konak hizmeti oluşturun.</span><span class="sxs-lookup"><span data-stu-id="78045-108">Create a service host for the service.</span></span>

- <span data-ttu-id="78045-109">Meta veri değişimi etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="78045-109">Enable metadata exchange.</span></span>

- <span data-ttu-id="78045-110">Hizmet ana bilgisayarı açın.</span><span class="sxs-lookup"><span data-stu-id="78045-110">Open the service host.</span></span>

<span data-ttu-id="78045-111">Bu görevde yazılan kodların tam listesi yordamdan örnekte sağlanır.</span><span class="sxs-lookup"><span data-stu-id="78045-111">A complete listing of the code written in this task is provided in the example following the procedure.</span></span>

## <a name="create-a-new-console-application-to-host-the-service"></a><span data-ttu-id="78045-112">Hizmeti barındırmak için yeni bir konsol uygulaması oluşturun</span><span class="sxs-lookup"><span data-stu-id="78045-112">Create a new console application to host the service</span></span>

1. <span data-ttu-id="78045-113">Başlarken çözüm üzerinde sağ tıklatıp seçerek Visual Studio'da yeni bir konsol uygulaması projesi oluşturma **Ekle** > **yeni proje**.</span><span class="sxs-lookup"><span data-stu-id="78045-113">Create a new Console Application project in Visual Studio by right-clicking on the Getting Started solution and selecting **Add** > **New Project**.</span></span> <span data-ttu-id="78045-114">İçinde **Yeni Proje Ekle** seçin sol taraftaki iletişim **Windows Masaüstü** kategorisi altında **Visual C#** veya **Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="78045-114">In the **Add New Project** dialog, on the left-hand side, select the **Windows Desktop** category under **Visual C#** or **Visual Basic**.</span></span> <span data-ttu-id="78045-115">Seçin **konsol uygulaması (.NET Framework)** şablonu ve ardından ad proje **GettingStartedHost**.</span><span class="sxs-lookup"><span data-stu-id="78045-115">Select the **Console App (.NET Framework)** template, and then name the project **GettingStartedHost**.</span></span>

2. <span data-ttu-id="78045-116">GettingStartedHost projeye GettingStartedLib projeye bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="78045-116">Add a reference to the GettingStartedLib project to the GettingStartedHost project.</span></span> <span data-ttu-id="78045-117">Sağ **başvuruları** klasörü altında GettingStartedHost projede **Çözüm Gezgini**ve ardından **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="78045-117">Right-click on the **References** folder under the GettingStartedHost project in **Solution Explorer**, and then select **Add Reference**.</span></span> <span data-ttu-id="78045-118">İçinde **Başvuru Ekle** iletişim kutusunda **çözüm** iletişim kutusunun sol taraftaki GettingStartedLib iletişim kutusunun orta kısmını seçin ve ardından **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="78045-118">In the **Add Reference** dialog, select **Solution** on the left-hand side of the dialog, select GettingStartedLib in the center section of the dialog, and then choose **Add**.</span></span> <span data-ttu-id="78045-119">Bu, GettingStartedLib GettingStartedHost projesi için tanımlanan türleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="78045-119">This makes the types defined in GettingStartedLib available to the GettingStartedHost project.</span></span>

3. <span data-ttu-id="78045-120">System.ServiceModel başvuru GettingStartedHost projeye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="78045-120">Add a reference to System.ServiceModel to the GettingStartedHost project.</span></span> <span data-ttu-id="78045-121">Sağ **başvuruları** klasörü altında GettingStartedHost projede **Çözüm Gezgini** seçip **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="78045-121">Right-click the **References** folder under the GettingStartedHost project in **Solution Explorer** and select **Add Reference**.</span></span> <span data-ttu-id="78045-122">İçinde **Başvuru Ekle** iletişim kutusunda **Framework** iletişim kutusunun sol taraftaki **derlemeleri**.</span><span class="sxs-lookup"><span data-stu-id="78045-122">In the **Add Reference** dialog, select **Framework** on the left-hand side of the dialog under **Assemblies**.</span></span> <span data-ttu-id="78045-123">Bulmak ve seçmek **System.ServiceModel**ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="78045-123">Find and select **System.ServiceModel**, and then choose **OK**.</span></span> <span data-ttu-id="78045-124">Çözüm seçerek Kaydet **dosya** > **Tümünü Kaydet**.</span><span class="sxs-lookup"><span data-stu-id="78045-124">Save the solution by selecting **File** > **Save All**.</span></span>

## <a name="host-the-service"></a><span data-ttu-id="78045-125">Hizmeti barındırma</span><span class="sxs-lookup"><span data-stu-id="78045-125">Host the service</span></span>

<span data-ttu-id="78045-126">Program.cs veya Module.vb dosyasını açın ve aşağıdaki kodu girin:</span><span class="sxs-lookup"><span data-stu-id="78045-126">Open the Program.cs or Module.vb file and enter the following code:</span></span>

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

<span data-ttu-id="78045-127">**1. adım** -hizmetin taban adresi için URI sınıf örneği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="78045-127">**Step 1** - Creates an instance of the Uri class to hold the base address of the service.</span></span> <span data-ttu-id="78045-128">Hizmetleri, bir taban adresi içeren bir URL ve isteğe bağlı bir URI tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="78045-128">Services are identified by a URL which contains a base address and an optional URI.</span></span> <span data-ttu-id="78045-129">Temel adres gibi biçimlendirilir: [aktarım] :// [makine adı veya etki alanı] [: isteğe bağlı bağlantı noktası #] / [isteğe bağlı URI segmenti] HTTP aktarımı hesaplayıcı hizmeti temel adresi kullanır, segment "GettingStarted" localhost, 8000 numaralı bağlantı noktasını ve URI</span><span class="sxs-lookup"><span data-stu-id="78045-129">The base address is formatted as follows:[transport]://[machine-name or domain][:optional port #]/[optional URI segment]The base address for the calculator service uses the HTTP transport, localhost, port 8000, and the URI segment "GettingStarted"</span></span>

<span data-ttu-id="78045-130">**2. adım** – bir örneğini oluşturur <xref:System.ServiceModel.ServiceHost> Hizmeti'ni barındıracak şekilde sınıfı.</span><span class="sxs-lookup"><span data-stu-id="78045-130">**Step 2** – Creates an instance of the <xref:System.ServiceModel.ServiceHost> class to host the service.</span></span> <span data-ttu-id="78045-131">Oluşturucu, iki parametre, hizmet sözleşmesi uygulayan sınıf türünü ve hizmetin taban adresi alır.</span><span class="sxs-lookup"><span data-stu-id="78045-131">The constructor takes two parameters, the type of the class that implements the service contract, and the base address of the service.</span></span>

<span data-ttu-id="78045-132">**3. adım** – oluşturur bir <xref:System.ServiceModel.Description.ServiceEndpoint> örneği.</span><span class="sxs-lookup"><span data-stu-id="78045-132">**Step 3** – Creates a <xref:System.ServiceModel.Description.ServiceEndpoint> instance.</span></span> <span data-ttu-id="78045-133">Hizmet uç noktası bir adresi, bağlama ve hizmet sözleşmesi oluşur.</span><span class="sxs-lookup"><span data-stu-id="78045-133">A service endpoint is composed of an address, a binding, and a service contract.</span></span> <span data-ttu-id="78045-134"><xref:System.ServiceModel.Description.ServiceEndpoint> Oluşturucusu bu nedenle hizmet sözleşme arabirimi türü, bağlama ve bir adresi alır.</span><span class="sxs-lookup"><span data-stu-id="78045-134">The <xref:System.ServiceModel.Description.ServiceEndpoint> constructor therefore takes the service contract interface type, a binding, and an address.</span></span> <span data-ttu-id="78045-135">Hizmet sözleşme `ICalculator`, tanımlanan ve hizmet türüne uygulayın.</span><span class="sxs-lookup"><span data-stu-id="78045-135">The service contract is `ICalculator`, which you defined and implement in the service type.</span></span> <span data-ttu-id="78045-136">Bu örnekte kullanılan bağlamanın <xref:System.ServiceModel.WSHttpBinding> WS - için uygun uç noktalarına bağlamak için kullanılan yerleşik bir bağlama olduğu \* belirtimleri.</span><span class="sxs-lookup"><span data-stu-id="78045-136">The binding used in this sample is <xref:System.ServiceModel.WSHttpBinding> which is a built-in binding that is used for connecting to endpoints that conform to the WS-\* specifications.</span></span> <span data-ttu-id="78045-137">WCF bağlamaları hakkında daha fazla bilgi için bkz: [WCF bağlamaları genel bakış](../../../docs/framework/wcf/bindings-overview.md).</span><span class="sxs-lookup"><span data-stu-id="78045-137">For more information about WCF bindings, see [WCF Bindings Overview](../../../docs/framework/wcf/bindings-overview.md).</span></span> <span data-ttu-id="78045-138">Adres, uç noktayı tanımlamak için taban adresi olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="78045-138">The address is appended to the base address to identify the endpoint.</span></span> <span data-ttu-id="78045-139">Tam uç nokta adresi "CalculatorService" Bu kodu belirtilen adresi olduğundan `"http://localhost:8000/GettingStarted/CalculatorService"`.</span><span class="sxs-lookup"><span data-stu-id="78045-139">The address specified in this code is "CalculatorService" so the fully qualified address for the endpoint is `"http://localhost:8000/GettingStarted/CalculatorService"`.</span></span>

    > [!IMPORTANT]
    > Adding a service endpoint is optional when using .NET Framework 4 or later. In these versions, if no endpoints are added in code or configuration, WCF adds one default endpoint for each combination of base address and contract implemented by the service. For more information about default endpoints see [Specifying an Endpoint Address](../../../docs/framework/wcf/specifying-an-endpoint-address.md). For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).

<span data-ttu-id="78045-140">**4. adım** – meta veri değişimi etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="78045-140">**Step 4** – Enable metadata exchange.</span></span> <span data-ttu-id="78045-141">İstemciler, meta veri değişimi, hizmet işlemlerini aramak için kullanılacak proxy üretmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="78045-141">Clients will use metadata exchange to generate proxies that will be used to call the service operations.</span></span> <span data-ttu-id="78045-142">Etkinleştirmek için meta veri değişimi oluşturma bir <xref:System.ServiceModel.Description.ServiceMetadataBehavior> ayarlayın, örnek 's <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> özelliğini `true`ve davranışların eklenmesi <!--zz <xref:System.ServiceModel.ServiceHost.Behaviors%2A>  --> `System.ServiceModel.ServiceHost.Behaviors%2A` koleksiyonunu <xref:System.ServiceModel.ServiceHost> örneği.</span><span class="sxs-lookup"><span data-stu-id="78045-142">To enable metadata exchange create a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance, set it’s <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> property to `true`, and add the behavior to the <!--zz <xref:System.ServiceModel.ServiceHost.Behaviors%2A>  -->`System.ServiceModel.ServiceHost.Behaviors%2A` collection of the <xref:System.ServiceModel.ServiceHost> instance.</span></span>

<span data-ttu-id="78045-143">**5. adım** – açık <xref:System.ServiceModel.ServiceHost> gelen iletileri dinlemek için.</span><span class="sxs-lookup"><span data-stu-id="78045-143">**Step 5** – Open the <xref:System.ServiceModel.ServiceHost> to listen for incoming messages.</span></span> <span data-ttu-id="78045-144">Uyarı kodunu kullanıcının isabet bekler girin.</span><span class="sxs-lookup"><span data-stu-id="78045-144">Notice the code waits for the user to hit enter.</span></span> <span data-ttu-id="78045-145">Bunu yaparsanız, uygulamayı hemen kapatmak ve hizmet kapanır. Bir try/catch bloğu kullanılan dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="78045-145">If you do not do this, the app will close immediately and the service will shut down.Also notice a  try/catch block used.</span></span> <span data-ttu-id="78045-146">Sonra <xref:System.ServiceModel.ServiceHost> olmuştur örneği, diğer tüm kod bir try/catch bloğu içinde yer alır.</span><span class="sxs-lookup"><span data-stu-id="78045-146">After the <xref:System.ServiceModel.ServiceHost> has been instantiated, all other code is placed in a try/catch block.</span></span> <span data-ttu-id="78045-147">Güvenli bir şekilde tarafından oluşturulan özel durumları yakalama hakkında daha fazla bilgi için <xref:System.ServiceModel.ServiceHost>, bkz: [kullanım Kapat ve iptal WCF istemci kaynakları serbest bırakmak için](../../../docs/framework/wcf/samples/use-close-abort-release-wcf-client-resources.md)</span><span class="sxs-lookup"><span data-stu-id="78045-147">For more information about safely catching exceptions thrown by <xref:System.ServiceModel.ServiceHost>, see [Use Close and Abort to release WCF client resources](../../../docs/framework/wcf/samples/use-close-abort-release-wcf-client-resources.md)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="78045-148">App.config dosyasında GettingStartedLib kodunda yaptığınız değişiklikleri yansıtacak şekilde düzenleyin:</span><span class="sxs-lookup"><span data-stu-id="78045-148">Edit App.config in GettingStartedLib to reflect the changes made in code:</span></span>
> 1. <span data-ttu-id="78045-149">14. satır için değiştirin `<service name="GettingStartedLib.CalculatorService">`</span><span class="sxs-lookup"><span data-stu-id="78045-149">Change line 14 to `<service name="GettingStartedLib.CalculatorService">`</span></span>
> 2. <span data-ttu-id="78045-150">17 satırına değiştirme `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span><span class="sxs-lookup"><span data-stu-id="78045-150">Change line 17 to `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span></span>
> 3. <span data-ttu-id="78045-151">Satır 22 için değiştirin `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`</span><span class="sxs-lookup"><span data-stu-id="78045-151">Change line 22 to `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`</span></span>

## <a name="verify-the-service-is-working"></a><span data-ttu-id="78045-152">Hizmetinin çalıştığını doğrulayın</span><span class="sxs-lookup"><span data-stu-id="78045-152">Verify the service is working</span></span>

1. <span data-ttu-id="78045-153">GettingStartedHost konsolunu çalıştıran Visual Studio içinde uygulama.</span><span class="sxs-lookup"><span data-stu-id="78045-153">Run the GettingStartedHost console application from inside Visual Studio.</span></span>

   <span data-ttu-id="78045-154">Hizmet, yönetici ayrıcalıklarıyla çalıştırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="78045-154">The service must be run with administrator privileges.</span></span> <span data-ttu-id="78045-155">Visual Studio'yu yönetici ayrıcalıklarıyla açılmış olduğundan GettingStartedHost da yönetici ayrıcalıklarıyla çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="78045-155">Because Visual Studio was opened with administrator privileges, GettingStartedHost is also run with administrator privileges.</span></span> <span data-ttu-id="78045-156">Yeni bir komut istemi kullanarak da açabilirsiniz **yönetici olarak çalıştır** ve içerdiği service.exe çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="78045-156">You can also open a new command prompt using **Run as administrator** and run service.exe within it.</span></span>

2. <span data-ttu-id="78045-157">Bir web tarayıcısı açın ve hizmet hata ayıklama sayfasına göz atın `http://localhost:8000/GettingStarted/CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="78045-157">Open a web browser and browse to the service's debug page at `http://localhost:8000/GettingStarted/CalculatorService`.</span></span>

## <a name="example"></a><span data-ttu-id="78045-158">Örnek</span><span class="sxs-lookup"><span data-stu-id="78045-158">Example</span></span>

<span data-ttu-id="78045-159">Aşağıdaki örnek, hizmet sözleşmesini ve önceki adımdan öğreticide içerir ve hizmeti bir konsol uygulamasında barındırır.</span><span class="sxs-lookup"><span data-stu-id="78045-159">The following example includes the service contract and implementation from previous steps in the tutorial and hosts the service in a console application.</span></span>

<span data-ttu-id="78045-160">Bu komut satırı derleyicisi ile derlemek için Iservice1.cs ve Service1.cs başvuran bir sınıf kitaplığı derleme `System.ServiceModel.dll`.</span><span class="sxs-lookup"><span data-stu-id="78045-160">To compile this with a command-line compiler, compile IService1.cs and Service1.cs into a class library that references `System.ServiceModel.dll`.</span></span> <span data-ttu-id="78045-161">Program.cs bir konsol uygulaması olarak derleyin.</span><span class="sxs-lookup"><span data-stu-id="78045-161">Compile Program.cs as a console application.</span></span>

```csharp
using System;
using System.ServiceModel;

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
using System;
using System.ServiceModel;

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
> <span data-ttu-id="78045-162">Bu gibi hizmetlere HTTP adresleri dinlemek makinede kaydetme izni gerektirir.</span><span class="sxs-lookup"><span data-stu-id="78045-162">Services such as this one require permission to register HTTP addresses on the machine for listening.</span></span> <span data-ttu-id="78045-163">Yönetim hesapları, bu izne sahiptir, ancak yönetici olmayan hesapların HTTP ad alanları için izin verilmelidir.</span><span class="sxs-lookup"><span data-stu-id="78045-163">Administrator accounts have this permission, but non-administrator accounts must be granted permission for HTTP namespaces.</span></span> <span data-ttu-id="78045-164">Ad alanı ayırmaları yapılandırma hakkında daha fazla bilgi için bkz. [yapılandırma HTTP ve HTTPS](../../../docs/framework/wcf/feature-details/configuring-http-and-https.md).</span><span class="sxs-lookup"><span data-stu-id="78045-164">For more information about how to configure namespace reservations, see [Configuring HTTP and HTTPS](../../../docs/framework/wcf/feature-details/configuring-http-and-https.md).</span></span> <span data-ttu-id="78045-165">Visual Studio altında çalışırken, service.exe yönetici ayrıcalıklarıyla çalıştırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="78045-165">When running under Visual Studio, the service.exe must be run with administrator privileges.</span></span>

## <a name="next-steps"></a><span data-ttu-id="78045-166">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="78045-166">Next steps</span></span>

<span data-ttu-id="78045-167">Artık hizmeti çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="78045-167">Now the service is running.</span></span> <span data-ttu-id="78045-168">Sonraki görevde bir WCF istemcisi oluşturma.</span><span class="sxs-lookup"><span data-stu-id="78045-168">In the next task, you create a WCF client.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="78045-169">Nasıl Yapılır: Bir WCF istemcisi oluşturma</span><span class="sxs-lookup"><span data-stu-id="78045-169">How to: Create a WCF client</span></span>](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)

<span data-ttu-id="78045-170">Sorun giderme bilgileri için bkz: [Başlarken Öğreticisi sorun giderme](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="78045-170">For troubleshooting information, see [Troubleshooting the Getting Started Tutorial](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="78045-171">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="78045-171">See also</span></span>

- [<span data-ttu-id="78045-172">Başlarken</span><span class="sxs-lookup"><span data-stu-id="78045-172">Getting Started</span></span>](../../../docs/framework/wcf/samples/getting-started-sample.md)
- [<span data-ttu-id="78045-173">Kendini Barındırma</span><span class="sxs-lookup"><span data-stu-id="78045-173">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)