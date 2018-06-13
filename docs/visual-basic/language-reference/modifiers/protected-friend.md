---
title: Korumalı Friend (Visual Basic)
ms.date: 05/10/2018
helpviewer_keywords:
- Protected Friend keyword [Visual Basic]
- Protected Friend keyword [Visual Basic], syntax
ms.openlocfilehash: b72cbee0394043620e792d1c014bfe55121e175e
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/18/2018
ms.locfileid: "34306557"
---
# <a name="protected-friend-visual-basic"></a><span data-ttu-id="84edf-102">Korumalı Friend (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="84edf-102">Protected Friend (Visual Basic)</span></span>

<span data-ttu-id="84edf-103">`Protected Friend` Anahtar sözcüğü birleşimi olan bir üye erişim değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="84edf-103">The `Protected Friend` keyword combination is a member access modifier.</span></span> <span data-ttu-id="84edf-104">Her ikisi de confers [arkadaş](friend.md) erişim ve [korumalı](protected.md) bildirilen öğelerde aynı bütünleştirilmiş kodda, kendi sınıfından ve türetilmiş sınıflarından herhangi bir yerindeki erişilebilir olduklarından erişim.</span><span class="sxs-lookup"><span data-stu-id="84edf-104">It confers both [Friend](friend.md) access and [Protected](protected.md) access on the declared elements, so they are accessible from anywhere in the same assembly, from their own class, and from derived classes.</span></span> <span data-ttu-id="84edf-105">Belirleyebileceğiniz `Protected Friend` yalnızca sınıfları; üyelerinde uygulayamazsınız `Protected Friend` bir yapı üyelerine yapıları devraldığından.</span><span class="sxs-lookup"><span data-stu-id="84edf-105">You can specify `Protected Friend` only on members of classes; you cannot apply `Protected Friend` to members of a structure because structures cannot be inherited.</span></span>

> [!NOTE]
> <span data-ttu-id="84edf-106">Visual Studio'da F1 Yardımı seçme `protected friend` ya da Yardım sağlar [korumalı](protected.md) veya [arkadaş](friend.md).</span><span class="sxs-lookup"><span data-stu-id="84edf-106">In Visual Studio, selecting F1 help on `protected friend` provides help for either [protected](protected.md) or [friend](friend.md).</span></span> <span data-ttu-id="84edf-107">IDE bileşik word yerine imleci altında tek belirteç seçer.</span><span class="sxs-lookup"><span data-stu-id="84edf-107">The IDE picks the single token under the cursor rather than the compound word.</span></span>

## <a name="rules"></a><span data-ttu-id="84edf-108">Kurallar</span><span class="sxs-lookup"><span data-stu-id="84edf-108">Rules</span></span>

- <span data-ttu-id="84edf-109">**Bildirim bağlamı.**</span><span class="sxs-lookup"><span data-stu-id="84edf-109">**Declaration Context.**</span></span> <span data-ttu-id="84edf-110">Kullanabileceğiniz `Protected Friend` yalnızca sınıf düzeyinde.</span><span class="sxs-lookup"><span data-stu-id="84edf-110">You can use `Protected Friend` only at the class level.</span></span> <span data-ttu-id="84edf-111">Bu bildirimi bağlamının anlamına gelir bir `Protected` öğesi bir sınıf olmalıdır ve bir kaynak dosyasını, ad alanı, arabirim, modülü, yapısı veya yordamı olamaz.</span><span class="sxs-lookup"><span data-stu-id="84edf-111">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span> 


## <a name="see-also"></a><span data-ttu-id="84edf-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="84edf-112">See Also</span></span>

[<span data-ttu-id="84edf-113">Public</span><span class="sxs-lookup"><span data-stu-id="84edf-113">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
[<span data-ttu-id="84edf-114">Protected</span><span class="sxs-lookup"><span data-stu-id="84edf-114">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
<span data-ttu-id="84edf-115">[Arkadaş](friend.md) </span><span class="sxs-lookup"><span data-stu-id="84edf-115">[Friend](friend.md) </span></span>  
[<span data-ttu-id="84edf-116">Private</span><span class="sxs-lookup"><span data-stu-id="84edf-116">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
<span data-ttu-id="84edf-117">[Özel korumalı](./private-protected.md) </span><span class="sxs-lookup"><span data-stu-id="84edf-117">[Private Protected](./private-protected.md) </span></span>  
[<span data-ttu-id="84edf-118">Visual Basic'de erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="84edf-118">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
[<span data-ttu-id="84edf-119">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="84edf-119">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
[<span data-ttu-id="84edf-120">Yapılar</span><span class="sxs-lookup"><span data-stu-id="84edf-120">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
[<span data-ttu-id="84edf-121">Nesneler ve Sınıflar</span><span class="sxs-lookup"><span data-stu-id="84edf-121">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
