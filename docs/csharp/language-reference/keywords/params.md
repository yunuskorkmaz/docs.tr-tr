---
title: parametre dizileri için params anahtar kelime - C# referans
ms.date: 07/20/2015
f1_keywords:
- params_CSharpKeyword
- params
helpviewer_keywords:
- parameters [C#], params
- params keyword [C#]
- parameter array
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
ms.openlocfilehash: 77d7fd19ff57f80f401191027e2fae95026e1966
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738838"
---
# <a name="params-c-reference"></a><span data-ttu-id="384c2-102">params (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="384c2-102">params (C# Reference)</span></span>

<span data-ttu-id="384c2-103">Anahtar kelimeyi `params` kullanarak, değişken sayıda bağımsız değişken alan bir [yöntem parametresi](method-parameters.md) belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="384c2-103">By using the `params` keyword, you can specify a [method parameter](method-parameters.md) that takes a variable number of arguments.</span></span> <span data-ttu-id="384c2-104">Parametre türü tek boyutlu bir dizi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="384c2-104">The parameter type must be a single-dimensional array.</span></span>

<span data-ttu-id="384c2-105">Yöntem bildirimindeki anahtar kelimeden `params` sonra ek parametreye `params` izin verilmez ve yöntem bildiriminde yalnızca bir anahtar kelimeye izin verilir.</span><span class="sxs-lookup"><span data-stu-id="384c2-105">No additional parameters are permitted after the `params` keyword in a method declaration, and only one `params` keyword is permitted in a method declaration.</span></span>

<span data-ttu-id="384c2-106">Bildirilen `params` parametre türü tek boyutlu bir dizi değilse, derleyici hatası [CS0225](../../misc/cs0225.md) oluşur.</span><span class="sxs-lookup"><span data-stu-id="384c2-106">If the declared type of the `params` parameter is not a single-dimensional array, compiler error [CS0225](../../misc/cs0225.md) occurs.</span></span>

<span data-ttu-id="384c2-107">Parametresi olan bir `params` yöntemi çağırdığınızda, şu yoldan geçebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="384c2-107">When you call a method with a `params` parameter, you can pass in:</span></span>

- <span data-ttu-id="384c2-108">Dizi öğelerinin türüne ait bağımsız değişkenlerin virgülle ayrılmış bir listesi.</span><span class="sxs-lookup"><span data-stu-id="384c2-108">A comma-separated list of arguments of the type of the array elements.</span></span>
- <span data-ttu-id="384c2-109">Belirtilen türdeki bağımsız değişkenler dizisi.</span><span class="sxs-lookup"><span data-stu-id="384c2-109">An array of arguments of the specified type.</span></span>
- <span data-ttu-id="384c2-110">Tartışma yok.</span><span class="sxs-lookup"><span data-stu-id="384c2-110">No arguments.</span></span> <span data-ttu-id="384c2-111">Bağımsız değişken göndermezseniz, `params` listenin uzunluğu sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="384c2-111">If you send no arguments, the length of the `params` list is zero.</span></span>

## <a name="example"></a><span data-ttu-id="384c2-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="384c2-112">Example</span></span>

<span data-ttu-id="384c2-113">Aşağıdaki örnek, bağımsız değişkenlerin bir `params` parametreye gönderilebildiği çeşitli yolları göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="384c2-113">The following example demonstrates various ways in which arguments can be sent to a `params` parameter.</span></span>

[!code-csharp[csrefKeywordsMethodParams#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsMethodParams/CS/csrefKeywordsMethodParams.cs#5)]

## <a name="c-language-specification"></a><span data-ttu-id="384c2-114">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="384c2-114">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="384c2-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="384c2-115">See also</span></span>

- [<span data-ttu-id="384c2-116">C# Referans</span><span class="sxs-lookup"><span data-stu-id="384c2-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="384c2-117">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="384c2-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="384c2-118">C# Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="384c2-118">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="384c2-119">Yöntem Parametreleri</span><span class="sxs-lookup"><span data-stu-id="384c2-119">Method Parameters</span></span>](method-parameters.md)
