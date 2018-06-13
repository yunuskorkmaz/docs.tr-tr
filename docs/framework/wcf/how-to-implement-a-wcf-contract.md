---
title: 'Nasıl yapılır: Windows Communication Foundation Hizmet Sözleşmesini Uygulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], implementing
ms.assetid: d5ab51ba-61ae-403e-b3c8-e2669e326806
ms.openlocfilehash: d8d1712e6fcc844a3606403efc3c2648ddcc9c65
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33499317"
---
# <a name="how-to-implement-a-windows-communication-foundation-service-contract"></a><span data-ttu-id="34d90-102">Nasıl yapılır: Windows Communication Foundation Hizmet Sözleşmesini Uygulama</span><span class="sxs-lookup"><span data-stu-id="34d90-102">How to: Implement a Windows Communication Foundation Service Contract</span></span>
<span data-ttu-id="34d90-103">Temel bir Windows Communication Foundation (WCF) hizmet ve hizmet çağırabilirsiniz bir istemci oluşturmak için gereken altı görevlerin saniyedir.</span><span class="sxs-lookup"><span data-stu-id="34d90-103">This is the second of six tasks required to create a basic Windows Communication Foundation (WCF) service and a client that can call the service.</span></span> <span data-ttu-id="34d90-104">Tüm altı görevler genel bakış için bkz: [başlangıç Öğreticisi](../../../docs/framework/wcf/getting-started-tutorial.md) konu.</span><span class="sxs-lookup"><span data-stu-id="34d90-104">For an overview of all six tasks, see the [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md) topic.</span></span>  
  
 <span data-ttu-id="34d90-105">WCF uygulaması oluşturma sonraki adım, hizmet arabirimi uygulamaktır.</span><span class="sxs-lookup"><span data-stu-id="34d90-105">The next step in creating a WCF application is to implement the service interface.</span></span> <span data-ttu-id="34d90-106">Bu adlı bir sınıf oluşturursunuz `CalculatorService` kullanıcı tanımlı uygulayan `ICalculator` arabirimi...</span><span class="sxs-lookup"><span data-stu-id="34d90-106">This involves creating a class called `CalculatorService` that implements the user-defined `ICalculator` interface..</span></span>  
  
### <a name="to-implement-a-wcf-service-contract"></a><span data-ttu-id="34d90-107">WCF hizmet sözleşmesini uygulama</span><span class="sxs-lookup"><span data-stu-id="34d90-107">To implement a WCF service contract</span></span>  
  
1.  <span data-ttu-id="34d90-108">Service1.cs dosyasını veya Service1.vb dosyasını açın ve aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="34d90-108">Open the Service1.cs or Service1.vb file and add the following code:</span></span>  
  
    ```csharp  
    //Service1.cs  
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
  
    ```vb
    ‘Service1.vb  
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
  
     <span data-ttu-id="34d90-109">Her yöntem hesaplayıcı işlemi uygular ve bazı metin sınamayı daha kolay hale getirmek için konsola yazar.</span><span class="sxs-lookup"><span data-stu-id="34d90-109">Each method implements the calculator operation and writes some text to the console to make testing easier.</span></span>  
  
## <a name="example"></a><span data-ttu-id="34d90-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="34d90-110">Example</span></span>  
 <span data-ttu-id="34d90-111">Aşağıdaki kod sözleşme ve arabiriminin uygulamasını tanımlayan iki arabirim gösterir.</span><span class="sxs-lookup"><span data-stu-id="34d90-111">The following code shows both the interface that defines the contract and the implementation of the interface.</span></span>  
  
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
  
```vb
‘IService.vb  
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
  
 <span data-ttu-id="34d90-112">Şimdi hizmet sözleşmesi oluşturulan uygulanan ve.</span><span class="sxs-lookup"><span data-stu-id="34d90-112">Now the service contract is created and implemented.</span></span> <span data-ttu-id="34d90-113">Derleme hata olmadığından emin olmak için çözümü oluşturun ve sonra devam [nasıl yapılır: temel bir hizmet barındırma ve çalıştırma](../../../docs/framework/wcf/how-to-host-and-run-a-basic-wcf-service.md) hizmetini çalıştırmak için.</span><span class="sxs-lookup"><span data-stu-id="34d90-113">Build the solution to ensure there are no compilation errors and then proceed to [How to: Host and Run a Basic Service](../../../docs/framework/wcf/how-to-host-and-run-a-basic-wcf-service.md) to run the service.</span></span> <span data-ttu-id="34d90-114">Sorun giderme bilgileri için bkz: [Başlarken Öğreticisi sorun giderme](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="34d90-114">For troubleshooting information, see [Troubleshooting the Getting Started Tutorial](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="34d90-115">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="34d90-115">Compiling the Code</span></span>  
 <span data-ttu-id="34d90-116">Visual Studio kullanıyorsanız, menüsünde Yapı Çözümü Derle tıklayın (veya CTRL + SHIFT + B tuşuna basın).</span><span class="sxs-lookup"><span data-stu-id="34d90-116">If you are using Visual Studio, on the Build menu click Build Solution (or press CTRL+SHIFT+B).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34d90-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="34d90-117">See Also</span></span>  
 [<span data-ttu-id="34d90-118">Başlarken</span><span class="sxs-lookup"><span data-stu-id="34d90-118">Getting Started</span></span>](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [<span data-ttu-id="34d90-119">Kendini Barındırma</span><span class="sxs-lookup"><span data-stu-id="34d90-119">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)
