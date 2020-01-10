---
title: try-catch-finally- C# Reference
ms.date: 07/20/2015
f1_keywords:
- catch-finally_CSharpKeyword
- catch-finally
helpviewer_keywords:
- finally blocks [C#]
- try-catch statement [C#]
ms.assetid: a1b443b0-ff7a-43ab-b835-0cc9bfbd15ca
ms.openlocfilehash: 5d98f6967595c7c32b23ba5422a8d9ca79f7f54c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713046"
---
# <a name="try-catch-finally-c-reference"></a><span data-ttu-id="3d73e-102">try-catch-finally (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="3d73e-102">try-catch-finally (C# Reference)</span></span>

<span data-ttu-id="3d73e-103">`catch` ve `finally` birlikte ortak kullanımı, bir `try` bloğunda kaynak almak ve kullanmak, bir `catch` bloğunda olağanüstü koşullara uğramak ve kaynakları `finally` bloğunda serbest bırakmektir.</span><span class="sxs-lookup"><span data-stu-id="3d73e-103">A common usage of `catch` and `finally` together is to obtain and use resources in a `try` block, deal with exceptional circumstances in a `catch` block, and release the resources in the `finally` block.</span></span>

 <span data-ttu-id="3d73e-104">Özel durumları yeniden oluşturma hakkında daha fazla bilgi ve örnek için bkz. [try-catch](try-catch.md) ve [özel durum atma](../../../standard/exceptions/index.md).</span><span class="sxs-lookup"><span data-stu-id="3d73e-104">For more information and examples on re-throwing exceptions, see [try-catch](try-catch.md) and [Throwing Exceptions](../../../standard/exceptions/index.md).</span></span> <span data-ttu-id="3d73e-105">`finally` bloğu hakkında daha fazla bilgi için bkz. [try-finally](try-finally.md).</span><span class="sxs-lookup"><span data-stu-id="3d73e-105">For more information about the `finally` block, see [try-finally](try-finally.md).</span></span>

## <a name="example"></a><span data-ttu-id="3d73e-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="3d73e-106">Example</span></span>

[!code-csharp[csrefKeywordsExceptions#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#1)]  

## <a name="c-language-specification"></a><span data-ttu-id="3d73e-107">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="3d73e-107">C# language specification</span></span>

<span data-ttu-id="3d73e-108">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [TRY deyimin](~/_csharplang/spec/statements.md#the-try-statement) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="3d73e-108">For more information, see [The try statement](~/_csharplang/spec/statements.md#the-try-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3d73e-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3d73e-109">See also</span></span>

- [<span data-ttu-id="3d73e-110">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="3d73e-110">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="3d73e-111">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="3d73e-111">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="3d73e-112">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="3d73e-112">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="3d73e-113">try, throw ve catch Deyimleri (C++)</span><span class="sxs-lookup"><span data-stu-id="3d73e-113">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [<span data-ttu-id="3d73e-114">throw</span><span class="sxs-lookup"><span data-stu-id="3d73e-114">throw</span></span>](throw.md)
- [<span data-ttu-id="3d73e-115">Nasıl yapılır: Açıkça Özel Durumlar Oluşturma</span><span class="sxs-lookup"><span data-stu-id="3d73e-115">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
- [<span data-ttu-id="3d73e-116">using Deyimi</span><span class="sxs-lookup"><span data-stu-id="3d73e-116">using Statement</span></span>](using-statement.md)
