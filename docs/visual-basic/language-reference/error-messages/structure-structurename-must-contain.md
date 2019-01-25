---
title: Yapı &#39; &lt;structurename&gt; &#39; en az bir örnek üye değişkeni veya işaretlenmemiş en az bir örnek olay bildirimi içermelidir &#39;özel&#39;
ms.date: 07/20/2015
f1_keywords:
- bc30941
- vbc30941
helpviewer_keywords:
- BC30941
ms.assetid: 7054cc1e-bac3-4c3d-82f3-35772bd8dd3b
ms.openlocfilehash: d8c654c212a459d40c6cf20cd62c3e0fcda8511b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54603787"
---
# <a name="structure-39ltstructurenamegt39-must-contain-at-least-one-instance-member-variable-or-at-least-one-instance-event-declaration-not-marked-39custom39"></a><span data-ttu-id="b745f-102">Yapı &#39; &lt;structurename&gt; &#39; en az bir örnek üye değişkeni veya işaretlenmemiş en az bir örnek olay bildirimi içermelidir &#39;özel&#39;</span><span class="sxs-lookup"><span data-stu-id="b745f-102">Structure &#39;&lt;structurename&gt;&#39; must contain at least one instance member variable or at least one instance event declaration not marked &#39;Custom&#39;</span></span>
<span data-ttu-id="b745f-103">Bir yapı tanımı, herhangi bir paylaşılmayan değişkenler veya paylaşılmayan, özel olmayan olaylar içermez.</span><span class="sxs-lookup"><span data-stu-id="b745f-103">A structure definition does not include any nonshared variables or nonshared noncustom events.</span></span>  
  
 <span data-ttu-id="b745f-104">Her yapı bir değişken ya da her belirli bir örneğine (yerine paylaşılmayan) tüm örneklerini topluca uygulandığı bir olay olmalıdır ([paylaşılan](../../../visual-basic/language-reference/modifiers/shared.md)).</span><span class="sxs-lookup"><span data-stu-id="b745f-104">Every structure must have either a variable or an event that applies to each specific instance (nonshared) instead of to all instances collectively ([Shared](../../../visual-basic/language-reference/modifiers/shared.md)).</span></span> <span data-ttu-id="b745f-105">Paylaşılmayan sabitler, özellikler ve yordamlar bu gereksinimi karşılamıyor.</span><span class="sxs-lookup"><span data-stu-id="b745f-105">Nonshared constants, properties, and procedures do not satisfy this requirement.</span></span> <span data-ttu-id="b745f-106">Ayrıca, herhangi bir paylaşılmayan değişkenler ve yalnızca bir paylaşılmayan olay varsa, bu olay olamaz bir `Custom` olay.</span><span class="sxs-lookup"><span data-stu-id="b745f-106">In addition, if there are no nonshared variables and only one nonshared event, that event cannot be a `Custom` event.</span></span>  
  
 <span data-ttu-id="b745f-107">**Hata Kimliği:** BC30941</span><span class="sxs-lookup"><span data-stu-id="b745f-107">**Error ID:** BC30941</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b745f-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="b745f-108">To correct this error</span></span>  
  
-   <span data-ttu-id="b745f-109">En az bir değişken veya değil olay tanımlama `Shared`.</span><span class="sxs-lookup"><span data-stu-id="b745f-109">Define at least one variable or event that is not `Shared`.</span></span> <span data-ttu-id="b745f-110">Yalnızca bir olay tanımlarsanız, özel olmayan yanı sıra paylaşılmayan olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b745f-110">If you define only one event, it must be noncustom as well as nonshared.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b745f-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b745f-111">See also</span></span>
- [<span data-ttu-id="b745f-112">Yapılar</span><span class="sxs-lookup"><span data-stu-id="b745f-112">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="b745f-113">Nasıl yapılır: Yapıyı Bildirme</span><span class="sxs-lookup"><span data-stu-id="b745f-113">How to: Declare a Structure</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="b745f-114">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="b745f-114">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
