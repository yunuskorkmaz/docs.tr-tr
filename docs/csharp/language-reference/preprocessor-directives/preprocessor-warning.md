---
title: '#Uyarı (C# Başvurusu)'
ms.date: 07/20/2015
f1_keywords:
- '#warning'
helpviewer_keywords:
- '#warning directive [C#]'
ms.assetid: e6fb496d-bb8b-4018-baf6-5b60a0c8902b
ms.openlocfilehash: 59ca63d5089e377627a9116f24f9a0a1681bb4b2
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43506353"
---
# <a name="warning-c-reference"></a><span data-ttu-id="170a2-102">#warning (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="170a2-102">#warning (C# Reference)</span></span>
<span data-ttu-id="170a2-103">`#warning` oluşturmanıza olanak sağlar. bir [CS1030](../../misc/cs1030.md) kodunuzda belirli bir konumdan bir derleyici uyarısı düzeyi.</span><span class="sxs-lookup"><span data-stu-id="170a2-103">`#warning` lets you generate a [CS1030](../../misc/cs1030.md) level one compiler warning from a specific location in your code.</span></span> <span data-ttu-id="170a2-104">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="170a2-104">For example:</span></span>  
  
```csharp
#warning Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="170a2-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="170a2-105">Remarks</span></span>
 <span data-ttu-id="170a2-106">Yaygın `#warning` bir koşullu yönergesiyse.</span><span class="sxs-lookup"><span data-stu-id="170a2-106">A common use of `#warning` is in a conditional directive.</span></span> <span data-ttu-id="170a2-107">Kullanıcı tanımlı bir hata ile oluşturmak mümkündür [#error](../../../csharp/language-reference/preprocessor-directives/preprocessor-error.md).</span><span class="sxs-lookup"><span data-stu-id="170a2-107">It is also possible to generate a user-defined error with [#error](../../../csharp/language-reference/preprocessor-directives/preprocessor-error.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="170a2-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="170a2-108">Example</span></span>  

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

## <a name="see-also"></a><span data-ttu-id="170a2-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="170a2-109">See Also</span></span>

- [<span data-ttu-id="170a2-110">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="170a2-110">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="170a2-111">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="170a2-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="170a2-112">C# Ön İşlemci Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="170a2-112">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
