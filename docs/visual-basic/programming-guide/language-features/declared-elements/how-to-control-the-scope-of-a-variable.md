---
title: 'Nasıl yapılır: Bir Değişkenin Kapsamını Denetleme (Visual Basic)'
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
ms.openlocfilehash: 23a10bd2d6c0c9f3a13bff864559460c48927e01
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582610"
---
# <a name="how-to-control-the-scope-of-a-variable-visual-basic"></a>Nasıl yapılır: Bir Değişkenin Kapsamını Denetleme (Visual Basic)
Normalde, bir değişken *kapsam*içinde veya başvuru için görünür, burada, bildirdiğiniz bölge boyunca olur. Bazı durumlarda, değişkenin *erişim düzeyi* kapsamını etkileyebilir.  
  
 Daha fazla bilgi için [Visual Basic kapsam](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)bölümüne bakın.  
  
## <a name="scope-at-block-or-procedure-level"></a>Blok veya yordam düzeyindeki kapsam  
  
#### <a name="to-make-a-variable-visible-only-within-a-block"></a>Bir değişkeni yalnızca bir blok içinde görünür hale getirmek için  
  
- Bir `For` döngüsünün `For` ve `Next` deyimleri arasında örneğin, bu bloğun başlatma ve sonlandırma bildirimi deyimleri arasına, değişken için [Dim deyimini](../../../../visual-basic/language-reference/statements/dim-statement.md) yerleştirin.  
  
     Değişkenine yalnızca bloğun içinden başvurabilirsiniz.  
  
#### <a name="to-make-a-variable-visible-only-within-a-procedure"></a>Bir değişkeni yalnızca bir yordam içinde görünür hale getirmek için  
  
- Değişken için `Dim` ifadesini yordamın içine yerleştirin, ancak herhangi bir bloğun dışında (örneğin, bir `With`... `End With` bloğu).  
  
     Yordamda yer alan herhangi bir bloğun içinde olduğu gibi yalnızca yordamın içinden değişkene başvurabilirsiniz.  
  
## <a name="scope-at-module-or-namespace-level"></a>Modül veya ad alanı düzeyinde kapsam  
 Kolaylık olması için, tek vadeli *Modül düzeyi* modüller, sınıflar ve yapılar için eşit oranda geçerlidir. Modül düzeyi değişkeninin erişim düzeyi kapsamını belirler. Modül, sınıf veya yapıyı içeren ad alanı da kapsamı etkiler.  
  
#### <a name="to-make-a-variable-visible-throughout-a-module-class-or-structure"></a>Bir değişkeni bir modül, sınıf veya yapı genelinde görünür hale getirmek için  
  
1. Değişken için `Dim` ifadesini modül, sınıf veya yapının içine, ancak herhangi bir yordamın dışına yerleştirin.  
  
2. @No__t_1 ifadesine [Private](../../../../visual-basic/language-reference/modifiers/private.md) anahtar sözcüğünü ekleyin.  
  
3. Değişkeni modülün, sınıfın veya yapının içinden herhangi bir yerde, ancak dışından kullanamazsınız.  
  
#### <a name="to-make-a-variable-visible-throughout-a-namespace"></a>Bir değişkeni bir ad alanı boyunca görünür hale getirmek için  
  
1. Değişken için `Dim` ifadesini modül, sınıf veya yapının içine, ancak herhangi bir yordamın dışına yerleştirin.  
  
2. @No__t_2 ifadesine [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) veya [Public](../../../../visual-basic/language-reference/modifiers/public.md) anahtar sözcüğünü ekleyin.  
  
3. Değişkeni, modül, sınıf veya yapıyı içeren ad alanı içinde herhangi bir yerden yazabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek modül düzeyinde bir değişken bildirir ve görünürlüğünü modül içindeki kodla sınırlandırır.  
  
```vb  
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
  
 Yukarıdaki örnekte, `demonstrateScope` modülünde tanımlanan tüm yordamlar `String` değişkenine başvurabilir `strMsg`. @No__t_0 yordam çağrıldığında, `strMsg` dize değişkeninin içeriğini bir iletişim kutusunda görüntüler.  
  
 Önceki örnekte yapılan aşağıdaki değişiklikle, dize değişkeni `strMsg`, bildiriminin ad alanı içinde herhangi bir yerde kodla başvurulabilir.  
  
```vb  
Public strMsg As String  
```  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Bir değişkenin kapsamını daraltmak için, yanlışlıkla aynı ada sahip başka bir değişken yerine buna başvuran daha az fırsat vardır. Ayrıca, başvuru eşleştirmesinin sorunlarını da en aza indirebilirsiniz.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Bir değişkenin kapsamını daraltmak, kötü amaçlı kodun yanlış kullanımı olasılığını en kısa hale getirir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic kapsam](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [Visual Basic ömrü](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [Visual Basic erişim düzeyleri](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Değişkenler](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [Değişken Bildirimi](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Dim Deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md)
