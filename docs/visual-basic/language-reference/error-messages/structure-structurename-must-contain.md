---
title: Yapı &#39; &lt;structurename&gt; &#39; en az bir örnek üye değişkeni ya da en az bir örnek olay bildirimi işaretlenmemiş içermelidir &#39;özel&#39;
ms.date: 07/20/2015
f1_keywords:
- bc30941
- vbc30941
helpviewer_keywords:
- BC30941
ms.assetid: 7054cc1e-bac3-4c3d-82f3-35772bd8dd3b
ms.openlocfilehash: 85a4babc808e274a99f2c9faf08a02abf8aa4e93
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33594507"
---
# <a name="structure-39ltstructurenamegt39-must-contain-at-least-one-instance-member-variable-or-at-least-one-instance-event-declaration-not-marked-39custom39"></a><span data-ttu-id="d6a10-102">Yapı &#39; &lt;structurename&gt; &#39; en az bir örnek üye değişkeni ya da en az bir örnek olay bildirimi işaretlenmemiş içermelidir &#39;özel&#39;</span><span class="sxs-lookup"><span data-stu-id="d6a10-102">Structure &#39;&lt;structurename&gt;&#39; must contain at least one instance member variable or at least one instance event declaration not marked &#39;Custom&#39;</span></span>
<span data-ttu-id="d6a10-103">Yapı tanımı, herhangi bir paylaşılmayan değişkenleri veya paylaşılmayan de olayları içermez.</span><span class="sxs-lookup"><span data-stu-id="d6a10-103">A structure definition does not include any nonshared variables or nonshared noncustom events.</span></span>  
  
 <span data-ttu-id="d6a10-104">Her yapısı, değişken veya her belirli bir örneğine (yerine paylaşılmayan) tüm örneklerini topluca uygulandığı olaya sahip olması gerekir ([paylaşılan](../../../visual-basic/language-reference/modifiers/shared.md)).</span><span class="sxs-lookup"><span data-stu-id="d6a10-104">Every structure must have either a variable or an event that applies to each specific instance (nonshared) instead of to all instances collectively ([Shared](../../../visual-basic/language-reference/modifiers/shared.md)).</span></span> <span data-ttu-id="d6a10-105">Paylaşılmayan sabitleri, özellikleri ve yordamlar bu gereksinimi karşılamıyor.</span><span class="sxs-lookup"><span data-stu-id="d6a10-105">Nonshared constants, properties, and procedures do not satisfy this requirement.</span></span> <span data-ttu-id="d6a10-106">Ayrıca, paylaşılmayan değişken yok ve yalnızca bir paylaşılmayan olay varsa, bu olay olamaz bir `Custom` olay.</span><span class="sxs-lookup"><span data-stu-id="d6a10-106">In addition, if there are no nonshared variables and only one nonshared event, that event cannot be a `Custom` event.</span></span>  
  
 <span data-ttu-id="d6a10-107">**Hata Kimliği:** BC30941</span><span class="sxs-lookup"><span data-stu-id="d6a10-107">**Error ID:** BC30941</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d6a10-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="d6a10-108">To correct this error</span></span>  
  
-   <span data-ttu-id="d6a10-109">En az bir değişken veya değil olay tanımlama `Shared`.</span><span class="sxs-lookup"><span data-stu-id="d6a10-109">Define at least one variable or event that is not `Shared`.</span></span> <span data-ttu-id="d6a10-110">Yalnızca bir olay tanımlarsanız de yanı sıra paylaşılmayan olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d6a10-110">If you define only one event, it must be noncustom as well as nonshared.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6a10-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d6a10-111">See Also</span></span>  
 [<span data-ttu-id="d6a10-112">Yapılar</span><span class="sxs-lookup"><span data-stu-id="d6a10-112">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="d6a10-113">Nasıl yapılır: Bir Yapıyı Bildirme</span><span class="sxs-lookup"><span data-stu-id="d6a10-113">How to: Declare a Structure</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [<span data-ttu-id="d6a10-114">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="d6a10-114">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
