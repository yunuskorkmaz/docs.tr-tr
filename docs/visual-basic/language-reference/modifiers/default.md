---
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
ms.openlocfilehash: ad4c9528f208cc2c31f07b0506d1b049a7568c86
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351578"
---
# <a name="default-visual-basic"></a><span data-ttu-id="cc4b3-102">Varsayılan (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cc4b3-102">Default (Visual Basic)</span></span>
<span data-ttu-id="cc4b3-103">Bir özelliği sınıfının, yapısının veya arabirimin varsayılan özelliği olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="cc4b3-103">Identifies a property as the default property of its class, structure, or interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cc4b3-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cc4b3-104">Remarks</span></span>  
 <span data-ttu-id="cc4b3-105">Bir sınıf, yapı veya arabirim, özelliğin en az bir parametre almasını sağlayan *varsayılan özellik*olarak özelliklerinden en çok birini belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="cc4b3-105">A class, structure, or interface can designate at most one of its properties as the *default property*, provided that property takes at least one parameter.</span></span> <span data-ttu-id="cc4b3-106">Kod, bir üye belirtmeden bir sınıfa veya yapıya bir başvuru yapıyorsa Visual Basic, bu başvuruyu varsayılan özelliğe çözer.</span><span class="sxs-lookup"><span data-stu-id="cc4b3-106">If code makes a reference to a class or structure without specifying a member, Visual Basic resolves that reference to the default property.</span></span>  
  
 <span data-ttu-id="cc4b3-107">Varsayılan Özellikler, kaynak kodu karakterlerinin küçük bir azalmasına neden olabilir, ancak kodunuzun okunmasını zorlaşabilir.</span><span class="sxs-lookup"><span data-stu-id="cc4b3-107">Default properties can result in a small reduction in source code-characters, but they can make your code more difficult to read.</span></span> <span data-ttu-id="cc4b3-108">Çağıran kod sınıfınız veya yapınız hakkında bilgi sahibi değilse, sınıf veya yapı adına bir başvuru yaptığında, başvurunun sınıfa veya yapıya ya da bir varsayılan özelliğe erişim izni verip etmediği kesin olamaz.</span><span class="sxs-lookup"><span data-stu-id="cc4b3-108">If the calling code is not familiar with your class or structure, when it makes a reference to the class or structure name it cannot be certain whether that reference accesses the class or structure itself, or a default property.</span></span> <span data-ttu-id="cc4b3-109">Bu, derleyici hatalarına veya hafif çalışma zamanı mantığı hatalarına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="cc4b3-109">This can lead to compiler errors or subtle run-time logic errors.</span></span>  
  
 <span data-ttu-id="cc4b3-110">Derleyici türü denetimini `On`olarak ayarlamak için, her zaman [katı bildiri seçeneğini](../../../visual-basic/language-reference/statements/option-strict-statement.md) kullanarak varsayılan özellik hatalarının olasılığını azaltabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cc4b3-110">You can somewhat reduce the chance of default property errors by always using the [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md) to set compiler type checking to `On`.</span></span>  
  
 <span data-ttu-id="cc4b3-111">Kodunuzda önceden tanımlanmış bir sınıf veya yapı kullanmayı planlıyorsanız, bunun varsayılan bir özelliği olup olmadığını ve varsa adının ne olduğunu belirlemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="cc4b3-111">If you are planning to use a predefined class or structure in your code, you must determine whether it has a default property, and if so, what its name is.</span></span>  
  
 <span data-ttu-id="cc4b3-112">Bu dezavantajlar nedeniyle varsayılan özellikleri tanımlamamalısınız.</span><span class="sxs-lookup"><span data-stu-id="cc4b3-112">Because of these disadvantages, you should consider not defining default properties.</span></span> <span data-ttu-id="cc4b3-113">Kod okunabilirlik için, her zaman tüm özelliklere, hatta varsayılan özelliklere de her zaman başvurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="cc4b3-113">For code readability, you should also consider always referring to all properties explicitly, even default properties.</span></span>  
  
 <span data-ttu-id="cc4b3-114">`Default` değiştiricisi Bu bağlamda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="cc4b3-114">The `Default` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="cc4b3-115">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="cc4b3-115">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="cc4b3-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cc4b3-116">See also</span></span>

- [<span data-ttu-id="cc4b3-117">Nasıl yapılır: Visual Basic varsayılan bir özellik bildirme ve çağırma</span><span class="sxs-lookup"><span data-stu-id="cc4b3-117">How to: Declare and Call a Default Property in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="cc4b3-118">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="cc4b3-118">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
