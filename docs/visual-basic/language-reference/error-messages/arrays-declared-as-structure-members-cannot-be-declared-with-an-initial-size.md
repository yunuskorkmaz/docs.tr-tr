---
title: Yapı üyeleri olarak bildirilen diziler için başlangıç boyutu bildirilemez
ms.date: 07/20/2015
f1_keywords:
- vbc31043
- bc31043
helpviewer_keywords:
- BC31043
ms.assetid: 5bd90c71-1b78-444b-91e1-4789451ef085
ms.openlocfilehash: 83342b780c0fa7c3a2e0a6797b80ef788117ae92
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/10/2019
ms.locfileid: "72250148"
---
# <a name="arrays-declared-as-structure-members-cannot-be-declared-with-an-initial-size"></a>Yapı üyeleri olarak bildirilen diziler için başlangıç boyutu bildirilemez

Yapıdaki bir dizi, başlangıç boyutuyla birlikte bildirilmiştir. Herhangi bir yapı öğesini başlatamıyor ve bir dizi boyutunun bildirilmesi, tek bir başlatma biçimidir.

**Hata kimliği:** BC31043

## <a name="example"></a>Örnek

Aşağıdaki örnek BC31043 oluşturur:

```vb
Structure DemoStruct
    Public demoArray(9) As Integer
End Structure
```

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

1. Yapıdaki diziyi dinamik (başlangıç boyutu olmadan) olarak tanımlayın.

2. Belirli bir dizi boyutuna ihtiyacınız varsa, kodunuz çalışırken bir [ReDim ifadesiyle](../statements/redim-statement.md) dinamik bir diziyi yeniden Dimension uygulayabilirsiniz. Aşağıdaki örnek şunu göstermektedir:
  
    ```vb
    Structure DemoStruct
        Public demoArray() As Integer
    End Structure
    Sub UseStruct()
        Dim struct As DemoStruct  
        ReDim struct.demoArray(9)
        Struct.demoArray(2) = 777
    End Sub  
    ```
  
## <a name="see-also"></a>Ayrıca bkz.

- [Diziler](../../programming-guide/language-features/arrays/index.md)
- [Nasıl yapılır: Bir Yapıyı Bildirme](../../programming-guide/language-features/data-types/how-to-declare-a-structure.md)
