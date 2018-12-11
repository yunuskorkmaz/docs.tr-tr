---
title: '! = İşleci - C# başvurusu'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '!=_CSharpKeyword'
helpviewer_keywords:
- inequality operator (!=) [C#]
- not equals operator (!=) [C#]
- '!= operator [C#]'
ms.assetid: eeff7a4e-ad6f-462d-9f8d-49e9b91c6c97
ms.openlocfilehash: 15f1b5930117e608644a58343fb855562f36b21c
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237824"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="047b4-102">!= İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="047b4-102">!= Operator (C# Reference)</span></span>
<span data-ttu-id="047b4-103">Eşitsizlik işleci (`!=`), işlenenlerinin true, eşitse false değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="047b4-103">The inequality operator (`!=`) returns false if its operands are equal, true otherwise.</span></span> <span data-ttu-id="047b4-104">Eşitsizlik işleçleri, string ve object dahil olmak üzere tüm türleri için önceden tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="047b4-104">Inequality operators are predefined for all types, including string and object.</span></span> <span data-ttu-id="047b4-105">Kullanıcı tanımlı türler aşırı yükleme `!=` işleci.</span><span class="sxs-lookup"><span data-stu-id="047b4-105">User-defined types can overload the `!=` operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="047b4-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="047b4-106">Remarks</span></span>  
 <span data-ttu-id="047b4-107">Önceden değer türleri, eşitsizlik işleci (`!=`) işlenenleri değerlerini, aksi takdirde farklı, false ise true değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="047b4-107">For predefined value types, the inequality operator (`!=`) returns true if the values of its operands are different, false otherwise.</span></span> <span data-ttu-id="047b4-108">İçin başvuru türleri dışındaki `string`, `!=` iki işlenenleri farklı nesnelere başvuruda bulunuyorsa true değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="047b4-108">For reference types other than `string`, `!=` returns true if its two operands refer to different objects.</span></span> <span data-ttu-id="047b4-109">İçin `string` türü `!=` dizelerin değerlerini karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="047b4-109">For the `string` type, `!=` compares the values of the strings.</span></span>  
  
 <span data-ttu-id="047b4-110">Kullanıcı tanımlı değer türleri aşırı yükleme `!=` işleci (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="047b4-110">User-defined value types can overload the `!=` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="047b4-111">Bu nedenle ancak varsayılan olarak kullanıcı tarafından tanımlanan başvuru türleri için `!=` hem önceden tanımlanmış ve kullanıcı tarafından tanımlanan başvuru türleri için yukarıda açıklandığı gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="047b4-111">So can user-defined reference types, although by default `!=` behaves as described above for both predefined and user-defined reference types.</span></span> <span data-ttu-id="047b4-112">Varsa `!=` aşırı yüklendi [ == ](../../../csharp/language-reference/operators/equality-comparison-operator.md) da aşırı yüklenmiş gerekir.</span><span class="sxs-lookup"><span data-stu-id="047b4-112">If `!=` is overloaded, [==](../../../csharp/language-reference/operators/equality-comparison-operator.md) must also be overloaded.</span></span> <span data-ttu-id="047b4-113">Tamsayı türlerinde işlemler genellikle numaralandırma üzerinde izin verilir.</span><span class="sxs-lookup"><span data-stu-id="047b4-113">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="047b4-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="047b4-114">Example</span></span>  
 [!code-csharp[csRefOperators#33](../../../csharp/language-reference/operators/codesnippet/CSharp/not-equal-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="047b4-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="047b4-115">See Also</span></span>

- [<span data-ttu-id="047b4-116">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="047b4-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="047b4-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="047b4-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="047b4-118">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="047b4-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
