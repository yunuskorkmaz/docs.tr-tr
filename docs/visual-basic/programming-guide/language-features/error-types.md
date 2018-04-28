---
title: Hata Türleri (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- exceptions, types
- errors [Visual Basic], types
- errors [Visual Basic], logic
- errors [Visual Basic], syntax
- logic errors [Visual Basic], Visual Basic
- run-time errors [Visual Basic], types of errors
- syntax errors [Visual Basic], Visual Basic
ms.assetid: 3048aabf-8c97-4e13-9150-853769cb5f6f
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2b3cf1307f54a5c902bf8e6379c8760c735a45e4
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="error-types-visual-basic"></a><span data-ttu-id="19dbe-102">Hata Türleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="19dbe-102">Error Types (Visual Basic)</span></span>
<span data-ttu-id="19dbe-103">Visual Basic'te hataları (olarak da bilinir *özel durumları*) üç kategoriden ayrılır: sözdizimi hataları, çalışma zamanı hataları ve mantık hataları.</span><span class="sxs-lookup"><span data-stu-id="19dbe-103">In Visual Basic, errors (also called *exceptions*) fall into one of three categories: syntax errors, run-time errors, and logic errors.</span></span>  
  
## <a name="syntax-errors"></a><span data-ttu-id="19dbe-104">Sözdizimi hataları</span><span class="sxs-lookup"><span data-stu-id="19dbe-104">Syntax Errors</span></span>  
 <span data-ttu-id="19dbe-105">*Sözdizimi hataları* kodu yazdığınız sırada görüntülenen olanlardır.</span><span class="sxs-lookup"><span data-stu-id="19dbe-105">*Syntax errors* are those that appear while you write code.</span></span> <span data-ttu-id="19dbe-106">Visual Basic içinde yazarken kodunuzu denetler **Kod düzenleyicisinde** penceresi ve bir sözcük yazım hatası veya hatalı bir dil öğesi kullanarak gibi bir hata yaparsanız sizi uyarır.</span><span class="sxs-lookup"><span data-stu-id="19dbe-106">Visual Basic checks your code as you type it in the **Code Editor** window and alerts you if you make a mistake, such as misspelling a word or using a language element improperly.</span></span> <span data-ttu-id="19dbe-107">Sözdizimi hataları hataları en yaygın türüdür.</span><span class="sxs-lookup"><span data-stu-id="19dbe-107">Syntax errors are the most common type of errors.</span></span> <span data-ttu-id="19dbe-108">Oluşma hemen bunları kodlama ortamında kolayca düzeltebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="19dbe-108">You can fix them easily in the coding environment as soon as they occur.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="19dbe-109">`Option Explicit` Açıklamadır sözdizimi hatalarını önleme bir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="19dbe-109">The `Option Explicit` statement is one means of avoiding syntax errors.</span></span> <span data-ttu-id="19dbe-110">Önceden, uygulamada kullanılacak tüm değişkenleri bildirmek zorlar.</span><span class="sxs-lookup"><span data-stu-id="19dbe-110">It forces you to declare, in advance, all the variables to be used in the application.</span></span> <span data-ttu-id="19dbe-111">Bu nedenle, bu değişkenleri kodda kullanıldığında, herhangi bir tipografik hata hemen yakalanan ve düzeltilebilir.</span><span class="sxs-lookup"><span data-stu-id="19dbe-111">Therefore, when those variables are used in the code, any typographic errors are caught immediately and can be fixed.</span></span>  
  
## <a name="run-time-errors"></a><span data-ttu-id="19dbe-112">Çalışma zamanı hataları</span><span class="sxs-lookup"><span data-stu-id="19dbe-112">Run-Time Errors</span></span>  
 <span data-ttu-id="19dbe-113">*Çalışma zamanı hataları* yalnızca derlemek ve kodunuzu çalıştırdıktan sonra görüntülenen olanlardır.</span><span class="sxs-lookup"><span data-stu-id="19dbe-113">*Run-time errors* are those that appear only after you compile and run your code.</span></span> <span data-ttu-id="19dbe-114">Bunlar sözdizimi hatası var, ancak bu yürütülemeyecek, doğru olarak görünebilir kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="19dbe-114">These involve code that may appear to be correct in that it has no syntax errors, but that will not execute.</span></span> <span data-ttu-id="19dbe-115">Örneğin, bir dosyayı açmaya kod satırını doğru yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="19dbe-115">For example, you might correctly write a line of code to open a file.</span></span> <span data-ttu-id="19dbe-116">Ancak uygulama dosyası bozuk olduğunda getirilemiyor `Open` işlevi ve onu durdurur çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="19dbe-116">But if the file is corrupted, the application cannot carry out the `Open` function, and it stops running.</span></span> <span data-ttu-id="19dbe-117">Hatalı kodu yeniden yazma işlemi ve daha sonra yeniden derlenmesi ve onu yeniden çalıştırma tarafından çoğu çalışma zamanı hataları düzeltebilir.</span><span class="sxs-lookup"><span data-stu-id="19dbe-117">You can fix most run-time errors by rewriting the faulty code, and then recompiling and rerunning it.</span></span>  
  
## <a name="logic-errors"></a><span data-ttu-id="19dbe-118">Mantık hataları</span><span class="sxs-lookup"><span data-stu-id="19dbe-118">Logic Errors</span></span>  
 <span data-ttu-id="19dbe-119">*Mantık hataları* uygulama kullanımda olduğunda görüntülenen olanlardır.</span><span class="sxs-lookup"><span data-stu-id="19dbe-119">*Logic errors* are those that appear once the application is in use.</span></span> <span data-ttu-id="19dbe-120">Bunların çoğu genellikle istenmeyen veya beklenmeyen sonuçlar kullanıcı eylemlerine yanıt olur.</span><span class="sxs-lookup"><span data-stu-id="19dbe-120">They are most often unwanted or unexpected results in response to user actions.</span></span> <span data-ttu-id="19dbe-121">Örneğin, yanlış yazılan bir anahtar veya diğer dış etkisi, uygulamanızın içinde beklenen parametreler, çalışmayı durdurmasına neden olabilir veya tamamen.</span><span class="sxs-lookup"><span data-stu-id="19dbe-121">For example, a mistyped key or other outside influence might cause your application to stop working within expected parameters, or altogether.</span></span> <span data-ttu-id="19dbe-122">Mantık hataları genellikle, her zaman burada kaynaklanan Temizle olmadığından çözmenin en zor türüdür.</span><span class="sxs-lookup"><span data-stu-id="19dbe-122">Logic errors are generally the hardest type to fix, since it is not always clear where they originate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19dbe-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="19dbe-123">See Also</span></span>  
 [<span data-ttu-id="19dbe-124">Try...Catch...Finally Deyimi</span><span class="sxs-lookup"><span data-stu-id="19dbe-124">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [<span data-ttu-id="19dbe-125">Hata ayıklayıcı temel bilgileri</span><span class="sxs-lookup"><span data-stu-id="19dbe-125">Debugger Basics</span></span>](/visualstudio/debugger/debugger-basics)
