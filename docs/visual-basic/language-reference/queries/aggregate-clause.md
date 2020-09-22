---
title: Aggregate Yan Tümcesi
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
ms.openlocfilehash: be2e401c7931b2637c14a3ea3b742a2c09917939
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90869992"
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
|`element`|Gereklidir. Koleksiyon öğeleri boyunca yinelemek için kullanılan değişken.|  
|`type`|İsteğe bağlı. Türü `element` . Hiçbir tür belirtilmemişse, türü `element` öğesinden çıkarsanamıyor `collection` .|  
|`collection`|Gereklidir. Üzerinde çalışılacak koleksiyona başvurur.|  
|`clause`|İsteğe bağlı. `Where`Toplama yan tümcesini veya yan tümceleri uygulamak üzere sorgu sonucunu daraltmak için bir yan tümce gibi bir veya daha fazla sorgu yan tümcesi.|  
|`expressionList`|Gereklidir. Koleksiyona uygulanacak bir toplama işlevini tanımlayan bir veya daha fazla virgülle ayrılmış ifade. Sorgu sonucu için bir üye adı belirtmek üzere bir toplama işlevine bir diğer ad uygulayabilirsiniz. Diğer ad sağlanmazsa, toplama işlevinin adı kullanılır. Örnekler için, bu konunun ilerleyen kısımlarında bulunan toplama işlevleri hakkında bölümüne bakın.|  
  
## <a name="remarks"></a>Açıklamalar  

 `Aggregate`Yan tümce, Sorgularınızdaki toplama işlevlerini dahil etmek için kullanılabilir. Toplama işlevleri, bir değerler kümesi üzerinde denetim ve hesaplamalar gerçekleştirir ve tek bir değer döndürür. Sorgu sonuç türünün bir üyesini kullanarak hesaplanan değere erişebilirsiniz. Kullanabileceğiniz standart toplama işlevleri,,,,,, `All` `Any` `Average` `Count` `LongCount` `Max` `Min` , ve `Sum` işlevleridir. Bu işlevler, SQL 'deki toplamalara alışkın olan geliştiricilere tanıdık gelecektir. Bunlar, bu konunun aşağıdaki bölümünde açıklanmaktadır.  
  
 Toplama işlevinin sonucu sorgu sonuç türünün bir alanı olarak sorgu sonucuna dahil edilir. Toplama işlevi sonucu için, toplam değeri tutacak sorgu sonuç türü üyesinin adını belirtmek üzere bir diğer ad sağlayabilirsiniz. Diğer ad sağlanmazsa, toplama işlevinin adı kullanılır.  
  
 `Aggregate`Yan tümce bir sorgu başlatabilir veya bir sorguya ek bir yan tümce olarak eklenebilir. `Aggregate`Yan tümce bir sorgu başlıyorsa, sonuç, yan tümcesinde belirtilen toplama işlevinin sonucu olan tek bir değerdir `Into` . Yan tümcesinde birden fazla toplama işlevi belirtilmişse `Into` , sorgu, yan tümcesindeki her toplama işlevinin sonucuna başvurmak için ayrı bir özelliği olan tek bir tür döndürür `Into` . `Aggregate`Yan tümce bir sorguya ek bir yan tümce olarak dahil edildiğinde, sorgu koleksiyonunda döndürülen tür, yan tümcesindeki her toplama işlevinin sonucuna başvuracak ayrı bir özelliğe sahip olur `Into` .  
  
## <a name="aggregate-functions"></a>Toplama İşlevleri

Aşağıdaki, yan tümcesiyle kullanılabilen standart toplama işlevleridir `Aggregate` .  
  
### <a name="all"></a>Tümü

