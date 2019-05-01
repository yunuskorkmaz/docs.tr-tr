---
title: "'<propertyname>' özelliğinin 'Set' erişimcisine erişilemiyor"
ms.date: 07/20/2015
f1_keywords:
- vbc31102
- bc31102
helpviewer_keywords:
- BC31102
ms.assetid: 6f7b31b7-3656-4ae1-8851-90f5f4c6950a
ms.openlocfilehash: 3bc50d6762998ca5d8f445d84c8b698c9f46436f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62055153"
---
# <a name="set-accessor-of-property-propertyname-is-not-accessible"></a><span data-ttu-id="e5784-102">'Set' erişimcisi'özelliğinin '\<propertyname >' erişilebilir değil</span><span class="sxs-lookup"><span data-stu-id="e5784-102">'Set' accessor of property '\<propertyname>' is not accessible</span></span>
<span data-ttu-id="e5784-103">Özelliğin erişimi olmadığında bir özellik değerini depolamak bir deyim çalışır `Set` yordamı.</span><span class="sxs-lookup"><span data-stu-id="e5784-103">A statement attempts to store the value of a property when it does not have access to the property's `Set` procedure.</span></span>  
  
 <span data-ttu-id="e5784-104">Varsa [bildirimine](../../../visual-basic/language-reference/statements/set-statement.md) ile daha kısıtlayıcı bir erişim düzeyi daha işaretlenmiş kendi [Property deyimi](../../../visual-basic/language-reference/statements/property-statement.md), aşağıdaki durumlarda özellik değerini ayarlama girişimi başarısız olabilir:</span><span class="sxs-lookup"><span data-stu-id="e5784-104">If the [Set Statement](../../../visual-basic/language-reference/statements/set-statement.md) is marked with a more restrictive access level than its [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md), an attempt to set the property value could fail in the following cases:</span></span>  
  
- <span data-ttu-id="e5784-105">`Set` Deyimi işaretlenmiş [özel](../../../visual-basic/language-reference/modifiers/private.md) ve çağrıldığı koda bir sınıf veya yapı özelliği tanımlanır dışında.</span><span class="sxs-lookup"><span data-stu-id="e5784-105">The `Set` statement is marked [Private](../../../visual-basic/language-reference/modifiers/private.md) and the calling code is outside the class or structure in which the property is defined.</span></span>  
  
- <span data-ttu-id="e5784-106">`Set` Deyimi işaretlenmiş [korumalı](../../../visual-basic/language-reference/modifiers/protected.md) ve çağıran kod değil, sınıf veya yapı özelliği tanımlanır, ya da türetilen bir sınıfta değil.</span><span class="sxs-lookup"><span data-stu-id="e5784-106">The `Set` statement is marked [Protected](../../../visual-basic/language-reference/modifiers/protected.md) and the calling code is not in the class or structure in which the property is defined, nor in a derived class.</span></span>  
  
- <span data-ttu-id="e5784-107">`Set` Deyimi işaretlenmiş [arkadaş](../../../visual-basic/language-reference/modifiers/friend.md) ve çağıran kod özelliği tanımlanır derlemede değil.</span><span class="sxs-lookup"><span data-stu-id="e5784-107">The `Set` statement is marked [Friend](../../../visual-basic/language-reference/modifiers/friend.md) and the calling code is not in the same assembly in which the property is defined.</span></span>  
  
 <span data-ttu-id="e5784-108">**Hata Kimliği:** BC31102</span><span class="sxs-lookup"><span data-stu-id="e5784-108">**Error ID:** BC31102</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e5784-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="e5784-109">To correct this error</span></span>  
  
- <span data-ttu-id="e5784-110">Özellik tanımlama kaynak kodu denetim varsa bildirmeyi göz önünde bulundurun `Set` yordamla aynı erişim düzeyi özelliği olarak.</span><span class="sxs-lookup"><span data-stu-id="e5784-110">If you have control of the source code defining the property, consider declaring the `Set` procedure with the same access level as the property itself.</span></span>  
  
- <span data-ttu-id="e5784-111">Özellik tanımlama kaynak kodu denetim sahibi olmadığınız ya da kısıtlamanız gerekir `Set` yordamı erişim düzeyi özelliği kendisini deneyin birden fazla özellik değeri, daha iyi erişimi olan kod bir bölgeye ayarlar deyimi taşımak özellik.</span><span class="sxs-lookup"><span data-stu-id="e5784-111">If you do not have control of the source code defining the property, or you must restrict the `Set` procedure access level more than the property itself, try to move the statement that sets the property value to a region of code that has better access to the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5784-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e5784-112">See also</span></span>

- [<span data-ttu-id="e5784-113">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="e5784-113">Property Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
- [<span data-ttu-id="e5784-114">Nasıl yapılır: Bir özelliği karışık erişim düzeyleriyle bildirme</span><span class="sxs-lookup"><span data-stu-id="e5784-114">How to: Declare a Property with Mixed Access Levels</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
