---
title: '* İşleci (C# Başvurusu)'
ms.date: 04/04/2018
f1_keywords:
- '*_CSharpKeyword'
helpviewer_keywords:
- multiplication operator (*) [C#]
- '* operator [C#]'
ms.assetid: abd9a5f0-9b24-431e-971a-09ee1c45c50e
ms.openlocfilehash: 873cc1dc0d81425117f1784353acf08b35158133
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43734375"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="589f2-102">\* İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="589f2-102">\* Operator (C# Reference)</span></span>
<span data-ttu-id="589f2-103">Çarpma işleci (`*`), işlenenlerinin çarpımını hesaplar.</span><span class="sxs-lookup"><span data-stu-id="589f2-103">The multiplication operator (`*`) computes the product of its operands.</span></span> <span data-ttu-id="589f2-104">Tüm sayısal türler, çarpma işleçleri önceden tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="589f2-104">All numeric types have predefined multiplication operators.</span></span>  

<span data-ttu-id="589f2-105">`*` Okuma ve yazma için bir işaretçi sağlar başvuru işleci de görür.</span><span class="sxs-lookup"><span data-stu-id="589f2-105">`*` also serves as the dereference operator, which allows reading and writing to a pointer.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="589f2-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="589f2-106">Remarks</span></span>  
 <span data-ttu-id="589f2-107">`*` İşleci işaretçi türleri bildirme ve işaretçi başvuru kaldırma için de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="589f2-107">The `*` operator is also used to declare pointer types and to dereference pointers.</span></span> <span data-ttu-id="589f2-108">Bu işleci yalnızca güvenli bağlamlarda kullanımı tarafından gösterilen kullanılabilir [güvenli olmayan](../../../csharp/language-reference/keywords/unsafe.md) anahtar sözcüğü ve gerektiren [/ unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="589f2-108">This operator can only be used in unsafe contexts, denoted by the use of the [unsafe](../../../csharp/language-reference/keywords/unsafe.md) keyword, and requiring the [/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>  <span data-ttu-id="589f2-109">Başvuru işleci yöneltme işleci de denir.</span><span class="sxs-lookup"><span data-stu-id="589f2-109">The dereference operator is also known as the indirection operator.</span></span>  
  
 <span data-ttu-id="589f2-110">Kullanıcı tanımlı türler ikili aşırı yükleme `*` işleci (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="589f2-110">User-defined types can overload the binary `*` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="589f2-111">İkili İşleç aşırı karşılık gelen atama işleci, varsa, aynı zamanda örtük olarak aşırı yüklenmiş olur.</span><span class="sxs-lookup"><span data-stu-id="589f2-111">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="589f2-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="589f2-112">Example</span></span>  
 [!code-csharp-interactive[csRefOperators#50](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-operator_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="589f2-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="589f2-113">Example</span></span>  
 [!code-csharp[csRefOperators#51](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-operator_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="589f2-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="589f2-114">See Also</span></span>

- [<span data-ttu-id="589f2-115">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="589f2-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="589f2-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="589f2-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="589f2-117">Güvenli Olmayan Kod ve İşaretçiler</span><span class="sxs-lookup"><span data-stu-id="589f2-117">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
- [<span data-ttu-id="589f2-118">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="589f2-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
