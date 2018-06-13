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
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33265476"
---
# <a name="params-c-reference"></a><span data-ttu-id="2ff1f-102">params (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="2ff1f-102">params (C# Reference)</span></span>
<span data-ttu-id="2ff1f-103">Kullanarak `params` anahtar sözcüğü, belirtebilirsiniz bir [yöntem parametresi](../../../csharp/language-reference/keywords/method-parameters.md) değişken sayıda bağımsız değişken alan.</span><span class="sxs-lookup"><span data-stu-id="2ff1f-103">By using the `params` keyword, you can specify a [method parameter](../../../csharp/language-reference/keywords/method-parameters.md) that takes a variable number of arguments.</span></span>  
  
 <span data-ttu-id="2ff1f-104">Bağımsız değişkenler belirtilen türde bir dizi parametre bildiriminde belirtilen tür bağımsız değişkenleri virgülle ayrılmış bir liste gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2ff1f-104">You can send a comma-separated list of arguments of the type specified in the parameter declaration or an array of arguments of the specified type.</span></span> <span data-ttu-id="2ff1f-105">Bağımsız değişkenler de gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2ff1f-105">You also can send no arguments.</span></span> <span data-ttu-id="2ff1f-106">Bağımsız değişkenler, uzunluğu gönderirseniz `params` sıfır listesidir.</span><span class="sxs-lookup"><span data-stu-id="2ff1f-106">If you send no arguments, the length of the `params` list is zero.</span></span>  
  
 <span data-ttu-id="2ff1f-107">Ek parametre sonra izin verilen `params` bir yöntem bildirimi ve tek bir anahtar sözcük `params` anahtar sözcüğü bir yöntem bildiriminde izin verilir.</span><span class="sxs-lookup"><span data-stu-id="2ff1f-107">No additional parameters are permitted after the `params` keyword in a method declaration, and only one `params` keyword is permitted in a method declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ff1f-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="2ff1f-108">Example</span></span>  
 <span data-ttu-id="2ff1f-109">Aşağıdaki örnek, bağımsız değişkenler gönderilebilir için çeşitli yollar gösterir bir `params` parametresi.</span><span class="sxs-lookup"><span data-stu-id="2ff1f-109">The following example demonstrates various ways in which arguments can be sent to a `params` parameter.</span></span>  
  
 [!code-csharp[csrefKeywordsMethodParams#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/params_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="2ff1f-110">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="2ff1f-110">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2ff1f-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2ff1f-111">See Also</span></span>  
 [<span data-ttu-id="2ff1f-112">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="2ff1f-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="2ff1f-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="2ff1f-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="2ff1f-114">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="2ff1f-114">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="2ff1f-115">Yöntem Parametreleri</span><span class="sxs-lookup"><span data-stu-id="2ff1f-115">Method Parameters</span></span>](../../../csharp/language-reference/keywords/method-parameters.md)
