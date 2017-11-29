---
title: "params (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- params_CSharpKeyword
- params
helpviewer_keywords:
- parameters [C#], params
- params keyword [C#]
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
caps.latest.revision: "24"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e66cfc8e7b131a4443ee227df5e39c7e3b775324
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="params-c-reference"></a><span data-ttu-id="6dca0-102">params (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="6dca0-102">params (C# Reference)</span></span>
<span data-ttu-id="6dca0-103">Kullanarak `params` anahtar sözcüğü, belirtebilirsiniz bir [yöntem parametresi](../../../csharp/language-reference/keywords/method-parameters.md) değişken sayıda bağımsız değişken alan.</span><span class="sxs-lookup"><span data-stu-id="6dca0-103">By using the `params` keyword, you can specify a [method parameter](../../../csharp/language-reference/keywords/method-parameters.md) that takes a variable number of arguments.</span></span>  
  
 <span data-ttu-id="6dca0-104">Bağımsız değişkenler belirtilen türde bir dizi parametre bildiriminde belirtilen tür bağımsız değişkenleri virgülle ayrılmış bir liste gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6dca0-104">You can send a comma-separated list of arguments of the type specified in the parameter declaration or an array of arguments of the specified type.</span></span> <span data-ttu-id="6dca0-105">Bağımsız değişkenler de gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6dca0-105">You also can send no arguments.</span></span> <span data-ttu-id="6dca0-106">Bağımsız değişkenler, uzunluğu gönderirseniz `params` sıfır listesidir.</span><span class="sxs-lookup"><span data-stu-id="6dca0-106">If you send no arguments, the length of the `params` list is zero.</span></span>  
  
 <span data-ttu-id="6dca0-107">Ek parametre sonra izin verilen `params` bir yöntem bildirimi ve tek bir anahtar sözcük `params` anahtar sözcüğü bir yöntem bildiriminde izin verilir.</span><span class="sxs-lookup"><span data-stu-id="6dca0-107">No additional parameters are permitted after the `params` keyword in a method declaration, and only one `params` keyword is permitted in a method declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6dca0-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="6dca0-108">Example</span></span>  
 <span data-ttu-id="6dca0-109">Aşağıdaki örnek, bağımsız değişkenler gönderilebilir için çeşitli yollar gösterir bir `params` parametresi.</span><span class="sxs-lookup"><span data-stu-id="6dca0-109">The following example demonstrates various ways in which arguments can be sent to a `params` parameter.</span></span>  
  
 [!code-csharp[csrefKeywordsMethodParams#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/params_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="6dca0-110">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="6dca0-110">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6dca0-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6dca0-111">See Also</span></span>  
 [<span data-ttu-id="6dca0-112">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="6dca0-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="6dca0-113">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="6dca0-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="6dca0-114">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="6dca0-114">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="6dca0-115">Yöntem parametreleri</span><span class="sxs-lookup"><span data-stu-id="6dca0-115">Method Parameters</span></span>](../../../csharp/language-reference/keywords/method-parameters.md)
