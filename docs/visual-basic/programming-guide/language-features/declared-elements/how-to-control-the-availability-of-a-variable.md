---
title: "Nasıl yapılır: Bir Değişkenin Kullanılabilirliğini Denetleme (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 004fb101661fadeaee084e1f9374ca8332ac7234
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-control-the-availability-of-a-variable-visual-basic"></a>Nasıl yapılır: Bir Değişkenin Kullanılabilirliğini Denetleme (Visual Basic)
Belirterek bir değişkenin kullanılabilirliğini denetleme kendi *erişim düzeyine*. Hangi kod okuma veya değişkenine yazma izni olan erişim düzeyini belirler.  
  
-   *Üye değişkenleri* (Modül düzeyinde ve herhangi bir yordam dışında tanımlanan) görebileceği herhangi bir kod erişebilmeniz anlamına gelen genel erişim için varsayılan. Bu, bir erişim değiştiricisi belirleyerek değiştirebilirsiniz.  
  
-   *Yerel değişkenler* (yordam içinde tanımlanmıştır) yalnızca kendi yordamı içindeki kod erişmesine olmamakla birlikte, ismen genel erişimi vardır. Yerel değişkene erişim düzeyini değiştiremezsiniz, ancak içerdiği yordamı erişim düzeyini değiştirebilirsiniz.  
  
 Daha fazla bilgi için bkz: [erişim düzeyini Visual Basic'te](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="private-and-public-access"></a>Özel ve genel erişim  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-module-class-or-structure"></a>Bir değişken modülü, sınıf veya yapı içinde yalnızca erişilebilir hale getirmek için  
  
1.  Yer [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md) modülü, sınıf veya yapı içinde ancak herhangi bir yordam dışında değişken için.  
  
2.  Dahil [özel](../../../../visual-basic/language-reference/modifiers/private.md) anahtar sözcük `Dim` deyimi.  
  
     Okuma veya modül, sınıf veya yapı içinde istediğiniz yere değiştirebilir, ancak değişkeninden yazma dışı.  
  
#### <a name="to-make-a-variable-accessible-from-any-code-that-can-see-it"></a>Bir değişken görebileceğiniz herhangi bir koddan erişilebilir hale getirmek için  
  
1.  Üye değişkeni için yerleştirin `Dim` modülü, sınıf veya yapı içinde ancak herhangi bir yordam dışında değişken bildirimi.  
  
2.  Dahil [ortak](../../../../visual-basic/language-reference/modifiers/public.md) anahtar sözcük `Dim` deyimi.  
  
     Okuma ya da değişkenine derlemenizi ile birlikte çalışan herhangi bir kodda yazma.  
  
 veya  
  
1.  Yerel bir değişken için yerleştirin `Dim` yordam içindeki değişken bildirimi.  
  
2.  İçermeyen `Public` anahtar sözcük `Dim` deyimi.  
  
     Okuma veya yordam içinde istediğiniz yere değiştirebilir, ancak değişkeninden yazma dışı.  
  
## <a name="protected-and-friend-access"></a>Korumalı Friend erişim  
 Bir değişken, sınıf ve türetilen tüm sınıflar ya da kendi derleme erişim düzeyini sınırlayabilirsiniz. Türetilmiş bir sınıf veya başka bir yerde aynı bütünleştirilmiş kodundan erişim sağlayan aşağıdaki sınırlamalara birleşimi de belirtebilirsiniz. Bu birleşim birleştirerek belirttiğiniz `Protected` ve `Friend` aynı bildiriminde anahtar sözcükler.  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-class-and-any-derived-classes"></a>Bir değişken, sınıf ve türetilen tüm sınıflar içinde yalnızca erişilebilir hale getirmek için  
  
1.  Yer `Dim` ifade değişkenin bir sınıf içinde ancak herhangi bir yordam dışında.  
  
2.  Dahil [korumalı](../../../../visual-basic/language-reference/modifiers/protected.md) anahtar sözcük `Dim` deyimi.  
  
     Okuma veya dışarı değiştirebilir, ancak herhangi bir sınıf türetilmiş sınıf içinde istediğiniz yere yanı sıra içinden değişkeninden yazma türetme zincirindeki herhangi bir sınıf dışında.  
  
#### <a name="to-make-a-variable-accessible-only-from-within-the-same-assembly"></a>Bir değişken aynı bütünleştirilmiş kod içinde yalnızca erişilebilir hale getirmek için  
  
1.  Yer `Dim` modülü, sınıf veya yapı içinde ancak herhangi bir yordam dışında değişken bildirimi.  
  
2.  Dahil [arkadaş](../../../../visual-basic/language-reference/modifiers/friend.md) anahtar sözcük `Dim` deyimi.  
  
     Okuma veya modül, sınıf veya yapı içinde istediğiniz yere yanı sıra herhangi bir koddan aynı bütünleştirilmiş kodda değiştirebilir, ancak değişkeninden yazma derleme dışına.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, değişkenlerle bildirimlerini gösterir `Public`, `Protected`, `Friend`, `Protected Friend`, ve `Private` erişim düzeyini. Unutmayın `Dim` deyimi bir erişim düzeyini belirtir, dahil etmek zorunda değildir `Dim` anahtar sözcüğü.  
  
```  
Public Class classForEverybody  
Protected Class classForMyHeirs  
Friend stringForThisProject As String  
Protected Friend stringForProjectAndHeirs As String  
Private numberForMeOnly As Integer  
```  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Daha fazla kısıtlayıcı bir değişken erişim düzeyi, kötü amaçlı kod hatalı yapabilirsiniz küçük büyük olasılıkla bunu kullanın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic'de erişim düzeyleri](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [Dim deyimi](../../../../visual-basic/language-reference/statements/dim-statement.md)  
 [Ortak](../../../../visual-basic/language-reference/modifiers/public.md)  
 [Korumalı](../../../../visual-basic/language-reference/modifiers/protected.md)  
 [Arkadaş](../../../../visual-basic/language-reference/modifiers/friend.md)  
 [Özel](../../../../visual-basic/language-reference/modifiers/private.md)
