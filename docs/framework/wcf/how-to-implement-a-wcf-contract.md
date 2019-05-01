---
title: 'Öğretici: Bir Windows Communication Foundation Hizmet sözleşmesini uygulama'
ms.date: 03/19/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], implementing
ms.assetid: d5ab51ba-61ae-403e-b3c8-e2669e326806
ms.openlocfilehash: fa8c5457c636d7f37215f0d4b4fdbb1c96c9481e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61929059"
---
# <a name="tutorial-implement-a-windows-communication-foundation-service-contract"></a><span data-ttu-id="1ee7c-102">Öğretici: Bir Windows Communication Foundation Hizmet sözleşmesini uygulama</span><span class="sxs-lookup"><span data-stu-id="1ee7c-102">Tutorial: Implement a Windows Communication Foundation service contract</span></span>

<span data-ttu-id="1ee7c-103">Bu öğreticide, temel Windows Communication Foundation (WCF) uygulaması oluşturmak için gereken beş görev ikinci açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1ee7c-103">This tutorial describes the second of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="1ee7c-104">Öğreticiler genel bakış için bkz. [Öğreticisi: Windows Communication Foundation uygulamalarla çalışmaya başlama](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="1ee7c-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="1ee7c-105">WCF uygulaması oluşturmak için sonraki adım, önceki adımda oluşturduğunuz WCF Hizmeti arabirim uygulamak için kod eklemektir.</span><span class="sxs-lookup"><span data-stu-id="1ee7c-105">The next step for creating a WCF application is to add code to implement the WCF service interface that you created in the previous step.</span></span> <span data-ttu-id="1ee7c-106">Bu adımda, adlı bir sınıf oluşturun `CalculatorService` uygulayan kullanıcı tanımlı `ICalculator` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="1ee7c-106">In this step, you create a class named `CalculatorService` that implements the user-defined `ICalculator` interface.</span></span> <span data-ttu-id="1ee7c-107">Aşağıdaki kod her bir yöntemin hesaplayıcı işlemi çağırır ve metin test etmek için konsola yazar.</span><span class="sxs-lookup"><span data-stu-id="1ee7c-107">Each method in the following code calls a calculator operation and writes text to the console to test it.</span></span> 

<span data-ttu-id="1ee7c-108">Bu öğreticide şunların nasıl yapıladığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="1ee7c-108">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="1ee7c-109">WCF hizmet sözleşmesini uygulama için kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1ee7c-109">Add code to implement the WCF service contract.</span></span>
> - <span data-ttu-id="1ee7c-110">Çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1ee7c-110">Build the solution.</span></span>

## <a name="add-code-to-implement-the-wcf-service-contract"></a><span data-ttu-id="1ee7c-111">WCF hizmet sözleşmesini uygulama için kod ekleyin</span><span class="sxs-lookup"><span data-stu-id="1ee7c-111">Add code to implement the WCF service contract</span></span>

<span data-ttu-id="1ee7c-112">İçinde **GettingStartedLib**açın **Service1.cs** veya **Service1.vb** dosya ve kendi kodu aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="1ee7c-112">In **GettingStartedLib**, open the **Service1.cs** or **Service1.vb** file and replace its code with the following code:</span></span>

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

## <a name="edit-appconfig"></a><span data-ttu-id="1ee7c-113">App.config Düzenle</span><span class="sxs-lookup"><span data-stu-id="1ee7c-113">Edit App.config</span></span>

<span data-ttu-id="1ee7c-114">Düzen **App.config** içinde **GettingStartedLib** koda yapılan değişiklikleri yansıtacak şekilde.</span><span class="sxs-lookup"><span data-stu-id="1ee7c-114">Edit **App.config** in **GettingStartedLib** to reflect the changes you made to the code.</span></span>
- <span data-ttu-id="1ee7c-115">Görsel için C# projeleri:</span><span class="sxs-lookup"><span data-stu-id="1ee7c-115">For Visual C# projects:</span></span>
  - <span data-ttu-id="1ee7c-116">14. satır için değiştirin `<service name="GettingStartedLib.CalculatorService">`</span><span class="sxs-lookup"><span data-stu-id="1ee7c-116">Change line 14 to `<service name="GettingStartedLib.CalculatorService">`</span></span>
  - <span data-ttu-id="1ee7c-117">17 satırına değiştirme `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span><span class="sxs-lookup"><span data-stu-id="1ee7c-117">Change line 17 to `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span></span>
  - <span data-ttu-id="1ee7c-118">Satır 22 için değiştirin `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`</span><span class="sxs-lookup"><span data-stu-id="1ee7c-118">Change line 22 to `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`</span></span>

- <span data-ttu-id="1ee7c-119">Visual Basic projeleri için:</span><span class="sxs-lookup"><span data-stu-id="1ee7c-119">For Visual Basic projects:</span></span>
  - <span data-ttu-id="1ee7c-120">14. satır için değiştirin `<service name="GettingStartedLib.GettingStartedLib.CalculatorService">`</span><span class="sxs-lookup"><span data-stu-id="1ee7c-120">Change line 14 to `<service name="GettingStartedLib.GettingStartedLib.CalculatorService">`</span></span>
  - <span data-ttu-id="1ee7c-121">17 satırına değiştirme `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span><span class="sxs-lookup"><span data-stu-id="1ee7c-121">Change line 17 to `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span></span>
  - <span data-ttu-id="1ee7c-122">Satır 22 için değiştirin `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.GettingStartedLib.ICalculator">`</span><span class="sxs-lookup"><span data-stu-id="1ee7c-122">Change line 22 to `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.GettingStartedLib.ICalculator">`</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="1ee7c-123">Kod derleme</span><span class="sxs-lookup"><span data-stu-id="1ee7c-123">Compile the code</span></span>

<span data-ttu-id="1ee7c-124">Derleme hataları doğrulamak için çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1ee7c-124">Build the solution to verify there aren't any compilation errors.</span></span> <span data-ttu-id="1ee7c-125">Visual Studio kullanıyorsanız **derleme** menüsünü seçin **Çözümü Derle** (veya basın **Ctrl**+**Shift** + **B**).</span><span class="sxs-lookup"><span data-stu-id="1ee7c-125">If you're using Visual Studio, on the **Build** menu select **Build Solution** (or press **Ctrl**+**Shift**+**B**).</span></span>

## <a name="next-steps"></a><span data-ttu-id="1ee7c-126">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="1ee7c-126">Next steps</span></span>

<span data-ttu-id="1ee7c-127">Bu öğreticide, şunların nasıl yapıldığını öğrendiniz:</span><span class="sxs-lookup"><span data-stu-id="1ee7c-127">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="1ee7c-128">WCF hizmet sözleşmesini uygulama için kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1ee7c-128">Add code to implement the WCF service contract.</span></span>
> - <span data-ttu-id="1ee7c-129">Çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1ee7c-129">Build the solution.</span></span>

<span data-ttu-id="1ee7c-130">WCF hizmeti çalıştırmaya hakkında bilgi edinmek için sonraki öğreticiye ilerleyin.</span><span class="sxs-lookup"><span data-stu-id="1ee7c-130">Advance to the next tutorial to learn how to run the WCF service.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1ee7c-131">Öğretici: Temel bir WCF Hizmeti barındırma ve çalıştırma</span><span class="sxs-lookup"><span data-stu-id="1ee7c-131">Tutorial: Host and run a basic WCF service</span></span>](how-to-host-and-run-a-basic-wcf-service.md)
