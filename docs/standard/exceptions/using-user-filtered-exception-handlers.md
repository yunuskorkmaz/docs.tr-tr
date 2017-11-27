---
title: "Kullanıcı Tarafından Filtrelenmiş Özel Durum İşleyicilerini Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user-filtered exceptions
- exceptions, user-filtered
ms.assetid: aa80d155-060d-41b4-a636-1ceb424afee8
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a71a722063448fb0d568f4bfb4f71d4e01c57454
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="using-user-filtered-exception-handlers"></a>Kullanıcı Tarafından Filtrelenmiş Özel Durum İşleyicilerini Kullanma
Şu anda, Visual Basic kullanıcı tarafından filtrelenmiş özel durumlar destekler. Kullanıcı tarafından filtrelenmiş özel durum işleyicileri yakalamak ve gereksinimler için özel durum tanımlayan temelinde özel durumları işleme. Bu işleyiciler kullanmak **Catch** deyimiyle **zaman** anahtar sözcüğü.  
  
 Bu yöntem, belirli özel durum nesnesi için birden çok hata karşılık gelen yararlıdır. Bu durumda, nesne genellikle şu hata ile ilişkilendirilmiş belirli hata kodunu içeren bir özelliğe sahiptir. Hata kodu özelliği yalnızca içinde işleyen istediğiniz belirli hata seçmek için ifade kullanabilirsiniz **Catch** yan tümcesi.  
  
 Aşağıdaki Visual Basic örnek gösterilmektedir **Catch/olduğunda** deyimi.  
  
```  
Try  
      'Try statements.  
   Catch When Err = VBErr_ClassLoadException  
      'Catch statements.  
End Try  
```  
  
 Kullanıcı tarafından filtrelenmiş yan tümcesinin ifadesi herhangi bir şekilde sınırlı değil. Kullanıcı tarafından filtrelenmiş ifadenin yürütülmesi sırasında bir özel durum oluşursa, başka bir özel durum atılır ve filtre ifadesi false olarak değerlendirildiğinden olarak değerlendirilir. Bu durumda, ortak dil çalışma zamanı geçerli özel durumu için bir işleyici aramaya devam eder.  
  
## <a name="combining-the-specific-exception-and-the-user-filtered-clauses"></a>Bir özel durum ve kullanıcı tarafından filtrelenmiş yan tümceleri birleştirme  
 Catch deyimi, bir özel durum ve kullanıcı tarafından filtrelenmiş yan tümceleri içerebilir. Çalışma zamanı bir özel durum ilk sınar. Bir özel durum başarılı olursa, çalışma zamanı kullanıcı filtresini yürütür. Genel filtre sınıfı filtrede bildirilen değişken başvuru içerebilir. İki filtre yan tümcesi sırasını tersine unutmayın.  
  
 Aşağıdaki Visual Basic örnek bir özel durum gösterir `ClassLoadException` içinde **Catch** deyimi yanı sıra kullanıcı tarafından filtrelenmiş yan tümcesini kullanarak **zaman** anahtar sözcüğü.  
  
```  
Try  
      'Try statements.  
   Catch cle As ClassLoadException When cle.IsRecoverable()  
      'Catch statements.  
End Try  
```  

## <a name="see-also"></a>Ayrıca Bkz.
[Özel durumlar](index.md)
