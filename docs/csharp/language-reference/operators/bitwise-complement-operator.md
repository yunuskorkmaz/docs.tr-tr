---
title: "~ İşleci (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: ~_CSharpKeyword
helpviewer_keywords:
- tilde (~) one's complement operator [C#]
- ~ operator [C#]
- ~ [C#], bitwise complement operator
- bitwise complement operator [C#]
ms.assetid: 11bc078a-50e2-4d7e-9896-67ef669dc602
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a9b0cabcb101fce8422b1390ec8c4cb3b3849631
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="c4db6-102">~ İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="c4db6-102">~ Operator (C# Reference)</span></span>
<span data-ttu-id="c4db6-103">`~` İşleci her bit ters etkisi, işlenen bir bit düzeyinde tamamlama işlemi gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="c4db6-103">The `~` operator performs a bitwise complement operation on its operand, which has the effect of reversing each bit.</span></span> <span data-ttu-id="c4db6-104">Bit düzeyinde tamamlama işleçleri için önceden tanımlanmış [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [uzun](../../../csharp/language-reference/keywords/long.md), ve [ulong](../../../csharp/language-reference/keywords/ulong.md).</span><span class="sxs-lookup"><span data-stu-id="c4db6-104">Bitwise complement operators are predefined for [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), and [ulong](../../../csharp/language-reference/keywords/ulong.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c4db6-105">`~` Simgesi de sonlandırıcılar bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c4db6-105">The `~` symbol also is used to declare finalizers.</span></span> <span data-ttu-id="c4db6-106">Daha fazla bilgi için bkz: [sonlandırıcılar](../../../csharp/programming-guide/classes-and-structs/destructors.md).</span><span class="sxs-lookup"><span data-stu-id="c4db6-106">For more information, see [Finalizers](../../../csharp/programming-guide/classes-and-structs/destructors.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c4db6-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c4db6-107">Remarks</span></span>  
 <span data-ttu-id="c4db6-108">Kullanıcı tanımlı türler aşırı yükleme `~` işleci.</span><span class="sxs-lookup"><span data-stu-id="c4db6-108">User-defined types can overload the `~` operator.</span></span> <span data-ttu-id="c4db6-109">Daha fazla bilgi için bkz: [işleci](../../../csharp/language-reference/keywords/operator.md).</span><span class="sxs-lookup"><span data-stu-id="c4db6-109">For more information, see [operator](../../../csharp/language-reference/keywords/operator.md).</span></span> <span data-ttu-id="c4db6-110">Tam sayı türleri üzerinde işlemler genellikle numaralandırma üzerinde izin verilir.</span><span class="sxs-lookup"><span data-stu-id="c4db6-110">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4db6-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="c4db6-111">Example</span></span>  
 [!code-csharp[csRefOperators#25](../../../csharp/language-reference/operators/codesnippet/CSharp/bitwise-complement-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="c4db6-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c4db6-112">See Also</span></span>  
 [<span data-ttu-id="c4db6-113">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="c4db6-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="c4db6-114">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c4db6-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c4db6-115">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="c4db6-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="c4db6-116">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="c4db6-116">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)
