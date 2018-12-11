---
title: == İşleci - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ==_CSharpKeyword
helpviewer_keywords:
- == operator [C#]
- equality operator [C#]
ms.assetid: 34c6b597-caa2-4855-a7cd-38ecdd11bd07
ms.openlocfilehash: c6f93be4d422fe42787e36f5b86e2cccbfc645b7
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53239020"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="8340c-102">== İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="8340c-102">== Operator (C# Reference)</span></span>
<span data-ttu-id="8340c-103">Önceden değer türleri eşitlik işlecini (`==`) işlenenleri değerlerini eşitse true değerini döndürür `false` Aksi takdirde.</span><span class="sxs-lookup"><span data-stu-id="8340c-103">For predefined value types, the equality operator (`==`) returns true if the values of its operands are equal, `false` otherwise.</span></span> <span data-ttu-id="8340c-104">İçin başvuru türleri dışındaki [dize](../../../csharp/language-reference/keywords/string.md), `==` döndürür `true` iki işlenenleri aynı nesneye başvuruyorsa.</span><span class="sxs-lookup"><span data-stu-id="8340c-104">For reference types other than [string](../../../csharp/language-reference/keywords/string.md), `==` returns `true` if its two operands refer to the same object.</span></span> <span data-ttu-id="8340c-105">İçin `string` türü `==` dizelerin değerlerini karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="8340c-105">For the `string` type, `==` compares the values of the strings.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8340c-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8340c-106">Remarks</span></span>  
 <span data-ttu-id="8340c-107">Kullanıcı tanımlı değer türleri aşırı yükleme `==` işleci (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="8340c-107">User-defined value types can overload the `==` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="8340c-108">Bu nedenle ancak varsayılan olarak kullanıcı tarafından tanımlanan başvuru türleri için `==` hem önceden tanımlanmış ve kullanıcı tarafından tanımlanan başvuru türleri için yukarıda açıklandığı gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="8340c-108">So can user-defined reference types, although by default `==` behaves as described above for both predefined and user-defined reference types.</span></span> <span data-ttu-id="8340c-109">Varsa `==` aşırı yüklendi [! =](../../../csharp/language-reference/operators/not-equal-operator.md) da aşırı yüklenmiş gerekir.</span><span class="sxs-lookup"><span data-stu-id="8340c-109">If `==` is overloaded, [!=](../../../csharp/language-reference/operators/not-equal-operator.md) must also be overloaded.</span></span> <span data-ttu-id="8340c-110">Tamsayı türlerinde işlemler genellikle numaralandırma üzerinde izin verilir.</span><span class="sxs-lookup"><span data-stu-id="8340c-110">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8340c-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="8340c-111">Example</span></span>  
 [!code-csharp[csRefOperators#36](../../../csharp/language-reference/operators/codesnippet/CSharp/equality-comparison-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="8340c-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8340c-112">See Also</span></span>

- [<span data-ttu-id="8340c-113">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="8340c-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="8340c-114">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="8340c-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="8340c-115">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="8340c-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
