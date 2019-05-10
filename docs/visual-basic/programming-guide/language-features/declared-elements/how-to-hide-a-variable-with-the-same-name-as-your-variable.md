---
title: 'Nasıl yapılır: Değişkeninizin (Visual Basic) aynı ada sahip bir değişkeni gizleme'
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
ms.openlocfilehash: 3230dac924e9c22231494bfc8b81cd74e356bca3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64610311"
---
# <a name="how-to-hide-a-variable-with-the-same-name-as-your-variable-visual-basic"></a>Nasıl yapılır: Değişkeninizin (Visual Basic) aynı ada sahip bir değişkeni gizleme
Bir değişken gizleyebilirsiniz *gölgeleme* , diğer bir deyişle, aynı ada sahip bir değişken tanımlayarak tarafından. İki yolla gizlemek istediğiniz değişkeni gölge:  
  
- **Kapsam yoluyla gölgeleme.** Bu kapsam yoluyla bir öğe alt bölgesini gizlemek istediğiniz değişkeni içeren bir bölge içinde redeclaring tarafından gölge.  
  
- **Devralma üzerinden gölgeleme.** Gizlemek istediğiniz değişken sınıf düzeyinde tanımlanmışsa, bu devralma yoluyla birlikte redeclaring gölge [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) anahtar sözcüğü türetilmiş bir sınıf içinde.  
  
## <a name="two-ways-to-hide-a-variable"></a>Bir değişkeni gizleme için iki yol  
  
#### <a name="to-hide-a-variable-by-shadowing-it-through-scope"></a>Bir değişken kapsam yoluyla gölgeleme tarafından gizlemek için  
  
1. Gizlemek istediğiniz değişken tanımlama bölgeyi belirlemeye ve burada, değişkenle tanımlanacak bir öğe alt bölgesini belirler.  
  
    |Değişkenin bölge|Bunu yeniden tanımlama için izin verilen öğe alt bölgesini|  
    |-----------------------|-------------------------------------------|  
    |Modül|Modüldeki bir sınıfı|  
    |örneği|Sınıf içindeki bir alt sınıfı<br /><br /> Bir yordam içinde sınıfı|  
  
     Bu yordamdaki bir blok içinde bir yordam değişken Örneğin içinde tanımlanamaz bir `If`... `End If` oluşturma veya `For` döngü.  
  
2. Zaten yoksa, öğe alt bölgesini oluşturun.  
  
3. Öğe alt bölgesini içinde yazma bir [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md) gölgeleme değişken bildirme.  
  
     Öğe alt bölgesini içinde kod değişkenin adı başvurduğunda, derleyicinin gölgeleme değişkenine başvuru çözümler.  
  
     Aşağıdaki örnek, kapsam yanı sıra gölgeleme atlar bir başvuru gölgeleme gösterir.  
  
    ```  
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
  
     Yukarıdaki örnekte değişkeni bildirir `num` Modül düzeyinde ve yordamı düzeyinde (yordamda `show`). Yerel değişken `num` Modül düzeyinde bir değişkene gölgeleri `num` içinde `show`, yerel değişken 2'ye ayarlanır. Ancak, hiçbir gölge yerel bir değişkene yoktur `num` içinde `useModuleLevelNum` yordamı. Bu nedenle, `useModuleLevelNum` Modül düzeyinde değişkeninin değeri 1'e ayarlar.  
  
     `MsgBox` İçinde çağrı `show` sağladığı gölgeleme mekanizması atlar `num` modül adı ile. Bu nedenle, yerel değişken yerine Modül düzeyinde değişkeni görüntüler.  
  
#### <a name="to-hide-a-variable-by-shadowing-it-through-inheritance"></a>Bir değişken devralma yoluyla gölgeleme tarafından gizlemek için  
  
1. Gizlemek istediğiniz değişkeni, bir sınıf ve sınıf düzeyinde (dışında herhangi bir yordam) bildirildiğinden emin olun. Aksi takdirde, devralma yoluyla gölgeleyemez.  
  
2. Henüz mevcut değilse, değişkenin sınıfından türetilen bir sınıf tanımlar.  
  
3. Türetilmiş sınıf içinde yazma bir `Dim` deyimi, değişken bildirme. Dahil [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) bildirimindeki anahtar sözcüğü.  
  
     Türetilmiş sınıftaki kod değişken adıdır, derleyici Değişkeninizi başvuruyu çözümler.  
  
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
 Gölgeleme, bir değişken aynı ada sahip birden fazla sürümünü tanıtır. Kod açıklaması değişken adıdır, derleyici başvurusu açığını giderir sürüm kod açıklaması konumunu ve uygun bir dize varlığını gibi faktörlere bağlıdır. Bu gölgeli bir değişkenin istenmeyen bir sürüme başvuran riskini artırabilir. Bu riski tam olarak gölgeli bir değişken tüm başvurularını uygun tarafından düşürebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bildirilmiş Öğelere Başvurular](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Visual Basic'de gölgeleme](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [Gölgeleme ve Geçersiz Kılma Arasındaki Farklar](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)
- [Nasıl yapılır: Devralınmış değişkeni gizleme](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)
- [Nasıl yapılır: Türetilmiş sınıf tarafından gizlenen bir değişkene erişme](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)
- [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [Me, My, MyBase ve MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [Devralma Temelleri](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
