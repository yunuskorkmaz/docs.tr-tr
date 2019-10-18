---
title: Korumalı arkadaş (Visual Basic)
ms.date: 05/10/2018
helpviewer_keywords:
- Protected Friend keyword [Visual Basic]
- Protected Friend keyword [Visual Basic], syntax
ms.openlocfilehash: d3592feaece1d5ce85ee6e2657d8a2715c4097a3
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524780"
---
# <a name="protected-friend-visual-basic"></a><span data-ttu-id="a8fff-102">Korumalı arkadaş (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a8fff-102">Protected Friend (Visual Basic)</span></span>

<span data-ttu-id="a8fff-103">@No__t_0 anahtar sözcük birleşimi bir üye erişim değiştiricisidir.</span><span class="sxs-lookup"><span data-stu-id="a8fff-103">The `Protected Friend` keyword combination is a member access modifier.</span></span> <span data-ttu-id="a8fff-104">Hem [arkadaş](friend.md) erişimi hem de tanımlı öğeler üzerinde [korumalı](protected.md) erişimi, bu nedenle aynı derlemede, kendi sınıflarından ve türetilmiş sınıflardan erişilebilen her yerde erişilebilir hale gelir.</span><span class="sxs-lookup"><span data-stu-id="a8fff-104">It confers both [Friend](friend.md) access and [Protected](protected.md) access on the declared elements, so they are accessible from anywhere in the same assembly, from their own class, and from derived classes.</span></span> <span data-ttu-id="a8fff-105">Yalnızca sınıfların üyelerinde `Protected Friend` belirtebilirsiniz; yapılar devralınamadığı için `Protected Friend` bir yapının üyelerine uygulayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="a8fff-105">You can specify `Protected Friend` only on members of classes; you cannot apply `Protected Friend` to members of a structure because structures cannot be inherited.</span></span>

> [!NOTE]
> <span data-ttu-id="a8fff-106">Visual Studio 'da F1 Yardımı ' nı seçmek `protected friend` [korumalı](protected.md) veya [arkadaş](friend.md)için yardım sağlar.</span><span class="sxs-lookup"><span data-stu-id="a8fff-106">In Visual Studio, selecting F1 help on `protected friend` provides help for either [protected](protected.md) or [friend](friend.md).</span></span> <span data-ttu-id="a8fff-107">IDE, bileşik sözcük yerine imleç altında tek belirteci seçer.</span><span class="sxs-lookup"><span data-stu-id="a8fff-107">The IDE picks the single token under the cursor rather than the compound word.</span></span>

## <a name="rules"></a><span data-ttu-id="a8fff-108">Kurallar</span><span class="sxs-lookup"><span data-stu-id="a8fff-108">Rules</span></span>

<span data-ttu-id="a8fff-109">**Bildirim bağlamı.**</span><span class="sxs-lookup"><span data-stu-id="a8fff-109">**Declaration Context.**</span></span> <span data-ttu-id="a8fff-110">@No__t_0 yalnızca sınıf düzeyinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a8fff-110">You can use `Protected Friend` only at the class level.</span></span> <span data-ttu-id="a8fff-111">Yani, bir `Protected` öğesi için bildirim bağlamı bir sınıf olmalıdır ve kaynak dosya, ad alanı, arabirim, modül, yapı veya yordam olamaz.</span><span class="sxs-lookup"><span data-stu-id="a8fff-111">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>

## <a name="see-also"></a><span data-ttu-id="a8fff-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a8fff-112">See also</span></span>

- [<span data-ttu-id="a8fff-113">Public</span><span class="sxs-lookup"><span data-stu-id="a8fff-113">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="a8fff-114">Protected</span><span class="sxs-lookup"><span data-stu-id="a8fff-114">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)
- [<span data-ttu-id="a8fff-115">Friend</span><span class="sxs-lookup"><span data-stu-id="a8fff-115">Friend</span></span>](friend.md)
- [<span data-ttu-id="a8fff-116">Private</span><span class="sxs-lookup"><span data-stu-id="a8fff-116">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="a8fff-117">Private Protected</span><span class="sxs-lookup"><span data-stu-id="a8fff-117">Private Protected</span></span>](./private-protected.md)
- [<span data-ttu-id="a8fff-118">Visual Basic erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="a8fff-118">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="a8fff-119">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="a8fff-119">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="a8fff-120">Yapılar</span><span class="sxs-lookup"><span data-stu-id="a8fff-120">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="a8fff-121">Nesneler ve Sınıflar</span><span class="sxs-lookup"><span data-stu-id="a8fff-121">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
