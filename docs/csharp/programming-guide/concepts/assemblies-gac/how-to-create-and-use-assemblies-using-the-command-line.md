---
title: 'Nasıl yapılır: Komut satırını kullanarak derlemeler oluşturma ve kullanma (C#)'
ms.date: 07/20/2015
ms.assetid: 408ddce3-89e3-4e12-8353-34a49beeb72b
ms.openlocfilehash: 0a8db22a05d834d15f6e6b7f049f59f86bc1fe1d
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595972"
---
# <a name="how-to-create-and-use-assemblies-using-the-command-line-c"></a><span data-ttu-id="f4bba-102">Nasıl yapılır: Komut satırını kullanarak derlemeler oluşturma ve kullanma (C#)</span><span class="sxs-lookup"><span data-stu-id="f4bba-102">How to: Create and Use Assemblies Using the Command Line (C#)</span></span>
<span data-ttu-id="f4bba-103">Bir derleme veya dinamik bağlantı kitaplığı (DLL), çalışma zamanında programınıza bağlanır.</span><span class="sxs-lookup"><span data-stu-id="f4bba-103">An assembly, or a dynamic linking library (DLL), is linked to your program at run time.</span></span> <span data-ttu-id="f4bba-104">Bir DLL oluşturmayı ve kullanmayı göstermek için aşağıdaki senaryoyu göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="f4bba-104">To demonstrate building and using a DLL, consider the following scenario:</span></span>  
  
- <span data-ttu-id="f4bba-105">`MathLibrary.DLL`: Çalışma zamanında çağrılacak yöntemleri içeren kitaplık dosyası.</span><span class="sxs-lookup"><span data-stu-id="f4bba-105">`MathLibrary.DLL`: The library file that contains the methods to be called at run time.</span></span> <span data-ttu-id="f4bba-106">Bu örnekte, DLL iki yöntem `Add` içerir ve. `Multiply`</span><span class="sxs-lookup"><span data-stu-id="f4bba-106">In this example, the DLL contains two methods, `Add` and `Multiply`.</span></span>  
  
- <span data-ttu-id="f4bba-107">`Add`: Yöntemini `Add`içeren kaynak dosya.</span><span class="sxs-lookup"><span data-stu-id="f4bba-107">`Add`: The source file that contains the method `Add`.</span></span> <span data-ttu-id="f4bba-108">Parametrelerinin toplamını döndürür.</span><span class="sxs-lookup"><span data-stu-id="f4bba-108">It returns the sum of its parameters.</span></span> <span data-ttu-id="f4bba-109">`UtilityMethods`Yöntemi `AddClass` içeren`Add` sınıf, ad alanının bir üyesidir.</span><span class="sxs-lookup"><span data-stu-id="f4bba-109">The class `AddClass` that contains the method `Add` is a member of the namespace `UtilityMethods`.</span></span>  
  
- <span data-ttu-id="f4bba-110">`Mult`: Yöntemini `Multiply`içeren kaynak kodu.</span><span class="sxs-lookup"><span data-stu-id="f4bba-110">`Mult`: The source code that contains the method `Multiply`.</span></span> <span data-ttu-id="f4bba-111">Kendi parametrelerinin çarpımını döndürür.</span><span class="sxs-lookup"><span data-stu-id="f4bba-111">It returns the product of its parameters.</span></span> <span data-ttu-id="f4bba-112">`UtilityMethods`Yöntemi `MultiplyClass` içeren`Multiply` sınıf ayrıca ad alanının bir üyesidir.</span><span class="sxs-lookup"><span data-stu-id="f4bba-112">The class `MultiplyClass` that contains the method `Multiply` is also a member of the namespace `UtilityMethods`.</span></span>  
  
- <span data-ttu-id="f4bba-113">`TestCode`: `Main` Yöntemini içeren dosya.</span><span class="sxs-lookup"><span data-stu-id="f4bba-113">`TestCode`: The file that contains the `Main` method.</span></span> <span data-ttu-id="f4bba-114">Çalışma zamanı bağımsız değişkenlerinin toplamını ve çarpımını hesaplamak için DLL dosyasındaki yöntemleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="f4bba-114">It uses the methods in the DLL file to calculate the sum and the product of the run-time arguments.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f4bba-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="f4bba-115">Example</span></span>  
  
```csharp  
// File: Add.cs   
namespace UtilityMethods  
{  
    public class AddClass   
    {  
        public static long Add(long i, long j)   
        {   
            return (i + j);  
        }  
    }  
}  
```  
  
