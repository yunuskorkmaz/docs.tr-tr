---
title: "Nasıl yapılır: Değişkeninizle Aynı Adı Taşıyan Bir Değişkeni Gizleme (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: af031f3ef134b2a509922e6ada28aa5b2b80d641
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-hide-a-variable-with-the-same-name-as-your-variable-visual-basic"></a>Nasıl yapılır: Değişkeninizle Aynı Adı Taşıyan Bir Değişkeni Gizleme (Visual Basic)
Bir değişkenin gizleyebilirsiniz *gölgeleme* , diğer bir deyişle, aynı ada sahip bir değişken tanımlayarak tarafından. İki yolla gizlemek istediğiniz değişkeni gölge:  
  
-   **Kapsam yoluyla gölgeleme.** Bu kapsam yoluyla gizlemek istediğiniz değişkenini içeren bölgenin alt içinde redeclaring tarafından gölge.  
  
-   **Devralma yoluyla gölgeleme.** Gizlemek istediğiniz değişken sınıf düzeyinde tanımlanmışsa, bu devralma yoluyla ile redeclaring gölge [gölgeleri](../../../../visual-basic/language-reference/modifiers/shadows.md) türetilmiş bir sınıf bir anahtar sözcük.  
  
## <a name="two-ways-to-hide-a-variable"></a>Bir değişkeni gizleme için iki yol  
  
#### <a name="to-hide-a-variable-by-shadowing-it-through-scope"></a>Kapsam yoluyla gölgeleme tarafından bir değişkeni gizleme  
  
1.  Gizlemek istediğiniz değişken tanımlama bölge belirlemek ve bir alt bölgeli değişkeni ile yeniden tanımlamak üzere belirleyin.  
  
    |Değişkenin bölge|Bunu yeniden tanımlama için izin verilen alt|  
    |-----------------------|-------------------------------------------|  
    |Modül|Modüldeki bir sınıfı|  
    |örneği|İçindeki bir alt sınıfı<br /><br /> Bir yordam içinde sınıfı|  
  
     Bu yordamı blokta yordamı değişkeninde örneğin içinde tanımlanamaz bir `If`... `End If` yapım veya `For` döngü.  
  
2.  Zaten yoksa, alt bölge oluşturun.  
  
3.  Alt bölge içinde yazma bir [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md) gölgeleme değişken bildirme.  
  
     Alt bölge içinde kod değişken adına başvurduğunda derleyici gölgeleme değişkeni referansı çözümler.  
  
     Aşağıdaki örnek, kapsam olarak gölgeleme atlayan bir başvuru gölgeleme gösterilmektedir.  
  
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
  
     Önceki örnekte değişken bildirir `num` hem modül düzeyi ve yordam düzeyinde (yordamda `show`). Yerel değişken `num` modül düzeyi değişkeni shadows `num` içinde `show`, yerel değişken 2'ye ayarlanır. Ancak, hiçbir yerel bir gölge değişkene yoktur `num` içinde `useModuleLevelNum` yordamı. Bu nedenle, `useModuleLevelNum` modül düzeyi değişkenin değerini 1 olarak ayarlar.  
  
     `MsgBox` İçinde arama `show` niteleme tarafından gölgeleme mekanizması atlar `num` modül adına sahip. Bu nedenle, yerel değişken yerine modül düzeyi değişkeni görüntüler.  
  
#### <a name="to-hide-a-variable-by-shadowing-it-through-inheritance"></a>Devralma yoluyla gölgeleme tarafından bir değişkeni gizleme  
  
1.  Gizlemek istediğiniz değişkeni bir sınıf ve sınıf düzeyinde (dışında herhangi bir yordam) bildirildiğinden emin olun. Aksi takdirde devralma yoluyla gölge olamaz.  
  
2.  Bir zaten yoksa, değişkenin sınıfından türetilen bir sınıfı tanımlar.  
  
3.  Türetilmiş sınıf içinde yazma bir `Dim` deyimi, değişken bildirme. Dahil [gölgeleri](../../../../visual-basic/language-reference/modifiers/shadows.md) bildiriminde anahtar sözcüğü.  
  
     Türetilmiş sınıf kodda değişken adına başvurduğunda, derleyici, değişkeni referansı çözümler.  
  
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
 Gölgeleme aynı ada sahip bir değişken birden fazla sürümünü getirmektedir. Kod açıklaması değişken adına başvurduğunda, derleyici Başvurusu Güvenlik giderir sürüm kod açıklaması konumunu ve uygun bir dize varlığını gibi etkenlere bağlıdır. Bu gölgeli bir değişken istenmeyen bir sürümüne başvuran riskini artırabilir. Bu riski tam olarak gölgeli bir değişken yapılan tüm başvuruları niteleme tarafından düşürebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bildirilmiş öğelere başvurular](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [Visual Basic'de gölgeleme](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)  
 [Gölgeleme ve geçersiz kılma arasındaki farklar](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)  
 [Nasıl yapılır: devralınmış değişkeni gizleme](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)  
 [Nasıl yapılır: türetilmiş sınıf tarafından gizlenen bir değişkene erişme](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)  
 [Geçersiz kılmaları](../../../../visual-basic/language-reference/modifiers/overrides.md)  
 [Me, My, MyBase ve MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [Devralma temelleri](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
