---
description: 'Hakkında daha fazla bilgi edinin: Visual Basic ana yordam'
title: Main Yordamı
ms.date: 07/20/2015
f1_keywords:
- vb.Main
helpviewer_keywords:
- Main procedure
- Main method [Visual Basic]
- main function
ms.assetid: f0db283e-f283-4464-b521-b90858cc1b44
ms.openlocfilehash: b25190ef216fe4219923a27d6bbe0acff4536685
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100432812"
---
# <a name="main-procedure-in-visual-basic"></a><span data-ttu-id="2b4a8-103">Visual Basic'de Ana Yordam</span><span class="sxs-lookup"><span data-stu-id="2b4a8-103">Main Procedure in Visual Basic</span></span>

<span data-ttu-id="2b4a8-104">Her Visual Basic uygulamasının adlı bir yordam içermesi gerekir `Main` .</span><span class="sxs-lookup"><span data-stu-id="2b4a8-104">Every Visual Basic application must contain a procedure called `Main`.</span></span> <span data-ttu-id="2b4a8-105">Bu yordam, uygulamanız için başlangıç noktası ve genel denetim görevi görür.</span><span class="sxs-lookup"><span data-stu-id="2b4a8-105">This procedure serves as the starting point and overall control for your application.</span></span> <span data-ttu-id="2b4a8-106">.NET Framework, `Main` uygulamanızı yüklemiş ve denetimi geçirmeye hazırsa, yordamınız çağrılır.</span><span class="sxs-lookup"><span data-stu-id="2b4a8-106">The .NET Framework calls your `Main` procedure when it has loaded your application and is ready to pass control to it.</span></span> <span data-ttu-id="2b4a8-107">Windows Forms uygulaması oluşturmadığınız takdirde, `Main` kendi üzerinde çalışan uygulamalar için yordamı yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2b4a8-107">Unless you are creating a Windows Forms application, you must write the `Main` procedure for applications that run on their own.</span></span>

 <span data-ttu-id="2b4a8-108">`Main` İlk olarak çalışan kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="2b4a8-108">`Main` contains the code that runs first.</span></span> <span data-ttu-id="2b4a8-109">İçinde `Main` , program başlatıldığında önce hangi formun yükleneceğini belirleyebilirsiniz, uygulamanızın bir kopyasının sistemde zaten çalışmakta olup olmadığını bulabilir, uygulamanız için bir dizi değişken oluşturun veya uygulamanın gerektirdiği bir veritabanını açın.</span><span class="sxs-lookup"><span data-stu-id="2b4a8-109">In `Main`, you can determine which form is to be loaded first when the program starts, find out if a copy of your application is already running on the system, establish a set of variables for your application, or open a database that the application requires.</span></span>

## <a name="requirements-for-the-main-procedure"></a><span data-ttu-id="2b4a8-110">Ana yordamın gereksinimleri</span><span class="sxs-lookup"><span data-stu-id="2b4a8-110">Requirements for the Main Procedure</span></span>

 <span data-ttu-id="2b4a8-111">Kendi üzerinde çalışan bir dosya (genellikle uzantısı. exe) bir `Main` yordam içermelidir.</span><span class="sxs-lookup"><span data-stu-id="2b4a8-111">A file that runs on its own (usually with extension .exe) must contain a `Main` procedure.</span></span> <span data-ttu-id="2b4a8-112">Bir kitaplık (örneğin,. dll uzantılı) kendi üzerinde çalışmaz ve bir `Main` yordam gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="2b4a8-112">A library (for example with extension .dll) does not run on its own and does not require a `Main` procedure.</span></span> <span data-ttu-id="2b4a8-113">Oluşturabileceğiniz farklı proje türleri için gereksinimler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="2b4a8-113">The requirements for the different types of projects you can create are as follows:</span></span>

