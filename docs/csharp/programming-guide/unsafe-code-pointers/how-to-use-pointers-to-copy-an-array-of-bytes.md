---
title: 'Nasıl yapılır: Bayt Dizisine Kopyalamak için İşaretçiler Kullanma (C# Programlama Kılavuzu)'
ms.date: 04/20/2018
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.openlocfilehash: 061bbbc4557cb25d39edfb1f6235bb065a5de7bd
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43541464"
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes--c-programming-guide"></a><span data-ttu-id="8c590-102">Nasıl yapılır: Bayt Dizisine Kopyalamak için İşaretçiler Kullanma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="8c590-102">How to: Use Pointers to Copy an Array of Bytes  (C# Programming Guide)</span></span>

<span data-ttu-id="8c590-103">Aşağıdaki örnek, bayt bir diziden kopyalamak için işaretçiler kullanır.</span><span class="sxs-lookup"><span data-stu-id="8c590-103">The following example uses pointers to copy bytes from one array to another.</span></span>

<span data-ttu-id="8c590-104">Bu örnekte [güvenli olmayan](../../language-reference/keywords/unsafe.md) işaretçiler, kullanmanıza olanak tanıyan anahtar sözcüğü `Copy` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8c590-104">This example uses the [unsafe](../../language-reference/keywords/unsafe.md) keyword, which enables you to use pointers in the `Copy` method.</span></span> <span data-ttu-id="8c590-105">[Sabit](../../language-reference/keywords/fixed-statement.md) deyimi, kaynak ve hedef dizi işaretçileri bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8c590-105">The [fixed](../../language-reference/keywords/fixed-statement.md) statement is used to declare pointers to the source and destination arrays.</span></span> <span data-ttu-id="8c590-106">`fixed` Deyimi *PIN'ler* çöp toplamadan taşınmayacak böylece bellekte konumunu kaynak ve hedef dizi.</span><span class="sxs-lookup"><span data-stu-id="8c590-106">The `fixed` statement *pins* the location of the source and destination arrays in memory so that they will not be moved by garbage collection.</span></span> <span data-ttu-id="8c590-107">Bellek bloklarını diziler için ne zaman sabitlenmemiş `fixed` blok tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="8c590-107">The memory blocks for the arrays are unpinned when the `fixed` block is completed.</span></span> <span data-ttu-id="8c590-108">Çünkü `Copy` Bu örnekte kullanmaktadır `unsafe` anahtar sözcüğü, onu derlenmelidir [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="8c590-108">Because the `Copy` method in this example uses the `unsafe` keyword, it must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>

<span data-ttu-id="8c590-109">Bu örnekte, ikinci bir yönetilmeyen işaretçi yerine dizinleri hem dizilerin öğelerine erişir.</span><span class="sxs-lookup"><span data-stu-id="8c590-109">This example accesses the elements of both arrays using indices rather than a second unmanaged pointer.</span></span> <span data-ttu-id="8c590-110">Bildirimi `pSource` ve `pTarget` işaretçileri, dizileri sabitler.</span><span class="sxs-lookup"><span data-stu-id="8c590-110">The declaration of the `pSource` and `pTarget` pointers pins the arrays.</span></span> <span data-ttu-id="8c590-111">Bu özellik, C# 7.3 ile başlayan kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8c590-111">This feature is available starting with C# 7.3.</span></span>

## <a name="example"></a><span data-ttu-id="8c590-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="8c590-112">Example</span></span>

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#8)]

## <a name="see-also"></a><span data-ttu-id="8c590-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8c590-113">See Also</span></span>

- [<span data-ttu-id="8c590-114">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="8c590-114">C# Programming Guide</span></span>](../index.md)  
- [<span data-ttu-id="8c590-115">Güvenli Olmayan Kod ve İşaretçiler</span><span class="sxs-lookup"><span data-stu-id="8c590-115">Unsafe Code and Pointers</span></span>](index.md)  
- [<span data-ttu-id="8c590-116">-unsafe (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="8c590-116">-unsafe (C# Compiler Options)</span></span>](../../language-reference/compiler-options/unsafe-compiler-option.md)  
- [<span data-ttu-id="8c590-117">Atık Toplama</span><span class="sxs-lookup"><span data-stu-id="8c590-117">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)  
