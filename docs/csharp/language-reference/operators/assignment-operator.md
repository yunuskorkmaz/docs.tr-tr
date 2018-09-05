---
title: = İşleci (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
ms.openlocfilehash: 9cd1af400a9afdb7942a49dee7e7f7bb78387f2d
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43507360"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="aa0eb-102">= İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="aa0eb-102">= Operator (C# Reference)</span></span>
<span data-ttu-id="aa0eb-103">Atama işleci (`=`) depolama konumu, özelliği veya dizin oluşturucu, sol işlenen tarafından belirtilen sağ işlenenin değerini depolar ve sonuç olarak değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="aa0eb-103">The assignment operator (`=`) stores the value of its right-hand operand in the storage location, property, or indexer denoted by its left-hand operand and returns the value as its result.</span></span> <span data-ttu-id="aa0eb-104">İşlenenler aynı türde olmalıdır (veya sağ işlenen, sol işlenen türüne örtük olarak dönüştürülebilir olmalıdır).</span><span class="sxs-lookup"><span data-stu-id="aa0eb-104">The operands must be of the same type (or the right-hand operand must be implicitly convertible to the type of the left-hand operand).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aa0eb-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="aa0eb-105">Remarks</span></span>  
 <span data-ttu-id="aa0eb-106">Atama işleci aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="aa0eb-106">The assignment operator cannot be overloaded.</span></span> <span data-ttu-id="aa0eb-107">Ancak, atama işleci bu türleriyle kullanmanıza olanak sağlayan örtük dönüşüm işleçleri için bir tür tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aa0eb-107">However, you can define implicit conversion operators for a type, which enable you to use the assignment operator with those types.</span></span> <span data-ttu-id="aa0eb-108">Daha fazla bilgi için [dönüştürme işleçleri kullanarak](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="aa0eb-108">For more information, see [Using Conversion Operators](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa0eb-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="aa0eb-109">Example</span></span>  
 [!code-csharp[csRefOperators#49](../../../csharp/language-reference/operators/codesnippet/CSharp/assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="aa0eb-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="aa0eb-110">See Also</span></span>

- [<span data-ttu-id="aa0eb-111">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="aa0eb-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="aa0eb-112">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="aa0eb-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="aa0eb-113">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="aa0eb-113">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
