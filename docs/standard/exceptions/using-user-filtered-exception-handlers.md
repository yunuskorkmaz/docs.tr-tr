---
title: Kullanıcı Tarafından Filtrelenmiş Özel Durum İşleyicilerini Kullanma
ms.date: 03/30/2017
helpviewer_keywords:
- user-filtered exceptions
- exceptions, user-filtered
ms.assetid: aa80d155-060d-41b4-a636-1ceb424afee8
ms.openlocfilehash: 4b85c2be0ed61af38eac1b65fb70f0ef1ea4405e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95669048"
---
# <a name="using-user-filtered-exception-handlers"></a>Kullanıcı Tarafından Filtrelenmiş Özel Durum İşleyicilerini Kullanma

Şu anda Visual Basic Kullanıcı tarafından filtrelenen özel durumları destekler. Kullanıcı filtrelenmiş özel durum işleyicileri özel durum için tanımladığınız gereksinimlere göre özel durumları yakalar ve işler. Bu işleyiciler **catch** **ifadesini as anahtar** sözcüğüyle birlikte kullanır.  
  
 Bu teknik, belirli bir özel durum nesnesi birden çok hataya karşılık geldiğinde yararlıdır. Bu durumda, nesnesi genellikle hatayla ilişkili özel hata kodunu içeren bir özelliğe sahiptir. Bu **catch** yan tümcesinde işlemek istediğiniz belirli bir hatayı seçmek için ifadesindeki hata kodu özelliğini kullanabilirsiniz.  
  
 Aşağıdaki Visual Basic örnek, **catch/** while ifadesini gösterir.  
  
```vb
Try  
    'Try statements.  
    Catch When Err = VBErr_ClassLoadException
    'Catch statements.
End Try  
```  
  
 Kullanıcı filtrelenmiş yan tümcesinin ifadesi herhangi bir şekilde kısıtlanmaz. Kullanıcı tarafından filtrelenen ifadenin yürütülmesi sırasında bir özel durum oluşursa, bu özel durum atılır ve filtre ifadesi yanlış olarak değerlendirilir. Bu durumda, ortak dil çalışma zamanı, geçerli özel durum için bir işleyici aramaya devam eder.  
  
## <a name="combining-the-specific-exception-and-the-user-filtered-clauses"></a>Belirli özel durumu ve User-Filtered yan tümcelerini birleştirme  

 Catch ifadesinde hem belirli özel durum hem de Kullanıcı tarafından filtrelenmiş yan tümceler bulunabilir. Çalışma zamanı, önce belirli özel durumu sınar. Belirli özel durum başarılı olursa, çalışma zamanı Kullanıcı filtresini yürütür. Genel filtre, sınıf filtresinde belirtilen değişkene bir başvuru içerebilir. İki filtre yan tümcelerinin sırasının geri çevrilmeyeceğini unutmayın.  
  
 Aşağıdaki Visual Basic örnek, catch deyimindeki özel durumun `ClassLoadException` yanı sıra **Catch** as anahtar sözcüğünü kullanan kullanıcı tarafından filtrelenmiş yan tümce gösterir. **When**  
  
```vb
Try  
    'Try statements.
    Catch cle As ClassLoadException When cle.IsRecoverable()  
    'Catch statements.
End Try  
```  

## <a name="see-also"></a>Ayrıca bkz.

- [Özel Durumlar](index.md)
