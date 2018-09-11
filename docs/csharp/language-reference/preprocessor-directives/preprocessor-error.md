---
title: '#hata (C# Başvurusu)'
ms.date: 07/20/2015
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive [C#]'
ms.assetid: f2a7f3af-4cf9-4111-b369-70204d24b26b
ms.openlocfilehash: ed43c1f85142ec6c54e44db5e3b0b7de3ef36bb8
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44259892"
---
# <a name="error-c-reference"></a><span data-ttu-id="1e59f-102">#error (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="1e59f-102">#error (C# Reference)</span></span>
<span data-ttu-id="1e59f-103">`#error` oluşturmanıza olanak sağlar. bir [CS1029](../compiler-messages/cs1029.md) kodunuzda belirli bir konumdan kullanıcı tanımlı hata.</span><span class="sxs-lookup"><span data-stu-id="1e59f-103">`#error` lets you generate a [CS1029](../compiler-messages/cs1029.md) user-defined error from a specific location in your code.</span></span> <span data-ttu-id="1e59f-104">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="1e59f-104">For example:</span></span>  
  
```csharp
#error Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="1e59f-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1e59f-105">Remarks</span></span>  
 <span data-ttu-id="1e59f-106">Yaygın `#error` bir koşullu yönergesiyse.</span><span class="sxs-lookup"><span data-stu-id="1e59f-106">A common use of `#error` is in a conditional directive.</span></span>  
  
 <span data-ttu-id="1e59f-107">Kullanıcı tanımlı bir uyarı ile oluşturmak mümkündür [#warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md).</span><span class="sxs-lookup"><span data-stu-id="1e59f-107">It is also possible to generate a user-defined warning with [#warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e59f-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="1e59f-108">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1e59f-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1e59f-109">See Also</span></span>

- [<span data-ttu-id="1e59f-110">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="1e59f-110">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="1e59f-111">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="1e59f-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="1e59f-112">C# Ön İşlemci Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="1e59f-112">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
