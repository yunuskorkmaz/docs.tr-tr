---
title: Visual Basic'de Ana Yordam
ms.date: 07/20/2015
f1_keywords:
- vb.Main
helpviewer_keywords:
- Main procedure
- Main method [Visual Basic]
- main function
ms.assetid: f0db283e-f283-4464-b521-b90858cc1b44
ms.openlocfilehash: 641edd2d0e0dde5f509c8fa77ccf65358fa76a31
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61920120"
---
# <a name="main-procedure-in-visual-basic"></a><span data-ttu-id="cf35b-102">Visual Basic'de Ana Yordam</span><span class="sxs-lookup"><span data-stu-id="cf35b-102">Main Procedure in Visual Basic</span></span>
<span data-ttu-id="cf35b-103">Her Visual Basic uygulama çağrılan yordam içermelidir `Main`.</span><span class="sxs-lookup"><span data-stu-id="cf35b-103">Every Visual Basic application must contain a procedure called `Main`.</span></span> <span data-ttu-id="cf35b-104">Bu yordamı başlangıç noktası ve uygulamanız için genel denetimi olarak işlev görür.</span><span class="sxs-lookup"><span data-stu-id="cf35b-104">This procedure serves as the starting point and overall control for your application.</span></span> <span data-ttu-id="cf35b-105">.NET Framework çağrıları, `Main` uygulamanızı yüklendikten ve denetim geçirmeye hazır olduğunda yordamı.</span><span class="sxs-lookup"><span data-stu-id="cf35b-105">The .NET Framework calls your `Main` procedure when it has loaded your application and is ready to pass control to it.</span></span> <span data-ttu-id="cf35b-106">Bir Windows Forms uygulaması oluşturmakta olduğunuz sürece, yazmanız gereken `Main` yordamı kendi çalışan uygulamalar için.</span><span class="sxs-lookup"><span data-stu-id="cf35b-106">Unless you are creating a Windows Forms application, you must write the `Main` procedure for applications that run on their own.</span></span>  
  
 <span data-ttu-id="cf35b-107">`Main` ilk olarak çalışan kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="cf35b-107">`Main` contains the code that runs first.</span></span> <span data-ttu-id="cf35b-108">İçinde `Main`, hangi formun program başladığında önce yüklenmesi gereken belirlemek, uygulamanızı bir kopyasını zaten sistemde çalışıp çalışmadığını öğrenmek, uygulamanız için bir dizi değişkenlerini kurmak veya uygulamanın gerek duyduğu bir veritabanı.</span><span class="sxs-lookup"><span data-stu-id="cf35b-108">In `Main`, you can determine which form is to be loaded first when the program starts, find out if a copy of your application is already running on the system, establish a set of variables for your application, or open a database that the application requires.</span></span>  
  
## <a name="requirements-for-the-main-procedure"></a><span data-ttu-id="cf35b-109">Main yordamı için gereksinimleri</span><span class="sxs-lookup"><span data-stu-id="cf35b-109">Requirements for the Main Procedure</span></span>  
 <span data-ttu-id="cf35b-110">(Genellikle ile uzantısı .exe) kendi çalıştığı bir dosya içermelidir bir `Main` yordamı.</span><span class="sxs-lookup"><span data-stu-id="cf35b-110">A file that runs on its own (usually with extension .exe) must contain a `Main` procedure.</span></span> <span data-ttu-id="cf35b-111">Bir kitaplık (örneğin ile .dll uzantısı) kendi çalıştırılmaz ve gerekli olmayan bir `Main` yordamı.</span><span class="sxs-lookup"><span data-stu-id="cf35b-111">A library (for example with extension .dll) does not run on its own and does not require a `Main` procedure.</span></span> <span data-ttu-id="cf35b-112">Oluşturabileceğiniz farklı türde projelere gereksinimleri aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="cf35b-112">The requirements for the different types of projects you can create are as follows:</span></span>  
  
- <span data-ttu-id="cf35b-113">Konsol uygulamalarının çalıştığı kendi ve en az bir sağlamalısınız `Main` yordamı.</span><span class="sxs-lookup"><span data-stu-id="cf35b-113">Console applications run on their own, and you must supply at least one `Main` procedure.</span></span> <span data-ttu-id="cf35b-114">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="cf35b-114">.</span></span>  
  
- <span data-ttu-id="cf35b-115">Windows Forms uygulamaları kendi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="cf35b-115">Windows Forms applications run on their own.</span></span> <span data-ttu-id="cf35b-116">Ancak, Visual Basic Derleyicisi otomatik olarak oluşturduğu bir `Main` gibi bir yordamda bir uygulama ve zorunda kalmadan bir yazma.</span><span class="sxs-lookup"><span data-stu-id="cf35b-116">However, the Visual Basic compiler automatically generates a `Main` procedure in such an application, and you do not need to write one.</span></span>  
  
- <span data-ttu-id="cf35b-117">Sınıf kitaplıkları gerekli olmayan bir `Main` yordamı.</span><span class="sxs-lookup"><span data-stu-id="cf35b-117">Class libraries do not require a `Main` procedure.</span></span> <span data-ttu-id="cf35b-118">Bunlar, Windows Denetim Kitaplığı ve Web denetimi kitaplıkları içerir.</span><span class="sxs-lookup"><span data-stu-id="cf35b-118">These include Windows Control Libraries and Web Control Libraries.</span></span> <span data-ttu-id="cf35b-119">Web uygulamaları, sınıf kitaplıkları dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="cf35b-119">Web applications are deployed as class libraries.</span></span>  
  
