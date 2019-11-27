---
title: Aggregate Tümcesi
ms.date: 08/28/2018
f1_keywords:
- vb.QueryAggregateIn
- vb.QueryAggregate
- vb.QueryAggregateInto
helpviewer_keywords:
- Aggregate clause [Visual Basic]
- Aggregate statement [Visual Basic]
- queries [Visual Basic], Aggregate
ms.assetid: 1315a814-5db6-4077-b34b-b141e11cc0eb
ms.openlocfilehash: 5aa4b9afea4b6b26b853d4f4f6d4c8db08554e19
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350878"
---
# <a name="aggregate-clause-visual-basic"></a>Aggregate Tümcesi (Visual Basic)
Bir koleksiyona bir veya daha fazla toplama işlevi uygular.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
Aggregate element [As type] In collection _  
  [, element2 [As type2] In collection2, [...]]  
  [ clause ]  
  Into expressionList  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`element`|Gerekli. Koleksiyon öğeleri boyunca yinelemek için kullanılan değişken.|  
|`type`|İsteğe bağlı. `element` öğesinin türü. Hiçbir tür belirtilmemişse, `element` türü `collection`algılanır.|  
|`collection`|Gerekli. Üzerinde çalışılacak koleksiyona başvurur.|  
|`clause`|İsteğe bağlı. Toplama yan tümcesini veya yan tümceleri uygulamak üzere sorgu sonucunu daraltmak için bir `Where` yan tümcesi gibi bir veya daha fazla sorgu yan tümcesi.|  
|`expressionList`|Gerekli. Koleksiyona uygulanacak bir toplama işlevini tanımlayan bir veya daha fazla virgülle ayrılmış ifade. Sorgu sonucu için bir üye adı belirtmek üzere bir toplama işlevine bir diğer ad uygulayabilirsiniz. Diğer ad sağlanmazsa, toplama işlevinin adı kullanılır. Örnekler için, bu konunun ilerleyen kısımlarında bulunan toplama işlevleri hakkında bölümüne bakın.|  
  
## <a name="remarks"></a>Açıklamalar  
 `Aggregate` yan tümcesi, Sorgularınızdaki toplama işlevlerini eklemek için kullanılabilir. Toplama işlevleri, bir değerler kümesi üzerinde denetim ve hesaplamalar gerçekleştirir ve tek bir değer döndürür. Sorgu sonuç türünün bir üyesini kullanarak hesaplanan değere erişebilirsiniz. Kullanabileceğiniz standart toplama işlevleri `All`, `Any`, `Average`, `Count`, `LongCount`, `Max`, `Min`ve `Sum` işlevleridir. Bu işlevler, SQL 'deki toplamalara alışkın olan geliştiricilere tanıdık gelecektir. Bunlar, bu konunun aşağıdaki bölümünde açıklanmaktadır.  
  
 Toplama işlevinin sonucu sorgu sonuç türünün bir alanı olarak sorgu sonucuna dahil edilir. Toplama işlevi sonucu için, toplam değeri tutacak sorgu sonuç türü üyesinin adını belirtmek üzere bir diğer ad sağlayabilirsiniz. Diğer ad sağlanmazsa, toplama işlevinin adı kullanılır.  
  
 `Aggregate` yan tümcesi bir sorgu başlatabilir veya bir sorguya ek bir yan tümce olarak eklenebilir. `Aggregate` yan tümcesi bir sorgu başlıyorsa, sonuç, `Into` yan tümcesinde belirtilen toplama işlevinin sonucu olan tek bir değerdir. `Into` yan tümcesinde birden fazla toplama işlevi belirtilmişse, sorgu, `Into` yan tümcesindeki her toplama işlevinin sonucuna başvurmak için ayrı bir özelliği olan tek bir tür döndürür. `Aggregate` yan tümcesi bir sorguya ek bir yan tümce olarak dahil edildiğinde, sorgu koleksiyonunda döndürülen türün, `Into` yan tümcesindeki her toplama işlevinin sonucuna başvurması için ayrı bir özelliği olacaktır.  
  
## <a name="aggregate-functions"></a>Toplama İşlevleri

Aşağıdakiler `Aggregate` yan tümcesiyle kullanılabilen standart toplama işlevleridir.  
  
### <a name="all"></a>Tümü

