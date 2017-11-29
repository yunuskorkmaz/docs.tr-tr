---
title: "Nasıl yapılır: (Visual Basic) komut satırını kullanarak derlemeler oluşturma ve kullanma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 229ff9fb-1bd1-403b-946b-526104864c60
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 72f3e91f9fb88019f937dcd281aa14ab4e887daf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-and-use-assemblies-using-the-command-line-visual-basic"></a><span data-ttu-id="07e2f-102">Nasıl yapılır: (Visual Basic) komut satırını kullanarak derlemeler oluşturma ve kullanma</span><span class="sxs-lookup"><span data-stu-id="07e2f-102">How to: Create and Use Assemblies Using the Command Line (Visual Basic)</span></span>
<span data-ttu-id="07e2f-103">Bir derlemeyi ya da dinamik bağlantı kitaplığı (DLL) programınıza çalışma zamanında bağlanır.</span><span class="sxs-lookup"><span data-stu-id="07e2f-103">An assembly, or a dynamic linking library (DLL), is linked to your program at run time.</span></span> <span data-ttu-id="07e2f-104">Derleme ve DLL kullanarak göstermek için aşağıdaki senaryoyu göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="07e2f-104">To demonstrate building and using a DLL, consider the following scenario:</span></span>  
  
-   <span data-ttu-id="07e2f-105">`MathLibrary.DLL`: Çalışma zamanında çağrılacak yöntem içerir kitaplık dosyası.</span><span class="sxs-lookup"><span data-stu-id="07e2f-105">`MathLibrary.DLL`: The library file that contains the methods to be called at run time.</span></span> <span data-ttu-id="07e2f-106">Bu örnekte, iki yöntem DLL içeren `Add` ve `Multiply`.</span><span class="sxs-lookup"><span data-stu-id="07e2f-106">In this example, the DLL contains two methods, `Add` and `Multiply`.</span></span>  
  
-   <span data-ttu-id="07e2f-107">`Add`: Yöntem içerir kaynak dosya `Add`.</span><span class="sxs-lookup"><span data-stu-id="07e2f-107">`Add`: The source file that contains the method `Add`.</span></span> <span data-ttu-id="07e2f-108">Bunu parametrelerinin toplamını döndürür.</span><span class="sxs-lookup"><span data-stu-id="07e2f-108">It returns the sum of its parameters.</span></span> <span data-ttu-id="07e2f-109">Sınıf `AddClass` yöntemi içeren `Add` ad üyesi `UtilityMethods`.</span><span class="sxs-lookup"><span data-stu-id="07e2f-109">The class `AddClass` that contains the method `Add` is a member of the namespace `UtilityMethods`.</span></span>  
  
-   <span data-ttu-id="07e2f-110">`Mult`: Yöntem içerir kaynak kodu `Multiply`.</span><span class="sxs-lookup"><span data-stu-id="07e2f-110">`Mult`: The source code that contains the method `Multiply`.</span></span> <span data-ttu-id="07e2f-111">Bunu parametrelerinin çarpımını döndürür.</span><span class="sxs-lookup"><span data-stu-id="07e2f-111">It returns the product of its parameters.</span></span> <span data-ttu-id="07e2f-112">Sınıf `MultiplyClass` yöntemi içeren `Multiply` de ad alanının bir üyesidir `UtilityMethods`.</span><span class="sxs-lookup"><span data-stu-id="07e2f-112">The class `MultiplyClass` that contains the method `Multiply` is also a member of the namespace `UtilityMethods`.</span></span>  
  
-   <span data-ttu-id="07e2f-113">`TestCode`: İçerir dosya `Main` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="07e2f-113">`TestCode`: The file that contains the `Main` method.</span></span> <span data-ttu-id="07e2f-114">Yöntemleri, toplam ve çalışma zamanı değişkenleri Ürün hesaplamak için DLL dosyasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="07e2f-114">It uses the methods in the DLL file to calculate the sum and the product of the run-time arguments.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07e2f-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="07e2f-115">Example</span></span>  
  
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
  
 <span data-ttu-id="07e2f-116">Bu dosya DLL yöntemleri tarafından kullanılan algoritmasını içerir `Add` ve `Multiply`.</span><span class="sxs-lookup"><span data-stu-id="07e2f-116">This file contains the algorithm that uses the DLL methods, `Add` and `Multiply`.</span></span> <span data-ttu-id="07e2f-117">Komut satırından girilen bağımsız değişkenlerini ayrıştırma ile başlayan `num1` ve `num2`.</span><span class="sxs-lookup"><span data-stu-id="07e2f-117">It starts with parsing the arguments entered from the command line, `num1` and `num2`.</span></span> <span data-ttu-id="07e2f-118">Kullanarak toplamı hesaplar sonra `Add` yöntemi `AddClass` sınıfını ve ürünü kullanarak `Multiply` yöntemi `MultiplyClass` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="07e2f-118">Then it calculates the sum by using the `Add` method on the `AddClass` class, and the product by using the `Multiply` method on the `MultiplyClass` class.</span></span>  
  
 <span data-ttu-id="07e2f-119">Dikkat `Imports` dosyasının başında deyimi DLL yöntemleri derleme zamanında şu şekilde başvurmak için nitelenmemiş sınıf adları kullanabilmenizi sağlar:</span><span class="sxs-lookup"><span data-stu-id="07e2f-119">Notice that the  `Imports` statement at the beginning of the file enables you to use the unqualified class names to reference the DLL methods at compile time, as follows:</span></span>  
  
