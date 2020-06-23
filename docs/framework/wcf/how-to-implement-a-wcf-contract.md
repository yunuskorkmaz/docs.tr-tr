---
title: 'Öğretici: Windows Communication Foundation hizmet sözleşmesi uygulama'
description: WCF uygulaması oluşturmaya başlamanıza yardımcı olan bir makale serisinin parçası olarak bir WCF hizmeti arabirimini uygulamak için kod ekleme hakkında bilgi edinin.
ms.date: 03/19/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], implementing
ms.assetid: d5ab51ba-61ae-403e-b3c8-e2669e326806
ms.openlocfilehash: 89f97610cccd42c2a5d298baa667327d077fd472
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244653"
---
# <a name="tutorial-implement-a-windows-communication-foundation-service-contract"></a><span data-ttu-id="9e758-103">Öğretici: Windows Communication Foundation hizmet sözleşmesi uygulama</span><span class="sxs-lookup"><span data-stu-id="9e758-103">Tutorial: Implement a Windows Communication Foundation service contract</span></span>

<span data-ttu-id="9e758-104">Bu öğreticide, temel bir Windows Communication Foundation (WCF) uygulaması oluşturmak için gereken beş görevin ikinci açıklaması açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9e758-104">This tutorial describes the second of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="9e758-105">Öğreticilere genel bakış için bkz. [öğretici: Windows Communication Foundation uygulamalarla çalışmaya başlama](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="9e758-105">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="9e758-106">Bir WCF uygulaması oluşturmaya yönelik sonraki adım, önceki adımda oluşturduğunuz WCF hizmeti arabirimini uygulamak için kod eklemektir.</span><span class="sxs-lookup"><span data-stu-id="9e758-106">The next step for creating a WCF application is to add code to implement the WCF service interface that you created in the previous step.</span></span> <span data-ttu-id="9e758-107">Bu adımda, `CalculatorService` Kullanıcı tanımlı arabirimi uygulayan adlı bir sınıf oluşturursunuz `ICalculator` .</span><span class="sxs-lookup"><span data-stu-id="9e758-107">In this step, you create a class named `CalculatorService` that implements the user-defined `ICalculator` interface.</span></span> <span data-ttu-id="9e758-108">Aşağıdaki koddaki her bir yöntem bir Hesaplayıcı işlemini çağırır ve test etmek üzere konsola metin yazar.</span><span class="sxs-lookup"><span data-stu-id="9e758-108">Each method in the following code calls a calculator operation and writes text to the console to test it.</span></span>

<span data-ttu-id="9e758-109">Bu öğreticide aşağıdakilerin nasıl yapılacağını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="9e758-109">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="9e758-110">WCF hizmet sözleşmesini uygulamak için kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9e758-110">Add code to implement the WCF service contract.</span></span>
> - <span data-ttu-id="9e758-111">Çözümü derleyin.</span><span class="sxs-lookup"><span data-stu-id="9e758-111">Build the solution.</span></span>

## <a name="add-code-to-implement-the-wcf-service-contract"></a><span data-ttu-id="9e758-112">WCF hizmet sözleşmesini uygulamak için kod ekleme</span><span class="sxs-lookup"><span data-stu-id="9e758-112">Add code to implement the WCF service contract</span></span>

<span data-ttu-id="9e758-113">**GettingStartedLib**içinde **Service1.cs** veya **Service1. vb** dosyasını açın ve kodunu aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="9e758-113">In **GettingStartedLib**, open the **Service1.cs** or **Service1.vb** file and replace its code with the following code:</span></span>

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

## <a name="edit-appconfig"></a><span data-ttu-id="9e758-114">App.config Düzenle</span><span class="sxs-lookup"><span data-stu-id="9e758-114">Edit App.config</span></span>

<span data-ttu-id="9e758-115">Kodda yaptığınız değişiklikleri yansıtmak için **GettingStartedLib** içindeki **App.config** düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="9e758-115">Edit **App.config** in **GettingStartedLib** to reflect the changes you made to the code.</span></span>

- <span data-ttu-id="9e758-116">Visual C# projeleri için:</span><span class="sxs-lookup"><span data-stu-id="9e758-116">For Visual C# projects:</span></span>
  - <span data-ttu-id="9e758-117">14 satırı olarak değiştir`<service name="GettingStartedLib.CalculatorService">`</span><span class="sxs-lookup"><span data-stu-id="9e758-117">Change line 14 to `<service name="GettingStartedLib.CalculatorService">`</span></span>
  - <span data-ttu-id="9e758-118">17. satırı olarak değiştir`<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span><span class="sxs-lookup"><span data-stu-id="9e758-118">Change line 17 to `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span></span>
  - <span data-ttu-id="9e758-119">Satır 22 ' i Değiştir`<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`</span><span class="sxs-lookup"><span data-stu-id="9e758-119">Change line 22 to `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`</span></span>

- <span data-ttu-id="9e758-120">Visual Basic projeleri için:</span><span class="sxs-lookup"><span data-stu-id="9e758-120">For Visual Basic projects:</span></span>
  - <span data-ttu-id="9e758-121">14 satırı olarak değiştir`<service name="GettingStartedLib.GettingStartedLib.CalculatorService">`</span><span class="sxs-lookup"><span data-stu-id="9e758-121">Change line 14 to `<service name="GettingStartedLib.GettingStartedLib.CalculatorService">`</span></span>
  - <span data-ttu-id="9e758-122">17. satırı olarak değiştir`<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span><span class="sxs-lookup"><span data-stu-id="9e758-122">Change line 17 to `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span></span>
  - <span data-ttu-id="9e758-123">Satır 22 ' i Değiştir`<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.GettingStartedLib.ICalculator">`</span><span class="sxs-lookup"><span data-stu-id="9e758-123">Change line 22 to `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.GettingStartedLib.ICalculator">`</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="9e758-124">Kodu derle</span><span class="sxs-lookup"><span data-stu-id="9e758-124">Compile the code</span></span>

<span data-ttu-id="9e758-125">Herhangi bir derleme hatası olmadığını doğrulamak için çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9e758-125">Build the solution to verify there aren't any compilation errors.</span></span> <span data-ttu-id="9e758-126">Visual Studio kullanıyorsanız, **Yapı** menüsünde **Build Solution** (veya **CTRL** + **SHIFT** + **B**tuşlarına basın) öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="9e758-126">If you're using Visual Studio, on the **Build** menu select **Build Solution** (or press **Ctrl**+**Shift**+**B**).</span></span>

## <a name="next-steps"></a><span data-ttu-id="9e758-127">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="9e758-127">Next steps</span></span>

<span data-ttu-id="9e758-128">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="9e758-128">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="9e758-129">WCF hizmet sözleşmesini uygulamak için kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9e758-129">Add code to implement the WCF service contract.</span></span>
> - <span data-ttu-id="9e758-130">Çözümü derleyin.</span><span class="sxs-lookup"><span data-stu-id="9e758-130">Build the solution.</span></span>

<span data-ttu-id="9e758-131">WCF hizmetini çalıştırmayı öğrenmek için bir sonraki öğreticiye ilerleyin.</span><span class="sxs-lookup"><span data-stu-id="9e758-131">Advance to the next tutorial to learn how to run the WCF service.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9e758-132">Öğretici: temel bir WCF hizmetini barındırma ve çalıştırma</span><span class="sxs-lookup"><span data-stu-id="9e758-132">Tutorial: Host and run a basic WCF service</span></span>](how-to-host-and-run-a-basic-wcf-service.md)
