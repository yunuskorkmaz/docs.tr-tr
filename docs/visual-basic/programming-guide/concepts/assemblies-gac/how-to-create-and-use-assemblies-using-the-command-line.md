---
title: 'Nasıl yapılır: (Visual Basic) komut satırını kullanarak derlemeler oluşturma ve kullanma'
ms.date: 03/14/2018
ms.assetid: 229ff9fb-1bd1-403b-946b-526104864c60
ms.openlocfilehash: eecd644a7b91492f0a78cf969cfa71ae927609ab
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819410"
---
# <a name="how-to-create-and-use-assemblies-using-the-command-line-visual-basic"></a><span data-ttu-id="4bb5e-102">Nasıl yapılır: (Visual Basic) komut satırını kullanarak derlemeler oluşturma ve kullanma</span><span class="sxs-lookup"><span data-stu-id="4bb5e-102">How to: Create and Use Assemblies Using the Command Line (Visual Basic)</span></span>
<span data-ttu-id="4bb5e-103">Bir derleme veya dinamik bağlantı kitaplığı (DLL), programınız için çalışma zamanında bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="4bb5e-103">An assembly, or a dynamic linking library (DLL), is linked to your program at run time.</span></span> <span data-ttu-id="4bb5e-104">Oluşturma ve bir DLL kullanarak göstermek için aşağıdaki senaryoyu göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="4bb5e-104">To demonstrate building and using a DLL, consider the following scenario:</span></span>  
  
-   <span data-ttu-id="4bb5e-105">`MathLibrary.DLL`: Çalışma zamanında çağrılabilir yöntemleri içeren kitaplık dosyası.</span><span class="sxs-lookup"><span data-stu-id="4bb5e-105">`MathLibrary.DLL`: The library file that contains the methods to be called at run time.</span></span> <span data-ttu-id="4bb5e-106">Bu örnekte, iki yöntem, DLL içeren `Add` ve `Multiply`.</span><span class="sxs-lookup"><span data-stu-id="4bb5e-106">In this example, the DLL contains two methods, `Add` and `Multiply`.</span></span>  
  
-   <span data-ttu-id="4bb5e-107">`Add`: Yöntemi içeren kaynak dosyayı `Add`.</span><span class="sxs-lookup"><span data-stu-id="4bb5e-107">`Add`: The source file that contains the method `Add`.</span></span> <span data-ttu-id="4bb5e-108">Parametrelerini toplamını döndürür.</span><span class="sxs-lookup"><span data-stu-id="4bb5e-108">It returns the sum of its parameters.</span></span> <span data-ttu-id="4bb5e-109">Sınıf `AddClass` yöntemi içeren `Add` ad alanının bir üyesidir `UtilityMethods`.</span><span class="sxs-lookup"><span data-stu-id="4bb5e-109">The class `AddClass` that contains the method `Add` is a member of the namespace `UtilityMethods`.</span></span>  
  
-   <span data-ttu-id="4bb5e-110">`Mult`: Yöntemi içeren kaynak kodu `Multiply`.</span><span class="sxs-lookup"><span data-stu-id="4bb5e-110">`Mult`: The source code that contains the method `Multiply`.</span></span> <span data-ttu-id="4bb5e-111">Parametrelerini çarpımını döndürür.</span><span class="sxs-lookup"><span data-stu-id="4bb5e-111">It returns the product of its parameters.</span></span> <span data-ttu-id="4bb5e-112">Sınıf `MultiplyClass` yöntemi içeren `Multiply` ayrıca ad alanının bir üyesidir `UtilityMethods`.</span><span class="sxs-lookup"><span data-stu-id="4bb5e-112">The class `MultiplyClass` that contains the method `Multiply` is also a member of the namespace `UtilityMethods`.</span></span>  
  
-   <span data-ttu-id="4bb5e-113">`TestCode`: İçeren dosyayı `Main` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4bb5e-113">`TestCode`: The file that contains the `Main` method.</span></span> <span data-ttu-id="4bb5e-114">Yöntemleri, toplam ve çalışma zamanı bağımsız değişken ürününü hesaplar için DLL dosyası içinde kullanır.</span><span class="sxs-lookup"><span data-stu-id="4bb5e-114">It uses the methods in the DLL file to calculate the sum and the product of the run-time arguments.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4bb5e-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="4bb5e-115">Example</span></span>  
  
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
  
 <span data-ttu-id="4bb5e-116">Bu dosyayı içeren DLL yöntemleri kullanan algoritma `Add` ve `Multiply`.</span><span class="sxs-lookup"><span data-stu-id="4bb5e-116">This file contains the algorithm that uses the DLL methods, `Add` and `Multiply`.</span></span> <span data-ttu-id="4bb5e-117">Girilen komut satırından bağımsız değişkenlerini ayrıştırma ile başlayan `num1` ve `num2`.</span><span class="sxs-lookup"><span data-stu-id="4bb5e-117">It starts with parsing the arguments entered from the command line, `num1` and `num2`.</span></span> <span data-ttu-id="4bb5e-118">Kullanarak toplamı hesaplar `Add` metodunda `AddClass` sınıfını ve ürünü kullanarak `Multiply` metodunda `MultiplyClass` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="4bb5e-118">Then it calculates the sum by using the `Add` method on the `AddClass` class, and the product by using the `Multiply` method on the `MultiplyClass` class.</span></span>  
  
 <span data-ttu-id="4bb5e-119">Dikkat `Imports` dosyasının başında deyimi DLL yöntemleri gibi derleme zamanında başvurmak için nitelenmemiş sınıf adları kullanmanıza olanak sağlar:</span><span class="sxs-lookup"><span data-stu-id="4bb5e-119">Notice that the  `Imports` statement at the beginning of the file enables you to use the unqualified class names to reference the DLL methods at compile time, as follows:</span></span>  
  
