---
title: 'Nasıl yapılır: Bir Değişkenin Kullanılabilirliğini Denetleme'
ms.date: 07/20/2015
helpviewer_keywords:
- access levels, declared elements
- Private keyword [Visual Basic], accessing variables
- access levels, variables
- Public keyword [Visual Basic], accessing variables
- Friend keyword [Visual Basic], accessing variables
- variables [Visual Basic], access level
- declared elements [Visual Basic], access level
- Protected keyword [Visual Basic], accessing variables
ms.assetid: eaf4f073-7922-43ce-ae1e-90ff376ae947
ms.openlocfilehash: e6173a0eaa0bf84abb1979711c6df932533c5ce9
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91086120"
---
# <a name="how-to-control-the-availability-of-a-variable-visual-basic"></a>Nasıl yapılır: Bir Değişkenin Kullanılabilirliğini Denetleme (Visual Basic)

Bir değişkenin kullanılabilirliğini, *erişim düzeyini*belirterek kontrol edersiniz. Erişim düzeyi, hangi kodun değişkene okuma veya yazma izni olduğunu belirler.  
  
- *Üye değişkenleri* (modül düzeyinde ve herhangi bir yordam dışında tanımlanır) varsayılan olarak genel erişim için, bu, bunlara erişebilen herhangi bir kod anlamına gelir. Bu, bir erişim değiştiricisi belirterek değiştirebilirsiniz.  
  
- *Yerel değişkenler* (bir yordamda tanımlanan) genel erişime sahiptir, ancak yordamındaki yalnızca kod bunlara erişebilir. Yerel bir değişkenin erişim düzeyini değiştiremezsiniz, ancak onu içeren yordamın erişim düzeyini değiştirebilirsiniz.  
  
 Daha fazla bilgi için bkz. [Visual Basic erişim düzeyleri](access-levels.md).  
  
## <a name="private-and-public-access"></a>Özel ve genel erişim  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-module-class-or-structure"></a>Bir değişkeni yalnızca kendi modülünün, sınıfının veya yapısının içinden erişilebilir hale getirmek için  
  
1. Değişken için [Dim ifadesini](../../../language-reference/statements/dim-statement.md) modül, sınıf veya yapının içine, ancak herhangi bir yordamın dışına yerleştirin.  
  
2. Deyimdeki [Private](../../../language-reference/modifiers/private.md) anahtar sözcüğünü ekleyin `Dim` .  
  
     Değişkeni modülün, sınıfın veya yapının içinden herhangi bir yerden okuyabilir veya yazabilirsiniz, ancak dışından kullanamazsınız.  
  
#### <a name="to-make-a-variable-accessible-from-any-code-that-can-see-it"></a>Bir değişkeni, görebileceği koddan erişilebilir hale getirmek için  
  
1. Bir üye değişkeni için, `Dim` değişkenin ifadesini bir modül, sınıf veya yapının içine, ancak herhangi bir yordamın dışına yerleştirin.  
  
2. Deyimdeki [Public](../../../language-reference/modifiers/public.md) anahtar sözcüğünü ekleyin `Dim` .  
  
     Derlemeden birlikte çalışan herhangi bir koddan değişkeni okuyabilir veya yazabilirsiniz.  
  
 -veya-  
  
1. Yerel bir değişken için, `Dim` değişkenin ifadesini bir yordamın içine yerleştirin.  
  
2. `Public`Deyimdeki anahtar sözcüğünü eklemeyin `Dim` .  
  
     Değişkeni yordamın içinden herhangi bir yerden okuyabilir veya yazabilirsiniz.  
  
## <a name="protected-and-friend-access"></a>Korumalı ve arkadaş erişimi  

 Bir değişkenin erişim düzeyini sınıfı ve türetilmiş sınıflar ya da kendi derlemesi ile sınırlayabilirsiniz. Ayrıca, herhangi bir türetilmiş sınıftaki koddan veya aynı derlemede bulunan başka bir yerde erişime izin veren bu kısıtlamaların birleşimini de belirtebilirsiniz. `Protected`Aynı bildirimde ve anahtar sözcüklerini birleştirerek bu birleşimi belirtirsiniz `Friend` .  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-class-and-any-derived-classes"></a>Bir değişkeni yalnızca kendi sınıfının ve türetilmiş sınıfların içinden erişilebilir hale getirmek için  
  
1. `Dim`Değişkenin ifadesini bir sınıfın içine, ancak herhangi bir yordamın dışına yerleştirin.  
  
2. [Korumalı](../../../language-reference/modifiers/protected.md) anahtar sözcüğünü `Dim` deyime ekleyin.  
  
     Değişkeni sınıfın içinde herhangi bir yerden okuyabilir veya yazabilirsiniz, ancak türetme zincirindeki herhangi bir sınıfın dışından değil, onun içinden türetilmiş herhangi bir sınıf içinden.  
  
#### <a name="to-make-a-variable-accessible-only-from-within-the-same-assembly"></a>Bir değişkeni yalnızca aynı derlemenin içinden erişilebilir hale getirmek için  
  
1. `Dim`Değişkenin ifadesini bir modül, sınıf veya yapının içine, ancak herhangi bir yordamın dışına yerleştirin.  
  
2. Deyime [arkadaş](../../../language-reference/modifiers/friend.md) anahtar sözcüğünü ekleyin `Dim` .  
  
     Değişkeni modül, sınıf veya yapının içinden herhangi bir yerden okuyabilir veya yazabilirsiniz, ancak derlemenin dışından değil, aynı derlemede bulunan herhangi bir koddan.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek,,,, `Public` `Protected` `Friend` `Protected Friend` ve `Private` erişim düzeylerindeki değişkenlerin bildirimlerini gösterir. `Dim`İfade bir erişim düzeyi belirttiğinde, anahtar sözcüğünü eklemeniz gerekmediğini unutmayın `Dim` .  
  
```vb  
Public Class classForEverybody  
Protected Class classForMyHeirs  
Friend stringForThisProject As String  
Protected Friend stringForProjectAndHeirs As String  
Private numberForMeOnly As Integer  
```  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  

 Bir değişkenin erişim düzeyi daha kısıtlayıcıysa, kötü amaçlı kodun yanlış kullanımı ihtimaline karşı daha az olabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic erişim düzeyleri](access-levels.md)
- [Dim Deyimi](../../../language-reference/statements/dim-statement.md)
- [Geneldir](../../../language-reference/modifiers/public.md)
- [Korunamadı](../../../language-reference/modifiers/protected.md)
- [Arkadaş](../../../language-reference/modifiers/friend.md)
- [Özelleştirme](../../../language-reference/modifiers/private.md)
