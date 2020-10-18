---
title: "'<propertyname>' özelliğinin 'Get' erişimcisine erişilemiyor"
ms.date: 07/20/2015
f1_keywords:
- vbc31103
- bc31103
helpviewer_keywords:
- BC31103
ms.assetid: 3c346c32-7669-4b04-841d-7a9df9cb703e
ms.openlocfilehash: bd6830e16ba3d1f76c61519b4456832a2efec716
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162914"
---
# <a name="bc31103-get-accessor-of-property-propertyname-is-not-accessible"></a><span data-ttu-id="7f961-102">BC31103: ' ' özelliğinin ' Get ' erişimcisi \<propertyname> erişilebilir değil</span><span class="sxs-lookup"><span data-stu-id="7f961-102">BC31103: 'Get' accessor of property '\<propertyname>' is not accessible</span></span>

<span data-ttu-id="7f961-103">Bir ifade, özelliğin yordamına erişimi olmayan bir özelliğin değerini almaya çalışır `Get` .</span><span class="sxs-lookup"><span data-stu-id="7f961-103">A statement attempts to retrieve the value of a property when it does not have access to the property's `Get` procedure.</span></span>

 <span data-ttu-id="7f961-104">[Get deyiminden](../statements/get-statement.md) daha kısıtlayıcı bir erişim düzeyiyle [işaretlenmişse, özellik](../statements/property-statement.md)değerini okuma girişimi aşağıdaki durumlarda başarısız olabilir:</span><span class="sxs-lookup"><span data-stu-id="7f961-104">If the [Get Statement](../statements/get-statement.md) is marked with a more restrictive access level than its [Property Statement](../statements/property-statement.md), an attempt to read the property value could fail in the following cases:</span></span>

- <span data-ttu-id="7f961-105">`Get`Ifade [Private](../modifiers/private.md) olarak işaretlenir ve çağıran kod, özelliğin tanımlandığı sınıfın veya yapının dışındadır.</span><span class="sxs-lookup"><span data-stu-id="7f961-105">The `Get` statement is marked [Private](../modifiers/private.md) and the calling code is outside the class or structure in which the property is defined.</span></span>

- <span data-ttu-id="7f961-106">`Get`Ifade [korumalı](../modifiers/protected.md) olarak işaretlenir ve çağıran kod, özelliğin tanımlandığı sınıf veya yapı içinde ya da türetilmiş bir sınıfta değil.</span><span class="sxs-lookup"><span data-stu-id="7f961-106">The `Get` statement is marked [Protected](../modifiers/protected.md) and the calling code is not in the class or structure in which the property is defined, nor in a derived class.</span></span>

- <span data-ttu-id="7f961-107">`Get`Ifade [arkadaş](../modifiers/friend.md) olarak işaretlenmiş ve çağıran kod, özelliğin tanımlandığı derlemede değil.</span><span class="sxs-lookup"><span data-stu-id="7f961-107">The `Get` statement is marked [Friend](../modifiers/friend.md) and the calling code is not in the same assembly in which the property is defined.</span></span>

 <span data-ttu-id="7f961-108">**Hata kimliği:** BC31103</span><span class="sxs-lookup"><span data-stu-id="7f961-108">**Error ID:** BC31103</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="7f961-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="7f961-109">To correct this error</span></span>

- <span data-ttu-id="7f961-110">Özelliği tanımlayan kaynak kodun denetimine sahipseniz, `Get` yordamı özelliğin kendisiyle aynı erişim düzeyiyle bildirmeyi göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="7f961-110">If you have control of the source code defining the property, consider declaring the `Get` procedure with the same access level as the property itself.</span></span>

- <span data-ttu-id="7f961-111">Özelliği tanımlayan kaynak kodu denetimine sahip değilseniz veya `Get` yordam erişim düzeyini özelliğin kendisinden daha fazla kısıtlamanız gerekiyorsa, özellik değerini okuyan ifadeyi özelliğe daha iyi erişimi olan bir kod bölgesine taşımayı deneyin.</span><span class="sxs-lookup"><span data-stu-id="7f961-111">If you do not have control of the source code defining the property, or you must restrict the `Get` procedure access level more than the property itself, try to move the statement that reads the property value to a region of code that has better access to the property.</span></span>

## <a name="see-also"></a><span data-ttu-id="7f961-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7f961-112">See also</span></span>

- [<span data-ttu-id="7f961-113">Özellik Yordamları</span><span class="sxs-lookup"><span data-stu-id="7f961-113">Property Procedures</span></span>](../../programming-guide/language-features/procedures/property-procedures.md)
- [<span data-ttu-id="7f961-114">Nasıl yapılır: Bir Özelliği Karışık Erişim Düzeyleriyle Bildirme</span><span class="sxs-lookup"><span data-stu-id="7f961-114">How to: Declare a Property with Mixed Access Levels</span></span>](../../programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
