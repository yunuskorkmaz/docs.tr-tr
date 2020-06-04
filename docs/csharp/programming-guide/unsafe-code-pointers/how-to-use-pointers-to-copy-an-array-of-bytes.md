---
title: Bir bayt dizisini kopyalamak için işaretçiler kullanma-C# Programlama Kılavuzu
ms.date: 04/20/2018
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.openlocfilehash: 8c1afc06fb567a923d604ad53dc26f94178a8d60
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397421"
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes-c-programming-guide"></a><span data-ttu-id="5450e-102">Bir bayt dizisini kopyalamak için işaretçiler kullanma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="5450e-102">How to use pointers to copy an array of bytes (C# Programming Guide)</span></span>

<span data-ttu-id="5450e-103">Aşağıdaki örnek, baytları bir diziden diğerine kopyalamak için işaretçileri kullanır.</span><span class="sxs-lookup"><span data-stu-id="5450e-103">The following example uses pointers to copy bytes from one array to another.</span></span>

<span data-ttu-id="5450e-104">Bu örnek, yönteminde işaretçiler kullanmanıza olanak tanıyan [unsafe](../../language-reference/keywords/unsafe.md) anahtar sözcüğünü kullanır `Copy` .</span><span class="sxs-lookup"><span data-stu-id="5450e-104">This example uses the [unsafe](../../language-reference/keywords/unsafe.md) keyword, which enables you to use pointers in the `Copy` method.</span></span> <span data-ttu-id="5450e-105">[Fixed](../../language-reference/keywords/fixed-statement.md) deyimleri, kaynak ve hedef dizilere işaretçiler bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5450e-105">The [fixed](../../language-reference/keywords/fixed-statement.md) statement is used to declare pointers to the source and destination arrays.</span></span> <span data-ttu-id="5450e-106">`fixed`İfade, kaynak ve hedef dizilerinin konumunu çöp toplama tarafından taşınmayacak şekilde *sabitler* .</span><span class="sxs-lookup"><span data-stu-id="5450e-106">The `fixed` statement *pins* the location of the source and destination arrays in memory so that they will not be moved by garbage collection.</span></span> <span data-ttu-id="5450e-107">Blok tamamlandığında diziler için bellek blokları `fixed` sabitlenemez.</span><span class="sxs-lookup"><span data-stu-id="5450e-107">The memory blocks for the arrays are unpinned when the `fixed` block is completed.</span></span> <span data-ttu-id="5450e-108">`Copy`Bu örnekteki yöntem `unsafe` anahtar sözcüğünü kullandığından, [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) derleyici seçeneğiyle derlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="5450e-108">Because the `Copy` method in this example uses the `unsafe` keyword, it must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>

<span data-ttu-id="5450e-109">Bu örnek, ikinci bir yönetilmeyen işaretçi yerine dizinler kullanılarak her iki dizinin öğelerine erişir.</span><span class="sxs-lookup"><span data-stu-id="5450e-109">This example accesses the elements of both arrays using indices rather than a second unmanaged pointer.</span></span> <span data-ttu-id="5450e-110">`pSource`Ve `pTarget` işaretçilerinin bildirimi dizileri sabitler.</span><span class="sxs-lookup"><span data-stu-id="5450e-110">The declaration of the `pSource` and `pTarget` pointers pins the arrays.</span></span> <span data-ttu-id="5450e-111">Bu özellik C# 7,3 ile başlayarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5450e-111">This feature is available starting with C# 7.3.</span></span>

## <a name="example"></a><span data-ttu-id="5450e-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="5450e-112">Example</span></span>

[!code-csharp[Struct with embedded inline array](snippets/FixedKeywordExamples.cs#8)]

## <a name="see-also"></a><span data-ttu-id="5450e-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5450e-113">See also</span></span>

- [<span data-ttu-id="5450e-114">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="5450e-114">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="5450e-115">Güvenli Olmayan Kod ve İşaretçiler</span><span class="sxs-lookup"><span data-stu-id="5450e-115">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="5450e-116">-unsafe (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="5450e-116">-unsafe (C# Compiler Options)</span></span>](../../language-reference/compiler-options/unsafe-compiler-option.md)
- [<span data-ttu-id="5450e-117">Çöp toplama</span><span class="sxs-lookup"><span data-stu-id="5450e-117">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
