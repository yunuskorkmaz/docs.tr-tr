---
title: Yöntem Parametreleri (C# Başvurusu)
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#], parameters
- method parameters [C#]
- parameters [C#]
ms.assetid: 680e39ff-775b-48b0-9f47-4186a5bfc4a1
ms.openlocfilehash: 8a8d300661eec42030900dd9ee85a17e66aa0922
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33269352"
---
# <a name="method-parameters-c-reference"></a><span data-ttu-id="6c70b-102">Yöntem Parametreleri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="6c70b-102">Method Parameters (C# Reference)</span></span>

<span data-ttu-id="6c70b-103">Bildirilen parametreler bir yöntem için [içinde](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md) veya [çıkışı](../../../csharp/language-reference/keywords/out-parameter-modifier.md), çağrılan yönteme değeriyle geçirilir.</span><span class="sxs-lookup"><span data-stu-id="6c70b-103">Parameters declared for a method without [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md), are passed to the called method by value.</span></span> <span data-ttu-id="6c70b-104">Bu değer yönteminde değiştirilebilir, ancak denetim arama yordamın geçtiğinde değişen değeri korunmaz.</span><span class="sxs-lookup"><span data-stu-id="6c70b-104">That value can be changed in the method, but the changed value will not be retained when control passes back to the calling procedure.</span></span> <span data-ttu-id="6c70b-105">Bir yöntemin parametre anahtar sözcüğünü kullanarak, bu davranışı değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6c70b-105">By using a method parameter keyword, you can change this behavior.</span></span>  
  
 <span data-ttu-id="6c70b-106">Bu bölüm, yöntem parametreleri bildirirken kullanabileceğiniz anahtar sözcükleri açıklar:</span><span class="sxs-lookup"><span data-stu-id="6c70b-106">This section describes the keywords you can use when declaring method parameters:</span></span>  
  
-   <span data-ttu-id="6c70b-107">[params](../../../csharp/language-reference/keywords/params.md) Bu parametre değişken sayıda bağımsız değişken alabileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6c70b-107">[params](../../../csharp/language-reference/keywords/params.md) specifies that this parameter may take a variable number of arguments.</span></span>
  
-   <span data-ttu-id="6c70b-108">[içinde](../../../csharp/language-reference/keywords/in-parameter-modifier.md) Bu parametre başvuruyla geçirildi ancak çağrılan yöntemi tarafından salt okunur belirtir.</span><span class="sxs-lookup"><span data-stu-id="6c70b-108">[in](../../../csharp/language-reference/keywords/in-parameter-modifier.md) specifies that this parameter is passed by reference but is only read by the called method.</span></span>
  
-   <span data-ttu-id="6c70b-109">[Ref](../../../csharp/language-reference/keywords/ref.md) Bu parametre başvuruya göre geçirilir ve okumak veya çağrılan yöntemi tarafından yazılmış belirtir.</span><span class="sxs-lookup"><span data-stu-id="6c70b-109">[ref](../../../csharp/language-reference/keywords/ref.md) specifies that this parameter is passed by reference and may be read or written by the called method.</span></span>
  
-   <span data-ttu-id="6c70b-110">[out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) Bu parametre başvuruya göre geçirilir ve çağrılan yöntemi tarafından yazılmış belirtir.</span><span class="sxs-lookup"><span data-stu-id="6c70b-110">[out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) specifies that this parameter is passed by reference and is written by the called method.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="6c70b-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6c70b-111">See Also</span></span>  
 [<span data-ttu-id="6c70b-112">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="6c70b-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="6c70b-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="6c70b-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="6c70b-114">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="6c70b-114">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
