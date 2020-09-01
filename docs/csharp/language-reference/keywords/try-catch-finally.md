---
description: try-catch-finally-C# başvurusu
title: try-catch-finally-C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- catch-finally_CSharpKeyword
- catch-finally
helpviewer_keywords:
- finally blocks [C#]
- try-catch statement [C#]
ms.assetid: a1b443b0-ff7a-43ab-b835-0cc9bfbd15ca
ms.openlocfilehash: 6e85330e12c53e0728ef671530709748090ebe02
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89142017"
---
# <a name="try-catch-finally-c-reference"></a><span data-ttu-id="8ce71-103">try-catch-finally (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="8ce71-103">try-catch-finally (C# Reference)</span></span>

<span data-ttu-id="8ce71-104">Ve birlikte ortak kullanımı `catch` , `finally` bir blokta kaynak almak ve kullanmak `try` , bir bloktaki olağanüstü koşullara uğramak `catch` ve bloktaki kaynakları serbest bırakmektir `finally` .</span><span class="sxs-lookup"><span data-stu-id="8ce71-104">A common usage of `catch` and `finally` together is to obtain and use resources in a `try` block, deal with exceptional circumstances in a `catch` block, and release the resources in the `finally` block.</span></span>

 <span data-ttu-id="8ce71-105">Özel durumları yeniden oluşturma hakkında daha fazla bilgi ve örnek için bkz. [try-catch](try-catch.md) ve [özel durum atma](../../../standard/exceptions/index.md).</span><span class="sxs-lookup"><span data-stu-id="8ce71-105">For more information and examples on re-throwing exceptions, see [try-catch](try-catch.md) and [Throwing Exceptions](../../../standard/exceptions/index.md).</span></span> <span data-ttu-id="8ce71-106">Blok hakkında daha fazla bilgi için `finally` bkz. [try-finally](try-finally.md).</span><span class="sxs-lookup"><span data-stu-id="8ce71-106">For more information about the `finally` block, see [try-finally](try-finally.md).</span></span>

## <a name="example"></a><span data-ttu-id="8ce71-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="8ce71-107">Example</span></span>

[!code-csharp[csrefKeywordsExceptions#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#1)]  

## <a name="c-language-specification"></a><span data-ttu-id="8ce71-108">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="8ce71-108">C# language specification</span></span>

<span data-ttu-id="8ce71-109">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [TRY deyimin](~/_csharplang/spec/statements.md#the-try-statement) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="8ce71-109">For more information, see [The try statement](~/_csharplang/spec/statements.md#the-try-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8ce71-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8ce71-110">See also</span></span>

- [<span data-ttu-id="8ce71-111">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="8ce71-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="8ce71-112">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="8ce71-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="8ce71-113">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="8ce71-113">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="8ce71-114">try, throw ve catch Deyimleri (C++)</span><span class="sxs-lookup"><span data-stu-id="8ce71-114">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [<span data-ttu-id="8ce71-115">throw</span><span class="sxs-lookup"><span data-stu-id="8ce71-115">throw</span></span>](throw.md)
- [<span data-ttu-id="8ce71-116">Nasıl yapılır: Açıkça Özel Durumlar Oluşturma</span><span class="sxs-lookup"><span data-stu-id="8ce71-116">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
- [<span data-ttu-id="8ce71-117">using Deyimi</span><span class="sxs-lookup"><span data-stu-id="8ce71-117">using Statement</span></span>](using-statement.md)
