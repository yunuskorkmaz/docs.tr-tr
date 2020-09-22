---
title: "'<structurename>' yapısı en az bir örnek üye değişkeni veya 'Custom' olarak işaretlenmemiş en az bir örnek olay bildirimi içermelidir"
ms.date: 07/20/2015
f1_keywords:
- bc30941
- vbc30941
helpviewer_keywords:
- BC30941
ms.assetid: 7054cc1e-bac3-4c3d-82f3-35772bd8dd3b
ms.openlocfilehash: a350940cf052aa8fbee4a1e3c61cbeaa4e37408a
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870590"
---
# <a name="structure-structurename-must-contain-at-least-one-instance-member-variable-or-at-least-one-instance-event-declaration-not-marked-custom"></a><span data-ttu-id="24b91-102">'\<structurename>' yapısı en az bir örnek üye değişkeni veya 'Custom' olarak işaretlenmemiş en az bir örnek olay bildirimi içermelidir</span><span class="sxs-lookup"><span data-stu-id="24b91-102">Structure '\<structurename>' must contain at least one instance member variable or at least one instance event declaration not marked 'Custom'</span></span>

<span data-ttu-id="24b91-103">Bir yapı tanımı, paylaşılmayan olmayan değişkenler veya paylaşılmayan özel olmayan olaylar içermez.</span><span class="sxs-lookup"><span data-stu-id="24b91-103">A structure definition does not include any nonshared variables or nonshared noncustom events.</span></span>  
  
 <span data-ttu-id="24b91-104">Her yapının, tek tek ([paylaşılan](../modifiers/shared.md)) tüm örnekler yerine her belirli örnek (paylaşılmayan) için geçerli olan bir değişkene veya olaya sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="24b91-104">Every structure must have either a variable or an event that applies to each specific instance (nonshared) instead of to all instances collectively ([Shared](../modifiers/shared.md)).</span></span> <span data-ttu-id="24b91-105">Paylaşılmayan sabitler, Özellikler ve yordamlar bu gereksinimi karşılamıyor.</span><span class="sxs-lookup"><span data-stu-id="24b91-105">Nonshared constants, properties, and procedures do not satisfy this requirement.</span></span> <span data-ttu-id="24b91-106">Ayrıca, paylaşılmayan değişkenler ve yalnızca paylaşılan olmayan bir olay yoksa, bu olay bir `Custom` olay olamaz.</span><span class="sxs-lookup"><span data-stu-id="24b91-106">In addition, if there are no nonshared variables and only one nonshared event, that event cannot be a `Custom` event.</span></span>  
  
 <span data-ttu-id="24b91-107">**Hata kimliği:** BC30941</span><span class="sxs-lookup"><span data-stu-id="24b91-107">**Error ID:** BC30941</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="24b91-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="24b91-108">To correct this error</span></span>  
  
- <span data-ttu-id="24b91-109">En az bir değişken veya olmayan olay tanımlayın `Shared` .</span><span class="sxs-lookup"><span data-stu-id="24b91-109">Define at least one variable or event that is not `Shared`.</span></span> <span data-ttu-id="24b91-110">Yalnızca bir olay tanımlarsanız, özel olmayan ve paylaşılmayan olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="24b91-110">If you define only one event, it must be noncustom as well as nonshared.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24b91-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="24b91-111">See also</span></span>

- [<span data-ttu-id="24b91-112">Yapılar</span><span class="sxs-lookup"><span data-stu-id="24b91-112">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="24b91-113">Nasıl yapılır: Yapıyı Bildirme</span><span class="sxs-lookup"><span data-stu-id="24b91-113">How to: Declare a Structure</span></span>](../../programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="24b91-114">Structure Yapısı</span><span class="sxs-lookup"><span data-stu-id="24b91-114">Structure Statement</span></span>](../statements/structure-statement.md)
