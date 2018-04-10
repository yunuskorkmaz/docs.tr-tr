---
title: == İşleci (C# Başvurusu)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ==_CSharpKeyword
helpviewer_keywords:
- == operator [C#]
- equality operator [C#]
ms.assetid: 34c6b597-caa2-4855-a7cd-38ecdd11bd07
caps.latest.revision: 14
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ca22846325968519a1f7625461867c0d83a1a9f5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="e4798-102">== İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="e4798-102">== Operator (C# Reference)</span></span>
<span data-ttu-id="e4798-103">İçin önceden tanımlanmış değer türleri, eşitlik işleci (`==`) işlenenleri değer eşitse, true döndürür `false` Aksi takdirde.</span><span class="sxs-lookup"><span data-stu-id="e4798-103">For predefined value types, the equality operator (`==`) returns true if the values of its operands are equal, `false` otherwise.</span></span> <span data-ttu-id="e4798-104">Başvuru türleri dışında [dize](../../../csharp/language-reference/keywords/string.md), `==` döndürür `true` iki işlenenleri de aynı nesneye başvuruda bulunuyorsa.</span><span class="sxs-lookup"><span data-stu-id="e4798-104">For reference types other than [string](../../../csharp/language-reference/keywords/string.md), `==` returns `true` if its two operands refer to the same object.</span></span> <span data-ttu-id="e4798-105">İçin `string` türü, `==` dize değerlerini karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="e4798-105">For the `string` type, `==` compares the values of the strings.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e4798-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e4798-106">Remarks</span></span>  
 <span data-ttu-id="e4798-107">Kullanıcı tanımlı bir değer türleri aşırı yükleme `==` işleci (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="e4798-107">User-defined value types can overload the `==` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="e4798-108">Bu nedenle ancak varsayılan olarak kullanıcı tanımlı başvuru türleri için `==` hem önceden tanımlanmış ve kullanıcı tanımlı referans türleri için yukarıda açıklandığı gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="e4798-108">So can user-defined reference types, although by default `==` behaves as described above for both predefined and user-defined reference types.</span></span> <span data-ttu-id="e4798-109">Varsa `==` aşırı yüklendi [! =](../../../csharp/language-reference/operators/not-equal-operator.md) da aşırı yüklenmiş gerekir.</span><span class="sxs-lookup"><span data-stu-id="e4798-109">If `==` is overloaded, [!=](../../../csharp/language-reference/operators/not-equal-operator.md) must also be overloaded.</span></span> <span data-ttu-id="e4798-110">Tam sayı türleri üzerinde işlemler genellikle numaralandırma üzerinde izin verilir.</span><span class="sxs-lookup"><span data-stu-id="e4798-110">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4798-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="e4798-111">Example</span></span>  
 [!code-csharp[csRefOperators#36](../../../csharp/language-reference/operators/codesnippet/CSharp/equality-comparison-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="e4798-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e4798-112">See Also</span></span>  
 [<span data-ttu-id="e4798-113">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="e4798-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="e4798-114">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e4798-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="e4798-115">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="e4798-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
