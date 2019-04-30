---
title: 'Nasıl yapılır: -Bayt dizisine kopyalamak için işaretçiler kullanma C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 04/20/2018
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.openlocfilehash: d174f51fa1709a70b98473a4dbbad89b9c62c22a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61708920"
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes--c-programming-guide"></a><span data-ttu-id="e9726-102">Nasıl yapılır: Bir bayt dizisine kopyalamak için işaretçiler kullanma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="e9726-102">How to: Use Pointers to Copy an Array of Bytes  (C# Programming Guide)</span></span>

<span data-ttu-id="e9726-103">Aşağıdaki örnek, bayt bir diziden kopyalamak için işaretçiler kullanır.</span><span class="sxs-lookup"><span data-stu-id="e9726-103">The following example uses pointers to copy bytes from one array to another.</span></span>

<span data-ttu-id="e9726-104">Bu örnekte [güvenli olmayan](../../language-reference/keywords/unsafe.md) işaretçiler, kullanmanıza olanak tanıyan anahtar sözcüğü `Copy` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e9726-104">This example uses the [unsafe](../../language-reference/keywords/unsafe.md) keyword, which enables you to use pointers in the `Copy` method.</span></span> <span data-ttu-id="e9726-105">[Sabit](../../language-reference/keywords/fixed-statement.md) deyimi, kaynak ve hedef dizi işaretçileri bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e9726-105">The [fixed](../../language-reference/keywords/fixed-statement.md) statement is used to declare pointers to the source and destination arrays.</span></span> <span data-ttu-id="e9726-106">`fixed` Deyimi *PIN'ler* çöp toplamadan taşınmayacak böylece bellekte konumunu kaynak ve hedef dizi.</span><span class="sxs-lookup"><span data-stu-id="e9726-106">The `fixed` statement *pins* the location of the source and destination arrays in memory so that they will not be moved by garbage collection.</span></span> <span data-ttu-id="e9726-107">Bellek bloklarını diziler için ne zaman sabitlenmemiş `fixed` blok tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="e9726-107">The memory blocks for the arrays are unpinned when the `fixed` block is completed.</span></span> <span data-ttu-id="e9726-108">Çünkü `Copy` Bu örnekte kullanmaktadır `unsafe` anahtar sözcüğü, onu derlenmelidir [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="e9726-108">Because the `Copy` method in this example uses the `unsafe` keyword, it must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>

<span data-ttu-id="e9726-109">Bu örnekte, ikinci bir yönetilmeyen işaretçi yerine dizinleri hem dizilerin öğelerine erişir.</span><span class="sxs-lookup"><span data-stu-id="e9726-109">This example accesses the elements of both arrays using indices rather than a second unmanaged pointer.</span></span> <span data-ttu-id="e9726-110">Bildirimi `pSource` ve `pTarget` işaretçileri, dizileri sabitler.</span><span class="sxs-lookup"><span data-stu-id="e9726-110">The declaration of the `pSource` and `pTarget` pointers pins the arrays.</span></span> <span data-ttu-id="e9726-111">Bu özellik, C# 7.3 ile başlayan kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e9726-111">This feature is available starting with C# 7.3.</span></span>

## <a name="example"></a><span data-ttu-id="e9726-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="e9726-112">Example</span></span>

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#8)]

## <a name="see-also"></a><span data-ttu-id="e9726-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e9726-113">See also</span></span>

- [<span data-ttu-id="e9726-114">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e9726-114">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="e9726-115">Güvenli Olmayan Kod ve İşaretçiler</span><span class="sxs-lookup"><span data-stu-id="e9726-115">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="e9726-116">-unsafe (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="e9726-116">-unsafe (C# Compiler Options)</span></span>](../../language-reference/compiler-options/unsafe-compiler-option.md)
- [<span data-ttu-id="e9726-117">Atık Toplama</span><span class="sxs-lookup"><span data-stu-id="e9726-117">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