```csharp  
// File: Mult.cs  
namespace UtilityMethods   
{  
    public class MultiplyClass  
    {  
        public static long Multiply(long x, long y)   
        {  
            return (x * y);   
        }  
    }  
}  
```  
  
```csharp  
// File: TestCode.cs  
  
using UtilityMethods;  
  
class TestCode  
{  
    static void Main(string[] args)   
    {  
        System.Console.WriteLine("Calling methods from MathLibrary.DLL:");  
  
        if (args.Length != 2)  
        {  
            System.Console.WriteLine("Usage: TestCode <num1> <num2>");  
            return;  
        }  
  
        long num1 = long.Parse(args[0]);  
        long num2 = long.Parse(args[1]);  
  
        long sum = AddClass.Add(num1, num2);  
        long product = MultiplyClass.Multiply(num1, num2);  
  
        System.Console.WriteLine("{0} + {1} = {2}", num1, num2, sum);  
        System.Console.WriteLine("{0} * {1} = {2}", num1, num2, product);  
    }  
}  
/* Output (assuming 1234 and 5678 are entered as command-line arguments):  
    Calling methods from MathLibrary.DLL:  
    1234 + 5678 = 6912  
    1234 * 5678 = 7006652          
*/  
```  
  
 <span data-ttu-id="f4bba-116">Bu dosya, dll yöntemlerini ve `Add` `Multiply`' ı kullanan algoritmayı içerir.</span><span class="sxs-lookup"><span data-stu-id="f4bba-116">This file contains the algorithm that uses the DLL methods, `Add` and `Multiply`.</span></span> <span data-ttu-id="f4bba-117">Komut satırından `num1` girilen bağımsız değişkenlerin ayrıştırılmasından başlar ve `num2`.</span><span class="sxs-lookup"><span data-stu-id="f4bba-117">It starts with parsing the arguments entered from the command line, `num1` and `num2`.</span></span> <span data-ttu-id="f4bba-118">Daha sonra, `Add` sınıfındaki yöntemini kullanarak ve `AddClass` `Multiply` `MultiplyClass` sınıfındaki yöntemi kullanarak toplamı hesaplar.</span><span class="sxs-lookup"><span data-stu-id="f4bba-118">Then it calculates the sum by using the `Add` method on the `AddClass` class, and the product by using the `Multiply` method on the `MultiplyClass` class.</span></span>  
  
 <span data-ttu-id="f4bba-119">Dosyanın başındaki yönerge, derleme zamanında DLL yöntemlerine başvurmak için, nitelenmemiş sınıf adlarını şu şekilde kullanmanıza olanak sağlar: `using`</span><span class="sxs-lookup"><span data-stu-id="f4bba-119">Notice that the `using` directive at the beginning of the file enables you to use the unqualified class names to reference the DLL methods at compile time, as follows:</span></span>  
  
```csharp  
MultiplyClass.Multiply(num1, num2);  
```  
  
 <span data-ttu-id="f4bba-120">Aksi takdirde, aşağıdaki gibi tam nitelikli adları kullanmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="f4bba-120">Otherwise, you have to use the fully qualified names, as follows:</span></span>  
  
```csharp  
UtilityMethods.MultiplyClass.Multiply(num1, num2);  
```  
  
## <a name="execution"></a><span data-ttu-id="f4bba-121">Yürütme</span><span class="sxs-lookup"><span data-stu-id="f4bba-121">Execution</span></span>  
 <span data-ttu-id="f4bba-122">Programı çalıştırmak için, EXE dosyasının adını ve ardından iki sayıyı aşağıdaki şekilde girin:</span><span class="sxs-lookup"><span data-stu-id="f4bba-122">To run the program, enter the name of the EXE file, followed by two numbers, as follows:</span></span>  
  
 `TestCode 1234 5678`  
  
## <a name="see-also"></a><span data-ttu-id="f4bba-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f4bba-123">See also</span></span>

- [<span data-ttu-id="f4bba-124">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f4bba-124">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="f4bba-125">.NET’te bütünleştirilmiş kodlar</span><span class="sxs-lookup"><span data-stu-id="f4bba-125">Assemblies in .NET</span></span>](../../../../standard/assembly/index.md)
- [<span data-ttu-id="f4bba-126">DLL İşlevleri için bir Sınıf Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f4bba-126">Creating a Class to Hold DLL Functions</span></span>](../../../../framework/interop/creating-a-class-to-hold-dll-functions.md)
