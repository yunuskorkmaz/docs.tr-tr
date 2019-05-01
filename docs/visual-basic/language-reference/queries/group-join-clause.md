---
title: Group Join Tümcesi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryGroupJoinIn
- vb.QueryGroupJoinOn
- vb.QueryGroupJoin
- vb.QueryGroupJoinInto
helpviewer_keywords:
- Group Join clause [Visual Basic]
- Group Join statement [Visual Basic]
- queries [Visual Basic], Group Join
ms.assetid: 37dbf79c-7b5c-421b-bbb7-dadfd2b92a1c
ms.openlocfilehash: 3da4ca2db299a65b2c0f1fa259bbaabe4f53aa33
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945320"
---
# <a name="group-join-clause-visual-basic"></a>Group Join Tümcesi (Visual Basic)
İki koleksiyonu tek bir hiyerarşik koleksiyon halinde birleştirir. Birleştirme işlemi anahtarların eşleşmesi temeline göre yapılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Group Join element [As type] In collection _  
  On key1 Equals key2 [ And key3 Equals key4 [... ] ] _  
  Into expressionList  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`element`|Gerekli. Denetim değişkeni birleştirilen koleksiyonu.|  
|`type`|İsteğe bağlı. Türünü `element`. Hayır ise `type` belirtilen türü `element` içinden gösterilen `collection`.|  
|`collection`|Gerekli. Sol tarafında koleksiyonu ile birleştirmek için koleksiyon `Group Join` işleci. A `Group Join` yan tümcesi iç içe geçirilemez içinde bir `Join` yan tümcesi veya başka bir `Group Join` yan tümcesi.|  
|`key1` `Equals` `key2`|Gerekli. Birleştirilen koleksiyonlar için anahtarları tanımlar. Kullanmalısınız `Equals` birleştirilen koleksiyonları'ndaki anahtarları Karşılaştırılacak işleci. Birleştirme koşulları kullanarak birleştirebilirsiniz `And` birden çok anahtar tanımlamak için işleci. `key1` Parametresi sol tarafındaki koleksiyondan olmalıdır `Join` işleci. `key2` Parametresi sağ alt tarafında koleksiyondan olmalıdır `Join` işleci.<br /><br /> Birleşim koşulunda kullanılan anahtarları koleksiyonundan birden fazla öğe içeren ifadeler olabilir. Ancak, her anahtar ifadesi yalnızca kendi ilgili koleksiyondaki öğeler içerebilir.|  
|`expressionList`|Gerekli. Grupları koleksiyonundan öğelerin nasıl toplanır tanımlayan bir veya daha fazla ifadeler. Gruplandırılmış sonuçlar için bir üye adını tanımlamak için kullanmak `Group` anahtar sözcüğü (`<alias> = Group`). Gruba uygulanacak toplama işlevleri de içerebilir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `Group Join` Yan tümcesi birleştirilen koleksiyonları anahtar değerlerinden eşleşmesi temeline göre iki koleksiyon birleştirir. Sonuçta elde edilen koleksiyon öğelerinin bir koleksiyonunu ilk koleksiyondan anahtar değeriyle eşleşen ikinci koleksiyondan başvuran bir üye içerebilir. İkinci koleksiyondan gruplandırılmış öğelerine uygulamak için toplama işlevleri de belirtebilirsiniz. Toplama işlevleri hakkında daha fazla bilgi için bkz. [Aggregate tümcesi](../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
 Örneğin, bir koleksiyon yöneticileri ve çalışanların koleksiyonunu düşünün. Her iki koleksiyon öğeleri belirli bir yöneticiye çalışanlar tanımlayan bir ManagerID özelliğine sahiptir. Sonuçta her Yöneticisi ve çalışan eşleşen ManagerID değere sahip bir birleştirme işlemi sonuçlarını içerir. Sonuçları bir `Group Join` işlem yöneticileri tam listesini içerebilir. Her manager sonucu belirli Yöneticisi için bir eşleşme olan çalışanlar listesini başvurulan bir üyeye sahip olması gerekir.  
  
 Kaynaklanan koleksiyonu bir `Group Join` işlemi tanımlanan koleksiyondan değerler herhangi bir birleşimini içerebilir `From` yan tümcesi ve tanımlanan ifadeleri `Into` yan tümcesi `Group Join` yan tümcesi. İçin geçerli ifadeler hakkında daha fazla bilgi için `Into` yan tümcesi bkz [Aggregate tümcesi](../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
 A `Group Join` işlemi sol tarafında belirtilen koleksiyondaki tüm sonuçları döndürecektir `Group Join` işleci. Birleştirilen koleksiyondaki herhangi bir eşleşme olsa bile bu geçerlidir. Bu benzer bir `LEFT OUTER JOIN` SQL.  
  
 Kullanabileceğiniz `Join` tek bir koleksiyon koleksiyonlara birleştirilecek yan tümcesi. Bunun eşdeğeri olan bir `INNER JOIN` SQL.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği iki koleksiyonu kullanarak birleştirir `Group Join` yan tümcesi.  
  
 [!code-vb[VbSimpleQuerySamples#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#14)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic'de LINQ'e giriş](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Sorgular](../../../visual-basic/language-reference/queries/index.md)
- [Select Yan Tümcesi](../../../visual-basic/language-reference/queries/select-clause.md)
- [From Yan Tümcesi](../../../visual-basic/language-reference/queries/from-clause.md)
- [Join Yan Tümcesi](../../../visual-basic/language-reference/queries/join-clause.md)
- [Where Yan Tümcesi](../../../visual-basic/language-reference/queries/where-clause.md)
- [Group By Yan Tümcesi](../../../visual-basic/language-reference/queries/group-by-clause.md)
