---
title: Proje düzeyi Imports '<qualifiedelementname>' içinde belirtilen ad alanı veya tür ortak üye içermiyor veya bulunamıyor
ms.date: 07/20/2015
f1_keywords:
- vbc40057
- bc40057
helpviewer_keywords:
- BC40057
ms.assetid: 4ae3506e-2ebe-4ff3-995d-14ac60db5e9f
ms.openlocfilehash: 554300f87dbfca351ebcd2d544051968e84880ab
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58816834"
---
# <a name="namespace-or-type-specified-in-the-project-level-imports-qualifiedelementname-doesnt-contain-any-public-member-or-cannot-be-found"></a>Belirtilen proje düzeyi Imports Namespace veya tür\<qualifiedelementname >', genel üye içermiyor veya bulunamıyor
Belirtilen proje düzeyi Imports Namespace veya tür\<qualifiedelementname >', genel üye içermiyor veya bulunamıyor. Ad alanı veya tür tanımlanır ve en az bir ortak üye içerdiğinden emin olun. Diğer ad başka diğer adlar içermediğinden emin olun.  
  
 Bir projenin bir içeri aktarma özelliği bulunamıyor ya da tüm tanımlamıyor içeren bir öğeyi belirtir `Public` üyeleri.  
  
 A *öğeyi içeren* bir ad alanı, sınıf, yapı, modülü, arabirimi veya sabit listesi olabilir. Kapsayıcı öğe üyeleri, değişkenleri, yordamları veya içeren diğer öğeleri içerir.  
  
 İçeri aktarma amacı, bunları uygun zorunda kalmadan kodunuzu ad alanı veya tür üyelerine erişmek için izin vermektir. Projenizi de ad alanı veya tür için bir başvuru eklemeniz gerekebilir. Daha fazla bilgi için "İçeren öğeleri içeri aktarma" bölümüne bakın. [bildirilmiş öğelere başvurular](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
 Derleyiciye belirtilen kapsayıcı öğe bulamazsa, kullanılmakta başvuru çözümlenemiyor. Öğeyi bulur ancak öğe herhangi kullanıma sunmuyor `Public` üyeleri, ardından hiçbir başvurusu olabilir başarılı. Her iki durumda da, içeri aktarma öğesi anlamsız.  
  
 Kullandığınız **Proje Tasarımcısı** almak için öğeleri belirtmek için. Kullanım **içeri aktarılan ad alanlarını** bölümünü **başvuruları** sayfası. Ulaşmak için **Proje Tasarımcısı** çift tıklayarak **Projem** simgesini **Çözüm Gezgini**.  
  
 **Hata Kimliği:** BC40057  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Açık **Proje Tasarımcısı** geçin **başvuru** sayfası.  
  
2.  İçinde **içeri aktarılan ad alanlarını** bölümünde, kapsayıcı öğe projenizden erişilebilir olduğunu doğrulayın.  
  
3.  Kapsayıcı öğe en az bir sunan doğrulayın `Public` üyesi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Başvurular Sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
- [Public](../../../visual-basic/language-reference/modifiers/public.md)
- [Visual Basic'de ad alanları](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [Bildirilmiş Öğelere Başvurular](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
