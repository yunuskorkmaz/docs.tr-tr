---
title: 'Nasıl yapılır: Türetilmiş Sınıf Tarafından Gizlenen Bir Değişkene Erişme'
ms.date: 07/20/2015
helpviewer_keywords:
- qualification [Visual Basic], of element names
- base classes [Visual Basic], accessing elements
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declared elements [Visual Basic], referencing
- variables [Visual Basic], accessing hidden
ms.assetid: ae21a8ac-9cd4-4fba-a3ec-ecc4321ef93c
ms.openlocfilehash: 276cb1411c66e1f7205507a1b1053cc8642c7cb0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345401"
---
# <a name="how-to-access-a-variable-hidden-by-a-derived-class-visual-basic"></a>Nasıl yapılır: Türetilmiş Sınıf Tarafından Gizlenen Bir Değişkene Erişme (Visual Basic)

Türetilmiş bir sınıftaki kod bir değişkene eriştiğinde, derleyici normal olarak en yakın erişilebilen sürüme (diğer bir deyişle, erişim sınıfından geri doğru olan erişilebilir sürüme) başvuruyu çözümler. Değişken türetilmiş sınıfta tanımlanmışsa, kod normalde bu tanıma erişir.

Türetilmiş sınıf değişkeni, temel sınıftaki bir değişkeni göltiği takdirde, temel sınıf sürümünü gizler. Ancak, `MyBase` anahtar sözcüğüyle niteleyerek temel sınıf değişkenine erişebilirsiniz.

### <a name="to-access-a-base-class-variable-hidden-by-a-derived-class"></a>Türetilmiş bir sınıf tarafından gizlenen bir taban sınıf değişkenine erişmek için

- Bir ifade veya atama deyiminde, değişken adının önüne `MyBase` anahtar sözcüğünü ve nokta (`.`) koyun.

    Derleyici, değişkenin temel sınıf sürümüne başvuruyu çözer.

    Aşağıdaki örnek, devralma yoluyla gölgelendirmeyi gösterir. Biri, gölgeleme değişkenine erişen diğeri de gölgelendirmeyi atlayan iki başvuru yapar.

    ```vb
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

    Yukarıdaki örnek, `shadowString` değişkenini temel sınıfta bildirir ve türetilmiş sınıfta gölgeleri. Türetilmiş sınıftaki yordam `showStrings`, ad `shadowString` nitelenmediği zaman, dizenin gölgeleme sürümünü görüntüler. Daha sonra, `shadowString` `MyBase` anahtar sözcüğüyle nitelendirildiğinden gölgeli sürümü görüntüler.

## <a name="robust-programming"></a>Güçlü Programlama

Gölgelendirilmiş bir değişkenin istenmeyen bir sürümüne başvurma riskini azaltmak için, tüm başvuruları gölgelendirilmiş bir değişkene tamamen niteleyebilirsiniz. Gölgeleme aynı ada sahip bir değişkenin birden fazla sürümünü tanıtır. Bir kod açıklaması değişken adına başvurduğunda, derleyicinin başvuruyu çözümleyen sürüm, kod ifadesinin konumu ve uygun bir dizenin varlığı gibi faktörlere bağlıdır. Bu, değişkenin yanlış sürümüne başvurma riskini artırabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Bildirilmiş Öğelere Başvurular](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Visual Basic gölgeleme](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [Gölgeleme ve Geçersiz Kılma Arasındaki Farklar](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)
- [Nasıl yapılır: Değişkeninizle Aynı Adı Taşıyan Bir Değişkeni Gizleme](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [Nasıl yapılır: Devralınmış Değişkeni Gizleme](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)
- [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [Me, My, MyBase ve MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [Devralma Temelleri](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
