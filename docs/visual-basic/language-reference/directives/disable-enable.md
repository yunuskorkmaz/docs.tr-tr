---
title: Yönergeleri etkinleştirme ve devre dışı bırakma
ms.date: 01/28/2021
helpviewer_keywords:
- directives, enable
- directives, disable
- disable directive
ms.openlocfilehash: 3104b25c903465f3a650304f477b25a74591c8ba
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2021
ms.locfileid: "99217231"
---
# <a name="disable-and-enable-directives-visual-basic"></a><span data-ttu-id="037fc-102">#Disable ve #Enable yönergeleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="037fc-102">#Disable and #Enable directives (Visual Basic)</span></span>

<span data-ttu-id="037fc-103">`#Disable`Ve `#Enable` yönergeleri Visual Basic kaynak kodu derleyici yönergelerinden.</span><span class="sxs-lookup"><span data-stu-id="037fc-103">The `#Disable` and `#Enable` directives are Visual Basic source code compiler directives.</span></span> <span data-ttu-id="037fc-104">Kod bölgeleri için belirli uyarıları devre dışı bırakmak ve yeniden etkinleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="037fc-104">They are used to disable and re-enable specific warnings for regions of code.</span></span>

```vb
' Suppress warning about no awaits in this method.
#Disable Warning BC42356
    Async Function TestAsync() As Task
        Console.WriteLine("testing")
    End Function
#Enable Warning BC42356
```

<span data-ttu-id="037fc-105">Ayrıca, virgülle ayrılmış bir uyarı kodları listesini devre dışı bırakabilir ve etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="037fc-105">You can also disable and enable a comma-separated list of warning codes.</span></span>

## <a name="see-also"></a><span data-ttu-id="037fc-106">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="037fc-106">See also</span></span>

- [<span data-ttu-id="037fc-107">Visual Basic dil başvurusu</span><span class="sxs-lookup"><span data-stu-id="037fc-107">Visual Basic Language Reference</span></span>](../index.md)
- [<span data-ttu-id="037fc-108">Kod Analizi uyarılarını gösterme</span><span class="sxs-lookup"><span data-stu-id="037fc-108">How to suppress code analysis warnings</span></span>](../../../fundamentals/code-analysis/suppress-warnings.md)
