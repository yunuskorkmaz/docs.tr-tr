---
title: 'Nasıl yapılır: Türetilmiş bir sınıf tarafından gizlenen bir değişkene erişme (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- qualification [Visual Basic], of element names
- base classes [Visual Basic], accessing elements
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declared elements [Visual Basic], referencing
- variables [Visual Basic], accessing hidden
ms.assetid: ae21a8ac-9cd4-4fba-a3ec-ecc4321ef93c
ms.openlocfilehash: 68f92142cdc435ebd82101eea83035e1d09dcf25
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630021"
---
# <a name="how-to-access-a-variable-hidden-by-a-derived-class-visual-basic"></a>Nasıl yapılır: Türetilmiş bir sınıf tarafından gizlenen bir değişkene erişme (Visual Basic)

Türetilmiş bir sınıftaki kod bir değişkene eriştiğinde, derleyici normal olarak en yakın erişilebilen sürüme (diğer bir deyişle, erişim sınıfından geri doğru olan erişilebilir sürüme) başvuruyu çözümler. Değişken türetilmiş sınıfta tanımlanmışsa, kod normalde bu tanıma erişir.

Türetilmiş sınıf değişkeni, temel sınıftaki bir değişkeni göltiği takdirde, temel sınıf sürümünü gizler. Ancak, `MyBase` anahtar sözcüğü ile niteleyerek temel sınıf değişkenine erişebilirsiniz.

### <a name="to-access-a-base-class-variable-hidden-by-a-derived-class"></a>Türetilmiş bir sınıf tarafından gizlenen bir taban sınıf değişkenine erişmek için

- Bir ifade veya atama deyiminde, değişken adından `MyBase` önce anahtar sözcüğü ve nokta (`.`) koyun.

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

    Önceki örnek, değişkeni `shadowString` temel sınıfta bildirir ve türetilmiş sınıfta gölgeleri. Türetilmiş sınıftaki `showStrings` yordamda, ad `shadowString` uygun olmadığında dizenin gölgeleme sürümü görüntülenir. Ardından, `shadowString` `MyBase` anahtar sözcüğü ile nitelendirilmeden gölgeli sürümü görüntüler.

## <a name="robust-programming"></a>Güçlü Programlama

Gölgelendirilmiş bir değişkenin istenmeyen bir sürümüne başvurma riskini azaltmak için, tüm başvuruları gölgelendirilmiş bir değişkene tamamen niteleyebilirsiniz. Gölgeleme aynı ada sahip bir değişkenin birden fazla sürümünü tanıtır. Bir kod açıklaması değişken adına başvurduğunda, derleyicinin başvuruyu çözümleyen sürüm, kod ifadesinin konumu ve uygun bir dizenin varlığı gibi faktörlere bağlıdır. Bu, değişkenin yanlış sürümüne başvurma riskini artırabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Bildirilmiş Öğelere Başvurular](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Visual Basic gölgeleme](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [Gölgeleme ve Geçersiz Kılma Arasındaki Farklar](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)
- [Nasıl yapılır: Değişkeninizle Aynı ada sahip bir değişkeni gizleyin](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [Nasıl yapılır: Devralınan bir değişkeni gizleme](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)
- [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [Me, My, MyBase ve MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [Devralma Temelleri](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
