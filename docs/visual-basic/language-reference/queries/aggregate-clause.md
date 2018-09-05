---
title: Aggregate Tümcesi (Visual Basic)
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
ms.openlocfilehash: e3ce8ff7da647120e5fd9e3b4cd44cc603eb797d
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43519492"
---
# <a name="aggregate-clause-visual-basic"></a>Aggregate Tümcesi (Visual Basic)
Bir veya daha fazla toplama işlevleri, bir koleksiyon için geçerlidir.  
  
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
|`type`|İsteğe bağlı. Türünü `element`. Tür yok belirtilirse, türü `element` içinden gösterilen `collection`.|  
|`collection`|Gerekli. Üzerinde çalışılacak koleksiyonuna başvuruyor.|  
|`clause`|İsteğe bağlı. Bir veya daha fazla yan tümcesi gibi sorgu bir `Where` aggregate yan tümcesi veya yan tümceyi uygulamak için sorgu sonucu iyileştirmek için yan tümcesi.|  
|`expressionList`|Gerekli. Koleksiyona uygulamak için bir toplama işlevi tanımlayan bir veya daha fazla virgülle ayrılmış ifadeler. Sorgu sonucu için bir üye adı belirtmek için bir toplama işlevi için bir diğer ad uygulayabilirsiniz. Takma ad sağlanmazsa, toplama işlevinin adı kullanılır. Örnekler için bu konunun ilerleyen bölümlerinde toplama işlevleri hakkındaki bölüme bakın.|  
  
## <a name="remarks"></a>Açıklamalar  
 `Aggregate` Yan tümcesi, sorgularınızdaki toplama işlevleri eklemek için kullanılabilir. Toplama işlevleri, bir dizi üzerinde denetimleri ve hesaplamalar gerçekleştirmek ve tek bir değer döndürür. Sorgu sonuç türü üyesi'ı kullanarak hesaplanan değer erişebilirsiniz. Kullanabileceğiniz standart toplama işlevleri `All`, `Any`, `Average`, `Count`, `LongCount`, `Max`, `Min`, ve `Sum` işlevleri. Bu işlevler, toplamlar SQL bilginiz geliştiriciler sahibisiniz. Bunlar, bu konunun aşağıdaki bölümde açıklanmıştır.  
  
 Bir toplama işlevi sonucu sorgu sonucu bir sorgu sonuç türünü alan olarak dahil edilir. Toplam değer tutacak sorgu sonuç türü üyesi adını belirtmek toplama işlevi sonucu için bir diğer ad sağlayabilirsiniz. Takma ad sağlanmazsa, toplama işlevinin adı kullanılır.  
  
 `Aggregate` Yan tümcesi bir sorgu başlayabilir veya başka bir yan tümce sorgu olarak dahil edilebilir. Varsa `Aggregate` yan tümcesi bir sorgu başlar, belirtilen toplama işlevinin sonucu tek bir değer sonuç `Into` yan tümcesi. Birden fazla toplama işlevi belirtilmişse `Into` yan tümcesi, sorgunun döndürdüğü her bir toplama işlevinde sonucunu başvurmak için ayrı bir özellik ile tek bir türü `Into` yan tümcesi. Varsa `Aggregate` yan tümcesi bir sorgu içinde başka bir yan tümce olarak dahil, sorgu koleksiyonda döndürülen tür her bir toplama işlevinde sonucunu başvurmak için ayrı bir özelliğe sahiptir `Into` yan tümcesi.  
  
## <a name="aggregate-functions"></a>Toplama İşlevleri

Kullanılabilir standart toplama işlevleri şunlardır `Aggregate` yan tümcesi.  
  
### <a name="all"></a>Tümü

Döndürür `true` koleksiyondaki tüm öğeler belirtilen bir koşulu; karşılıyorsanız, döndürür, aksi takdirde `false`. Bir örnek verilmiştir:

