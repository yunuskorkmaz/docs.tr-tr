---
title: Hata Türleri (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions, types
- errors [Visual Basic], types
- errors [Visual Basic], logic
- errors [Visual Basic], syntax
- logic errors [Visual Basic], Visual Basic
- run-time errors [Visual Basic], types of errors
- syntax errors [Visual Basic], Visual Basic
ms.assetid: 3048aabf-8c97-4e13-9150-853769cb5f6f
ms.openlocfilehash: 07db963ac3cf9d1c0d17c420480189d362cdaf2c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58831572"
---
# <a name="error-types-visual-basic"></a><span data-ttu-id="2c82c-102">Hata Türleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2c82c-102">Error Types (Visual Basic)</span></span>
<span data-ttu-id="2c82c-103">Visual Basic'te, hataları (olarak da adlandırılan *özel durumları*) üç kategoriden birine girer: söz dizimi hatalarını, çalışma zamanı hataları ve mantık hataları.</span><span class="sxs-lookup"><span data-stu-id="2c82c-103">In Visual Basic, errors (also called *exceptions*) fall into one of three categories: syntax errors, run-time errors, and logic errors.</span></span>  
  
## <a name="syntax-errors"></a><span data-ttu-id="2c82c-104">Sözdizimi hataları</span><span class="sxs-lookup"><span data-stu-id="2c82c-104">Syntax Errors</span></span>  
 <span data-ttu-id="2c82c-105">*Söz dizimi hataları* kodu yazdığınız sırada görüntülenen olanlardır.</span><span class="sxs-lookup"><span data-stu-id="2c82c-105">*Syntax errors* are those that appear while you write code.</span></span> <span data-ttu-id="2c82c-106">Visual Basic içinde yazdığınız sırada kodunuzu denetler **Kod Düzenleyicisi** penceresi ve gibi bir sözcük yazım hatası veya yanlış bir dil öğesini kullanarak bağlı olarak, bir hata yaparsanız sizi uyarır.</span><span class="sxs-lookup"><span data-stu-id="2c82c-106">Visual Basic checks your code as you type it in the **Code Editor** window and alerts you if you make a mistake, such as misspelling a word or using a language element improperly.</span></span> <span data-ttu-id="2c82c-107">Söz dizimi hataları en yaygın türü hatalardır.</span><span class="sxs-lookup"><span data-stu-id="2c82c-107">Syntax errors are the most common type of errors.</span></span> <span data-ttu-id="2c82c-108">Ortaya hemen sonra bunları kodlama ortamında kolayca giderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2c82c-108">You can fix them easily in the coding environment as soon as they occur.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2c82c-109">`Option Explicit` Deyimi, söz dizimi hatalarını önleme bir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="2c82c-109">The `Option Explicit` statement is one means of avoiding syntax errors.</span></span> <span data-ttu-id="2c82c-110">Önceden, uygulamada kullanılan tüm değişkenleri bildirmeye zorlar.</span><span class="sxs-lookup"><span data-stu-id="2c82c-110">It forces you to declare, in advance, all the variables to be used in the application.</span></span> <span data-ttu-id="2c82c-111">Bu nedenle, kodda değişkenlere kullanıldığında tipografik hataları hemen yakalanır ve düzeltilebilir.</span><span class="sxs-lookup"><span data-stu-id="2c82c-111">Therefore, when those variables are used in the code, any typographic errors are caught immediately and can be fixed.</span></span>  
  
## <a name="run-time-errors"></a><span data-ttu-id="2c82c-112">Çalışma zamanı hataları</span><span class="sxs-lookup"><span data-stu-id="2c82c-112">Run-Time Errors</span></span>  
 <span data-ttu-id="2c82c-113">*Çalışma zamanı hataları* yalnızca derleme ve kodunuzu çalıştırdıktan sonra görüntülenen olanlardır.</span><span class="sxs-lookup"><span data-stu-id="2c82c-113">*Run-time errors* are those that appear only after you compile and run your code.</span></span> <span data-ttu-id="2c82c-114">Bu, söz dizimi hatası var, ancak bu yürütülemeyecek, doğru olarak görünebilir kod içerir.</span><span class="sxs-lookup"><span data-stu-id="2c82c-114">These involve code that may appear to be correct in that it has no syntax errors, but that will not execute.</span></span> <span data-ttu-id="2c82c-115">Örneğin, bir dosyayı açmak için kod satırı doğru şekilde yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2c82c-115">For example, you might correctly write a line of code to open a file.</span></span> <span data-ttu-id="2c82c-116">Ancak uygulama dosya bozuk, çalıştırılamaz `Open` işlevi ve çalışan durdurur.</span><span class="sxs-lookup"><span data-stu-id="2c82c-116">But if the file is corrupted, the application cannot carry out the `Open` function, and it stops running.</span></span> <span data-ttu-id="2c82c-117">Hatalı kodu yeniden yazma yeniden derlemeden ve ardından onu yeniden çalıştırma tarafından en fazla çalışma zamanı hataları düzeltebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2c82c-117">You can fix most run-time errors by rewriting the faulty code, and then recompiling and rerunning it.</span></span>  
  
## <a name="logic-errors"></a><span data-ttu-id="2c82c-118">Mantık hataları</span><span class="sxs-lookup"><span data-stu-id="2c82c-118">Logic Errors</span></span>  
 <span data-ttu-id="2c82c-119">*Mantık hataları* uygulama kullanımda olduğunda görüntülenen olanlardır.</span><span class="sxs-lookup"><span data-stu-id="2c82c-119">*Logic errors* are those that appear once the application is in use.</span></span> <span data-ttu-id="2c82c-120">Yanıt olarak kullanıcı eylemlerini çoğu genellikle istenmeyen veya beklenmeyen sonuçlar değildirler.</span><span class="sxs-lookup"><span data-stu-id="2c82c-120">They are most often unwanted or unexpected results in response to user actions.</span></span> <span data-ttu-id="2c82c-121">Örneğin, yanlış yazılan bir anahtar veya diğer dış etkisi, uygulamanızın beklenen parametrelerin içinde çalışmayı durdurmasına neden olabilir veya tamamen.</span><span class="sxs-lookup"><span data-stu-id="2c82c-121">For example, a mistyped key or other outside influence might cause your application to stop working within expected parameters, or altogether.</span></span> <span data-ttu-id="2c82c-122">Mantık hataları genellikle, her zaman burada kaynaklanan NET olmadığından, düzeltmek için uygulamalarınızdaki türüdür.</span><span class="sxs-lookup"><span data-stu-id="2c82c-122">Logic errors are generally the hardest type to fix, since it is not always clear where they originate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c82c-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2c82c-123">See also</span></span>

- [<span data-ttu-id="2c82c-124">Try...Catch...Finally Deyimi</span><span class="sxs-lookup"><span data-stu-id="2c82c-124">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="2c82c-125">Hata Ayıklayıcısı Temel Bilgileri</span><span class="sxs-lookup"><span data-stu-id="2c82c-125">Debugger Basics</span></span>](/visualstudio/debugger/debugger-basics)
