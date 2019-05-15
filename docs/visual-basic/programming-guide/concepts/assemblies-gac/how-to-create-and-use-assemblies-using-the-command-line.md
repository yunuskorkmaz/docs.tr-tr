---
title: 'Nasıl yapılır: (Visual Basic) komut satırını kullanarak derlemeler oluşturma ve kullanma'
ms.date: 03/14/2018
ms.assetid: 229ff9fb-1bd1-403b-946b-526104864c60
ms.openlocfilehash: a30d4b3ea203a8b4d3ba621fc7b0310477ddf10d
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592690"
---
# <a name="how-to-create-and-use-assemblies-using-the-command-line-visual-basic"></a><span data-ttu-id="2fc73-102">Nasıl yapılır: (Visual Basic) komut satırını kullanarak derlemeler oluşturma ve kullanma</span><span class="sxs-lookup"><span data-stu-id="2fc73-102">How to: Create and Use Assemblies Using the Command Line (Visual Basic)</span></span>
<span data-ttu-id="2fc73-103">Bir derleme veya dinamik bağlantı kitaplığı (DLL), programınız için çalışma zamanında bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="2fc73-103">An assembly, or a dynamic linking library (DLL), is linked to your program at run time.</span></span> <span data-ttu-id="2fc73-104">Oluşturma ve bir DLL kullanarak göstermek için aşağıdaki senaryoyu göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="2fc73-104">To demonstrate building and using a DLL, consider the following scenario:</span></span>  
  
- <span data-ttu-id="2fc73-105">`MathLibrary.DLL`: Çalışma zamanında çağrılabilir yöntemleri içeren kitaplık dosyası.</span><span class="sxs-lookup"><span data-stu-id="2fc73-105">`MathLibrary.DLL`: The library file that contains the methods to be called at run time.</span></span> <span data-ttu-id="2fc73-106">Bu örnekte, iki yöntem, DLL içeren `Add` ve `Multiply`.</span><span class="sxs-lookup"><span data-stu-id="2fc73-106">In this example, the DLL contains two methods, `Add` and `Multiply`.</span></span>  
  
- <span data-ttu-id="2fc73-107">`Add`: Yöntemi içeren kaynak dosyayı `Add`.</span><span class="sxs-lookup"><span data-stu-id="2fc73-107">`Add`: The source file that contains the method `Add`.</span></span> <span data-ttu-id="2fc73-108">Parametrelerini toplamını döndürür.</span><span class="sxs-lookup"><span data-stu-id="2fc73-108">It returns the sum of its parameters.</span></span> <span data-ttu-id="2fc73-109">Sınıf `AddClass` yöntemi içeren `Add` ad alanının bir üyesidir `UtilityMethods`.</span><span class="sxs-lookup"><span data-stu-id="2fc73-109">The class `AddClass` that contains the method `Add` is a member of the namespace `UtilityMethods`.</span></span>  
  
- <span data-ttu-id="2fc73-110">`Mult`: Yöntemi içeren kaynak kodu `Multiply`.</span><span class="sxs-lookup"><span data-stu-id="2fc73-110">`Mult`: The source code that contains the method `Multiply`.</span></span> <span data-ttu-id="2fc73-111">Parametrelerini çarpımını döndürür.</span><span class="sxs-lookup"><span data-stu-id="2fc73-111">It returns the product of its parameters.</span></span> <span data-ttu-id="2fc73-112">Sınıf `MultiplyClass` yöntemi içeren `Multiply` ayrıca ad alanının bir üyesidir `UtilityMethods`.</span><span class="sxs-lookup"><span data-stu-id="2fc73-112">The class `MultiplyClass` that contains the method `Multiply` is also a member of the namespace `UtilityMethods`.</span></span>  
  
- <span data-ttu-id="2fc73-113">`TestCode`: İçeren dosyayı `Main` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2fc73-113">`TestCode`: The file that contains the `Main` method.</span></span> <span data-ttu-id="2fc73-114">Yöntemleri, toplam ve çalışma zamanı bağımsız değişken ürününü hesaplar için DLL dosyası içinde kullanır.</span><span class="sxs-lookup"><span data-stu-id="2fc73-114">It uses the methods in the DLL file to calculate the sum and the product of the run-time arguments.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2fc73-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="2fc73-115">Example</span></span>  
  
```vb  
' File: Add.vb   
Namespace UtilityMethods  
    Public Class AddClass  
        Public Shared Function Add(ByVal i As Long, ByVal j As Long) As Long  
            Return i + j  
        End Function  
    End Class  
End Namespace  
```  
  
