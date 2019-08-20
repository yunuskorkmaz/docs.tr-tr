---
title: '#Bölge C# başvurusu'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#region'
helpviewer_keywords:
- '#region directive [C#]'
ms.assetid: 672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4
ms.openlocfilehash: ba5b47d77c69761a77b05ac6079e1b003af336b3
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608758"
---
# <a name="region-c-reference"></a><span data-ttu-id="724d1-102">#region (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="724d1-102">#region (C# Reference)</span></span>
<span data-ttu-id="724d1-103">`#region`Visual Studio Code düzenleyicisinin ana [hat](/visualstudio/ide/outlining) özelliğini kullanırken genişletebileceğiniz veya daraltabileceğiniz bir kod bloğu belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="724d1-103">`#region` lets you specify a block of code that you can expand or collapse when using the [outlining](/visualstudio/ide/outlining) feature of the Visual Studio Code Editor.</span></span> <span data-ttu-id="724d1-104">Daha uzun kod dosyalarında, üzerinde çalışmakta olduğunuz dosyanın bölümüne odaklanabilmeniz için bir veya daha fazla bölgenin daraltılanması veya gizlenmesi uygun olabilir.</span><span class="sxs-lookup"><span data-stu-id="724d1-104">In longer code files, it is convenient to be able to collapse or hide one or more regions so that you can focus on the part of the file that you are currently working on.</span></span> <span data-ttu-id="724d1-105">Aşağıdaki örnek, bir bölgenin nasıl tanımlanacağını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="724d1-105">The following example shows how to define a region:</span></span>  
  
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
  
## <a name="remarks"></a><span data-ttu-id="724d1-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="724d1-106">Remarks</span></span>  
 <span data-ttu-id="724d1-107">Bir `#region` blok, bir [#endregion](./preprocessor-endregion.md) yönergesi ile sonlandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="724d1-107">A `#region` block must be terminated with a [#endregion](./preprocessor-endregion.md) directive.</span></span>  
  
 <span data-ttu-id="724d1-108">Bir `#region` blok [#if](./preprocessor-if.md) bloğuyla çakışamaz.</span><span class="sxs-lookup"><span data-stu-id="724d1-108">A `#region` block cannot overlap with a [#if](./preprocessor-if.md) block.</span></span> <span data-ttu-id="724d1-109">Ancak bir blok bir `#if` blokta iç içe olabilir ve `#if` bir blok bir `#region` blok içinde iç içe olabilir. `#region`</span><span class="sxs-lookup"><span data-stu-id="724d1-109">However, a `#region` block can be nested in a `#if` block, and a `#if` block can be nested in a `#region` block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="724d1-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="724d1-110">See also</span></span>

- [<span data-ttu-id="724d1-111">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="724d1-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="724d1-112">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="724d1-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="724d1-113">C# Ön İşlemci Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="724d1-113">C# Preprocessor Directives</span></span>](./index.md)
