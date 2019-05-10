---
title: "'<structurename>' yapısı en az bir örnek üye değişkeni veya 'Custom' olarak işaretlenmemiş en az bir örnek olay bildirimi içermelidir"
ms.date: 07/20/2015
f1_keywords:
- bc30941
- vbc30941
helpviewer_keywords:
- BC30941
ms.assetid: 7054cc1e-bac3-4c3d-82f3-35772bd8dd3b
ms.openlocfilehash: 4ce24073896326bb5a68e563e2d34aafa09ef1c1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64593212"
---
# <a name="structure-structurename-must-contain-at-least-one-instance-member-variable-or-at-least-one-instance-event-declaration-not-marked-custom"></a><span data-ttu-id="cacaf-102">Yapı '\<structurename >' en az bir örnek üye değişkeni veya 'Custom' olarak işaretlenmemiş en az bir örnek olay bildirimi içermelidir</span><span class="sxs-lookup"><span data-stu-id="cacaf-102">Structure '\<structurename>' must contain at least one instance member variable or at least one instance event declaration not marked 'Custom'</span></span>
<span data-ttu-id="cacaf-103">Bir yapı tanımı, herhangi bir paylaşılmayan değişkenler veya paylaşılmayan, özel olmayan olaylar içermez.</span><span class="sxs-lookup"><span data-stu-id="cacaf-103">A structure definition does not include any nonshared variables or nonshared noncustom events.</span></span>  
  
 <span data-ttu-id="cacaf-104">Her yapı bir değişken ya da her belirli bir örneğine (yerine paylaşılmayan) tüm örneklerini topluca uygulandığı bir olay olmalıdır ([paylaşılan](../../../visual-basic/language-reference/modifiers/shared.md)).</span><span class="sxs-lookup"><span data-stu-id="cacaf-104">Every structure must have either a variable or an event that applies to each specific instance (nonshared) instead of to all instances collectively ([Shared](../../../visual-basic/language-reference/modifiers/shared.md)).</span></span> <span data-ttu-id="cacaf-105">Paylaşılmayan sabitler, özellikler ve yordamlar bu gereksinimi karşılamıyor.</span><span class="sxs-lookup"><span data-stu-id="cacaf-105">Nonshared constants, properties, and procedures do not satisfy this requirement.</span></span> <span data-ttu-id="cacaf-106">Ayrıca, herhangi bir paylaşılmayan değişkenler ve yalnızca bir paylaşılmayan olay varsa, bu olay olamaz bir `Custom` olay.</span><span class="sxs-lookup"><span data-stu-id="cacaf-106">In addition, if there are no nonshared variables and only one nonshared event, that event cannot be a `Custom` event.</span></span>  
  
 <span data-ttu-id="cacaf-107">**Hata Kimliği:** BC30941</span><span class="sxs-lookup"><span data-stu-id="cacaf-107">**Error ID:** BC30941</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="cacaf-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="cacaf-108">To correct this error</span></span>  
  
- <span data-ttu-id="cacaf-109">En az bir değişken veya değil olay tanımlama `Shared`.</span><span class="sxs-lookup"><span data-stu-id="cacaf-109">Define at least one variable or event that is not `Shared`.</span></span> <span data-ttu-id="cacaf-110">Yalnızca bir olay tanımlarsanız, özel olmayan yanı sıra paylaşılmayan olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cacaf-110">If you define only one event, it must be noncustom as well as nonshared.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cacaf-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cacaf-111">See also</span></span>

- [<span data-ttu-id="cacaf-112">Yapılar</span><span class="sxs-lookup"><span data-stu-id="cacaf-112">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="cacaf-113">Nasıl yapılır: Yapıyı Bildirme</span><span class="sxs-lookup"><span data-stu-id="cacaf-113">How to: Declare a Structure</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="cacaf-114">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="cacaf-114">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
