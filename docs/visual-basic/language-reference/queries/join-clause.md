---
title: "Join Tümcesi (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryJoinIn
- vb.QueryJoin
- vb.QueryJoinOn
helpviewer_keywords:
- queries [Visual Basic], Join
- Join statement [Visual Basic]
- Join clause [Visual Basic]
ms.assetid: 6dd37936-b27c-4e00-98ad-154b23f4de64
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2bb25c9dac8994e7f975539c1d036f0f0d9d239e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="join-clause-visual-basic"></a>Join Tümcesi (Visual Basic)
Tek bir koleksiyon iki koleksiyonlara birleştirir. Birleştirme işlemi anahtarları eşleşmesini temel alan ve kullandığı `Equals` işleci.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Join element In collection _  
  [ joinClause _ ]   
  [ groupJoinClause ... _ ]   
On key1 Equals key2 [ And key3 Equals key4 [... ]  
```  
  
## <a name="parts"></a>Bölümler  
 `element`  
 Gerekli. Denetim değişkeni birleştirilen koleksiyonu.  
  
 `collection`  
 Gerekli. Sol tarafında tanımlanan derlemesiyle birleştirmek için koleksiyon `Join` işleci. A `Join` yan tümcesi iç içe geçirilemez başka bir programda `Join` yan tümcesi veya bir `Group Join` yan tümcesi.  
  
 `joinClause`  
 İsteğe bağlı. Bir veya daha fazla ek `Join` daha da fazla yan tümceleri sorgu daraltın.  
  
 `groupJoinClause`  
 İsteğe bağlı. Bir veya daha fazla ek `Group Join` daha da fazla yan tümceleri sorgu daraltın.  
  
 `key1` `Equals` `key2`  
 Gerekli. Birleştirilen koleksiyonları tuşları tanımlar. Kullanmalısınız `Equals` birleştirilen koleksiyonları anahtarlarından Karşılaştırılacak işleci. Kullanarak birleştirme koşulları birleştirebilirsiniz `And` birden çok anahtar tanımlamak için işleci. `key1`sol tarafındaki koleksiyonundan olmalıdır `Join` işleci. `key2`sağ tarafında koleksiyonundan olmalıdır `Join` işleci.  
  
 Birleşim koşulu kullanılan anahtarları koleksiyonundan birden çok öğe içeren bir ifade olabilir. Bununla birlikte, her anahtar ifadesi yalnızca kendi ilgili koleksiyonundan öğeleri içerebilir.  
  
## <a name="remarks"></a>Açıklamalar  
 `Join` Yan tümcesi anahtar değerleri birleştirilen koleksiyonlardan eşleşmesini temel alan iki koleksiyon birleştirir. Sonuçta elde edilen koleksiyon sol tarafında tanımlanan koleksiyondan değerler herhangi bir birleşimini içerebilir `Join` işleci ve tanımlanan koleksiyonu `Join` yan tümcesi. Sorguyu yalnızca tarafından koşul için belirtilen sonuç döndürür `Equals` işleci karşılanıyorsa. Bu eşdeğer olan bir `INNER JOIN` SQL.  
  
 Birden çok kullanabilirsiniz `Join` tek bir koleksiyon iki veya daha fazla koleksiyonlara katılmak için bir sorgu yan tümcelerinde.  
  
 Koleksiyonları olmadan birleştirmek için örtük bir birleşim gerçekleştirebilirsiniz `Join` yan tümcesi. Bunu yapmak için birden çok dahil `In` yan tümcelerinde, `From` yan tümcesi ve belirtin bir `Where` birleştirme için kullanmak istediğiniz anahtarları tanımlayan yan tümcesi.  
  
 Kullanabileceğiniz `Group Join` tek hiyerarşik derlemeye koleksiyonları birleştirme yan tümcesi. Bu benzer bir `LEFT OUTER JOIN` SQL.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde, emirleri ile müşteriler listesini birleştirmek için örtük bir birleştirme gerçekleştirir.  
  
 [!code-vb[VbSimpleQuerySamples#13](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/join-clause_1.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği iki koleksiyonları kullanarak birleştirir `Join` yan tümcesi.  
  
 [!code-vb[VbSimpleQuerySamples#12](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/join-clause_2.vb)]  
  
 Bu örnek, aşağıdakine benzer bir çıktı üretir:  
  
 `winlogon (968), Windows Logon`  
  
 `explorer (2424), File Explorer`  
  
 `cmd (5136), Command Window`  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği iki koleksiyonları kullanarak birleştirir `Join` yan tümcesiyle birlikte iki anahtar sütun.  
  
 [!code-vb[VbSimpleQuerySamples#17](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/join-clause_3.vb)]  
  
 Örneğin, aşağıdakine benzer bir çıktı üretir:  
  
 `winlogon (968), Windows Logon, Priority = 13`  
  
 `cmd (700), Command Window, Priority = 8`  
  
 `explorer (2424), File Explorer, Priority = 8`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic'de LINQ'e giriş](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Sorguları](../../../visual-basic/language-reference/queries/queries.md)  
 [Select tümcesi](../../../visual-basic/language-reference/queries/select-clause.md)  
 [From yan tümcesi](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Group Join tümcesi](../../../visual-basic/language-reference/queries/group-join-clause.md)  
 [Burada yan tümcesi](../../../visual-basic/language-reference/queries/where-clause.md)
