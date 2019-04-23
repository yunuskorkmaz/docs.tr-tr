---
title: 'Nasıl yapılır: (Visual Basic) bir yapıyı bildirme'
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], structures
- structure statements [Visual Basic]
- statements [Visual Basic], structure
- structures [Visual Basic], declaring
ms.assetid: d5e98381-eb81-47d4-af83-48cc534a2572
ms.openlocfilehash: a52daddaa8701ccca9bd9b5b4a48535a6ffa19ed
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59343564"
---
# <a name="how-to-declare-a-structure-visual-basic"></a>Nasıl yapılır: (Visual Basic) bir yapıyı bildirme
Yapı bildirimi ile başlayan [Structure deyimi](../../../../visual-basic/language-reference/statements/structure-statement.md), ve ile sona `End Structure` deyimi. Bu iki deyimden arasında en az bir bildirmelisiniz *öğesi*. Öğeleri herhangi bir veri türünde olabilir, ancak en az bir paylaşılmayan bir değişken veya paylaşılmayan, özel olmayan bir olay olması gerekir.  
  
 Yapı öğeleri yapısı bildiriminde başlatılamıyor. Bir yapı türünde olması için bir değişken bildirdiğinizde, değerler öğelerine değişken üzerinden erişerek atayın.  
  
 Yapılar ve sınıflar arasındaki farklar için bkz [yapılar ve sınıflar](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md).  
  
 Tanıtım amacıyla, bir çalışanın adı, dahili telefon numarası ve maaş izlemek istediğiniz bir durum düşünün. Bir yapı, tek bir değişkende bunu yapmanızı sağlar.  
  
### <a name="to-declare-a-structure"></a>Bir yapıyı bildirmek için  
  
1. Başlangıç ve bitiş ifadeleri yapısının oluşturun.  
  
     Yapısı kullanarak bir erişim düzeyini belirleyebileceğiniz [genel](../../../../visual-basic/language-reference/modifiers/public.md), [korumalı](../../../../visual-basic/language-reference/modifiers/protected.md), [arkadaş](../../../../visual-basic/language-reference/modifiers/friend.md), veya [özel](../../../../visual-basic/language-reference/modifiers/private.md) anahtar sözcük veya izin, Varsayılan olarak `Public`.  
  
    ```  
    Private Structure employee  
    End Structure  
    ```  
  
2. Öğeleri yapısı gövdesi ekleyin.  
  
     Bir yapı en az bir öğe içermelidir. Her öğe bildirmek ve bunun için bir erişim düzeyi belirtmeniz gerekir. Kullanırsanız [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md) erişilebilirlik herhangi bir anahtar, varsayılan olarak `Public`.  
  
    ```  
    Private Structure employee  
        Public givenName As String  
        Public familyName As String  
        Public phoneExtension As Long  
        Private salary As Decimal  
        Public Sub giveRaise(raise As Double)  
            salary *= raise  
        End Sub  
        Public Event salaryReviewTime()  
    End Structure  
    ```  
  
     `salary` Önceki örnekte alandır `Private`, hatta içeren sınıftan yapısı dışında erişilemez durumda anlamına gelir. Ancak, `giveRaise` oluşan bir yordamdır `Public`, bu nedenle, gelen yapısı çağrılabilir. Benzer şekilde, yükseltebilirsiniz `salaryReviewTime` olaydan yapısı dışında.  
  
     Değişkenleri yanı sıra `Sub` yordamları ve olayları, sabitleri, ayrıca tanımlayabilirsiniz `Function` yordamlar ve bir yapı özellikleri. En fazla bir özellik olarak belirlediğiniz *varsayılan özellik*, sağlanan en az bir bağımsız değişken alır. Bir olayla işleyebilir bir [paylaşılan](../../../../visual-basic/language-reference/modifiers/shared.md) `Sub` yordamı. Daha fazla bilgi için [nasıl yapılır: Bildirme ve Visual Basic'te bir varsayılan özellik çağırma](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Başlangıç Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [Bileşik Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [Değer Türleri ve Başvuru Türleri](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Yapılar](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Veri Türü Sorunlarını Giderme](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Yapı Değişkenleri](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)
- [Yapılar ve Diğer Programlama Öğeleri](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)
- [Yapılar ve Sınıflar](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [User-Defined Veri Türü](../../../../visual-basic/language-reference/data-types/user-defined-data-type.md)