- <span data-ttu-id="2b4a8-114">Konsol uygulamaları kendi üzerinde çalışır ve en az bir yordam sağlamanız gerekir `Main` .</span><span class="sxs-lookup"><span data-stu-id="2b4a8-114">Console applications run on their own, and you must supply at least one `Main` procedure.</span></span>

- <span data-ttu-id="2b4a8-115">Windows Forms uygulamalar kendi kendilerine çalışır.</span><span class="sxs-lookup"><span data-stu-id="2b4a8-115">Windows Forms applications run on their own.</span></span> <span data-ttu-id="2b4a8-116">Ancak, Visual Basic derleyici `Main` Bu uygulama için otomatik olarak bir yordam oluşturur ve bir tane yazmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="2b4a8-116">However, the Visual Basic compiler automatically generates a `Main` procedure in such an application, and you do not need to write one.</span></span>

- <span data-ttu-id="2b4a8-117">Sınıf kitaplıkları bir `Main` yordam gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="2b4a8-117">Class libraries do not require a `Main` procedure.</span></span> <span data-ttu-id="2b4a8-118">Bunlar Windows Denetim kitaplıklarını ve Web denetim kitaplıklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="2b4a8-118">These include Windows Control Libraries and Web Control Libraries.</span></span> <span data-ttu-id="2b4a8-119">Web uygulamaları, sınıf kitaplıkları olarak dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="2b4a8-119">Web applications are deployed as class libraries.</span></span>

## <a name="declaring-the-main-procedure"></a><span data-ttu-id="2b4a8-120">Ana yordamı bildirme</span><span class="sxs-lookup"><span data-stu-id="2b4a8-120">Declaring the Main Procedure</span></span>

 <span data-ttu-id="2b4a8-121">Yordamı belirtmenin dört yolu vardır `Main` .</span><span class="sxs-lookup"><span data-stu-id="2b4a8-121">There are four ways to declare the `Main` procedure.</span></span> <span data-ttu-id="2b4a8-122">Bağımsız değişkenler alabilir veya içermez ve bir değer döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="2b4a8-122">It can take arguments or not, and it can return a value or not.</span></span>

> [!NOTE]
> <span data-ttu-id="2b4a8-123">`Main`Bir sınıfında bildirirseniz `Shared` anahtar sözcüğünü kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2b4a8-123">If you declare `Main` in a class, you must use the `Shared` keyword.</span></span> <span data-ttu-id="2b4a8-124">Bir modülde `Main` olması gerekmez `Shared` .</span><span class="sxs-lookup"><span data-stu-id="2b4a8-124">In a module, `Main` does not need to be `Shared`.</span></span>

- <span data-ttu-id="2b4a8-125">En basit yol, `Sub` bağımsız değişken olmayan veya bir değer döndüren bir yordam bildirmenin bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="2b4a8-125">The simplest way is to declare a `Sub` procedure that does not take arguments or return a value.</span></span>

    ```vb
    Module mainModule
        Sub Main()
            MsgBox("The Main procedure is starting the application.")
            ' Insert call to appropriate starting place in your code.
            MsgBox("The application is terminating.")
        End Sub
    End Module
    ```

