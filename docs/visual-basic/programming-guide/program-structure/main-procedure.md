---
title: Visual Basic'de Ana Yordam
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Main
helpviewer_keywords:
- Main procedure
- Main method [Visual Basic]
- main function
ms.assetid: f0db283e-f283-4464-b521-b90858cc1b44
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6de98ad4e470cd0becaf25f5a9a00c8095e44b15
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="main-procedure-in-visual-basic"></a><span data-ttu-id="3aecb-102">Visual Basic'de Ana Yordam</span><span class="sxs-lookup"><span data-stu-id="3aecb-102">Main Procedure in Visual Basic</span></span>
<span data-ttu-id="3aecb-103">Her Visual Basic uygulama çağrılan bir yordam içermelidir `Main`.</span><span class="sxs-lookup"><span data-stu-id="3aecb-103">Every Visual Basic application must contain a procedure called `Main`.</span></span> <span data-ttu-id="3aecb-104">Bu yordam görevi görür, başlangıç noktası ve genel olarak, uygulamanız için Denetim aynıdır.</span><span class="sxs-lookup"><span data-stu-id="3aecb-104">This procedure serves as the starting point and overall control for your application.</span></span> <span data-ttu-id="3aecb-105">.NET Framework çağrıları, `Main` uygulamanızı yükledi ve denetim geçirmeye hazır olduğunda yordamı.</span><span class="sxs-lookup"><span data-stu-id="3aecb-105">The .NET Framework calls your `Main` procedure when it has loaded your application and is ready to pass control to it.</span></span> <span data-ttu-id="3aecb-106">Bir Windows Forms uygulaması oluşturmakta olduğunuz sürece yazmalısınız `Main` yordamı kendi çalışan uygulamalar için.</span><span class="sxs-lookup"><span data-stu-id="3aecb-106">Unless you are creating a Windows Forms application, you must write the `Main` procedure for applications that run on their own.</span></span>  
  
 <span data-ttu-id="3aecb-107">`Main`ilk çalışan bir kod içerir.</span><span class="sxs-lookup"><span data-stu-id="3aecb-107">`Main` contains the code that runs first.</span></span> <span data-ttu-id="3aecb-108">İçinde `Main`, hangi formda bir program başlatıldığında önce yüklenmesi gereken belirlemek, uygulamanızı bir kopyası zaten sistemde çalışıp çalışmadığını öğrenmek, uygulamanız için değişkenleri kümesinin kurmak veya uygulama gerektiren bir veritabanını açın.</span><span class="sxs-lookup"><span data-stu-id="3aecb-108">In `Main`, you can determine which form is to be loaded first when the program starts, find out if a copy of your application is already running on the system, establish a set of variables for your application, or open a database that the application requires.</span></span>  
  
## <a name="requirements-for-the-main-procedure"></a><span data-ttu-id="3aecb-109">Main yordamı için gereksinimleri</span><span class="sxs-lookup"><span data-stu-id="3aecb-109">Requirements for the Main Procedure</span></span>  
 <span data-ttu-id="3aecb-110">(Genellikle ile .exe uzantılı) kendi üzerinde çalıştığı bir dosyanın içermesi gereken bir `Main` yordamı.</span><span class="sxs-lookup"><span data-stu-id="3aecb-110">A file that runs on its own (usually with extension .exe) must contain a `Main` procedure.</span></span> <span data-ttu-id="3aecb-111">Bir kitaplıkla (örneğin uzantısı .dll) kendi çalıştırılmaz ve gerekli olmadığı bir `Main` yordamı.</span><span class="sxs-lookup"><span data-stu-id="3aecb-111">A library (for example with extension .dll) does not run on its own and does not require a `Main` procedure.</span></span> <span data-ttu-id="3aecb-112">Oluşturabileceğiniz farklı proje türleri için gereksinimleri aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="3aecb-112">The requirements for the different types of projects you can create are as follows:</span></span>  
  
-   <span data-ttu-id="3aecb-113">Konsol uygulamaları çalıştıracağınız kendi ve en az bir sağlamalısınız `Main` yordamı.</span><span class="sxs-lookup"><span data-stu-id="3aecb-113">Console applications run on their own, and you must supply at least one `Main` procedure.</span></span> <span data-ttu-id="3aecb-114">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="3aecb-114">.</span></span>  
  
