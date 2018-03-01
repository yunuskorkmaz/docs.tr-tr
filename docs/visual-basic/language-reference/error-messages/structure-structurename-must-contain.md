---
title: "Yapı &#39; &lt;structurename&gt;&#39; en az bir örnek üye değişkeni veya işaretlenmemiş en az bir örnek olay bildirimi &#39; içermelidir Özel &#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30941
- vbc30941
helpviewer_keywords:
- BC30941
ms.assetid: 7054cc1e-bac3-4c3d-82f3-35772bd8dd3b
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b28dd59271bdaca52072710ea797fae6e9168eab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="structure-39ltstructurenamegt39-must-contain-at-least-one-instance-member-variable-or-at-least-one-instance-event-declaration-not-marked-39custom39"></a><span data-ttu-id="a9ca7-102">Yapı &#39; &lt;structurename&gt;&#39; en az bir örnek üye değişkeni veya işaretlenmemiş en az bir örnek olay bildirimi &#39; içermelidir Özel &#39;</span><span class="sxs-lookup"><span data-stu-id="a9ca7-102">Structure &#39;&lt;structurename&gt;&#39; must contain at least one instance member variable or at least one instance event declaration not marked &#39;Custom&#39;</span></span>
<span data-ttu-id="a9ca7-103">Yapı tanımı, herhangi bir paylaşılmayan değişkenleri veya paylaşılmayan de olayları içermez.</span><span class="sxs-lookup"><span data-stu-id="a9ca7-103">A structure definition does not include any nonshared variables or nonshared noncustom events.</span></span>  
  
 <span data-ttu-id="a9ca7-104">Her yapısı, değişken veya her belirli bir örneğine (yerine paylaşılmayan) tüm örneklerini topluca uygulandığı olaya sahip olması gerekir ([paylaşılan](../../../visual-basic/language-reference/modifiers/shared.md)).</span><span class="sxs-lookup"><span data-stu-id="a9ca7-104">Every structure must have either a variable or an event that applies to each specific instance (nonshared) instead of to all instances collectively ([Shared](../../../visual-basic/language-reference/modifiers/shared.md)).</span></span> <span data-ttu-id="a9ca7-105">Paylaşılmayan sabitleri, özellikleri ve yordamlar bu gereksinimi karşılamıyor.</span><span class="sxs-lookup"><span data-stu-id="a9ca7-105">Nonshared constants, properties, and procedures do not satisfy this requirement.</span></span> <span data-ttu-id="a9ca7-106">Ayrıca, paylaşılmayan değişken yok ve yalnızca bir paylaşılmayan olay varsa, bu olay olamaz bir `Custom` olay.</span><span class="sxs-lookup"><span data-stu-id="a9ca7-106">In addition, if there are no nonshared variables and only one nonshared event, that event cannot be a `Custom` event.</span></span>  
  
 <span data-ttu-id="a9ca7-107">**Hata Kimliği:** BC30941</span><span class="sxs-lookup"><span data-stu-id="a9ca7-107">**Error ID:** BC30941</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a9ca7-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="a9ca7-108">To correct this error</span></span>  
  
-   <span data-ttu-id="a9ca7-109">En az bir değişken veya değil olay tanımlama `Shared`.</span><span class="sxs-lookup"><span data-stu-id="a9ca7-109">Define at least one variable or event that is not `Shared`.</span></span> <span data-ttu-id="a9ca7-110">Yalnızca bir olay tanımlarsanız de yanı sıra paylaşılmayan olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a9ca7-110">If you define only one event, it must be noncustom as well as nonshared.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9ca7-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a9ca7-111">See Also</span></span>  
 [<span data-ttu-id="a9ca7-112">Yapıları</span><span class="sxs-lookup"><span data-stu-id="a9ca7-112">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="a9ca7-113">Nasıl yapılır: bir yapıyı bildirme</span><span class="sxs-lookup"><span data-stu-id="a9ca7-113">How to: Declare a Structure</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [<span data-ttu-id="a9ca7-114">Structure deyimi</span><span class="sxs-lookup"><span data-stu-id="a9ca7-114">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
