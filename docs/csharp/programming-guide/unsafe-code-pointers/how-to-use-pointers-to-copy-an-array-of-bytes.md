---
title: Bir bayt dizisini kopyalamak için işaretçiler kullanma- C# Programlama Kılavuzu
ms.date: 04/20/2018
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.openlocfilehash: 4929699c2d1e07b16d4694cff79f9b1394b1de38
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75698462"
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes-c-programming-guide"></a><span data-ttu-id="4679b-102">Bir bayt dizisini kopyalamak için işaretçiler kullanma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="4679b-102">How to use pointers to copy an array of bytes (C# Programming Guide)</span></span>

<span data-ttu-id="4679b-103">Aşağıdaki örnek, baytları bir diziden diğerine kopyalamak için işaretçileri kullanır.</span><span class="sxs-lookup"><span data-stu-id="4679b-103">The following example uses pointers to copy bytes from one array to another.</span></span>

<span data-ttu-id="4679b-104">Bu örnek, `Copy` yönteminde işaretçiler kullanmanıza olanak sağlayan [unsafe](../../language-reference/keywords/unsafe.md) anahtar sözcüğünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="4679b-104">This example uses the [unsafe](../../language-reference/keywords/unsafe.md) keyword, which enables you to use pointers in the `Copy` method.</span></span> <span data-ttu-id="4679b-105">[Fixed](../../language-reference/keywords/fixed-statement.md) deyimleri, kaynak ve hedef dizilere işaretçiler bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4679b-105">The [fixed](../../language-reference/keywords/fixed-statement.md) statement is used to declare pointers to the source and destination arrays.</span></span> <span data-ttu-id="4679b-106">`fixed` bildiri, kaynak ve hedef dizilerin konumunu çöp toplama tarafından taşınamayacak şekilde *sabitler* .</span><span class="sxs-lookup"><span data-stu-id="4679b-106">The `fixed` statement *pins* the location of the source and destination arrays in memory so that they will not be moved by garbage collection.</span></span> <span data-ttu-id="4679b-107">`fixed` bloğu tamamlandığında diziler için bellek blokları sabitlenemez.</span><span class="sxs-lookup"><span data-stu-id="4679b-107">The memory blocks for the arrays are unpinned when the `fixed` block is completed.</span></span> <span data-ttu-id="4679b-108">Bu örnekteki `Copy` yöntemi `unsafe` anahtar sözcüğünü kullandığından, [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) derleyici seçeneğiyle derlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="4679b-108">Because the `Copy` method in this example uses the `unsafe` keyword, it must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>

<span data-ttu-id="4679b-109">Bu örnek, ikinci bir yönetilmeyen işaretçi yerine dizinler kullanılarak her iki dizinin öğelerine erişir.</span><span class="sxs-lookup"><span data-stu-id="4679b-109">This example accesses the elements of both arrays using indices rather than a second unmanaged pointer.</span></span> <span data-ttu-id="4679b-110">`pSource` ve `pTarget` işaretçilerinin bildirimi dizileri sabitler.</span><span class="sxs-lookup"><span data-stu-id="4679b-110">The declaration of the `pSource` and `pTarget` pointers pins the arrays.</span></span> <span data-ttu-id="4679b-111">Bu özellik 7,3 ile C# başlayarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4679b-111">This feature is available starting with C# 7.3.</span></span>

## <a name="example"></a><span data-ttu-id="4679b-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="4679b-112">Example</span></span>

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#8)]

## <a name="see-also"></a><span data-ttu-id="4679b-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4679b-113">See also</span></span>

- [<span data-ttu-id="4679b-114">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="4679b-114">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="4679b-115">Güvenli Olmayan Kod ve İşaretçiler</span><span class="sxs-lookup"><span data-stu-id="4679b-115">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="4679b-116">-unsafe (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="4679b-116">-unsafe (C# Compiler Options)</span></span>](../../language-reference/compiler-options/unsafe-compiler-option.md)
- [<span data-ttu-id="4679b-117">Atık Toplama</span><span class="sxs-lookup"><span data-stu-id="4679b-117">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
