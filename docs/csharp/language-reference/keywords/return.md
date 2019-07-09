---
title: return deyimi - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- return_CSharpKeyword
- return
helpviewer_keywords:
- return statement [C#]
- return keyword [C#]
ms.assetid: 6da6e152-5b58-4448-8f3f-470dd0617ecd
ms.openlocfilehash: a845ce257bf7f0cf0e64d6815b2278f6cec946e7
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661609"
---
# <a name="return-c-reference"></a><span data-ttu-id="4e234-102">return (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="4e234-102">return (C# Reference)</span></span>

<span data-ttu-id="4e234-103">`return` Deyimi yöntemin hangi görüntülenir ve çağıran Metoda döndürür denetim yürütülmesini sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="4e234-103">The `return` statement terminates execution of the method in which it appears and returns control to the calling method.</span></span> <span data-ttu-id="4e234-104">Ayrıca, isteğe bağlı bir değer de döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="4e234-104">It can also return an optional value.</span></span> <span data-ttu-id="4e234-105">Yöntem ise bir `void` türü `return` ifade atlanabilir.</span><span class="sxs-lookup"><span data-stu-id="4e234-105">If the method is a `void` type, the `return` statement can be omitted.</span></span>

 <span data-ttu-id="4e234-106">Return deyimi içinde ise bir `try` bloğu `finally` bloğu, varsa, yürütülecek önce denetimini çağıran Metoda döndürür.</span><span class="sxs-lookup"><span data-stu-id="4e234-106">If the return statement is inside a `try` block, the `finally` block, if one exists, will be executed before control returns to the calling method.</span></span>

## <a name="example"></a><span data-ttu-id="4e234-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="4e234-107">Example</span></span>

 <span data-ttu-id="4e234-108">Aşağıdaki örnekte, yöntem `CalculateArea()` yerel değişkeni döndürür `area` olarak bir `double` değeri.</span><span class="sxs-lookup"><span data-stu-id="4e234-108">In the following example, the method `CalculateArea()` returns the local variable `area` as a `double` value.</span></span>

[!code-csharp[csrefKeywordsJump#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#6)]  

## <a name="c-language-specification"></a><span data-ttu-id="4e234-109">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="4e234-109">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="4e234-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4e234-110">See also</span></span>

- [<span data-ttu-id="4e234-111">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="4e234-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="4e234-112">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="4e234-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="4e234-113">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="4e234-113">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="4e234-114">return Deyimi</span><span class="sxs-lookup"><span data-stu-id="4e234-114">return Statement</span></span>](/cpp/cpp/return-statement-cpp)
