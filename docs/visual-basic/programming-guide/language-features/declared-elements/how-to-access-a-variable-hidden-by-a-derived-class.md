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
ms.openlocfilehash: c5ff802a0f6e081acd00d7cdfab4a8296b4daad9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392863"
---
# <a name="how-to-access-a-variable-hidden-by-a-derived-class-visual-basic"></a>Nasıl yapılır: Türetilmiş Sınıf Tarafından Gizlenen Bir Değişkene Erişme (Visual Basic)

Türetilmiş bir sınıftaki kod bir değişkene eriştiğinde, derleyici normal olarak en yakın erişilebilen sürüme (diğer bir deyişle, erişim sınıfından geri doğru olan erişilebilir sürüme) başvuruyu çözümler. Değişken türetilmiş sınıfta tanımlanmışsa, kod normalde bu tanıma erişir.

Türetilmiş sınıf değişkeni, temel sınıftaki bir değişkeni göltiği takdirde, temel sınıf sürümünü gizler. Ancak, anahtar sözcüğü ile niteleyerek temel sınıf değişkenine erişebilirsiniz `MyBase` .

### <a name="to-access-a-base-class-variable-hidden-by-a-derived-class"></a>Türetilmiş bir sınıf tarafından gizlenen bir taban sınıf değişkenine erişmek için

- Bir ifade veya atama deyiminde, değişken adından önce `MyBase` anahtar sözcüğü ve nokta ( `.` ) koyun.

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

    Önceki örnek, değişkeni `shadowString` temel sınıfta bildirir ve türetilmiş sınıfta gölgeleri. `showStrings`Türetilmiş sınıftaki yordamda, ad uygun olmadığında dizenin gölgeleme sürümü görüntülenir `shadowString` . Ardından, `shadowString` anahtar sözcüğü ile nitelendirilmeden gölgeli sürümü görüntüler `MyBase` .

## <a name="robust-programming"></a>Güçlü Programlama

Gölgelendirilmiş bir değişkenin istenmeyen bir sürümüne başvurma riskini azaltmak için, tüm başvuruları gölgelendirilmiş bir değişkene tamamen niteleyebilirsiniz. Gölgeleme aynı ada sahip bir değişkenin birden fazla sürümünü tanıtır. Bir kod açıklaması değişken adına başvurduğunda, derleyicinin başvuruyu çözümleyen sürüm, kod ifadesinin konumu ve uygun bir dizenin varlığı gibi faktörlere bağlıdır. Bu, değişkenin yanlış sürümüne başvurma riskini artırabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Bildirilmiş Öğelere Başvurular](references-to-declared-elements.md)
- [Visual Basic'de Gölgeleme](shadowing.md)
- [Gölgeleme ve Geçersiz Kılma Arasındaki Farklar](differences-between-shadowing-and-overriding.md)
- [Nasıl yapılır: Değişkeninizle Aynı Adı Taşıyan Bir Değişkeni Gizleme](how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [Nasıl yapılır: Devralınmış Değişkeni Gizleme](how-to-hide-an-inherited-variable.md)
- [Shadows](../../../language-reference/modifiers/shadows.md)
- [Geçersiz Kılmalar](../../../language-reference/modifiers/overrides.md)
- [Me, My, MyBase ve MyClass](../../program-structure/me-my-mybase-and-myclass.md)
- [Devralma Temelleri](../objects-and-classes/inheritance-basics.md)
