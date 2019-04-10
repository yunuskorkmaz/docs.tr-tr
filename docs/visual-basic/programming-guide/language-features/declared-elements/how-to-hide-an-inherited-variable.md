---
title: 'Nasıl yapılır: (Visual Basic) devralınmış değişkeni gizleme'
ms.date: 07/20/2015
helpviewer_keywords:
- qualification [Visual Basic], of element names
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declaration statements [Visual Basic], declared elements
- referencing declared elements [Visual Basic]
- declared elements [Visual Basic], referencing
- declared elements [Visual Basic], about declared elements
- variables [Visual Basic], hiding inherited
ms.assetid: 765728d9-7351-4a30-999d-b5f34f024412
ms.openlocfilehash: ee147ecd00b88b538ace32844c42ac9c5022b2ef
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59331708"
---
# <a name="how-to-hide-an-inherited-variable-visual-basic"></a>Nasıl yapılır: (Visual Basic) devralınmış değişkeni gizleme
Türetilmiş bir sınıf kendi temel sınıfının tüm tanımları devralır. Bir öğe temel sınıf aynı adı kullanarak bir değişkeni tanımlamak istiyorsanız, gizleyebilirsiniz, veya *gölge*, türetilen sınıfta Değişkeninizi tanımladığınızda, temel sınıf öğesi. Bunu yaparsanız, türetilmiş sınıftaki kod açıkça gölgeleme mekanizması atlar sürece Değişkeninizi erişir.  
  
 Devralınmış değişkeni gizleme isteyebileceğiniz diğer bir neden, temel sınıf düzeltme karşı korunmasını sağlamaktır. Temel sınıf devralma öğe değiştiren bir değişiklik uygulanabilir. Böyle bir durumda `Shadows` değiştiricisi değişkeninize, temel sınıf öğenin yerine çözülmesi türetilmiş sınıf başvurularından zorlar.  
  
### <a name="to-hide-an-inherited-variable"></a>Devralınmış değişkeni gizleme  
  
1. Gizlemek istediğiniz değişken sınıf düzeyinde (dışında herhangi bir yordam) bildirildiğinden emin olun. Aksi takdirde gizlemek gerekmez.  
  
2. Türetilmiş sınıf içinde yazma bir [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md) , değişken bildirme. Aynı ada, devralınmış değişkeni kullanın.  
  
3. Dahil [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) bildirimindeki anahtar sözcüğü.  
  
     Türetilmiş sınıftaki kod değişken adıdır, derleyici Değişkeninizi başvuruyu çözümler.  
  
     Aşağıdaki örnek, devralınan bir değişken gölgeleme gösterir.  
  
    ```  
    Public Class shadowBaseClass  
        Public shadowString As String = "This is the base class string."  
    End Class  
    Public Class shadowDerivedClass  
        Inherits shadowBaseClass  
        Public Shadows shadowString As String = "This is the derived class string."  
        Public Sub showStrings()  
            Dim s As String = "Unqualified shadowString: " & shadowString &  
                vbCrLf & "MyBase.shadowString: " & MyBase.shadowString  
            MsgBox(s)  
        End Sub  
    End Class  
    ```  
  
     Yukarıdaki örnekte değişkeni bildirir `shadowString` temel sınıf ve türetilen sınıfta gölgeliyor. Yordamı `showStrings` türetilmiş bir sınıf içindeki dize gölgeleme sürümünü görüntüler, ad `shadowString` yetkili değil. Ardından gölgeli sürüm görüntüler, `shadowString` ile tam olduğundan `MyBase` anahtar sözcüğü.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Gölgeleme, bir değişken aynı ada sahip birden fazla sürümünü tanıtır. Kod açıklaması değişken adıdır, derleyici başvurusu açığını giderir sürüm kod açıklaması konumunu ve uygun bir dize varlığını gibi faktörlere bağlıdır. Bu gölgeli bir değişkenin istenmeyen bir sürüme başvuran riskini artırabilir. Bu riski tam olarak gölgeli bir değişken tüm başvurularını uygun tarafından düşürebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bildirilmiş Öğelere Başvurular](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Visual Basic'de Gölgeleme](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [Gölgeleme ve Geçersiz Kılma Arasındaki Farklar](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)
- [Nasıl yapılır: Değişkeninizle Aynı Adı Taşıyan Bir Değişkeni Gizleme](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [Nasıl yapılır: Türetilmiş Sınıf Tarafından Gizlenen Bir Değişkene Erişme](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)
- [Geçersiz Kılmalar](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [Me, My, MyBase ve MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [Devralma Temelleri](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
