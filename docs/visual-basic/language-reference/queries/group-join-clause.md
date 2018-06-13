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
ms.openlocfilehash: 094281b0afb34451ae8539e4eb967043b21d379c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604763"
---
# <a name="group-join-clause-visual-basic"></a>Group Join Tümcesi (Visual Basic)
Tek bir hiyerarşik koleksiyon iki koleksiyonlara birleştirir. Birleştirme işlemi eşleşen anahtarlarla temel alır.  
  
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
|`type`|İsteğe bağlı. Türü `element`. Öyle değilse `type` belirtilirse, türü `element` gelen olayla `collection`.|  
|`collection`|Gerekli. Sol tarafında koleksiyonu ile birleştirmek için koleksiyon `Group Join` işleci. A `Group Join` yan tümcesi iç içe geçirilemez içinde bir `Join` yan tümcesi veya başka bir `Group Join` yan tümcesi.|  
|`key1` `Equals` `key2`|Gerekli. Birleştirilen koleksiyonları tuşları tanımlar. Kullanmalısınız `Equals` birleştirilen koleksiyonları anahtarlarından Karşılaştırılacak işleci. Kullanarak birleştirme koşulları birleştirebilirsiniz `And` birden çok anahtar tanımlamak için işleci. `key1` Parametresi sol tarafındaki koleksiyonundan olmalıdır `Join` işleci. `key2` Parametresi sağ tarafında koleksiyonundan olmalıdır `Join` işleci.<br /><br /> Birleşim koşulu kullanılan anahtarları koleksiyonundan birden çok öğe içeren bir ifade olabilir. Bununla birlikte, her anahtar ifadesi yalnızca kendi ilgili koleksiyonundan öğeleri içerebilir.|  
|`expressionList`|Gerekli. Koleksiyondaki öğelerin grupları nasıl toplanır tanımlayan bir veya daha fazla ifadeler. Gruplandırılmış sonuçlar için bir üye adı tanımlamak için kullanmak `Group` anahtar sözcüğü (`<alias> = Group`). Gruba uygulamak için toplama işlevleri de içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `Group Join` Yan tümcesi anahtar değerleri birleştirilen koleksiyonlardan eşleşmesini temel alan iki koleksiyon birleştirir. Sonuçta elde edilen koleksiyon öğe koleksiyonunu ilk koleksiyonundan anahtar değeri ile eşleşecek ikinci koleksiyondan başvuruda bulunan bir üye içerebilir. İkinci koleksiyondan gruplandırılmış öğelerine uygulamak için toplama işlevleri de belirtebilirsiniz. Toplama işlevleri hakkında daha fazla bilgi için bkz: [Aggregate tümcesi](../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
 Örneğin, bir koleksiyon yöneticileri ve çalışanlar koleksiyonu düşünün. Her iki koleksiyon öğeleri belirli bir yöneticiye çalışanlar tanımlayan bir ManagerID özelliği vardır. Bir birleştirme işlemi sonuçlarından her Yöneticisi ve çalışan eşleşen ManagerID değere sahip bir sonuç içerecektir. Sonuçları bir `Group Join` işlem yöneticileri tam listesi içerebilir. Her bir Yöneticisi sonucu belirli Yöneticisi için bir eşleşme olan çalışanların listesini başvurulan üyesi gerekir.  
  
 Kaynaklanan koleksiyonu bir `Group Join` işlemi tanımlanan koleksiyondan değerler herhangi bir birleşimini içerebilir `From` yan tümcesi ve tanımlanan ifadeleri `Into` yan tümcesi `Group Join` yan tümcesi. İçin geçerli ifadeler hakkında daha fazla bilgi için `Into` yan tümcesi, bkz: [Aggregate tümcesi](../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
 A `Group Join` işlemi sol tarafında tanımlanan koleksiyonundan tüm sonuçları döndürecektir `Group Join` işleci. Birleştirilen koleksiyondaki herhangi bir eşleşme olsa bile bu geçerlidir. Bu benzer bir `LEFT OUTER JOIN` SQL.  
  
 Kullanabileceğiniz `Join` tek bir koleksiyon koleksiyonlara birleştirme yan tümcesi. Bu eşdeğer olan bir `INNER JOIN` SQL.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği iki koleksiyonları kullanarak birleştirir `Group Join` yan tümcesi.  
  
 [!code-vb[VbSimpleQuerySamples#14](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/group-join-clause_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic'de LINQ'e giriş](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Sorgular](../../../visual-basic/language-reference/queries/queries.md)  
 [Select Yan Tümcesi](../../../visual-basic/language-reference/queries/select-clause.md)  
 [From Yan Tümcesi](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Join Yan Tümcesi](../../../visual-basic/language-reference/queries/join-clause.md)  
 [Where Yan Tümcesi](../../../visual-basic/language-reference/queries/where-clause.md)  
 [Group By Yan Tümcesi](../../../visual-basic/language-reference/queries/group-by-clause.md)
