---
title: params anahtar kelime - C# Referans
ms.date: 07/20/2015
f1_keywords:
- params_CSharpKeyword
- params
helpviewer_keywords:
- parameters [C#], params
- params keyword [C#]
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
ms.openlocfilehash: f462ccc2421fef3ea111d263ec035a701cf04775
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173555"
---
# <a name="params-c-reference"></a><span data-ttu-id="951bb-102">params (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="951bb-102">params (C# Reference)</span></span>

<span data-ttu-id="951bb-103">Anahtar kelimeyi `params` kullanarak, değişken sayıda bağımsız değişken alan bir [yöntem parametresi](method-parameters.md) belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="951bb-103">By using the `params` keyword, you can specify a [method parameter](method-parameters.md) that takes a variable number of arguments.</span></span>

<span data-ttu-id="951bb-104">Parametre bildiriminde belirtilen türdeki bağımsız değişkenlerin veya belirtilen türdeki bağımsız değişkenlerin bir dizi virgülle ayrılmış bir listesini gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="951bb-104">You can send a comma-separated list of arguments of the type specified in the parameter declaration or an array of arguments of the specified type.</span></span> <span data-ttu-id="951bb-105">Ayrıca hiçbir bağımsız değişken gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="951bb-105">You also can send no arguments.</span></span> <span data-ttu-id="951bb-106">Bağımsız değişken göndermezseniz, `params` listenin uzunluğu sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="951bb-106">If you send no arguments, the length of the `params` list is zero.</span></span>

<span data-ttu-id="951bb-107">Yöntem bildirimindeki anahtar kelimeden `params` sonra ek parametreye `params` izin verilmez ve yöntem bildiriminde yalnızca bir anahtar kelimeye izin verilir.</span><span class="sxs-lookup"><span data-stu-id="951bb-107">No additional parameters are permitted after the `params` keyword in a method declaration, and only one `params` keyword is permitted in a method declaration.</span></span>

<span data-ttu-id="951bb-108">Aşağıdaki örnekte `params` görüldüğü gibi, parametrenin bildirilen türü tek boyutlu bir dizi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="951bb-108">The declared type of the `params` parameter must be a single-dimensional array, as the following example shows.</span></span> <span data-ttu-id="951bb-109">Aksi takdirde, bir derleyici hatası [CS0225](../../misc/cs0225.md) oluşur.</span><span class="sxs-lookup"><span data-stu-id="951bb-109">Otherwise, a compiler error [CS0225](../../misc/cs0225.md) occurs.</span></span>

## <a name="example"></a><span data-ttu-id="951bb-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="951bb-110">Example</span></span>

<span data-ttu-id="951bb-111">Aşağıdaki örnek, bağımsız değişkenlerin bir `params` parametreye gönderilebildiği çeşitli yolları göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="951bb-111">The following example demonstrates various ways in which arguments can be sent to a `params` parameter.</span></span>

[!code-csharp[csrefKeywordsMethodParams#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsMethodParams/CS/csrefKeywordsMethodParams.cs#5)]

## <a name="c-language-specification"></a><span data-ttu-id="951bb-112">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="951bb-112">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="951bb-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="951bb-113">See also</span></span>

- [<span data-ttu-id="951bb-114">C# Referans</span><span class="sxs-lookup"><span data-stu-id="951bb-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="951bb-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="951bb-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="951bb-116">C# Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="951bb-116">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="951bb-117">Yöntem Parametreleri</span><span class="sxs-lookup"><span data-stu-id="951bb-117">Method Parameters</span></span>](method-parameters.md)
