---
title: try-catch-finally- C# Reference
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- catch-finally_CSharpKeyword
- catch-finally
helpviewer_keywords:
- finally blocks [C#]
- try-catch statement [C#]
ms.assetid: a1b443b0-ff7a-43ab-b835-0cc9bfbd15ca
ms.openlocfilehash: 9f2c82fb140e18454491660d17b570db0a8a2aef
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70168585"
---
# <a name="try-catch-finally-c-reference"></a><span data-ttu-id="14319-102">try-catch-finally (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="14319-102">try-catch-finally (C# Reference)</span></span>

<span data-ttu-id="14319-103">`catch` `try` Ve `finally` `catch` birlikte ortak kullanımı, bir blokta kaynak almak ve kullanmak, bir bloktaki olağanüstü koşullara uğramak ve bloktaki kaynakları serbest bırakmektir. `finally`</span><span class="sxs-lookup"><span data-stu-id="14319-103">A common usage of `catch` and `finally` together is to obtain and use resources in a `try` block, deal with exceptional circumstances in a `catch` block, and release the resources in the `finally` block.</span></span>

 <span data-ttu-id="14319-104">Özel durumları yeniden oluşturma hakkında daha fazla bilgi ve örnek için bkz. [try-catch](try-catch.md) ve [özel durum atma](../../../standard/exceptions/index.md).</span><span class="sxs-lookup"><span data-stu-id="14319-104">For more information and examples on re-throwing exceptions, see [try-catch](try-catch.md) and [Throwing Exceptions](../../../standard/exceptions/index.md).</span></span> <span data-ttu-id="14319-105">`finally` Blok hakkında daha fazla bilgi için bkz. [try-finally](try-finally.md).</span><span class="sxs-lookup"><span data-stu-id="14319-105">For more information about the `finally` block, see [try-finally](try-finally.md).</span></span>

## <a name="example"></a><span data-ttu-id="14319-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="14319-106">Example</span></span>

[!code-csharp[csrefKeywordsExceptions#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#1)]  

## <a name="c-language-specification"></a><span data-ttu-id="14319-107">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="14319-107">C# language specification</span></span>

<span data-ttu-id="14319-108">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [TRY deyimin](~/_csharplang/spec/statements.md#the-try-statement) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="14319-108">For more information, see [The try statement](~/_csharplang/spec/statements.md#the-try-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="14319-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="14319-109">See also</span></span>

- [<span data-ttu-id="14319-110">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="14319-110">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="14319-111">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="14319-111">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="14319-112">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="14319-112">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="14319-113">try, throw ve catch Deyimleri (C++)</span><span class="sxs-lookup"><span data-stu-id="14319-113">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [<span data-ttu-id="14319-114">throw</span><span class="sxs-lookup"><span data-stu-id="14319-114">throw</span></span>](throw.md)
- [<span data-ttu-id="14319-115">Nasıl yapılır: Özel durumları açık olarak oluştur</span><span class="sxs-lookup"><span data-stu-id="14319-115">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
- [<span data-ttu-id="14319-116">using Deyimi</span><span class="sxs-lookup"><span data-stu-id="14319-116">using Statement</span></span>](using-statement.md)
