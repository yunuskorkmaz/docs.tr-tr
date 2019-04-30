---
title: '#Bölge - C# başvurusu'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#region'
helpviewer_keywords:
- '#region directive [C#]'
ms.assetid: 672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4
ms.openlocfilehash: adaa58fc47da557a31270e99ff8a1dae3d0731bb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61659988"
---
# <a name="region-c-reference"></a><span data-ttu-id="00ad5-102">#region (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="00ad5-102">#region (C# Reference)</span></span>
<span data-ttu-id="00ad5-103">`#region` Genişlet veya daralt kullanarak bir kod bloğunu belirtmenizi sağlar [anahat oluşturma](/visualstudio/ide/outlining) özelliği, Visual Studio Kod Düzenleyicisi.</span><span class="sxs-lookup"><span data-stu-id="00ad5-103">`#region` lets you specify a block of code that you can expand or collapse when using the [outlining](/visualstudio/ide/outlining) feature of the Visual Studio Code Editor.</span></span> <span data-ttu-id="00ad5-104">Uzun kod dosyalarında Daralt veya, üzerinde çalıştığınız dosya yoluna odaklanabilmeniz için bir veya daha fazla bölgede gizlemek uygundur.</span><span class="sxs-lookup"><span data-stu-id="00ad5-104">In longer code files, it is convenient to be able to collapse or hide one or more regions so that you can focus on the part of the file that you are currently working on.</span></span> <span data-ttu-id="00ad5-105">Aşağıdaki örnek, bir bölge tanımlamasına gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="00ad5-105">The following example shows how to define a region:</span></span>  
  
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
  
## <a name="remarks"></a><span data-ttu-id="00ad5-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="00ad5-106">Remarks</span></span>  
 <span data-ttu-id="00ad5-107">A `#region` blok sonlandırıldı, ile bir [#endregion](../../../csharp/language-reference/preprocessor-directives/preprocessor-endregion.md) yönergesi.</span><span class="sxs-lookup"><span data-stu-id="00ad5-107">A `#region` block must be terminated with a [#endregion](../../../csharp/language-reference/preprocessor-directives/preprocessor-endregion.md) directive.</span></span>  
  
 <span data-ttu-id="00ad5-108">A `#region` blok ile örtüşemez bir [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) blok.</span><span class="sxs-lookup"><span data-stu-id="00ad5-108">A `#region` block cannot overlap with a [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) block.</span></span> <span data-ttu-id="00ad5-109">Ancak, bir `#region` blok iç içe geçirilemez içinde bir `#if` bloğu ve `#if` blok iç içe geçirilemez bir `#region` blok.</span><span class="sxs-lookup"><span data-stu-id="00ad5-109">However, a `#region` block can be nested in a `#if` block, and a `#if` block can be nested in a `#region` block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00ad5-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="00ad5-110">See also</span></span>

- [<span data-ttu-id="00ad5-111">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="00ad5-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="00ad5-112">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="00ad5-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="00ad5-113">C# Ön İşlemci Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="00ad5-113">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
