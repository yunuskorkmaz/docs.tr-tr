---
title: 'Nasıl yapılır: komut satırını (C#) kullanarak derlemeler oluşturma ve kullanma'
ms.date: 07/20/2015
ms.assetid: 408ddce3-89e3-4e12-8353-34a49beeb72b
ms.openlocfilehash: 0cb964991cdbcdb3fa528ac96a0e883a37439099
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43514561"
---
# <a name="how-to-create-and-use-assemblies-using-the-command-line-c"></a><span data-ttu-id="94033-102">Nasıl yapılır: komut satırını (C#) kullanarak derlemeler oluşturma ve kullanma</span><span class="sxs-lookup"><span data-stu-id="94033-102">How to: Create and Use Assemblies Using the Command Line (C#)</span></span>
<span data-ttu-id="94033-103">Bir derleme veya dinamik bağlantı kitaplığı (DLL), programınız için çalışma zamanında bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="94033-103">An assembly, or a dynamic linking library (DLL), is linked to your program at run time.</span></span> <span data-ttu-id="94033-104">Oluşturma ve bir DLL kullanarak göstermek için aşağıdaki senaryoyu göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="94033-104">To demonstrate building and using a DLL, consider the following scenario:</span></span>  
  
-   <span data-ttu-id="94033-105">`MathLibrary.DLL`: Çalışma zamanında çağrılacak yöntem içerir kitaplık dosyası.</span><span class="sxs-lookup"><span data-stu-id="94033-105">`MathLibrary.DLL`: The library file that contains the methods to be called at run time.</span></span> <span data-ttu-id="94033-106">Bu örnekte, iki yöntem, DLL içeren `Add` ve `Multiply`.</span><span class="sxs-lookup"><span data-stu-id="94033-106">In this example, the DLL contains two methods, `Add` and `Multiply`.</span></span>  
  
-   <span data-ttu-id="94033-107">`Add`: Yöntem içerir kaynak dosyası `Add`.</span><span class="sxs-lookup"><span data-stu-id="94033-107">`Add`: The source file that contains the method `Add`.</span></span> <span data-ttu-id="94033-108">Parametrelerini toplamını döndürür.</span><span class="sxs-lookup"><span data-stu-id="94033-108">It returns the sum of its parameters.</span></span> <span data-ttu-id="94033-109">Sınıf `AddClass` yöntemi içeren `Add` ad alanının bir üyesidir `UtilityMethods`.</span><span class="sxs-lookup"><span data-stu-id="94033-109">The class `AddClass` that contains the method `Add` is a member of the namespace `UtilityMethods`.</span></span>  
  
-   <span data-ttu-id="94033-110">`Mult`: Yöntem içerir kaynak kodu `Multiply`.</span><span class="sxs-lookup"><span data-stu-id="94033-110">`Mult`: The source code that contains the method `Multiply`.</span></span> <span data-ttu-id="94033-111">Parametrelerini çarpımını döndürür.</span><span class="sxs-lookup"><span data-stu-id="94033-111">It returns the product of its parameters.</span></span> <span data-ttu-id="94033-112">Sınıf `MultiplyClass` yöntemi içeren `Multiply` ayrıca ad alanının bir üyesidir `UtilityMethods`.</span><span class="sxs-lookup"><span data-stu-id="94033-112">The class `MultiplyClass` that contains the method `Multiply` is also a member of the namespace `UtilityMethods`.</span></span>  
  
-   <span data-ttu-id="94033-113">`TestCode`: Dosyayı içeren `Main` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="94033-113">`TestCode`: The file that contains the `Main` method.</span></span> <span data-ttu-id="94033-114">Yöntemleri, toplam ve çalışma zamanı bağımsız değişken ürününü hesaplar için DLL dosyası içinde kullanır.</span><span class="sxs-lookup"><span data-stu-id="94033-114">It uses the methods in the DLL file to calculate the sum and the product of the run-time arguments.</span></span>  
  
## <a name="example"></a><span data-ttu-id="94033-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="94033-115">Example</span></span>  
  
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
  
 <span data-ttu-id="94033-116">Bu dosyayı içeren DLL yöntemleri kullanan algoritma `Add` ve `Multiply`.</span><span class="sxs-lookup"><span data-stu-id="94033-116">This file contains the algorithm that uses the DLL methods, `Add` and `Multiply`.</span></span> <span data-ttu-id="94033-117">Girilen komut satırından bağımsız değişkenlerini ayrıştırma ile başlayan `num1` ve `num2`.</span><span class="sxs-lookup"><span data-stu-id="94033-117">It starts with parsing the arguments entered from the command line, `num1` and `num2`.</span></span> <span data-ttu-id="94033-118">Kullanarak toplamı hesaplar `Add` metodunda `AddClass` sınıfını ve ürünü kullanarak `Multiply` metodunda `MultiplyClass` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="94033-118">Then it calculates the sum by using the `Add` method on the `AddClass` class, and the product by using the `Multiply` method on the `MultiplyClass` class.</span></span>  
  
 <span data-ttu-id="94033-119">Dikkat `using` dosyasının başında yönergesi DLL yöntemleri gibi derleme zamanında başvurmak için nitelenmemiş sınıf adları kullanmanıza olanak sağlar:</span><span class="sxs-lookup"><span data-stu-id="94033-119">Notice that the `using` directive at the beginning of the file enables you to use the unqualified class names to reference the DLL methods at compile time, as follows:</span></span>  
  