- <span data-ttu-id="2b4a8-126">`Main``Integer`, işletim sisteminin programınız için çıkış kodu olarak kullandığı bir değer de döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="2b4a8-126">`Main` can also return an `Integer` value, which the operating system uses as the exit code for your program.</span></span> <span data-ttu-id="2b4a8-127">Diğer programlar Windows ERRORLEVEL değerini inceleyerek bu kodu test edebilir.</span><span class="sxs-lookup"><span data-stu-id="2b4a8-127">Other programs can test this code by examining the Windows ERRORLEVEL value.</span></span> <span data-ttu-id="2b4a8-128">Çıkış kodu döndürmek için, `Main` yordam yerine bir yordam olarak bildirmeniz gerekir `Function` `Sub` .</span><span class="sxs-lookup"><span data-stu-id="2b4a8-128">To return an exit code, you must declare `Main` as a `Function` procedure instead of a `Sub` procedure.</span></span>

    ```vb
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

- <span data-ttu-id="2b4a8-129">`Main` , bir `String` dizi bağımsız değişken olarak da alabilir.</span><span class="sxs-lookup"><span data-stu-id="2b4a8-129">`Main` can also take a `String` array as an argument.</span></span> <span data-ttu-id="2b4a8-130">Dizideki her dize, programınızı çağırmak için kullanılan komut satırı bağımsız değişkenlerinden birini içerir.</span><span class="sxs-lookup"><span data-stu-id="2b4a8-130">Each string in the array contains one of the command-line arguments used to invoke your program.</span></span> <span data-ttu-id="2b4a8-131">Değerlerine bağlı olarak farklı eylemler gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2b4a8-131">You can take different actions depending on their values.</span></span>

    ```vb
    Module mainModule
        Function Main(ByVal cmdArgs() As String) As Integer
            MsgBox("The Main procedure is starting the application.")
            Dim returnValue As Integer = 0
            ' See if there are any arguments.
            If cmdArgs.Length > 0 Then
                For argNum As Integer = 0 To UBound(cmdArgs, 1)
                    ' Insert code to examine cmdArgs(argNum) and take
                    ' appropriate action based on its value.
                Next
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

- <span data-ttu-id="2b4a8-132">`Main`Komut satırı bağımsız değişkenlerini incelemek için, ancak aşağıdaki gibi bir çıkış kodu döndürmezsiniz.</span><span class="sxs-lookup"><span data-stu-id="2b4a8-132">You can declare `Main` to examine the command-line arguments but not return an exit code, as follows.</span></span>

    ```vb
    Module mainModule
        Sub Main(ByVal cmdArgs() As String)
            MsgBox("The Main procedure is starting the application.")
            Dim returnValue As Integer = 0
            ' See if there are any arguments.
            If cmdArgs.Length > 0 Then
                For argNum As Integer = 0 To UBound(cmdArgs, 1)
                    ' Insert code to examine cmdArgs(argNum) and take
                    ' appropriate action based on its value.
                Next
            End If
            ' Insert call to appropriate starting place in your code.
            MsgBox("The application is terminating.")
        End Sub
    End Module
    ```
  
## <a name="see-also"></a><span data-ttu-id="2b4a8-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2b4a8-133">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>
- <xref:System.Array.Length%2A>
- <xref:Microsoft.VisualBasic.Information.UBound%2A>
- [<span data-ttu-id="2b4a8-134">Bir Visual Basic Programının Yapısı</span><span class="sxs-lookup"><span data-stu-id="2b4a8-134">Structure of a Visual Basic Program</span></span>](structure-of-a-visual-basic-program.md)
- [<span data-ttu-id="2b4a8-135">-Main</span><span class="sxs-lookup"><span data-stu-id="2b4a8-135">-main</span></span>](../../reference/command-line-compiler/main.md)
- [<span data-ttu-id="2b4a8-136">Paylaşılan</span><span class="sxs-lookup"><span data-stu-id="2b4a8-136">Shared</span></span>](../../language-reference/modifiers/shared.md)
- [<span data-ttu-id="2b4a8-137">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="2b4a8-137">Sub Statement</span></span>](../../language-reference/statements/sub-statement.md)
- [<span data-ttu-id="2b4a8-138">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="2b4a8-138">Function Statement</span></span>](../../language-reference/statements/function-statement.md)
- [<span data-ttu-id="2b4a8-139">Integer Veri Türü</span><span class="sxs-lookup"><span data-stu-id="2b4a8-139">Integer Data Type</span></span>](../../language-reference/data-types/integer-data-type.md)
- [<span data-ttu-id="2b4a8-140">Dize Veri Türü</span><span class="sxs-lookup"><span data-stu-id="2b4a8-140">String Data Type</span></span>](../../language-reference/data-types/string-data-type.md)
