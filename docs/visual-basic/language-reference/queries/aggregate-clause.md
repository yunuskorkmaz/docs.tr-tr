---
title: Aggregate Tümcesi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryAggregateIn
- vb.QueryAggregate
- vb.QueryAggregateInto
helpviewer_keywords:
- Aggregate clause [Visual Basic]
- Aggregate statement [Visual Basic]
- queries [Visual Basic], Aggregate
ms.assetid: 1315a814-5db6-4077-b34b-b141e11cc0eb
ms.openlocfilehash: 1db4b7fdcf9c8a38c2c49eca9d874eccea90ab1d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604906"
---
# <a name="aggregate-clause-visual-basic"></a>Aggregate Tümcesi (Visual Basic)
Bir veya daha fazla toplama işlevleri bir koleksiyon için geçerlidir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Aggregate element [As type] In collection _  
  [, element2 [As type2] In collection2, [...]]  
  [ clause ]  
  Into expressionList  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`element`|Gerekli. Değişken koleksiyonu öğelerinde yineleme yapmak için kullanılır.|  
|`type`|İsteğe bağlı. Türü `element`. Tür belirtilmedi, türü `element` gelen olayla `collection`.|  
|`collection`|Gerekli. Üzerinde çalışılacak koleksiyonu ifade eder.|  
|`clause`|İsteğe bağlı. Bir veya daha fazla yan tümceleri, gibi sorgu bir `Where` aggregate tümcesi veya yan tümcelerini uygulamak için sorgu sonucu iyileştirmek için yan tümcesi.|  
|`expressionList`|Gerekli. Koleksiyona uygulamak için bir toplama işlevi tanımlayan bir veya daha fazla virgülle ayrılmış ifadeler. Sorgu sonucu için bir üye adı belirtmek için bir toplama işlevi için diğer ad uygulayabilirsiniz. Diğer ad sağlanırsa, toplama işlevinin adı kullanılır. Örnekler için bu konunun ilerleyen bölümlerinde toplama işlevleri hakkındaki bölüme bakın.|  
  
## <a name="remarks"></a>Açıklamalar  
 `Aggregate` Yan tümcesi, toplama işlevleri sorgularınızda dahil etmek için kullanılabilir. Toplama işlevleri değerleri kümesi üzerinde denetim ve hesaplamalar gerçekleştirmek ve tek bir değer döndürür. Hesaplanan değeri, sorgu sonuç türünün bir üyesi kullanarak erişebilirsiniz. Kullanabileceğiniz standart toplama işlevleri `All`, `Any`, `Average`, `Count`, `LongCount`, `Max`, `Min`, ve `Sum` işlevleri. Bu işlevler tanıdık SQL Toplamaların bilginiz geliştiriciler için. Bunlar, bu konunun aşağıdaki bölümde açıklanmıştır.  
  
 Bir toplama işlevinde sonucu sorgu sonucu sorgu sonucu türünde bir alan dahil edilir. Toplam değeri tutacak sorgu sonuç türü üyesi adını belirtmek toplama işlevi sonucu için bir diğer ad sağlayabilir. Diğer ad sağlanırsa, toplama işlevinin adı kullanılır.  
  
 `Aggregate` Yan tümcesi, bir sorgu başlayabilir veya ek bir yan tümcesi bir sorgu olarak dahil edilebilir. Varsa `Aggregate` yan tümcesi bir sorgu başlar, belirtilen toplama işlevinin sonucu olan bir tek değer sonuç `Into` yan tümcesi. Birden fazla toplama işlevi belirtilmişse `Into` yan tümcesi, sorgunun döndürdüğü her toplama işlevinde sonucunu başvurmak için ayrı bir özellik ile tek bir türü `Into` yan tümcesi. Varsa `Aggregate` yan tümcesi, ek bir yan tümcesi bir sorgu olarak eklenir, sorgu koleksiyonunda döndürülen türü her toplama işlevinde sonucunu başvurmak için ayrı bir özelliğe sahiptir `Into` yan tümcesi.  
  
## <a name="aggregate-functions"></a>Toplama İşlevleri  
 Aşağıdaki listede kullanılabilir standart toplama işlevleri açıklanmaktadır `Aggregate` yan tümcesi.  
  
