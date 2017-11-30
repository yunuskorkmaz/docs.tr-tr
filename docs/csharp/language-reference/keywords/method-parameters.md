---
title: "Yöntem Parametreleri (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- methods [C#], parameters
- method parameters [C#]
- parameters [C#]
ms.assetid: 680e39ff-775b-48b0-9f47-4186a5bfc4a1
caps.latest.revision: "8"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 924e261cc876d2428e28ed0f490beb46b95f96e6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="method-parameters-c-reference"></a><span data-ttu-id="0da90-102">Yöntem Parametreleri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="0da90-102">Method Parameters (C# Reference)</span></span>
<span data-ttu-id="0da90-103">Bir parametre bir yöntem için bildirilirse [ref](../../../csharp/language-reference/keywords/ref.md) veya [çıkışı](../../../csharp/language-reference/keywords/out.md), parametresi, kendisiyle ilişkili bir değere sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="0da90-103">If a parameter is declared for a method without [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out.md), the parameter can have a value associated with it.</span></span> <span data-ttu-id="0da90-104">Bu değer yönteminde değiştirilebilir, ancak denetim arama yordamın geçtiğinde değişen değeri korunmaz.</span><span class="sxs-lookup"><span data-stu-id="0da90-104">That value can be changed in the method, but the changed value will not be retained when control passes back to the calling procedure.</span></span> <span data-ttu-id="0da90-105">Bir yöntemin parametre anahtar sözcüğünü kullanarak, bu davranışı değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0da90-105">By using a method parameter keyword, you can change this behavior.</span></span>  
  
 <span data-ttu-id="0da90-106">Bu bölüm, yöntem parametreleri bildirirken kullanabileceğiniz anahtar sözcükleri açıklar:</span><span class="sxs-lookup"><span data-stu-id="0da90-106">This section describes the keywords you can use when declaring method parameters:</span></span>  
  
-   [<span data-ttu-id="0da90-107">parametreleri</span><span class="sxs-lookup"><span data-stu-id="0da90-107">params</span></span>](../../../csharp/language-reference/keywords/params.md)  
  
-   [<span data-ttu-id="0da90-108">Ref</span><span class="sxs-lookup"><span data-stu-id="0da90-108">ref</span></span>](../../../csharp/language-reference/keywords/ref.md)  
  
-   [<span data-ttu-id="0da90-109">çıkışı</span><span class="sxs-lookup"><span data-stu-id="0da90-109">out</span></span>](../../../csharp/language-reference/keywords/out.md)  
  
## <a name="see-also"></a><span data-ttu-id="0da90-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0da90-110">See Also</span></span>  
 [<span data-ttu-id="0da90-111">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="0da90-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="0da90-112">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0da90-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="0da90-113">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="0da90-113">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
