---
title: 'Nasıl yapılır: Bayt Dizisine Kopyalamak için İşaretçiler Kullanma (C# Programlama Kılavuzu)'
ms.date: 04/20/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6e87a2ec2c04812ac9b998c4c6d9a18d1b097342
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes--c-programming-guide"></a><span data-ttu-id="634ca-102">Nasıl yapılır: Bayt Dizisine Kopyalamak için İşaretçiler Kullanma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="634ca-102">How to: Use Pointers to Copy an Array of Bytes  (C# Programming Guide)</span></span>

<span data-ttu-id="634ca-103">Aşağıdaki örnek, bir diziden bayt kopyalamak için işaretçiler kullanır.</span><span class="sxs-lookup"><span data-stu-id="634ca-103">The following example uses pointers to copy bytes from one array to another.</span></span>

<span data-ttu-id="634ca-104">Bu örnekte [güvensiz](../../language-reference/keywords/unsafe.md) içinde işaretçileri kullanmanıza olanak tanır anahtar sözcüğü `Copy` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="634ca-104">This example uses the [unsafe](../../language-reference/keywords/unsafe.md) keyword, which enables you to use pointers in the `Copy` method.</span></span> <span data-ttu-id="634ca-105">[Sabit](../../language-reference/keywords/fixed-statement.md) deyimi, kaynak ve hedef diziler işaretçiler bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="634ca-105">The [fixed](../../language-reference/keywords/fixed-statement.md) statement is used to declare pointers to the source and destination arrays.</span></span> <span data-ttu-id="634ca-106">`fixed` Deyimi *PIN'ler* kaynak ve hedef konumu, böylece atık toplama tarafından taşınmayacak bellekte dizi.</span><span class="sxs-lookup"><span data-stu-id="634ca-106">The `fixed` statement *pins* the location of the source and destination arrays in memory so that they will not be moved by garbage collection.</span></span> <span data-ttu-id="634ca-107">Bellek blokları dizileri ne zaman sabitlenmemiş `fixed` blok tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="634ca-107">The memory blocks for the arrays are unpinned when the `fixed` block is completed.</span></span> <span data-ttu-id="634ca-108">Çünkü `Copy` Bu örnekte bir yöntem `unsafe` anahtar sözcüğü, onu derlenmelidir [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="634ca-108">Because the `Copy` method in this example uses the `unsafe` keyword, it must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>

<span data-ttu-id="634ca-109">Bu örnekte, ikinci bir yönetilmeyen işaretçi yerine dizinlerini her iki dizi öğeleri erişir.</span><span class="sxs-lookup"><span data-stu-id="634ca-109">This example accesses the elements of both arrays using indices rather than a second unmanaged pointer.</span></span> <span data-ttu-id="634ca-110">Bildirimi `pSource` ve `pTarget` işaretçileri sabitler diziler.</span><span class="sxs-lookup"><span data-stu-id="634ca-110">The declaration of the `pSource` and `pTarget` pointers pins the arrays.</span></span> <span data-ttu-id="634ca-111">Bu özellik, C# 7.3 ile başlayarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="634ca-111">This feature is available starting with C# 7.3.</span></span>

## <a name="example"></a><span data-ttu-id="634ca-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="634ca-112">Example</span></span>

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#8)]

## <a name="see-also"></a><span data-ttu-id="634ca-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="634ca-113">See Also</span></span>
 [<span data-ttu-id="634ca-114">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="634ca-114">C# Programming Guide</span></span>](../index.md)  
 [<span data-ttu-id="634ca-115">Güvenli Olmayan Kod ve İşaretçiler</span><span class="sxs-lookup"><span data-stu-id="634ca-115">Unsafe Code and Pointers</span></span>](index.md)  
 [<span data-ttu-id="634ca-116">-unsafe (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="634ca-116">-unsafe (C# Compiler Options)</span></span>](../../language-reference/compiler-options/unsafe-compiler-option.md)  
 [<span data-ttu-id="634ca-117">Atık Toplama</span><span class="sxs-lookup"><span data-stu-id="634ca-117">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)  
