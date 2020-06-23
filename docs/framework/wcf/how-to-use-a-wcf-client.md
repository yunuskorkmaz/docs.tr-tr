---
title: 'Öğretici: Windows Communication Foundation istemci kullanma'
description: Bir istemci örneği oluşturmayı, uygulamayı derlemeyi ve bir hizmet ile iletişim kurmayı, bir WCF uygulaması oluşturma hakkında bir makale serisinin parçası olarak nasıl iletişim kuracağınızı öğrenin.
ms.date: 03/19/2019
helpviewer_keywords:
- WCF clients [WCF], using
dev_langs:
- CSharp
- VB
ms.assetid: 190349fc-0573-49c7-bb85-8e316df7f31f
ms.openlocfilehash: 5c94d5f8af679580c4194aaaadeda759098953d2
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244341"
---
# <a name="tutorial-use-a-windows-communication-foundation-client"></a><span data-ttu-id="fb0e7-103">Öğretici: Windows Communication Foundation istemci kullanma</span><span class="sxs-lookup"><span data-stu-id="fb0e7-103">Tutorial: Use a Windows Communication Foundation client</span></span>

<span data-ttu-id="fb0e7-104">Bu öğreticide, temel Windows Communication Foundation (WCF) uygulaması oluşturmak için gereken beş görevin son açıklaması açıklanır.</span><span class="sxs-lookup"><span data-stu-id="fb0e7-104">This tutorial describes the last of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="fb0e7-105">Öğreticilere genel bakış için bkz. [öğretici: Windows Communication Foundation uygulamalarla çalışmaya başlama](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="fb0e7-105">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="fb0e7-106">Bir Windows Communication Foundation (WCF) proxy oluşturup yapılandırdıktan sonra, bir istemci örneği oluşturup istemci uygulamasını derleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fb0e7-106">After you've created and configured a Windows Communication Foundation (WCF) proxy, you create a client instance and compile the client application.</span></span> <span data-ttu-id="fb0e7-107">Daha sonra WCF hizmeti ile iletişim kurmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fb0e7-107">You then use it to communicate with the WCF service.</span></span>

<span data-ttu-id="fb0e7-108">Bu öğreticide aşağıdakilerin nasıl yapılacağını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="fb0e7-108">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="fb0e7-109">WCF istemcisini kullanmak için kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fb0e7-109">Add code to use the WCF client.</span></span>
> - <span data-ttu-id="fb0e7-110">WCF istemcisini test edin.</span><span class="sxs-lookup"><span data-stu-id="fb0e7-110">Test the WCF client.</span></span>

## <a name="add-code-to-use-the-wcf-client"></a><span data-ttu-id="fb0e7-111">WCF istemcisini kullanmak için kod ekleme</span><span class="sxs-lookup"><span data-stu-id="fb0e7-111">Add code to use the WCF client</span></span>

<span data-ttu-id="fb0e7-112">İstemci kodu aşağıdaki adımları yapar:</span><span class="sxs-lookup"><span data-stu-id="fb0e7-112">The client code does the following steps:</span></span>

- <span data-ttu-id="fb0e7-113">WCF istemcisini başlatır.</span><span class="sxs-lookup"><span data-stu-id="fb0e7-113">Instantiates the WCF client.</span></span>
- <span data-ttu-id="fb0e7-114">Oluşturulan proxy 'den hizmet işlemlerini çağırır.</span><span class="sxs-lookup"><span data-stu-id="fb0e7-114">Calls the service operations from the generated proxy.</span></span>
- <span data-ttu-id="fb0e7-115">İşlem çağrısı tamamlandıktan sonra istemciyi kapatır.</span><span class="sxs-lookup"><span data-stu-id="fb0e7-115">Closes the client after the operation call is completed.</span></span>

<span data-ttu-id="fb0e7-116">**GettingStartedClient** projesinden **program.cs** veya **Module1. vb** dosyasını açın ve kodunu aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="fb0e7-116">Open the **Program.cs** or **Module1.vb** file from the **GettingStartedClient** project and replace its code with the following code:</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GettingStartedClient.ServiceReference1;

namespace GettingStartedClient
{
    class Program
    {
        static void Main(string[] args)
        {
            //Step 1: Create an instance of the WCF proxy.
            CalculatorClient client = new CalculatorClient();

            // Step 2: Call the service operations.
            // Call the Add service operation.
            double value1 = 100.00D;
            double value2 = 15.99D;
            double result = client.Add(value1, value2);
            Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);

            // Call the Subtract service operation.
            value1 = 145.00D;
            value2 = 76.54D;
            result = client.Subtract(value1, value2);
            Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);

            // Call the Multiply service operation.
            value1 = 9.00D;
            value2 = 81.25D;
            result = client.Multiply(value1, value2);
            Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);

            // Call the Divide service operation.
            value1 = 22.00D;
            value2 = 7.00D;
            result = client.Divide(value1, value2);
            Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);

            // Step 3: Close the client to gracefully close the connection and clean up resources.
            Console.WriteLine("\nPress <Enter> to terminate the client.");
            Console.ReadLine();
            client.Close();
        }
    }
}
```

```vb
Imports System.Collections.Generic
Imports System.Text
Imports System.ServiceModel
Imports GettingStartedClient.ServiceReference1

