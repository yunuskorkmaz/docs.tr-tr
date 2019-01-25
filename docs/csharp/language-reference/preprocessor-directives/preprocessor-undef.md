---
title: '#undef - C# başvurusu'
ms.custom: seodec18
ms.date: 06/30/2018
f1_keywords:
- '#undef'
helpviewer_keywords:
- '#undef directive [C#]'
ms.assetid: 686c92d2-7194-4be4-b2f4-80091712d513
ms.openlocfilehash: 0dedd1480dae15d2c04b47cee132ab3227098f56
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54739042"
---
# <a name="undef-c-reference"></a><span data-ttu-id="5fde7-102">#undef (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="5fde7-102">#undef (C# Reference)</span></span>
<span data-ttu-id="5fde7-103">`#undef` Bir sembolün tanımını olanak tanır şekilde sembol deyim olarak kullanarak, bir [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) yönergesi, ifade için değerlendirilecek olan `false`.</span><span class="sxs-lookup"><span data-stu-id="5fde7-103">`#undef` lets you undefine a symbol, such that, by using the symbol as the expression in a [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) directive, the expression will evaluate to `false`.</span></span>  
  
 <span data-ttu-id="5fde7-104">Bir sembol olabilir ya da ile tanımlanan [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) yönergesi veya [-tanımlama](../../../csharp/language-reference/compiler-options/define-compiler-option.md) derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="5fde7-104">A symbol can be defined either with the [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) directive or the [-define](../../../csharp/language-reference/compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="5fde7-105">`#undef` Yönergeleri de yer almayan herhangi bir deyim kullanmadan önce yönergesi dosyada görünmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="5fde7-105">The `#undef` directive must appear in the file before you use any statements that are not also directives.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5fde7-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="5fde7-106">Example</span></span>  

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

<span data-ttu-id="5fde7-107">**Hata ayıklama tanımlı değil**</span><span class="sxs-lookup"><span data-stu-id="5fde7-107">**DEBUG is not defined**</span></span>

## <a name="see-also"></a><span data-ttu-id="5fde7-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5fde7-108">See also</span></span>

- [<span data-ttu-id="5fde7-109">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="5fde7-109">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="5fde7-110">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="5fde7-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="5fde7-111">C# Ön İşlemci Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="5fde7-111">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
