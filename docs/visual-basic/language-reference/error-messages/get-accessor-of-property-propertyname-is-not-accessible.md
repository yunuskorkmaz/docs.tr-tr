---
title: "'<propertyname>' özelliğinin 'Get' erişimcisine erişilemiyor"
ms.date: 07/20/2015
f1_keywords:
- vbc31103
- bc31103
helpviewer_keywords:
- BC31103
ms.assetid: 3c346c32-7669-4b04-841d-7a9df9cb703e
ms.openlocfilehash: 92cc6d732b59617a6043bd71a9549649ff1ad356
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662053"
---
# <a name="get-accessor-of-property-propertyname-is-not-accessible"></a><span data-ttu-id="05c6a-102">' Özelliğinin'get ' erişimcisine '\<propertyname >' erişilebilir değil</span><span class="sxs-lookup"><span data-stu-id="05c6a-102">'Get' accessor of property '\<propertyname>' is not accessible</span></span>
<span data-ttu-id="05c6a-103">Özelliğin erişimi olmadığında bir özelliğin değerini almak bir deyim çalışır `Get` yordamı.</span><span class="sxs-lookup"><span data-stu-id="05c6a-103">A statement attempts to retrieve the value of a property when it does not have access to the property's `Get` procedure.</span></span>  
  
 <span data-ttu-id="05c6a-104">Varsa [alma deyimi](../../../visual-basic/language-reference/statements/get-statement.md) ile daha kısıtlayıcı bir erişim düzeyi daha işaretlenmiş kendi [Property deyimi](../../../visual-basic/language-reference/statements/property-statement.md), aşağıdaki durumlarda özellik değerini okuma girişimi başarısız olabilir:</span><span class="sxs-lookup"><span data-stu-id="05c6a-104">If the [Get Statement](../../../visual-basic/language-reference/statements/get-statement.md) is marked with a more restrictive access level than its [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md), an attempt to read the property value could fail in the following cases:</span></span>  
  
- <span data-ttu-id="05c6a-105">`Get` Deyimi işaretlenmiş [özel](../../../visual-basic/language-reference/modifiers/private.md) ve çağrıldığı koda bir sınıf veya yapı özelliği tanımlanır dışında.</span><span class="sxs-lookup"><span data-stu-id="05c6a-105">The `Get` statement is marked [Private](../../../visual-basic/language-reference/modifiers/private.md) and the calling code is outside the class or structure in which the property is defined.</span></span>  
  
- <span data-ttu-id="05c6a-106">`Get` Deyimi işaretlenmiş [korumalı](../../../visual-basic/language-reference/modifiers/protected.md) ve çağıran kod değil, sınıf veya yapı özelliği tanımlanır, ya da türetilen bir sınıfta değil.</span><span class="sxs-lookup"><span data-stu-id="05c6a-106">The `Get` statement is marked [Protected](../../../visual-basic/language-reference/modifiers/protected.md) and the calling code is not in the class or structure in which the property is defined, nor in a derived class.</span></span>  
  
- <span data-ttu-id="05c6a-107">`Get` Deyimi işaretlenmiş [arkadaş](../../../visual-basic/language-reference/modifiers/friend.md) ve çağıran kod özelliği tanımlanır derlemede değil.</span><span class="sxs-lookup"><span data-stu-id="05c6a-107">The `Get` statement is marked [Friend](../../../visual-basic/language-reference/modifiers/friend.md) and the calling code is not in the same assembly in which the property is defined.</span></span>  
  
 <span data-ttu-id="05c6a-108">**Hata Kimliği:** BC31103</span><span class="sxs-lookup"><span data-stu-id="05c6a-108">**Error ID:** BC31103</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="05c6a-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="05c6a-109">To correct this error</span></span>  
  
- <span data-ttu-id="05c6a-110">Özellik tanımlama kaynak kodu denetim varsa bildirmeyi göz önünde bulundurun `Get` yordamla aynı erişim düzeyi özelliği olarak.</span><span class="sxs-lookup"><span data-stu-id="05c6a-110">If you have control of the source code defining the property, consider declaring the `Get` procedure with the same access level as the property itself.</span></span>  
  
- <span data-ttu-id="05c6a-111">Özellik tanımlama kaynak kodu denetim sahibi olmadığınız ya da kısıtlamanız gerekir `Get` yordamı erişim düzeyi özelliği kendisini deneyin birden fazla özellik değeri daha iyi erişimi olan bir bölge kodu okuyan deyim taşımak özellik.</span><span class="sxs-lookup"><span data-stu-id="05c6a-111">If you do not have control of the source code defining the property, or you must restrict the `Get` procedure access level more than the property itself, try to move the statement that reads the property value to a region of code that has better access to the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05c6a-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="05c6a-112">See also</span></span>

- [<span data-ttu-id="05c6a-113">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="05c6a-113">Property Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
- [<span data-ttu-id="05c6a-114">Nasıl yapılır: Bir özelliği karışık erişim düzeyleriyle bildirme</span><span class="sxs-lookup"><span data-stu-id="05c6a-114">How to: Declare a Property with Mixed Access Levels</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
