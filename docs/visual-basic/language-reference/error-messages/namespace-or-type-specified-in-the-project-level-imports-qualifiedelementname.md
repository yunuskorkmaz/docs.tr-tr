---
title: Proje düzeyi Imports '<qualifiedelementname>' içinde belirtilen ad alanı veya tür ortak üye içermiyor veya bulunamıyor
ms.date: 07/20/2015
f1_keywords:
- vbc40057
- bc40057
helpviewer_keywords:
- BC40057
ms.assetid: 4ae3506e-2ebe-4ff3-995d-14ac60db5e9f
ms.openlocfilehash: 0ee235252d69e6f77ce53b048f45e73d0969e864
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409458"
---
# <a name="namespace-or-type-specified-in-the-project-level-imports-qualifiedelementname-doesnt-contain-any-public-member-or-cannot-be-found"></a>Proje düzeyi Imports '\<qualifiedelementname>' içinde belirtilen ad alanı veya tür ortak üye içermiyor veya bulunamıyor
Proje düzeyi Imports ' ' içinde belirtilen ad alanı veya tür \<qualifiedelementname> ortak üye içermiyor veya bulunamıyor. Ad alanının veya türün tanımlandığından ve en az bir ortak üye içerdiğinden emin olun. Diğer ad adının başka diğer adlar içermediğinden emin olun.  
  
 Projenin içeri aktarma özelliği, bulunamayan veya hiçbir üye tanımlamayan bir kapsayan öğe belirtiyor `Public` .  
  
 *Kapsayan bir öğe* bir Namespace, Class, Structure, Module, Interface veya Enumeration olabilir. Kapsayan öğe, değişkenler, yordamlar veya içerilen diğer öğeler gibi Üyeler içerir.  
  
 İçeri aktarma amacı, kodunuzun ad alanına veya tür üyelerine, bunları nitelemek zorunda kalmadan erişmesine izin versağlamaktır. Projenizin ad alanına veya türe bir başvuru eklemesi de gerekebilir. Daha fazla bilgi için, bkz. "Içerilen öğeleri Içeri aktarma", [belirtilen öğelerin başvuruları](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
 Derleyici belirtilen içeren öğeyi bulamazsa, onu kullanan başvuruları çözemez. Öğe bulunursa ancak öğe hiçbir üye sunmadığında `Public` , hiçbir başvuru başarılı olmaz. Her iki durumda da, öğesini içeri aktarmak anlamlı değildir.  
  
 İçeri aktarılacak öğeleri belirtmek için **Proje tasarımcısını** kullanın. **Başvurular** sayfasının **içeri aktarılan ad alanları** bölümünü kullanın. **Proje tasarımcısına** , **Çözüm Gezgini**içindeki **projem** simgesine çift tıklayarak ulaşabilirsiniz.  
  
 **Hata kimliği:** BC40057  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. **Proje tasarımcısını** açın ve **başvuru** sayfasına geçin.  
  
2. **Içeri aktarılan ad alanları** bölümünde, içeren öğenin projenizden erişilebilir olduğunu doğrulayın.  
  
3. Kapsayan öğenin en az bir üye gösterdiğinden emin olun `Public` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Başvurular Sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
- [Geneldir](../modifiers/public.md)
- [Visual Basic'de Ad Alanları](../../programming-guide/program-structure/namespaces.md)
- [Bildirilmiş Öğelere Başvurular](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
