---
title: Kullanıcı tarafından filtrelenmiş özel durum işleyicilerini kullanma
description: C# ve Visual Basic Kullanıcı filtrelenmiş özel durum işleyicilerini nasıl kullanacağınızı öğrenin.
ms.date: 12/14/2020
helpviewer_keywords:
- user-filtered exceptions
- exceptions, user-filtered
dev_langs:
- csharp
- vb
ms.openlocfilehash: 2dba43ad2fc685a6555ab43fc973814fd7f359a3
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97512677"
---
# <a name="use-user-filtered-exception-handlers"></a>Kullanıcı tarafından filtrelenmiş özel durum işleyicilerini kullanma

Kullanıcı filtrelenmiş özel durum işleyicileri özel durum için tanımladığınız gereksinimlere göre özel durumları yakalar ve işler. Bu işleyiciler, `catch` ifadesini `when` anahtar sözcüğüyle ( `Catch` ve `When` Visual Basic) kullanır.  
  
 Bu teknik, belirli bir özel durum nesnesi birden çok hataya karşılık geldiğinde yararlıdır. Bu durumda, nesnesi genellikle hatayla ilişkili özel hata kodunu içeren bir özelliğe sahiptir. Deyimdeki hata kodu özelliğini yalnızca bu yan tümce içinde işlemek istediğiniz belirli hatayı seçmek için kullanabilirsiniz `catch` .  
  
 Aşağıdaki örnek, ifadesini gösterir `catch` / `when` .

```csharp
try
{
    //Try statements.  
}
catch (Exception ex) when (ex.Message.Contains("404"))
{
    //Catch statements.
}
```  
  
```vb
Try  
    'Try statements.  
    Catch When Err = VBErr_ClassLoadException
    'Catch statements.
End Try  
```  
  
 Kullanıcı filtrelenmiş yan tümcesinin ifadesi herhangi bir şekilde kısıtlanmaz. Kullanıcı tarafından filtrelenen ifadenin yürütülmesi sırasında bir özel durum oluşursa, bu özel durum atılır ve filtre ifadesi yanlış olarak değerlendirilir. Bu durumda, ortak dil çalışma zamanı, geçerli özel durum için bir işleyici aramaya devam eder.  
  
## <a name="combine-the-specific-exception-and-the-user-filtered-clauses"></a>Belirli özel durumu ve kullanıcı filtrelenmiş yan tümceleri birleştirme  

 Bir `catch` ifade, hem belirli özel durumu hem de Kullanıcı tarafından filtrelenmiş yan tümceleri içerebilir. Çalışma zamanı, önce belirli özel durumu sınar. Belirli özel durum başarılı olursa, çalışma zamanı Kullanıcı filtresini yürütür. Genel filtre, sınıf filtresinde belirtilen değişkene bir başvuru içerebilir. İki filtre yan tümcelerinin sırasının geri çevrilmeyeceğini unutmayın.  
  
 Aşağıdaki örnek, **catch** deyimindeki belirli bir özel **durumu ve while anahtar sözcüğünü** kullanan kullanıcı filtrelenmiş yan tümceyi gösterir.  
  
```csharp
try
{
    //Try statements.  
}
catch (System.Net.Http.HttpRequestException ex) when (ex.Message.Contains("404"))
{
    //Catch statements.
}
```  
  
```vb
Try  
    'Try statements.
    Catch cle As ClassLoadException When cle.IsRecoverable()  
    'Catch statements.
End Try  
```  

## <a name="see-also"></a>Ayrıca bkz.

- [Özel durumlar](index.md)
