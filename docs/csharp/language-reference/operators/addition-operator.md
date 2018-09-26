---
title: + İşleci (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- +_CSharpKeyword
helpviewer_keywords:
- + operator [C#]
- concatenation operator [C#]
- addition operator [C#]
ms.assetid: 93e56486-bb42-43c1-bd43-60af11e64e67
ms.openlocfilehash: b49694bc8937c58bd295f0f8e57c378802d0dfb9
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47083091"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="86011-102">+ İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="86011-102">+ Operator (C# Reference)</span></span>
<span data-ttu-id="86011-103">`+` İşleci bir birli veya ikili işleç olarak işlev görebilir.</span><span class="sxs-lookup"><span data-stu-id="86011-103">The `+` operator can function as either a unary or a binary operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="86011-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="86011-104">Remarks</span></span>  
 <span data-ttu-id="86011-105">Birli `+` işleçleri tüm sayısal türler için önceden tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="86011-105">Unary `+` operators are predefined for all numeric types.</span></span> <span data-ttu-id="86011-106">Bir tekli sonucunu `+` işlemdir üzerinde bir sayısal tür işleneni değeri.</span><span class="sxs-lookup"><span data-stu-id="86011-106">The result of a unary `+` operation on a numeric type is just the value of the operand.</span></span>  
  
 <span data-ttu-id="86011-107">İkili `+` işleçleri sayısal ve dize türleri için önceden tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="86011-107">Binary `+` operators are predefined for numeric and string types.</span></span> <span data-ttu-id="86011-108">İçin sayısal türleri + iki işlenenleri toplamını hesaplar.</span><span class="sxs-lookup"><span data-stu-id="86011-108">For numeric types, + computes the sum of its two operands.</span></span> <span data-ttu-id="86011-109">Ne zaman bir veya iki işlenenin türü dize olan + işlenenler dize temsillerini art arda ekler.</span><span class="sxs-lookup"><span data-stu-id="86011-109">When one or both operands are of type string, + concatenates the string representations of the operands.</span></span>  
  
 <span data-ttu-id="86011-110">Temsilci türleri de sağlayan bir ikili `+` işleci temsilci birleştirme gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="86011-110">Delegate types also provide a binary `+` operator, which performs delegate concatenation.</span></span>  
  
 <span data-ttu-id="86011-111">Kullanıcı tanımlı türler aşırı yükleme birli `+` ve ikili `+` işleçleri.</span><span class="sxs-lookup"><span data-stu-id="86011-111">User-defined types can overload the unary `+` and binary `+` operators.</span></span> <span data-ttu-id="86011-112">Tamsayı türlerinde işlemler genellikle numaralandırma üzerinde izin verilir.</span><span class="sxs-lookup"><span data-stu-id="86011-112">Operations on integral types are generally allowed on enumeration.</span></span> <span data-ttu-id="86011-113">Daha fazla bilgi için [işleci (C# Başvurusu)](../../../csharp/language-reference/keywords/operator.md).</span><span class="sxs-lookup"><span data-stu-id="86011-113">For more information, see [operator (C# Reference)](../../../csharp/language-reference/keywords/operator.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="86011-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="86011-114">Example</span></span>  
 [!code-csharp[csRefOperators#28](../../../csharp/language-reference/operators/codesnippet/CSharp/addition-operator_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="86011-115">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="86011-115">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="86011-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="86011-116">See Also</span></span>

- [<span data-ttu-id="86011-117">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="86011-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="86011-118">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="86011-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="86011-119">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="86011-119">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
- [<span data-ttu-id="86011-120">İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="86011-120">operator (C# Reference)</span></span>](../../../csharp/language-reference/keywords/operator.md)
