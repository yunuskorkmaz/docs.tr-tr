---
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
ms.openlocfilehash: 77515357ac9dc972992df09c471695aad13985c4
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867937"
---
# <a name="narrowing-visual-basic"></a><span data-ttu-id="c3859-102">Daraltma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c3859-102">Narrowing (Visual Basic)</span></span>

<span data-ttu-id="c3859-103">Bir dönüştürme işlecinin () bir `CType` sınıfı ya da yapıyı özgün sınıf veya yapının olası bazı değerlerini tutabilecek bir türe dönüştürdüğü anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c3859-103">Indicates that a conversion operator (`CType`) converts a class or structure to a type that might not be able to hold some of the possible values of the original class or structure.</span></span>  
  
## <a name="converting-with-the-narrowing-keyword"></a><span data-ttu-id="c3859-104">Daraltma anahtar sözcüğüyle dönüştürme</span><span class="sxs-lookup"><span data-stu-id="c3859-104">Converting with the Narrowing Keyword</span></span>  

 <span data-ttu-id="c3859-105">Dönüştürme yordamının öğesine ek olarak belirtmeniz gerekir `Public Shared` `Narrowing` .</span><span class="sxs-lookup"><span data-stu-id="c3859-105">The conversion procedure must specify `Public Shared` in addition to `Narrowing`.</span></span>  
  
 <span data-ttu-id="c3859-106">Daraltma dönüştürmeleri her zaman çalışma zamanında başarılı olmaz ve veri kaybına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="c3859-106">Narrowing conversions do not always succeed at run time, and can fail or incur data loss.</span></span> <span data-ttu-id="c3859-107">Örnekler `Long` `Integer` , `String` `Date` türetilmiş bir türe ve temel türe örnektir.</span><span class="sxs-lookup"><span data-stu-id="c3859-107">Examples are `Long` to `Integer`, `String` to `Date`, and a base type to a derived type.</span></span> <span data-ttu-id="c3859-108">Temel tür türetilmiş türün tüm üyelerini içermediğinden ve bu nedenle türetilmiş türün bir örneği olmadığından, bu son dönüştürme daraltma yapılır.</span><span class="sxs-lookup"><span data-stu-id="c3859-108">This last conversion is narrowing because the base type might not contain all the members of the derived type and thus is not an instance of the derived type.</span></span>  
  
 <span data-ttu-id="c3859-109">`Option Strict`İse `On` , tüketim kodu `CType` tüm daraltma dönüştürmeleri için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c3859-109">If `Option Strict` is `On`, the consuming code must use `CType` for all narrowing conversions.</span></span>  
  
 <span data-ttu-id="c3859-110">`Narrowing`Anahtar sözcüğü bu bağlamda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="c3859-110">The `Narrowing` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="c3859-111">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="c3859-111">Operator Statement</span></span>](../statements/operator-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="c3859-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c3859-112">See also</span></span>

- [<span data-ttu-id="c3859-113">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="c3859-113">Operator Statement</span></span>](../statements/operator-statement.md)
- [<span data-ttu-id="c3859-114">Genişletme</span><span class="sxs-lookup"><span data-stu-id="c3859-114">Widening</span></span>](widening.md)
- [<span data-ttu-id="c3859-115">Genişletme ve Daraltma Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="c3859-115">Widening and Narrowing Conversions</span></span>](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="c3859-116">Nasıl yapılır: İşleç Tanımlama</span><span class="sxs-lookup"><span data-stu-id="c3859-116">How to: Define an Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="c3859-117">CType İşlevi</span><span class="sxs-lookup"><span data-stu-id="c3859-117">CType Function</span></span>](../functions/ctype-function.md)
- [<span data-ttu-id="c3859-118">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="c3859-118">Option Strict Statement</span></span>](../statements/option-strict-statement.md)
