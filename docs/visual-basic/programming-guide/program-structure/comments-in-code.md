---
title: Kod Açıklamaları (Visual Basic)
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
ms.openlocfilehash: a8094397ff2a076cf474d735e65298b3d2f0a9cd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62050571"
---
# <a name="comments-in-code-visual-basic"></a><span data-ttu-id="88096-102">Kod Açıklamaları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="88096-102">Comments in Code (Visual Basic)</span></span>
<span data-ttu-id="88096-103">Kod örneklerini okurken açıklama sembolüyle sık karşılaştığınız (`'`).</span><span class="sxs-lookup"><span data-stu-id="88096-103">As you read the code examples, you often encounter the comment symbol (`'`).</span></span> <span data-ttu-id="88096-104">Bu simge, metni yok saymak için Visual Basic derleyiciye veya *yorum*.</span><span class="sxs-lookup"><span data-stu-id="88096-104">This symbol tells the Visual Basic compiler to ignore the text following it, or the *comment*.</span></span> <span data-ttu-id="88096-105">Açıklamalar, okuyan kişinin yararına olması için koda eklenmiş kısa ve açıklayıcı notlardır.</span><span class="sxs-lookup"><span data-stu-id="88096-105">Comments are brief explanatory notes added to code for the benefit of those reading it.</span></span>  
  
 <span data-ttu-id="88096-106">Tüm yordamlara, ilgili yordamın işlevsel özelliklerini (neler yaptığını) açıklayan kısa bir açıklama ile başlanması iyi bir programlama uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="88096-106">It is good programming practice to begin all procedures with a brief comment describing the functional characteristics of the procedure (what it does).</span></span> <span data-ttu-id="88096-107">Bu hem sizin yararınıza, hem de kodu inceleyen herhangi bir kişinin yararına olur.</span><span class="sxs-lookup"><span data-stu-id="88096-107">This is for your own benefit and the benefit of anyone else who examines the code.</span></span> <span data-ttu-id="88096-108">Gerçekleştirme ayrıntılarını (yordamın bunu nasıl yaptığı), işlevsel özellikleri anlatan açıklamalardan ayırmalısınız.</span><span class="sxs-lookup"><span data-stu-id="88096-108">You should separate the implementation details (how the procedure does it) from comments that describe the functional characteristics.</span></span> <span data-ttu-id="88096-109">Açıklamaya gerçekleştirme ayrıntılarını eklediğinizde, işlevi güncelleştirirken bunları da güncelleştirmeyi unutmayın.</span><span class="sxs-lookup"><span data-stu-id="88096-109">When you include implementation details in the description, remember to update them when you update the function.</span></span>  
  
 <span data-ttu-id="88096-110">Açıklamalar aynı satırdaki bir deyimi izleyebilir veya tüm bir satırı kaplayabilir.</span><span class="sxs-lookup"><span data-stu-id="88096-110">Comments can follow a statement on the same line, or occupy an entire line.</span></span> <span data-ttu-id="88096-111">Her ikisi de aşağıdaki kodda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="88096-111">Both are illustrated in the following code.</span></span>  
  
 [!code-vb[VbVbcnConventions#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#16)]  
  
 <span data-ttu-id="88096-112">Açıklamanız için birden fazla satır gerekiyorsa, aşağıdaki örnekte gösterildiği gibi her satırda açıklama sembolünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="88096-112">If your comment requires more than one line, use the comment symbol on each line, as the following example illustrates.</span></span>  
  
 [!code-vb[VbVbcnConventions#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#17)]  
  
## <a name="commenting-guidelines"></a><span data-ttu-id="88096-113">Açıklamalara İlişkin Kurallar</span><span class="sxs-lookup"><span data-stu-id="88096-113">Commenting Guidelines</span></span>  
 <span data-ttu-id="88096-114">Aşağıdaki tabloda, kodun bir bölümünden önce hangi tür açıklamaların gelebileceğine dair genel kurallar verilmektedir.</span><span class="sxs-lookup"><span data-stu-id="88096-114">The following table provides general guidelines for what types of comments can precede a section of code.</span></span> <span data-ttu-id="88096-115">Bunlar önerilerdir; Visual Basic açıklama eklemek için kuralları zorunlu kılmaz.</span><span class="sxs-lookup"><span data-stu-id="88096-115">These are suggestions; Visual Basic does not enforce rules for adding comments.</span></span> <span data-ttu-id="88096-116">Hem sizin, hem de kodu okuyan herhangi bir kişinin işine en çok yarayacak şeyleri yazın.</span><span class="sxs-lookup"><span data-stu-id="88096-116">Write what works best, both for you and for anyone else who reads your code.</span></span>  
  
|||  
|---|---|  
|<span data-ttu-id="88096-117">Açıklama türü</span><span class="sxs-lookup"><span data-stu-id="88096-117">Comment type</span></span>|<span data-ttu-id="88096-118">Açıklama tanımı</span><span class="sxs-lookup"><span data-stu-id="88096-118">Comment description</span></span>|  
|<span data-ttu-id="88096-119">Amaç</span><span class="sxs-lookup"><span data-stu-id="88096-119">Purpose</span></span>|<span data-ttu-id="88096-120">Yordamın ne yaptığını açıklar (bunu nasıl yaptığını değil)</span><span class="sxs-lookup"><span data-stu-id="88096-120">Describes what the procedure does (not how it does it)</span></span>|  
|<span data-ttu-id="88096-121">Varsayımlar</span><span class="sxs-lookup"><span data-stu-id="88096-121">Assumptions</span></span>|<span data-ttu-id="88096-122">Her bir dış bağımsız değişkeni, denetimi, dosya açmayı veya yordamın erişim sağladığı diğer öğeyi listeler</span><span class="sxs-lookup"><span data-stu-id="88096-122">Lists each external variable, control, open file, or other element accessed by the procedure</span></span>|  
|<span data-ttu-id="88096-123">Etkiler</span><span class="sxs-lookup"><span data-stu-id="88096-123">Effects</span></span>|<span data-ttu-id="88096-124">Her bir etkilenen dış bağımsız değişkeni, denetimi veya dosyayı ve sahip olduğu etkiyi (bu etki bariz değilse) listeler</span><span class="sxs-lookup"><span data-stu-id="88096-124">Lists each affected external variable, control, or file, and the effect it has (only if it is not obvious)</span></span>|  
|<span data-ttu-id="88096-125">Girişler</span><span class="sxs-lookup"><span data-stu-id="88096-125">Inputs</span></span>|<span data-ttu-id="88096-126">Bağımsız değişkenin amacını belirtir</span><span class="sxs-lookup"><span data-stu-id="88096-126">Specifies the purpose of the argument</span></span>|  
|<span data-ttu-id="88096-127">Döndürür</span><span class="sxs-lookup"><span data-stu-id="88096-127">Returns</span></span>|<span data-ttu-id="88096-128">Yordamın döndürdüğü değerleri açıklar</span><span class="sxs-lookup"><span data-stu-id="88096-128">Explains the values returned by the procedure</span></span>|  
  
 <span data-ttu-id="88096-129">Aşağıdaki hususları unutmayın:</span><span class="sxs-lookup"><span data-stu-id="88096-129">Remember the following points:</span></span>  
  
- <span data-ttu-id="88096-130">Her önemli değişken bildiriminin önünde, bildirilen değişkenin kullanımını anlatan bir açıklama bulunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="88096-130">Every important variable declaration should be preceded by a comment describing the use of the variable being declared.</span></span>  
  
- <span data-ttu-id="88096-131">Değişkenler, denetimler ve yordamlar, yalnızca karmaşık gerçekleştirme ayrıntıları için açıklamaya gerek duyulacak şekilde yeterince açık adlandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="88096-131">Variables, controls, and procedures should be named clearly enough that commenting is needed only for complex implementation details.</span></span>  
  
- <span data-ttu-id="88096-132">Açıklamalar, aynı satırdaki bir satır devamlılığı dizisinden sonra gelemez.</span><span class="sxs-lookup"><span data-stu-id="88096-132">Comments cannot follow a line-continuation sequence on the same line.</span></span>  
  
 <span data-ttu-id="88096-133">Ekleyebilir veya bir veya daha fazla kod satırlarını ve seçerek bir kod bloğu için açıklama sembolleri kaldırmak **yorum** (![Visual Studio. Visual Basic Açıklama düğmesi](./media/comments-in-code/visual-basic-comment-button.gif)) ve **açıklamayı Kaldır**  (![Düğmesini Visual Studio. Visual Basic açıklamadan çıkarın](./media/comments-in-code/visual-basic-uncomment-button.gif)) düğmelerini **Düzenle** araç çubuğu.</span><span class="sxs-lookup"><span data-stu-id="88096-133">You can add or remove comment symbols for a block of code by selecting one or more lines of code and choosing the **Comment** (![The Visual Basic Comment button in Visual Studio.](./media/comments-in-code/visual-basic-comment-button.gif)) and **Uncomment** (![The Visual Basic Uncomment button in Visual Studio.](./media/comments-in-code/visual-basic-uncomment-button.gif)) buttons on the **Edit** toolbar.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="88096-134">Metinle koyarak kodunuza açıklama ekleyebilirsiniz `REM` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="88096-134">You can also add comments to your code by preceding the text with the `REM` keyword.</span></span> <span data-ttu-id="88096-135">Ancak, `'` sembol ve **yorum**/**açıklamayı Kaldır** düğmeleri daha kolay ve daha az alan ve bellek gerektirir.</span><span class="sxs-lookup"><span data-stu-id="88096-135">However, the `'` symbol and the **Comment**/**Uncomment** buttons are easier to use and require less space and memory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88096-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="88096-136">See also</span></span>

- [<span data-ttu-id="88096-137">Temel Küçümsemeyin - XML açıklamalarıyla kodunuzu belgeleme</span><span class="sxs-lookup"><span data-stu-id="88096-137">Basic Instincts - Documenting Your Code With XML Comments</span></span>](https://msdn.microsoft.com/magazine/dd722812.aspx)
- [<span data-ttu-id="88096-138">Nasıl yapılır: XML belgesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="88096-138">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
- [<span data-ttu-id="88096-139">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="88096-139">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
- [<span data-ttu-id="88096-140">Program Yapısı ve Kod Kuralları</span><span class="sxs-lookup"><span data-stu-id="88096-140">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [<span data-ttu-id="88096-141">REM Deyimi</span><span class="sxs-lookup"><span data-stu-id="88096-141">REM Statement</span></span>](../../../visual-basic/language-reference/statements/rem-statement.md)
