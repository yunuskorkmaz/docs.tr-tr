---
title: Imports belirtilen Namespace veya tür &#39; &lt;qualifiedelementname&gt; &#39; eklenmemişse&#39;t, genel üye içeren veya bulunamıyor
ms.date: 07/20/2015
f1_keywords:
- bc40056
- vbc40056
helpviewer_keywords:
- BC40056
ms.assetid: b59f5754-444f-4378-9272-9678b437e84a
ms.openlocfilehash: 21c0794fb4ed6104204fba5d49e37394eff24865
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54552144"
---
# <a name="namespace-or-type-specified-in-the-imports-39ltqualifiedelementnamegt39-doesn39t-contain-any-public-member-or-cannot-be-found"></a>Imports belirtilen Namespace veya tür &#39; &lt;qualifiedelementname&gt; &#39; eklenmemişse&#39;t, genel üye içeren veya bulunamıyor
Imports belirtilen Namespace veya tür\<qualifiedelementname >', genel üye içermiyor veya bulunamıyor. Ad alanı veya tür tanımlanır ve en az bir ortak üye içerdiğinden emin olun. Diğer ad başka diğer adlar içermediğinden emin olun.  
  
 Bir `Imports` deyimi belirtir bulunamıyor ya da tüm tanımlamıyor içeren bir öğe `Public` üyeleri.  
  
 A *öğeyi içeren* bir ad alanı, sınıf, yapı, modülü, arabirimi veya sabit listesi olabilir. Kapsayıcı öğe üyeleri, değişkenleri, yordamları veya içeren diğer öğeleri içerir.  
  
 İçeri aktarma amacı, bunları uygun zorunda kalmadan kodunuzu ad alanı veya tür üyelerine erişmek için izin vermektir. Projenizi de ad alanı veya tür için bir başvuru eklemeniz gerekebilir. Daha fazla bilgi için "İçeren öğeleri içeri aktarma" bölümüne bakın. [bildirilmiş öğelere başvurular](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
 Derleyiciye belirtilen kapsayıcı öğe bulamazsa, kullanılmakta başvuru çözümlenemiyor. Öğeyi bulur ancak öğe herhangi kullanıma sunmuyor `Public` üyeleri, ardından hiçbir başvurusu olabilir başarılı. Her iki durumda da, içeri aktarma öğesi anlamsız.  
  
 Bir kapsayıcı öğe içeri aktarma ve içeri aktarma diğer ad atayın, ardından bu içeri aktarma diğer ad başka bir öğe almak için kullanamazsınız olduğunu aklınızda bulundurun. Aşağıdaki kod bir derleyici hatası oluşturur.  
  
 `Imports`   `winfrm`   `= System.Windows.Forms`  
  
 `' The following statement is`   `INVALID`   `because it reuses an import alias.`  
  
 `Imports behav =`   `winfrm`  `.Design.Behavior`  
  
 **Hata Kimliği:** BC40056  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Kapsayıcı öğe projenizden erişilebilir olduğunu doğrulayın.  
  
2.  Kapsayıcı öğe belirtimi başka bir içeri aktarma ad alanından başka bir içeri aktarma içerip içermediğini doğrulayın.  
  
3.  Kapsayıcı öğe en az bir sunan doğrulayın `Public` üyesi.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Imports Deyimi (.NET Ad Alanı ve Türü)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [Namespace Deyimi](../../../visual-basic/language-reference/statements/namespace-statement.md)
- [Public](../../../visual-basic/language-reference/modifiers/public.md)
- [Visual Basic'de ad alanları](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [Bildirilmiş Öğelere Başvurular](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
