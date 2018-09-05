---
title: Yöntem Parametreleri (C# Başvurusu)
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#], parameters
- method parameters [C#]
- parameters [C#]
ms.assetid: 680e39ff-775b-48b0-9f47-4186a5bfc4a1
ms.openlocfilehash: 446a5239fa1de8559dea50f7e8b8869aed0297c5
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43512791"
---
# <a name="method-parameters-c-reference"></a><span data-ttu-id="28d70-102">Yöntem Parametreleri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="28d70-102">Method Parameters (C# Reference)</span></span>

<span data-ttu-id="28d70-103">Olarak bildirilen parametreleri olmayan bir yöntem için [içinde](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md) veya [kullanıma](../../../csharp/language-reference/keywords/out-parameter-modifier.md), çağrılan yöntem için değere göre geçirilir.</span><span class="sxs-lookup"><span data-stu-id="28d70-103">Parameters declared for a method without [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md), are passed to the called method by value.</span></span> <span data-ttu-id="28d70-104">Bu değer yönteminde değiştirilebilir, ancak çağıran yordama denetimi başarılı olduğunda değişen değeri korunmaz.</span><span class="sxs-lookup"><span data-stu-id="28d70-104">That value can be changed in the method, but the changed value will not be retained when control passes back to the calling procedure.</span></span> <span data-ttu-id="28d70-105">Bir yöntem parametresi anahtar sözcüğü kullanarak bu davranışı değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="28d70-105">By using a method parameter keyword, you can change this behavior.</span></span>  
  
 <span data-ttu-id="28d70-106">Yöntem parametreleri bildirirken kullanabilirsiniz anahtar sözcükleri Bu bölümde açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="28d70-106">This section describes the keywords you can use when declaring method parameters:</span></span>  
  
-   <span data-ttu-id="28d70-107">[params](../../../csharp/language-reference/keywords/params.md) Bu parametre, değişken sayıda bağımsız değişken alabilir belirtir.</span><span class="sxs-lookup"><span data-stu-id="28d70-107">[params](../../../csharp/language-reference/keywords/params.md) specifies that this parameter may take a variable number of arguments.</span></span>
  
-   <span data-ttu-id="28d70-108">[içinde](../../../csharp/language-reference/keywords/in-parameter-modifier.md) Bu parametre başvurusu tarafından geçirilir ancak tarafından çağrılan yöntem salt okunur belirtir.</span><span class="sxs-lookup"><span data-stu-id="28d70-108">[in](../../../csharp/language-reference/keywords/in-parameter-modifier.md) specifies that this parameter is passed by reference but is only read by the called method.</span></span>
  
-   <span data-ttu-id="28d70-109">[Ref](../../../csharp/language-reference/keywords/ref.md) Bu parametre başvuruyla geçirildi ve okuma veya olabilir çağrılan yöntem tarafından yazılmış, belirtir.</span><span class="sxs-lookup"><span data-stu-id="28d70-109">[ref](../../../csharp/language-reference/keywords/ref.md) specifies that this parameter is passed by reference and may be read or written by the called method.</span></span>
  
-   <span data-ttu-id="28d70-110">[Çıkış](../../../csharp/language-reference/keywords/out-parameter-modifier.md) Bu parametre, başvuruyla geçirildi ve çağrılan yöntem tarafından yazılan belirtir.</span><span class="sxs-lookup"><span data-stu-id="28d70-110">[out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) specifies that this parameter is passed by reference and is written by the called method.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="28d70-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="28d70-111">See Also</span></span>

- [<span data-ttu-id="28d70-112">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="28d70-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="28d70-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="28d70-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="28d70-114">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="28d70-114">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
