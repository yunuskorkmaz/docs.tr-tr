---
title: Yapı Değişkenleri (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic], variables
- structures [Visual Basic], structure variables
- variables [Visual Basic], structure variables
- structure variables [Visual Basic]
ms.assetid: 156872f8-aabc-4454-8e2d-f2253c3c13c9
ms.openlocfilehash: f9cc6d0165b0eda8358d250c37910b1362473ab1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54640608"
---
# <a name="structure-variables-visual-basic"></a>Yapı Değişkenleri (Visual Basic)
Bir yapı oluşturulduktan sonra bu türü olarak yordam ve Modül düzeyinde değişkenleri bildirebilirsiniz. Örneğin, bir bilgisayar sistemi ilgili bilgileri kaydeden bir yapısı oluşturabilirsiniz. Aşağıdaki örnekte bu gösterir.  
  
```  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public purchaseDate As Date  
End Structure  
```  
  
 Artık, değişkenlerini türü bildirebilirsiniz. Aşağıdaki bildirimi bunu göstermektedir.  
  
```  
Dim mySystem, yourSystem As systemInfo  
```  
  
> [!NOTE]
>  Yapıları sınıflar ve modüller, kullanılarak bildirilen [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md) varsayılan genel erişim için. Bir yapı özel olmasını istiyorsanız'ı kullanarak bildirdiğinizden emin olun [özel](../../../../visual-basic/language-reference/modifiers/private.md) anahtar sözcüğü.  
  
## <a name="access-to-structure-values"></a>Yapı değerlerine erişim  
 Atamak ve bir yapı değişkenin öğeleri değerleri almak için bir nesne üzerinde özelliklerini alma ve ayarlamak için kullandığınız aynı sözdizimini kullanın. Üye erişimi işleci yerleştirin (`.`) değişkenin adını yapı arasındaki öğe adı. Aşağıdaki örnekte önceden türü olarak bildirilmiş değişkenlerin öğeleri erişen `systemInfo`.  
  
```  
mySystem.cPU = "486"  
Dim tooOld As Boolean  
If yourSystem.purchaseDate < #1/1/1992# Then tooOld = True  
```  
  
## <a name="assigning-structure-variables"></a>Yapı değişkenleri atama  
 Her ikisi de aynı yapı türü olduğunda, ayrıca bir değişken diğerine atayabilirsiniz. Bu, bir yapının tüm öğeleri karşılık gelen öğelerle diğer kopyalar. Aşağıdaki bildirimi bunu göstermektedir.  
  
```  
yourSystem = mySystem  
```  
  
 Yapı öğesi bir başvuru türü olduğu gibi bir `String`, `Object`, ya da veri işaretçisine diziye kopyalanır. Önceki örnekte, `systemInfo` sonra kopyalanan işaretçisinden önceki örnekte bir nesne değişkeninin dahil `mySystem` için `yourSystem`, ve bir değişiklik nesne verilerinin bir yapısı üzerinden erişildiğinde yürürlükte olur diğer yapısı.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Başlangıç Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [Bileşik Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [Değer Türleri ve Başvuru Türleri](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Yapılar](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Veri Türü Sorunlarını Giderme](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Nasıl yapılır: Yapıyı Bildirme](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Yapılar ve Diğer Programlama Öğeleri](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)
- [Yapılar ve Sınıflar](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [Structure Deyimi](../../../../visual-basic/language-reference/statements/structure-statement.md)
