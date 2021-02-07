---
description: 'Daha fazla bilgi edinin: genişletme (Visual Basic)'
title: Genişletme
ms.date: 07/20/2015
f1_keywords:
- vb.widening
helpviewer_keywords:
- conversions [Visual Basic], type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- Widening keyword [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: 646ae263-94d3-40a2-b0cc-64f619292f56
ms.openlocfilehash: de290296ba2b7716ba992c6bed46443053048282
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700708"
---
# <a name="widening-visual-basic"></a><span data-ttu-id="d148b-103">Genişletme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d148b-103">Widening (Visual Basic)</span></span>

<span data-ttu-id="d148b-104">Bir dönüştürme işlecinin () bir `CType` sınıfı ya da yapıyı özgün sınıf veya yapının tüm olası değerlerini tutabilecek bir türe dönüştürdüğü anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="d148b-104">Indicates that a conversion operator (`CType`) converts a class or structure to a type that can hold all possible values of the original class or structure.</span></span>  
  
## <a name="converting-with-the-widening-keyword"></a><span data-ttu-id="d148b-105">Genişletme anahtar sözcüğüyle dönüştürme</span><span class="sxs-lookup"><span data-stu-id="d148b-105">Converting with the Widening Keyword</span></span>  

 <span data-ttu-id="d148b-106">Dönüştürme yordamının öğesine ek olarak belirtmeniz gerekir `Public Shared` `Widening` .</span><span class="sxs-lookup"><span data-stu-id="d148b-106">The conversion procedure must specify `Public Shared` in addition to `Widening`.</span></span>  
  
 <span data-ttu-id="d148b-107">Genişletme dönüştürmeleri her zaman çalışma zamanında başarılı olur ve veri kaybına neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="d148b-107">Widening conversions always succeed at run time and never incur data loss.</span></span> <span data-ttu-id="d148b-108">Örnekler `Single` `Double` , `Char` `String` temel türüne ve türetilmiş bir türe örnektir.</span><span class="sxs-lookup"><span data-stu-id="d148b-108">Examples are `Single` to `Double`, `Char` to `String`, and a derived type to its base type.</span></span> <span data-ttu-id="d148b-109">Türetilmiş tür temel türün tüm üyelerini içerdiğinden ve bu nedenle temel türün bir örneği olduğundan, bu son dönüştürme işlemi genişletme.</span><span class="sxs-lookup"><span data-stu-id="d148b-109">This last conversion is widening because the derived type contains all the members of the base type and thus is an instance of the base type.</span></span>  
  
 <span data-ttu-id="d148b-110">Tüketim kodu, `CType` olsa bile, genişletme dönüştürmeleri için kullanmak zorunda değildir `Option Strict` `On` .</span><span class="sxs-lookup"><span data-stu-id="d148b-110">The consuming code does not have to use `CType` for widening conversions, even if `Option Strict` is `On`.</span></span>  
  
 <span data-ttu-id="d148b-111">`Widening`Anahtar sözcüğü bu bağlamda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="d148b-111">The `Widening` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="d148b-112">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="d148b-112">Operator Statement</span></span>](../statements/operator-statement.md)  
  
 <span data-ttu-id="d148b-113">Genişletme ve daraltma dönüştürme işleçlerinin tanımları için bkz. [nasıl yapılır: dönüştürme Işleci tanımlama](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span><span class="sxs-lookup"><span data-stu-id="d148b-113">For example definitions of widening and narrowing conversion operators, see [How to: Define a Conversion Operator](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d148b-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d148b-114">See also</span></span>

- [<span data-ttu-id="d148b-115">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="d148b-115">Operator Statement</span></span>](../statements/operator-statement.md)
- [<span data-ttu-id="d148b-116">Narrowing</span><span class="sxs-lookup"><span data-stu-id="d148b-116">Narrowing</span></span>](narrowing.md)
- [<span data-ttu-id="d148b-117">Genişletme ve Daraltma Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="d148b-117">Widening and Narrowing Conversions</span></span>](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="d148b-118">Nasıl yapılır: İşleç Tanımlama</span><span class="sxs-lookup"><span data-stu-id="d148b-118">How to: Define an Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="d148b-119">CType İşlevi</span><span class="sxs-lookup"><span data-stu-id="d148b-119">CType Function</span></span>](../functions/ctype-function.md)
- [<span data-ttu-id="d148b-120">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="d148b-120">Option Strict Statement</span></span>](../statements/option-strict-statement.md)
- [<span data-ttu-id="d148b-121">Nasıl yapılır: Dönüştürme İşleci Tanımlama</span><span class="sxs-lookup"><span data-stu-id="d148b-121">How to: Define a Conversion Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
