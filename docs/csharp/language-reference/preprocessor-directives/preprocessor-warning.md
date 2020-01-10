---
title: '#Uyarı- C# başvuru'
ms.date: 07/20/2015
f1_keywords:
- '#warning'
helpviewer_keywords:
- '#warning directive [C#]'
ms.assetid: e6fb496d-bb8b-4018-baf6-5b60a0c8902b
ms.openlocfilehash: 38c3807a696599390667060d3bf374c68845fed0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715063"
---
# <a name="warning-c-reference"></a><span data-ttu-id="9907f-102">#warning (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="9907f-102">#warning (C# Reference)</span></span>
<span data-ttu-id="9907f-103">`#warning` kodunuzda belirli bir konumdan [bir derleyici](../../misc/cs1030.md) uyarısı oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="9907f-103">`#warning` lets you generate a [CS1030](../../misc/cs1030.md) level one compiler warning from a specific location in your code.</span></span> <span data-ttu-id="9907f-104">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="9907f-104">For example:</span></span>  
  
```csharp
#warning Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="9907f-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9907f-105">Remarks</span></span>
 <span data-ttu-id="9907f-106">`#warning` ortak bir kullanımı koşullu yönergedir.</span><span class="sxs-lookup"><span data-stu-id="9907f-106">A common use of `#warning` is in a conditional directive.</span></span> <span data-ttu-id="9907f-107">[#Error](./preprocessor-error.md)ile Kullanıcı tanımlı bir hata oluşturmak da mümkündür.</span><span class="sxs-lookup"><span data-stu-id="9907f-107">It is also possible to generate a user-defined error with [#error](./preprocessor-error.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9907f-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="9907f-108">Example</span></span>  

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

## <a name="see-also"></a><span data-ttu-id="9907f-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9907f-109">See also</span></span>

- [<span data-ttu-id="9907f-110">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="9907f-110">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="9907f-111">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="9907f-111">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="9907f-112">C# Ön İşlemci Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="9907f-112">C# Preprocessor Directives</span></span>](./index.md)
