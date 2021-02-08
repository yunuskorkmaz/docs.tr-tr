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
