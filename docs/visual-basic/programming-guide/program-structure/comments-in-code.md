---
title: Kod Açıklamaları
ms.date: 07/20/2015
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
ms.openlocfilehash: 189810393db42c54cb8a0f97b22b3d1514d9a7c4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346167"
---
# <a name="comments-in-code-visual-basic"></a><span data-ttu-id="83790-102">Kod Açıklamaları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="83790-102">Comments in Code (Visual Basic)</span></span>
<span data-ttu-id="83790-103">Kod örneklerini okurken genellikle açıklama simgesiyle (`'`) karşılaşırsınız.</span><span class="sxs-lookup"><span data-stu-id="83790-103">As you read the code examples, you often encounter the comment symbol (`'`).</span></span> <span data-ttu-id="83790-104">Bu simge, Visual Basic derleyicisine onu izleyen metni veya *yorumu*yoksaymasını söyler.</span><span class="sxs-lookup"><span data-stu-id="83790-104">This symbol tells the Visual Basic compiler to ignore the text following it, or the *comment*.</span></span> <span data-ttu-id="83790-105">Açıklamalar, okuyan kişinin yararına olması için koda eklenmiş kısa ve açıklayıcı notlardır.</span><span class="sxs-lookup"><span data-stu-id="83790-105">Comments are brief explanatory notes added to code for the benefit of those reading it.</span></span>  
  
 <span data-ttu-id="83790-106">Tüm yordamlara, ilgili yordamın işlevsel özelliklerini (neler yaptığını) açıklayan kısa bir açıklama ile başlanması iyi bir programlama uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="83790-106">It is good programming practice to begin all procedures with a brief comment describing the functional characteristics of the procedure (what it does).</span></span> <span data-ttu-id="83790-107">Bu hem sizin yararınıza, hem de kodu inceleyen herhangi bir kişinin yararına olur.</span><span class="sxs-lookup"><span data-stu-id="83790-107">This is for your own benefit and the benefit of anyone else who examines the code.</span></span> <span data-ttu-id="83790-108">Gerçekleştirme ayrıntılarını (yordamın bunu nasıl yaptığı), işlevsel özellikleri anlatan açıklamalardan ayırmalısınız.</span><span class="sxs-lookup"><span data-stu-id="83790-108">You should separate the implementation details (how the procedure does it) from comments that describe the functional characteristics.</span></span> <span data-ttu-id="83790-109">Açıklamaya gerçekleştirme ayrıntılarını eklediğinizde, işlevi güncelleştirirken bunları da güncelleştirmeyi unutmayın.</span><span class="sxs-lookup"><span data-stu-id="83790-109">When you include implementation details in the description, remember to update them when you update the function.</span></span>  
  
 <span data-ttu-id="83790-110">Açıklamalar aynı satırdaki bir deyimi izleyebilir veya tüm bir satırı kaplayabilir.</span><span class="sxs-lookup"><span data-stu-id="83790-110">Comments can follow a statement on the same line, or occupy an entire line.</span></span> <span data-ttu-id="83790-111">Her ikisi de aşağıdaki kodda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="83790-111">Both are illustrated in the following code.</span></span>  
  
 [!code-vb[VbVbcnConventions#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#16)]  
  
 <span data-ttu-id="83790-112">Açıklamanız için birden fazla satır gerekiyorsa, aşağıdaki örnekte gösterildiği gibi her satırda açıklama sembolünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="83790-112">If your comment requires more than one line, use the comment symbol on each line, as the following example illustrates.</span></span>  
  
 [!code-vb[VbVbcnConventions#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#17)]  
  
## <a name="commenting-guidelines"></a><span data-ttu-id="83790-113">Açıklamalara İlişkin Kurallar</span><span class="sxs-lookup"><span data-stu-id="83790-113">Commenting Guidelines</span></span>  
 <span data-ttu-id="83790-114">Aşağıdaki tabloda, kodun bir bölümünden önce hangi tür açıklamaların gelebileceğine dair genel kurallar verilmektedir.</span><span class="sxs-lookup"><span data-stu-id="83790-114">The following table provides general guidelines for what types of comments can precede a section of code.</span></span> <span data-ttu-id="83790-115">Bunlar önerilerdir; Visual Basic, yorum eklemek için kuralları zorlamaz.</span><span class="sxs-lookup"><span data-stu-id="83790-115">These are suggestions; Visual Basic does not enforce rules for adding comments.</span></span> <span data-ttu-id="83790-116">Hem sizin, hem de kodu okuyan herhangi bir kişinin işine en çok yarayacak şeyleri yazın.</span><span class="sxs-lookup"><span data-stu-id="83790-116">Write what works best, both for you and for anyone else who reads your code.</span></span>  
  
|||  
|---|---|  
|<span data-ttu-id="83790-117">Açıklama türü</span><span class="sxs-lookup"><span data-stu-id="83790-117">Comment type</span></span>|<span data-ttu-id="83790-118">Açıklama tanımı</span><span class="sxs-lookup"><span data-stu-id="83790-118">Comment description</span></span>|  
|<span data-ttu-id="83790-119">Amaç</span><span class="sxs-lookup"><span data-stu-id="83790-119">Purpose</span></span>|<span data-ttu-id="83790-120">Yordamın ne yaptığını açıklar (bunu nasıl yaptığını değil)</span><span class="sxs-lookup"><span data-stu-id="83790-120">Describes what the procedure does (not how it does it)</span></span>|  
|<span data-ttu-id="83790-121">Varsayımlar</span><span class="sxs-lookup"><span data-stu-id="83790-121">Assumptions</span></span>|<span data-ttu-id="83790-122">Her bir dış bağımsız değişkeni, denetimi, dosya açmayı veya yordamın erişim sağladığı diğer öğeyi listeler</span><span class="sxs-lookup"><span data-stu-id="83790-122">Lists each external variable, control, open file, or other element accessed by the procedure</span></span>|  
|<span data-ttu-id="83790-123">Etkiler</span><span class="sxs-lookup"><span data-stu-id="83790-123">Effects</span></span>|<span data-ttu-id="83790-124">Her bir etkilenen dış bağımsız değişkeni, denetimi veya dosyayı ve sahip olduğu etkiyi (bu etki bariz değilse) listeler</span><span class="sxs-lookup"><span data-stu-id="83790-124">Lists each affected external variable, control, or file, and the effect it has (only if it is not obvious)</span></span>|  
|<span data-ttu-id="83790-125">Girdiler</span><span class="sxs-lookup"><span data-stu-id="83790-125">Inputs</span></span>|<span data-ttu-id="83790-126">Bağımsız değişkenin amacını belirtir</span><span class="sxs-lookup"><span data-stu-id="83790-126">Specifies the purpose of the argument</span></span>|  
|<span data-ttu-id="83790-127">Döndürür</span><span class="sxs-lookup"><span data-stu-id="83790-127">Returns</span></span>|<span data-ttu-id="83790-128">Yordamın döndürdüğü değerleri açıklar</span><span class="sxs-lookup"><span data-stu-id="83790-128">Explains the values returned by the procedure</span></span>|  
  
 <span data-ttu-id="83790-129">Aşağıdaki hususları unutmayın:</span><span class="sxs-lookup"><span data-stu-id="83790-129">Remember the following points:</span></span>  
  
- <span data-ttu-id="83790-130">Her önemli değişken bildiriminin önünde, bildirilen değişkenin kullanımını anlatan bir açıklama bulunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="83790-130">Every important variable declaration should be preceded by a comment describing the use of the variable being declared.</span></span>  
  
- <span data-ttu-id="83790-131">Değişkenler, denetimler ve yordamlar, yalnızca karmaşık gerçekleştirme ayrıntıları için açıklamaya gerek duyulacak şekilde yeterince açık adlandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="83790-131">Variables, controls, and procedures should be named clearly enough that commenting is needed only for complex implementation details.</span></span>  
  
- <span data-ttu-id="83790-132">Açıklamalar, aynı satırdaki bir satır devamlılığı dizisinden sonra gelemez.</span><span class="sxs-lookup"><span data-stu-id="83790-132">Comments cannot follow a line-continuation sequence on the same line.</span></span>  
  
 <span data-ttu-id="83790-133">Bir ya da daha fazla kod satırı seçip açıklamayı seçerek (Visual Studio 'da Visual Basic Yorum düğmesini![ve **Açıklama** ' ya **tıklayarak (visual** studio.](./media/comments-in-code/visual-basic-comment-button.gif))![ve **Düzen** araç çubuğundaki Visual Basic açıklamayı kaldır.](./media/comments-in-code/visual-basic-uncomment-button.gif)) düğmelerine tıklayarak bir kod bloğu için açıklama sembolleri ekleyebilir veya kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="83790-133">You can add or remove comment symbols for a block of code by selecting one or more lines of code and choosing the **Comment** (![The Visual Basic Comment button in Visual Studio.](./media/comments-in-code/visual-basic-comment-button.gif)) and **Uncomment** (![The Visual Basic Uncomment button in Visual Studio.](./media/comments-in-code/visual-basic-uncomment-button.gif)) buttons on the **Edit** toolbar.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="83790-134">Ayrıca, `REM` anahtar sözcüğüyle metinden önce kodunuza yorum ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="83790-134">You can also add comments to your code by preceding the text with the `REM` keyword.</span></span> <span data-ttu-id="83790-135">Ancak, `'` sembol ve açıklama/**Açıklama** ekleme düğmelerinin kullanımı daha kolaydır ve daha az alan ve bellek gerektirir.</span><span class="sxs-lookup"><span data-stu-id="83790-135">However, the `'` symbol and the **Comment**/**Uncomment** buttons are easier to use and require less space and memory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83790-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="83790-136">See also</span></span>

- [<span data-ttu-id="83790-137">Temel ınstınts-kodunuzu XML açıklamalarıyla belgeleme</span><span class="sxs-lookup"><span data-stu-id="83790-137">Basic Instincts - Documenting Your Code With XML Comments</span></span>](https://docs.microsoft.com/archive/msdn-magazine/2009/may/documenting-your-code-with-xml-comments)
- [<span data-ttu-id="83790-138">Nasıl yapılır: XML Belgesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="83790-138">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
- [<span data-ttu-id="83790-139">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="83790-139">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
- [<span data-ttu-id="83790-140">Program Yapısı ve Kod Kuralları</span><span class="sxs-lookup"><span data-stu-id="83790-140">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [<span data-ttu-id="83790-141">REM Deyimi</span><span class="sxs-lookup"><span data-stu-id="83790-141">REM Statement</span></span>](../../../visual-basic/language-reference/statements/rem-statement.md)
