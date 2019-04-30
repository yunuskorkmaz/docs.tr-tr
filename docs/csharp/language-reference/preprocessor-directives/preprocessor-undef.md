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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61688572"
---
# <a name="undef-c-reference"></a><span data-ttu-id="ff9e0-102">#undef (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="ff9e0-102">#undef (C# Reference)</span></span>
<span data-ttu-id="ff9e0-103">`#undef` Bir sembolün tanımını olanak tanır şekilde sembol deyim olarak kullanarak, bir [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) yönergesi, ifade için değerlendirilecek olan `false`.</span><span class="sxs-lookup"><span data-stu-id="ff9e0-103">`#undef` lets you undefine a symbol, such that, by using the symbol as the expression in a [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) directive, the expression will evaluate to `false`.</span></span>  
  
 <span data-ttu-id="ff9e0-104">Bir sembol olabilir ya da ile tanımlanan [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) yönergesi veya [-tanımlama](../../../csharp/language-reference/compiler-options/define-compiler-option.md) derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="ff9e0-104">A symbol can be defined either with the [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) directive or the [-define](../../../csharp/language-reference/compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="ff9e0-105">`#undef` Yönergeleri de yer almayan herhangi bir deyim kullanmadan önce yönergesi dosyada görünmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="ff9e0-105">The `#undef` directive must appear in the file before you use any statements that are not also directives.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ff9e0-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="ff9e0-106">Example</span></span>  

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

<span data-ttu-id="ff9e0-107">**Hata ayıklama tanımlı değil**</span><span class="sxs-lookup"><span data-stu-id="ff9e0-107">**DEBUG is not defined**</span></span>

## <a name="see-also"></a><span data-ttu-id="ff9e0-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ff9e0-108">See also</span></span>

- [<span data-ttu-id="ff9e0-109">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="ff9e0-109">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="ff9e0-110">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ff9e0-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="ff9e0-111">C# Ön İşlemci Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="ff9e0-111">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
