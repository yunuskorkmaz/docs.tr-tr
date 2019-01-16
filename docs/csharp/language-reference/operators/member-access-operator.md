---
title: biçimindeki telefon numarasıdır. Operator - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ._CSharpKeyword
helpviewer_keywords:
- member access operator (.) [C#]
- . operator [C#]
- dot operator (.) [C#]
ms.assetid: a1f54b52-b686-4ae5-a48e-a2a9ebd0eb7b
ms.openlocfilehash: a59f69d0349a054c8c2a5b701b8f63df113a6580
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333726"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="79363-103">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="79363-103">.</span></span> <span data-ttu-id="79363-104">operator (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="79363-104">operator (C# Reference)</span></span>

<span data-ttu-id="79363-105">Nokta işleci (`.`) üye erişimi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="79363-105">The dot operator (`.`) is used for member access.</span></span> <span data-ttu-id="79363-106">Dot işleci, bir tür veya ad alanı üyesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="79363-106">The dot operator specifies a member of a type or namespace.</span></span> <span data-ttu-id="79363-107">Örneğin, nokta işleci, .NET Framework sınıf kitaplıkları belirli yöntemlerinde erişmek için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="79363-107">For example, the dot operator is used to access specific methods within the .NET Framework class libraries:</span></span>

[!code-csharp[csRefOperators#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#16)]

<span data-ttu-id="79363-108">Örneğin, aşağıdaki sınıf göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="79363-108">For example, consider the following class:</span></span>

[!code-csharp[csRefOperators#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#17)]

[!code-csharp[csRefOperators#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#18)]

<span data-ttu-id="79363-109">Değişken `s` iki üyesi olan `a` ve `b`; bunlara erişmek için nokta işlecini kullanın:</span><span class="sxs-lookup"><span data-stu-id="79363-109">The variable `s` has two members, `a` and `b`; to access them, use the dot operator:</span></span>

[!code-csharp[csRefOperators#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#19)]

<span data-ttu-id="79363-110">Nokta ad alanı veya arabirimi, örneğin, ait oldukları belirten adlarının tam adları oluşturmak için de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="79363-110">The dot is also used to form qualified names, which are names that specify the namespace or interface, for example, to which they belong.</span></span>

[!code-csharp[csRefOperators#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#20)]

<span data-ttu-id="79363-111">Using yönergesi bazı ad niteliği isteğe bağlı yapar:</span><span class="sxs-lookup"><span data-stu-id="79363-111">The using directive makes some name qualification optional:</span></span>

[!code-csharp[csRefOperators#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#21)]

<span data-ttu-id="79363-112">Ancak, bir tanımlayıcı belirsiz olduğunda nitelenmelidir:</span><span class="sxs-lookup"><span data-stu-id="79363-112">But when an identifier is ambiguous, it must be qualified:</span></span>

[!code-csharp[csRefOperators#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#22)]

## <a name="c-language-specification"></a><span data-ttu-id="79363-113">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="79363-113">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="79363-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="79363-114">See also</span></span>

- [<span data-ttu-id="79363-115">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="79363-115">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="79363-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="79363-116">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="79363-117">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="79363-117">C# Operators</span></span>](index.md)