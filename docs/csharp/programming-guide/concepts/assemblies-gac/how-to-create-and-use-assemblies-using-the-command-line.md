---
title: "Nasıl yapılır: komut satırını (C#) kullanarak derlemeler oluşturma ve kullanma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 408ddce3-89e3-4e12-8353-34a49beeb72b
caps.latest.revision: "4"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d59988ec4899b4115d8d0fd7172e0c8ff8802378
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-and-use-assemblies-using-the-command-line-c"></a><span data-ttu-id="bf085-102">Nasıl yapılır: komut satırını (C#) kullanarak derlemeler oluşturma ve kullanma</span><span class="sxs-lookup"><span data-stu-id="bf085-102">How to: Create and Use Assemblies Using the Command Line (C#)</span></span>
<span data-ttu-id="bf085-103">Bir derlemeyi ya da dinamik bağlantı kitaplığı (DLL) programınıza çalışma zamanında bağlanır.</span><span class="sxs-lookup"><span data-stu-id="bf085-103">An assembly, or a dynamic linking library (DLL), is linked to your program at run time.</span></span> <span data-ttu-id="bf085-104">Derleme ve DLL kullanarak göstermek için aşağıdaki senaryoyu göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="bf085-104">To demonstrate building and using a DLL, consider the following scenario:</span></span>  
  
-   <span data-ttu-id="bf085-105">`MathLibrary.DLL`: Çalışma zamanında çağrılacak yöntem içerir kitaplık dosyası.</span><span class="sxs-lookup"><span data-stu-id="bf085-105">`MathLibrary.DLL`: The library file that contains the methods to be called at run time.</span></span> <span data-ttu-id="bf085-106">Bu örnekte, iki yöntem DLL içeren `Add` ve `Multiply`.</span><span class="sxs-lookup"><span data-stu-id="bf085-106">In this example, the DLL contains two methods, `Add` and `Multiply`.</span></span>  
  
-   <span data-ttu-id="bf085-107">`Add`: Yöntem içerir kaynak dosya `Add`.</span><span class="sxs-lookup"><span data-stu-id="bf085-107">`Add`: The source file that contains the method `Add`.</span></span> <span data-ttu-id="bf085-108">Bunu parametrelerinin toplamını döndürür.</span><span class="sxs-lookup"><span data-stu-id="bf085-108">It returns the sum of its parameters.</span></span> <span data-ttu-id="bf085-109">Sınıf `AddClass` yöntemi içeren `Add` ad üyesi `UtilityMethods`.</span><span class="sxs-lookup"><span data-stu-id="bf085-109">The class `AddClass` that contains the method `Add` is a member of the namespace `UtilityMethods`.</span></span>  
  
-   <span data-ttu-id="bf085-110">`Mult`: Yöntem içerir kaynak kodu `Multiply`.</span><span class="sxs-lookup"><span data-stu-id="bf085-110">`Mult`: The source code that contains the method `Multiply`.</span></span> <span data-ttu-id="bf085-111">Bunu parametrelerinin çarpımını döndürür.</span><span class="sxs-lookup"><span data-stu-id="bf085-111">It returns the product of its parameters.</span></span> <span data-ttu-id="bf085-112">Sınıf `MultiplyClass` yöntemi içeren `Multiply` de ad alanının bir üyesidir `UtilityMethods`.</span><span class="sxs-lookup"><span data-stu-id="bf085-112">The class `MultiplyClass` that contains the method `Multiply` is also a member of the namespace `UtilityMethods`.</span></span>  
  
-   <span data-ttu-id="bf085-113">`TestCode`: İçerir dosya `Main` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="bf085-113">`TestCode`: The file that contains the `Main` method.</span></span> <span data-ttu-id="bf085-114">Yöntemleri, toplam ve çalışma zamanı değişkenleri Ürün hesaplamak için DLL dosyasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="bf085-114">It uses the methods in the DLL file to calculate the sum and the product of the run-time arguments.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf085-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="bf085-115">Example</span></span>  
  
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
  
 <span data-ttu-id="bf085-116">Bu dosya DLL yöntemleri tarafından kullanılan algoritmasını içerir `Add` ve `Multiply`.</span><span class="sxs-lookup"><span data-stu-id="bf085-116">This file contains the algorithm that uses the DLL methods, `Add` and `Multiply`.</span></span> <span data-ttu-id="bf085-117">Komut satırından girilen bağımsız değişkenlerini ayrıştırma ile başlayan `num1` ve `num2`.</span><span class="sxs-lookup"><span data-stu-id="bf085-117">It starts with parsing the arguments entered from the command line, `num1` and `num2`.</span></span> <span data-ttu-id="bf085-118">Kullanarak toplamı hesaplar sonra `Add` yöntemi `AddClass` sınıfını ve ürünü kullanarak `Multiply` yöntemi `MultiplyClass` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="bf085-118">Then it calculates the sum by using the `Add` method on the `AddClass` class, and the product by using the `Multiply` method on the `MultiplyClass` class.</span></span>  
  
 <span data-ttu-id="bf085-119">Dikkat `using` yönergesi dosyasının başında DLL yöntemleri derleme zamanında şu şekilde başvurmak için nitelenmemiş sınıf adları kullanabilmenizi sağlar:</span><span class="sxs-lookup"><span data-stu-id="bf085-119">Notice that the `using` directive at the beginning of the file enables you to use the unqualified class names to reference the DLL methods at compile time, as follows:</span></span>  
  
