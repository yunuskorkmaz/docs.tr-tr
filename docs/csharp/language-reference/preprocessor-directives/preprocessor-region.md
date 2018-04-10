---
title: '#Bölge (C# Başvurusu)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#region'
helpviewer_keywords:
- '#region directive [C#]'
ms.assetid: 672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4
caps.latest.revision: 12
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: cce4a8ac79c4687280e28618d8863d16cd193a3b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="region-c-reference"></a><span data-ttu-id="3192a-102">#region (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="3192a-102">#region (C# Reference)</span></span>
<span data-ttu-id="3192a-103">`#region`Genişlet veya daralt kullanırken kod bloğu belirtmenizi sağlar [anahat oluşturma](/visualstudio/ide/outlining) özelliği Visual Studio Kod Düzenleyicisi'nin.</span><span class="sxs-lookup"><span data-stu-id="3192a-103">`#region` lets you specify a block of code that you can expand or collapse when using the [outlining](/visualstudio/ide/outlining) feature of the Visual Studio Code Editor.</span></span> <span data-ttu-id="3192a-104">Uzun kod dosyalarında daraltın veya üzerinde çalışmakta olduğunuz dosya bölümüne odaklanabiliriz bir veya daha fazla bölge gizlemek uygundur.</span><span class="sxs-lookup"><span data-stu-id="3192a-104">In longer code files, it is convenient to be able to collapse or hide one or more regions so that you can focus on the part of the file that you are currently working on.</span></span> <span data-ttu-id="3192a-105">Aşağıdaki örnek, bir bölge tanımlamasına gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="3192a-105">The following example shows how to define a region:</span></span>  
  
```csharp
#region MyClass definition  
public class MyClass   
{  
    static void Main()   
    {  
    }  
}  
#endregion  
```  
  
## <a name="remarks"></a><span data-ttu-id="3192a-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3192a-106">Remarks</span></span>  
 <span data-ttu-id="3192a-107">A `#region` blok sonlandırıldı, ile bir [#endregion](../../../csharp/language-reference/preprocessor-directives/preprocessor-endregion.md) yönergesi.</span><span class="sxs-lookup"><span data-stu-id="3192a-107">A `#region` block must be terminated with a [#endregion](../../../csharp/language-reference/preprocessor-directives/preprocessor-endregion.md) directive.</span></span>  
  
 <span data-ttu-id="3192a-108">A `#region` bloğu ile örtüşemez bir [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) bloğu.</span><span class="sxs-lookup"><span data-stu-id="3192a-108">A `#region` block cannot overlap with a [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) block.</span></span> <span data-ttu-id="3192a-109">Ancak, bir `#region` bloğu iç içe geçirilemez içinde bir `#if` bloğu ve `#if` bloğu iç içe geçirilemez içinde bir `#region` blok.</span><span class="sxs-lookup"><span data-stu-id="3192a-109">However, a `#region` block can be nested in a `#if` block, and a `#if` block can be nested in a `#region` block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3192a-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3192a-110">See Also</span></span>  
 [<span data-ttu-id="3192a-111">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="3192a-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="3192a-112">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="3192a-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="3192a-113">C# önişlemci yönergeleri</span><span class="sxs-lookup"><span data-stu-id="3192a-113">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
