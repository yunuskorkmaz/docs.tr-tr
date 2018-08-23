---
title: params (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- params_CSharpKeyword
- params
helpviewer_keywords:
- parameters [C#], params
- params keyword [C#]
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
ms.openlocfilehash: 692c2f61ae99f1c1c8e04a5a1bcad08814d286fe
ms.sourcegitcommit: a1e35d4e94edab384a63406c0a5438306873031b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2018
ms.locfileid: "42753960"
---
# <a name="params-c-reference"></a><span data-ttu-id="380d3-102">params (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="380d3-102">params (C# Reference)</span></span>
<span data-ttu-id="380d3-103">Kullanarak `params` belirtebileceğiniz anahtar sözcüğü, bir [yöntem parametresi](../../../csharp/language-reference/keywords/method-parameters.md) , değişken sayıda bağımsız değişken alır.</span><span class="sxs-lookup"><span data-stu-id="380d3-103">By using the `params` keyword, you can specify a [method parameter](../../../csharp/language-reference/keywords/method-parameters.md) that takes a variable number of arguments.</span></span>  
  
 <span data-ttu-id="380d3-104">Parametre bildiriminde belirtilen türde bağımsız değişkenleri dizisini belirtilen türdeki bağımsız değişkenlerin virgülle ayrılmış bir liste gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="380d3-104">You can send a comma-separated list of arguments of the type specified in the parameter declaration or an array of arguments of the specified type.</span></span> <span data-ttu-id="380d3-105">Ayrıca, herhangi bir bağımsız değişken gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="380d3-105">You also can send no arguments.</span></span> <span data-ttu-id="380d3-106">Hiçbir bağımsız değişken uzunluğu gönderirseniz `params` sıfır listesidir.</span><span class="sxs-lookup"><span data-stu-id="380d3-106">If you send no arguments, the length of the `params` list is zero.</span></span>  
  
 <span data-ttu-id="380d3-107">Ek parametre sonra izin verilen `params` anahtar sözcüğü bir yöntem bildiriminde ve tek `params` anahtar sözcüğü bir metodun bildiriminde izin verilir.</span><span class="sxs-lookup"><span data-stu-id="380d3-107">No additional parameters are permitted after the `params` keyword in a method declaration, and only one `params` keyword is permitted in a method declaration.</span></span>  
 
 <span data-ttu-id="380d3-108">Bildirilen türü `params` parametresi, aşağıdaki örnekte gösterildiği gibi bir tek boyutlu bir dizi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="380d3-108">The declared type of the `params` parameter must be a single-dimensional array, as the following example shows.</span></span> <span data-ttu-id="380d3-109">Aksi halde bir derleyici hatası [CS0225](../../../csharp/misc/cs0225.md) gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="380d3-109">Otherwise, a compiler error [CS0225](../../../csharp/misc/cs0225.md) occurs.</span></span>
  
## <a name="example"></a><span data-ttu-id="380d3-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="380d3-110">Example</span></span>  
 <span data-ttu-id="380d3-111">Aşağıdaki örnek, bağımsız değişkenleri göndermenin çeşitli yollarını gösterir bir `params` parametresi.</span><span class="sxs-lookup"><span data-stu-id="380d3-111">The following example demonstrates various ways in which arguments can be sent to a `params` parameter.</span></span>  
  
 [!code-csharp[csrefKeywordsMethodParams#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/params_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="380d3-112">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="380d3-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="380d3-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="380d3-113">See Also</span></span>  
 [<span data-ttu-id="380d3-114">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="380d3-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="380d3-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="380d3-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="380d3-116">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="380d3-116">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="380d3-117">Yöntem Parametreleri</span><span class="sxs-lookup"><span data-stu-id="380d3-117">Method Parameters</span></span>](../../../csharp/language-reference/keywords/method-parameters.md)
