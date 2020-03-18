---
title: try-catch-finally - C# Referans
ms.date: 07/20/2015
f1_keywords:
- catch-finally_CSharpKeyword
- catch-finally
helpviewer_keywords:
- finally blocks [C#]
- try-catch statement [C#]
ms.assetid: a1b443b0-ff7a-43ab-b835-0cc9bfbd15ca
ms.openlocfilehash: 5d98f6967595c7c32b23ba5422a8d9ca79f7f54c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713046"
---
# <a name="try-catch-finally-c-reference"></a><span data-ttu-id="f5a1a-102">try-catch-finally (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="f5a1a-102">try-catch-finally (C# Reference)</span></span>

<span data-ttu-id="f5a1a-103">Ortak kullanım `catch` ve `finally` birlikte bir `try` blok kaynakları elde etmek ve kullanmak, `catch` bir blok istisnai `finally` koşullar ile başa çıkmak ve bloktaki kaynakları serbest bırakmak.</span><span class="sxs-lookup"><span data-stu-id="f5a1a-103">A common usage of `catch` and `finally` together is to obtain and use resources in a `try` block, deal with exceptional circumstances in a `catch` block, and release the resources in the `finally` block.</span></span>

 <span data-ttu-id="f5a1a-104">Yeniden atma özel durumları hakkında daha fazla bilgi ve örnekler için [try-catch](try-catch.md) ve [Atma Özel Durumları'na](../../../standard/exceptions/index.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="f5a1a-104">For more information and examples on re-throwing exceptions, see [try-catch](try-catch.md) and [Throwing Exceptions](../../../standard/exceptions/index.md).</span></span> <span data-ttu-id="f5a1a-105">`finally` Blok hakkında daha fazla bilgi için [try-finally'a](try-finally.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="f5a1a-105">For more information about the `finally` block, see [try-finally](try-finally.md).</span></span>

## <a name="example"></a><span data-ttu-id="f5a1a-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="f5a1a-106">Example</span></span>

[!code-csharp[csrefKeywordsExceptions#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#1)]  

## <a name="c-language-specification"></a><span data-ttu-id="f5a1a-107">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="f5a1a-107">C# language specification</span></span>

<span data-ttu-id="f5a1a-108">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [try deyimi](~/_csharplang/spec/statements.md#the-try-statement) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="f5a1a-108">For more information, see [The try statement](~/_csharplang/spec/statements.md#the-try-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f5a1a-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f5a1a-109">See also</span></span>

- [<span data-ttu-id="f5a1a-110">C# Referans</span><span class="sxs-lookup"><span data-stu-id="f5a1a-110">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f5a1a-111">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f5a1a-111">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f5a1a-112">C# Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="f5a1a-112">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="f5a1a-113">try, throw ve catch Deyimleri (C++)</span><span class="sxs-lookup"><span data-stu-id="f5a1a-113">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [<span data-ttu-id="f5a1a-114">throw</span><span class="sxs-lookup"><span data-stu-id="f5a1a-114">throw</span></span>](throw.md)
- [<span data-ttu-id="f5a1a-115">Nasıl yapılır: Açıkça Özel Durumlar Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f5a1a-115">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
- [<span data-ttu-id="f5a1a-116">Ekstresi'ni kullanma</span><span class="sxs-lookup"><span data-stu-id="f5a1a-116">using Statement</span></span>](using-statement.md)