```csharp  
MultiplyClass.Multiply(num1, num2);  
```  
  
 <span data-ttu-id="bf085-120">Aksi halde, tam olarak nitelenmiş adlar aşağıdaki gibi kullanmak zorunda:</span><span class="sxs-lookup"><span data-stu-id="bf085-120">Otherwise, you have to use the fully qualified names, as follows:</span></span>  
  
```csharp  
UtilityMethods.MultiplyClass.Multiply(num1, num2);  
```  
  
## <a name="execution"></a><span data-ttu-id="bf085-121">Yürütme</span><span class="sxs-lookup"><span data-stu-id="bf085-121">Execution</span></span>  
 <span data-ttu-id="bf085-122">Programı çalıştırmak için iki numaralarına göre aşağıdaki gibi ardından EXE dosyasının adını girin:</span><span class="sxs-lookup"><span data-stu-id="bf085-122">To run the program, enter the name of the EXE file, followed by two numbers, as follows:</span></span>  
  
 `TestCode 1234 5678`  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bf085-123">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="bf085-123">Compiling the Code</span></span>  
 <span data-ttu-id="bf085-124">Dosyasını oluşturmak için `MathLibrary.DLL`, iki dosyalarını derlemek `Add` ve `Mult` aşağıdaki komut satırını kullanarak.</span><span class="sxs-lookup"><span data-stu-id="bf085-124">To build the file `MathLibrary.DLL`, compile the two files `Add` and `Mult` by using the following command line.</span></span>  
  
```csharp  
csc /target:library /out:MathLibrary.DLL Add.cs Mult.cs  
```  
  
 <span data-ttu-id="bf085-125">[/Target: library](../../../../csharp/language-reference/compiler-options/target-library-compiler-option.md) derleyici seçeneği bir EXE dosyası yerine bir DLL çıktısını almak için derleyici söyler.</span><span class="sxs-lookup"><span data-stu-id="bf085-125">The [/target:library](../../../../csharp/language-reference/compiler-options/target-library-compiler-option.md) compiler option tells the compiler to output a DLL instead of an EXE file.</span></span> <span data-ttu-id="bf085-126">[/Out](../../../../csharp/language-reference/compiler-options/out-compiler-option.md) dosya adından derleyici seçeneği DLL dosya adı belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bf085-126">The [/out](../../../../csharp/language-reference/compiler-options/out-compiler-option.md) compiler option followed by a file name is used to specify the DLL file name.</span></span> <span data-ttu-id="bf085-127">Aksi durumda, ilk dosya derleyici kullanır (`Add.cs`) DLL adından farklı.</span><span class="sxs-lookup"><span data-stu-id="bf085-127">Otherwise, the compiler uses the first file (`Add.cs`) as the name of the DLL.</span></span>  
  
 <span data-ttu-id="bf085-128">Yürütülebilir dosyasını oluşturmak için `TestCode.exe`, aşağıdaki komut satırını kullanın:</span><span class="sxs-lookup"><span data-stu-id="bf085-128">To build the executable file, `TestCode.exe`, use the following command line:</span></span>  
  
```csharp  
csc /out:TestCode.exe /reference:MathLibrary.DLL TestCode.cs  
```  
  
 <span data-ttu-id="bf085-129">**/Out** derleyici seçeneği çıkış bir EXE dosyası bildirir ve çıktı dosyası adını belirtir (`TestCode.exe`).</span><span class="sxs-lookup"><span data-stu-id="bf085-129">The **/out** compiler option tells the compiler to output an EXE file and specifies the name of the output file (`TestCode.exe`).</span></span> <span data-ttu-id="bf085-130">Bu derleyici seçeneği isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="bf085-130">This compiler option is optional.</span></span> <span data-ttu-id="bf085-131">[/Reference](../../../../csharp/language-reference/compiler-options/reference-compiler-option.md) derleyici seçeneği DLL dosyası ya da, bu programın kullandığı dosyalarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="bf085-131">The [/reference](../../../../csharp/language-reference/compiler-options/reference-compiler-option.md) compiler option specifies the DLL file or files that this program uses.</span></span> <span data-ttu-id="bf085-132">Daha fazla bilgi için bkz: [/reference](../../../../csharp/language-reference/compiler-options/reference-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="bf085-132">For more information, see [/reference](../../../../csharp/language-reference/compiler-options/reference-compiler-option.md).</span></span>  
  
 <span data-ttu-id="bf085-133">Komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırı derleme ile csc.exe](../../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="bf085-133">For more information about building from the command line, see [Command-line Building With csc.exe](../../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf085-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bf085-134">See Also</span></span>  
 [<span data-ttu-id="bf085-135">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="bf085-135">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="bf085-136">Derlemeler ve Genel Derleme Önbelleği (C#)</span><span class="sxs-lookup"><span data-stu-id="bf085-136">Assemblies and the Global Assembly Cache (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="bf085-137">DLL işlevleri için bir sınıf oluşturma</span><span class="sxs-lookup"><span data-stu-id="bf085-137">Creating a Class to Hold DLL Functions</span></span>](../../../../framework/interop/creating-a-class-to-hold-dll-functions.md)
