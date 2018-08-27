---
title: işleç anahtar sözcüğü (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- operator_CSharpKeyword
- operator
helpviewer_keywords:
- operator keyword [C#]
ms.assetid: 59218cce-e90e-42f6-a6bb-30300981b86a
ms.openlocfilehash: c3bfada235993670bf158fe9803a09707b2b3251
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42929878"
---
# <a name="operator-c-reference"></a><span data-ttu-id="03f5b-102">operator (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="03f5b-102">operator (C# Reference)</span></span>

<span data-ttu-id="03f5b-103">Kullanım `operator` anahtar sözcük yerleşik bir işleç aşırı yüklemesi veya bir kullanıcı tanımlı dönüştürme bir class veya struct bildiriminde sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="03f5b-103">Use the `operator` keyword to overload a built-in operator or to provide a user-defined conversion in a class or struct declaration.</span></span>

## <a name="example"></a><span data-ttu-id="03f5b-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="03f5b-104">Example</span></span>

<span data-ttu-id="03f5b-105">Kesirli sayılar için çok basitleştirilmiş bir sınıf verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="03f5b-105">The following is a very simplified class for fractional numbers.</span></span> <span data-ttu-id="03f5b-106">Aşırı `+` ve `*` kesirli toplama ve çarpma gerçekleştirmek için işleçler ve ayrıca bir dönüştürme işleci bu dönüştürür sağlar bir `Fraction` için yazın bir `double` türü.</span><span class="sxs-lookup"><span data-stu-id="03f5b-106">It overloads the `+` and `*` operators to perform fractional addition and multiplication, and also provides a conversion operator that converts a `Fraction` type to a `double` type.</span></span>

[!code-csharp[csrefKeywordsConversion#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#6)]

## <a name="c-language-specification"></a><span data-ttu-id="03f5b-107">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="03f5b-107">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="03f5b-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="03f5b-108">See also</span></span>

- [<span data-ttu-id="03f5b-109">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="03f5b-109">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="03f5b-110">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="03f5b-110">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="03f5b-111">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="03f5b-111">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="03f5b-112">implicit</span><span class="sxs-lookup"><span data-stu-id="03f5b-112">implicit</span></span>](implicit.md)
- [<span data-ttu-id="03f5b-113">explicit</span><span class="sxs-lookup"><span data-stu-id="03f5b-113">explicit</span></span>](explicit.md)
- [<span data-ttu-id="03f5b-114">Nasıl yapılır: Yapılar Arasında Kullanıcı Tanımlı Dönüştürmeler Uygulama</span><span class="sxs-lookup"><span data-stu-id="03f5b-114">How to: Implement User-Defined Conversions Between Structs</span></span>](../../programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)