[!code-vb[VbSimpleQuerySamples#5](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_1.vb)]

### <a name="any"></a>Tüm

Döndürür `true` koleksiyondaki herhangi bir öğeyi; belirtilen bir koşulu karşılıyorsa döndürür, aksi takdirde `false`. Bir örnek verilmiştir:

[!code-vb[VbSimpleQuerySamples#6](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_2.vb)]

### <a name="average"></a>Ortalama

Koleksiyondaki tüm öğelerin ortalamasını hesaplar veya koleksiyondaki tüm öğeler için sağlanan bir ifade sonucunu hesaplar. Bir örnek verilmiştir:

[!code-vb[VbSimpleQuerySamples#7](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_3.vb)]

### <a name="count"></a>Sayısı

Koleksiyondaki öğe sayısını sayar. İsteğe bağlı bir tedarik `Boolean` ifade yalnızca bir koşulu karşılayan koleksiyondaki öğe sayısı. Bir örnek verilmiştir:

[!code-vb[VbSimpleQuerySamples#8](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_4.vb)]

### <a name="group"></a>Grup

Sonucu olarak gruplandırılır sorgu sonuçları başvurduğu bir `Group By` veya `Group Join` yan tümcesi. `Group` İşlev, yalnızca geçerli `Into` yan tümcesi bir `Group By` veya `Group Join` yan tümcesi. Daha fazla bilgi ve örnekler için bkz. [Group yan tümcesi tarafından](../../../visual-basic/language-reference/queries/group-by-clause.md) ve [Group JOIN yan tümcesi](../../../visual-basic/language-reference/queries/group-join-clause.md).

### <a name="longcount"></a>LongCount

Koleksiyondaki öğe sayısını sayar. İsteğe bağlı bir tedarik `Boolean` ifade yalnızca bir koşulu karşılayan koleksiyondaki öğe sayısı. Sonuç olarak döndüren bir `Long`. Bir örnek için bkz `Count` toplama işlevi.

### <a name="max"></a>Maks.

Koleksiyondan maksimum değeri hesaplar ve koleksiyondaki tüm öğeler için sağlanan bir ifadeyi hesaplar. Bir örnek verilmiştir:

[!code-vb[VbSimpleQuerySamples#9](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_5.vb)]

### <a name="min"></a>Min.

Koleksiyondan minimum değeri hesaplar ve koleksiyondaki tüm öğeler için sağlanan bir ifadeyi hesaplar. Bir örnek verilmiştir:

[!code-vb[VbSimpleQuerySamples#10](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_6.vb)]

### <a name="sum"></a>TOPLA

Koleksiyondaki tüm öğelerin toplamını hesaplar ve koleksiyondaki tüm öğeler için sağlanan bir ifadeyi hesaplar. Bir örnek verilmiştir:

[!code-vb[VbSimpleQuerySamples#15](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_7.vb)]

## <a name="example"></a>Örnek  

Aşağıdaki örnek nasıl kullanılacağını gösterir `Aggregate` yan tümcesi bir sorgu sonucuna toplama işlevleri uygulamak için.  
  
 [!code-vb[VbSimpleQuerySamples#4](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_8.vb)]  
  
## <a name="creating-user-defined-aggregate-functions"></a>Kullanıcı tanımlı toplama işlevleri oluşturma

 Kendi özel toplama işlevleri için genişletme yöntemleri ekleyerek bir sorgu ifadesine dahil edebileceğiniz <xref:System.Collections.Generic.IEnumerable%601> türü. Özel yönteminiz, ardından bir hesaplama veya toplama işlevinizi başvurmuş sıralanabilir koleksiyonun işlemi gerçekleştirebilirsiniz. Uzantı yöntemleri hakkında daha fazla bilgi için bkz. [genişletme yöntemleri](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).  
  
 Örneğin, aşağıdaki örnek, sayıdan oluşan bir koleksiyon ORTANCA değerini hesaplar. özel bir toplama işlevi gösterir. İki aşırı yükleme `Median` genişletme yöntemi. İlk aşırı yükleme, giriş olarak bir koleksiyon türü kabul eden `IEnumerable(Of Double)`. Varsa `Median` toplama işlevi türü için bir sorgu alanını adlı `Double`, bu yöntem çağrılır. İkinci aşırı yüklemesi `Median` yöntemi herhangi bir genel tür geçirilebilir. Genel aşırı yüklemesini `Median` yöntemi başvuran ikinci bir parametre alır `Func(Of T, Double)` lambda ifadesi (bir koleksiyondan) bir tür için bir değer türüne karşılık gelen değeri olarak projeye `Double`. Ardından bir aşırı yüklemesini ORTANCA değeri hesaplama Temsilciler `Median` yöntemi. Lambda ifadeleri hakkında daha fazla bilgi için bkz. [Lambda ifadeleri](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 [!code-vb[VbSimpleQuerySamples#18](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_9.vb)]  
  
 Aşağıdaki örnek, çağıran örnek sorgular gösterir `Median` toplama türü koleksiyonunda işlevi `Integer`ve bir koleksiyon türü `Double`. Çağıran bir sorgu `Median` toplama türü koleksiyonunu işlevi `Double` aşırı yüklemesini çağırır `Median` türünde bir girdi olarak kabul eden yöntemi `Double`. Çağıran bir sorgu `Median` toplama türü koleksiyonunu işlevi `Integer` genel aşırı yüklemesini çağırır `Median` yöntemi.  
  
 [!code-vb[VbSimpleQuerySamples#19](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_10.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [Visual Basic'de LINQ'e giriş](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
- [Sorgular](../../../visual-basic/language-reference/queries/index.md)  
- [Select Yan Tümcesi](../../../visual-basic/language-reference/queries/select-clause.md)  
- [From Yan Tümcesi](../../../visual-basic/language-reference/queries/from-clause.md)  
- [Where Yan Tümcesi](../../../visual-basic/language-reference/queries/where-clause.md)  
- [Group By Yan Tümcesi](../../../visual-basic/language-reference/queries/group-by-clause.md)
