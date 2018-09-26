---
title: 'Nasıl yapılır: Windows Communication Foundation Hizmet Sözleşmesini Uygulama'
ms.date: 09/14/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], implementing
ms.assetid: d5ab51ba-61ae-403e-b3c8-e2669e326806
ms.openlocfilehash: 569de6f49b56b46ccfeb22e9f0bd25bcf339b7e0
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47202992"
---
# <a name="how-to-implement-a-windows-communication-foundation-service-contract"></a><span data-ttu-id="3c0bf-102">Nasıl yapılır: Windows Communication Foundation Hizmet Sözleşmesini Uygulama</span><span class="sxs-lookup"><span data-stu-id="3c0bf-102">How to: Implement a Windows Communication Foundation Service Contract</span></span>

<span data-ttu-id="3c0bf-103">Altı görevden temel bir Windows Communication Foundation (WCF) hizmeti oluşturup hizmeti çağırmak bir istemci için gerekli ikincisi budur.</span><span class="sxs-lookup"><span data-stu-id="3c0bf-103">This is the second of six tasks required to create a basic Windows Communication Foundation (WCF) service and a client that can call the service.</span></span> <span data-ttu-id="3c0bf-104">Altı tüm görevler genel bakış için bkz. [başlangıç Öğreticisi](../../../docs/framework/wcf/getting-started-tutorial.md) konu.</span><span class="sxs-lookup"><span data-stu-id="3c0bf-104">For an overview of all six tasks, see the [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md) topic.</span></span>

<span data-ttu-id="3c0bf-105">WCF uygulaması oluşturma bir sonraki adımınız hizmet arabirimi uygulamaktır.</span><span class="sxs-lookup"><span data-stu-id="3c0bf-105">The next step in creating a WCF application is to implement the service interface.</span></span> <span data-ttu-id="3c0bf-106">Bu adında bir sınıf oluşturulmasını ilgilendirir `CalculatorService` uygulayan kullanıcı tanımlı `ICalculator` arabirimi...</span><span class="sxs-lookup"><span data-stu-id="3c0bf-106">This involves creating a class called `CalculatorService` that implements the user-defined `ICalculator` interface..</span></span>

## <a name="to-implement-a-wcf-service-contract"></a><span data-ttu-id="3c0bf-107">Bir WCF hizmet sözleşmesini uygulama</span><span class="sxs-lookup"><span data-stu-id="3c0bf-107">To implement a WCF service contract</span></span>

<span data-ttu-id="3c0bf-108">Service1.cs veya gt;service1.vb dosyasını açın ve aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="3c0bf-108">Open the Service1.cs or Service1.vb file and add the following code:</span></span>

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

<span data-ttu-id="3c0bf-109">Her yöntem hesaplayıcı işlemi uygular ve bazı metin test işlemini kolaylaştıran için konsola yazar.</span><span class="sxs-lookup"><span data-stu-id="3c0bf-109">Each method implements the calculator operation and writes some text to the console to make testing easier.</span></span>

## <a name="example"></a><span data-ttu-id="3c0bf-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="3c0bf-110">Example</span></span>

<span data-ttu-id="3c0bf-111">Aşağıdaki kod, sözleşme ve uygulama arabiriminin tanımlayan iki arabirim gösterir.</span><span class="sxs-lookup"><span data-stu-id="3c0bf-111">The following code shows both the interface that defines the contract and the implementation of the interface.</span></span>

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

## <a name="compile-the-code"></a><span data-ttu-id="3c0bf-112">Kod derleme</span><span class="sxs-lookup"><span data-stu-id="3c0bf-112">Compile the code</span></span>

<span data-ttu-id="3c0bf-113">Hiç derleme hatası olmadığından emin olmak için çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3c0bf-113">Build the solution to ensure there are no compilation errors.</span></span> <span data-ttu-id="3c0bf-114">Visual Studio kullanıyorsanız **derleme** menüsünü seçin **Çözümü Derle** (veya basın **Ctrl**+**Shift** + **B**).</span><span class="sxs-lookup"><span data-stu-id="3c0bf-114">If you're using Visual Studio, on the **Build** menu select **Build Solution** (or press **Ctrl**+**Shift**+**B**).</span></span>

## <a name="next-steps"></a><span data-ttu-id="3c0bf-115">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="3c0bf-115">Next steps</span></span>

<span data-ttu-id="3c0bf-116">Artık hizmet sözleşmesi uygulanan ve oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3c0bf-116">Now the service contract is created and implemented.</span></span> <span data-ttu-id="3c0bf-117">Sonraki adımda, hizmet çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="3c0bf-117">In the next step, you run the service.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3c0bf-118">Nasıl yapılır: Temel Bir Hizmet Barındırma ve Çalıştırma</span><span class="sxs-lookup"><span data-stu-id="3c0bf-118">How to: Host and Run a Basic Service</span></span>](../../../docs/framework/wcf/how-to-host-and-run-a-basic-wcf-service.md)

<span data-ttu-id="3c0bf-119">Sorun giderme bilgileri için bkz: [Başlarken Öğreticisi sorun giderme](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="3c0bf-119">For troubleshooting information, see [Troubleshooting the Getting Started Tutorial](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3c0bf-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3c0bf-120">See also</span></span>

- [<span data-ttu-id="3c0bf-121">Başlarken</span><span class="sxs-lookup"><span data-stu-id="3c0bf-121">Getting Started</span></span>](../../../docs/framework/wcf/samples/getting-started-sample.md)
- [<span data-ttu-id="3c0bf-122">Kendini Barındırma</span><span class="sxs-lookup"><span data-stu-id="3c0bf-122">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)