---
title: '* İşleci (C# Başvurusu)'
ms.date: 04/04/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '*_CSharpKeyword'
helpviewer_keywords:
- multiplication operator (*) [C#]
- '* operator [C#]'
ms.assetid: abd9a5f0-9b24-431e-971a-09ee1c45c50e
caps.latest.revision: 14
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 07d06d668ba43ebc3f4fae394d7b6641b122f4a6
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="-operator-c-reference"></a><span data-ttu-id="8abe8-102">\* İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="8abe8-102">\* Operator (C# Reference)</span></span>
<span data-ttu-id="8abe8-103">Çarpma işleci (`*`) işlenenleri çarpımını hesaplar.</span><span class="sxs-lookup"><span data-stu-id="8abe8-103">The multiplication operator (`*`) computes the product of its operands.</span></span> <span data-ttu-id="8abe8-104">Tüm sayısal türler çarpma işleçleri önceden.</span><span class="sxs-lookup"><span data-stu-id="8abe8-104">All numeric types have predefined multiplication operators.</span></span>  

<span data-ttu-id="8abe8-105">`*` Okuma ve yazma için bir işaretçi verir başvuru işleci de görür.</span><span class="sxs-lookup"><span data-stu-id="8abe8-105">`*` also serves as the dereference operator, which allows reading and writing to a pointer.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="8abe8-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8abe8-106">Remarks</span></span>  
 <span data-ttu-id="8abe8-107">`*` İşleci işaretçi türleri bildirme ve işaretçileri başvuru için de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8abe8-107">The `*` operator is also used to declare pointer types and to dereference pointers.</span></span> <span data-ttu-id="8abe8-108">Bu işleç yalnızca tarafından kullanımını gösterilen güvensiz bağlamlarında kullanılabilir [güvensiz](../../../csharp/language-reference/keywords/unsafe.md) anahtar sözcüğü ve gerektiren [/ unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="8abe8-108">This operator can only be used in unsafe contexts, denoted by the use of the [unsafe](../../../csharp/language-reference/keywords/unsafe.md) keyword, and requiring the [/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>  <span data-ttu-id="8abe8-109">Başvuru işleci indirection işleci de denir.</span><span class="sxs-lookup"><span data-stu-id="8abe8-109">The dereference operator is also known as the indirection operator.</span></span>  
  
 <span data-ttu-id="8abe8-110">Kullanıcı tanımlı türler ikili aşırı yükleme `*` işleci (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="8abe8-110">User-defined types can overload the binary `*` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="8abe8-111">İkili İşleç aşırı, karşılık gelen atama işleci varsa, aynı zamanda örtük olarak aşırı yüklü değildir.</span><span class="sxs-lookup"><span data-stu-id="8abe8-111">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8abe8-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="8abe8-112">Example</span></span>  
 [!code-csharp[csRefOperators#50](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-operator_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="8abe8-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="8abe8-113">Example</span></span>  
 [!code-csharp[csRefOperators#51](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-operator_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="8abe8-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8abe8-114">See Also</span></span>  
 [<span data-ttu-id="8abe8-115">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="8abe8-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="8abe8-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="8abe8-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="8abe8-117">Güvenli Olmayan Kod ve İşaretçiler</span><span class="sxs-lookup"><span data-stu-id="8abe8-117">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [<span data-ttu-id="8abe8-118">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="8abe8-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
