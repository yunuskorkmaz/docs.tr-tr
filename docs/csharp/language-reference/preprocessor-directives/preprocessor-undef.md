---
description: '#undef-C# başvurusu'
title: '#undef-C# başvurusu'
ms.date: 06/30/2018
f1_keywords:
- '#undef'
helpviewer_keywords:
- '#undef directive [C#]'
ms.assetid: 686c92d2-7194-4be4-b2f4-80091712d513
ms.openlocfilehash: 7db79be7ea9d8462e09b6ae874bf0ae7d265afe2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91150563"
---
# <a name="undef-c-reference"></a><span data-ttu-id="4e172-103">#undef (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="4e172-103">#undef (C# Reference)</span></span>

<span data-ttu-id="4e172-104">`#undef` bir simge tanımlamanızı sağlar, örneğin, simgeyi bir [#if](./preprocessor-if.md) yönergesinde ifade olarak kullanarak ifade edilir `false` .</span><span class="sxs-lookup"><span data-stu-id="4e172-104">`#undef` lets you undefine a symbol, such that, by using the symbol as the expression in a [#if](./preprocessor-if.md) directive, the expression will evaluate to `false`.</span></span>  
  
 <span data-ttu-id="4e172-105">Bir sembol [#define](./preprocessor-define.md) yönergesi veya [-define](../compiler-options/define-compiler-option.md) derleyici seçeneği ile tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="4e172-105">A symbol can be defined either with the [#define](./preprocessor-define.md) directive or the [-define](../compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="4e172-106">`#undef`Ayrıca, yönergesi olmayan hiçbir deyimi kullanmadan önce yönerge dosyada görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="4e172-106">The `#undef` directive must appear in the file before you use any statements that are not also directives.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e172-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="4e172-107">Example</span></span>  

```csharp
// preprocessor_undef.cs  
// compile with: /d:DEBUG  
#undef DEBUG  
using System;  
class MyClass
{  
    static void Main()
    {  
#if DEBUG  
        Console.WriteLine("DEBUG is defined");  
#else  
        Console.WriteLine("DEBUG is not defined");  
#endif  
    }  
}  
```

<span data-ttu-id="4e172-108">**Hata ayıklama tanımlı değil**</span><span class="sxs-lookup"><span data-stu-id="4e172-108">**DEBUG is not defined**</span></span>

## <a name="see-also"></a><span data-ttu-id="4e172-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4e172-109">See also</span></span>

- [<span data-ttu-id="4e172-110">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="4e172-110">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="4e172-111">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="4e172-111">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="4e172-112">C# Önişlemci yönergeleri</span><span class="sxs-lookup"><span data-stu-id="4e172-112">C# Preprocessor Directives</span></span>](./index.md)
