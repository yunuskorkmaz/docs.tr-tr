---
title: 'Nasıl yapılır: (Visual Basic) türetilmiş sınıf tarafından gizlenen bir değişkene erişme'
ms.date: 07/20/2015
helpviewer_keywords:
- qualification [Visual Basic], of element names
- base classes [Visual Basic], accessing elements
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declared elements [Visual Basic], referencing
- variables [Visual Basic], accessing hidden
ms.assetid: ae21a8ac-9cd4-4fba-a3ec-ecc4321ef93c
ms.openlocfilehash: a97a51d4570d87eaa873fb3152ad810f528dff46
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58832183"
---
# <a name="how-to-access-a-variable-hidden-by-a-derived-class-visual-basic"></a>Nasıl yapılır: (Visual Basic) türetilmiş sınıf tarafından gizlenen bir değişkene erişme
Kod türetilen bir sınıfta bir değişken eriştiğinde, derleyici en yakın erişilebilir sürüme, yani erişilebilir sürümü başvuru normalde az derivational adımlardan geriye dönük erişen sınıf çözümler. Değişken türetilmiş sınıf içinde tanımlanmış olması durumunda, kod normalde bu tanımı erişir.  
  
 Türetilmiş sınıf değişkeni gölgeleri temel sınıfında bir değişkeni, temel sınıftaki sürümün gizler. Ancak, kendisiyle uygun temel sınıf değişkenine erişebileceği `MyBase` anahtar sözcüğü.  
  
### <a name="to-access-a-base-class-variable-hidden-by-a-derived-class"></a>Türetilmiş sınıf tarafından gizlenen bir temel sınıf değişkene erişmek için  
  
-   Bir ifade veya atama ifadesi değişken adıyla önünde `MyBase` anahtar sözcüğü ve bir süre (`.`).  
  
     Derleyici, değişkenin temel sınıftaki sürümün başvuruyu çözümler.  
  
     Aşağıdaki örnek, devralma yoluyla gölgeleme gösterir. İki başvuru, gölgelendirme değişkeni erişen diğeri, gölgeleme atlar kolaylaştırır.  
  
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
 Gölgeli bir değişkenin istenmeyen bir sürüme başvuran riskini azaltmak için tam olarak gölgeli bir değişken tüm başvuruları kazanabilir. Gölgeleme, bir değişken aynı ada sahip birden fazla sürümünü tanıtır. Kod açıklaması değişken adıdır, derleyici başvurusu açığını giderir sürüm kod açıklaması konumunu ve uygun bir dize varlığını gibi faktörlere bağlıdır. Bu değişkeni yanlış sürümüne başvuran riskini artırabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bildirilmiş Öğelere Başvurular](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Visual Basic'de gölgeleme](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [Gölgeleme ve Geçersiz Kılma Arasındaki Farklar](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)
- [Nasıl yapılır: Değişkeninizle aynı ada sahip bir değişkeni gizleme](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [Nasıl yapılır: Devralınmış değişkeni gizleme](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)
- [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [Me, My, MyBase ve MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [Devralma Temelleri](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
