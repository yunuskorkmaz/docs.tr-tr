---
title: Protected Friend
ms.date: 05/10/2018
helpviewer_keywords:
- Protected Friend keyword [Visual Basic]
- Protected Friend keyword [Visual Basic], syntax
ms.openlocfilehash: f92021f5f0dab9762470c270bdd5182187d587e5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351317"
---
# <a name="protected-friend-visual-basic"></a><span data-ttu-id="e65e0-102">Korumalı arkadaş (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e65e0-102">Protected Friend (Visual Basic)</span></span>

<span data-ttu-id="e65e0-103">`Protected Friend` anahtar sözcük birleşimi bir üye erişim değiştiricisidir.</span><span class="sxs-lookup"><span data-stu-id="e65e0-103">The `Protected Friend` keyword combination is a member access modifier.</span></span> <span data-ttu-id="e65e0-104">Hem [arkadaş](friend.md) erişimi hem de tanımlı öğeler üzerinde [korumalı](protected.md) erişimi, bu nedenle aynı derlemede, kendi sınıflarından ve türetilmiş sınıflardan erişilebilen her yerde erişilebilir hale gelir.</span><span class="sxs-lookup"><span data-stu-id="e65e0-104">It confers both [Friend](friend.md) access and [Protected](protected.md) access on the declared elements, so they are accessible from anywhere in the same assembly, from their own class, and from derived classes.</span></span> <span data-ttu-id="e65e0-105">Yalnızca sınıfların üyelerinde `Protected Friend` belirtebilirsiniz; yapılar devralınamadığı için `Protected Friend` bir yapının üyelerine uygulayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="e65e0-105">You can specify `Protected Friend` only on members of classes; you cannot apply `Protected Friend` to members of a structure because structures cannot be inherited.</span></span>

> [!NOTE]
> <span data-ttu-id="e65e0-106">Visual Studio 'da F1 Yardımı ' nı seçmek `protected friend` [korumalı](protected.md) veya [arkadaş](friend.md)için yardım sağlar.</span><span class="sxs-lookup"><span data-stu-id="e65e0-106">In Visual Studio, selecting F1 help on `protected friend` provides help for either [protected](protected.md) or [friend](friend.md).</span></span> <span data-ttu-id="e65e0-107">IDE, bileşik sözcük yerine imleç altında tek belirteci seçer.</span><span class="sxs-lookup"><span data-stu-id="e65e0-107">The IDE picks the single token under the cursor rather than the compound word.</span></span>

## <a name="rules"></a><span data-ttu-id="e65e0-108">Kurallar</span><span class="sxs-lookup"><span data-stu-id="e65e0-108">Rules</span></span>

<span data-ttu-id="e65e0-109">**Bildirim bağlamı.**</span><span class="sxs-lookup"><span data-stu-id="e65e0-109">**Declaration Context.**</span></span> <span data-ttu-id="e65e0-110">`Protected Friend` yalnızca sınıf düzeyinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e65e0-110">You can use `Protected Friend` only at the class level.</span></span> <span data-ttu-id="e65e0-111">Yani, bir `Protected` öğesi için bildirim bağlamı bir sınıf olmalıdır ve kaynak dosya, ad alanı, arabirim, modül, yapı veya yordam olamaz.</span><span class="sxs-lookup"><span data-stu-id="e65e0-111">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>

## <a name="see-also"></a><span data-ttu-id="e65e0-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e65e0-112">See also</span></span>

- [<span data-ttu-id="e65e0-113">Public</span><span class="sxs-lookup"><span data-stu-id="e65e0-113">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="e65e0-114">Protected</span><span class="sxs-lookup"><span data-stu-id="e65e0-114">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)
- [<span data-ttu-id="e65e0-115">Friend</span><span class="sxs-lookup"><span data-stu-id="e65e0-115">Friend</span></span>](friend.md)
- [<span data-ttu-id="e65e0-116">Private</span><span class="sxs-lookup"><span data-stu-id="e65e0-116">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="e65e0-117">Private Protected</span><span class="sxs-lookup"><span data-stu-id="e65e0-117">Private Protected</span></span>](./private-protected.md)
- [<span data-ttu-id="e65e0-118">Visual Basic erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="e65e0-118">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="e65e0-119">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="e65e0-119">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="e65e0-120">Yapılar</span><span class="sxs-lookup"><span data-stu-id="e65e0-120">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="e65e0-121">Nesneler ve Sınıflar</span><span class="sxs-lookup"><span data-stu-id="e65e0-121">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
