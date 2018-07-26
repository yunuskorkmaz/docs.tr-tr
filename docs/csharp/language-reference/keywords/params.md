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
ms.openlocfilehash: d7e0094d0f60aa201ae7229983f3e4b9764d2cbc
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37960201"
---
# <a name="params-c-reference"></a><span data-ttu-id="92fda-102">params (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="92fda-102">params (C# Reference)</span></span>
<span data-ttu-id="92fda-103">Kullanarak `params` belirtebileceğiniz anahtar sözcüğü, bir [yöntem parametresi](../../../csharp/language-reference/keywords/method-parameters.md) , değişken sayıda bağımsız değişken alır.</span><span class="sxs-lookup"><span data-stu-id="92fda-103">By using the `params` keyword, you can specify a [method parameter](../../../csharp/language-reference/keywords/method-parameters.md) that takes a variable number of arguments.</span></span>  
  
 <span data-ttu-id="92fda-104">Parametre bildiriminde belirtilen türde bağımsız değişkenleri dizisini belirtilen türdeki bağımsız değişkenlerin virgülle ayrılmış bir liste gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="92fda-104">You can send a comma-separated list of arguments of the type specified in the parameter declaration or an array of arguments of the specified type.</span></span> <span data-ttu-id="92fda-105">Ayrıca, herhangi bir bağımsız değişken gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="92fda-105">You also can send no arguments.</span></span> <span data-ttu-id="92fda-106">Hiçbir bağımsız değişken uzunluğu gönderirseniz `params` sıfır listesidir.</span><span class="sxs-lookup"><span data-stu-id="92fda-106">If you send no arguments, the length of the `params` list is zero.</span></span>  
  
 <span data-ttu-id="92fda-107">Ek parametre sonra izin verilen `params` anahtar sözcüğü bir yöntem bildiriminde ve tek `params` anahtar sözcüğü bir metodun bildiriminde izin verilir.</span><span class="sxs-lookup"><span data-stu-id="92fda-107">No additional parameters are permitted after the `params` keyword in a method declaration, and only one `params` keyword is permitted in a method declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="92fda-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="92fda-108">Example</span></span>  
 <span data-ttu-id="92fda-109">Aşağıdaki örnek, bağımsız değişkenleri göndermenin çeşitli yollarını gösterir bir `params` parametresi.</span><span class="sxs-lookup"><span data-stu-id="92fda-109">The following example demonstrates various ways in which arguments can be sent to a `params` parameter.</span></span>  
  
 [!code-csharp[csrefKeywordsMethodParams#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/params_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="92fda-110">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="92fda-110">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="92fda-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="92fda-111">See Also</span></span>  
 [<span data-ttu-id="92fda-112">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="92fda-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="92fda-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="92fda-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="92fda-114">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="92fda-114">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="92fda-115">Yöntem Parametreleri</span><span class="sxs-lookup"><span data-stu-id="92fda-115">Method Parameters</span></span>](../../../csharp/language-reference/keywords/method-parameters.md)
