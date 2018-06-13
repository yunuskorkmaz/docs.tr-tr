---
title: '* İşleci (C# Başvurusu)'
ms.date: 04/04/2018
f1_keywords:
- '*_CSharpKeyword'
helpviewer_keywords:
- multiplication operator (*) [C#]
- '* operator [C#]'
ms.assetid: abd9a5f0-9b24-431e-971a-09ee1c45c50e
ms.openlocfilehash: 6c5d4de587b67e5ade158c163a87e8dea6bece5a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33275847"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="3190f-102">\* İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="3190f-102">\* Operator (C# Reference)</span></span>
<span data-ttu-id="3190f-103">Çarpma işleci (`*`) işlenenleri çarpımını hesaplar.</span><span class="sxs-lookup"><span data-stu-id="3190f-103">The multiplication operator (`*`) computes the product of its operands.</span></span> <span data-ttu-id="3190f-104">Tüm sayısal türler çarpma işleçleri önceden.</span><span class="sxs-lookup"><span data-stu-id="3190f-104">All numeric types have predefined multiplication operators.</span></span>  

<span data-ttu-id="3190f-105">`*` Okuma ve yazma için bir işaretçi verir başvuru işleci de görür.</span><span class="sxs-lookup"><span data-stu-id="3190f-105">`*` also serves as the dereference operator, which allows reading and writing to a pointer.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="3190f-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3190f-106">Remarks</span></span>  
 <span data-ttu-id="3190f-107">`*` İşleci işaretçi türleri bildirme ve işaretçileri başvuru için de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3190f-107">The `*` operator is also used to declare pointer types and to dereference pointers.</span></span> <span data-ttu-id="3190f-108">Bu işleç yalnızca tarafından kullanımını gösterilen güvensiz bağlamlarında kullanılabilir [güvensiz](../../../csharp/language-reference/keywords/unsafe.md) anahtar sözcüğü ve gerektiren [/ unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="3190f-108">This operator can only be used in unsafe contexts, denoted by the use of the [unsafe](../../../csharp/language-reference/keywords/unsafe.md) keyword, and requiring the [/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>  <span data-ttu-id="3190f-109">Başvuru işleci indirection işleci de denir.</span><span class="sxs-lookup"><span data-stu-id="3190f-109">The dereference operator is also known as the indirection operator.</span></span>  
  
 <span data-ttu-id="3190f-110">Kullanıcı tanımlı türler ikili aşırı yükleme `*` işleci (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="3190f-110">User-defined types can overload the binary `*` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="3190f-111">İkili İşleç aşırı, karşılık gelen atama işleci varsa, aynı zamanda örtük olarak aşırı yüklü değildir.</span><span class="sxs-lookup"><span data-stu-id="3190f-111">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3190f-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="3190f-112">Example</span></span>  
 [!code-csharp[csRefOperators#50](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-operator_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="3190f-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="3190f-113">Example</span></span>  
 [!code-csharp[csRefOperators#51](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-operator_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="3190f-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3190f-114">See Also</span></span>  
 [<span data-ttu-id="3190f-115">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="3190f-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="3190f-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="3190f-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="3190f-117">Güvenli Olmayan Kod ve İşaretçiler</span><span class="sxs-lookup"><span data-stu-id="3190f-117">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [<span data-ttu-id="3190f-118">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="3190f-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