Module Module1

    Sub Main()
        ' Step 1: Create an instance of the WCF proxy.
        Dim Client As New CalculatorClient()

        ' Step 2: Call the service operations.
        ' Call the Add service operation.
        Dim value1 As Double = 100D
        Dim value2 As Double = 15.99D
        Dim result As Double = Client.Add(value1, value2)
        Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result)

        ' Call the Subtract service operation.
        value1 = 145D
        value2 = 76.54D
        result = Client.Subtract(value1, value2)
        Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result)

        ' Call the Multiply service operation.
        value1 = 9D
        value2 = 81.25D
        result = Client.Multiply(value1, value2)
        Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result)

        ' Call the Divide service operation.
        value1 = 22D
        value2 = 7D
        result = Client.Divide(value1, value2)
        Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result)

        ' Step 3: Close the client to gracefully close the connection and clean up resources.
        Console.WriteLine()
        Console.WriteLine("Press <Enter> to terminate the client.")
        Console.ReadLine()
        Client.Close()

    End Sub

End Module
```

<span data-ttu-id="fb0e7-117">`using`İçeri aktaran (Visual C# için) veya `Imports` (for Visual Basic) bildirimine dikkat edin `GettingStartedClient.ServiceReference1` .</span><span class="sxs-lookup"><span data-stu-id="fb0e7-117">Notice the `using` (for Visual C#) or `Imports` (for Visual Basic) statement that imports `GettingStartedClient.ServiceReference1`.</span></span> <span data-ttu-id="fb0e7-118">Bu ifade, Visual Studio 'Nun **hizmet başvurusu Ekle** işleviyle oluşturduğu kodu içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="fb0e7-118">This statement imports the code that Visual Studio generated with the **Add Service Reference** function.</span></span> <span data-ttu-id="fb0e7-119">Kod, WCF ara sunucusunu başlatır ve hesap makinesi hizmetinin sunduğu hizmet işlemlerinin her birini çağırır.</span><span class="sxs-lookup"><span data-stu-id="fb0e7-119">The code instantiates the WCF proxy and calls each of the service operations that the calculator service exposes.</span></span> <span data-ttu-id="fb0e7-120">Ardından, proxy 'yi kapatır ve programı sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="fb0e7-120">It then closes the proxy and ends the program.</span></span>

## <a name="test-the-wcf-client"></a><span data-ttu-id="fb0e7-121">WCF istemcisini test etme</span><span class="sxs-lookup"><span data-stu-id="fb0e7-121">Test the WCF client</span></span>

### <a name="test-the-application-from-visual-studio"></a><span data-ttu-id="fb0e7-122">Uygulamayı Visual Studio 'dan test etme</span><span class="sxs-lookup"><span data-stu-id="fb0e7-122">Test the application from Visual Studio</span></span>

1. <span data-ttu-id="fb0e7-123">Çözümü kaydedin ve oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fb0e7-123">Save and build the solution.</span></span>

2. <span data-ttu-id="fb0e7-124">**GettingStartedLib** klasörünü seçin ve ardından kısayol menüsünde **Başlangıç projesi olarak ayarla** ' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="fb0e7-124">Select the **GettingStartedLib** folder, and then select **Set as Startup Project** from the shortcut menu.</span></span>

3. <span data-ttu-id="fb0e7-125">**Başlangıç projeleri**' nden, açılan listeden **GettingStartedLib** ' i seçin, sonra **Çalıştır** ' ı seçin veya **F5**tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="fb0e7-125">From **Startup Projects**, select **GettingStartedLib** from the drop-down list, then select **Run** or press **F5**.</span></span>

### <a name="test-the-application-from-a-command-prompt"></a><span data-ttu-id="fb0e7-126">Uygulamayı bir komut isteminden test etme</span><span class="sxs-lookup"><span data-stu-id="fb0e7-126">Test the application from a command prompt</span></span>

1. <span data-ttu-id="fb0e7-127">Yönetici olarak bir komut istemi açın ve ardından Visual Studio çözüm dizininize gidin.</span><span class="sxs-lookup"><span data-stu-id="fb0e7-127">Open a command prompt as an administrator, and then navigate to your Visual Studio solution directory.</span></span>

2. <span data-ttu-id="fb0e7-128">Hizmeti başlatmak için: *GettingStartedHost\bin\Debug\GettingStartedHost.exe*girin.</span><span class="sxs-lookup"><span data-stu-id="fb0e7-128">To start the service: Enter *GettingStartedHost\bin\Debug\GettingStartedHost.exe*.</span></span>

3. <span data-ttu-id="fb0e7-129">İstemcisini başlatmak için: başka bir komut istemi açın, Visual Studio çözüm dizininize gidin ve *GettingStartedClient\bin\Debug\GettingStartedClient.exe*girin.</span><span class="sxs-lookup"><span data-stu-id="fb0e7-129">To start the client: Open another command prompt, navigate to your Visual Studio solution directory, then enter *GettingStartedClient\bin\Debug\GettingStartedClient.exe*.</span></span>

   <span data-ttu-id="fb0e7-130">*GettingStartedHost.exe* aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="fb0e7-130">*GettingStartedHost.exe* produces the following output:</span></span>

   ```text
   The service is ready.
   Press <Enter> to terminate the service.

   Received Add(100,15.99)
   Return: 115.99
   Received Subtract(145,76.54)
   Return: 68.46
   Received Multiply(9,81.25)
   Return: 731.25
   Received Divide(22,7)
   Return: 3.14285714285714
   ```

   <span data-ttu-id="fb0e7-131">*GettingStartedClient.exe* aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="fb0e7-131">*GettingStartedClient.exe* produces the following output:</span></span>

   ```text
   Add(100,15.99) = 115.99
   Subtract(145,76.54) = 68.46
   Multiply(9,81.25) = 731.25
   Divide(22,7) = 3.14285714285714

   Press <Enter> to terminate the client.
   ```

## <a name="next-steps"></a><span data-ttu-id="fb0e7-132">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="fb0e7-132">Next steps</span></span>

<span data-ttu-id="fb0e7-133">Artık WCF başlangıç öğreticisindeki tüm görevleri tamamladınız.</span><span class="sxs-lookup"><span data-stu-id="fb0e7-133">You've now completed all the tasks in the WCF get started tutorial.</span></span> <span data-ttu-id="fb0e7-134">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="fb0e7-134">In this tutorial, you learned how to:</span></span>

<span data-ttu-id="fb0e7-135">Bu öğreticide aşağıdakilerin nasıl yapılacağını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="fb0e7-135">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="fb0e7-136">WCF istemcisini kullanmak için kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fb0e7-136">Add code to use the WCF client.</span></span>
> - <span data-ttu-id="fb0e7-137">WCF istemcisini test edin.</span><span class="sxs-lookup"><span data-stu-id="fb0e7-137">Test the WCF client.</span></span>

<span data-ttu-id="fb0e7-138">Adımlardan birinde sorun veya hatalar varsa, bunları gidermek için sorun giderme makalesindeki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="fb0e7-138">If you have problems or errors in any of the steps, follow the steps in the troubleshooting article to fix them.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="fb0e7-139">WCF öğreticileri ile çalışmaya başlama hakkında sorun giderme</span><span class="sxs-lookup"><span data-stu-id="fb0e7-139">Troubleshoot the Get started with WCF tutorials</span></span>](troubleshooting-the-getting-started-tutorial.md)
