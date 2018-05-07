---
title: 'Nasıl yapılır: Devralınmış Değişkeni Gizleme (Visual Basic)'
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
ms.openlocfilehash: c59fdd8c6c6d2444b8d687c78c61f4e0d4bf9a52
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-hide-an-inherited-variable-visual-basic"></a>Nasıl yapılır: Devralınmış Değişkeni Gizleme (Visual Basic)
Türetilmiş bir sınıf kendi temel sınıfının tüm tanımları devralır. Bir temel sınıf öğesi olarak aynı adı taşıyan bir değişkeni tanımlamak istiyorsanız, gizleyebilirsiniz, veya *gölge*, türetilen sınıfta değişkeniniz tanımladığınızda, temel sınıf öğesi. Bunu yaparsanız, türetilmiş sınıf kodda açıkça gölgeleme mekanizması atlar sürece değişkeniniz erişir.  
  
 Başka bir nedenle devralınmış değişkeni gizleme isteyebilirsiniz, temel sınıf düzeltme karşı korumaktır. Taban sınıf devralma öğesi olarak değiştiren bir değişiklik uygulanabilir. Bu durumda, `Shadows` değiştiricisi değişkeniniz için temel sınıf öğesine yerine çözülmesi türetilmiş sınıf başvurularından zorlar.  
  
### <a name="to-hide-an-inherited-variable"></a>Devralınmış değişkeni gizleme  
  
1.  Gizlemek istediğiniz değişkeni (dışında herhangi bir yordam) Sınıf düzeyinde bildirildiğinden emin olun. Aksi takdirde gizleme gerekmez.  
  
2.  Türetilmiş sınıf içinde yazma bir [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md) , değişken bildirme. Aynı adı, devralınmış değişkeni kullanın.  
  
3.  Dahil [gölgeleri](../../../../visual-basic/language-reference/modifiers/shadows.md) bildiriminde anahtar sözcüğü.  
  
     Türetilmiş sınıf kodda değişken adına başvurduğunda, derleyici, değişkeni referansı çözümler.  
  
     Aşağıdaki örnek devralınmış değişkeni gölgeleme gösterilmektedir.  
  
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
  
     Önceki örnekte değişken bildirir `shadowString` temel sınıf ve türetilen sınıfta shadows. Yordamı `showStrings` türetilen sınıfta dize gölgeleme sürümünü görüntüler zaman adı `shadowString` yetkili değil. Ardından gölgeli sürümünü görüntüler zaman `shadowString` ile nitelenmiş `MyBase` anahtar sözcüğü.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Gölgeleme aynı ada sahip bir değişken birden fazla sürümünü getirmektedir. Kod açıklaması değişken adına başvurduğunda, derleyici Başvurusu Güvenlik giderir sürüm kod açıklaması konumunu ve uygun bir dize varlığını gibi etkenlere bağlıdır. Bu gölgeli bir değişken istenmeyen bir sürümüne başvuran riskini artırabilir. Bu riski tam olarak gölgeli bir değişken yapılan tüm başvuruları niteleme tarafından düşürebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bildirilmiş Öğelere Başvurular](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [Visual Basic'de gölgeleme](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)  
 [Gölgeleme ve Geçersiz Kılma Arasındaki Farklar](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)  
 [Nasıl yapılır: Değişkeninizle Aynı Adı Taşıyan Bir Değişkeni Gizleme](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)  
 [Nasıl yapılır: Türetilmiş Sınıf Tarafından Gizlenen Bir Değişkene Erişme](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)  
 [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)  
 [Me, My, MyBase ve MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [Devralma Temelleri](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
