---
title: "Namespace veya proje düzeyi içeri aktarmalar &#39;belirtilen türü; &lt;qualifiedelementname&gt;&#39; mevcut değil &#39; t ortak üye içermiyor ya da bulunamıyor"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40057
- bc40057
helpviewer_keywords: BC40057
ms.assetid: 4ae3506e-2ebe-4ff3-995d-14ac60db5e9f
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0d0a164562524af239b3b130f681dbc6eff23814
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="namespace-or-type-specified-in-the-project-level-imports-39ltqualifiedelementnamegt39-doesn39t-contain-any-public-member-or-cannot-be-found"></a>Namespace veya proje düzeyi içeri aktarmalar &#39;belirtilen türü; &lt;qualifiedelementname&gt;&#39; mevcut değil &#39; t ortak üye içermiyor ya da bulunamıyor
Namespace veya türü belirtilen proje düzeyi içeri aktarmalar içinde\<qualifiedelementname >' ortak üye içermiyor veya bulunamıyor. Ad alanı veya tür tanımlanır ve en az bir ortak üye içerdiğinden emin olun. Diğer ad başka diğer adlar içermediğinden emin olun.  
  
 Projenin bir alma özellik bulunamıyor veya herhangi bir tanımlamıyor içeren bir öğeyi belirtir `Public` üyeleri.  
  
 A *öğeyi içeren* bir ad alanı, sınıf, yapı, modülü, arabirimi veya numaralandırması olabilir. Üye değişkenleri, yordamlar ve içeren diğer öğeler gibi içeren öğe içeriyor.  
  
 İçeri aktarma amacı bunları uygun gerek kalmadan kodunuzu erişim ad alanı veya tür üyeleri için izin vermektir. Projenizi de ad alanı veya türü bir başvuru eklemeniz gerekebilir. Daha fazla bilgi için bkz: "İçeren öğelerini içe aktarma" [bildirilmiş öğelere başvurular](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
 Derleyici belirtilen içeren öğe bulamazsanız, bunu kullanan başvuruları çözümlenemiyor. Öğeyi bulur ancak öğe herhangi kullanıma sunmuyor `Public` üyeleri sonra hiçbir başvurusu olabilir başarılı. Her iki durumda da içeri aktarma öğesi anlamsız hale gelir.  
  
 Kullandığınız **Proje Tasarımcısı** almak için öğeleri belirtmek için. Kullanım **içeri aktarılan ad alanları** bölümünü **başvuruları** sayfası. İçin edinebilirsiniz **Proje Tasarımcısı** çift tıklatarak **My proje** simgesine **Çözüm Gezgini**.  
  
 **Hata Kimliği:** BC40057  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Açık **Proje Tasarımcısı** ve geçiş **başvuru** sayfası.  
  
2.  İçinde **içeri aktarılan ad alanları** bölümünde, kapsayan öğe projenizden erişilebilir olduğunu doğrulayın.  
  
3.  İçeren öğesi en az bir gösterir doğrulayın `Public` üyesi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Başvurular sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic)  
 [Proje ve çözüm özelliklerini yönetme](/visualstudio/ide/managing-project-and-solution-properties)  
 [Ortak](../../../visual-basic/language-reference/modifiers/public.md)  
 [Visual Basic'de ad alanları](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [Bildirilmiş öğelere başvurular](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