`true`Koleksiyondaki tüm öğelerin belirtilen koşulu karşılayıp karşılamadığını döndürür; Aksi takdirde döndürür `false` . Aşağıda bir örnek verilmiştir:

 [!code-vb[VbSimpleQuerySamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#5)]

### <a name="any"></a>Herhangi biri

`true`Koleksiyondaki herhangi bir öğenin belirtilen koşulu karşılayıp karşılamadığını döndürür; Aksi takdirde döndürür `false` . Aşağıda bir örnek verilmiştir:

 [!code-vb[VbSimpleQuerySamples#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#6)]

### <a name="average"></a>Ortalama

Koleksiyondaki tüm öğelerin ortalamasını hesaplar veya koleksiyondaki tüm öğeler için sağlanan bir ifadeyi hesaplar. Aşağıda bir örnek verilmiştir:

 [!code-vb[VbSimpleQuerySamples#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#7)]

### <a name="count"></a>Count

Koleksiyondaki öğelerin sayısını sayar. `Boolean`Koleksiyonda yalnızca bir koşulu karşılayan öğelerin sayısını saymak için isteğe bağlı bir ifade sağlayabilirsiniz. Aşağıda bir örnek verilmiştir:

 [!code-vb[VbSimpleQuerySamples#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#8)]

### <a name="group"></a>Grup

, `Group By` Veya yan tümcesinin sonucu olarak gruplandırılan sorgu sonuçlarının başvurduğu anlamına gelir `Group Join` . `Group`İşlev yalnızca `Into` `Group By` OR yan tümcesinde geçerlidir `Group Join` . Daha fazla bilgi ve örnek için bkz. [Group by yan tümcesi](group-by-clause.md) ve [Group JOIN yan tümcesi](group-join-clause.md).

### <a name="longcount"></a>LongCount

Koleksiyondaki öğelerin sayısını sayar. `Boolean`Koleksiyonda yalnızca bir koşulu karşılayan öğelerin sayısını saymak için isteğe bağlı bir ifade sağlayabilirsiniz. Sonucu bir olarak döndürür `Long` . Bir örnek için bkz `Count` . toplama işlevi.

### <a name="max"></a>En yüksek değer

Koleksiyondaki maksimum değeri hesaplar veya koleksiyondaki tüm öğeler için sağlanan bir ifadeyi hesaplar. Aşağıda bir örnek verilmiştir:

 [!code-vb[VbSimpleQuerySamples#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#9)]

### <a name="min"></a>Min

Koleksiyondaki en küçük değeri hesaplar veya koleksiyondaki tüm öğeler için sağlanan bir ifadeyi hesaplar. Aşağıda bir örnek verilmiştir:

 [!code-vb[VbSimpleQuerySamples#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#10)]

### <a name="sum"></a>Toplam

Koleksiyondaki tüm öğelerin toplamını hesaplar veya koleksiyondaki tüm öğeler için sağlanan bir ifadeyi hesaplar. Aşağıda bir örnek verilmiştir:

 [!code-vb[VbSimpleQuerySamples#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#15)]

## <a name="example"></a>Örnek  

Aşağıdaki örnek, `Aggregate` bir sorgu sonucuna toplama işlevleri uygulamak için yan tümcesinin nasıl kullanılacağını gösterir.  
  
 [!code-vb[VbSimpleQuerySamples#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#4)]  
  
## <a name="creating-user-defined-aggregate-functions"></a>Kullanıcı tanımlı toplama Işlevleri oluşturma

 Türe uzantı yöntemleri ekleyerek kendi özel toplama işlevlerinizi bir sorgu ifadesine dahil edebilirsiniz <xref:System.Collections.Generic.IEnumerable%601> . Özel yönteminiz, toplama işlevinizin başvurduğu sıralanabilir koleksiyonda bir hesaplama veya işlem gerçekleştirebilir. Uzantı yöntemleri hakkında daha fazla bilgi için bkz. [Uzantı yöntemleri](../../programming-guide/language-features/procedures/extension-methods.md).  
  
 Örneğin, aşağıdaki örnek bir sayı koleksiyonunun ortanca değerini hesaplayan özel bir toplama işlevi gösterir. Uzantı yönteminin iki aşırı yüklemesi vardır `Median` . İlk aşırı yükleme giriş olarak bir tür koleksiyonu kabul eder `IEnumerable(Of Double)` . `Median`Toplama işlevi, türünde bir sorgu alanı için çağrılırsa `Double` , bu yöntem çağrılır. Metodun ikinci aşırı yüklemesi `Median` herhangi bir genel tür geçirilebilir. Yönteminin genel aşırı yüklemesi, `Median` `Func(Of T, Double)` bir tür için değeri (bir koleksiyondan), karşılık gelen türü olarak proje için lambda ifadesine başvuran ikinci bir parametre alır `Double` . Daha sonra ortanca değer hesaplamasını metodun diğer aşırı yüküne devreder `Median` . Lambda ifadeleri hakkında daha fazla bilgi için bkz. [lambda ifadeleri](../../programming-guide/language-features/procedures/lambda-expressions.md).  
  
 [!code-vb[VbSimpleQuerySamples#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/UserDefinedAggregates.vb#18)]  
  
 Aşağıdaki örnek `Median` , bir türü koleksiyonda toplama işlevini çağıran örnek sorguları `Integer` ve türünde bir koleksiyonu gösterir `Double` . `Median`Türü koleksiyonundaki toplama işlevini çağıran sorgu, `Double` `Median` türü bir koleksiyon olarak kabul eden metodun aşırı yüklemesini çağırır `Double` . `Median`Türü koleksiyonundaki toplama işlevini çağıran sorgu, `Integer` yönteminin genel aşırı yüklemesini çağırır `Median` .  
  
 [!code-vb[VbSimpleQuerySamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/UserDefinedAggregates.vb#19)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic'de LINQ'e Giriş](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [Sorgular](index.md)
- [Select yan tümcesi](select-clause.md)
- [From yan tümcesi](from-clause.md)
- [WHERE yan tümcesi](where-clause.md)
- [Group By Yan Tümcesi](group-by-clause.md)
