---
title: '!= İşleci (C# Başvurusu)'
ms.date: 07/20/2015
f1_keywords:
- '!=_CSharpKeyword'
helpviewer_keywords:
- inequality operator (!=) [C#]
- not equals operator (!=) [C#]
- '!= operator [C#]'
ms.assetid: eeff7a4e-ad6f-462d-9f8d-49e9b91c6c97
ms.openlocfilehash: e974ffb1b25944e24fca23864dc7e932ec1876d5
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43741227"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="63c01-102">!= İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="63c01-102">!= Operator (C# Reference)</span></span>
<span data-ttu-id="63c01-103">Eşitsizlik işleci (`!=`), işlenenlerinin true, eşitse false değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="63c01-103">The inequality operator (`!=`) returns false if its operands are equal, true otherwise.</span></span> <span data-ttu-id="63c01-104">Eşitsizlik işleçleri, string ve object dahil olmak üzere tüm türleri için önceden tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="63c01-104">Inequality operators are predefined for all types, including string and object.</span></span> <span data-ttu-id="63c01-105">Kullanıcı tanımlı türler aşırı yükleme `!=` işleci.</span><span class="sxs-lookup"><span data-stu-id="63c01-105">User-defined types can overload the `!=` operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="63c01-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="63c01-106">Remarks</span></span>  
 <span data-ttu-id="63c01-107">Önceden değer türleri, eşitsizlik işleci (`!=`) işlenenleri değerlerini, aksi takdirde farklı, false ise true değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="63c01-107">For predefined value types, the inequality operator (`!=`) returns true if the values of its operands are different, false otherwise.</span></span> <span data-ttu-id="63c01-108">İçin başvuru türleri dışındaki `string`, `!=` iki işlenenleri farklı nesnelere başvuruda bulunuyorsa true değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="63c01-108">For reference types other than `string`, `!=` returns true if its two operands refer to different objects.</span></span> <span data-ttu-id="63c01-109">İçin `string` türü `!=` dizelerin değerlerini karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="63c01-109">For the `string` type, `!=` compares the values of the strings.</span></span>  
  
 <span data-ttu-id="63c01-110">Kullanıcı tanımlı değer türleri aşırı yükleme `!=` işleci (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="63c01-110">User-defined value types can overload the `!=` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="63c01-111">Bu nedenle ancak varsayılan olarak kullanıcı tarafından tanımlanan başvuru türleri için `!=` hem önceden tanımlanmış ve kullanıcı tarafından tanımlanan başvuru türleri için yukarıda açıklandığı gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="63c01-111">So can user-defined reference types, although by default `!=` behaves as described above for both predefined and user-defined reference types.</span></span> <span data-ttu-id="63c01-112">Varsa `!=` aşırı yüklendi [ == ](../../../csharp/language-reference/operators/equality-comparison-operator.md) da aşırı yüklenmiş gerekir.</span><span class="sxs-lookup"><span data-stu-id="63c01-112">If `!=` is overloaded, [==](../../../csharp/language-reference/operators/equality-comparison-operator.md) must also be overloaded.</span></span> <span data-ttu-id="63c01-113">Tamsayı türlerinde işlemler genellikle numaralandırma üzerinde izin verilir.</span><span class="sxs-lookup"><span data-stu-id="63c01-113">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="63c01-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="63c01-114">Example</span></span>  
 [!code-csharp[csRefOperators#33](../../../csharp/language-reference/operators/codesnippet/CSharp/not-equal-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="63c01-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="63c01-115">See Also</span></span>

- [<span data-ttu-id="63c01-116">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="63c01-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="63c01-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="63c01-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="63c01-118">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="63c01-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
