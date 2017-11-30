---
title: "Nasıl yapılır: Bir Değişkenin Kapsamını Denetleme (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7284d344e3bf0fdd0f900f2a820d6c8db4a4bf74
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-control-the-scope-of-a-variable-visual-basic"></a>Nasıl yapılır: Bir Değişkenin Kapsamını Denetleme (Visual Basic)
Bir değişken olarak normalde *kapsam*, veya içinde bildirdiğiniz, bölge boyunca, başvuru için görünür. Bazı durumlarda, değişkeni 's *erişim düzeyine* kapsamını etkileyebilir.  
  
 Daha fazla bilgi için bkz: [Visual Basic'de kapsam](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).  
  
## <a name="scope-at-block-or-procedure-level"></a>Blok veya yordam düzeyinde kapsamı  
  
#### <a name="to-make-a-variable-visible-only-within-a-block"></a>Bir değişken yalnızca bir bloğu içinde görünür hale getirmek için  
  
-   Yer [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md) başlatmak ve bu bloğunun bildirim deyimleri arasında örneğin sonlandırma arasında bir değişken `For` ve `Next` bilgilerinin bir `For` döngü.  
  
     Yalnızca değişken bloğu içinde başvurabilirsiniz.  
  
#### <a name="to-make-a-variable-visible-only-within-a-procedure"></a>Bir değişken yalnızca bir yordam içinde görünür hale getirmek için  
  
-   Yer `Dim` yordam içindeki ancak herhangi bir bloğuna dışında değişken bildirimi (gibi bir `With`... `End With` blok).  
  
     Yalnızca değişken yordamda bulunan tüm bloğunun dahil olmak üzere bu yordamı içinde başvurabilirsiniz.  
  
## <a name="scope-at-module-or-namespace-level"></a>Modül veya Namespace düzeyinde kapsamı  
 Tek ifadeli kolaylık sağlamak için *modül düzeyi* modüller, sınıflar ve yapılar için eşit oranda geçerlidir. Modül düzeyi değişkeni erişim düzeyini kapsamı belirler. Modül, sınıf veya yapı içeren ad alanı kapsamı de etkiler.  
  
#### <a name="to-make-a-variable-visible-throughout-a-module-class-or-structure"></a>Bir değişken modülü, sınıf veya yapı boyunca görünür hale getirmek için  
  
1.  Yer `Dim` modülü, sınıf veya yapı içinde ancak herhangi bir yordam dışında değişken bildirimi.  
  
2.  Dahil [özel](../../../../visual-basic/language-reference/modifiers/private.md) anahtar sözcük `Dim` deyimi.  
  
3.  Modül, sınıf veya yapı içinde istediğiniz yere değiştirebilir, ancak değişkeninden başvurabilirsiniz onu dışında.  
  
#### <a name="to-make-a-variable-visible-throughout-a-namespace"></a>Bir değişkenin bir ad alanı boyunca görünür hale getirmek için  
  
1.  Yer `Dim` modülü, sınıf veya yapı içinde ancak herhangi bir yordam dışında değişken bildirimi.  
  
2.  Dahil [arkadaş](../../../../visual-basic/language-reference/modifiers/friend.md) veya [ortak](../../../../visual-basic/language-reference/modifiers/public.md) anahtar sözcük `Dim` deyimi.  
  
3.  Her yerden değişkenini ifade edebilir modülü, sınıf veya yapı içeren ad alanı içinde.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek modülü düzeyinde bir değişkeni bildirir ve modüldeki koduna görünürlüğü sınırlar.  
  
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
  
 Yukarıdaki örnekte tüm yordamları tanımlanan modülünde `demonstrateScope` başvurabilirsiniz `String` değişkeni `strMsg`. Zaman `usePrivateVariable` yordam çağrıldığında, dize değişkenine içeriğini görüntüler `strMsg` iletişim kutusunda.  
  
 Önceki örnekte, dize değişkenine için aşağıdaki değişiklikle birlikte `strMsg` için ad alanı bildiriminden başka bir yerindeki kodu tarafından başvurulabilir.  
  
```  
Public strMsg As String  
```  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Daha dar bir değişkenin kapsamını, yanlışlıkla aynı ada sahip başka bir değişken yerine başvuruda için sahip kesintilerinden. Başvuru eşleşen sorunları en aza indirebilirsiniz.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Daha dar bir değişkenin kapsamını, kötü amaçlı kod hatalı yapabilirsiniz küçük büyük olasılıkla bunu kullanın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic'de kapsam](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)  
 [Visual Basic'de ömür](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [Visual Basic'de erişim düzeyleri](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [Değişkenleri](../../../../visual-basic/programming-guide/language-features/variables/index.md)  
 [Değişken bildirimi](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md)
