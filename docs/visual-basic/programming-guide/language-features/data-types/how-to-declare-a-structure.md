---
title: 'Nasıl yapılır: Bir Yapıyı Bildirme'
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], structures
- structure statements [Visual Basic]
- statements [Visual Basic], structure
- structures [Visual Basic], declaring
ms.assetid: d5e98381-eb81-47d4-af83-48cc534a2572
ms.openlocfilehash: 41d2d03064dea703909218de56feb863526c220b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350005"
---
# <a name="how-to-declare-a-structure-visual-basic"></a>Nasıl yapılır: Bir Yapıyı Bildirme (Visual Basic)
Yapı [ifadesiyle](../../../../visual-basic/language-reference/statements/structure-statement.md)bir yapı bildirimi başlar ve `End Structure` ifadesiyle sonlandırın. Bu iki deyim arasında en az bir *öğe*bildirmeniz gerekir. Öğeleri herhangi bir veri türünde olabilir, ancak en az bir veya paylaşılmayan olmayan bir değişken ya da paylaşılmayan olmayan bir olay olmalıdır.  
  
 Yapı bildiriminde yapı öğelerinden hiçbirini başlatamıyor. Bir yapı türünde olması için bir değişken bildirdiğinizde, değişkenine değerleri değişken aracılığıyla erişerek atayabilirsiniz.  
  
 Yapılar ve sınıflar arasındaki farklılıklarla ilgili bir tartışma için bkz. [yapılar ve sınıflar](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md).  
  
 Tanıtım amacıyla, bir çalışanın adını, telefon uzantısını ve maaşını izlemek istediğiniz bir durum düşünün. Bir yapı bunu tek bir değişkende yapmanıza olanak sağlar.  
  
### <a name="to-declare-a-structure"></a>Bir yapıyı bildirmek için  
  
1. Yapı için başlangıç ve bitiş deyimlerini oluşturun.  
  
     [Ortak](../../../../visual-basic/language-reference/modifiers/public.md), [korumalı](../../../../visual-basic/language-reference/modifiers/protected.md), [arkadaş](../../../../visual-basic/language-reference/modifiers/friend.md)veya [özel](../../../../visual-basic/language-reference/modifiers/private.md) anahtar sözcüğünü kullanarak bir yapının erişim düzeyini belirtebilir veya bunun `Public`varsayılana izin verebilirsiniz.  
  
    ```vb  
    Private Structure employee  
    End Structure  
    ```  
  
2. Yapının gövdesine öğe ekleyin.  
  
     Bir yapının en az bir öğesi olmalıdır. Her öğeyi bildirmeniz ve bunun için bir erişim düzeyi belirtmeniz gerekir. [Dim ifadesini](../../../../visual-basic/language-reference/statements/dim-statement.md) herhangi bir anahtar sözcük olmadan kullanırsanız, erişilebilirlik varsayılan olarak `Public`olur.  
  
    ```vb  
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
  
     Yukarıdaki örnekteki `salary` alanı `Private`, bu, kapsayan sınıftan bile yapının dışında erişilemeyen anlamına gelir. Ancak, `giveRaise` yordamı `Public`, bu nedenle yapının dışından çağrılabilir. Benzer şekilde, `salaryReviewTime` olayını yapının dışından da yükseltebilirsiniz.  
  
     Değişkenlere, `Sub` yordamlarına ve olaylara ek olarak, bir yapıda sabitler, `Function` yordamlar ve özellikler de tanımlayabilirsiniz. En az bir bağımsız değişken alması şartıyla, en az bir özelliği *varsayılan özellik*olarak belirleyebilirsiniz. Bir olayı, [paylaşılan](../../../../visual-basic/language-reference/modifiers/shared.md) bir`Sub` yordamıyla işleyebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: Visual Basic ' de varsayılan bir özellik bildirme ve çağırma](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md).  
  
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
