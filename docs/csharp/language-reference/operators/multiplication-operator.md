---
title: '* Operator - C# başvurusu'
ms.custom: seodec18
ms.date: 04/04/2018
f1_keywords:
- '*_CSharpKeyword'
helpviewer_keywords:
- multiplication operator (*) [C#]
- '* operator [C#]'
ms.assetid: abd9a5f0-9b24-431e-971a-09ee1c45c50e
ms.openlocfilehash: f4490c4632d9344eb879ea55c20787b838781d91
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333739"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="e91f5-102">\* işleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="e91f5-102">\* operator (C# Reference)</span></span>

<span data-ttu-id="e91f5-103">Çarpma işleci (`*`), işlenenlerinin çarpımını hesaplar.</span><span class="sxs-lookup"><span data-stu-id="e91f5-103">The multiplication operator (`*`) computes the product of its operands.</span></span> <span data-ttu-id="e91f5-104">Tüm sayısal türler, çarpma işleçleri önceden tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="e91f5-104">All numeric types have predefined multiplication operators.</span></span>

<span data-ttu-id="e91f5-105">`*` Okuma ve yazma için bir işaretçi sağlar başvuru işleci de görür.</span><span class="sxs-lookup"><span data-stu-id="e91f5-105">`*` also serves as the dereference operator, which allows reading and writing to a pointer.</span></span>

## <a name="remarks"></a><span data-ttu-id="e91f5-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e91f5-106">Remarks</span></span>

<span data-ttu-id="e91f5-107">`*` İşleci işaretçi türleri bildirme ve işaretçi başvuru kaldırma için de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e91f5-107">The `*` operator is also used to declare pointer types and to dereference pointers.</span></span> <span data-ttu-id="e91f5-108">Bu işleci yalnızca güvenli bağlamlarda kullanımı tarafından gösterilen kullanılabilir [güvenli olmayan](../keywords/unsafe.md) anahtar sözcüğü ve gerektiren [/ unsafe](../compiler-options/unsafe-compiler-option.md) derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="e91f5-108">This operator can only be used in unsafe contexts, denoted by the use of the [unsafe](../keywords/unsafe.md) keyword, and requiring the [/unsafe](../compiler-options/unsafe-compiler-option.md) compiler option.</span></span>  <span data-ttu-id="e91f5-109">Başvuru işleci yöneltme işleci de denir.</span><span class="sxs-lookup"><span data-stu-id="e91f5-109">The dereference operator is also known as the indirection operator.</span></span>

<span data-ttu-id="e91f5-110">Kullanıcı tanımlı türler ikili aşırı yükleme `*` işleci (bkz [işleci](../keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="e91f5-110">User-defined types can overload the binary `*` operator (see [operator](../keywords/operator.md)).</span></span> <span data-ttu-id="e91f5-111">İkili İşleç aşırı karşılık gelen atama işleci, varsa, aynı zamanda örtük olarak aşırı yüklenmiş olur.</span><span class="sxs-lookup"><span data-stu-id="e91f5-111">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>

## <a name="example"></a><span data-ttu-id="e91f5-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="e91f5-112">Example</span></span>

[!code-csharp-interactive[csRefOperators#50](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#50)]

## <a name="example"></a><span data-ttu-id="e91f5-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="e91f5-113">Example</span></span>

[!code-csharp[csRefOperators#51](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#51)]

## <a name="see-also"></a><span data-ttu-id="e91f5-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e91f5-114">See also</span></span>

- [<span data-ttu-id="e91f5-115">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="e91f5-115">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e91f5-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e91f5-116">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e91f5-117">Güvenli Olmayan Kod ve İşaretçiler</span><span class="sxs-lookup"><span data-stu-id="e91f5-117">Unsafe Code and Pointers</span></span>](../../programming-guide/unsafe-code-pointers/index.md)
- [<span data-ttu-id="e91f5-118">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="e91f5-118">C# Operators</span></span>](index.md)