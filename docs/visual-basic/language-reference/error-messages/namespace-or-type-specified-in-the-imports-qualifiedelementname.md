---
title: "Namespace veya içeri aktarmalar &#39;belirtilen türü; &lt;qualifiedelementname&gt;&#39; mevcut değil &#39; t ortak üye içermiyor ya da bulunamıyor"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40056
- vbc40056
helpviewer_keywords: BC40056
ms.assetid: b59f5754-444f-4378-9272-9678b437e84a
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 49cd9fa5d5182b2cf2d7fc4623bc8e9aa02bf85e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="namespace-or-type-specified-in-the-imports-39ltqualifiedelementnamegt39-doesn39t-contain-any-public-member-or-cannot-be-found"></a>Namespace veya içeri aktarmalar &#39;belirtilen türü; &lt;qualifiedelementname&gt;&#39; mevcut değil &#39; t ortak üye içermiyor ya da bulunamıyor
Namespace veya türü belirtilen içeri aktarmalar içinde\<qualifiedelementname >' ortak üye içermiyor veya bulunamıyor. Ad alanı veya tür tanımlanır ve en az bir ortak üye içerdiğinden emin olun. Diğer ad başka diğer adlar içermediğinden emin olun.  
  
 Bir `Imports` deyimi belirtir bulunamıyor veya herhangi bir tanımlamıyor içeren bir öğeyi `Public` üyeleri.  
  
 A *öğeyi içeren* bir ad alanı, sınıf, yapı, modülü, arabirimi veya numaralandırması olabilir. Üye değişkenleri, yordamlar ve içeren diğer öğeler gibi içeren öğe içeriyor.  
  
 İçeri aktarma amacı bunları uygun gerek kalmadan kodunuzu erişim ad alanı veya tür üyeleri için izin vermektir. Projenizi de ad alanı veya türü bir başvuru eklemeniz gerekebilir. Daha fazla bilgi için bkz: "İçeren öğelerini içe aktarma" [bildirilmiş öğelere başvurular](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
 Derleyici belirtilen içeren öğe bulamazsanız, bunu kullanan başvuruları çözümlenemiyor. Öğeyi bulur ancak öğe herhangi kullanıma sunmuyor `Public` üyeleri sonra hiçbir başvurusu olabilir başarılı. Her iki durumda da içeri aktarma öğesi anlamsız hale gelir.  
  
 İçeren bir öğe içeri aktarma ve içeri aktarma diğer ad atayın, ardından bu içeri aktarma diğer ad başka bir öğe içeri aktarmak için kullanamazsınız olduğunu aklınızda bulundurun. Aşağıdaki kod derleyici hatası oluşturur.  
  
 `Imports`   `winfrm`   `= System.Windows.Forms`  
  
 `' The following statement is`   `INVALID`   `because it reuses an import alias.`  
  
 `Imports behav =`   `winfrm`  `.Design.Behavior`  
  
 **Hata Kimliği:** BC40056  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Kapsayan öğe projenizden erişilebilir olduğunu doğrulayın.  
  
2.  İçeren öğesinin belirtimini herhangi alma diğer başka bir içeri aktarma adından içermez doğrulayın.  
  
3.  İçeren öğesi en az bir gösterir doğrulayın `Public` üyesi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Imports deyimi (.NET Namespace ve türü)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [Namespace deyimi](../../../visual-basic/language-reference/statements/namespace-statement.md)  
 [Ortak](../../../visual-basic/language-reference/modifiers/public.md)  
 [Visual Basic'de ad alanları](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [Bildirilmiş öğelere başvurular](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
