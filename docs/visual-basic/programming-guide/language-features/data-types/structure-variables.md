---
title: Yapı Değişkenleri
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic], variables
- structures [Visual Basic], structure variables
- variables [Visual Basic], structure variables
- structure variables [Visual Basic]
ms.assetid: 156872f8-aabc-4454-8e2d-f2253c3c13c9
ms.openlocfilehash: 16b6cdc5a849b50f6caa8b7963dac5c12d63cf3e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346300"
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
> Sınıflarda ve modüllerde, [Dim ifadesiyle](../../../../visual-basic/language-reference/statements/dim-statement.md) varsayılan olarak genel erişim için belirtilen yapılar. Bir yapıyı özel olarak düşünüyorsanız, [Private](../../../../visual-basic/language-reference/modifiers/private.md) anahtar sözcüğünü kullanarak bildirdiğinizden emin olun.

## <a name="access-to-structure-values"></a>Yapı değerlerine erişim

Bir yapı değişkeninin öğelerinden değer atamak ve almak için, bir nesne üzerinde özellikleri ayarlamak ve almak için kullandığınız söz dizimini kullanın. Üye erişim işlecini (`.`) yapı değişkeni adı ve öğe adı arasında yerleştirebilirsiniz. Aşağıdaki örnek, daha önce tür `systemInfo`olarak belirtilen değişkenlerin öğelerine erişir.

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

Bir yapı öğesi `String`, `Object`veya dizi gibi bir başvuru türü ise, verilerin işaretçisi kopyalanır. Önceki örnekte, `systemInfo` bir nesne değişkeni içeriyorsa, yukarıdaki örnek işaretçiyi `mySystem` `yourSystem`öğesine kopyalamalıdır ve bir yapı aracılığıyla nesne verilerinde yapılan bir değişiklik, diğer yapıyla erişildiğinde geçerli olur.

## <a name="see-also"></a>Ayrıca bkz.

- [Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Başlangıç Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [Bileşik Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [Değer Türleri ve Başvuru Türleri](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Yapılar](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Veri Türü Sorunlarını Giderme](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Nasıl yapılır: Bir Yapıyı Bildirme](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Yapılar ve Diğer Programlama Öğeleri](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)
- [Yapılar ve Sınıflar](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [Structure Deyimi](../../../../visual-basic/language-reference/statements/structure-statement.md)
