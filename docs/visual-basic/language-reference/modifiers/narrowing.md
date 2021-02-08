---
description: 'Daha fazla bilgi edinin: daraltma (Visual Basic)'
title: Narrowing
ms.date: 07/20/2015
f1_keywords:
- vb.narrowing
helpviewer_keywords:
- conversions [Visual Basic], type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- Narrowing keyword [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: a207ee91-aca4-4771-b4e2-713f029bf2bb
ms.openlocfilehash: 1dd9185ccf30fb6f9dc9360f75450c2533ab90e5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795358"
---
# <a name="narrowing-visual-basic"></a><span data-ttu-id="3baf8-103">Daraltma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3baf8-103">Narrowing (Visual Basic)</span></span>

<span data-ttu-id="3baf8-104">Bir dönüştürme işlecinin () bir `CType` sınıfı ya da yapıyı özgün sınıf veya yapının olası bazı değerlerini tutabilecek bir türe dönüştürdüğü anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="3baf8-104">Indicates that a conversion operator (`CType`) converts a class or structure to a type that might not be able to hold some of the possible values of the original class or structure.</span></span>  
  
## <a name="converting-with-the-narrowing-keyword"></a><span data-ttu-id="3baf8-105">Daraltma anahtar sözcüğüyle dönüştürme</span><span class="sxs-lookup"><span data-stu-id="3baf8-105">Converting with the Narrowing Keyword</span></span>  

 <span data-ttu-id="3baf8-106">Dönüştürme yordamının öğesine ek olarak belirtmeniz gerekir `Public Shared` `Narrowing` .</span><span class="sxs-lookup"><span data-stu-id="3baf8-106">The conversion procedure must specify `Public Shared` in addition to `Narrowing`.</span></span>  
  
 <span data-ttu-id="3baf8-107">Daraltma dönüştürmeleri her zaman çalışma zamanında başarılı olmaz ve veri kaybına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="3baf8-107">Narrowing conversions do not always succeed at run time, and can fail or incur data loss.</span></span> <span data-ttu-id="3baf8-108">Örnekler `Long` `Integer` , `String` `Date` türetilmiş bir türe ve temel türe örnektir.</span><span class="sxs-lookup"><span data-stu-id="3baf8-108">Examples are `Long` to `Integer`, `String` to `Date`, and a base type to a derived type.</span></span> <span data-ttu-id="3baf8-109">Temel tür türetilmiş türün tüm üyelerini içermediğinden ve bu nedenle türetilmiş türün bir örneği olmadığından, bu son dönüştürme daraltma yapılır.</span><span class="sxs-lookup"><span data-stu-id="3baf8-109">This last conversion is narrowing because the base type might not contain all the members of the derived type and thus is not an instance of the derived type.</span></span>  
  
 <span data-ttu-id="3baf8-110">`Option Strict`İse `On` , tüketim kodu `CType` tüm daraltma dönüştürmeleri için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3baf8-110">If `Option Strict` is `On`, the consuming code must use `CType` for all narrowing conversions.</span></span>  
  
 <span data-ttu-id="3baf8-111">`Narrowing`Anahtar sözcüğü bu bağlamda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="3baf8-111">The `Narrowing` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="3baf8-112">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="3baf8-112">Operator Statement</span></span>](../statements/operator-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="3baf8-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3baf8-113">See also</span></span>

- [<span data-ttu-id="3baf8-114">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="3baf8-114">Operator Statement</span></span>](../statements/operator-statement.md)
- [<span data-ttu-id="3baf8-115">Genişletme</span><span class="sxs-lookup"><span data-stu-id="3baf8-115">Widening</span></span>](widening.md)
- [<span data-ttu-id="3baf8-116">Genişletme ve Daraltma Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="3baf8-116">Widening and Narrowing Conversions</span></span>](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="3baf8-117">Nasıl yapılır: İşleç Tanımlama</span><span class="sxs-lookup"><span data-stu-id="3baf8-117">How to: Define an Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="3baf8-118">CType İşlevi</span><span class="sxs-lookup"><span data-stu-id="3baf8-118">CType Function</span></span>](../functions/ctype-function.md)
- [<span data-ttu-id="3baf8-119">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="3baf8-119">Option Strict Statement</span></span>](../statements/option-strict-statement.md)
