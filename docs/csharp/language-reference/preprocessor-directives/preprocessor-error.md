---
title: '#hata (C# Başvurusu)'
ms.date: 07/20/2015
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive [C#]'
ms.assetid: f2a7f3af-4cf9-4111-b369-70204d24b26b
ms.openlocfilehash: 9ea4c24dcc3c0a4d39499bee5900cb9c6cc768c9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33269405"
---
# <a name="error-c-reference"></a><span data-ttu-id="9df9f-102">#error (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="9df9f-102">#error (C# Reference)</span></span>
<span data-ttu-id="9df9f-103">`#error` belirli bir konumdan, kodunuzda bir hata oluştur olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="9df9f-103">`#error` lets you generate an error from a specific location in your code.</span></span> <span data-ttu-id="9df9f-104">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="9df9f-104">For example:</span></span>  
  
```csharp
#error Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="9df9f-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9df9f-105">Remarks</span></span>  
 <span data-ttu-id="9df9f-106">Yaygın kullanımı `#error` koşullu yönergesinde değil.</span><span class="sxs-lookup"><span data-stu-id="9df9f-106">A common use of `#error` is in a conditional directive.</span></span>  
  
 <span data-ttu-id="9df9f-107">Kullanıcı tanımlı bir uyarıyla oluşturmak mümkündür [#warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md).</span><span class="sxs-lookup"><span data-stu-id="9df9f-107">It is also possible to generate a user-defined warning with [#warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9df9f-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="9df9f-108">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9df9f-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9df9f-109">See Also</span></span>  
 [<span data-ttu-id="9df9f-110">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="9df9f-110">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="9df9f-111">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="9df9f-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="9df9f-112">C# Ön İşlemci Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="9df9f-112">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
