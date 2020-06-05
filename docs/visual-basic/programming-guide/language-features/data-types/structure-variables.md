---
title: Yapı Değişkenleri
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic], variables
- structures [Visual Basic], structure variables
- variables [Visual Basic], structure variables
- structure variables [Visual Basic]
ms.assetid: 156872f8-aabc-4454-8e2d-f2253c3c13c9
ms.openlocfilehash: 270e8ca26185e4a68def3b95f4ce6ab4c57a629c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393591"
---
# <a name="structure-variables-visual-basic"></a>Yapı Değişkenleri (Visual Basic)

Bir yapı oluşturduktan sonra, bu tür olarak yordam düzeyi ve modül düzeyi değişkenler bildirebilirsiniz. Örneğin, bir bilgisayar sistemiyle ilgili bilgileri kaydeden bir yapı oluşturabilirsiniz. Aşağıdaki örnek bunu gösterir.

```vb
Public Structure systemInfo
    Public cPU As String
    Public memory As Long
    Public purchaseDate As Date
End Structure
```

Artık bu tür değişkenleri bildirebilirsiniz. Aşağıdaki bildirimde bu gösterilmektedir.

```vb
Dim mySystem, yourSystem As systemInfo
```

> [!NOTE]
> Sınıflarda ve modüllerde, [Dim ifadesiyle](../../../language-reference/statements/dim-statement.md) varsayılan olarak genel erişim için belirtilen yapılar. Bir yapıyı özel olarak düşünüyorsanız, [Private](../../../language-reference/modifiers/private.md) anahtar sözcüğünü kullanarak bildirdiğinizden emin olun.

## <a name="access-to-structure-values"></a>Yapı değerlerine erişim

Bir yapı değişkeninin öğelerinden değer atamak ve almak için, bir nesne üzerinde özellikleri ayarlamak ve almak için kullandığınız söz dizimini kullanın. Üye erişim işlecini ( `.` ) yapı değişkeni adı ve öğe adı arasında yerleştirebilirsiniz. Aşağıdaki örnek, daha önce tür olarak belirtilen değişkenlerin öğelerine erişir `systemInfo` .

```vb
mySystem.cPU = "486"
Dim tooOld As Boolean
If yourSystem.purchaseDate < #1/1/1992# Then tooOld = True
```

## <a name="assigning-structure-variables"></a>Yapı değişkenleri atama

Aynı yapı türünde her ikisi de varsa, başka bir değişken de atayabilirsiniz. Bu, bir yapının tüm öğelerini diğerinin karşılık gelen öğelerine kopyalar. Aşağıdaki bildirimde bu gösterilmektedir.

```vb
yourSystem = mySystem
```

Bir yapı öğesi,, veya dizisi gibi bir başvuru türü ise `String` , `Object` verilerin işaretçisi kopyalanır. Önceki örnekte, `systemInfo` bir nesne değişkeni içeriyorsa, yukarıdaki örnek işaretçisini `mySystem` ' dan ' a kopyalamalıdır `yourSystem` ve bir yapı aracılığıyla nesne verilerinde yapılan bir değişiklik, diğer yapıyla erişildiğinde geçerli olur.

## <a name="see-also"></a>Ayrıca bkz.

- [Veri türleri](index.md)
- [Başlangıç Veri Türleri](elementary-data-types.md)
- [Bileşik Veri Türleri](composite-data-types.md)
- [Değer Türleri ve Başvuru Türleri](value-types-and-reference-types.md)
- [Yapılar](structures.md)
- [Veri Türü Sorunlarını Giderme](troubleshooting-data-types.md)
- [Nasıl yapılır: Yapıyı Bildirme](how-to-declare-a-structure.md)
- [Yapılar ve Diğer Programlama Öğeleri](structures-and-other-programming-elements.md)
- [Yapılar ve Sınıflar](structures-and-classes.md)
- [Structure Yapısı](../../../language-reference/statements/structure-statement.md)
