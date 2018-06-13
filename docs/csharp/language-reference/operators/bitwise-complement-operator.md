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
ms.openlocfilehash: 25b157fafde7d2b75cd8b112848a01e9b3fb0db2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33270309"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="6740c-102">~ İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="6740c-102">~ Operator (C# Reference)</span></span>
<span data-ttu-id="6740c-103">`~` İşleci her bit ters etkisi, işlenen bir bit düzeyinde tamamlama işlemi gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="6740c-103">The `~` operator performs a bitwise complement operation on its operand, which has the effect of reversing each bit.</span></span> <span data-ttu-id="6740c-104">Bit düzeyinde tamamlama işleçleri için önceden tanımlanmış [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [uzun](../../../csharp/language-reference/keywords/long.md), ve [ulong](../../../csharp/language-reference/keywords/ulong.md).</span><span class="sxs-lookup"><span data-stu-id="6740c-104">Bitwise complement operators are predefined for [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), and [ulong](../../../csharp/language-reference/keywords/ulong.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6740c-105">`~` Simgesi de sonlandırıcılar bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6740c-105">The `~` symbol also is used to declare finalizers.</span></span> <span data-ttu-id="6740c-106">Daha fazla bilgi için bkz: [sonlandırıcılar](../../../csharp/programming-guide/classes-and-structs/destructors.md).</span><span class="sxs-lookup"><span data-stu-id="6740c-106">For more information, see [Finalizers](../../../csharp/programming-guide/classes-and-structs/destructors.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6740c-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6740c-107">Remarks</span></span>  
 <span data-ttu-id="6740c-108">Kullanıcı tanımlı türler aşırı yükleme `~` işleci.</span><span class="sxs-lookup"><span data-stu-id="6740c-108">User-defined types can overload the `~` operator.</span></span> <span data-ttu-id="6740c-109">Daha fazla bilgi için bkz: [işleci](../../../csharp/language-reference/keywords/operator.md).</span><span class="sxs-lookup"><span data-stu-id="6740c-109">For more information, see [operator](../../../csharp/language-reference/keywords/operator.md).</span></span> <span data-ttu-id="6740c-110">Tam sayı türleri üzerinde işlemler genellikle numaralandırma üzerinde izin verilir.</span><span class="sxs-lookup"><span data-stu-id="6740c-110">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6740c-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="6740c-111">Example</span></span>  
 [!code-csharp[csRefOperators#25](../../../csharp/language-reference/operators/codesnippet/CSharp/bitwise-complement-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="6740c-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6740c-112">See Also</span></span>  
 [<span data-ttu-id="6740c-113">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="6740c-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="6740c-114">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="6740c-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="6740c-115">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="6740c-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="6740c-116">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="6740c-116">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)
