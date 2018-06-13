---
title: '&#39;Ayarlama&#39; özelliği erişimcisi &#39; &lt;propertyname&gt; &#39; erişilebilir değil'
ms.date: 07/20/2015
f1_keywords:
- vbc31102
- bc31102
helpviewer_keywords:
- BC31102
ms.assetid: 6f7b31b7-3656-4ae1-8851-90f5f4c6950a
ms.openlocfilehash: d047d03755de89d4740482db4845d5db72003ac0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33595858"
---
# <a name="39set39-accessor-of-property-39ltpropertynamegt39-is-not-accessible"></a><span data-ttu-id="d001b-102">&#39;Ayarlama&#39; özelliği erişimcisi &#39; &lt;propertyname&gt; &#39; erişilebilir değil</span><span class="sxs-lookup"><span data-stu-id="d001b-102">&#39;Set&#39; accessor of property &#39;&lt;propertyname&gt;&#39; is not accessible</span></span>
<span data-ttu-id="d001b-103">Özelliğin erişimi olmadığında bir özelliğin değerini depolamak bir deyim çalışır `Set` yordamı.</span><span class="sxs-lookup"><span data-stu-id="d001b-103">A statement attempts to store the value of a property when it does not have access to the property's `Set` procedure.</span></span>  
  
 <span data-ttu-id="d001b-104">Varsa [Set deyimi](../../../visual-basic/language-reference/statements/set-statement.md) daha kısıtlayıcı bir erişimle daha düzeyi işaretlenmiş kendi [Property deyimi](../../../visual-basic/language-reference/statements/property-statement.md), aşağıdaki durumlarda özellik değerini ayarlama girişimi başarısız olabilir:</span><span class="sxs-lookup"><span data-stu-id="d001b-104">If the [Set Statement](../../../visual-basic/language-reference/statements/set-statement.md) is marked with a more restrictive access level than its [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md), an attempt to set the property value could fail in the following cases:</span></span>  
  
-   <span data-ttu-id="d001b-105">`Set` Deyimi işaretlenmiş [özel](../../../visual-basic/language-reference/modifiers/private.md) ve arama sınıf veya yapı özelliği tanımlanır dışında kodudur.</span><span class="sxs-lookup"><span data-stu-id="d001b-105">The `Set` statement is marked [Private](../../../visual-basic/language-reference/modifiers/private.md) and the calling code is outside the class or structure in which the property is defined.</span></span>  
  
-   <span data-ttu-id="d001b-106">`Set` Deyimi işaretlenmiş [korumalı](../../../visual-basic/language-reference/modifiers/protected.md) ve çağıran kodun sınıf veya özellik tanımlanır yapı içinde değil veya türetilmiş bir sınıf içinde değil.</span><span class="sxs-lookup"><span data-stu-id="d001b-106">The `Set` statement is marked [Protected](../../../visual-basic/language-reference/modifiers/protected.md) and the calling code is not in the class or structure in which the property is defined, nor in a derived class.</span></span>  
  
-   <span data-ttu-id="d001b-107">`Set` Deyimi işaretlenmiş [arkadaş](../../../visual-basic/language-reference/modifiers/friend.md) ve çağrıyı yapan kod özelliği tanımlanır aynı bütünleştirilmiş kodda değil.</span><span class="sxs-lookup"><span data-stu-id="d001b-107">The `Set` statement is marked [Friend](../../../visual-basic/language-reference/modifiers/friend.md) and the calling code is not in the same assembly in which the property is defined.</span></span>  
  
 <span data-ttu-id="d001b-108">**Hata Kimliği:** BC31102</span><span class="sxs-lookup"><span data-stu-id="d001b-108">**Error ID:** BC31102</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d001b-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="d001b-109">To correct this error</span></span>  
  
-   <span data-ttu-id="d001b-110">Denetim özellik tanımlama kaynak kodu varsa, bildirme göz önünde bulundurun `Set` özelliği olarak aynı erişim düzeyini yordamı.</span><span class="sxs-lookup"><span data-stu-id="d001b-110">If you have control of the source code defining the property, consider declaring the `Set` procedure with the same access level as the property itself.</span></span>  
  
-   <span data-ttu-id="d001b-111">Özellik tanımlama kaynak kodu denetimi yok ya da kısıtlamanız gerekir `Set` yordamı erişim düzeyine özelliği kendisini deneyin birden fazla özellik değeri bir bölgeye daha iyi erişimi olan kod ayarlar deyimi taşımak özellik.</span><span class="sxs-lookup"><span data-stu-id="d001b-111">If you do not have control of the source code defining the property, or you must restrict the `Set` procedure access level more than the property itself, try to move the statement that sets the property value to a region of code that has better access to the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d001b-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d001b-112">See Also</span></span>  
 [<span data-ttu-id="d001b-113">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="d001b-113">Property Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)  
 [<span data-ttu-id="d001b-114">Nasıl yapılır: Bir Özelliği Karışık Erişim Düzeyleriyle Bildirme</span><span class="sxs-lookup"><span data-stu-id="d001b-114">How to: Declare a Property with Mixed Access Levels</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
