---
description: 'Hakkında daha fazla bilgi edinin: #Disable ve #Enable yönergeleri (Visual Basic)'
title: Yönergeleri etkinleştirme ve devre dışı bırakma
ms.date: 01/28/2021
helpviewer_keywords:
- directives, enable
- directives, disable
- disable directive
ms.openlocfilehash: d600cc959639a3f70bca5678fbc81aae0806c9cc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797269"
---
# <a name="disable-and-enable-directives-visual-basic"></a><span data-ttu-id="31c30-103">#Disable ve #Enable yönergeleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31c30-103">#Disable and #Enable directives (Visual Basic)</span></span>

<span data-ttu-id="31c30-104">`#Disable`Ve `#Enable` yönergeleri Visual Basic kaynak kodu derleyici yönergelerinden.</span><span class="sxs-lookup"><span data-stu-id="31c30-104">The `#Disable` and `#Enable` directives are Visual Basic source code compiler directives.</span></span> <span data-ttu-id="31c30-105">Kod bölgeleri için belirli uyarıları devre dışı bırakmak ve yeniden etkinleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="31c30-105">They are used to disable and re-enable specific warnings for regions of code.</span></span>

```vb
' Suppress warning about no awaits in this method.
#Disable Warning BC42356
    Async Function TestAsync() As Task
        Console.WriteLine("testing")
    End Function
#Enable Warning BC42356
```

<span data-ttu-id="31c30-106">Ayrıca, virgülle ayrılmış bir uyarı kodları listesini devre dışı bırakabilir ve etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="31c30-106">You can also disable and enable a comma-separated list of warning codes.</span></span>

## <a name="see-also"></a><span data-ttu-id="31c30-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="31c30-107">See also</span></span>

- [<span data-ttu-id="31c30-108">Visual Basic dil başvurusu</span><span class="sxs-lookup"><span data-stu-id="31c30-108">Visual Basic Language Reference</span></span>](../index.md)
- [<span data-ttu-id="31c30-109">Kod Analizi uyarılarını gösterme</span><span class="sxs-lookup"><span data-stu-id="31c30-109">How to suppress code analysis warnings</span></span>](../../../fundamentals/code-analysis/suppress-warnings.md)