-   <span data-ttu-id="3aecb-115">Windows Forms uygulamaları kendi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="3aecb-115">Windows Forms applications run on their own.</span></span> <span data-ttu-id="3aecb-116">Ancak, Visual Basic derleyici otomatik olarak oluşturan bir `Main` gibi yordamda bir uygulama ve gerekmez bir yazma.</span><span class="sxs-lookup"><span data-stu-id="3aecb-116">However, the Visual Basic compiler automatically generates a `Main` procedure in such an application, and you do not need to write one.</span></span>  
  
-   <span data-ttu-id="3aecb-117">Sınıf kitaplıkları gerekli olmadığı bir `Main` yordamı.</span><span class="sxs-lookup"><span data-stu-id="3aecb-117">Class libraries do not require a `Main` procedure.</span></span> <span data-ttu-id="3aecb-118">Bunlar, Windows Denetim kitaplıklar ve Web denetimi kitaplıkları içerir.</span><span class="sxs-lookup"><span data-stu-id="3aecb-118">These include Windows Control Libraries and Web Control Libraries.</span></span> <span data-ttu-id="3aecb-119">Web uygulamaları sınıf kitaplıkları dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="3aecb-119">Web applications are deployed as class libraries.</span></span>  
  
## <a name="declaring-the-main-procedure"></a><span data-ttu-id="3aecb-120">Main yordamı bildirme</span><span class="sxs-lookup"><span data-stu-id="3aecb-120">Declaring the Main Procedure</span></span>  
 <span data-ttu-id="3aecb-121">Bildirmek için dört yolla `Main` yordamı.</span><span class="sxs-lookup"><span data-stu-id="3aecb-121">There are four ways to declare the `Main` procedure.</span></span> <span data-ttu-id="3aecb-122">Bağımsız değişkenler veya alabilir ve bir değer veya döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="3aecb-122">It can take arguments or not, and it can return a value or not.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3aecb-123">Bildirirseniz `Main` bir sınıfta kullanmalısınız `Shared` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="3aecb-123">If you declare `Main` in a class, you must use the `Shared` keyword.</span></span> <span data-ttu-id="3aecb-124">Bir modüldeki `Main` olması gerekmez `Shared`.</span><span class="sxs-lookup"><span data-stu-id="3aecb-124">In a module, `Main` does not need to be `Shared`.</span></span>  
  
-   <span data-ttu-id="3aecb-125">En basit yolu bildirmektir bir `Sub` olmayan bağımsız değişkenler almayan veya bir değer döndüren bir yordam.</span><span class="sxs-lookup"><span data-stu-id="3aecb-125">The simplest way is to declare a `Sub` procedure that does not take arguments or return a value.</span></span>  
  
    ```  
    Module mainModule  
        Sub Main()  
            MsgBox("The Main procedure is starting the application.")  
            ' Insert call to appropriate starting place in your code.  
            MsgBox("The application is terminating.")  
        End Sub  
    End Module  
    ```  
  
-   <span data-ttu-id="3aecb-126">`Main`Ayrıca dönebilirsiniz bir `Integer` işletim sistemi çıkış kodu programınızın kullanır. değer.</span><span class="sxs-lookup"><span data-stu-id="3aecb-126">`Main` can also return an `Integer` value, which the operating system uses as the exit code for your program.</span></span> <span data-ttu-id="3aecb-127">Diğer programları Windows ERRORLEVEL değerini inceleyerek bu kodu test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3aecb-127">Other programs can test this code by examining the Windows ERRORLEVEL value.</span></span> <span data-ttu-id="3aecb-128">Bir çıkış kodu döndürülecek bildirmelisiniz `Main` olarak bir `Function` yordamı yerine bir `Sub` yordamı.</span><span class="sxs-lookup"><span data-stu-id="3aecb-128">To return an exit code, you must declare `Main` as a `Function` procedure instead of a `Sub` procedure.</span></span>  
  
    ```  
    Module mainModule  
        Function Main() As Integer  
            MsgBox("The Main procedure is starting the application.")  
            Dim returnValue As Integer = 0  
            ' Insert call to appropriate starting place in your code.  
            ' On return, assign appropriate value to returnValue.  
            ' 0 usually means successful completion.  
            MsgBox("The application is terminating with error level " &  
                 CStr(returnValue) & ".")  
            Return returnValue  
        End Function  
    End Module  
    ```  
  
