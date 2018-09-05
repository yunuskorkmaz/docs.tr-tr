---
title: ~ İşleci (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- ~_CSharpKeyword
helpviewer_keywords:
- tilde (~) one's complement operator [C#]
- ~ operator [C#]
- ~ [C#], bitwise complement operator
- bitwise complement operator [C#]
ms.assetid: 11bc078a-50e2-4d7e-9896-67ef669dc602
ms.openlocfilehash: 8af25217f9e7e66796192783a0b8e3415604dc90
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43510117"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="9d296-102">~ İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="9d296-102">~ Operator (C# Reference)</span></span>
<span data-ttu-id="9d296-103">`~` İşleci bir her bit ters etkisi, işlenenin bit düzeyinde tamamlayıcı işlem gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="9d296-103">The `~` operator performs a bitwise complement operation on its operand, which has the effect of reversing each bit.</span></span> <span data-ttu-id="9d296-104">Bit düzeyinde tamamlayıcı işleçleri için önceden tanımlanmış [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [uzun](../../../csharp/language-reference/keywords/long.md), ve [ulong](../../../csharp/language-reference/keywords/ulong.md).</span><span class="sxs-lookup"><span data-stu-id="9d296-104">Bitwise complement operators are predefined for [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), and [ulong](../../../csharp/language-reference/keywords/ulong.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9d296-105">`~` Simgesi de sonlandırıcılar bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9d296-105">The `~` symbol also is used to declare finalizers.</span></span> <span data-ttu-id="9d296-106">Daha fazla bilgi için [sonlandırıcılar](../../../csharp/programming-guide/classes-and-structs/destructors.md).</span><span class="sxs-lookup"><span data-stu-id="9d296-106">For more information, see [Finalizers](../../../csharp/programming-guide/classes-and-structs/destructors.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d296-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9d296-107">Remarks</span></span>  
 <span data-ttu-id="9d296-108">Kullanıcı tanımlı türler aşırı yükleme `~` işleci.</span><span class="sxs-lookup"><span data-stu-id="9d296-108">User-defined types can overload the `~` operator.</span></span> <span data-ttu-id="9d296-109">Daha fazla bilgi için [işleci](../../../csharp/language-reference/keywords/operator.md).</span><span class="sxs-lookup"><span data-stu-id="9d296-109">For more information, see [operator](../../../csharp/language-reference/keywords/operator.md).</span></span> <span data-ttu-id="9d296-110">Tamsayı türlerinde işlemler genellikle numaralandırma üzerinde izin verilir.</span><span class="sxs-lookup"><span data-stu-id="9d296-110">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d296-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="9d296-111">Example</span></span>  
 [!code-csharp[csRefOperators#25](../../../csharp/language-reference/operators/codesnippet/CSharp/bitwise-complement-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="9d296-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9d296-112">See Also</span></span>

- [<span data-ttu-id="9d296-113">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="9d296-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="9d296-114">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="9d296-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="9d296-115">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="9d296-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
- [<span data-ttu-id="9d296-116">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="9d296-116">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)
