---
title: '#hata - C# Başvuru'
ms.date: 07/20/2015
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive [C#]'
ms.assetid: f2a7f3af-4cf9-4111-b369-70204d24b26b
ms.openlocfilehash: 28e77304edee617adc1422e6a52d0a617cd9b3bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173412"
---
# <a name="error-c-reference"></a><span data-ttu-id="3b94c-102">#error (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="3b94c-102">#error (C# Reference)</span></span>
<span data-ttu-id="3b94c-103">`#error`kodunuzda belirli bir konumdan [CS1029](../compiler-messages/cs1029.md) kullanıcı tanımlı bir hata oluşturmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="3b94c-103">`#error` lets you generate a [CS1029](../compiler-messages/cs1029.md) user-defined error from a specific location in your code.</span></span> <span data-ttu-id="3b94c-104">Örnek:</span><span class="sxs-lookup"><span data-stu-id="3b94c-104">For example:</span></span>  
  
```csharp
#error Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="3b94c-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3b94c-105">Remarks</span></span>  
 <span data-ttu-id="3b94c-106">Yaygın bir `#error` kullanım koşullu bir yönergede yer alan bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="3b94c-106">A common use of `#error` is in a conditional directive.</span></span>  
  
 <span data-ttu-id="3b94c-107">[#warning](./preprocessor-warning.md)ile kullanıcı tanımlı bir uyarı oluşturmak da mümkündür.</span><span class="sxs-lookup"><span data-stu-id="3b94c-107">It is also possible to generate a user-defined warning with [#warning](./preprocessor-warning.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b94c-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="3b94c-108">Example</span></span>  
  
```csharp
// preprocessor_error.cs  
// CS1029 expected  
#define DEBUG  
class MainClass
{  
    static void Main()
    {  
#if DEBUG  
#error DEBUG is defined  
#endif  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="3b94c-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3b94c-109">See also</span></span>

- [<span data-ttu-id="3b94c-110">C# Referans</span><span class="sxs-lookup"><span data-stu-id="3b94c-110">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="3b94c-111">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="3b94c-111">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="3b94c-112">C# Önİşleme İşlemciler Direktifleri</span><span class="sxs-lookup"><span data-stu-id="3b94c-112">C# Preprocessor Directives</span></span>](./index.md)
