---
title: Group Join Yan Tümcesi
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
ms.openlocfilehash: 8d5f3ec80cb39825a3a283907d614b9be28e6e91
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90869911"
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
|`element`|Gereklidir. Birleştirilen koleksiyonun denetim değişkeni.|  
|`type`|İsteğe bağlı. Türü `element` . Hayır `type` belirtilmemişse, türü `element` öğesinden çıkarsanamıyor `collection` .|  
|`collection`|Gereklidir. İşlecin sol tarafındaki koleksiyonla birleştirilecek koleksiyon `Group Join` . `Group Join`Yan tümce bir `Join` yan tümce veya başka bir yan tümce içinde iç içe olabilir `Group Join` .|  
|`key1` `Equals` `key2`|Gereklidir. Katılmakta olan koleksiyonlar için anahtarları tanımlar. `Equals`Birleştirilecek koleksiyonlardan anahtarları karşılaştırmak için işlecini kullanmanız gerekir. `And`Birden çok anahtarı tanımlamak için işlecini kullanarak Birleştirme koşullarını birleştirebilirsiniz. `key1`Parametrenin, işlecin sol tarafındaki koleksiyondan olması gerekir `Join` . `key2`Parametrenin, işlecin sağ tarafındaki koleksiyondan olması gerekir `Join` .<br /><br /> JOIN koşulunda kullanılan anahtarlar, koleksiyondan birden fazla öğe içeren ifadeler olabilir. Ancak, her anahtar ifadesi yalnızca ilgili koleksiyonundan öğe içerebilir.|  
|`expressionList`|Gereklidir. Koleksiyondan öğe gruplarının nasıl toplanacağına ilişkin bir veya daha fazla ifade. Gruplanmış sonuçların üye adını belirlemek için `Group` () anahtar sözcüğünü kullanın `<alias> = Group` . Gruba uygulanacak toplama işlevlerini de ekleyebilirsiniz.|  
  
## <a name="remarks"></a>Açıklamalar  

 `Group Join`Yan tümcesi, katılmakta olan koleksiyonlardan eşleşen anahtar değerlerini temel alarak iki koleksiyonu birleştirir. Elde edilen koleksiyon, ikinci koleksiyondaki bir öğe koleksiyonuna başvuran ve ilk koleksiyondaki anahtar değeriyle eşleşen bir üye içerebilir. İkinci koleksiyondaki gruplanmış öğelere uygulanacak toplama işlevlerini de belirtebilirsiniz. Toplama işlevleri hakkında bilgi için bkz. [Aggregate yan tümcesi](aggregate-clause.md).  
  
 Örneğin, bir grup yönetici ve bir çalışan koleksiyonu gibi düşünün. Her iki koleksiyonun öğesi, belirli bir yöneticiye rapor veren çalışanları tanımlayan bir ManagerID özelliğine sahiptir. Bir JOIN işleminin sonuçları, eşleşen bir ManagerID değeri olan her yönetici ve çalışan için sonuç içerir. Bir işlemin sonuçları, `Group Join` yöneticilerin tüm listesini içerir. Her yöneticinin sonucu, belirli bir yönetici için eşleşme olan çalışanların listesine başvuran bir üyeye sahip olur.  
  
 Bir işlemden kaynaklanan koleksiyon, `Group Join` yan tümcelerinde tanımlanan koleksiyondan `From` ve yan tümce içinde tanımlanan ifadelerde herhangi bir değer birleşimini içerebilir `Into` `Group Join` . Yan tümce için geçerli ifadeler hakkında daha fazla bilgi için `Into` bkz. [Aggregate yan tümcesi](aggregate-clause.md).  
  
 Bir `Group Join` işlem, işlecin sol tarafında tanımlanan koleksiyondaki tüm sonuçları döndürür `Group Join` . Bu, toplanmakta olan koleksiyonda eşleşme olmaması durumunda da geçerlidir. Bu `LEFT OUTER JOIN` SQL içindeki gibidir.  
  
 `Join`Yan tümcesini kullanarak koleksiyonları tek bir koleksiyon içinde birleştirebilirsiniz. Bu, bir SQL ile eşdeğerdir `INNER JOIN` .  
  
## <a name="example"></a>Örnek  

 Aşağıdaki kod örneği, yan tümcesini kullanarak iki koleksiyonu birleştirir `Group Join` .  
  
 [!code-vb[VbSimpleQuerySamples#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#14)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic'de LINQ'e Giriş](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [Sorgular](index.md)
- [Select yan tümcesi](select-clause.md)
- [From yan tümcesi](from-clause.md)
- [JOIN yan tümcesi](join-clause.md)
- [WHERE yan tümcesi](where-clause.md)
- [Group By Yan Tümcesi](group-by-clause.md)
