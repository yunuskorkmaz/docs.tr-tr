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
ms.openlocfilehash: 69040bf48b44a54f7a231738b88db1cbc716ebb3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359909"
---
# <a name="widening-visual-basic"></a><span data-ttu-id="93337-102">Genişletme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="93337-102">Widening (Visual Basic)</span></span>
<span data-ttu-id="93337-103">Bir dönüştürme işlecinin () bir `CType` sınıfı ya da yapıyı özgün sınıf veya yapının tüm olası değerlerini tutabilecek bir türe dönüştürdüğü anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="93337-103">Indicates that a conversion operator (`CType`) converts a class or structure to a type that can hold all possible values of the original class or structure.</span></span>  
  
## <a name="converting-with-the-widening-keyword"></a><span data-ttu-id="93337-104">Genişletme anahtar sözcüğüyle dönüştürme</span><span class="sxs-lookup"><span data-stu-id="93337-104">Converting with the Widening Keyword</span></span>  
 <span data-ttu-id="93337-105">Dönüştürme yordamının öğesine ek olarak belirtmeniz gerekir `Public Shared` `Widening` .</span><span class="sxs-lookup"><span data-stu-id="93337-105">The conversion procedure must specify `Public Shared` in addition to `Widening`.</span></span>  
  
 <span data-ttu-id="93337-106">Genişletme dönüştürmeleri her zaman çalışma zamanında başarılı olur ve veri kaybına neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="93337-106">Widening conversions always succeed at run time and never incur data loss.</span></span> <span data-ttu-id="93337-107">Örnekler `Single` `Double` , `Char` `String` temel türüne ve türetilmiş bir türe örnektir.</span><span class="sxs-lookup"><span data-stu-id="93337-107">Examples are `Single` to `Double`, `Char` to `String`, and a derived type to its base type.</span></span> <span data-ttu-id="93337-108">Türetilmiş tür temel türün tüm üyelerini içerdiğinden ve bu nedenle temel türün bir örneği olduğundan, bu son dönüştürme işlemi genişletme.</span><span class="sxs-lookup"><span data-stu-id="93337-108">This last conversion is widening because the derived type contains all the members of the base type and thus is an instance of the base type.</span></span>  
  
 <span data-ttu-id="93337-109">Tüketim kodu, `CType` olsa bile, genişletme dönüştürmeleri için kullanmak zorunda değildir `Option Strict` `On` .</span><span class="sxs-lookup"><span data-stu-id="93337-109">The consuming code does not have to use `CType` for widening conversions, even if `Option Strict` is `On`.</span></span>  
  
 <span data-ttu-id="93337-110">`Widening`Anahtar sözcüğü bu bağlamda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="93337-110">The `Widening` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="93337-111">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="93337-111">Operator Statement</span></span>](../statements/operator-statement.md)  
  
 <span data-ttu-id="93337-112">Genişletme ve daraltma dönüştürme işleçlerinin tanımları için bkz. [nasıl yapılır: dönüştürme Işleci tanımlama](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span><span class="sxs-lookup"><span data-stu-id="93337-112">For example definitions of widening and narrowing conversion operators, see [How to: Define a Conversion Operator](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93337-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="93337-113">See also</span></span>

- [<span data-ttu-id="93337-114">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="93337-114">Operator Statement</span></span>](../statements/operator-statement.md)
- [<span data-ttu-id="93337-115">Narrowing</span><span class="sxs-lookup"><span data-stu-id="93337-115">Narrowing</span></span>](narrowing.md)
- [<span data-ttu-id="93337-116">Genişletme ve Daraltma Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="93337-116">Widening and Narrowing Conversions</span></span>](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="93337-117">Nasıl yapılır: İşleç Tanımlama</span><span class="sxs-lookup"><span data-stu-id="93337-117">How to: Define an Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="93337-118">CType İşlevi</span><span class="sxs-lookup"><span data-stu-id="93337-118">CType Function</span></span>](../functions/ctype-function.md)
- [<span data-ttu-id="93337-119">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="93337-119">Option Strict Statement</span></span>](../statements/option-strict-statement.md)
- [<span data-ttu-id="93337-120">Nasıl yapılır: Dönüştürme İşleci Tanımlama</span><span class="sxs-lookup"><span data-stu-id="93337-120">How to: Define a Conversion Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
