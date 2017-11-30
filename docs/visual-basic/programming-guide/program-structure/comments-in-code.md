---
title: "Kod Açıklamaları (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Uncomment button
- REM statement [Visual Basic]
- comments [Visual Basic], in code
- comments [Visual Basic], Visual Basic code
- Comment button
- buttons [Visual Basic], Uncomment
- buttons [Visual Basic], Comment
- code comments [Visual Basic], Visual Basic
- Visual Basic code, comments
- comments
- code comments
ms.assetid: 90136fba-22eb-49f9-ba81-63db629b4a47
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0cf1aa755c479c73c64951f80ab0b76985507da6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="comments-in-code-visual-basic"></a><span data-ttu-id="6f65b-102">Kod Açıklamaları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6f65b-102">Comments in Code (Visual Basic)</span></span>
<span data-ttu-id="6f65b-103">Kod örnekleri okurken Yorum simgesinin sık karşılaşırsanız (`'`).</span><span class="sxs-lookup"><span data-stu-id="6f65b-103">As you read the code examples, you often encounter the comment symbol (`'`).</span></span> <span data-ttu-id="6f65b-104">Bu simgenin söyler [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] , aşağıdaki metni yoksay derleyici veya *açıklama*.</span><span class="sxs-lookup"><span data-stu-id="6f65b-104">This symbol tells the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler to ignore the text following it, or the *comment*.</span></span> <span data-ttu-id="6f65b-105">Açıklamalar, okuyan kişinin yararına olması için koda eklenmiş kısa ve açıklayıcı notlardır.</span><span class="sxs-lookup"><span data-stu-id="6f65b-105">Comments are brief explanatory notes added to code for the benefit of those reading it.</span></span>  
  
 <span data-ttu-id="6f65b-106">Tüm yordamlara, ilgili yordamın işlevsel özelliklerini (neler yaptığını) açıklayan kısa bir açıklama ile başlanması iyi bir programlama uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="6f65b-106">It is good programming practice to begin all procedures with a brief comment describing the functional characteristics of the procedure (what it does).</span></span> <span data-ttu-id="6f65b-107">Bu hem sizin yararınıza, hem de kodu inceleyen herhangi bir kişinin yararına olur.</span><span class="sxs-lookup"><span data-stu-id="6f65b-107">This is for your own benefit and the benefit of anyone else who examines the code.</span></span> <span data-ttu-id="6f65b-108">Gerçekleştirme ayrıntılarını (yordamın bunu nasıl yaptığı), işlevsel özellikleri anlatan açıklamalardan ayırmalısınız.</span><span class="sxs-lookup"><span data-stu-id="6f65b-108">You should separate the implementation details (how the procedure does it) from comments that describe the functional characteristics.</span></span> <span data-ttu-id="6f65b-109">Açıklamaya gerçekleştirme ayrıntılarını eklediğinizde, işlevi güncelleştirirken bunları da güncelleştirmeyi unutmayın.</span><span class="sxs-lookup"><span data-stu-id="6f65b-109">When you include implementation details in the description, remember to update them when you update the function.</span></span>  
  
 <span data-ttu-id="6f65b-110">Açıklamalar aynı satırdaki bir deyimi izleyebilir veya tüm bir satırı kaplayabilir.</span><span class="sxs-lookup"><span data-stu-id="6f65b-110">Comments can follow a statement on the same line, or occupy an entire line.</span></span> <span data-ttu-id="6f65b-111">Her ikisi de aşağıdaki kodda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6f65b-111">Both are illustrated in the following code.</span></span>  
  
 [!code-vb[VbVbcnConventions#16](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/comments-in-code_1.vb)]  
  
 <span data-ttu-id="6f65b-112">Açıklamanız için birden fazla satır gerekiyorsa, aşağıdaki örnekte gösterildiği gibi her satırda açıklama sembolünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="6f65b-112">If your comment requires more than one line, use the comment symbol on each line, as the following example illustrates.</span></span>  
  
 [!code-vb[VbVbcnConventions#17](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/comments-in-code_2.vb)]  
  
## <a name="commenting-guidelines"></a><span data-ttu-id="6f65b-113">Açıklamalara İlişkin Kurallar</span><span class="sxs-lookup"><span data-stu-id="6f65b-113">Commenting Guidelines</span></span>  
 <span data-ttu-id="6f65b-114">Aşağıdaki tabloda, kodun bir bölümünden önce hangi tür açıklamaların gelebileceğine dair genel kurallar verilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6f65b-114">The following table provides general guidelines for what types of comments can precede a section of code.</span></span> <span data-ttu-id="6f65b-115">Bunlar önerilerdir; [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] açıklamaları eklemek için kuralları uygulamaz.</span><span class="sxs-lookup"><span data-stu-id="6f65b-115">These are suggestions; [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] does not enforce rules for adding comments.</span></span> <span data-ttu-id="6f65b-116">Hem sizin, hem de kodu okuyan herhangi bir kişinin işine en çok yarayacak şeyleri yazın.</span><span class="sxs-lookup"><span data-stu-id="6f65b-116">Write what works best, both for you and for anyone else who reads your code.</span></span>  
  
|||  
|---|---|  
|<span data-ttu-id="6f65b-117">Açıklama türü</span><span class="sxs-lookup"><span data-stu-id="6f65b-117">Comment type</span></span>|<span data-ttu-id="6f65b-118">Açıklama tanımı</span><span class="sxs-lookup"><span data-stu-id="6f65b-118">Comment description</span></span>|  
|<span data-ttu-id="6f65b-119">Amaç</span><span class="sxs-lookup"><span data-stu-id="6f65b-119">Purpose</span></span>|<span data-ttu-id="6f65b-120">Yordamın ne yaptığını açıklar (bunu nasıl yaptığını değil)</span><span class="sxs-lookup"><span data-stu-id="6f65b-120">Describes what the procedure does (not how it does it)</span></span>|  
|<span data-ttu-id="6f65b-121">Varsayımlar</span><span class="sxs-lookup"><span data-stu-id="6f65b-121">Assumptions</span></span>|<span data-ttu-id="6f65b-122">Her bir dış bağımsız değişkeni, denetimi, dosya açmayı veya yordamın erişim sağladığı diğer öğeyi listeler</span><span class="sxs-lookup"><span data-stu-id="6f65b-122">Lists each external variable, control, open file, or other element accessed by the procedure</span></span>|  
|<span data-ttu-id="6f65b-123">Etkiler</span><span class="sxs-lookup"><span data-stu-id="6f65b-123">Effects</span></span>|<span data-ttu-id="6f65b-124">Her bir etkilenen dış bağımsız değişkeni, denetimi veya dosyayı ve sahip olduğu etkiyi (bu etki bariz değilse) listeler</span><span class="sxs-lookup"><span data-stu-id="6f65b-124">Lists each affected external variable, control, or file, and the effect it has (only if it is not obvious)</span></span>|  
|<span data-ttu-id="6f65b-125">Girişler</span><span class="sxs-lookup"><span data-stu-id="6f65b-125">Inputs</span></span>|<span data-ttu-id="6f65b-126">Bağımsız değişkenin amacını belirtir</span><span class="sxs-lookup"><span data-stu-id="6f65b-126">Specifies the purpose of the argument</span></span>|  
|<span data-ttu-id="6f65b-127">Döndürür</span><span class="sxs-lookup"><span data-stu-id="6f65b-127">Returns</span></span>|<span data-ttu-id="6f65b-128">Yordamın döndürdüğü değerleri açıklar</span><span class="sxs-lookup"><span data-stu-id="6f65b-128">Explains the values returned by the procedure</span></span>|  
  
 <span data-ttu-id="6f65b-129">Aşağıdaki hususları unutmayın:</span><span class="sxs-lookup"><span data-stu-id="6f65b-129">Remember the following points:</span></span>  
  
-   <span data-ttu-id="6f65b-130">Her önemli değişken bildiriminin önünde, bildirilen değişkenin kullanımını anlatan bir açıklama bulunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6f65b-130">Every important variable declaration should be preceded by a comment describing the use of the variable being declared.</span></span>  
  
-   <span data-ttu-id="6f65b-131">Değişkenler, denetimler ve yordamlar, yalnızca karmaşık gerçekleştirme ayrıntıları için açıklamaya gerek duyulacak şekilde yeterince açık adlandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6f65b-131">Variables, controls, and procedures should be named clearly enough that commenting is needed only for complex implementation details.</span></span>  
  
-   <span data-ttu-id="6f65b-132">Açıklamalar, aynı satırdaki bir satır devamlılığı dizisinden sonra gelemez.</span><span class="sxs-lookup"><span data-stu-id="6f65b-132">Comments cannot follow a line-continuation sequence on the same line.</span></span>  
  
 <span data-ttu-id="6f65b-133">Ekleyebilir veya bir veya daha fazla kod satırı bulunmaktadır ve seçerek bir kod bloğunun açıklama simgelerini kaldırmak **açıklama** (![VisualBasicWinAppCodeEditorCommentButton](../../../visual-basic/programming-guide/program-structure/media/vacommentbutton.gif "vaCommentButton ")) ve **açıklamasını kaldırın** (![VisualStudioWinAppProjectUncommentButton](../../../visual-basic/programming-guide/program-structure/media/vauncommentbutton.gif "vaUncommentButton")) üzerinde düğmeleri **Düzenle**  araç.</span><span class="sxs-lookup"><span data-stu-id="6f65b-133">You can add or remove comment symbols for a block of code by selecting one or more lines of code and choosing the **Comment** (![VisualBasicWinAppCodeEditorCommentButton](../../../visual-basic/programming-guide/program-structure/media/vacommentbutton.gif "vaCommentButton")) and **Uncomment** (![VisualStudioWinAppProjectUncommentButton](../../../visual-basic/programming-guide/program-structure/media/vauncommentbutton.gif "vaUncommentButton")) buttons on the **Edit** toolbar.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6f65b-134">Metinle koyarak kodunuzu yorumlar ekleyebilirsiniz `REM` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="6f65b-134">You can also add comments to your code by preceding the text with the `REM` keyword.</span></span> <span data-ttu-id="6f65b-135">Ancak, `'` simgesi ve **açıklama**/**açıklamasını kaldırın** düğmelerini kullanın ve daha az alan ve bellek gerektirir daha kolay olur.</span><span class="sxs-lookup"><span data-stu-id="6f65b-135">However, the `'` symbol and the **Comment**/**Uncomment** buttons are easier to use and require less space and memory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f65b-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6f65b-136">See Also</span></span>  
 [<span data-ttu-id="6f65b-137">XML açıklamaları ile kodunuzu belgeleme</span><span class="sxs-lookup"><span data-stu-id="6f65b-137">Documenting Your Code With XML Comments</span></span>](http://msdn.microsoft.com/magazine/dd722812.aspx)  
 [<span data-ttu-id="6f65b-138">Nasıl yapılır: XML belgesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="6f65b-138">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)  
 [<span data-ttu-id="6f65b-139">XML açıklama etiketleri</span><span class="sxs-lookup"><span data-stu-id="6f65b-139">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)  
 [<span data-ttu-id="6f65b-140">Program yapısı ve kod kuralları</span><span class="sxs-lookup"><span data-stu-id="6f65b-140">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [<span data-ttu-id="6f65b-141">REM deyimi</span><span class="sxs-lookup"><span data-stu-id="6f65b-141">REM Statement</span></span>](../../../visual-basic/language-reference/statements/rem-statement.md)
