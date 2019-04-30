---
title: '#Uyarı - C# başvurusu'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#warning'
helpviewer_keywords:
- '#warning directive [C#]'
ms.assetid: e6fb496d-bb8b-4018-baf6-5b60a0c8902b
ms.openlocfilehash: 55768a354b2841021607ed40b4ef87b9767edcad
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61659962"
---
# <a name="warning-c-reference"></a><span data-ttu-id="cbf5f-102">#warning (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="cbf5f-102">#warning (C# Reference)</span></span>
<span data-ttu-id="cbf5f-103">`#warning` oluşturmanıza olanak sağlar. bir [CS1030](../../misc/cs1030.md) kodunuzda belirli bir konumdan bir derleyici uyarısı düzeyi.</span><span class="sxs-lookup"><span data-stu-id="cbf5f-103">`#warning` lets you generate a [CS1030](../../misc/cs1030.md) level one compiler warning from a specific location in your code.</span></span> <span data-ttu-id="cbf5f-104">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="cbf5f-104">For example:</span></span>  
  
```csharp
#warning Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="cbf5f-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cbf5f-105">Remarks</span></span>
 <span data-ttu-id="cbf5f-106">Yaygın `#warning` bir koşullu yönergesiyse.</span><span class="sxs-lookup"><span data-stu-id="cbf5f-106">A common use of `#warning` is in a conditional directive.</span></span> <span data-ttu-id="cbf5f-107">Kullanıcı tanımlı bir hata ile oluşturmak mümkündür [#error](../../../csharp/language-reference/preprocessor-directives/preprocessor-error.md).</span><span class="sxs-lookup"><span data-stu-id="cbf5f-107">It is also possible to generate a user-defined error with [#error](../../../csharp/language-reference/preprocessor-directives/preprocessor-error.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cbf5f-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="cbf5f-108">Example</span></span>  

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

## <a name="see-also"></a><span data-ttu-id="cbf5f-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cbf5f-109">See also</span></span>

- [<span data-ttu-id="cbf5f-110">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="cbf5f-110">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="cbf5f-111">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="cbf5f-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="cbf5f-112">C# Ön İşlemci Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="cbf5f-112">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