|İşlev|Açıklama|  
|---|---|  
|`All`|Döndürür `true` koleksiyondaki tüm öğeleri belirtilen bir koşul; belirtecini karşılıyorsa döndürür `false`. Aşağıda bir örnek verilmiştir:<br /><br /> [!code-vb[VbSimpleQuerySamples#5](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_1.vb)]|  
|`Any`|Döndürür `true` herhangi bir öğe koleksiyonda belirtilen bir koşul; uymazsa döndürür `false`. Aşağıda bir örnek verilmiştir:<br /><br /> [!code-vb[VbSimpleQuerySamples#6](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_2.vb)]|  
|`Average`|Koleksiyon veya bir koleksiyondaki tüm öğeler için sağlanan hesaplar ifadesi içindeki tüm öğelerin ortalama hesaplar. Aşağıda bir örnek verilmiştir:<br /><br /> [!code-vb[VbSimpleQuerySamples#7](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_3.vb)]|  
|`Count`|Koleksiyondaki öğe sayısını sayar. İsteğe bağlı bir sağlayabilir `Boolean` yalnızca bir koşulu karşılıyor koleksiyondaki öğe sayısını ifade. Aşağıda bir örnek verilmiştir:<br /><br /> [!code-vb[VbSimpleQuerySamples#8](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_4.vb)]|  
|`Group`|Sonucu olarak gruplandırılır sorgu sonuçları başvurduğu bir `Group By` veya `Group Join` yan tümcesi. `Group` İşlevi, yalnızca geçerli `Into` yan tümcesinde bir `Group By` veya `Group Join` yan tümcesi. Daha fazla bilgi ve örnekler için bkz: [Grup By yan tümcesi](../../../visual-basic/language-reference/queries/group-by-clause.md) ve [Grup JOIN yan tümcesi](../../../visual-basic/language-reference/queries/group-join-clause.md).|  
|`LongCount`|Koleksiyondaki öğe sayısını sayar. İsteğe bağlı bir sağlayabilir `Boolean` yalnızca bir koşulu karşılıyor koleksiyondaki öğe sayısını ifade. Sonuç olarak döndüren bir `Long`. Bir örnek için bkz: `Count` toplama işlevi.|  
|`Max`|Koleksiyondan en büyük değeri hesaplar veya koleksiyondaki tüm öğeler için sağlanan bir ifadeyi hesaplar. Aşağıda bir örnek verilmiştir:<br /><br /> [!code-vb[VbSimpleQuerySamples#9](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_5.vb)]|  
|`Min`|En düşük değer koleksiyondan hesaplar veya koleksiyondaki tüm öğeler için sağlanan bir ifadeyi hesaplar. Aşağıda bir örnek verilmiştir:<br /><br /> [!code-vb[VbSimpleQuerySamples#10](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_6.vb)]|  
|`Sum`|Koleksiyondaki tüm öğelerin toplamı, hesaplar veya koleksiyondaki tüm öğeler için sağlanan bir ifadeyi hesaplar. Aşağıda bir örnek verilmiştir:<br /><br /> [!code-vb[VbSimpleQuerySamples#15](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_7.vb)]|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde nasıl kullanılacağını gösterir `Aggregate` toplama işlevleri bir sorgu sonucu uygulamak için yan tümcesi.  
  
 [!code-vb[VbSimpleQuerySamples#4](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_8.vb)]  
  
## <a name="creating-user-defined-aggregate-functions"></a>Kullanıcı tanımlı toplama işlevleri oluşturma  
 Kendi özel toplama işlevleri için genişletme yöntemleri ekleyerek sorgu ifadesinde dahil edebilirsiniz <xref:System.Collections.Generic.IEnumerable%601> türü. Özel yöntem, bir hesaplama veya toplama işlevi başvurmuş numaralandırılabilir toplama işlemi daha sonra gerçekleştirebilirsiniz. Uzantı yöntemleri hakkında daha fazla bilgi için bkz: [genişletme yöntemleri](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).  
  
 Örneğin, aşağıdaki kod örneğinde numaraları koleksiyonu ORTANCA değerini hesaplar özel bir toplama işlevi gösterir. İki aşırı `Median` genişletme yöntemi. İlk aşırı kabul, girdi olarak türünden bir koleksiyona `IEnumerable(Of Double)`. Varsa `Median` toplama işlevi için türünde bir sorgu alan adlı `Double`, bu yöntem çağrılır. İkinci aşırı yüklemesini `Median` yöntemi herhangi bir genel türü geçirilebilir. Genel aşırı yüklemesini `Median` yöntemi alır başvuran ikinci bir parametresi `Func(Of T, Double)` lambda ifadesi türü (koleksiyonundan) için bir değer türüne karşılık gelen değeri olarak proje `Double`. Ardından bir aşırı yüklemesini için ORTANCA değer hesaplama Temsilciler `Median` yöntemi. Lambda ifadeleri hakkında daha fazla bilgi için bkz: [Lambda ifadeleri](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 [!code-vb[VbSimpleQuerySamples#18](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_9.vb)]  
  
 Aşağıdaki kod örneğinde gösterildiği örnek arama sorguları `Median` türünde bir toplama işlevinde bir araya `Integer`ve bir koleksiyon türü `Double`. Çağıran sorgu `Median` toplama işlevi türü koleksiyonunu üzerinde `Double` aşırı yüklemesini çağırır `Median` türünü birtakım giriş olarak kabul yöntemi `Double`. Çağıran sorgu `Median` toplama işlevi türü koleksiyonunu üzerinde `Integer` genel aşırı yüklemesini çağırır `Median` yöntemi.  
  
 [!code-vb[VbSimpleQuerySamples#19](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_10.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic'de LINQ'e giriş](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Sorgular](../../../visual-basic/language-reference/queries/queries.md)  
 [Select Yan Tümcesi](../../../visual-basic/language-reference/queries/select-clause.md)  
 [From Yan Tümcesi](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Where Yan Tümcesi](../../../visual-basic/language-reference/queries/where-clause.md)  
 [Group By Yan Tümcesi](../../../visual-basic/language-reference/queries/group-by-clause.md)
