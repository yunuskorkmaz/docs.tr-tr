---
title: params anahtar sözcüğü (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- params_CSharpKeyword
- params
helpviewer_keywords:
- parameters [C#], params
- params keyword [C#]
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
ms.openlocfilehash: 089e31f3aad12c2303619e2a1998d0d6a5a0ad86
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44175471"
---
# <a name="params-c-reference"></a><span data-ttu-id="9f986-102">params (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="9f986-102">params (C# Reference)</span></span>

<span data-ttu-id="9f986-103">Kullanarak `params` belirtebileceğiniz anahtar sözcüğü, bir [yöntem parametresi](method-parameters.md) , değişken sayıda bağımsız değişken alır.</span><span class="sxs-lookup"><span data-stu-id="9f986-103">By using the `params` keyword, you can specify a [method parameter](method-parameters.md) that takes a variable number of arguments.</span></span>

<span data-ttu-id="9f986-104">Parametre bildiriminde belirtilen türde bağımsız değişkenleri dizisini belirtilen türdeki bağımsız değişkenlerin virgülle ayrılmış bir liste gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9f986-104">You can send a comma-separated list of arguments of the type specified in the parameter declaration or an array of arguments of the specified type.</span></span> <span data-ttu-id="9f986-105">Ayrıca, herhangi bir bağımsız değişken gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9f986-105">You also can send no arguments.</span></span> <span data-ttu-id="9f986-106">Hiçbir bağımsız değişken uzunluğu gönderirseniz `params` sıfır listesidir.</span><span class="sxs-lookup"><span data-stu-id="9f986-106">If you send no arguments, the length of the `params` list is zero.</span></span>

<span data-ttu-id="9f986-107">Ek parametre sonra izin verilen `params` anahtar sözcüğü bir yöntem bildiriminde ve tek `params` anahtar sözcüğü bir metodun bildiriminde izin verilir.</span><span class="sxs-lookup"><span data-stu-id="9f986-107">No additional parameters are permitted after the `params` keyword in a method declaration, and only one `params` keyword is permitted in a method declaration.</span></span>

<span data-ttu-id="9f986-108">Bildirilen türü `params` parametresi, aşağıdaki örnekte gösterildiği gibi bir tek boyutlu bir dizi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9f986-108">The declared type of the `params` parameter must be a single-dimensional array, as the following example shows.</span></span> <span data-ttu-id="9f986-109">Aksi halde bir derleyici hatası [CS0225](../../misc/cs0225.md) gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="9f986-109">Otherwise, a compiler error [CS0225](../../misc/cs0225.md) occurs.</span></span>

## <a name="example"></a><span data-ttu-id="9f986-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="9f986-110">Example</span></span>

<span data-ttu-id="9f986-111">Aşağıdaki örnek, bağımsız değişkenleri göndermenin çeşitli yollarını gösterir bir `params` parametresi.</span><span class="sxs-lookup"><span data-stu-id="9f986-111">The following example demonstrates various ways in which arguments can be sent to a `params` parameter.</span></span>

[!code-csharp[csrefKeywordsMethodParams#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsMethodParams/CS/csrefKeywordsMethodParams.cs#5)] 

## <a name="c-language-specification"></a><span data-ttu-id="9f986-112">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="9f986-112">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="9f986-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9f986-113">See also</span></span>

- [<span data-ttu-id="9f986-114">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="9f986-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="9f986-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="9f986-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="9f986-116">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="9f986-116">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="9f986-117">Yöntem Parametreleri</span><span class="sxs-lookup"><span data-stu-id="9f986-117">Method Parameters</span></span>](method-parameters.md)