-   <span data-ttu-id="3aecb-129">`Main`Ayrıca gerçekleştirebileceğiniz bir `String` bağımsız değişken olarak bir dizi.</span><span class="sxs-lookup"><span data-stu-id="3aecb-129">`Main` can also take a `String` array as an argument.</span></span> <span data-ttu-id="3aecb-130">Dizideki her dize programınızı çağırmak için kullanılan komut satırı bağımsız değişkenleri birini içerir.</span><span class="sxs-lookup"><span data-stu-id="3aecb-130">Each string in the array contains one of the command-line arguments used to invoke your program.</span></span> <span data-ttu-id="3aecb-131">Değerlerine bağlı olarak farklı işlemler yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3aecb-131">You can take different actions depending on their values.</span></span>  
  
    ```  
    Module mainModule  
        Function Main(ByVal cmdArgs() As String) As Integer  
            MsgBox("The Main procedure is starting the application.")  
            Dim returnValue As Integer = 0  
            ' See if there are any arguments.  
            If cmdArgs.Length > 0 Then  
                For argNum As Integer = 0 To UBound(cmdArgs, 1)  
                    ' Insert code to examine cmdArgs(argNum) and take  
                    ' appropriate action based on its value.  
                Next argNum  
            End If  
            ' Insert call to appropriate starting place in your code.  
            ' On return, assign appropriate value to returnValue.  
            ' 0 usually means successful completion.  
            MsgBox("The application is terminating with error level " &  
                 CStr(returnValue) & ".")  
            Return returnValue  
        End Function  
    End Module  
    ```  
  
-   <span data-ttu-id="3aecb-132">Bildirebilirsiniz `Main` komut satırı bağımsız değişkenleri inceleyin, ancak bir çıkış kodu gibi iade değil.</span><span class="sxs-lookup"><span data-stu-id="3aecb-132">You can declare `Main` to examine the command-line arguments but not return an exit code, as follows.</span></span>  
  
    ```  
    Module mainModule  
        Sub Main(ByVal cmdArgs() As String)  
            MsgBox("The Main procedure is starting the application.")  
            Dim returnValue As Integer = 0  
            ' See if there are any arguments.  
            If cmdArgs.Length > 0 Then  
                For argNum As Integer = 0 To UBound(cmdArgs, 1)  
                    ' Insert code to examine cmdArgs(argNum) and take  
                    ' appropriate action based on its value.  
                Next argNum  
            End If  
            ' Insert call to appropriate starting place in your code.  
            MsgBox("The application is terminating.")  
        End Sub  
    End Module  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="3aecb-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3aecb-133">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>  
 <xref:System.Array.Length%2A>  
 <xref:Microsoft.VisualBasic.Information.UBound%2A>  
 [<span data-ttu-id="3aecb-134">Visual Basic programının yapısı</span><span class="sxs-lookup"><span data-stu-id="3aecb-134">Structure of a Visual Basic Program</span></span>](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)  
 [<span data-ttu-id="3aecb-135">/main</span><span class="sxs-lookup"><span data-stu-id="3aecb-135">/main</span></span>](../../../visual-basic/reference/command-line-compiler/main.md)  
 [<span data-ttu-id="3aecb-136">Shared</span><span class="sxs-lookup"><span data-stu-id="3aecb-136">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)  
 [<span data-ttu-id="3aecb-137">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="3aecb-137">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="3aecb-138">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="3aecb-138">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="3aecb-139">Integer Veri Türü</span><span class="sxs-lookup"><span data-stu-id="3aecb-139">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)  
 [<span data-ttu-id="3aecb-140">String Veri Türü</span><span class="sxs-lookup"><span data-stu-id="3aecb-140">String Data Type</span></span>](../../../visual-basic/language-reference/data-types/string-data-type.md)
