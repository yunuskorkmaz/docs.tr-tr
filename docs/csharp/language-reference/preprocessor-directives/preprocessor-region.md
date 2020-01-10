---
title: '#Bölge C# başvurusu'
ms.date: 07/20/2015
f1_keywords:
- '#region'
helpviewer_keywords:
- '#region directive [C#]'
ms.assetid: 672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4
ms.openlocfilehash: 723a904d18955caceea9e0d485ab51f84366c66e
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715126"
---
# <a name="region-c-reference"></a><span data-ttu-id="60d14-102">#region (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="60d14-102">#region (C# Reference)</span></span>
<span data-ttu-id="60d14-103">`#region`, Visual Studio Code düzenleyicisinin ana [hat](/visualstudio/ide/outlining) özelliğini kullanırken genişletebileceğiniz veya daraltabileceğiniz bir kod bloğu belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="60d14-103">`#region` lets you specify a block of code that you can expand or collapse when using the [outlining](/visualstudio/ide/outlining) feature of the Visual Studio Code Editor.</span></span> <span data-ttu-id="60d14-104">Daha uzun kod dosyalarında, üzerinde çalışmakta olduğunuz dosyanın bölümüne odaklanabilmeniz için bir veya daha fazla bölgenin daraltılanması veya gizlenmesi uygun olabilir.</span><span class="sxs-lookup"><span data-stu-id="60d14-104">In longer code files, it is convenient to be able to collapse or hide one or more regions so that you can focus on the part of the file that you are currently working on.</span></span> <span data-ttu-id="60d14-105">Aşağıdaki örnek, bir bölgenin nasıl tanımlanacağını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="60d14-105">The following example shows how to define a region:</span></span>  
  
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
  
## <a name="remarks"></a><span data-ttu-id="60d14-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="60d14-106">Remarks</span></span>  
 <span data-ttu-id="60d14-107">Bir `#region` bloğunun [#endregion](./preprocessor-endregion.md) yönergesiyle sonlandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="60d14-107">A `#region` block must be terminated with a [#endregion](./preprocessor-endregion.md) directive.</span></span>  
  
 <span data-ttu-id="60d14-108">`#region` bloğu bir [#if](./preprocessor-if.md) bloğuyla çakışamaz.</span><span class="sxs-lookup"><span data-stu-id="60d14-108">A `#region` block cannot overlap with a [#if](./preprocessor-if.md) block.</span></span> <span data-ttu-id="60d14-109">Ancak, bir `#region` bloğu bir `#if` bloğunda iç içe olabilir ve bir `#if` bloğu bir `#region` bloğunda iç içe geçmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="60d14-109">However, a `#region` block can be nested in a `#if` block, and a `#if` block can be nested in a `#region` block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60d14-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="60d14-110">See also</span></span>

- [<span data-ttu-id="60d14-111">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="60d14-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="60d14-112">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="60d14-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="60d14-113">C# Ön İşlemci Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="60d14-113">C# Preprocessor Directives</span></span>](./index.md)
