---
description: '#undef-C# başvurusu'
title: '#undef-C# başvurusu'
ms.date: 06/30/2018
f1_keywords:
- '#undef'
helpviewer_keywords:
- '#undef directive [C#]'
ms.assetid: 686c92d2-7194-4be4-b2f4-80091712d513
ms.openlocfilehash: ecbf8f5793e70c7dd6e602a3992ee3783a76c7ca
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2021
ms.locfileid: "103477983"
---
# <a name="undef-c-reference"></a><span data-ttu-id="05002-103">#undef (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="05002-103">#undef (C# Reference)</span></span>

<span data-ttu-id="05002-104">`#undef` bir simge tanımlamanızı sağlar, örneğin, simgeyi bir [#if](./preprocessor-if.md) yönergesinde ifade olarak kullanarak ifade edilir `false` .</span><span class="sxs-lookup"><span data-stu-id="05002-104">`#undef` lets you undefine a symbol, such that, by using the symbol as the expression in a [#if](./preprocessor-if.md) directive, the expression will evaluate to `false`.</span></span>  
  
 <span data-ttu-id="05002-105">Bir sembol [#define](./preprocessor-define.md) yönergesi veya [**definesabitleri**](../compiler-options/language.md#defineconstants) derleyici seçeneği ile tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="05002-105">A symbol can be defined either with the [#define](./preprocessor-define.md) directive or the [**DefineConstants**](../compiler-options/language.md#defineconstants) compiler option.</span></span> <span data-ttu-id="05002-106">`#undef`Ayrıca, yönergesi olmayan hiçbir deyimi kullanmadan önce yönerge dosyada görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="05002-106">The `#undef` directive must appear in the file before you use any statements that are not also directives.</span></span>  
  
## <a name="example"></a><span data-ttu-id="05002-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="05002-107">Example</span></span>  

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

<span data-ttu-id="05002-108">**Hata ayıklama tanımlı değil**</span><span class="sxs-lookup"><span data-stu-id="05002-108">**DEBUG is not defined**</span></span>

## <a name="see-also"></a><span data-ttu-id="05002-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="05002-109">See also</span></span>

- [<span data-ttu-id="05002-110">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="05002-110">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="05002-111">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="05002-111">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="05002-112">C# Önişlemci yönergeleri</span><span class="sxs-lookup"><span data-stu-id="05002-112">C# Preprocessor Directives</span></span>](./index.md)
