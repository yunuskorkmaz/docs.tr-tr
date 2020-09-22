---
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
ms.openlocfilehash: 14e0b026f4fc3b0bf202ea643a28d6f1a7df2b7c
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867649"
---
# <a name="widening-visual-basic"></a><span data-ttu-id="dad08-102">Genişletme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dad08-102">Widening (Visual Basic)</span></span>

<span data-ttu-id="dad08-103">Bir dönüştürme işlecinin () bir `CType` sınıfı ya da yapıyı özgün sınıf veya yapının tüm olası değerlerini tutabilecek bir türe dönüştürdüğü anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="dad08-103">Indicates that a conversion operator (`CType`) converts a class or structure to a type that can hold all possible values of the original class or structure.</span></span>  
  
## <a name="converting-with-the-widening-keyword"></a><span data-ttu-id="dad08-104">Genişletme anahtar sözcüğüyle dönüştürme</span><span class="sxs-lookup"><span data-stu-id="dad08-104">Converting with the Widening Keyword</span></span>  

 <span data-ttu-id="dad08-105">Dönüştürme yordamının öğesine ek olarak belirtmeniz gerekir `Public Shared` `Widening` .</span><span class="sxs-lookup"><span data-stu-id="dad08-105">The conversion procedure must specify `Public Shared` in addition to `Widening`.</span></span>  
  
 <span data-ttu-id="dad08-106">Genişletme dönüştürmeleri her zaman çalışma zamanında başarılı olur ve veri kaybına neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="dad08-106">Widening conversions always succeed at run time and never incur data loss.</span></span> <span data-ttu-id="dad08-107">Örnekler `Single` `Double` , `Char` `String` temel türüne ve türetilmiş bir türe örnektir.</span><span class="sxs-lookup"><span data-stu-id="dad08-107">Examples are `Single` to `Double`, `Char` to `String`, and a derived type to its base type.</span></span> <span data-ttu-id="dad08-108">Türetilmiş tür temel türün tüm üyelerini içerdiğinden ve bu nedenle temel türün bir örneği olduğundan, bu son dönüştürme işlemi genişletme.</span><span class="sxs-lookup"><span data-stu-id="dad08-108">This last conversion is widening because the derived type contains all the members of the base type and thus is an instance of the base type.</span></span>  
  
 <span data-ttu-id="dad08-109">Tüketim kodu, `CType` olsa bile, genişletme dönüştürmeleri için kullanmak zorunda değildir `Option Strict` `On` .</span><span class="sxs-lookup"><span data-stu-id="dad08-109">The consuming code does not have to use `CType` for widening conversions, even if `Option Strict` is `On`.</span></span>  
  
 <span data-ttu-id="dad08-110">`Widening`Anahtar sözcüğü bu bağlamda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="dad08-110">The `Widening` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="dad08-111">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="dad08-111">Operator Statement</span></span>](../statements/operator-statement.md)  
  
 <span data-ttu-id="dad08-112">Genişletme ve daraltma dönüştürme işleçlerinin tanımları için bkz. [nasıl yapılır: dönüştürme Işleci tanımlama](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span><span class="sxs-lookup"><span data-stu-id="dad08-112">For example definitions of widening and narrowing conversion operators, see [How to: Define a Conversion Operator](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dad08-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dad08-113">See also</span></span>

- [<span data-ttu-id="dad08-114">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="dad08-114">Operator Statement</span></span>](../statements/operator-statement.md)
- [<span data-ttu-id="dad08-115">Narrowing</span><span class="sxs-lookup"><span data-stu-id="dad08-115">Narrowing</span></span>](narrowing.md)
- [<span data-ttu-id="dad08-116">Genişletme ve Daraltma Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="dad08-116">Widening and Narrowing Conversions</span></span>](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="dad08-117">Nasıl yapılır: İşleç Tanımlama</span><span class="sxs-lookup"><span data-stu-id="dad08-117">How to: Define an Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="dad08-118">CType İşlevi</span><span class="sxs-lookup"><span data-stu-id="dad08-118">CType Function</span></span>](../functions/ctype-function.md)
- [<span data-ttu-id="dad08-119">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="dad08-119">Option Strict Statement</span></span>](../statements/option-strict-statement.md)
- [<span data-ttu-id="dad08-120">Nasıl yapılır: Dönüştürme İşleci Tanımlama</span><span class="sxs-lookup"><span data-stu-id="dad08-120">How to: Define a Conversion Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
