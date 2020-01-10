---
title: '#undef- C# başvuru'
ms.date: 06/30/2018
f1_keywords:
- '#undef'
helpviewer_keywords:
- '#undef directive [C#]'
ms.assetid: 686c92d2-7194-4be4-b2f4-80091712d513
ms.openlocfilehash: 21923412aa178c3b86e94a54bd911130e48e4deb
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712448"
---
# <a name="undef-c-reference"></a><span data-ttu-id="c4d8e-102">#undef (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="c4d8e-102">#undef (C# Reference)</span></span>
<span data-ttu-id="c4d8e-103">`#undef` bir sembol tanımlamanızı sağlar, örneğin, simgeyi bir [#if](./preprocessor-if.md) yönergesinde ifade olarak kullanarak, ifade `false`olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="c4d8e-103">`#undef` lets you undefine a symbol, such that, by using the symbol as the expression in a [#if](./preprocessor-if.md) directive, the expression will evaluate to `false`.</span></span>  
  
 <span data-ttu-id="c4d8e-104">Bir sembol [#define](./preprocessor-define.md) yönergesi veya [-define](../compiler-options/define-compiler-option.md) derleyici seçeneği ile tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="c4d8e-104">A symbol can be defined either with the [#define](./preprocessor-define.md) directive or the [-define](../compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="c4d8e-105">Ayrıca, yönergesi olmayan deyimleri kullanmadan önce `#undef` yönergesinin dosyada görünmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="c4d8e-105">The `#undef` directive must appear in the file before you use any statements that are not also directives.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4d8e-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="c4d8e-106">Example</span></span>  

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

<span data-ttu-id="c4d8e-107">**Hata ayıklama tanımlı değil**</span><span class="sxs-lookup"><span data-stu-id="c4d8e-107">**DEBUG is not defined**</span></span>

## <a name="see-also"></a><span data-ttu-id="c4d8e-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c4d8e-108">See also</span></span>

- [<span data-ttu-id="c4d8e-109">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="c4d8e-109">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c4d8e-110">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c4d8e-110">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c4d8e-111">C# Ön İşlemci Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="c4d8e-111">C# Preprocessor Directives</span></span>](./index.md)
