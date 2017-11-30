---
title: "Nasıl yapılır: Türetilmiş Sınıf Tarafından Gizlenen Bir Değişkene Erişme (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- qualification [Visual Basic], of element names
- base classes [Visual Basic], accessing elements
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declared elements [Visual Basic], referencing
- variables [Visual Basic], accessing hidden
ms.assetid: ae21a8ac-9cd4-4fba-a3ec-ecc4321ef93c
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0f94e45fcb0a26b0d59789e101c37aceba219250
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [Bildirilmiş öğelere başvurular](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [Visual Basic'de gölgeleme](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)  
 [Gölgeleme ve geçersiz kılma arasındaki farklar](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)  
 [Nasıl yapılır: değişkeninizle aynı ada sahip bir değişkeni gizleme](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)  
 [Nasıl yapılır: devralınmış değişkeni gizleme](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)  
 [Gölgeleri](../../../../visual-basic/language-reference/modifiers/shadows.md)  
 [Geçersiz kılmaları](../../../../visual-basic/language-reference/modifiers/overrides.md)  
 [Me, My, MyBase ve MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [Devralma temelleri](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