```csharp  
MultiplyClass.Multiply(num1, num2);  
```  
  
 <span data-ttu-id="94033-120">Aksi takdirde, tam olarak nitelenmiş adlar kullanacak şekilde gerekir:</span><span class="sxs-lookup"><span data-stu-id="94033-120">Otherwise, you have to use the fully qualified names, as follows:</span></span>  
  
```csharp  
UtilityMethods.MultiplyClass.Multiply(num1, num2);  
```  
  
## <a name="execution"></a><span data-ttu-id="94033-121">Yürütme</span><span class="sxs-lookup"><span data-stu-id="94033-121">Execution</span></span>  
 <span data-ttu-id="94033-122">Programı çalıştırmak için iki sayı, aşağıdaki gibi yazın, bir EXE dosyasının adını girin:</span><span class="sxs-lookup"><span data-stu-id="94033-122">To run the program, enter the name of the EXE file, followed by two numbers, as follows:</span></span>  
  
 `TestCode 1234 5678`  
  
## <a name="compiling-the-code"></a><span data-ttu-id="94033-123">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="94033-123">Compiling the Code</span></span>  
 <span data-ttu-id="94033-124">Dosyayı oluşturmak için `MathLibrary.DLL`, iki dosya derleme `Add` ve `Mult` şu komut satırını kullanarak.</span><span class="sxs-lookup"><span data-stu-id="94033-124">To build the file `MathLibrary.DLL`, compile the two files `Add` and `Mult` by using the following command line.</span></span>  
  
```csharp  
csc /target:library /out:MathLibrary.DLL Add.cs Mult.cs  
```  
  
 <span data-ttu-id="94033-125">[/Target: library](../../../../csharp/language-reference/compiler-options/target-library-compiler-option.md) derleyici seçeneği, derleyicinin çıktısını bir EXE dosyası yerine bir DLL söyler.</span><span class="sxs-lookup"><span data-stu-id="94033-125">The [/target:library](../../../../csharp/language-reference/compiler-options/target-library-compiler-option.md) compiler option tells the compiler to output a DLL instead of an EXE file.</span></span> <span data-ttu-id="94033-126">[/Out](../../../../csharp/language-reference/compiler-options/out-compiler-option.md) dosya adından önce gelen derleyici seçeneği, DLL dosya adı belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="94033-126">The [/out](../../../../csharp/language-reference/compiler-options/out-compiler-option.md) compiler option followed by a file name is used to specify the DLL file name.</span></span> <span data-ttu-id="94033-127">Aksi halde, derleyici ilk dosyayı kullanır (`Add.cs`) olarak DLL'in adı.</span><span class="sxs-lookup"><span data-stu-id="94033-127">Otherwise, the compiler uses the first file (`Add.cs`) as the name of the DLL.</span></span>  
  
 <span data-ttu-id="94033-128">Yürütülebilir dosyayı oluşturmak için `TestCode.exe`, şu komut satırını kullanın:</span><span class="sxs-lookup"><span data-stu-id="94033-128">To build the executable file, `TestCode.exe`, use the following command line:</span></span>  
  
```csharp  
csc /out:TestCode.exe /reference:MathLibrary.DLL TestCode.cs  
```  
  
 <span data-ttu-id="94033-129">**/Out** derleyici seçeneği, derleyiciye bir EXE dosyası çıkış ve çıktı dosyası adını belirtir (`TestCode.exe`).</span><span class="sxs-lookup"><span data-stu-id="94033-129">The **/out** compiler option tells the compiler to output an EXE file and specifies the name of the output file (`TestCode.exe`).</span></span> <span data-ttu-id="94033-130">Bu derleyici seçeneğini isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="94033-130">This compiler option is optional.</span></span> <span data-ttu-id="94033-131">[/Reference](../../../../csharp/language-reference/compiler-options/reference-compiler-option.md) derleyici seçeneği, DLL dosyasının veya bu programın kullandığı dosyaları belirtir.</span><span class="sxs-lookup"><span data-stu-id="94033-131">The [/reference](../../../../csharp/language-reference/compiler-options/reference-compiler-option.md) compiler option specifies the DLL file or files that this program uses.</span></span> <span data-ttu-id="94033-132">Daha fazla bilgi için [/reference](../../../../csharp/language-reference/compiler-options/reference-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="94033-132">For more information, see [/reference](../../../../csharp/language-reference/compiler-options/reference-compiler-option.md).</span></span>  
  
 <span data-ttu-id="94033-133">Komut satırından oluşturma hakkında daha fazla bilgi için bkz. [oluşturma ile komut satırı csc.exe](../../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="94033-133">For more information about building from the command line, see [Command-line Building With csc.exe](../../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94033-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="94033-134">See Also</span></span>

- [<span data-ttu-id="94033-135">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="94033-135">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="94033-136">Derlemeler ve Genel Derleme Önbelleği (C#)</span><span class="sxs-lookup"><span data-stu-id="94033-136">Assemblies and the Global Assembly Cache (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)  
- [<span data-ttu-id="94033-137">DLL İşlevleri için bir Sınıf Oluşturma</span><span class="sxs-lookup"><span data-stu-id="94033-137">Creating a Class to Hold DLL Functions</span></span>](../../../../framework/interop/creating-a-class-to-hold-dll-functions.md)