## <a name="declaring-the-main-procedure"></a><span data-ttu-id="cf35b-120">Main yordamı bildirme</span><span class="sxs-lookup"><span data-stu-id="cf35b-120">Declaring the Main Procedure</span></span>  
 <span data-ttu-id="cf35b-121">Bildirmek için dört yolla `Main` yordamı.</span><span class="sxs-lookup"><span data-stu-id="cf35b-121">There are four ways to declare the `Main` procedure.</span></span> <span data-ttu-id="cf35b-122">Veya bağımsız değişken alabilir ve bir değer veya döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="cf35b-122">It can take arguments or not, and it can return a value or not.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cf35b-123">Bildirirseniz `Main` bir sınıfta kullanmalısınız `Shared` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="cf35b-123">If you declare `Main` in a class, you must use the `Shared` keyword.</span></span> <span data-ttu-id="cf35b-124">Bir modüldeki `Main` olması gerekmez `Shared`.</span><span class="sxs-lookup"><span data-stu-id="cf35b-124">In a module, `Main` does not need to be `Shared`.</span></span>  
  
- <span data-ttu-id="cf35b-125">Bildirmek için en kolay yolu olan bir `Sub` bağımsız değişken almaz veya bir değer döndüren yordam.</span><span class="sxs-lookup"><span data-stu-id="cf35b-125">The simplest way is to declare a `Sub` procedure that does not take arguments or return a value.</span></span>  
  
    ```  
    Module mainModule  
        Sub Main()  
            MsgBox("The Main procedure is starting the application.")  
            ' Insert call to appropriate starting place in your code.  
            MsgBox("The application is terminating.")  
        End Sub  
    End Module  
    ```  
  
- <span data-ttu-id="cf35b-126">`Main` Ayrıca döndürebilir bir `Integer` programınız için çıkış kodu işletim sisteminin kullandığı değer.</span><span class="sxs-lookup"><span data-stu-id="cf35b-126">`Main` can also return an `Integer` value, which the operating system uses as the exit code for your program.</span></span> <span data-ttu-id="cf35b-127">Diğer programları, Windows ERRORLEVEL değeri inceleyerek bu kodu test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cf35b-127">Other programs can test this code by examining the Windows ERRORLEVEL value.</span></span> <span data-ttu-id="cf35b-128">Çıkış kodu döndürülecek bildirmelisiniz `Main` olarak bir `Function` yerine yordam bir `Sub` yordamı.</span><span class="sxs-lookup"><span data-stu-id="cf35b-128">To return an exit code, you must declare `Main` as a `Function` procedure instead of a `Sub` procedure.</span></span>  
  
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
  
- <span data-ttu-id="cf35b-129">`Main` Ayrıca gerçekleştirebileceğiniz bir `String` bağımsız değişken olarak bir dizi.</span><span class="sxs-lookup"><span data-stu-id="cf35b-129">`Main` can also take a `String` array as an argument.</span></span> <span data-ttu-id="cf35b-130">Dizideki her bir dizenin programınızı çağırmak için kullanılan komut satırı bağımsız değişkenlerden biri içerir.</span><span class="sxs-lookup"><span data-stu-id="cf35b-130">Each string in the array contains one of the command-line arguments used to invoke your program.</span></span> <span data-ttu-id="cf35b-131">Değerlerine bağlı olarak farklı eylemleri gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cf35b-131">You can take different actions depending on their values.</span></span>  
  
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
  
- <span data-ttu-id="cf35b-132">Bildirebilirsiniz `Main` bir çıkış kodu gibi döndürmediğine ancak komut satırı bağımsız değişkenlerini inceleyin.</span><span class="sxs-lookup"><span data-stu-id="cf35b-132">You can declare `Main` to examine the command-line arguments but not return an exit code, as follows.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cf35b-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cf35b-133">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>
- <xref:System.Array.Length%2A>
- <xref:Microsoft.VisualBasic.Information.UBound%2A>
- [<span data-ttu-id="cf35b-134">Visual Basic programının yapısı</span><span class="sxs-lookup"><span data-stu-id="cf35b-134">Structure of a Visual Basic Program</span></span>](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)
- [<span data-ttu-id="cf35b-135">/main</span><span class="sxs-lookup"><span data-stu-id="cf35b-135">/main</span></span>](../../../visual-basic/reference/command-line-compiler/main.md)
- [<span data-ttu-id="cf35b-136">Shared</span><span class="sxs-lookup"><span data-stu-id="cf35b-136">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)
- [<span data-ttu-id="cf35b-137">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="cf35b-137">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="cf35b-138">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="cf35b-138">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="cf35b-139">Integer Veri Türü</span><span class="sxs-lookup"><span data-stu-id="cf35b-139">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [<span data-ttu-id="cf35b-140">String Veri Türü</span><span class="sxs-lookup"><span data-stu-id="cf35b-140">String Data Type</span></span>](../../../visual-basic/language-reference/data-types/string-data-type.md)
