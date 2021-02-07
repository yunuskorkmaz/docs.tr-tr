---
description: ': WithEvents (Visual Basic) hakkında daha fazla bilgi'
title: WithEvents
ms.date: 07/20/2015
f1_keywords:
- vb.WithEvents
- WithEvents
helpviewer_keywords:
- WithEvents keyword [Visual Basic]
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
ms.openlocfilehash: b27f84fe54aaa10bc9b2359cd74fad3d3ace1ad5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99674772"
---
# <a name="withevents-visual-basic"></a><span data-ttu-id="8ea0f-103">WithEvents (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8ea0f-103">WithEvents (Visual Basic)</span></span>

<span data-ttu-id="8ea0f-104">Bir veya daha fazla tanımlanmış üye değişkeninin, olayları tetiklebilecek bir sınıfın örneğine başvurmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="8ea0f-104">Specifies that one or more declared member variables refer to an instance of a class that can raise events.</span></span>

## <a name="remarks"></a><span data-ttu-id="8ea0f-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8ea0f-105">Remarks</span></span>

<span data-ttu-id="8ea0f-106">Bir değişken kullanılarak tanımlandığında `WithEvents` , bir yöntemin anahtar sözcüğünü kullanarak değişkenin olaylarını işlediğini bildirimli olarak belirtebilirsiniz `Handles` .</span><span class="sxs-lookup"><span data-stu-id="8ea0f-106">When a variable is defined using `WithEvents`, you can declaratively specify that a method handles the variable's events using the `Handles` keyword.</span></span>

<span data-ttu-id="8ea0f-107">`WithEvents`Yalnızca sınıf veya modül düzeyinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ea0f-107">You can use `WithEvents` only at class or module level.</span></span> <span data-ttu-id="8ea0f-108">Diğer bir deyişle, bir değişken için bildirim bağlamı `WithEvents` bir sınıf veya modül olmalıdır ve kaynak dosya, ad alanı, yapı veya yordam olamaz.</span><span class="sxs-lookup"><span data-stu-id="8ea0f-108">This means the declaration context for a `WithEvents` variable must be a class or module and cannot be a source file, namespace, structure, or procedure.</span></span>

<span data-ttu-id="8ea0f-109">`WithEvents`Yapı üyesi üzerinde kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="8ea0f-109">You cannot use `WithEvents` on a structure member.</span></span>

<span data-ttu-id="8ea0f-110">İle yalnızca bağımsız değişkenleri (diziler değil) bildirebilirsiniz `WithEvents` .</span><span class="sxs-lookup"><span data-stu-id="8ea0f-110">You can declare only individual variables—not arrays—with `WithEvents`.</span></span>

## <a name="rules"></a><span data-ttu-id="8ea0f-111">Kurallar</span><span class="sxs-lookup"><span data-stu-id="8ea0f-111">Rules</span></span>

<span data-ttu-id="8ea0f-112">**Öğe türleri.**</span><span class="sxs-lookup"><span data-stu-id="8ea0f-112">**Element Types.**</span></span> <span data-ttu-id="8ea0f-113">`WithEvents`Değişkenleri, sınıf örneklerini kabul edebilecek şekilde nesne değişkenleri olacak şekilde bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8ea0f-113">You must declare `WithEvents` variables to be object variables so that they can accept class instances.</span></span> <span data-ttu-id="8ea0f-114">Ancak, bunları olarak bildiremezsiniz `Object` .</span><span class="sxs-lookup"><span data-stu-id="8ea0f-114">However, you cannot declare them as `Object`.</span></span> <span data-ttu-id="8ea0f-115">Bunları, olayları yükseltebilen belirli bir sınıf olarak bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8ea0f-115">You must declare them as the specific class that can raise the events.</span></span>

<span data-ttu-id="8ea0f-116">`WithEvents`Değiştirici Bu bağlamda kullanılabilir: [Dim ekstresi](../statements/dim-statement.md)</span><span class="sxs-lookup"><span data-stu-id="8ea0f-116">The `WithEvents` modifier can be used in this context: [Dim Statement](../statements/dim-statement.md)</span></span>

## <a name="example"></a><span data-ttu-id="8ea0f-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="8ea0f-117">Example</span></span>

```vb
Dim WithEvents app As Application
```

## <a name="see-also"></a><span data-ttu-id="8ea0f-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8ea0f-118">See also</span></span>

- [<span data-ttu-id="8ea0f-119">Handles</span><span class="sxs-lookup"><span data-stu-id="8ea0f-119">Handles</span></span>](../statements/handles-clause.md)
- [<span data-ttu-id="8ea0f-120">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="8ea0f-120">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="8ea0f-121">Ekinlikler</span><span class="sxs-lookup"><span data-stu-id="8ea0f-121">Events</span></span>](../../programming-guide/language-features/events/index.md)