Koleksiyondaki tüm öğelerin belirtilen bir koşulu karşılaması durumunda `true` döndürür; Aksi takdirde `false`döndürür. Aşağıda bir örnek verilmiştir:

 [!code-vb[VbSimpleQuerySamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#5)]

### <a name="any"></a>Tümü

Koleksiyondaki herhangi bir öğe belirtilen koşulu karşılıyorsa `true` döndürür; Aksi takdirde `false`döndürür. Aşağıda bir örnek verilmiştir:

 [!code-vb[VbSimpleQuerySamples#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#6)]

### <a name="average"></a>Ortalama

Koleksiyondaki tüm öğelerin ortalamasını hesaplar veya koleksiyondaki tüm öğeler için sağlanan bir ifadeyi hesaplar. Aşağıda bir örnek verilmiştir:

 [!code-vb[VbSimpleQuerySamples#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#7)]

### <a name="count"></a>Sayı

Koleksiyondaki öğelerin sayısını sayar. Koleksiyonda yalnızca bir koşulu karşılayan öğelerin sayısını saymak için isteğe bağlı bir `Boolean` ifadesi sağlayabilirsiniz. Aşağıda bir örnek verilmiştir:

 [!code-vb[VbSimpleQuerySamples#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#8)]

### <a name="group"></a>Grup

Bir `Group By` veya `Group Join` yan tümcesinin sonucu olarak gruplandırılan sorgu sonuçlarının başvurduğu anlamına gelir. `Group` işlevi yalnızca bir `Group By` veya `Group Join` yan tümcesinin `Into` yan tümcesinde geçerlidir. Daha fazla bilgi ve örnek için bkz. [Group by yan tümcesi](../../../visual-basic/language-reference/queries/group-by-clause.md) ve [Group JOIN yan tümcesi](../../../visual-basic/language-reference/queries/group-join-clause.md).

### <a name="longcount"></a>LongCount

Koleksiyondaki öğelerin sayısını sayar. Koleksiyonda yalnızca bir koşulu karşılayan öğelerin sayısını saymak için isteğe bağlı bir `Boolean` ifadesi sağlayabilirsiniz. `Long`sonucunu döndürür. Bir örnek için `Count` toplama işlevine bakın.

### <a name="max"></a>Maks

Koleksiyondaki maksimum değeri hesaplar veya koleksiyondaki tüm öğeler için sağlanan bir ifadeyi hesaplar. Aşağıda bir örnek verilmiştir:

 [!code-vb[VbSimpleQuerySamples#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#9)]

### <a name="min"></a>Min

Koleksiyondaki en küçük değeri hesaplar veya koleksiyondaki tüm öğeler için sağlanan bir ifadeyi hesaplar. Aşağıda bir örnek verilmiştir:

 [!code-vb[VbSimpleQuerySamples#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#10)]

### <a name="sum"></a>TOPLA

Koleksiyondaki tüm öğelerin toplamını hesaplar veya koleksiyondaki tüm öğeler için sağlanan bir ifadeyi hesaplar. Aşağıda bir örnek verilmiştir:

 [!code-vb[VbSimpleQuerySamples#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#15)]

## <a name="example"></a>Örnek  

Aşağıdaki örnek, bir sorgu sonucuna toplama işlevleri uygulamak için `Aggregate` yan tümcesinin nasıl kullanılacağını gösterir.  
  
 [!code-vb[VbSimpleQuerySamples#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#4)]  
  
## <a name="creating-user-defined-aggregate-functions"></a>Kullanıcı tanımlı toplama Işlevleri oluşturma

 <xref:System.Collections.Generic.IEnumerable%601> türüne uzantı yöntemleri ekleyerek kendi özel toplama işlevlerinizi bir sorgu ifadesine dahil edebilirsiniz. Özel yönteminiz, toplama işlevinizin başvurduğu sıralanabilir koleksiyonda bir hesaplama veya işlem gerçekleştirebilir. Uzantı yöntemleri hakkında daha fazla bilgi için bkz. [Uzantı yöntemleri](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).  
  
 Örneğin, aşağıdaki örnek bir sayı koleksiyonunun ortanca değerini hesaplayan özel bir toplama işlevi gösterir. `Median` uzantısı yönteminin iki aşırı yüklemesi vardır. İlk aşırı yükleme giriş olarak, `IEnumerable(Of Double)`türünde bir koleksiyon kabul eder. `Double`türündeki bir sorgu alanı için `Median` toplama işlevi çağrılırsa, bu yöntem çağrılır. `Median` yönteminin ikinci aşırı yüklemesi herhangi bir genel tür geçirilebilir. `Median` yönteminin genel aşırı yüklemesi, `Func(Of T, Double)` lambda ifadesine başvuran ikinci bir parametre alır (bir koleksiyondan), karşılık gelen `Double`türü olarak bir değer proje. Daha sonra ortanca değer hesaplamasını `Median` yönteminin diğer aşırı yüküne devreder. Lambda ifadeleri hakkında daha fazla bilgi için bkz. [lambda ifadeleri](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 [!code-vb[VbSimpleQuerySamples#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/UserDefinedAggregates.vb#18)]  
  
 Aşağıdaki örnek, `Integer`türünde bir koleksiyon üzerinde `Median` toplama işlevini çağıran örnek sorguları ve `Double`türünde bir koleksiyonu gösterir. `Double` türü koleksiyonundaki `Median` toplama işlevini çağıran sorgu, giriş olarak kabul eden `Median` yönteminin `Double`bir koleksiyon olan aşırı yüklemesini çağırır. `Integer` türü koleksiyonundaki `Median` toplama işlevini çağıran sorgu `Median` yönteminin genel aşırı yüklemesini çağırır.  
  
 [!code-vb[VbSimpleQuerySamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/UserDefinedAggregates.vb#19)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic LINQ 'e giriş](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Sorgular](../../../visual-basic/language-reference/queries/index.md)
- [Select Yan Tümcesi](../../../visual-basic/language-reference/queries/select-clause.md)
- [From Yan Tümcesi](../../../visual-basic/language-reference/queries/from-clause.md)
- [Where Yan Tümcesi](../../../visual-basic/language-reference/queries/where-clause.md)
- [Group By Yan Tümcesi](../../../visual-basic/language-reference/queries/group-by-clause.md)
