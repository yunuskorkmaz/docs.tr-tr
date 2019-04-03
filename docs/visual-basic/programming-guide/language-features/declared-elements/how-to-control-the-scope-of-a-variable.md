---
title: 'Nasıl yapılır: (Visual Basic) bir değişkenin kapsamını denetleme'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], scope
- declared elements [Visual Basic], scope
- visibility [Visual Basic], declared elements
- variables [Visual Basic], visibility
- scope [Visual Basic], declared elements
- scope [Visual Basic], variables
- scope [Visual Basic], Visual Basic
- declared elements [Visual Basic], visibility
- visibility [Visual Basic], variables
ms.assetid: 44b7f62a-cb5c-4d50-bce9-60ae68f87072
ms.openlocfilehash: ef7957a991718112fe01c4fa3a85f29b9226abd3
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58818729"
---
# <a name="how-to-control-the-scope-of-a-variable-visual-basic"></a>Nasıl yapılır: (Visual Basic) bir değişkenin kapsamını denetleme
Normalde, içinde bir değişkeni olduğunu *kapsam*, ya da, bildirdiğiniz, bölge, başvuru için görünür. Bazı durumlarda, değişken 's *erişim düzeyi* kapsamını etkileyebilir.  
  
 Daha fazla bilgi için [Visual Basic'de kapsam](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).  
  
## <a name="scope-at-block-or-procedure-level"></a>Kapsamda blok veya yordam düzeyi  
  
#### <a name="to-make-a-variable-visible-only-within-a-block"></a>Bir değişken yalnızca bir blok içinde görünür hale getirmek için  
  
-   Bir yerde [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md) başlatma ve bildirim deyimleri, bloğun başlangıcını arasında örneğin sonlandırma arasında değişken için `For` ve `Next` bilgilerinin bir `For` döngü.  
  
     Yalnızca değişken bloğu içinde başvurabilirsiniz.  
  
#### <a name="to-make-a-variable-visible-only-within-a-procedure"></a>Bir değişken yalnızca bir yordam içinde görünür hale getirmek için  
  
-   Bir yerde `Dim` yordam içinde ancak herhangi bir blok dışındaki değişken bildirimi (gibi bir `With`... `End With` blok).  
  
     İçinde yordamda bulunan herhangi bir bloğu içinde dahil olmak üzere bu yordamı yalnızca değişkene başvurabilirsiniz.  
  
## <a name="scope-at-module-or-namespace-level"></a>Modül veya Namespace düzeyinde kapsamı  
 Kolaylık sağlamak adına, tek ifadeli *modül düzeyi* modülleri, sınıflar ve yapılar için eşit oranda geçerlidir. Modül düzeyi değişkeni erişim düzeyini kapsamı belirler. Modül, sınıf veya yapı içeren ad uzayı kapsam da etkiler.  
  
#### <a name="to-make-a-variable-visible-throughout-a-module-class-or-structure"></a>Bir değişken bir modül, sınıf veya yapı içinde görünür hale getirmek için  
  
1.  Bir yerde `Dim` modülü, sınıf veya yapı içinde ancak her türlü yordam dışındaki değişken bildirimi.  
  
2.  Dahil [özel](../../../../visual-basic/language-reference/modifiers/private.md) anahtar sözcüğünü `Dim` deyimi.  
  
3.  Modül, sınıf veya yapı içinde herhangi bir yere değiştirebilir, ancak değişkeninden başvurabilirsiniz dışı.  
  
#### <a name="to-make-a-variable-visible-throughout-a-namespace"></a>Bir değişken bir isim uzayı boyunca görünür hale getirmek için  
  
1.  Bir yerde `Dim` modülü, sınıf veya yapı içinde ancak her türlü yordam dışındaki değişken bildirimi.  
  
2.  Dahil [arkadaş](../../../../visual-basic/language-reference/modifiers/friend.md) veya [genel](../../../../visual-basic/language-reference/modifiers/public.md) anahtar sözcüğünü `Dim` deyimi.  
  
3.  Her yerden değişkene başvurabilirsiniz modül, sınıf veya yapı içeren ad alanı içinde.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, Modül düzeyinde bir değişkeni bildirir ve kod modülündeki görünürlüğü sınırlar.  
  
```  
Module demonstrateScope  
    Private strMsg As String  
    Sub initializePrivateVariable()  
        strMsg = "This variable cannot be used outside this module."  
    End Sub  
    Sub usePrivateVariable()  
        MsgBox(strMsg)  
    End Sub  
End Module  
```  
  
 Önceki örnekte, tüm yordamları modülde tanımlanan `demonstrateScope` başvurabilir `String` değişkeni `strMsg`. Zaman `usePrivateVariable` yordamı çağrılır, string değişkeni içeriğini görüntüler `strMsg` iletişim kutusunda.  
  
 Önceki örnekte, dize değişkeni için aşağıdaki değişikliği ile `strMsg` kod bildiriminden ad alanındaki herhangi bir ifade.  
  
```  
Public strMsg As String  
```  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Dar bir değişkenin kapsamını, yanlışlıkla aynı ada sahip başka bir değişken yerine başvuruda için sahip olduğunuz kesintilerinden. Başvuru eşleşen sorunlarını en aza indirebilirsiniz.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Kötü amaçlı kod hatalı yapabileceğiniz küçük olasılığını daha dar bir değişkenin kapsamını, bunu kullanın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic'de kapsam](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [Visual Basic'de ömür](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [Visual Basic'de erişim düzeyleri](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Değişkenler](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [Değişken Bildirimi](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Dim Deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md)
