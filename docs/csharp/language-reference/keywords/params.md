---
description: Parameter dizileri için params anahtar sözcüğü-C# başvurusu
title: Parameter dizileri için params anahtar sözcüğü-C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- params_CSharpKeyword
- params
helpviewer_keywords:
- parameters [C#], params
- params keyword [C#]
- parameter array
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
ms.openlocfilehash: a2726c725508cd297001aaabddeff414704d1115
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89134477"
---
# <a name="params-c-reference"></a><span data-ttu-id="69750-103">params (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="69750-103">params (C# Reference)</span></span>

<span data-ttu-id="69750-104">`params`Anahtar sözcüğünü kullanarak, değişken sayıda bağımsız değişken alan bir [yöntem parametresi](method-parameters.md) belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="69750-104">By using the `params` keyword, you can specify a [method parameter](method-parameters.md) that takes a variable number of arguments.</span></span> <span data-ttu-id="69750-105">Parametre türü tek boyutlu bir dizi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="69750-105">The parameter type must be a single-dimensional array.</span></span>

<span data-ttu-id="69750-106">`params`Yöntem bildiriminde anahtar kelimeden sonra ek parametrelere izin verilmez ve `params` bir yöntem bildiriminde yalnızca bir anahtar sözcüğe izin verilir.</span><span class="sxs-lookup"><span data-stu-id="69750-106">No additional parameters are permitted after the `params` keyword in a method declaration, and only one `params` keyword is permitted in a method declaration.</span></span>

<span data-ttu-id="69750-107">Parametrenin bildirildiği tür `params` tek boyutlu bir dizi değilse, derleyici hatası [CS0225](../../misc/cs0225.md) oluşur.</span><span class="sxs-lookup"><span data-stu-id="69750-107">If the declared type of the `params` parameter is not a single-dimensional array, compiler error [CS0225](../../misc/cs0225.md) occurs.</span></span>

<span data-ttu-id="69750-108">Bir parametre içeren bir yöntemi çağırdığınızda `params` , şu şekilde geçiş yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="69750-108">When you call a method with a `params` parameter, you can pass in:</span></span>

- <span data-ttu-id="69750-109">Dizi öğelerinin türünün bağımsız değişkenlerinin virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="69750-109">A comma-separated list of arguments of the type of the array elements.</span></span>
- <span data-ttu-id="69750-110">Belirtilen türde bir bağımsız değişken dizisi.</span><span class="sxs-lookup"><span data-stu-id="69750-110">An array of arguments of the specified type.</span></span>
- <span data-ttu-id="69750-111">Bağımsız değişken yok.</span><span class="sxs-lookup"><span data-stu-id="69750-111">No arguments.</span></span> <span data-ttu-id="69750-112">Bağımsız değişken gönderirseniz, `params` listenin uzunluğu sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="69750-112">If you send no arguments, the length of the `params` list is zero.</span></span>

## <a name="example"></a><span data-ttu-id="69750-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="69750-113">Example</span></span>

<span data-ttu-id="69750-114">Aşağıdaki örnekte, bağımsız değişkenlerin bir parametreye gönderilebileceği çeşitli yollar gösterilmektedir `params` .</span><span class="sxs-lookup"><span data-stu-id="69750-114">The following example demonstrates various ways in which arguments can be sent to a `params` parameter.</span></span>

[!code-csharp[csrefKeywordsMethodParams#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsMethodParams/CS/csrefKeywordsMethodParams.cs#5)]

## <a name="c-language-specification"></a><span data-ttu-id="69750-115">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="69750-115">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="69750-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="69750-116">See also</span></span>

- [<span data-ttu-id="69750-117">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="69750-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="69750-118">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="69750-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="69750-119">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="69750-119">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="69750-120">Yöntem Parametreleri</span><span class="sxs-lookup"><span data-stu-id="69750-120">Method Parameters</span></span>](method-parameters.md)
