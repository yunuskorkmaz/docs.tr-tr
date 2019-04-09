---
title: Korumalı arkadaş (Visual Basic)
ms.date: 05/10/2018
helpviewer_keywords:
- Protected Friend keyword [Visual Basic]
- Protected Friend keyword [Visual Basic], syntax
ms.openlocfilehash: 331c63dc290d4096e8158f265ee869b47743a273
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59151781"
---
# <a name="protected-friend-visual-basic"></a><span data-ttu-id="e2238-102">Korumalı arkadaş (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e2238-102">Protected Friend (Visual Basic)</span></span>

<span data-ttu-id="e2238-103">`Protected Friend` Anahtar sözcüğü bir üye erişim değiştiricisi oluşur.</span><span class="sxs-lookup"><span data-stu-id="e2238-103">The `Protected Friend` keyword combination is a member access modifier.</span></span> <span data-ttu-id="e2238-104">Her ikisi de confers [arkadaş](friend.md) erişim ve [korumalı](protected.md) kendi sınıf ve türetilen sınıflar aynı derlemenin başka bir yerindeki erişilebilir olduklarından bildirilmiş öğelere erişimi.</span><span class="sxs-lookup"><span data-stu-id="e2238-104">It confers both [Friend](friend.md) access and [Protected](protected.md) access on the declared elements, so they are accessible from anywhere in the same assembly, from their own class, and from derived classes.</span></span> <span data-ttu-id="e2238-105">Belirtebileceğiniz `Protected Friend` yalnızca; sınıfların üyeleri üzerinde uygulayamazsınız `Protected Friend` bir yapının üyelerine yapıları devraldığından.</span><span class="sxs-lookup"><span data-stu-id="e2238-105">You can specify `Protected Friend` only on members of classes; you cannot apply `Protected Friend` to members of a structure because structures cannot be inherited.</span></span>

> [!NOTE]
> <span data-ttu-id="e2238-106">Visual Studio'da F1 Yardımı seçme `protected friend` ya da Yardım sağlayan [korumalı](protected.md) veya [arkadaş](friend.md).</span><span class="sxs-lookup"><span data-stu-id="e2238-106">In Visual Studio, selecting F1 help on `protected friend` provides help for either [protected](protected.md) or [friend](friend.md).</span></span> <span data-ttu-id="e2238-107">IDE bileşik sözcüğü yerine imleç altında tek belirteç seçer.</span><span class="sxs-lookup"><span data-stu-id="e2238-107">The IDE picks the single token under the cursor rather than the compound word.</span></span>

## <a name="rules"></a><span data-ttu-id="e2238-108">Kurallar</span><span class="sxs-lookup"><span data-stu-id="e2238-108">Rules</span></span>

- **<span data-ttu-id="e2238-109">Bildirim bağlamı.</span><span class="sxs-lookup"><span data-stu-id="e2238-109">Declaration Context.</span></span>** <span data-ttu-id="e2238-110">Kullanabileceğiniz `Protected Friend` yalnızca sınıf düzeyinde.</span><span class="sxs-lookup"><span data-stu-id="e2238-110">You can use `Protected Friend` only at the class level.</span></span> <span data-ttu-id="e2238-111">Bildirim bağlamı başka bir deyişle bir `Protected` öğesi bir sınıf olması gerekir ve bir kaynak dosyası, ad alanı, arabirim, modülü, yapı veya yordamı olamaz.</span><span class="sxs-lookup"><span data-stu-id="e2238-111">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span> 

## <a name="see-also"></a><span data-ttu-id="e2238-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e2238-112">See also</span></span>

- [<span data-ttu-id="e2238-113">Ortak</span><span class="sxs-lookup"><span data-stu-id="e2238-113">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="e2238-114">Korumalı</span><span class="sxs-lookup"><span data-stu-id="e2238-114">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)
- [<span data-ttu-id="e2238-115">Arkadaş</span><span class="sxs-lookup"><span data-stu-id="e2238-115">Friend</span></span>](friend.md)
- [<span data-ttu-id="e2238-116">Özel</span><span class="sxs-lookup"><span data-stu-id="e2238-116">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="e2238-117">Özel korumalı</span><span class="sxs-lookup"><span data-stu-id="e2238-117">Private Protected</span></span>](./private-protected.md)
- [<span data-ttu-id="e2238-118">Visual Basic'de erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="e2238-118">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="e2238-119">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="e2238-119">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="e2238-120">Yapılar</span><span class="sxs-lookup"><span data-stu-id="e2238-120">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="e2238-121">Nesneler ve Sınıflar</span><span class="sxs-lookup"><span data-stu-id="e2238-121">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
