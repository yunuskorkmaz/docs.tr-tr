---
title: WithEvents
ms.date: 07/20/2015
f1_keywords:
- vb.WithEvents
- WithEvents
helpviewer_keywords:
- WithEvents keyword [Visual Basic]
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
ms.openlocfilehash: 48261e27de302c1809c9725e6e2fc0705a803930
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84386782"
---
# <a name="withevents-visual-basic"></a><span data-ttu-id="e2a07-102">WithEvents (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e2a07-102">WithEvents (Visual Basic)</span></span>
<span data-ttu-id="e2a07-103">Bir veya daha fazla tanımlanmış üye değişkeninin, olayları tetiklebilecek bir sınıfın örneğine başvurmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e2a07-103">Specifies that one or more declared member variables refer to an instance of a class that can raise events.</span></span>

## <a name="remarks"></a><span data-ttu-id="e2a07-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e2a07-104">Remarks</span></span>

<span data-ttu-id="e2a07-105">Bir değişken kullanılarak tanımlandığında `WithEvents` , bir yöntemin anahtar sözcüğünü kullanarak değişkenin olaylarını işlediğini bildirimli olarak belirtebilirsiniz `Handles` .</span><span class="sxs-lookup"><span data-stu-id="e2a07-105">When a variable is defined using `WithEvents`, you can declaratively specify that a method handles the variable's events using the `Handles` keyword.</span></span>

<span data-ttu-id="e2a07-106">`WithEvents`Yalnızca sınıf veya modül düzeyinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e2a07-106">You can use `WithEvents` only at class or module level.</span></span> <span data-ttu-id="e2a07-107">Diğer bir deyişle, bir değişken için bildirim bağlamı `WithEvents` bir sınıf veya modül olmalıdır ve kaynak dosya, ad alanı, yapı veya yordam olamaz.</span><span class="sxs-lookup"><span data-stu-id="e2a07-107">This means the declaration context for a `WithEvents` variable must be a class or module and cannot be a source file, namespace, structure, or procedure.</span></span>

<span data-ttu-id="e2a07-108">`WithEvents`Yapı üyesi üzerinde kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="e2a07-108">You cannot use `WithEvents` on a structure member.</span></span>

<span data-ttu-id="e2a07-109">İle yalnızca bağımsız değişkenleri (diziler değil) bildirebilirsiniz `WithEvents` .</span><span class="sxs-lookup"><span data-stu-id="e2a07-109">You can declare only individual variables—not arrays—with `WithEvents`.</span></span>

## <a name="rules"></a><span data-ttu-id="e2a07-110">Kurallar</span><span class="sxs-lookup"><span data-stu-id="e2a07-110">Rules</span></span>

<span data-ttu-id="e2a07-111">**Öğe türleri.**</span><span class="sxs-lookup"><span data-stu-id="e2a07-111">**Element Types.**</span></span> <span data-ttu-id="e2a07-112">`WithEvents`Değişkenleri, sınıf örneklerini kabul edebilecek şekilde nesne değişkenleri olacak şekilde bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e2a07-112">You must declare `WithEvents` variables to be object variables so that they can accept class instances.</span></span> <span data-ttu-id="e2a07-113">Ancak, bunları olarak bildiremezsiniz `Object` .</span><span class="sxs-lookup"><span data-stu-id="e2a07-113">However, you cannot declare them as `Object`.</span></span> <span data-ttu-id="e2a07-114">Bunları, olayları yükseltebilen belirli bir sınıf olarak bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e2a07-114">You must declare them as the specific class that can raise the events.</span></span>

<span data-ttu-id="e2a07-115">`WithEvents`Değiştirici Bu bağlamda kullanılabilir: [Dim ekstresi](../statements/dim-statement.md)</span><span class="sxs-lookup"><span data-stu-id="e2a07-115">The `WithEvents` modifier can be used in this context: [Dim Statement](../statements/dim-statement.md)</span></span>

## <a name="example"></a><span data-ttu-id="e2a07-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="e2a07-116">Example</span></span>

```vb
Dim WithEvents app As Application
```

## <a name="see-also"></a><span data-ttu-id="e2a07-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e2a07-117">See also</span></span>

- [<span data-ttu-id="e2a07-118">Handles</span><span class="sxs-lookup"><span data-stu-id="e2a07-118">Handles</span></span>](../statements/handles-clause.md)
- [<span data-ttu-id="e2a07-119">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="e2a07-119">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="e2a07-120">Olaylar</span><span class="sxs-lookup"><span data-stu-id="e2a07-120">Events</span></span>](../../programming-guide/language-features/events/index.md)
