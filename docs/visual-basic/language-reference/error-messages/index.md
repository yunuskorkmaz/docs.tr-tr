---
title: Hata İletileri (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- errors [Visual Basic]
- error messages
- trappable errors
- errors [Visual Basic], trappable
ms.assetid: f2dda05b-baef-41f5-8bb1-598bd7cf239f
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: de52d95cfbc8135db1dc9434860f02b8992db0b4
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="error-messages-visual-basic"></a><span data-ttu-id="2f44e-102">Hata İletileri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2f44e-102">Error Messages (Visual Basic)</span></span>
<span data-ttu-id="2f44e-103">Yazma, derleme veya Visual Basic uygulama çalıştırdığınızda aşağıdaki tür hataları oluşabilir:</span><span class="sxs-lookup"><span data-stu-id="2f44e-103">When you write, compile, or run a Visual Basic application, the following types of errors can occur:</span></span>  
  
1.  <span data-ttu-id="2f44e-104">Visual Studio'da bir uygulama yazdığınızda ortaya tasarım zamanı hataları.</span><span class="sxs-lookup"><span data-stu-id="2f44e-104">Design-time errors, which occur when you write an application in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="2f44e-105">Visual Studio'da veya bir komut isteminde bir uygulamayı derlediğinizde ortaya derleme zamanı hataları.</span><span class="sxs-lookup"><span data-stu-id="2f44e-105">Compile-time errors, which occur when you compile an application in Visual Studio or at a command prompt.</span></span>  
  
3.  <span data-ttu-id="2f44e-106">Visual Studio'da veya tek başına yürütülebilir bir dosya olarak bir uygulamayı çalıştırdığınızda ortaya çalışma zamanı hataları.</span><span class="sxs-lookup"><span data-stu-id="2f44e-106">Run-time errors, which occur when you run an application in Visual Studio or as a stand-alone executable file.</span></span>  
  
 <span data-ttu-id="2f44e-107">Belirli bir hata ile ilgili sorunları giderme hakkında daha fazla bilgi için bkz: [Visual Basic programcıları için ek kaynaklar](../../../visual-basic/getting-started/additional-resources.md).</span><span class="sxs-lookup"><span data-stu-id="2f44e-107">For information about how to troubleshoot a specific error, see [Additional Resources for Visual Basic Programmers](../../../visual-basic/getting-started/additional-resources.md).</span></span>  
  
## <a name="run-time-errors"></a><span data-ttu-id="2f44e-108">Çalıştırma zamanı hataları</span><span class="sxs-lookup"><span data-stu-id="2f44e-108">Run Time Errors</span></span>  
 <span data-ttu-id="2f44e-109">Visual Basic uygulama sistem yürütülemiyor bir eylem gerçekleştirmek üzere çalışırsa, bir çalışma zamanı hatası oluşur ve Visual Basic oluşturur bir `Exception` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="2f44e-109">If a Visual Basic application tries to perform an action that the system can't execute, a run-time error occurs, and Visual Basic throws an `Exception` object.</span></span> <span data-ttu-id="2f44e-110">Visual Basic, özel hatalar tüm verilerin üretebilir yazın, dahil olmak üzere `Exception` kullanarak nesneleri, `Throw` deyimi.</span><span class="sxs-lookup"><span data-stu-id="2f44e-110">Visual Basic can generate custom errors of any data type, including `Exception` objects, by using the `Throw` statement.</span></span> <span data-ttu-id="2f44e-111">Bir uygulama hatası hata numarası ve yakalanan özel durum iletisi görüntüleyerek belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2f44e-111">An application can identify the error by displaying the error number and message of a caught exception.</span></span> <span data-ttu-id="2f44e-112">Bir hata belirledi değil, uygulama sona erer.</span><span class="sxs-lookup"><span data-stu-id="2f44e-112">If an error isn't caught, the application ends.</span></span>  
  
 <span data-ttu-id="2f44e-113">Kod yakalamak ve çalışma zamanı hataları inceleyin.</span><span class="sxs-lookup"><span data-stu-id="2f44e-113">The code can trap and examine run-time errors.</span></span> <span data-ttu-id="2f44e-114">Hatayı üreten kodu alın, bir `Try` bloğu, eşleşen bir içindeki tüm atılmış hata yakalayabilir `Catch` bloğu.</span><span class="sxs-lookup"><span data-stu-id="2f44e-114">If you enclose the code that produces the error in a `Try` block, you can catch any thrown error within a matching `Catch` block.</span></span> <span data-ttu-id="2f44e-115">Çalışma zamanında hataları yakalar ve bunları kodunuzda yanıt hakkında daha fazla bilgi için bkz: [deneyin... Catch... Finally ifadesi](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="2f44e-115">For information about how to trap errors at run time and respond to them in your code, see [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
## <a name="compile-time-errors"></a><span data-ttu-id="2f44e-116">Derleme zamanı hataları</span><span class="sxs-lookup"><span data-stu-id="2f44e-116">Compile Time Errors</span></span>  
 <span data-ttu-id="2f44e-117">Visual Basic derleyici kodundaki bir sorunla karşılaşırsa, derleme zamanı hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="2f44e-117">If the Visual Basic compiler encounters a problem in the code, a compile-time error occurs.</span></span> <span data-ttu-id="2f44e-118">Kod Düzenleyicisi'nde dalgalı bir çizgi kod satırını altında göründüğünden hangi satırlık bir kod hataya kolayca tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2f44e-118">In the Code Editor, you can easily identify which line of code caused the error because a wavy line appears under that line of code.</span></span> <span data-ttu-id="2f44e-119">Dalgalı alt çizgi veya açık ya da işaret hata iletisi görüntülenir **hata listesi**, diğer iletileri de gösterir.</span><span class="sxs-lookup"><span data-stu-id="2f44e-119">The error message appears if you either point to the wavy underline or open the **Error List**, which also shows other messages.</span></span>  
  
 <span data-ttu-id="2f44e-120">Dalgalı alt çizgi bir tanımlayıcısı varsa ve kısa çizgi en sağdaki karakterin altında görünür, sınıf, oluşturucusu, yöntemi, özelliği, alan veya numaralandırma için bir saplama oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="2f44e-120">If an identifier has a wavy underline and a short underline appears under the rightmost character, you can generate a stub for the class, constructor, method, property, field or enum.</span></span> <span data-ttu-id="2f44e-121">Daha fazla bilgi için bkz: [kullanımından Oluştur](/visualstudio/ide/visual-csharp-intellisense#generate-from-usage).</span><span class="sxs-lookup"><span data-stu-id="2f44e-121">For more information, see [Generate From Usage](/visualstudio/ide/visual-csharp-intellisense#generate-from-usage).</span></span>
  
 <span data-ttu-id="2f44e-122">Visual Basic derleyici gelen uyarıları çözümleme göre daha hızlı çalışır ve daha az hataları olan kod yazmayı mümkün olabilir.</span><span class="sxs-lookup"><span data-stu-id="2f44e-122">By resolving warnings from the Visual Basic compiler, you might be able to write code that runs faster and has fewer bugs.</span></span> <span data-ttu-id="2f44e-123">Bu uyarılar uygulamayı çalıştırdığınızda, hatalara neden olabilecek kodunu belirleyin.</span><span class="sxs-lookup"><span data-stu-id="2f44e-123">These warnings identify code that may cause errors when the application is run.</span></span> <span data-ttu-id="2f44e-124">Örneğin, derleyici, bir atanmamış nesne değişkeni üyesi çağrılacak çalışırsanız dönüş değeri ayarlamadan bir işlevinden dönmek, ya yürütme konusunda sizi uyarır bir `Try` bloğu özel durumları yakalamak için mantığı hatalı.</span><span class="sxs-lookup"><span data-stu-id="2f44e-124">For example, the compiler warns you if you try to invoke a member of an unassigned object variable, return from a function without setting the return value, or execute a `Try` block with errors in the logic to catch exceptions.</span></span> <span data-ttu-id="2f44e-125">Açma ve kapatma, devre dışı bırakma dahil olmak üzere uyarılar hakkında daha fazla bilgi için bkz: [yapılandırma uyarılarını Visual Basic'te](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="2f44e-125">For more information about warnings, including how to turn them on and off, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>
