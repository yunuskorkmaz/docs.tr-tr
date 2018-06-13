---
title: '#Uyarı (C# Başvurusu)'
ms.date: 07/20/2015
f1_keywords:
- '#warning'
helpviewer_keywords:
- '#warning directive [C#]'
ms.assetid: e6fb496d-bb8b-4018-baf6-5b60a0c8902b
ms.openlocfilehash: c56458e0100c23450655e48b2abfb346e18e0bb8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33268189"
---
# <a name="warning-c-reference"></a><span data-ttu-id="5206e-102">#warning (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="5206e-102">#warning (C# Reference)</span></span>
<span data-ttu-id="5206e-103">`#warning` kodunuzda belirli bir konumdan bir düzey bir uyarı üretir olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="5206e-103">`#warning` lets you generate a level one warning from a specific location in your code.</span></span> <span data-ttu-id="5206e-104">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="5206e-104">For example:</span></span>  
  
```csharp
#warning Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="5206e-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5206e-105">Remarks</span></span>  
 <span data-ttu-id="5206e-106">Yaygın kullanımı `#warning` koşullu yönergesinde değil.</span><span class="sxs-lookup"><span data-stu-id="5206e-106">A common use of `#warning` is in a conditional directive.</span></span> <span data-ttu-id="5206e-107">Kullanıcı tanımlı bir hata ile oluşturmak mümkündür [#error](../../../csharp/language-reference/preprocessor-directives/preprocessor-error.md).</span><span class="sxs-lookup"><span data-stu-id="5206e-107">It is also possible to generate a user-defined error with [#error](../../../csharp/language-reference/preprocessor-directives/preprocessor-error.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5206e-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="5206e-108">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5206e-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5206e-109">See Also</span></span>  
 [<span data-ttu-id="5206e-110">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="5206e-110">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="5206e-111">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="5206e-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="5206e-112">C# Ön İşlemci Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="5206e-112">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
