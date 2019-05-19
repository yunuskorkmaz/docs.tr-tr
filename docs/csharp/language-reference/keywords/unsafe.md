---
title: güven olmayan anahtar sözcük - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- unsafe_CSharpKeyword
- unsafe
helpviewer_keywords:
- unsafe keyword [C#]
ms.assetid: 7e818009-1c6e-4b9e-b769-3728a01586a0
ms.openlocfilehash: bca12c1dd8c79a5ae17e4a9b7b75d3c7b302fb89
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65875868"
---
# <a name="unsafe-c-reference"></a><span data-ttu-id="7ca65-102">unsafe (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="7ca65-102">unsafe (C# Reference)</span></span>

<span data-ttu-id="7ca65-103">`unsafe` Anahtar sözcüğü, işaretçileri içeren tüm işlemler için gerekli olan güvensiz bir bağlamı gösterir.</span><span class="sxs-lookup"><span data-stu-id="7ca65-103">The `unsafe` keyword denotes an unsafe context, which is required for any operation involving pointers.</span></span> <span data-ttu-id="7ca65-104">Daha fazla bilgi için [güvenli olmayan kod ve işaretçiler](../../programming-guide/unsafe-code-pointers/index.md).</span><span class="sxs-lookup"><span data-stu-id="7ca65-104">For more information, see [Unsafe Code and Pointers](../../programming-guide/unsafe-code-pointers/index.md).</span></span>

<span data-ttu-id="7ca65-105">Kullanabileceğiniz `unsafe` bildirimi bir tür veya üye değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="7ca65-105">You can use the `unsafe` modifier in the declaration of a type or a member.</span></span> <span data-ttu-id="7ca65-106">Türe veya üyeye tüm metinsel kapsamını, bu nedenle güvenli olmayan bir bağlam kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="7ca65-106">The entire textual extent of the type or member is therefore considered an unsafe context.</span></span> <span data-ttu-id="7ca65-107">Örneğin, aşağıdaki ile bildirilen bir yöntemi olan `unsafe` değiştiricisi:</span><span class="sxs-lookup"><span data-stu-id="7ca65-107">For example, the following is a method declared with the `unsafe` modifier:</span></span>

```csharp
unsafe static void FastCopy(byte[] src, byte[] dst, int count)
{
    // Unsafe context: can use pointers here.
}
```

<span data-ttu-id="7ca65-108">İşaretçiler, parametre listesinde kullanılabilmesi için güvenli olmayan bir bağlam kapsamını parametre listesinden, yöntemin sonuna kadar genişletir:</span><span class="sxs-lookup"><span data-stu-id="7ca65-108">The scope of the unsafe context extends from the parameter list to the end of the method, so pointers can also be used in the parameter list:</span></span>

```csharp
unsafe static void FastCopy ( byte* ps, byte* pd, int count ) {...}
```

<span data-ttu-id="7ca65-109">Güvenli olmayan bir blok, bu blok içinde bir güvenli olmayan kod kullanımını etkinleştirmek için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7ca65-109">You can also use an unsafe block to enable the use of an unsafe code inside this block.</span></span> <span data-ttu-id="7ca65-110">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="7ca65-110">For example:</span></span>

```csharp
unsafe
{
    // Unsafe context: can use pointers here.
}
```

<span data-ttu-id="7ca65-111">Güvenli olmayan kod olarak derlemek için belirtmelisiniz [ `-unsafe` ](../compiler-options/unsafe-compiler-option.md) derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="7ca65-111">To compile unsafe code, you must specify the [`-unsafe`](../compiler-options/unsafe-compiler-option.md) compiler option.</span></span> <span data-ttu-id="7ca65-112">Güvenli olmayan kod ortak dil çalışma zamanı tarafından doğrulanabilir değil.</span><span class="sxs-lookup"><span data-stu-id="7ca65-112">Unsafe code is not verifiable by the common language runtime.</span></span>

## <a name="example"></a><span data-ttu-id="7ca65-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="7ca65-113">Example</span></span>

[!code-csharp[csrefKeywordsModifiers#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#22)]

## <a name="c-language-specification"></a><span data-ttu-id="7ca65-114">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="7ca65-114">C# language specification</span></span>

<span data-ttu-id="7ca65-115">Daha fazla bilgi için [güvenli olmayan kod](~/_csharplang/spec/unsafe-code.md) içinde [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="7ca65-115">For more information, see [Unsafe code](~/_csharplang/spec/unsafe-code.md) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="7ca65-116">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="7ca65-116">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="7ca65-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7ca65-117">See also</span></span>

- [<span data-ttu-id="7ca65-118">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="7ca65-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="7ca65-119">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="7ca65-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="7ca65-120">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="7ca65-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="7ca65-121">fixed Deyimi</span><span class="sxs-lookup"><span data-stu-id="7ca65-121">fixed Statement</span></span>](fixed-statement.md)
- [<span data-ttu-id="7ca65-122">Güvenli Olmayan Kod ve İşaretçiler</span><span class="sxs-lookup"><span data-stu-id="7ca65-122">Unsafe Code and Pointers</span></span>](../../programming-guide/unsafe-code-pointers/index.md)
- [<span data-ttu-id="7ca65-123">Sabit Boyutlu Arabellekler</span><span class="sxs-lookup"><span data-stu-id="7ca65-123">Fixed Size Buffers</span></span>](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
