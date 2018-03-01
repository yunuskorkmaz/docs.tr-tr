---
title: "Let Tümcesi (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryLet
helpviewer_keywords:
- queries [Visual Basic], Let
- Let clause [Visual Basic]
- Let statement [Visual Basic]
ms.assetid: 981aa516-16eb-4c53-b1f1-5aa3e82f316e
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 70e47517a62f58dcababd31c26277417b62eab66
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="let-clause-visual-basic"></a>Let Tümcesi (Visual Basic)
Bir değeri hesaplar ve sorgu içinde yeni bir değişkene atar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Let variable = expression [, ...]  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`variable`|Gerekli. Sağlanan ifade sonuçlarını başvurmak için kullanılan bir diğer ad.|  
|`expression`|Gerekli. Değerlendirilecek ve belirtilen değişkenine atanan bir ifade.|  
  
## <a name="remarks"></a>Açıklamalar  
 `Let` Yan tümcesi, her biri için değerleri sorgu sonucu ve bir diğer ad kullanarak başvuru işlem olanak tanır. Diğer ad diğer yan tümcelerinde gibi kullanılabilir `Where` yan tümcesi. `Let` Yan tümcesi, çünkü sorguda bir ifade yan tümcesi için diğer ad belirtin ve ifade yan tümcesinde kullanılan her zaman diğer adı yerine okunması daha kolay olan bir sorgu deyimi oluşturmanıza olanak sağlar.  
  
 Herhangi bir sayıda içerebilir `variable` ve `expression` atamalarını `Let` yan tümcesi. Her bir atama virgülle (,) ayırın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde `Let` yüzde 10 indirim ürünlerine hesaplamak için yan tümcesi.  
  
 [!code-vb[VbSimpleQuerySamples#16](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/let-clause_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic'de LINQ'e giriş](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Sorguları](../../../visual-basic/language-reference/queries/queries.md)  
 [Select tümcesi](../../../visual-basic/language-reference/queries/select-clause.md)  
 [From yan tümcesi](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Burada yan tümcesi](../../../visual-basic/language-reference/queries/where-clause.md)
