---
title: Join Yan Tümcesi
ms.date: 07/20/2015
f1_keywords:
- vb.QueryJoinIn
- vb.QueryJoin
- vb.QueryJoinOn
helpviewer_keywords:
- queries [Visual Basic], Join
- Join statement [Visual Basic]
- Join clause [Visual Basic]
ms.assetid: 6dd37936-b27c-4e00-98ad-154b23f4de64
ms.openlocfilehash: f73dc31bbbb9014a8a1a315de406c53fa58d1c65
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359780"
---
# <a name="join-clause-visual-basic"></a>Join Tümcesi (Visual Basic)

İki koleksiyonu tek bir koleksiyon halinde birleştirir. JOIN işlemi, eşleşen anahtarlara dayalıdır ve `Equals` işlecini kullanır.

## <a name="syntax"></a>Sözdizimi

```vb
Join element In collection _
  [ joinClause _ ]
  [ groupJoinClause ... _ ]
On key1 Equals key2 [ And key3 Equals key4 [... ]
```

## <a name="parts"></a>Bölümler

`element`Gerekli. Birleştirilen koleksiyonun denetim değişkeni.

`collection`  
Gereklidir. İşlecin sol tarafında tanımlanan koleksiyonla birleştirilecek koleksiyon `Join` . `Join`Yan tümce, başka bir `Join` yan tümce içinde veya yan tümcesinde iç içe olabilir `Group Join` .

`joinClause`  
İsteğe bağlı. `Join`Sorguyu daha da belirginleştirmek için bir veya daha fazla ek yan tümce.

`groupJoinClause`  
İsteğe bağlı. `Group Join`Sorguyu daha da belirginleştirmek için bir veya daha fazla ek yan tümce.

`key1` `Equals` `key2`  
Gereklidir. Katılmakta olan koleksiyonlar için anahtarları tanımlar. `Equals`Birleştirilecek koleksiyonlardan anahtarları karşılaştırmak için işlecini kullanmanız gerekir. `And`Birden çok anahtarı tanımlamak için işlecini kullanarak Birleştirme koşullarını birleştirebilirsiniz. `key1`işlecin sol tarafındaki koleksiyondan olmalıdır `Join` . `key2`işlecin sağ tarafındaki koleksiyondan olmalıdır `Join` .

JOIN koşulunda kullanılan anahtarlar, koleksiyondan birden fazla öğe içeren ifadeler olabilir. Ancak, her anahtar ifadesi yalnızca ilgili koleksiyonundan öğe içerebilir.

## <a name="remarks"></a>Açıklamalar

`Join`Yan tümcesi, katılmakta olan koleksiyonlardan eşleşen anahtar değerlerini temel alarak iki koleksiyonu birleştirir. Elde edilen koleksiyon, işlecin sol tarafında tanımlanan koleksiyondaki değerlerin herhangi bir birleşimini `Join` ve yan tümcesinde tanımlanan koleksiyonu içerebilir `Join` . Sorgu yalnızca işleç tarafından belirtilen koşulun `Equals` karşılandığı sonuçları döndürür. Bu, bir SQL ile eşdeğerdir `INNER JOIN` .

`Join`İki veya daha fazla koleksiyonu tek bir koleksiyonda birleştirmek için bir sorguda birden çok yan tümce kullanabilirsiniz.

Yan tümce olmadan koleksiyonları birleştirmek için örtük bir birleştirme gerçekleştirebilirsiniz `Join` . Bunu yapmak için, yan tümcesine birden çok yan tümce ekleyin `In` `From` ve `Where` JOIN için kullanmak istediğiniz anahtarları tanımlayan bir yan tümce belirtin.

`Group Join`Yan tümcesini, koleksiyonları tek bir hiyerarşik koleksiyonda birleştirmek için kullanabilirsiniz. Bu `LEFT OUTER JOIN` SQL içindeki gibidir.

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, bir müşteri listesini siparişleriyle birlikte birleştirmek için örtük bir birleştirme gerçekleştirir.

[!code-vb[VbSimpleQuerySamples#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#13)]

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, yan tümcesini kullanarak iki koleksiyonu birleştirir `Join` .

[!code-vb[VbSimpleQuerySamples#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples2.vb#12)]

Bu örnek aşağıdakine benzer bir çıktı oluşturacaktır:

`winlogon (968), Windows Logon`

`explorer (2424), File Explorer`

`cmd (5136), Command Window`

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, `Join` iki anahtar sütunu olan yan tümcesini kullanarak iki koleksiyonu birleştirir.

[!code-vb[VbSimpleQuerySamples#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples3.vb#17)]

Örnek aşağıdakine benzer bir çıktı oluşturacaktır:

`winlogon (968), Windows Logon, Priority = 13`

`cmd (700), Command Window, Priority = 8`

`explorer (2424), File Explorer, Priority = 8`

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic'de LINQ'e Giriş](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [Sorgular](index.md)
- [Select yan tümcesi](select-clause.md)
- [From yan tümcesi](from-clause.md)
- [Group Join Yan Tümcesi](group-join-clause.md)
- [WHERE yan tümcesi](where-clause.md)
