---
title: '#uyarı - C# Referans'
ms.date: 07/20/2015
f1_keywords:
- '#warning'
helpviewer_keywords:
- '#warning directive [C#]'
ms.assetid: e6fb496d-bb8b-4018-baf6-5b60a0c8902b
ms.openlocfilehash: 38c3807a696599390667060d3bf374c68845fed0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715063"
---
# <a name="warning-c-reference"></a><span data-ttu-id="33dd9-102">#warning (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="33dd9-102">#warning (C# Reference)</span></span>
<span data-ttu-id="33dd9-103">`#warning`kodunuzda belirli bir konumdan [bir CS1030](../../misc/cs1030.md) düzey bir derleyici uyarısı oluşturmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="33dd9-103">`#warning` lets you generate a [CS1030](../../misc/cs1030.md) level one compiler warning from a specific location in your code.</span></span> <span data-ttu-id="33dd9-104">Örnek:</span><span class="sxs-lookup"><span data-stu-id="33dd9-104">For example:</span></span>  
  
```csharp
#warning Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="33dd9-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="33dd9-105">Remarks</span></span>
 <span data-ttu-id="33dd9-106">Yaygın bir `#warning` kullanım koşullu bir yönergede yer alan bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="33dd9-106">A common use of `#warning` is in a conditional directive.</span></span> <span data-ttu-id="33dd9-107">[#error](./preprocessor-error.md)ile kullanıcı tanımlı bir hata oluşturmak da mümkündür.</span><span class="sxs-lookup"><span data-stu-id="33dd9-107">It is also possible to generate a user-defined error with [#error](./preprocessor-error.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="33dd9-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="33dd9-108">Example</span></span>  

```csharp
// preprocessor_warning.cs  
// CS1030 expected  
#define DEBUG  
class MainClass
{  
    static void Main()
    {  
#if DEBUG  
#warning DEBUG is defined  
#endif  
    }  
}  
```  

## <a name="see-also"></a><span data-ttu-id="33dd9-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="33dd9-109">See also</span></span>

- [<span data-ttu-id="33dd9-110">C# Referans</span><span class="sxs-lookup"><span data-stu-id="33dd9-110">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="33dd9-111">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="33dd9-111">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="33dd9-112">C# Önİşleme İşlemciler Direktifleri</span><span class="sxs-lookup"><span data-stu-id="33dd9-112">C# Preprocessor Directives</span></span>](./index.md)