```vb  
MultiplyClass.Multiply(num1, num2)  
```  
  
 <span data-ttu-id="4bb5e-120">Aksi takdirde, tam olarak nitelenmiş adlar kullanacak şekilde gerekir:</span><span class="sxs-lookup"><span data-stu-id="4bb5e-120">Otherwise, you have to use the fully qualified names, as follows:</span></span>  
  
```vb  
UtilityMethods.MultiplyClass.Multiply(num1, num2)  
```  
  
## <a name="execution"></a><span data-ttu-id="4bb5e-121">Yürütme</span><span class="sxs-lookup"><span data-stu-id="4bb5e-121">Execution</span></span>  
 <span data-ttu-id="4bb5e-122">Programı çalıştırmak için iki sayı, aşağıdaki gibi yazın, bir EXE dosyasının adını girin:</span><span class="sxs-lookup"><span data-stu-id="4bb5e-122">To run the program, enter the name of the EXE file, followed by two numbers, as follows:</span></span>  
  
 `TestCode 1234 5678`  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4bb5e-123">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="4bb5e-123">Compiling the Code</span></span>  
 <span data-ttu-id="4bb5e-124">Dosyayı oluşturmak için `MathLibrary.DLL`, iki dosya derleme `Add` ve `Mult` şu komut satırını kullanarak.</span><span class="sxs-lookup"><span data-stu-id="4bb5e-124">To build the file `MathLibrary.DLL`, compile the two files `Add` and `Mult` by using the following command line.</span></span>  
  
```console  
vbc -target:library -out:MathLibrary.DLL Add.vb Mult.vb  
```  
  
 <span data-ttu-id="4bb5e-125">[-Target (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/target.md) derleyici seçeneği, derleyicinin çıktısını bir EXE dosyası yerine bir DLL söyler.</span><span class="sxs-lookup"><span data-stu-id="4bb5e-125">The [-target (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/target.md) compiler option tells the compiler to output a DLL instead of an EXE file.</span></span> <span data-ttu-id="4bb5e-126">[-Out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md) dosya adından önce gelen derleyici seçeneği, DLL dosya adı belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4bb5e-126">The [-out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md) compiler option followed by a file name is used to specify the DLL file name.</span></span> <span data-ttu-id="4bb5e-127">Aksi halde, derleyici ilk dosyayı kullanır (`Add.vb`) olarak DLL'in adı.</span><span class="sxs-lookup"><span data-stu-id="4bb5e-127">Otherwise, the compiler uses the first file (`Add.vb`) as the name of the DLL.</span></span>  
  
 <span data-ttu-id="4bb5e-128">Yürütülebilir dosyayı oluşturmak için `TestCode.exe`, şu komut satırını kullanın:</span><span class="sxs-lookup"><span data-stu-id="4bb5e-128">To build the executable file, `TestCode.exe`, use the following command line:</span></span>  
  
```console  
vbc -out:TestCode.exe -reference:MathLibrary.DLL TestCode.vb  
```  
  
 <span data-ttu-id="4bb5e-129">**-Out** derleyici seçeneği, derleyiciye bir EXE dosyası çıkış ve çıktı dosyası adını belirtir (`TestCode.exe`).</span><span class="sxs-lookup"><span data-stu-id="4bb5e-129">The **-out** compiler option tells the compiler to output an EXE file and specifies the name of the output file (`TestCode.exe`).</span></span> <span data-ttu-id="4bb5e-130">Bu derleyici seçeneğini isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="4bb5e-130">This compiler option is optional.</span></span> <span data-ttu-id="4bb5e-131">[-Başvuru (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md) derleyici seçeneği, DLL dosyasının veya bu programın kullandığı dosyaları belirtir.</span><span class="sxs-lookup"><span data-stu-id="4bb5e-131">The [-reference (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md) compiler option specifies the DLL file or files that this program uses.</span></span>  
  
 <span data-ttu-id="4bb5e-132">Komut satırından oluşturma hakkında daha fazla bilgi için bkz ve [komut satırından derleme](../../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="4bb5e-132">For more information about building from the command line, see  and [Building from the Command Line](../../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bb5e-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4bb5e-133">See also</span></span>

- [<span data-ttu-id="4bb5e-134">Programlama Kavramları</span><span class="sxs-lookup"><span data-stu-id="4bb5e-134">Programming Concepts</span></span>](../../../../visual-basic/programming-guide/concepts/index.md)
- [<span data-ttu-id="4bb5e-135">.NET’te bütünleştirilmiş kodlar</span><span class="sxs-lookup"><span data-stu-id="4bb5e-135">Assemblies in .NET</span></span>](../../../../standard/assembly/index.md)
- [<span data-ttu-id="4bb5e-136">DLL İşlevleri için bir Sınıf Oluşturma</span><span class="sxs-lookup"><span data-stu-id="4bb5e-136">Creating a Class to Hold DLL Functions</span></span>](../../../../framework/interop/creating-a-class-to-hold-dll-functions.md)
