---
title: '#undef - C# Referans'
ms.date: 06/30/2018
f1_keywords:
- '#undef'
helpviewer_keywords:
- '#undef directive [C#]'
ms.assetid: 686c92d2-7194-4be4-b2f4-80091712d513
ms.openlocfilehash: 21923412aa178c3b86e94a54bd911130e48e4deb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712448"
---
# <a name="undef-c-reference"></a><span data-ttu-id="ab197-102">#undef (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="ab197-102">#undef (C# Reference)</span></span>
<span data-ttu-id="ab197-103">`#undef`bir #if yönergesindeki ifade olarak sembolü kullanarak ifadeyi değerlendirecek [#if](./preprocessor-if.md) `false`şekilde bir sembolü tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="ab197-103">`#undef` lets you undefine a symbol, such that, by using the symbol as the expression in a [#if](./preprocessor-if.md) directive, the expression will evaluate to `false`.</span></span>  
  
 <span data-ttu-id="ab197-104">Bir [sembol, #define](./preprocessor-define.md) yönergesi veya [-define](../compiler-options/define-compiler-option.md) derleyici seçeneği ile tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="ab197-104">A symbol can be defined either with the [#define](./preprocessor-define.md) directive or the [-define](../compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="ab197-105">Yönerge, `#undef` yönerge olmayan ifadeleri kullanmadan önce dosyada görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="ab197-105">The `#undef` directive must appear in the file before you use any statements that are not also directives.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab197-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="ab197-106">Example</span></span>  

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

<span data-ttu-id="ab197-107">**HATA Ayıklama tanımlı değil**</span><span class="sxs-lookup"><span data-stu-id="ab197-107">**DEBUG is not defined**</span></span>

## <a name="see-also"></a><span data-ttu-id="ab197-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ab197-108">See also</span></span>

- [<span data-ttu-id="ab197-109">C# Referans</span><span class="sxs-lookup"><span data-stu-id="ab197-109">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ab197-110">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ab197-110">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="ab197-111">C# Önİşleme İşlemciler Direktifleri</span><span class="sxs-lookup"><span data-stu-id="ab197-111">C# Preprocessor Directives</span></span>](./index.md)
