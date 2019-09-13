---
title: 'Öğretici: Windows Communication Foundation hizmet sözleşmesi uygulama'
ms.date: 03/19/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], implementing
ms.assetid: d5ab51ba-61ae-403e-b3c8-e2669e326806
ms.openlocfilehash: 05923dc0a2223da5e5fcda483abc1ee1dd2d643f
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928706"
---
# <a name="tutorial-implement-a-windows-communication-foundation-service-contract"></a><span data-ttu-id="19ce3-102">Öğretici: Windows Communication Foundation hizmet sözleşmesi uygulama</span><span class="sxs-lookup"><span data-stu-id="19ce3-102">Tutorial: Implement a Windows Communication Foundation service contract</span></span>

<span data-ttu-id="19ce3-103">Bu öğreticide, temel bir Windows Communication Foundation (WCF) uygulaması oluşturmak için gereken beş görevin ikinci açıklaması açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="19ce3-103">This tutorial describes the second of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="19ce3-104">Öğreticilere genel bakış için bkz [. Öğretici: Windows Communication Foundation uygulamaları](getting-started-tutorial.md)ile çalışmaya başlayın.</span><span class="sxs-lookup"><span data-stu-id="19ce3-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="19ce3-105">Bir WCF uygulaması oluşturmaya yönelik sonraki adım, önceki adımda oluşturduğunuz WCF hizmeti arabirimini uygulamak için kod eklemektir.</span><span class="sxs-lookup"><span data-stu-id="19ce3-105">The next step for creating a WCF application is to add code to implement the WCF service interface that you created in the previous step.</span></span> <span data-ttu-id="19ce3-106">Bu adımda, Kullanıcı tanımlı `CalculatorService` `ICalculator` arabirimi uygulayan adlı bir sınıf oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="19ce3-106">In this step, you create a class named `CalculatorService` that implements the user-defined `ICalculator` interface.</span></span> <span data-ttu-id="19ce3-107">Aşağıdaki koddaki her bir yöntem bir Hesaplayıcı işlemini çağırır ve test etmek üzere konsola metin yazar.</span><span class="sxs-lookup"><span data-stu-id="19ce3-107">Each method in the following code calls a calculator operation and writes text to the console to test it.</span></span> 

<span data-ttu-id="19ce3-108">Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="19ce3-108">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="19ce3-109">WCF hizmet sözleşmesini uygulamak için kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="19ce3-109">Add code to implement the WCF service contract.</span></span>
> - <span data-ttu-id="19ce3-110">Çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="19ce3-110">Build the solution.</span></span>

## <a name="add-code-to-implement-the-wcf-service-contract"></a><span data-ttu-id="19ce3-111">WCF hizmet sözleşmesini uygulamak için kod ekleme</span><span class="sxs-lookup"><span data-stu-id="19ce3-111">Add code to implement the WCF service contract</span></span>

<span data-ttu-id="19ce3-112">**GettingStartedLib**içinde **Service1.cs** veya **Service1. vb** dosyasını açın ve kodunu aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="19ce3-112">In **GettingStartedLib**, open the **Service1.cs** or **Service1.vb** file and replace its code with the following code:</span></span>

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

## <a name="edit-appconfig"></a><span data-ttu-id="19ce3-113">App. config dosyasını Düzenle</span><span class="sxs-lookup"><span data-stu-id="19ce3-113">Edit App.config</span></span>

<span data-ttu-id="19ce3-114">Kodda yaptığınız değişiklikleri yansıtmak için **GettingStartedLib** içinde **app. config dosyasını** düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="19ce3-114">Edit **App.config** in **GettingStartedLib** to reflect the changes you made to the code.</span></span>

- <span data-ttu-id="19ce3-115">Görsel C# projeler için:</span><span class="sxs-lookup"><span data-stu-id="19ce3-115">For Visual C# projects:</span></span>
  - <span data-ttu-id="19ce3-116">14 satırı olarak değiştir`<service name="GettingStartedLib.CalculatorService">`</span><span class="sxs-lookup"><span data-stu-id="19ce3-116">Change line 14 to `<service name="GettingStartedLib.CalculatorService">`</span></span>
  - <span data-ttu-id="19ce3-117">17. satırı olarak değiştir`<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span><span class="sxs-lookup"><span data-stu-id="19ce3-117">Change line 17 to `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span></span>
  - <span data-ttu-id="19ce3-118">Satır 22 ' i Değiştir`<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`</span><span class="sxs-lookup"><span data-stu-id="19ce3-118">Change line 22 to `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`</span></span>

- <span data-ttu-id="19ce3-119">Visual Basic projeleri için:</span><span class="sxs-lookup"><span data-stu-id="19ce3-119">For Visual Basic projects:</span></span>
  - <span data-ttu-id="19ce3-120">14 satırı olarak değiştir`<service name="GettingStartedLib.GettingStartedLib.CalculatorService">`</span><span class="sxs-lookup"><span data-stu-id="19ce3-120">Change line 14 to `<service name="GettingStartedLib.GettingStartedLib.CalculatorService">`</span></span>
  - <span data-ttu-id="19ce3-121">17. satırı olarak değiştir`<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span><span class="sxs-lookup"><span data-stu-id="19ce3-121">Change line 17 to `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span></span>
  - <span data-ttu-id="19ce3-122">Satır 22 ' i Değiştir`<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.GettingStartedLib.ICalculator">`</span><span class="sxs-lookup"><span data-stu-id="19ce3-122">Change line 22 to `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.GettingStartedLib.ICalculator">`</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="19ce3-123">Kod derleme</span><span class="sxs-lookup"><span data-stu-id="19ce3-123">Compile the code</span></span>

<span data-ttu-id="19ce3-124">Herhangi bir derleme hatası olmadığını doğrulamak için çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="19ce3-124">Build the solution to verify there aren't any compilation errors.</span></span> <span data-ttu-id="19ce3-125">Visual Studio kullanıyorsanız, **Yapı** menüsünde **Build Solution** (veya **CTRL**+**SHIFT**+**B**tuşlarına basın) öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="19ce3-125">If you're using Visual Studio, on the **Build** menu select **Build Solution** (or press **Ctrl**+**Shift**+**B**).</span></span>

## <a name="next-steps"></a><span data-ttu-id="19ce3-126">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="19ce3-126">Next steps</span></span>

<span data-ttu-id="19ce3-127">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="19ce3-127">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="19ce3-128">WCF hizmet sözleşmesini uygulamak için kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="19ce3-128">Add code to implement the WCF service contract.</span></span>
> - <span data-ttu-id="19ce3-129">Çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="19ce3-129">Build the solution.</span></span>

<span data-ttu-id="19ce3-130">WCF hizmetini çalıştırmayı öğrenmek için bir sonraki öğreticiye ilerleyin.</span><span class="sxs-lookup"><span data-stu-id="19ce3-130">Advance to the next tutorial to learn how to run the WCF service.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="19ce3-131">Öğretici: Temel bir WCF hizmetini barındırma ve çalıştırma</span><span class="sxs-lookup"><span data-stu-id="19ce3-131">Tutorial: Host and run a basic WCF service</span></span>](how-to-host-and-run-a-basic-wcf-service.md)
