---
title: Protected Friend
ms.date: 05/10/2018
f1_keywords:
- vb.ProtectedFriend
helpviewer_keywords:
- Protected Friend keyword [Visual Basic]
- Protected Friend keyword [Visual Basic], syntax
ms.openlocfilehash: 27fc993ca0b94d406261d5e6275de8cd619eb6a8
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303458"
---
# <a name="protected-friend-visual-basic"></a><span data-ttu-id="950c2-102">Korumalı arkadaş (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="950c2-102">Protected Friend (Visual Basic)</span></span>

<span data-ttu-id="950c2-103">`Protected Friend`Anahtar sözcük birleşimi bir üye erişim değiştiricisidir.</span><span class="sxs-lookup"><span data-stu-id="950c2-103">The `Protected Friend` keyword combination is a member access modifier.</span></span> <span data-ttu-id="950c2-104">Hem [arkadaş](friend.md) erişimi hem de tanımlı öğeler üzerinde [korumalı](protected.md) erişimi, bu nedenle aynı derlemede, kendi sınıflarından ve türetilmiş sınıflardan erişilebilen her yerde erişilebilir hale gelir.</span><span class="sxs-lookup"><span data-stu-id="950c2-104">It confers both [Friend](friend.md) access and [Protected](protected.md) access on the declared elements, so they are accessible from anywhere in the same assembly, from their own class, and from derived classes.</span></span> <span data-ttu-id="950c2-105">`Protected Friend`Yalnızca sınıfların üyelerinde belirtebilirsiniz; `Protected Friend` yapılar devralınamadığı için bir yapının üyelerine uygulayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="950c2-105">You can specify `Protected Friend` only on members of classes; you cannot apply `Protected Friend` to members of a structure because structures cannot be inherited.</span></span>

> [!NOTE]
> <span data-ttu-id="950c2-106">Visual Studio 'da F1 Yardımı ' nı seçmek, `protected friend` [korumalı](protected.md) veya [arkadaş](friend.md)için yardım sağlar.</span><span class="sxs-lookup"><span data-stu-id="950c2-106">In Visual Studio, selecting F1 help on `protected friend` provides help for either [protected](protected.md) or [friend](friend.md).</span></span> <span data-ttu-id="950c2-107">IDE, bileşik sözcük yerine imleç altında tek belirteci seçer.</span><span class="sxs-lookup"><span data-stu-id="950c2-107">The IDE picks the single token under the cursor rather than the compound word.</span></span>

## <a name="rules"></a><span data-ttu-id="950c2-108">Kurallar</span><span class="sxs-lookup"><span data-stu-id="950c2-108">Rules</span></span>

<span data-ttu-id="950c2-109">**Bildirim bağlamı.**</span><span class="sxs-lookup"><span data-stu-id="950c2-109">**Declaration Context.**</span></span> <span data-ttu-id="950c2-110">`Protected Friend`Yalnızca sınıf düzeyinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="950c2-110">You can use `Protected Friend` only at the class level.</span></span> <span data-ttu-id="950c2-111">Yani bir öğe için bildirim bağlamı `Protected` bir sınıf olmalıdır ve kaynak dosya, ad alanı, arabirim, modül, yapı veya yordam olamaz.</span><span class="sxs-lookup"><span data-stu-id="950c2-111">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>

## <a name="see-also"></a><span data-ttu-id="950c2-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="950c2-112">See also</span></span>

- [<span data-ttu-id="950c2-113">Geneldir</span><span class="sxs-lookup"><span data-stu-id="950c2-113">Public</span></span>](public.md)
- [<span data-ttu-id="950c2-114">Korunamadı</span><span class="sxs-lookup"><span data-stu-id="950c2-114">Protected</span></span>](protected.md)
- [<span data-ttu-id="950c2-115">Dost</span><span class="sxs-lookup"><span data-stu-id="950c2-115">Friend</span></span>](friend.md)
- [<span data-ttu-id="950c2-116">Özel</span><span class="sxs-lookup"><span data-stu-id="950c2-116">Private</span></span>](private.md)
- [<span data-ttu-id="950c2-117">Özel korumalı</span><span class="sxs-lookup"><span data-stu-id="950c2-117">Private Protected</span></span>](./private-protected.md)
- [<span data-ttu-id="950c2-118">Visual Basic erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="950c2-118">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="950c2-119">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="950c2-119">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="950c2-120">Yapılar</span><span class="sxs-lookup"><span data-stu-id="950c2-120">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="950c2-121">Nesneler ve sınıflar</span><span class="sxs-lookup"><span data-stu-id="950c2-121">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