```vb  
' File: Mult.vb  
Namespace UtilityMethods  
    Public Class MultiplyClass  
        Public Shared Function Multiply(ByVal x As Long, ByVal y As Long) As Long  
            Return x * y  
        End Function  
    End Class  
End Namespace  
```  
  
```vb  
' File: TestCode.vb  
  
Imports UtilityMethods  
  
Module Test  
  
    Sub Main(ByVal args As String())  
  
        System.Console.WriteLine("Calling methods from MathLibrary.DLL:")  
  
        If args.Length <> 2 Then  
            System.Console.WriteLine("Usage: TestCode <num1> <num2>")  
            Return  
        End If  
  
        Dim num1 As Long = Long.Parse(args(0))  
        Dim num2 As Long = Long.Parse(args(1))  
  
        Dim sum As Long = AddClass.Add(num1, num2)  
        Dim product As Long = MultiplyClass.Multiply(num1, num2)  
  
        System.Console.WriteLine("{0} + {1} = {2}", num1, num2, sum)  
        System.Console.WriteLine("{0} * {1} = {2}", num1, num2, product)  
  
    End Sub  
  
End Module  
  
' Output (assuming 1234 and 5678 are entered as command-line arguments):  
' Calling methods from MathLibrary.DLL:  
' 1234 + 5678 = 6912  
' 1234 * 5678 = 7006652  
```  
  
 <span data-ttu-id="2fc73-116">Bu dosyayı içeren DLL yöntemleri kullanan algoritma `Add` ve `Multiply`.</span><span class="sxs-lookup"><span data-stu-id="2fc73-116">This file contains the algorithm that uses the DLL methods, `Add` and `Multiply`.</span></span> <span data-ttu-id="2fc73-117">Girilen komut satırından bağımsız değişkenlerini ayrıştırma ile başlayan `num1` ve `num2`.</span><span class="sxs-lookup"><span data-stu-id="2fc73-117">It starts with parsing the arguments entered from the command line, `num1` and `num2`.</span></span> <span data-ttu-id="2fc73-118">Kullanarak toplamı hesaplar `Add` metodunda `AddClass` sınıfını ve ürünü kullanarak `Multiply` metodunda `MultiplyClass` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="2fc73-118">Then it calculates the sum by using the `Add` method on the `AddClass` class, and the product by using the `Multiply` method on the `MultiplyClass` class.</span></span>  
  
 <span data-ttu-id="2fc73-119">Dikkat `Imports` dosyasının başında deyimi DLL yöntemleri gibi derleme zamanında başvurmak için nitelenmemiş sınıf adları kullanmanıza olanak sağlar:</span><span class="sxs-lookup"><span data-stu-id="2fc73-119">Notice that the  `Imports` statement at the beginning of the file enables you to use the unqualified class names to reference the DLL methods at compile time, as follows:</span></span>  
  
```vb  
MultiplyClass.Multiply(num1, num2)  
```  
  
 <span data-ttu-id="2fc73-120">Aksi takdirde, tam olarak nitelenmiş adlar kullanacak şekilde gerekir:</span><span class="sxs-lookup"><span data-stu-id="2fc73-120">Otherwise, you have to use the fully qualified names, as follows:</span></span>  
  
```vb  
UtilityMethods.MultiplyClass.Multiply(num1, num2)  
```  
  
## <a name="execution"></a><span data-ttu-id="2fc73-121">Yürütme</span><span class="sxs-lookup"><span data-stu-id="2fc73-121">Execution</span></span>  
 <span data-ttu-id="2fc73-122">Programı çalıştırmak için iki sayı, aşağıdaki gibi yazın, bir EXE dosyasının adını girin:</span><span class="sxs-lookup"><span data-stu-id="2fc73-122">To run the program, enter the name of the EXE file, followed by two numbers, as follows:</span></span>  
  
 `TestCode 1234 5678`  
  
## <a name="see-also"></a><span data-ttu-id="2fc73-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2fc73-123">See also</span></span>

- [<span data-ttu-id="2fc73-124">Programlama Kavramları</span><span class="sxs-lookup"><span data-stu-id="2fc73-124">Programming Concepts</span></span>](../../../../visual-basic/programming-guide/concepts/index.md)
- [<span data-ttu-id="2fc73-125">.NET’te bütünleştirilmiş kodlar</span><span class="sxs-lookup"><span data-stu-id="2fc73-125">Assemblies in .NET</span></span>](../../../../standard/assembly/index.md)
- [<span data-ttu-id="2fc73-126">DLL İşlevleri için bir Sınıf Oluşturma</span><span class="sxs-lookup"><span data-stu-id="2fc73-126">Creating a Class to Hold DLL Functions</span></span>](../../../../framework/interop/creating-a-class-to-hold-dll-functions.md)
