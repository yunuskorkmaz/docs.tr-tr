---
title: Group Join Tümcesi
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
ms.openlocfilehash: 0546c86322663ce6c56a89e63311d0f02f88cfe4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346849"
---
# <a name="group-join-clause-visual-basic"></a>Group Join Tümcesi (Visual Basic)
İki koleksiyonu tek bir hiyerarşik koleksiyonda birleştirir. JOIN işlemi, eşleşen anahtarları temel alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
Group Join element [As type] In collection _  
  On key1 Equals key2 [ And key3 Equals key4 [... ] ] _  
  Into expressionList  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`element`|Gerekli. Birleştirilen koleksiyonun denetim değişkeni.|  
|`type`|İsteğe bağlı. `element` öğesinin türü. `type` belirtilmemişse, `element` türü `collection`algılanır.|  
|`collection`|Gerekli. `Group Join` işlecinin sol tarafındaki koleksiyonla birleştirilecek koleksiyon. `Group Join` yan tümcesi, bir `Join` yan tümcesinde veya başka bir `Group Join` yan tümcesinde iç içe olabilir.|  
|`key1` `Equals` `key2`|Gerekli. Katılmakta olan koleksiyonlar için anahtarları tanımlar. Birleştirilecek koleksiyonlardan anahtarları karşılaştırmak için `Equals` işlecini kullanmanız gerekir. Birden çok anahtarı belirlemek için `And` işlecini kullanarak Birleştirme koşullarını birleştirebilirsiniz. `key1` parametresi, `Join` işlecinin sol tarafındaki koleksiyondan olmalıdır. `key2` parametresi, `Join` işlecinin sağ tarafındaki koleksiyondan olmalıdır.<br /><br /> JOIN koşulunda kullanılan anahtarlar, koleksiyondan birden fazla öğe içeren ifadeler olabilir. Ancak, her anahtar ifadesi yalnızca ilgili koleksiyonundan öğe içerebilir.|  
|`expressionList`|Gerekli. Koleksiyondan öğe gruplarının nasıl toplanacağına ilişkin bir veya daha fazla ifade. Gruplanmış sonuçların üye adını belirlemek için `Group` anahtar sözcüğünü kullanın (`<alias> = Group`). Gruba uygulanacak toplama işlevlerini de ekleyebilirsiniz.|  
  
## <a name="remarks"></a>Açıklamalar  
 `Group Join` yan tümcesi, katılmakta olan koleksiyonlardan eşleşen anahtar değerlerini temel alarak iki koleksiyonu birleştirir. Elde edilen koleksiyon, ikinci koleksiyondaki bir öğe koleksiyonuna başvuran ve ilk koleksiyondaki anahtar değeriyle eşleşen bir üye içerebilir. İkinci koleksiyondaki gruplanmış öğelere uygulanacak toplama işlevlerini de belirtebilirsiniz. Toplama işlevleri hakkında bilgi için bkz. [Aggregate yan tümcesi](../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
 Örneğin, bir grup yönetici ve bir çalışan koleksiyonu gibi düşünün. Her iki koleksiyonun öğesi, belirli bir yöneticiye rapor veren çalışanları tanımlayan bir ManagerID özelliğine sahiptir. Bir JOIN işleminin sonuçları, eşleşen bir ManagerID değeri olan her yönetici ve çalışan için sonuç içerir. `Group Join` bir işlemin sonuçları, yöneticilerin tüm listesini içerir. Her yöneticinin sonucu, belirli bir yönetici için eşleşme olan çalışanların listesine başvuran bir üyeye sahip olur.  
  
 `Group Join` bir işlemden kaynaklanan koleksiyon, `From` yan tümcesinde tanımlanan koleksiyondan ve `Group Join` yan tümcesinin `Into` yan tümcesinde tanımlanan ifadelerde herhangi bir değer birleşimini içerebilir. `Into` yan tümcesi için geçerli ifadeler hakkında daha fazla bilgi için bkz. [Aggregate yan tümcesi](../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
 Bir `Group Join` işlemi, `Group Join` işlecinin sol tarafında tanımlanan koleksiyondaki tüm sonuçları döndürür. Bu, toplanmakta olan koleksiyonda eşleşme olmaması durumunda da geçerlidir. Bu SQL 'de bir `LEFT OUTER JOIN` gibidir.  
  
 Koleksiyonları tek bir koleksiyonda birleştirmek için `Join` yan tümcesini kullanabilirsiniz. Bu, SQL 'deki bir `INNER JOIN` eşdeğerdir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, `Group Join` yan tümcesini kullanarak iki koleksiyonu birleştirir.  
  
 [!code-vb[VbSimpleQuerySamples#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#14)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic LINQ 'e giriş](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Sorgular](../../../visual-basic/language-reference/queries/index.md)
- [Select Yan Tümcesi](../../../visual-basic/language-reference/queries/select-clause.md)
- [From Yan Tümcesi](../../../visual-basic/language-reference/queries/from-clause.md)
- [Join Yan Tümcesi](../../../visual-basic/language-reference/queries/join-clause.md)
- [Where Yan Tümcesi](../../../visual-basic/language-reference/queries/where-clause.md)
- [Group By Yan Tümcesi](../../../visual-basic/language-reference/queries/group-by-clause.md)
