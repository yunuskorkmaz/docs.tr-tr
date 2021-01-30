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
# <a name="disable-and-enable-directives-visual-basic"></a>#Disable ve #Enable yönergeleri (Visual Basic)

`#Disable`Ve `#Enable` yönergeleri Visual Basic kaynak kodu derleyici yönergelerinden. Kod bölgeleri için belirli uyarıları devre dışı bırakmak ve yeniden etkinleştirmek için kullanılır.

```vb
' Suppress warning about no awaits in this method.
#Disable Warning BC42356
    Async Function TestAsync() As Task
        Console.WriteLine("testing")
    End Function
#Enable Warning BC42356
```

Ayrıca, virgülle ayrılmış bir uyarı kodları listesini devre dışı bırakabilir ve etkinleştirebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic dil başvurusu](../index.md)
- [Kod Analizi uyarılarını gösterme](../../../fundamentals/code-analysis/suppress-warnings.md)
