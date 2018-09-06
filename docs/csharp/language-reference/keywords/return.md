---
title: return deyimi (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- return_CSharpKeyword
- return
helpviewer_keywords:
- return statement [C#]
- return keyword [C#]
ms.assetid: 6da6e152-5b58-4448-8f3f-470dd0617ecd
ms.openlocfilehash: 0d20da39d3f56220c4499f699e542bd24ded93ca
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43742008"
---
# <a name="return-c-reference"></a><span data-ttu-id="faeda-102">return (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="faeda-102">return (C# Reference)</span></span>

<span data-ttu-id="faeda-103">`return` Deyimi yöntemin hangi görüntülenir ve çağıran Metoda döndürür denetim yürütülmesini sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="faeda-103">The `return` statement terminates execution of the method in which it appears and returns control to the calling method.</span></span> <span data-ttu-id="faeda-104">Ayrıca, isteğe bağlı bir değer de döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="faeda-104">It can also return an optional value.</span></span> <span data-ttu-id="faeda-105">Yöntem ise bir `void` türü `return` ifade atlanabilir.</span><span class="sxs-lookup"><span data-stu-id="faeda-105">If the method is a `void` type, the `return` statement can be omitted.</span></span>

 <span data-ttu-id="faeda-106">Return deyimi içinde ise bir `try` bloğu `finally` bloğu, varsa, yürütülecek önce denetimini çağıran Metoda döndürür.</span><span class="sxs-lookup"><span data-stu-id="faeda-106">If the return statement is inside a `try` block, the `finally` block, if one exists, will be executed before control returns to the calling method.</span></span>

## <a name="example"></a><span data-ttu-id="faeda-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="faeda-107">Example</span></span>

 <span data-ttu-id="faeda-108">Aşağıdaki örnekte, yöntem `CalculateArea()` yerel değişkeni döndürür `area` olarak bir [çift](double.md) değeri.</span><span class="sxs-lookup"><span data-stu-id="faeda-108">In the following example, the method `CalculateArea()` returns the local variable `area` as a [double](double.md) value.</span></span>

[!code-csharp[csrefKeywordsJump#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#6)]  

## <a name="c-language-specification"></a><span data-ttu-id="faeda-109">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="faeda-109">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="faeda-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="faeda-110">See also</span></span>

- [<span data-ttu-id="faeda-111">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="faeda-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="faeda-112">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="faeda-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="faeda-113">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="faeda-113">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="faeda-114">return Deyimi</span><span class="sxs-lookup"><span data-stu-id="faeda-114">return Statement</span></span>](/cpp/cpp/return-statement-cpp)
- [<span data-ttu-id="faeda-115">Atlama Deyimleri</span><span class="sxs-lookup"><span data-stu-id="faeda-115">Jump Statements</span></span>](jump-statements.md)
