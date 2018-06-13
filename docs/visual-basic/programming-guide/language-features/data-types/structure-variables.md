---
title: Yapı Değişkenleri (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic], variables
- structures [Visual Basic], structure variables
- variables [Visual Basic], structure variables
- structure variables [Visual Basic]
ms.assetid: 156872f8-aabc-4454-8e2d-f2253c3c13c9
ms.openlocfilehash: 0dad7bdcac5428753e252f3b26ca0a127c293a7f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648505"
---
# <a name="structure-variables-visual-basic"></a>Yapı Değişkenleri (Visual Basic)
Bir yapı oluşturduktan sonra bu tür olarak yordamı ve modül düzeyi değişkenleri bildirebilirsiniz. Örneğin, bir bilgisayar sistemi ilgili bilgileri kaydeden bir yapı oluşturabilirsiniz. Aşağıdaki örnekte bu gösterir.  
  
```  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public purchaseDate As Date  
End Structure  
```  
  
 Bu tür değişkenler şimdi bildirebilirsiniz. Aşağıdaki bildirimi bu gösterilmektedir.  
  
```  
Dim mySystem, yourSystem As systemInfo  
```  
  
> [!NOTE]
>  Sınıfları ve modülleri, yapıları bildirilen kullanarak [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md) varsayılan olarak genel erişim. Özel olarak bir yapı düşünüyorsanız, bildirdiğiniz kullanarak emin olun [özel](../../../../visual-basic/language-reference/modifiers/private.md) anahtar sözcüğü.  
  
## <a name="access-to-structure-values"></a>Yapı değerleri erişimi  
 Atamak ve bir yapı değişkenin öğeleri değerleri almak için ayarlamak ve nesne özellikleri elde etmek için kullandığınız aynı sözdizimini kullanın. Üye erişimi işleci yerleştirin (`.`) arasında yapısı değişken adını ve öğe adı. Aşağıdaki örnek daha önce türü olarak bildirilen değişkenlerin öğeleri erişen `systemInfo`.  
  
```  
mySystem.cPU = "486"  
Dim tooOld As Boolean  
If yourSystem.purchaseDate < #1/1/1992# Then tooOld = True  
```  
  
## <a name="assigning-structure-variables"></a>Yapı değişkenleri atama  
 Her ikisi de aynı yapısı türde olduğunda, aynı zamanda bir değişken diğerine atayabilirsiniz. Bu diğer karşılık gelen öğe bir yapısının tüm öğeleri kopyalar. Aşağıdaki bildirimi bu gösterilmektedir.  
  
```  
yourSystem = mySystem  
```  
  
 Yapı öğesi bir başvuru türü gibi ise bir `String`, `Object`, veya dizi, verileri işaretçisine kopyalanır. Önceki örnekte, `systemInfo` önceki örnekte işaretçi kopyaladığınız sonra bir nesne değişkeni dahil `mySystem` için `yourSystem`, ve bir yapı nesnenin verilerine bir değişiklik erişildiğinde etkili olacaktır diğer yapısı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Başlangıç Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [Bileşik Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [Değer Türleri ve Başvuru Türleri](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Yapılar](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Veri Türü Sorunlarını Giderme](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Nasıl yapılır: Bir Yapıyı Bildirme](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [Yapılar ve Diğer Programlama Öğeleri](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)  
 [Yapılar ve Sınıflar](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)  
 [Structure Deyimi](../../../../visual-basic/language-reference/statements/structure-statement.md)
