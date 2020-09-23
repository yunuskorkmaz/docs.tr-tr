---
title: 'Nasıl yapılır: Bir Değişkenin Kapsamını Denetleme'
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
ms.openlocfilehash: 2ce7c1700eec54542719e6e0880466ca136e86f6
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91095440"
---
# <a name="how-to-control-the-scope-of-a-variable-visual-basic"></a>Nasıl yapılır: Bir Değişkenin Kapsamını Denetleme (Visual Basic)

Normalde, bir değişken *kapsam*içinde veya başvuru için görünür, burada, bildirdiğiniz bölge boyunca olur. Bazı durumlarda, değişkenin *erişim düzeyi* kapsamını etkileyebilir.  
  
 Daha fazla bilgi için [Visual Basic kapsam](scope.md)bölümüne bakın.  
  
## <a name="scope-at-block-or-procedure-level"></a>Blok veya yordam düzeyindeki kapsam  
  
#### <a name="to-make-a-variable-visible-only-within-a-block"></a>Bir değişkeni yalnızca bir blok içinde görünür hale getirmek için  
  
- Değişken için [Dim deyimini](../../../language-reference/statements/dim-statement.md) , bu bloktaki başlatma ve sonlandırma bildirimi deyimleri arasına, örneğin `For` `Next` bir döngünün ve deyimleri arasına yerleştirin `For` .  
  
     Değişkenine yalnızca bloğun içinden başvurabilirsiniz.  
  
#### <a name="to-make-a-variable-visible-only-within-a-procedure"></a>Bir değişkeni yalnızca bir yordam içinde görünür hale getirmek için  
  
- `Dim`Değişkeninin ifadesini yordamın içine yerleştirin, ancak herhangi bir bloğun dışında (örneğin, `With` ... `End With` bloğu).  
  
     Yordamda yer alan herhangi bir bloğun içinde olduğu gibi yalnızca yordamın içinden değişkene başvurabilirsiniz.  
  
## <a name="scope-at-module-or-namespace-level"></a>Modül veya ad alanı düzeyinde kapsam  

 Kolaylık olması için, tek vadeli *Modül düzeyi* modüller, sınıflar ve yapılar için eşit oranda geçerlidir. Modül düzeyi değişkeninin erişim düzeyi kapsamını belirler. Modül, sınıf veya yapıyı içeren ad alanı da kapsamı etkiler.  
  
#### <a name="to-make-a-variable-visible-throughout-a-module-class-or-structure"></a>Bir değişkeni bir modül, sınıf veya yapı genelinde görünür hale getirmek için  
  
1. `Dim`Değişkenin ifadesini modül, sınıf veya yapının içine, ancak herhangi bir yordamın dışına yerleştirin.  
  
2. Deyimdeki [Private](../../../language-reference/modifiers/private.md) anahtar sözcüğünü ekleyin `Dim` .  
  
3. Değişkeni modülün, sınıfın veya yapının içinden herhangi bir yerde, ancak dışından kullanamazsınız.  
  
#### <a name="to-make-a-variable-visible-throughout-a-namespace"></a>Bir değişkeni bir ad alanı boyunca görünür hale getirmek için  
  
1. `Dim`Değişkenin ifadesini modül, sınıf veya yapının içine, ancak herhangi bir yordamın dışına yerleştirin.  
  
2. İfadeye [Friend](../../../language-reference/modifiers/friend.md) veya [Public](../../../language-reference/modifiers/public.md) anahtar sözcüğünü ekleyin `Dim` .  
  
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
  
 Önceki örnekte, modülünde tanımlanan tüm yordamlar `demonstrateScope` `String` değişkenine başvurabilir `strMsg` . `usePrivateVariable`Yordam çağrıldığında, dize değişkeninin içeriğini `strMsg` bir iletişim kutusunda görüntüler.  
  
 Önceki örnekte yapılan aşağıdaki değişiklikle, dize değişkenine, `strMsg` bildiriminin ad alanı içinde herhangi bir yerde kod eklenebilir.  
  
```vb  
Public strMsg As String  
```  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 Bir değişkenin kapsamını daraltmak için, yanlışlıkla aynı ada sahip başka bir değişken yerine buna başvuran daha az fırsat vardır. Ayrıca, başvuru eşleştirmesinin sorunlarını da en aza indirebilirsiniz.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  

 Bir değişkenin kapsamını daraltmak, kötü amaçlı kodun yanlış kullanımı olasılığını en kısa hale getirir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic'de Kapsam](scope.md)
- [Visual Basic'de Ömür](lifetime.md)
- [Visual Basic erişim düzeyleri](access-levels.md)
- [Değişkenler](../variables/index.md)
- [Değişken Bildirimi](../variables/variable-declaration.md)
- [Dim Deyimi](../../../language-reference/statements/dim-statement.md)
