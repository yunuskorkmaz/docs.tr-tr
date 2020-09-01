---
description: Return ekstresi-C# başvurusu
title: Return ekstresi-C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- return_CSharpKeyword
- return
helpviewer_keywords:
- return statement [C#]
- return keyword [C#]
ms.assetid: 6da6e152-5b58-4448-8f3f-470dd0617ecd
ms.openlocfilehash: 486db846304c0972942ff58f3d5b276083681abe
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89137012"
---
# <a name="return-c-reference"></a><span data-ttu-id="98500-103">return (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="98500-103">return (C# Reference)</span></span>

<span data-ttu-id="98500-104">`return`İfadesi, göründüğü yöntemin yürütmesini sonlandırır ve çağırma yöntemine denetim döndürür.</span><span class="sxs-lookup"><span data-stu-id="98500-104">The `return` statement terminates execution of the method in which it appears and returns control to the calling method.</span></span> <span data-ttu-id="98500-105">Ayrıca, isteğe bağlı bir değer de döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="98500-105">It can also return an optional value.</span></span> <span data-ttu-id="98500-106">Yöntem bir `void` tür ise, `return` ifade atlanabilir.</span><span class="sxs-lookup"><span data-stu-id="98500-106">If the method is a `void` type, the `return` statement can be omitted.</span></span>

 <span data-ttu-id="98500-107">Return yöntemi bir blok içindeyse, bir blok varsa, `try` `finally` Denetim çağırma yöntemine döndürmeden önce yürütülür.</span><span class="sxs-lookup"><span data-stu-id="98500-107">If the return statement is inside a `try` block, the `finally` block, if one exists, will be executed before control returns to the calling method.</span></span>

## <a name="example"></a><span data-ttu-id="98500-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="98500-108">Example</span></span>

 <span data-ttu-id="98500-109">Aşağıdaki örnekte, yöntemi `CalculateArea()` yerel değişkeni `area` bir değer olarak döndürür `double` .</span><span class="sxs-lookup"><span data-stu-id="98500-109">In the following example, the method `CalculateArea()` returns the local variable `area` as a `double` value.</span></span>

[!code-csharp[csrefKeywordsJump#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#6)]  

## <a name="c-language-specification"></a><span data-ttu-id="98500-110">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="98500-110">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="98500-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="98500-111">See also</span></span>

- [<span data-ttu-id="98500-112">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="98500-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="98500-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="98500-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="98500-114">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="98500-114">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="98500-115">Return ekstresi</span><span class="sxs-lookup"><span data-stu-id="98500-115">return Statement</span></span>](/cpp/cpp/return-statement-cpp)
