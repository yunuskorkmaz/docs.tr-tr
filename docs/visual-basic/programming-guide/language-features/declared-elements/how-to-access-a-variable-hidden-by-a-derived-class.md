---
title: 'Nasıl yapılır: Türetilmiş Sınıf Tarafından Gizlenen Bir Değişkene Erişme (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- qualification [Visual Basic], of element names
- base classes [Visual Basic], accessing elements
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declared elements [Visual Basic], referencing
- variables [Visual Basic], accessing hidden
ms.assetid: ae21a8ac-9cd4-4fba-a3ec-ecc4321ef93c
ms.openlocfilehash: 8dd59dff5b8123331237db905432bbb4e94d62ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-access-a-variable-hidden-by-a-derived-class-visual-basic"></a>Nasıl yapılır: Türetilmiş Sınıf Tarafından Gizlenen Bir Değişkene Erişme (Visual Basic)
Türetilmiş bir sınıf kodda bir değişken eriştiğinde derleyici sürümüne başvuru en yakın erişilebilir, diğer bir deyişle, erişilebilir sürümü en az derivational adımları geriye dönük erişilirken sınıfından normalde çözümler. Değişkeni türetilmiş sınıfında tanımlanmışsa kodu tanımın normal olarak erişir.  
  
 Türetilmiş sınıf değişkeni temel sınıfı bir değişkende shadows, temel sınıf sürüm gizler. İle niteleme tarafından temel sınıf değişkenine ancak erişebilir `MyBase` anahtar sözcüğü.  
  
### <a name="to-access-a-base-class-variable-hidden-by-a-derived-class"></a>Türetilmiş sınıf tarafından gizlenen bir temel sınıf değişkene erişmek için  
  
-   Bir deyim veya atama deyimi değişken adından `MyBase` anahtar sözcüğü ve bir süre (`.`).  
  
     Derleyici değişkenin temel sınıf sürümüne başvuru çözümler.  
  
     Aşağıdaki örnek, devralma yoluyla gölgeleme gösterilmektedir. İki başvuru, gölgeleme değişkeni erişen diğeri gölgeleme atlayan kolaylaştırır.  
  
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
 Gölgeli bir değişken istenmeyen bir sürümüne başvuran riskini düşürmek için tüm başvurular gölgeli bir değişkene tam olarak nitelemek. Gölgeleme aynı ada sahip bir değişken birden fazla sürümünü getirmektedir. Kod açıklaması değişken adına başvurduğunda, derleyici Başvurusu Güvenlik giderir sürüm kod açıklaması konumunu ve uygun bir dize varlığını gibi etkenlere bağlıdır. Bu değişkeni yanlış sürüme başvuran riskini artırabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bildirilmiş Öğelere Başvurular](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [Visual Basic'de gölgeleme](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)  
 [Gölgeleme ve Geçersiz Kılma Arasındaki Farklar](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)  
 [Nasıl yapılır: Değişkeninizle Aynı Adı Taşıyan Bir Değişkeni Gizleme](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)  
 [Nasıl yapılır: Devralınmış Değişkeni Gizleme](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)  
 [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)  
 [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)  
 [Me, My, MyBase ve MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [Devralma Temelleri](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