```vb  
MultiplyClass.Multiply(num1, num2)  
```  
  
 <span data-ttu-id="07e2f-120">Aksi halde, tam olarak nitelenmiş adlar aşağıdaki gibi kullanmak zorunda:</span><span class="sxs-lookup"><span data-stu-id="07e2f-120">Otherwise, you have to use the fully qualified names, as follows:</span></span>  
  
```vb  
UtilityMethods.MultiplyClass.Multiply(num1, num2)  
```  
  
## <a name="execution"></a><span data-ttu-id="07e2f-121">Yürütme</span><span class="sxs-lookup"><span data-stu-id="07e2f-121">Execution</span></span>  
 <span data-ttu-id="07e2f-122">Programı çalıştırmak için iki numaralarına göre aşağıdaki gibi ardından EXE dosyasının adını girin:</span><span class="sxs-lookup"><span data-stu-id="07e2f-122">To run the program, enter the name of the EXE file, followed by two numbers, as follows:</span></span>  
  
 `TestCode 1234 5678`  
  
## <a name="compiling-the-code"></a><span data-ttu-id="07e2f-123">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="07e2f-123">Compiling the Code</span></span>  
 <span data-ttu-id="07e2f-124">Dosyasını oluşturmak için `MathLibrary.DLL`, iki dosyalarını derlemek `Add` ve `Mult` aşağıdaki komut satırını kullanarak.</span><span class="sxs-lookup"><span data-stu-id="07e2f-124">To build the file `MathLibrary.DLL`, compile the two files `Add` and `Mult` by using the following command line.</span></span>  
  
```vb  
vbc /target:library /out:MathLibrary.DLL Add.vb Mult.vb  
```  
  
 <span data-ttu-id="07e2f-125">[/Target (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/target.md) derleyici seçeneği bir EXE dosyası yerine bir DLL çıktısını almak için derleyici söyler.</span><span class="sxs-lookup"><span data-stu-id="07e2f-125">The [/target (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/target.md) compiler option tells the compiler to output a DLL instead of an EXE file.</span></span> <span data-ttu-id="07e2f-126">[/Out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md) dosya adından derleyici seçeneği DLL dosya adı belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="07e2f-126">The [/out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md) compiler option followed by a file name is used to specify the DLL file name.</span></span> <span data-ttu-id="07e2f-127">Aksi durumda, ilk dosya derleyici kullanır (`Add.vb`) DLL adından farklı.</span><span class="sxs-lookup"><span data-stu-id="07e2f-127">Otherwise, the compiler uses the first file (`Add.vb`) as the name of the DLL.</span></span>  
  
 <span data-ttu-id="07e2f-128">Yürütülebilir dosyasını oluşturmak için `TestCode.exe`, aşağıdaki komut satırını kullanın:</span><span class="sxs-lookup"><span data-stu-id="07e2f-128">To build the executable file, `TestCode.exe`, use the following command line:</span></span>  
  
```vb  
vbc /out:TestCode.exe /reference:MathLibrary.DLL TestCode.vb  
```  
  
 <span data-ttu-id="07e2f-129">**/Out** derleyici seçeneği çıkış bir EXE dosyası bildirir ve çıktı dosyası adını belirtir (`TestCode.exe`).</span><span class="sxs-lookup"><span data-stu-id="07e2f-129">The **/out** compiler option tells the compiler to output an EXE file and specifies the name of the output file (`TestCode.exe`).</span></span> <span data-ttu-id="07e2f-130">Bu derleyici seçeneği isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="07e2f-130">This compiler option is optional.</span></span> <span data-ttu-id="07e2f-131">[/Reference (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md) derleyici seçeneği DLL dosyası ya da, bu programın kullandığı dosyalarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="07e2f-131">The [/reference (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md) compiler option specifies the DLL file or files that this program uses.</span></span>  
  
 <span data-ttu-id="07e2f-132">Komut satırından oluşturma hakkında daha fazla bilgi için bkz: ve [komut satırından derleme](../../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="07e2f-132">For more information about building from the command line, see  and [Building from the Command Line](../../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07e2f-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="07e2f-133">See Also</span></span>  
 [<span data-ttu-id="07e2f-134">Programlama Kavramları</span><span class="sxs-lookup"><span data-stu-id="07e2f-134">Programming Concepts</span></span>](../../../../visual-basic/programming-guide/concepts/index.md)  
 [<span data-ttu-id="07e2f-135">Derlemeler ve Genel Derleme Önbelleği (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="07e2f-135">Assemblies and the Global Assembly Cache (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="07e2f-136">DLL işlevleri için bir sınıf oluşturma</span><span class="sxs-lookup"><span data-stu-id="07e2f-136">Creating a Class to Hold DLL Functions</span></span>](../../../../framework/interop/creating-a-class-to-hold-dll-functions.md)
