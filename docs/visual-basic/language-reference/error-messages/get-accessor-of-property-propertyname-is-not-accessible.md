---
title: "&#39; Al &#39; erişimci özelliği &#39; &lt;propertyname&gt;&#39; erişilebilir değil"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31103
- bc31103
helpviewer_keywords:
- BC31103
ms.assetid: 3c346c32-7669-4b04-841d-7a9df9cb703e
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 167e040570af1fc78ce48f5e930e54981ba909ae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="39get39-accessor-of-property-39ltpropertynamegt39-is-not-accessible"></a><span data-ttu-id="3a3a0-102">&#39; Al &#39; erişimci özelliği &#39; &lt;propertyname&gt;&#39; erişilebilir değil</span><span class="sxs-lookup"><span data-stu-id="3a3a0-102">&#39;Get&#39; accessor of property &#39;&lt;propertyname&gt;&#39; is not accessible</span></span>
<span data-ttu-id="3a3a0-103">Bir deyim özelliğin erişimi olmadığında bir özelliğin değerini almaya çalışır `Get` yordamı.</span><span class="sxs-lookup"><span data-stu-id="3a3a0-103">A statement attempts to retrieve the value of a property when it does not have access to the property's `Get` procedure.</span></span>  
  
 <span data-ttu-id="3a3a0-104">Varsa [alma deyimi](../../../visual-basic/language-reference/statements/get-statement.md) daha kısıtlayıcı bir erişimle daha düzeyi işaretlenmiş kendi [Property deyimi](../../../visual-basic/language-reference/statements/property-statement.md), aşağıdaki durumlarda özellik değerini okuma girişimi başarısız olabilir:</span><span class="sxs-lookup"><span data-stu-id="3a3a0-104">If the [Get Statement](../../../visual-basic/language-reference/statements/get-statement.md) is marked with a more restrictive access level than its [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md), an attempt to read the property value could fail in the following cases:</span></span>  
  
-   <span data-ttu-id="3a3a0-105">`Get` Deyimi işaretlenmiş [özel](../../../visual-basic/language-reference/modifiers/private.md) ve arama sınıf veya yapı özelliği tanımlanır dışında kodudur.</span><span class="sxs-lookup"><span data-stu-id="3a3a0-105">The `Get` statement is marked [Private](../../../visual-basic/language-reference/modifiers/private.md) and the calling code is outside the class or structure in which the property is defined.</span></span>  
  
-   <span data-ttu-id="3a3a0-106">`Get` Deyimi işaretlenmiş [korumalı](../../../visual-basic/language-reference/modifiers/protected.md) ve çağıran kodun sınıf veya özellik tanımlanır yapı içinde değil veya türetilmiş bir sınıf içinde değil.</span><span class="sxs-lookup"><span data-stu-id="3a3a0-106">The `Get` statement is marked [Protected](../../../visual-basic/language-reference/modifiers/protected.md) and the calling code is not in the class or structure in which the property is defined, nor in a derived class.</span></span>  
  
-   <span data-ttu-id="3a3a0-107">`Get` Deyimi işaretlenmiş [arkadaş](../../../visual-basic/language-reference/modifiers/friend.md) ve çağrıyı yapan kod özelliği tanımlanır aynı bütünleştirilmiş kodda değil.</span><span class="sxs-lookup"><span data-stu-id="3a3a0-107">The `Get` statement is marked [Friend](../../../visual-basic/language-reference/modifiers/friend.md) and the calling code is not in the same assembly in which the property is defined.</span></span>  
  
 <span data-ttu-id="3a3a0-108">**Hata Kimliği:** BC31103</span><span class="sxs-lookup"><span data-stu-id="3a3a0-108">**Error ID:** BC31103</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3a3a0-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="3a3a0-109">To correct this error</span></span>  
  
-   <span data-ttu-id="3a3a0-110">Denetim özellik tanımlama kaynak kodu varsa, bildirme göz önünde bulundurun `Get` özelliği olarak aynı erişim düzeyini yordamı.</span><span class="sxs-lookup"><span data-stu-id="3a3a0-110">If you have control of the source code defining the property, consider declaring the `Get` procedure with the same access level as the property itself.</span></span>  
  
-   <span data-ttu-id="3a3a0-111">Özellik tanımlama kaynak kodu denetimi yok ya da kısıtlamanız gerekir `Get` yordamı erişim düzeyine özelliği kendisini deneyin birden çok daha iyi erişimi olan bir bölge kodu için özellik değeri okuyan deyimi taşımak özellik.</span><span class="sxs-lookup"><span data-stu-id="3a3a0-111">If you do not have control of the source code defining the property, or you must restrict the `Get` procedure access level more than the property itself, try to move the statement that reads the property value to a region of code that has better access to the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a3a0-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3a3a0-112">See Also</span></span>  
 [<span data-ttu-id="3a3a0-113">Özellik yordamları</span><span class="sxs-lookup"><span data-stu-id="3a3a0-113">Property Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)  
 [<span data-ttu-id="3a3a0-114">Nasıl yapılır: bir özelliği karışık erişim düzeyleriyle bildirme</span><span class="sxs-lookup"><span data-stu-id="3a3a0-114">How to: Declare a Property with Mixed Access Levels</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
