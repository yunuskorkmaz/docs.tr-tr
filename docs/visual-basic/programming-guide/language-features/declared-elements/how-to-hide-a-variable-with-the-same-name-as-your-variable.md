---
title: 'Nasıl yapılır: Değişkeninizle Aynı Adı Taşıyan Bir Değişkeni Gizleme'
ms.date: 07/20/2015
helpviewer_keywords:
- qualification [Visual Basic], of element names
- declarations [Visual Basic], elements
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declaration statements [Visual Basic], declared elements
- declaring elements [Visual Basic]
- referencing declared elements [Visual Basic]
- declared elements [Visual Basic], referencing
- declared elements [Visual Basic], about declared elements
ms.assetid: e39c0752-f19f-4d2e-a453-00df1b5fc7ee
ms.openlocfilehash: 0915adbbabb778b1bdd3b6b30e56725a7e74867c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345362"
---
# <a name="how-to-hide-a-variable-with-the-same-name-as-your-variable-visual-basic"></a>Nasıl yapılır: Değişkeninizle Aynı Adı Taşıyan Bir Değişkeni Gizleme (Visual Basic)

Bir değişkeni, aynı ada sahip bir değişkenle yeniden tanımlayarak, bir değeri *gölgelendirerek* gizleyebilirsiniz. Gizlemek istediğiniz değişkeni iki şekilde gölgelendireseçebilirsiniz:

- **Kapsam üzerinden gölgeleme.** Onu, gizlemek istediğiniz değişkeni içeren bölgenin bir alt bölgesi içinde yeniden bildirerek kapsam aracılığıyla gölgelendirebilir.

- **Devralma yoluyla gölgeleme.** Gizlemek istediğiniz değişken sınıf düzeyinde tanımlıysa, türetilmiş bir sınıftaki [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) anahtar sözcüğüyle yeniden bildirerek devralma yoluyla gölge oluşturabilirsiniz.

## <a name="two-ways-to-hide-a-variable"></a>Bir değişkeni gizlemek için iki yol

#### <a name="to-hide-a-variable-by-shadowing-it-through-scope"></a>Bir değişkeni kapsam aracılığıyla gölgelendirerek gizlemek için

1. Gizlemek istediğiniz değişkeni tanımlayan bölgeyi belirleme ve Değişkeninizle birlikte yeniden tanımlanacak bir alt bölge belirleme.

    |Değişkenin bölgesi|Yeniden tanımlama için izin verilen alt bölge|
    |-----------------------|-------------------------------------------|
    |Modül|Modül içindeki bir sınıf|
    |Sınıf|Sınıf içindeki bir alt sınıf<br /><br /> Sınıf içindeki bir yordam|

    Bu yordam içindeki bir blok içindeki bir yordam değişkenini, örneğin bir `If`...`End If` oluşturma veya `For` döngüsünde yeniden tanımlayamazsınız.

2. Zaten yoksa alt bölge oluşturun.

3. Alt bölge içinde, gölgeleme değişkenini bildiren bir [Dim ekstresi](../../../../visual-basic/language-reference/statements/dim-statement.md) yazın.

    Alt bölge içindeki kod değişken adına başvurduğunda, derleyici, gölgeleme değişkeninin başvurusunu çözümler.

    Aşağıdaki örnekte, kapsam aracılığıyla gölgeleme ve ayrıca, gölgelendirmeyi atlayan bir başvuru gösterilmektedir.

    ```vb
    Module shadowByScope
        ' The following statement declares num as a module-level variable.
        Public num As Integer
        Sub show()
            ' The following statement declares num as a local variable.
            Dim num As Integer
            ' The following statement sets the value of the local variable.
            num = 2
            ' The following statement displays the module-level variable.
            MsgBox(CStr(shadowByScope.num))
        End Sub
        Sub useModuleLevelNum()
            ' The following statement sets the value of the module-level variable.
            num = 1
            show()
        End Sub
    End Module
    ```

    Yukarıdaki örnek, değişken `num` hem modül düzeyinde hem de yordam düzeyinde (yordamda `show`) bildirir. Yerel değişken, `show`içinde `num` modül düzeyi değişkeninin gölge `num`, bu nedenle yerel değişken 2 olarak ayarlanır. Ancak, `useModuleLevelNum` yordamda gölge `num` için yerel değişken yoktur. Bu nedenle, `useModuleLevelNum` modül düzeyi değişkeninin değerini 1 olarak ayarlar.

    `show` içindeki `MsgBox` çağrısı, modül adıyla `num` niteleyerek gölgeleme mekanizmasını atlar. Bu nedenle, yerel değişken yerine modül düzeyi değişkeni görüntüler.

#### <a name="to-hide-a-variable-by-shadowing-it-through-inheritance"></a>Bir değişkeni devralma yoluyla gölgelendirerek gizlemek için

1. Gizlemek istediğiniz değişkenin bir sınıfta ve sınıf düzeyinde (herhangi bir yordam dışında) olduğundan emin olun. Aksi takdirde, devralma aracılığıyla gölgelendiremezsiniz.

2. Değişkenin sınıfından türetilmiş bir sınıfı, zaten mevcut değilse tanımlayın.

3. Türetilmiş sınıfın içinde, değişkeninizi bildiren bir `Dim` ifadesini yazın. Bildirime [gölgeler](../../../../visual-basic/language-reference/modifiers/shadows.md) anahtar sözcüğünü ekleyin.

    Türetilmiş sınıftaki kod, değişken adına başvurduğunda, derleyici değişkeninizin başvurusunu çözer.

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

Gölgeleme aynı ada sahip bir değişkenin birden fazla sürümünü tanıtır. Bir kod açıklaması değişken adına başvurduğunda, derleyicinin başvuruyu çözümleyen sürüm, kod ifadesinin konumu ve uygun bir dizenin varlığı gibi faktörlere bağlıdır. Bu, gölgelendirilmiş bir değişkenin istenmeyen bir sürümüne başvurma riskini artırabilir. Gölgelendirilmiş bir değişkene tüm başvuruları tam olarak niteleyerek bu riski düşürebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Bildirilmiş Öğelere Başvurular](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Visual Basic gölgeleme](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [Gölgeleme ve Geçersiz Kılma Arasındaki Farklar](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)
- [Nasıl yapılır: Devralınmış Değişkeni Gizleme](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)
- [Nasıl yapılır: Türetilmiş Sınıf Tarafından Gizlenen Bir Değişkene Erişme](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)
- [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [Me, My, MyBase ve MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [Devralma Temelleri](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
