---
description: 'Hakkında daha fazla bilgi: varsayılan (Visual Basic)'
title: Varsayılan
ms.date: 07/20/2015
f1_keywords:
- vb.Default
helpviewer_keywords:
- defaults, properties
- properties [Visual Basic], default
- default properties, in Visual Basic
- Default keyword [Visual Basic]
- default properties
ms.assetid: 45fce9b9-d212-4b2d-ab86-6e359b8b57af
ms.openlocfilehash: fe135df4f29ae3c4064c97d4f2789be7f4f3d8f9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99774609"
---
# <a name="default-visual-basic"></a><span data-ttu-id="b8a24-103">Varsayılan (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b8a24-103">Default (Visual Basic)</span></span>

<span data-ttu-id="b8a24-104">Bir özelliği sınıfının, yapısının veya arabirimin varsayılan özelliği olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b8a24-104">Identifies a property as the default property of its class, structure, or interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b8a24-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b8a24-105">Remarks</span></span>  

 <span data-ttu-id="b8a24-106">Bir sınıf, yapı veya arabirim, özelliğin en az bir parametre almasını sağlayan *varsayılan özellik* olarak özelliklerinden en çok birini belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="b8a24-106">A class, structure, or interface can designate at most one of its properties as the *default property*, provided that property takes at least one parameter.</span></span> <span data-ttu-id="b8a24-107">Kod, bir üye belirtmeden bir sınıfa veya yapıya bir başvuru yapıyorsa Visual Basic, bu başvuruyu varsayılan özelliğe çözer.</span><span class="sxs-lookup"><span data-stu-id="b8a24-107">If code makes a reference to a class or structure without specifying a member, Visual Basic resolves that reference to the default property.</span></span>  
  
 <span data-ttu-id="b8a24-108">Varsayılan Özellikler, kaynak kodu karakterlerinin küçük bir azalmasına neden olabilir, ancak kodunuzun okunmasını zorlaşabilir.</span><span class="sxs-lookup"><span data-stu-id="b8a24-108">Default properties can result in a small reduction in source code-characters, but they can make your code more difficult to read.</span></span> <span data-ttu-id="b8a24-109">Çağıran kod sınıfınız veya yapınız hakkında bilgi sahibi değilse, sınıf veya yapı adına bir başvuru yaptığında, başvurunun sınıfa veya yapıya ya da bir varsayılan özelliğe erişim izni verip etmediği kesin olamaz.</span><span class="sxs-lookup"><span data-stu-id="b8a24-109">If the calling code is not familiar with your class or structure, when it makes a reference to the class or structure name it cannot be certain whether that reference accesses the class or structure itself, or a default property.</span></span> <span data-ttu-id="b8a24-110">Bu, derleyici hatalarına veya hafif çalışma zamanı mantığı hatalarına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="b8a24-110">This can lead to compiler errors or subtle run-time logic errors.</span></span>  
  
 <span data-ttu-id="b8a24-111">Derleyici türü denetimini olarak ayarlamak için, her zaman [katı deyimin seçeneğini](../statements/option-strict-statement.md) kullanarak varsayılan özellik hatalarının olasılığını azaltabilirsiniz `On` .</span><span class="sxs-lookup"><span data-stu-id="b8a24-111">You can somewhat reduce the chance of default property errors by always using the [Option Strict Statement](../statements/option-strict-statement.md) to set compiler type checking to `On`.</span></span>  
  
 <span data-ttu-id="b8a24-112">Kodunuzda önceden tanımlanmış bir sınıf veya yapı kullanmayı planlıyorsanız, bunun varsayılan bir özelliği olup olmadığını ve varsa adının ne olduğunu belirlemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="b8a24-112">If you are planning to use a predefined class or structure in your code, you must determine whether it has a default property, and if so, what its name is.</span></span>  
  
 <span data-ttu-id="b8a24-113">Bu dezavantajlar nedeniyle varsayılan özellikleri tanımlamamalısınız.</span><span class="sxs-lookup"><span data-stu-id="b8a24-113">Because of these disadvantages, you should consider not defining default properties.</span></span> <span data-ttu-id="b8a24-114">Kod okunabilirlik için, her zaman tüm özelliklere, hatta varsayılan özelliklere de her zaman başvurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b8a24-114">For code readability, you should also consider always referring to all properties explicitly, even default properties.</span></span>  
  
 <span data-ttu-id="b8a24-115">`Default`Değiştirici Bu bağlamda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="b8a24-115">The `Default` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="b8a24-116">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="b8a24-116">Property Statement</span></span>](../statements/property-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="b8a24-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b8a24-117">See also</span></span>

- [<span data-ttu-id="b8a24-118">Nasıl yapılır: Visual Basic'de Varsayılan Bir Özelliği Bildirme ve Çağırma</span><span class="sxs-lookup"><span data-stu-id="b8a24-118">How to: Declare and Call a Default Property in Visual Basic</span></span>](../../programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="b8a24-119">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="b8a24-119">Keywords</span></span>](../keywords/index.md)
