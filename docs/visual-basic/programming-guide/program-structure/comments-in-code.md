---
description: 'Daha fazla bilgi edinin: koddaki açıklamalar (Visual Basic)'
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
ms.openlocfilehash: 66e12a18c2532bb5b694affccb84153f01bcddd5
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100461937"
---
# <a name="comments-in-code-visual-basic"></a><span data-ttu-id="f200f-103">Kod Açıklamaları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f200f-103">Comments in Code (Visual Basic)</span></span>

<span data-ttu-id="f200f-104">Kod örneklerini okurken genellikle açıklama simgesiyle ( `'` ) karşılaşırsınız.</span><span class="sxs-lookup"><span data-stu-id="f200f-104">As you read the code examples, you often encounter the comment symbol (`'`).</span></span> <span data-ttu-id="f200f-105">Bu simge, Visual Basic derleyicisine onu izleyen metni veya *yorumu* yoksaymasını söyler.</span><span class="sxs-lookup"><span data-stu-id="f200f-105">This symbol tells the Visual Basic compiler to ignore the text following it, or the *comment*.</span></span> <span data-ttu-id="f200f-106">Açıklamalar, okuyan kişinin yararına olması için koda eklenmiş kısa ve açıklayıcı notlardır.</span><span class="sxs-lookup"><span data-stu-id="f200f-106">Comments are brief explanatory notes added to code for the benefit of those reading it.</span></span>  
  
 <span data-ttu-id="f200f-107">Tüm yordamlara, ilgili yordamın işlevsel özelliklerini (neler yaptığını) açıklayan kısa bir açıklama ile başlanması iyi bir programlama uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="f200f-107">It is good programming practice to begin all procedures with a brief comment describing the functional characteristics of the procedure (what it does).</span></span> <span data-ttu-id="f200f-108">Bu hem sizin yararınıza, hem de kodu inceleyen herhangi bir kişinin yararına olur.</span><span class="sxs-lookup"><span data-stu-id="f200f-108">This is for your own benefit and the benefit of anyone else who examines the code.</span></span> <span data-ttu-id="f200f-109">Gerçekleştirme ayrıntılarını (yordamın bunu nasıl yaptığı), işlevsel özellikleri anlatan açıklamalardan ayırmalısınız.</span><span class="sxs-lookup"><span data-stu-id="f200f-109">You should separate the implementation details (how the procedure does it) from comments that describe the functional characteristics.</span></span> <span data-ttu-id="f200f-110">Açıklamaya gerçekleştirme ayrıntılarını eklediğinizde, işlevi güncelleştirirken bunları da güncelleştirmeyi unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f200f-110">When you include implementation details in the description, remember to update them when you update the function.</span></span>  
  
 <span data-ttu-id="f200f-111">Açıklamalar aynı satırdaki bir deyimi izleyebilir veya tüm bir satırı kaplayabilir.</span><span class="sxs-lookup"><span data-stu-id="f200f-111">Comments can follow a statement on the same line, or occupy an entire line.</span></span> <span data-ttu-id="f200f-112">Her ikisi de aşağıdaki kodda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f200f-112">Both are illustrated in the following code.</span></span>  
  
 [!code-vb[VbVbcnConventions#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#16)]  
  
 <span data-ttu-id="f200f-113">Açıklamanız için birden fazla satır gerekiyorsa, aşağıdaki örnekte gösterildiği gibi her satırda açıklama sembolünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="f200f-113">If your comment requires more than one line, use the comment symbol on each line, as the following example illustrates.</span></span>  
  
 [!code-vb[VbVbcnConventions#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#17)]  
  
## <a name="commenting-guidelines"></a><span data-ttu-id="f200f-114">Açıklamalara İlişkin Kurallar</span><span class="sxs-lookup"><span data-stu-id="f200f-114">Commenting Guidelines</span></span>  

 <span data-ttu-id="f200f-115">Aşağıdaki tabloda, kodun bir bölümünden önce hangi tür açıklamaların gelebileceğine dair genel kurallar verilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f200f-115">The following table provides general guidelines for what types of comments can precede a section of code.</span></span> <span data-ttu-id="f200f-116">Bunlar önerilerdir; Visual Basic, yorum eklemek için kuralları zorlamaz.</span><span class="sxs-lookup"><span data-stu-id="f200f-116">These are suggestions; Visual Basic does not enforce rules for adding comments.</span></span> <span data-ttu-id="f200f-117">Hem sizin, hem de kodu okuyan herhangi bir kişinin işine en çok yarayacak şeyleri yazın.</span><span class="sxs-lookup"><span data-stu-id="f200f-117">Write what works best, both for you and for anyone else who reads your code.</span></span>  
  
|||  
|---|---|  
|<span data-ttu-id="f200f-118">Açıklama türü</span><span class="sxs-lookup"><span data-stu-id="f200f-118">Comment type</span></span>|<span data-ttu-id="f200f-119">Açıklama tanımı</span><span class="sxs-lookup"><span data-stu-id="f200f-119">Comment description</span></span>|  
|<span data-ttu-id="f200f-120">Amaç</span><span class="sxs-lookup"><span data-stu-id="f200f-120">Purpose</span></span>|<span data-ttu-id="f200f-121">Yordamın ne yaptığını açıklar (bunu nasıl yaptığını değil)</span><span class="sxs-lookup"><span data-stu-id="f200f-121">Describes what the procedure does (not how it does it)</span></span>|  
|<span data-ttu-id="f200f-122">Varsayımlar</span><span class="sxs-lookup"><span data-stu-id="f200f-122">Assumptions</span></span>|<span data-ttu-id="f200f-123">Her bir dış bağımsız değişkeni, denetimi, dosya açmayı veya yordamın erişim sağladığı diğer öğeyi listeler</span><span class="sxs-lookup"><span data-stu-id="f200f-123">Lists each external variable, control, open file, or other element accessed by the procedure</span></span>|  
|<span data-ttu-id="f200f-124">Etkiler</span><span class="sxs-lookup"><span data-stu-id="f200f-124">Effects</span></span>|<span data-ttu-id="f200f-125">Her bir etkilenen dış bağımsız değişkeni, denetimi veya dosyayı ve sahip olduğu etkiyi (bu etki bariz değilse) listeler</span><span class="sxs-lookup"><span data-stu-id="f200f-125">Lists each affected external variable, control, or file, and the effect it has (only if it is not obvious)</span></span>|  
|<span data-ttu-id="f200f-126">Girişler</span><span class="sxs-lookup"><span data-stu-id="f200f-126">Inputs</span></span>|<span data-ttu-id="f200f-127">Bağımsız değişkenin amacını belirtir</span><span class="sxs-lookup"><span data-stu-id="f200f-127">Specifies the purpose of the argument</span></span>|  
|<span data-ttu-id="f200f-128">Döndürülenler</span><span class="sxs-lookup"><span data-stu-id="f200f-128">Returns</span></span>|<span data-ttu-id="f200f-129">Yordamın döndürdüğü değerleri açıklar</span><span class="sxs-lookup"><span data-stu-id="f200f-129">Explains the values returned by the procedure</span></span>|  
  
 <span data-ttu-id="f200f-130">Aşağıdaki hususları unutmayın:</span><span class="sxs-lookup"><span data-stu-id="f200f-130">Remember the following points:</span></span>  
  
- <span data-ttu-id="f200f-131">Her önemli değişken bildiriminin önünde, bildirilen değişkenin kullanımını anlatan bir açıklama bulunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f200f-131">Every important variable declaration should be preceded by a comment describing the use of the variable being declared.</span></span>  
  
- <span data-ttu-id="f200f-132">Değişkenler, denetimler ve yordamlar, yalnızca karmaşık gerçekleştirme ayrıntıları için açıklamaya gerek duyulacak şekilde yeterince açık adlandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f200f-132">Variables, controls, and procedures should be named clearly enough that commenting is needed only for complex implementation details.</span></span>  
  
- <span data-ttu-id="f200f-133">Açıklamalar, aynı satırdaki bir satır devamlılığı dizisinden sonra gelemez.</span><span class="sxs-lookup"><span data-stu-id="f200f-133">Comments cannot follow a line-continuation sequence on the same line.</span></span>  
  
 <span data-ttu-id="f200f-134">Bir veya daha fazla kod satırı seçip **Açıklama** ( ![ visual Studio 'da Visual Basic Açıklama düğmesi) seçerek ve ](./media/comments-in-code/visual-basic-comment-button.gif)  ![ ](./media/comments-in-code/visual-basic-uncomment-button.gif) **düzenleme** araç çubuğundaki açıklamayı (Visual Studio 'da yorum düğmesi Visual Basic) seçerek bir kod bloğu için açıklama sembolleri ekleyebilir veya kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f200f-134">You can add or remove comment symbols for a block of code by selecting one or more lines of code and choosing the **Comment** (![The Visual Basic Comment button in Visual Studio.](./media/comments-in-code/visual-basic-comment-button.gif)) and **Uncomment** (![The Visual Basic Uncomment button in Visual Studio.](./media/comments-in-code/visual-basic-uncomment-button.gif)) buttons on the **Edit** toolbar.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f200f-135">Ayrıca, metin anahtar sözcüğüyle metinden önce kodunuza yorum ekleyebilirsiniz `REM` .</span><span class="sxs-lookup"><span data-stu-id="f200f-135">You can also add comments to your code by preceding the text with the `REM` keyword.</span></span> <span data-ttu-id="f200f-136">Ancak `'` simge ve **Açıklama açıklama** ekleme /  düğmelerinin kullanımı daha kolaydır ve daha az alan ve bellek gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f200f-136">However, the `'` symbol and the **Comment**/**Uncomment** buttons are easier to use and require less space and memory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f200f-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f200f-137">See also</span></span>

- [<span data-ttu-id="f200f-138">Temel ınstınts-kodunuzu XML açıklamalarıyla belgeleme</span><span class="sxs-lookup"><span data-stu-id="f200f-138">Basic Instincts - Documenting Your Code With XML Comments</span></span>](/archive/msdn-magazine/2009/may/documenting-your-code-with-xml-comments)
- [<span data-ttu-id="f200f-139">Nasıl yapılır: XML Belgesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f200f-139">How to: Create XML Documentation</span></span>](how-to-create-xml-documentation.md)
- [<span data-ttu-id="f200f-140">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="f200f-140">XML Comment Tags</span></span>](../../language-reference/xmldoc/index.md)
- [<span data-ttu-id="f200f-141">Program yapısı ve kod kuralları</span><span class="sxs-lookup"><span data-stu-id="f200f-141">Program Structure and Code Conventions</span></span>](program-structure-and-code-conventions.md)
- [<span data-ttu-id="f200f-142">REM Deyimi</span><span class="sxs-lookup"><span data-stu-id="f200f-142">REM Statement</span></span>](../../language-reference/statements/rem-statement.md)
