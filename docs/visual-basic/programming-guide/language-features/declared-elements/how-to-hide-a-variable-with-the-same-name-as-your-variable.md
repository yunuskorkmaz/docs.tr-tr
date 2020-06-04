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
ms.openlocfilehash: c1f4c2fbf339358be77e76468b1db94616bf04a2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84357238"
---
# <a name="how-to-hide-a-variable-with-the-same-name-as-your-variable-visual-basic"></a>Nasıl yapılır: Değişkeninizle Aynı Adı Taşıyan Bir Değişkeni Gizleme (Visual Basic)

Bir değişkeni, aynı ada sahip bir değişkenle yeniden tanımlayarak, bir değeri *gölgelendirerek* gizleyebilirsiniz. Gizlemek istediğiniz değişkeni iki şekilde gölgelendireseçebilirsiniz:

- **Kapsam üzerinden gölgeleme.** Onu, gizlemek istediğiniz değişkeni içeren bölgenin bir alt bölgesi içinde yeniden bildirerek kapsam aracılığıyla gölgelendirebilir.

- **Devralma yoluyla gölgeleme.** Gizlemek istediğiniz değişken sınıf düzeyinde tanımlıysa, türetilmiş bir sınıftaki [Shadows](../../../language-reference/modifiers/shadows.md) anahtar sözcüğüyle yeniden bildirerek devralma yoluyla gölge oluşturabilirsiniz.

## <a name="two-ways-to-hide-a-variable"></a>Bir değişkeni gizlemek için iki yol

#### <a name="to-hide-a-variable-by-shadowing-it-through-scope"></a>Bir değişkeni kapsam aracılığıyla gölgelendirerek gizlemek için

1. Gizlemek istediğiniz değişkeni tanımlayan bölgeyi belirleme ve Değişkeninizle birlikte yeniden tanımlanacak bir alt bölge belirleme.

    |Değişkenin bölgesi|Yeniden tanımlama için izin verilen alt bölge|
    |-----------------------|-------------------------------------------|
    |Modül|Modül içindeki bir sınıf|
    |Sınıf|Sınıf içindeki bir alt sınıf<br /><br /> Sınıf içindeki bir yordam|

    Bu yordam içindeki bir blok içindeki bir yordam değişkenini, örneğin bir `If` ... `End If` inşaat veya bir döngüde yeniden tanımlayamazsınız `For` .

2. Zaten yoksa alt bölge oluşturun.

3. Alt bölge içinde, gölgeleme değişkenini bildiren bir [Dim ekstresi](../../../language-reference/statements/dim-statement.md) yazın.

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

    Yukarıdaki örnek, değişkeni `num` hem modül düzeyinde hem de yordam düzeyinde (yordamda `show` ) bildirir. Yerel değişken, `num` içinde modül düzeyi değişkeni gölgeler `num` , bu `show` nedenle yerel değişken 2 olarak ayarlanır. Ancak, yordamda gölge için yerel bir değişken yoktur `num` `useModuleLevelNum` . Bu nedenle, `useModuleLevelNum` Modül düzeyi değişkeninin değerini 1 olarak ayarlar.

    `MsgBox`İçindeki çağrı, `show` modül adıyla niteleyerek gölgeleme mekanizmasını atlar `num` . Bu nedenle, yerel değişken yerine modül düzeyi değişkeni görüntüler.

#### <a name="to-hide-a-variable-by-shadowing-it-through-inheritance"></a>Bir değişkeni devralma yoluyla gölgelendirerek gizlemek için

1. Gizlemek istediğiniz değişkenin bir sınıfta ve sınıf düzeyinde (herhangi bir yordam dışında) olduğundan emin olun. Aksi takdirde, devralma aracılığıyla gölgelendiremezsiniz.

2. Değişkenin sınıfından türetilmiş bir sınıfı, zaten mevcut değilse tanımlayın.

3. Türetilmiş sınıfın içinde, `Dim` değişkeninizi bildiren bir ifade yazın. Bildirime [gölgeler](../../../language-reference/modifiers/shadows.md) anahtar sözcüğünü ekleyin.

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

    Önceki örnek, değişkeni `shadowString` temel sınıfta bildirir ve türetilmiş sınıfta gölgeleri. `showStrings`Türetilmiş sınıftaki yordamda, ad uygun olmadığında dizenin gölgeleme sürümü görüntülenir `shadowString` . Ardından, `shadowString` anahtar sözcüğü ile nitelendirilmeden gölgeli sürümü görüntüler `MyBase` .

## <a name="robust-programming"></a>Güçlü Programlama

Gölgeleme aynı ada sahip bir değişkenin birden fazla sürümünü tanıtır. Bir kod açıklaması değişken adına başvurduğunda, derleyicinin başvuruyu çözümleyen sürüm, kod ifadesinin konumu ve uygun bir dizenin varlığı gibi faktörlere bağlıdır. Bu, gölgelendirilmiş bir değişkenin istenmeyen bir sürümüne başvurma riskini artırabilir. Gölgelendirilmiş bir değişkene tüm başvuruları tam olarak niteleyerek bu riski düşürebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Bildirilmiş Öğelere Başvurular](references-to-declared-elements.md)
- [Visual Basic'de Gölgeleme](shadowing.md)
- [Gölgeleme ve Geçersiz Kılma Arasındaki Farklar](differences-between-shadowing-and-overriding.md)
- [Nasıl yapılır: Devralınmış Değişkeni Gizleme](how-to-hide-an-inherited-variable.md)
- [Nasıl yapılır: Türetilmiş Sınıf Tarafından Gizlenen Bir Değişkene Erişme](how-to-access-a-variable-hidden-by-a-derived-class.md)
- [Geçersiz Kılmalar](../../../language-reference/modifiers/overrides.md)
- [Me, My, MyBase ve MyClass](../../program-structure/me-my-mybase-and-myclass.md)
- [Devralma Temelleri](../objects-and-classes/inheritance-basics.md)
