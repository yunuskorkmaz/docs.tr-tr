---
description: '#Region-C# başvurusu'
title: '#Region-C# başvurusu'
ms.date: 07/20/2015
f1_keywords:
- '#region'
helpviewer_keywords:
- '#region directive [C#]'
ms.assetid: 672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4
ms.openlocfilehash: dcb806a213bea9d7c782eeddc712f1eb76257e80
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91186412"
---
# <a name="region-c-reference"></a><span data-ttu-id="42656-103">#region (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="42656-103">#region (C# Reference)</span></span>

<span data-ttu-id="42656-104">`#region` kod düzenleyicisinin ana [hat](/visualstudio/ide/outlining) özelliğini kullanırken genişletebileceğiniz veya daraltabileceğiniz bir kod bloğu belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="42656-104">`#region` lets you specify a block of code that you can expand or collapse when using the [outlining](/visualstudio/ide/outlining) feature of the code editor.</span></span> <span data-ttu-id="42656-105">Daha uzun kod dosyalarında, üzerinde çalışmakta olduğunuz dosyanın bölümüne odaklanabilmeniz için bir veya daha fazla bölgenin daraltılanması veya gizlenmesi uygun olabilir.</span><span class="sxs-lookup"><span data-stu-id="42656-105">In longer code files, it is convenient to be able to collapse or hide one or more regions so that you can focus on the part of the file that you are currently working on.</span></span> <span data-ttu-id="42656-106">Aşağıdaki örnek, bir bölgenin nasıl tanımlanacağını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="42656-106">The following example shows how to define a region:</span></span>  
  
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
  
## <a name="remarks"></a><span data-ttu-id="42656-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="42656-107">Remarks</span></span>  

 <span data-ttu-id="42656-108">Bir `#region` blok, bir [#endregion](./preprocessor-endregion.md) yönergesi ile sonlandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="42656-108">A `#region` block must be terminated with a [#endregion](./preprocessor-endregion.md) directive.</span></span>  
  
 <span data-ttu-id="42656-109">Bir `#region` blok [#if](./preprocessor-if.md) bloğuyla çakışamaz.</span><span class="sxs-lookup"><span data-stu-id="42656-109">A `#region` block cannot overlap with a [#if](./preprocessor-if.md) block.</span></span> <span data-ttu-id="42656-110">Ancak bir blok `#region` bir blokta iç içe olabilir ve bir blok `#if` bir blok `#if` içinde iç içe olabilir `#region` .</span><span class="sxs-lookup"><span data-stu-id="42656-110">However, a `#region` block can be nested in a `#if` block, and a `#if` block can be nested in a `#region` block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42656-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="42656-111">See also</span></span>

- [<span data-ttu-id="42656-112">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="42656-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="42656-113">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="42656-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="42656-114">C# Önişlemci yönergeleri</span><span class="sxs-lookup"><span data-stu-id="42656-114">C# Preprocessor Directives</span></span>](./index.md)
