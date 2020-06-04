---
title: 'Nasıl yapılır: Devralınmış Değişkeni Gizleme'
ms.date: 07/20/2015
helpviewer_keywords:
- qualification [Visual Basic], of element names
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declaration statements [Visual Basic], declared elements
- referencing declared elements [Visual Basic]
- declared elements [Visual Basic], referencing
- declared elements [Visual Basic], about declared elements
- variables [Visual Basic], hiding inherited
ms.assetid: 765728d9-7351-4a30-999d-b5f34f024412
ms.openlocfilehash: f49bba0497f9f4f2774b01284c815bba9aaed119
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84357276"
---
# <a name="how-to-hide-an-inherited-variable-visual-basic"></a>Nasıl yapılır: Devralınmış Değişkeni Gizleme (Visual Basic)

Türetilmiş bir sınıf, temel sınıfının tüm tanımlarını devralır. Temel sınıfın bir öğesiyle aynı adı kullanarak bir değişken tanımlamak istiyorsanız, türetilmiş sınıfta değişkeninizi tanımlarken bu temel sınıf öğesini gizleyebilir veya *gölgelendirebilir*. Bunu yaparsanız, bu türetilmiş sınıftaki kod, gölgeleme mekanizmasını açıkça atladıkça değişkeninizin erişimine erişir.

Devralınan bir değişkeni gizlemek isteyebileceğiniz diğer bir neden de temel sınıf düzeltmesine karşı koruma sağlar. Temel sınıf, devraldığınız öğeyi değiştiren bir değişikliği olumsuz etkileyebilir. Bu durumda, `Shadows` değiştirici türetilmiş sınıftan başvuruları, temel sınıf öğesi yerine, değişkeninizden çözümlenecek şekilde zorlar.

## <a name="to-hide-an-inherited-variable"></a>Devralınan bir değişkeni gizlemek için

1. Gizlemek istediğiniz değişkenin sınıf düzeyinde (herhangi bir yordam dışında) bildirilmesine dikkat edin. Aksi takdirde, bunu gizlemeniz gerekmez.
  
2. Türetilmiş sınıfınız içinde, değişkeninizi bildiren bir [Dim ekstresi](../../../language-reference/statements/dim-statement.md) yazın. Devralınan değişkenle aynı adı kullanın.

3. Bildirime [gölgeler](../../../language-reference/modifiers/shadows.md) anahtar sözcüğünü ekleyin.

     Türetilmiş sınıftaki kod, değişken adına başvurduğunda, derleyici değişkeninizin başvurusunu çözer.

     Aşağıdaki örnek, devralınan bir değişkenin gölgelendirdiğini gösterir:
  
    ```vb  
    Public Class ShadowBaseClass  
        Public shadowString As String = "This is the base class string."  
    End Class  
    Public Class ShadowDerivedClass  
        Inherits ShadowBaseClass  
        Public Shadows shadowString As String = "This is the derived class string."  
        Public Sub ShowStrings()  
            Dim s As String = $"Unqualified shadowString: {shadowString}{vbCrLf}MyBase.shadowString: {MyBase.shadowString}"
            MsgBox(s)  
        End Sub  
    End Class  
    ```  
  
     Önceki örnek, değişkeni `shadowString` temel sınıfta bildirir ve türetilmiş sınıfta gölgeleri. `ShowStrings`Türetilmiş sınıftaki yordamda, ad uygun olmadığında dizenin gölgeleme sürümü görüntülenir `shadowString` . Ardından, `shadowString` anahtar sözcüğü ile nitelendirilmeden gölgeli sürümü görüntüler `MyBase` .  
  
## <a name="robust-programming"></a>Güçlü programlama

Gölgeleme aynı ada sahip bir değişkenin birden fazla sürümünü tanıtır. Bir kod açıklaması değişken adına başvurduğunda, derleyicinin başvuruyu çözümleyen sürüm, kod ifadesinin konumu ve uygun bir dizenin varlığı gibi faktörlere bağlıdır. Bu, gölgelendirilmiş bir değişkenin istenmeyen bir sürümüne başvurma riskini artırabilir. Gölgelendirilmiş bir değişkene tüm başvuruları tam olarak niteleyerek bu riski düşürebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Bildirilmiş Öğelere Başvurular](references-to-declared-elements.md)
- [Visual Basic'de Gölgeleme](shadowing.md)
- [Gölgeleme ve Geçersiz Kılma Arasındaki Farklar](differences-between-shadowing-and-overriding.md)
- [Nasıl yapılır: Değişkeninizle Aynı Adı Taşıyan Bir Değişkeni Gizleme](how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [Nasıl yapılır: Türetilmiş Sınıf Tarafından Gizlenen Bir Değişkene Erişme](how-to-access-a-variable-hidden-by-a-derived-class.md)
- [Geçersiz Kılmalar](../../../language-reference/modifiers/overrides.md)
- [Me, My, MyBase ve MyClass](../../program-structure/me-my-mybase-and-myclass.md)
- [Devralma Temelleri](../objects-and-classes/inheritance-basics.md)
