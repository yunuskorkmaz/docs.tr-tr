---
title: "Yöntem Parametreleri (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- methods [C#], parameters
- method parameters [C#]
- parameters [C#]
ms.assetid: 680e39ff-775b-48b0-9f47-4186a5bfc4a1
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b20d2d233350cfb9de55cbd07e722082ec311597
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2018
---
# <a name="method-parameters-c-reference"></a><span data-ttu-id="5104e-102">Yöntem Parametreleri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="5104e-102">Method Parameters (C# Reference)</span></span>

<span data-ttu-id="5104e-103">Bildirilen parametreler bir yöntem için [içinde](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md) veya [çıkışı](../../../csharp/language-reference/keywords/out-parameter-modifier.md), çağrılan yönteme değeriyle geçirilir.</span><span class="sxs-lookup"><span data-stu-id="5104e-103">Parameters declared for a method without [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md), are passed to the called method by value.</span></span> <span data-ttu-id="5104e-104">Bu değer yönteminde değiştirilebilir, ancak denetim arama yordamın geçtiğinde değişen değeri korunmaz.</span><span class="sxs-lookup"><span data-stu-id="5104e-104">That value can be changed in the method, but the changed value will not be retained when control passes back to the calling procedure.</span></span> <span data-ttu-id="5104e-105">Bir yöntemin parametre anahtar sözcüğünü kullanarak, bu davranışı değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5104e-105">By using a method parameter keyword, you can change this behavior.</span></span>  
  
 <span data-ttu-id="5104e-106">Bu bölüm, yöntem parametreleri bildirirken kullanabileceğiniz anahtar sözcükleri açıklar:</span><span class="sxs-lookup"><span data-stu-id="5104e-106">This section describes the keywords you can use when declaring method parameters:</span></span>  
  
-   [<span data-ttu-id="5104e-107">params</span><span class="sxs-lookup"><span data-stu-id="5104e-107">params</span></span>](../../../csharp/language-reference/keywords/params.md)  
  
-   [<span data-ttu-id="5104e-108">in</span><span class="sxs-lookup"><span data-stu-id="5104e-108">in</span></span>](../../../csharp/language-reference/keywords/in-parameter-modifier.md)  
  
-   [<span data-ttu-id="5104e-109">ref</span><span class="sxs-lookup"><span data-stu-id="5104e-109">ref</span></span>](../../../csharp/language-reference/keywords/ref.md)  
  
-   [<span data-ttu-id="5104e-110">out</span><span class="sxs-lookup"><span data-stu-id="5104e-110">out</span></span>](../../../csharp/language-reference/keywords/out-parameter-modifier.md)  
  
## <a name="see-also"></a><span data-ttu-id="5104e-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5104e-111">See Also</span></span>  
 [<span data-ttu-id="5104e-112">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="5104e-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="5104e-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="5104e-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="5104e-114">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="5104e-114">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
