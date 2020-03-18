---
title: Kullanıcı Tarafından Filtrelenmiş Özel Durum İşleyicilerini Kullanma
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- user-filtered exceptions
- exceptions, user-filtered
ms.assetid: aa80d155-060d-41b4-a636-1ceb424afee8
ms.openlocfilehash: 5537404178b746310f720c5b0c075c77287dda4c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708459"
---
# <a name="using-user-filtered-exception-handlers"></a>Kullanıcı Tarafından Filtrelenmiş Özel Durum İşleyicilerini Kullanma

Şu anda Visual Basic, kullanıcı tarafından filtre uygulanmış özel durumları destekler. Kullanıcı tarafından filtre uygulanmış özel durum işleyicileri, özel durum için tanımladığınız gereksinimlere göre özel durumları yakalar ve işler. Bu işleyiciler Catch **deyimini** **When** anahtar sözcüğüyle birlikte kullanır.  
  
 Bu teknik, belirli bir özel durum nesnesi birden çok hataya karşılık geldiğinde yararlıdır. Bu durumda, nesne genellikle hata ile ilişkili belirli hata kodu içeren bir özelliği vardır. İfadedeki hata kodu özelliğini yalnızca bu **Catch** yan tümcesinde işlemek istediğiniz belirli hatayı seçmek için kullanabilirsiniz.  
  
 Aşağıdaki Visual Basic örneği **Catch/When** deyimini göstermektedir.  
  
```vb
Try  
    'Try statements.  
    Catch When Err = VBErr_ClassLoadException
    'Catch statements.
End Try  
```  
  
 Kullanıcı tarafından filtre uygulanmış yan tümcenin ifadesi hiçbir şekilde kısıtlanmaz. Kullanıcı tarafından filtre uygulanan ifadenin yürütülmesi sırasında bir özel durum oluşursa, bu özel durum atılır ve filtre ifadesi yanlış olarak değerlendirilmiş olarak kabul edilir. Bu durumda, ortak dil çalışma zamanı geçerli özel durum için bir işleyici aramaya devam ediyor.  
  
## <a name="combining-the-specific-exception-and-the-user-filtered-clauses"></a>Özel Özel Durum ve Kullanıcı Filtreuygulanan Yan Tümceleri Birleştirme  
 Catch deyimi hem özel özel durum hem de kullanıcı tarafından filtre uygulanmış yan tümceleri içerebilir. Çalışma zamanı önce belirli özel durumu sınar. Belirli bir özel durum başarılı olursa, çalışma zamanı kullanıcı filtresini yürütür. Genel filtre, sınıf filtresinde bildirilen değişkene bir başvuru içerebilir. İki filtre yan tümcesinin sırasının geri alınamayacağını unutmayın.  
  
 Aşağıdaki Visual Basic örneği, `ClassLoadException` **Catch** deyimindeki özel özel durumu ve **Zaman** anahtar sözcük lerini kullanarak kullanıcı tarafından filtre uygulanmış yan tümcesini gösterir.  
  
```vb
Try  
    'Try statements.
    Catch cle As ClassLoadException When cle.IsRecoverable()  
    'Catch statements.
End Try  
```  

## <a name="see-also"></a>Ayrıca bkz.

- [Özel durumlar](index.md)
