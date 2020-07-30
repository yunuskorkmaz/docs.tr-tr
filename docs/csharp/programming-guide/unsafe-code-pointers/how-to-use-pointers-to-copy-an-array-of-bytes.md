---
title: Bir bayt dizisini kopyalamak için işaretçiler kullanma-C# Programlama Kılavuzu
description: Bir bayt dizisini kopyalamak için işaretçileri nasıl kullanacağınızı öğrenin. Bir kod örneğine ve kullanılabilir ek kaynaklara bakın.
ms.date: 04/20/2018
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.openlocfilehash: 70ab1441d25ea69afb2244bd94bd404a3e32838d
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381794"
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes-c-programming-guide"></a><span data-ttu-id="0a3e8-104">Bir bayt dizisini kopyalamak için işaretçiler kullanma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="0a3e8-104">How to use pointers to copy an array of bytes (C# Programming Guide)</span></span>

<span data-ttu-id="0a3e8-105">Aşağıdaki örnek, baytları bir diziden diğerine kopyalamak için işaretçileri kullanır.</span><span class="sxs-lookup"><span data-stu-id="0a3e8-105">The following example uses pointers to copy bytes from one array to another.</span></span>

<span data-ttu-id="0a3e8-106">Bu örnek, yönteminde işaretçiler kullanmanıza olanak tanıyan [unsafe](../../language-reference/keywords/unsafe.md) anahtar sözcüğünü kullanır `Copy` .</span><span class="sxs-lookup"><span data-stu-id="0a3e8-106">This example uses the [unsafe](../../language-reference/keywords/unsafe.md) keyword, which enables you to use pointers in the `Copy` method.</span></span> <span data-ttu-id="0a3e8-107">[Fixed](../../language-reference/keywords/fixed-statement.md) deyimleri, kaynak ve hedef dizilere işaretçiler bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0a3e8-107">The [fixed](../../language-reference/keywords/fixed-statement.md) statement is used to declare pointers to the source and destination arrays.</span></span> <span data-ttu-id="0a3e8-108">`fixed`İfade, kaynak ve hedef dizilerinin konumunu çöp toplama tarafından taşınmayacak şekilde *sabitler* .</span><span class="sxs-lookup"><span data-stu-id="0a3e8-108">The `fixed` statement *pins* the location of the source and destination arrays in memory so that they will not be moved by garbage collection.</span></span> <span data-ttu-id="0a3e8-109">Blok tamamlandığında diziler için bellek blokları `fixed` sabitlenemez.</span><span class="sxs-lookup"><span data-stu-id="0a3e8-109">The memory blocks for the arrays are unpinned when the `fixed` block is completed.</span></span> <span data-ttu-id="0a3e8-110">`Copy`Bu örnekteki yöntem `unsafe` anahtar sözcüğünü kullandığından, [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) derleyici seçeneğiyle derlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="0a3e8-110">Because the `Copy` method in this example uses the `unsafe` keyword, it must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>

<span data-ttu-id="0a3e8-111">Bu örnek, ikinci bir yönetilmeyen işaretçi yerine dizinler kullanılarak her iki dizinin öğelerine erişir.</span><span class="sxs-lookup"><span data-stu-id="0a3e8-111">This example accesses the elements of both arrays using indices rather than a second unmanaged pointer.</span></span> <span data-ttu-id="0a3e8-112">`pSource`Ve `pTarget` işaretçilerinin bildirimi dizileri sabitler.</span><span class="sxs-lookup"><span data-stu-id="0a3e8-112">The declaration of the `pSource` and `pTarget` pointers pins the arrays.</span></span> <span data-ttu-id="0a3e8-113">Bu özellik C# 7,3 ile başlayarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0a3e8-113">This feature is available starting with C# 7.3.</span></span>

## <a name="example"></a><span data-ttu-id="0a3e8-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="0a3e8-114">Example</span></span>

[!code-csharp[Struct with embedded inline array](snippets/FixedKeywordExamples.cs#8)]

## <a name="see-also"></a><span data-ttu-id="0a3e8-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0a3e8-115">See also</span></span>

- [<span data-ttu-id="0a3e8-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0a3e8-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="0a3e8-117">Güvenli olmayan kod ve Işaretçiler</span><span class="sxs-lookup"><span data-stu-id="0a3e8-117">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="0a3e8-118">-unsafe (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="0a3e8-118">-unsafe (C# Compiler Options)</span></span>](../../language-reference/compiler-options/unsafe-compiler-option.md)
- [<span data-ttu-id="0a3e8-119">Çöp toplama</span><span class="sxs-lookup"><span data-stu-id="0a3e8-119">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
