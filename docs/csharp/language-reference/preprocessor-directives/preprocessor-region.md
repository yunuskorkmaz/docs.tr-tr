---
title: '#bölge - C# Referans'
ms.date: 07/20/2015
f1_keywords:
- '#region'
helpviewer_keywords:
- '#region directive [C#]'
ms.assetid: 672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4
ms.openlocfilehash: 48e8a6796c3b07b348fd988a9b8501ee496b8ad5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173399"
---
# <a name="region-c-reference"></a><span data-ttu-id="28499-102">#region (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="28499-102">#region (C# Reference)</span></span>
<span data-ttu-id="28499-103">`#region`Visual Studio Code Editor'un [anahat](/visualstudio/ide/outlining) özelliğini kullanırken genişletebileceğiniz veya daraltabileceğiniz bir kod bloğu belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="28499-103">`#region` lets you specify a block of code that you can expand or collapse when using the [outlining](/visualstudio/ide/outlining) feature of the Visual Studio Code Editor.</span></span> <span data-ttu-id="28499-104">Uzun kod dosyalarında, şu anda üzerinde çalıştığınız dosya parçasına odaklanabilmeniz için bir veya daha fazla bölgeyi daraltmak veya gizlemek uygundur.</span><span class="sxs-lookup"><span data-stu-id="28499-104">In longer code files, it is convenient to be able to collapse or hide one or more regions so that you can focus on the part of the file that you are currently working on.</span></span> <span data-ttu-id="28499-105">Aşağıdaki örnek, bir bölgenin nasıl tanımlandığını gösterir:</span><span class="sxs-lookup"><span data-stu-id="28499-105">The following example shows how to define a region:</span></span>  
  
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
  
## <a name="remarks"></a><span data-ttu-id="28499-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="28499-106">Remarks</span></span>  
 <span data-ttu-id="28499-107">Bir `#region` blok [#endregion](./preprocessor-endregion.md) bir yönerge ile sonlandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="28499-107">A `#region` block must be terminated with a [#endregion](./preprocessor-endregion.md) directive.</span></span>  
  
 <span data-ttu-id="28499-108">Bir `#region` blok [#if](./preprocessor-if.md) bir blokla çakışamaz.</span><span class="sxs-lookup"><span data-stu-id="28499-108">A `#region` block cannot overlap with a [#if](./preprocessor-if.md) block.</span></span> <span data-ttu-id="28499-109">Ancak, `#region` bir blok bir `#if` blok iç içe `#if` olabilir ve bir `#region` blok bir blok iç içe olabilir.</span><span class="sxs-lookup"><span data-stu-id="28499-109">However, a `#region` block can be nested in a `#if` block, and a `#if` block can be nested in a `#region` block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28499-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="28499-110">See also</span></span>

- [<span data-ttu-id="28499-111">C# Referans</span><span class="sxs-lookup"><span data-stu-id="28499-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="28499-112">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="28499-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="28499-113">C# Önİşleme İşlemciler Direktifleri</span><span class="sxs-lookup"><span data-stu-id="28499-113">C# Preprocessor Directives</span></span>](./index.md)
