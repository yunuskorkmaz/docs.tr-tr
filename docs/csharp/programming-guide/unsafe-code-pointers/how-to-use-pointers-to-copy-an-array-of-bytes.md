---
title: Bayt dizisi kopyalamak için işaretçiler nasıl kullanılır - C# Programlama Kılavuzu
ms.date: 04/20/2018
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.openlocfilehash: 4929699c2d1e07b16d4694cff79f9b1394b1de38
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75698462"
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes-c-programming-guide"></a><span data-ttu-id="a5d64-102">Bir dizi bayt kopyalamak için işaretçiler nasıl kullanılır (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="a5d64-102">How to use pointers to copy an array of bytes (C# Programming Guide)</span></span>

<span data-ttu-id="a5d64-103">Aşağıdaki örnek, bir diziden diğerine bayt kopyalamak için işaretçiler kullanır.</span><span class="sxs-lookup"><span data-stu-id="a5d64-103">The following example uses pointers to copy bytes from one array to another.</span></span>

<span data-ttu-id="a5d64-104">Bu örnek, [unsafe](../../language-reference/keywords/unsafe.md) `Copy` yöntemde işaretçileri kullanmanıza olanak tanıyan güvenli olmayan anahtar sözcüğü kullanır.</span><span class="sxs-lookup"><span data-stu-id="a5d64-104">This example uses the [unsafe](../../language-reference/keywords/unsafe.md) keyword, which enables you to use pointers in the `Copy` method.</span></span> <span data-ttu-id="a5d64-105">[Sabit](../../language-reference/keywords/fixed-statement.md) deyim, işaretçileri kaynak ve hedef dizilerine bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a5d64-105">The [fixed](../../language-reference/keywords/fixed-statement.md) statement is used to declare pointers to the source and destination arrays.</span></span> <span data-ttu-id="a5d64-106">İfade, `fixed` kaynak ve hedef dizilerinin konumunu bellekte *sabitler,* böylece çöp toplama tarafından taşınmaz.</span><span class="sxs-lookup"><span data-stu-id="a5d64-106">The `fixed` statement *pins* the location of the source and destination arrays in memory so that they will not be moved by garbage collection.</span></span> <span data-ttu-id="a5d64-107">`fixed` Blok tamamlandığında dizilerin bellek blokları sabitlenmez.</span><span class="sxs-lookup"><span data-stu-id="a5d64-107">The memory blocks for the arrays are unpinned when the `fixed` block is completed.</span></span> <span data-ttu-id="a5d64-108">Bu `Copy` örnekteki yöntem anahtar `unsafe` sözcüğü kullandığından, [-güvenli olmayan](../../language-reference/compiler-options/unsafe-compiler-option.md) derleyici seçeneğiyle derlenmiş olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a5d64-108">Because the `Copy` method in this example uses the `unsafe` keyword, it must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>

<span data-ttu-id="a5d64-109">Bu örnek, ikinci bir yönetilmeyen işaretçi yerine endeksleri kullanarak her iki dizinin öğelerine erişer.</span><span class="sxs-lookup"><span data-stu-id="a5d64-109">This example accesses the elements of both arrays using indices rather than a second unmanaged pointer.</span></span> <span data-ttu-id="a5d64-110">Ve `pSource` `pTarget` işaretçilerin bildirimi dizileri sabitler.</span><span class="sxs-lookup"><span data-stu-id="a5d64-110">The declaration of the `pSource` and `pTarget` pointers pins the arrays.</span></span> <span data-ttu-id="a5d64-111">Bu özellik C# 7.3 ile başlayarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a5d64-111">This feature is available starting with C# 7.3.</span></span>

## <a name="example"></a><span data-ttu-id="a5d64-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="a5d64-112">Example</span></span>

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#8)]

## <a name="see-also"></a><span data-ttu-id="a5d64-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a5d64-113">See also</span></span>

- [<span data-ttu-id="a5d64-114">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a5d64-114">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="a5d64-115">Güvenli Olmayan Kod ve İşaretçiler</span><span class="sxs-lookup"><span data-stu-id="a5d64-115">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="a5d64-116">-güvenli değil (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="a5d64-116">-unsafe (C# Compiler Options)</span></span>](../../language-reference/compiler-options/unsafe-compiler-option.md)
- [<span data-ttu-id="a5d64-117">Çöp Toplama</span><span class="sxs-lookup"><span data-stu-id="a5d64-117">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
