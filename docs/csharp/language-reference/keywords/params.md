---
title: params anahtar sözcüğü C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- params_CSharpKeyword
- params
helpviewer_keywords:
- parameters [C#], params
- params keyword [C#]
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
ms.openlocfilehash: 90d224080f607cbac96514aaf5ac6d67affef9e0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713241"
---
# <a name="params-c-reference"></a><span data-ttu-id="a708c-102">params (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="a708c-102">params (C# Reference)</span></span>

<span data-ttu-id="a708c-103">`params` anahtar sözcüğünü kullanarak, değişken sayıda bağımsız değişken alan bir [yöntem parametresi](method-parameters.md) belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a708c-103">By using the `params` keyword, you can specify a [method parameter](method-parameters.md) that takes a variable number of arguments.</span></span>

<span data-ttu-id="a708c-104">Parametre bildiriminde belirtilen türde bağımsız değişkenlerin virgülle ayrılmış bir listesini veya belirtilen türdeki bağımsız değişkenlerin dizisini gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a708c-104">You can send a comma-separated list of arguments of the type specified in the parameter declaration or an array of arguments of the specified type.</span></span> <span data-ttu-id="a708c-105">Bağımsız değişken de gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a708c-105">You also can send no arguments.</span></span> <span data-ttu-id="a708c-106">Bağımsız değişken gönderirseniz `params` listesinin uzunluğu sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="a708c-106">If you send no arguments, the length of the `params` list is zero.</span></span>

<span data-ttu-id="a708c-107">Yöntem bildiriminde `params` anahtar sözcüğünden sonra ek parametre yapılmasına izin verilmez ve yöntem bildiriminde yalnızca bir `params` anahtar sözcüğüne izin verilir.</span><span class="sxs-lookup"><span data-stu-id="a708c-107">No additional parameters are permitted after the `params` keyword in a method declaration, and only one `params` keyword is permitted in a method declaration.</span></span>

<span data-ttu-id="a708c-108">`params` parametresinin belirtilen türü, aşağıdaki örnekte gösterildiği gibi tek boyutlu bir dizi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a708c-108">The declared type of the `params` parameter must be a single-dimensional array, as the following example shows.</span></span> <span data-ttu-id="a708c-109">Aksi takdirde, bir derleyici hatası [CS0225](../../misc/cs0225.md) oluşur.</span><span class="sxs-lookup"><span data-stu-id="a708c-109">Otherwise, a compiler error [CS0225](../../misc/cs0225.md) occurs.</span></span>

## <a name="example"></a><span data-ttu-id="a708c-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="a708c-110">Example</span></span>

<span data-ttu-id="a708c-111">Aşağıdaki örnekte, bağımsız değişkenlerin `params` parametreye gönderilebileceği çeşitli yollar gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a708c-111">The following example demonstrates various ways in which arguments can be sent to a `params` parameter.</span></span>

[!code-csharp[csrefKeywordsMethodParams#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsMethodParams/CS/csrefKeywordsMethodParams.cs#5)] 

## <a name="c-language-specification"></a><span data-ttu-id="a708c-112">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="a708c-112">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="a708c-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a708c-113">See also</span></span>

- [<span data-ttu-id="a708c-114">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="a708c-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="a708c-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a708c-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="a708c-116">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="a708c-116">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="a708c-117">Yöntem Parametreleri</span><span class="sxs-lookup"><span data-stu-id="a708c-117">Method Parameters</span></span>](method-parameters.md)
