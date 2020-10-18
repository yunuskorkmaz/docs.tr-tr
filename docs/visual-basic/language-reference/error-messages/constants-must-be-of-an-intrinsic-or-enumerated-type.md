---
title: Sabitler iç veya numaralandırılmış türde olmalıdır; sınıf, yapı, tür parametresi veya dizi türünde olamaz
ms.date: 07/20/2015
f1_keywords:
- vbc30424
- bc30424
helpviewer_keywords:
- BC30424
ms.assetid: 2d402c2f-27ad-428b-b699-d45cd62f7196
ms.openlocfilehash: e820287f0ddf462b30867d90501f7d730c9c6739
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163161"
---
# <a name="bc30424-constants-must-be-of-an-intrinsic-or-enumerated-type-not-a-class-structure-type-parameter-or-array-type"></a><span data-ttu-id="b014a-102">BC30424: sabitler bir iç veya numaralandırılmış türde olmalıdır; sınıf, yapı, tür parametresi veya dizi türünde olamaz</span><span class="sxs-lookup"><span data-stu-id="b014a-102">BC30424: Constants must be of an intrinsic or enumerated type, not a class, structure, type parameter, or array type</span></span>

<span data-ttu-id="b014a-103">Bir sabiti sınıf, yapı veya dizi türü olarak ya da içeren bir genel tür tarafından tanımlanan bir tür parametresi olarak bildirmeye çalıştınız.</span><span class="sxs-lookup"><span data-stu-id="b014a-103">You have attempted to declare a constant as a class, structure, or array type, or as a type parameter defined by a containing generic type.</span></span>

 <span data-ttu-id="b014a-104">Sabitler bir iç tür (,,,,,,,,,,,,,,,,,,,,,,, `Boolean` `Byte` `Date` `Decimal` `Double` `Integer` `Long` `Object` `SByte` `Short` `Single` `String` `UInteger` `ULong` veya `UShort` ) olmalıdır veya `Enum` integral türlerinden birini temel alan bir tür olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b014a-104">Constants must be of an intrinsic type (`Boolean`, `Byte`, `Date`, `Decimal`, `Double`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, or `UShort`), or an `Enum` type based on one of the integral types.</span></span>

 <span data-ttu-id="b014a-105">**Hata kimliği:** BC30424</span><span class="sxs-lookup"><span data-stu-id="b014a-105">**Error ID:** BC30424</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="b014a-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="b014a-106">To correct this error</span></span>

1. <span data-ttu-id="b014a-107">Sabiti bir iç veya tür olarak bildirin `Enum` .</span><span class="sxs-lookup"><span data-stu-id="b014a-107">Declare the constant as an intrinsic or `Enum` type.</span></span>

2. <span data-ttu-id="b014a-108">Bir sabit,, veya gibi özel bir değer de `True` olabilir `False` `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="b014a-108">A constant can also be a special value such as `True`, `False`, or `Nothing`.</span></span> <span data-ttu-id="b014a-109">Derleyici, bu önceden tanımlı değerleri uygun iç türden olacak şekilde değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="b014a-109">The compiler considers these predefined values to be of the appropriate intrinsic type.</span></span>

## <a name="see-also"></a><span data-ttu-id="b014a-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b014a-110">See also</span></span>

- [<span data-ttu-id="b014a-111">Sabitler ve numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="b014a-111">Constants and Enumerations</span></span>](../constants-and-enumerations.md)
- [<span data-ttu-id="b014a-112">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="b014a-112">Data Types</span></span>](../../programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="b014a-113">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="b014a-113">Data Types</span></span>](../data-types/index.md)
