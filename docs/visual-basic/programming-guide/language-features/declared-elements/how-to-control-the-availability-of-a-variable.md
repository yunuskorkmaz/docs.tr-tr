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
ms.openlocfilehash: 886b57909cf6ba25dbaceea5c5f06eb4e3ba6f1f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345388"
---
# <a name="how-to-control-the-availability-of-a-variable-visual-basic"></a>Nasıl yapılır: Bir Değişkenin Kullanılabilirliğini Denetleme (Visual Basic)
Bir değişkenin kullanılabilirliğini, *erişim düzeyini*belirterek kontrol edersiniz. Erişim düzeyi, hangi kodun değişkene okuma veya yazma izni olduğunu belirler.  
  
- *Üye değişkenleri* (modül düzeyinde ve herhangi bir yordam dışında tanımlanır) varsayılan olarak genel erişim için, bu, bunlara erişebilen herhangi bir kod anlamına gelir. Bu, bir erişim değiştiricisi belirterek değiştirebilirsiniz.  
  
- *Yerel değişkenler* (bir yordamda tanımlanan) genel erişime sahiptir, ancak yordamındaki yalnızca kod bunlara erişebilir. Yerel bir değişkenin erişim düzeyini değiştiremezsiniz, ancak onu içeren yordamın erişim düzeyini değiştirebilirsiniz.  
  
 Daha fazla bilgi için bkz. [Visual Basic erişim düzeyleri](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="private-and-public-access"></a>Özel ve genel erişim  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-module-class-or-structure"></a>Bir değişkeni yalnızca kendi modülünün, sınıfının veya yapısının içinden erişilebilir hale getirmek için  
  
1. Değişken için [Dim ifadesini](../../../../visual-basic/language-reference/statements/dim-statement.md) modül, sınıf veya yapının içine, ancak herhangi bir yordamın dışına yerleştirin.  
  
2. `Dim` ifadesine [Private](../../../../visual-basic/language-reference/modifiers/private.md) anahtar sözcüğünü ekleyin.  
  
     Değişkeni modülün, sınıfın veya yapının içinden herhangi bir yerden okuyabilir veya yazabilirsiniz, ancak dışından kullanamazsınız.  
  
#### <a name="to-make-a-variable-accessible-from-any-code-that-can-see-it"></a>Bir değişkeni, görebileceği koddan erişilebilir hale getirmek için  
  
1. Bir üye değişkeni için, değişken için `Dim` ifadesini modül, sınıf veya yapının içine, ancak herhangi bir yordamın dışına koyun.  
  
2. `Dim` ifadesine [Public](../../../../visual-basic/language-reference/modifiers/public.md) anahtar sözcüğünü ekleyin.  
  
     Derlemeden birlikte çalışan herhangi bir koddan değişkeni okuyabilir veya yazabilirsiniz.  
  
 veya  
  
1. Yerel bir değişken için, değişkenin `Dim` ifadesini bir yordamın içine yerleştirin.  
  
2. `Dim` ifadesine `Public` anahtar sözcüğünü eklemeyin.  
  
     Değişkeni yordamın içinden herhangi bir yerden okuyabilir veya yazabilirsiniz.  
  
## <a name="protected-and-friend-access"></a>Korumalı ve arkadaş erişimi  
 Bir değişkenin erişim düzeyini sınıfı ve türetilmiş sınıflar ya da kendi derlemesi ile sınırlayabilirsiniz. Ayrıca, herhangi bir türetilmiş sınıftaki koddan veya aynı derlemede bulunan başka bir yerde erişime izin veren bu kısıtlamaların birleşimini de belirtebilirsiniz. Bu UNION `Protected` ve `Friend` anahtar sözcüklerini aynı bildirimde birleştirerek belirlersiniz.  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-class-and-any-derived-classes"></a>Bir değişkeni yalnızca kendi sınıfının ve türetilmiş sınıfların içinden erişilebilir hale getirmek için  
  
1. Değişken için `Dim` ifadesini bir sınıfın içine, ancak herhangi bir yordamın dışına yerleştirin.  
  
2. [Protected](../../../../visual-basic/language-reference/modifiers/protected.md) anahtar sözcüğünü `Dim` ifadesine ekleyin.  
  
     Değişkeni sınıfın içinde herhangi bir yerden okuyabilir veya yazabilirsiniz, ancak türetme zincirindeki herhangi bir sınıfın dışından değil, onun içinden türetilmiş herhangi bir sınıf içinden.  
  
#### <a name="to-make-a-variable-accessible-only-from-within-the-same-assembly"></a>Bir değişkeni yalnızca aynı derlemenin içinden erişilebilir hale getirmek için  
  
1. Değişken için `Dim` ifadesini modül, sınıf veya yapının içine, ancak herhangi bir yordamın dışına yerleştirin.  
  
2. `Dim` ifadesine [arkadaş](../../../../visual-basic/language-reference/modifiers/friend.md) anahtar sözcüğünü ekleyin.  
  
     Değişkeni modül, sınıf veya yapının içinden herhangi bir yerden okuyabilir veya yazabilirsiniz, ancak derlemenin dışından değil, aynı derlemede bulunan herhangi bir koddan.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek `Public`, `Protected`, `Friend`, `Protected Friend`ve `Private` erişim düzeylerine sahip değişkenlerin bildirimlerini gösterir. `Dim` deyimin bir erişim düzeyi belirttiğinde, `Dim` anahtar sözcüğünü eklemeniz gerekmediğini unutmayın.  
  
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

- [Visual Basic erişim düzeyleri](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Dim Deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [Public](../../../../visual-basic/language-reference/modifiers/public.md)
- [Protected](../../../../visual-basic/language-reference/modifiers/protected.md)
- [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)
- [Private](../../../../visual-basic/language-reference/modifiers/private.md)
