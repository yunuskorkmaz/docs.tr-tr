---
title: 'Nasıl yapılır: (Visual Basic) bir değişkenin kullanılabilirliğini denetleme'
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
ms.openlocfilehash: 4d5db7fe474d8732e0ae37f3d95d0187eef68ec9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54582498"
---
# <a name="how-to-control-the-availability-of-a-variable-visual-basic"></a>Nasıl yapılır: (Visual Basic) bir değişkenin kullanılabilirliğini denetleme
Belirterek bir değişkenin kullanılabilirliğini denetleme kendi *erişim düzeyi*. Hangi kod okuma veya değişkenine yazma izni olan erişim düzeyini belirler.  
  
-   *Üye değişkenleri* (Modül düzeyinde ve her türlü yordam dışında tanımlanan) varsayılan görebileceği herhangi bir kod erişebileceği anlamına gelir genel erişim için. Bu, bir erişim değiştiricisidir belirterek değiştirebilirsiniz.  
  
-   *Yerel değişkenler* (bir yordam içinde tanımlanmıştır) olup genel erişim sahip ancak yalnızca kendi yordamdaki kodu erişebilir. Yerel bir değişken erişim düzeyini değiştiremezsiniz, ancak içerdiği yordamı erişim düzeyini değiştirebilirsiniz.  
  
 Daha fazla bilgi için [erişim düzeyini Visual Basic'te](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="private-and-public-access"></a>Özel ve genel erişim  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-module-class-or-structure"></a>Bir değişkenin kendi modül, sınıf veya yapı içinde yalnızca erişilebilir hale getirmek için  
  
1.  Bir yerde [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md) değişken modülü, sınıf veya yapı içinde ancak dışında herhangi bir yordam için.  
  
2.  Dahil [özel](../../../../visual-basic/language-reference/modifiers/private.md) anahtar sözcüğünü `Dim` deyimi.  
  
     Okuma veya değişkeninden değil, ancak, modül, sınıf veya yapı içinde herhangi bir yere yazmak, dışında.  
  
#### <a name="to-make-a-variable-accessible-from-any-code-that-can-see-it"></a>Bir değişken görebileceğiniz herhangi bir koddan erişilebilir hale getirmek için  
  
1.  Bir üye değişkeni için yerleştirin `Dim` bir modül, sınıf veya yapı içinde ancak her türlü yordam dışındaki değişken bildirimi.  
  
2.  Dahil [genel](../../../../visual-basic/language-reference/modifiers/public.md) anahtar sözcüğünü `Dim` deyimi.  
  
     Okuma veya değişkene derlemenizi ile birlikte çalışan herhangi bir kodu yazın.  
  
 -veya-  
  
1.  Yerel bir değişken için yerleştirin `Dim` bir yordam içinde değişken bildirimi.  
  
2.  Dahil etmezseniz `Public` anahtar sözcüğünü `Dim` deyimi.  
  
     Okuma veya değişkeninden değil, ancak yordam içinde herhangi bir yere yazmak, dışında.  
  
## <a name="protected-and-friend-access"></a>Korumalı ve öğesine Friend erişimi  
 Bir değişken sınıfına ve tüm türetilmiş sınıfları veya kendi derlemesi için erişim düzeyini sınırlayabilirsiniz. Türetilmiş bir sınıf ya da başka bir yerde aynı bütünleştirilmiş kodundan erişim sağlayan Bu sınırlamalar birleşimi belirtebilirsiniz. Bu birleşim birleştirerek belirttiğiniz `Protected` ve `Friend` aynı bildirimde anahtar sözcükleri.  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-class-and-any-derived-classes"></a>Bir değişken sınıfına ve tüm türetilmiş sınıflar içinde yalnızca erişilebilir hale getirmek için  
  
1.  Bir yerde `Dim` bir sınıf içinde ancak her türlü yordam dışındaki değişken bildirimi.  
  
2.  Dahil [korumalı](../../../../visual-basic/language-reference/modifiers/protected.md) anahtar sözcüğünü `Dim` deyimi.  
  
     Okuma veya herhangi bir sınıf değil, ancak ondan türetilen sınıf içinde herhangi bir yere yanı sıra içinden değişkeninden yazma türetme zincirindeki herhangi bir sınıfın dışında.  
  
#### <a name="to-make-a-variable-accessible-only-from-within-the-same-assembly"></a>Bir değişken aynı bütünleştirilmiş kod içinde yalnızca erişilebilir hale getirmek için  
  
1.  Bir yerde `Dim` bir modül, sınıf veya yapı içinde ancak her türlü yordam dışındaki değişken bildirimi.  
  
2.  Dahil [arkadaş](../../../../visual-basic/language-reference/modifiers/friend.md) anahtar sözcüğünü `Dim` deyimi.  
  
     Okuma veya modül, sınıf veya yapı içinde herhangi bir yere yanı sıra herhangi bir koddan değil, ancak aynı bütünleştirilmiş kodun değişkeninden yazma derleme dışından.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, içeren değişken bildirimlerini gösterir `Public`, `Protected`, `Friend`, `Protected Friend`, ve `Private` erişim düzeyi. Dikkat edin `Dim` eklemek gerekmez, deyimi belirtir bir erişim düzeyi `Dim` anahtar sözcüğü.  
  
```  
Public Class classForEverybody  
Protected Class classForMyHeirs  
Friend stringForThisProject As String  
Protected Friend stringForProjectAndHeirs As String  
Private numberForMeOnly As Integer  
```  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Daha kısıtlayıcı bir değişken erişim düzeyi, kötü amaçlı kod hatalı yapabilirsiniz daha küçük büyük olasılıkla bunu kullanın.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Visual Basic'de erişim düzeyleri](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Dim Deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [Public](../../../../visual-basic/language-reference/modifiers/public.md)
- [Protected](../../../../visual-basic/language-reference/modifiers/protected.md)
- [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)
- [Private](../../../../visual-basic/language-reference/modifiers/private.md)
