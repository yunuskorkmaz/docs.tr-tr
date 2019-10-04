---
title: Standart sorgu Işleci çevirisi
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a60c30fa-1e68-45fe-b984-f6abb9ede40e
ms.openlocfilehash: af22b6a895fef8037eb5c069ffb7cb23d1333531
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833676"
---
# <a name="standard-query-operator-translation"></a>Standart sorgu Işleci çevirisi

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] standart sorgu Işleçlerini SQL komutlarına çevirir. Veritabanının sorgu işlemcisi SQL çevirisi 'nin yürütme semantiğini belirler.

Standart sorgu Işleçleri *sıralara*göre tanımlanır. Bir sıra *sıralanır* ve dizideki her öğe için başvuru kimliğini kullanır. Daha fazla bilgi için bkz. [Standart sorgu işleçlerineC#genel bakış ()](../../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) veya [Standart sorgu işleçleri genel bakış (Visual Basic)](../../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).

SQL, birincil olarak *sırasız değer kümeleriyle anlaşmalar yapar*. Sıralama genellikle, ara sonuçlar yerine bir sorgunun nihai sonucuna uygulanan, açıkça belirtilmiş, işleme sonrası bir işlemdir. Kimlik, değerler tarafından tanımlanır. Bu nedenle SQL sorguları, *kümeler*yerine çoklu kümeler (*bAdım*) ile uğraşmak üzere anlaşılmıştır.

Aşağıdaki paragraflarda, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ' a yönelik SQL Server sağlayıcısı için standart sorgu Işleçleri ve SQL çevirisi arasındaki farklar açıklanır.

## <a name="operator-support"></a>İşleç desteği

### <a name="concat"></a>Concat

@No__t-0 yöntemi, alıcı sırasının ve bağımsız değişkenin sırası aynı olduğu sıralı çoklu kümeler için tanımlanmıştır. <xref:System.Linq.Enumerable.Concat%2A>, multisets 'ler üzerinde `UNION ALL` olarak çalışarak ortak sipariş ' i izler.

Son adım, sonuçlar üretilmadan önce SQL 'de sıralamaktır. <xref:System.Linq.Enumerable.Concat%2A>, bağımsız değişkenlerinin sırasını korumaz. Uygun sıralamayı sağlamak için <xref:System.Linq.Enumerable.Concat%2A> ' a ait sonuçları açıkça Sıralamalı olmanız gerekir.

### <a name="intersect-except-union"></a>Intersect, Except, birleşim

@No__t-0 ve <xref:System.Linq.Enumerable.Except%2A> yöntemleri yalnızca kümeler üzerinde tanımlıdır. Multisets semantiği tanımsızdır.

@No__t-0 yöntemi multisets 'ler için birden çok kümeler için tanımlanır (SQL 'deki UNıON ALL yan tümcesinin sonucu etkin değildir).

### <a name="take-skip"></a>Al, atla

<xref:System.Linq.Enumerable.Take%2A> ve <xref:System.Linq.Enumerable.Skip%2A> yöntemleri yalnızca *sıralı kümelere*karşı iyi tanımlanmış. Sıralanmamış kümeler veya birden çok küme semantiği tanımsızdır.

> [!NOTE]
> <xref:System.Linq.Enumerable.Take%2A> ve <xref:System.Linq.Enumerable.Skip%2A> SQL Server 2000 ' de sorgularda kullanıldıkları zaman belirli sınırlamalara sahiptir. Daha fazla bilgi için bkz. [sorun giderme](troubleshooting.md)içindeki "SQL Server 2000 'de özel durumları atla ve al" girişi.

SQL 'de sıralamaya yönelik sınırlamalar nedeniyle [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], bu yöntemlerin bağımsız değişkeninin sıralamasını yöntemin sonucuna taşımaya çalışır. Örneğin, aşağıdaki [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sorgusunu göz önünde bulundurun:

[!code-csharp[DLinqSQOTranslation#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#1)]
[!code-vb[DLinqSQOTranslation#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#1)]

Bu kod için oluşturulan SQL, aşağıdaki gibi sıralamayı sonuna taşıdır:

```sql
SELECT TOP 1 [t0].[CustomerID], [t0].[CompanyName],
FROM [Customers] AS [t0]
WHERE (NOT (EXISTS(
    SELECT NULL AS [EMPTY]
    FROM (
        SELECT TOP 1 [t1].[CustomerID]
        FROM [Customers] AS [t1]
        WHERE [t1].[City] = @p0
        ORDER BY [t1].[CustomerID]
        ) AS [t2]
    WHERE [t0].[CustomerID] = [t2].[CustomerID]
    ))) AND ([t0].[City] = @p1)
ORDER BY [t0].[CustomerID]
```

@No__t-0 ve <xref:System.Linq.Enumerable.Skip%2A> birlikte zincirleme yapıldığında, belirtilen tüm sıralamayı tutarlı hale gelir. Aksi takdirde, sonuçlar tanımsızdır.

Hem <xref:System.Linq.Enumerable.Take%2A> hem de <xref:System.Linq.Enumerable.Skip%2A>, standart sorgu Işleci belirtimine göre negatif olmayan, sabit integral bağımsız değişkenler için iyi tanımlanmıştır.

### <a name="operators-with-no-translation"></a>Çevirisi olmayan işleçler

Aşağıdaki yöntemler [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ' a çevrilmez. En yaygın neden, sıralanmamış çoklu kümeler ve diziler arasındaki farktır.

|İşleçler|Mantığı anladığınızdan|
|---------------|---------------|
|<xref:System.Linq.Enumerable.TakeWhile%2A>, <xref:System.Linq.Enumerable.SkipWhile%2A>|SQL sorguları diziler üzerinde değil, çoklu kümeler üzerinde çalışır. `ORDER BY` ' ın sonuçlara uygulanan son yan tümce olması gerekir. Bu nedenle, bu iki yöntem için genel amaçlı bir çeviri yoktur.|
|<xref:System.Linq.Enumerable.Reverse%2A>|Bu yöntemin çevirisi, sıralı bir küme için mümkündür ancak şu anda [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ile çevrilmez.|
|<xref:System.Linq.Enumerable.Last%2A>, <xref:System.Linq.Enumerable.LastOrDefault%2A>|Bu yöntemlerin çevirisi, sıralı bir küme için mümkündür ancak şu anda [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ile çevrilmez.|
|<xref:System.Linq.Enumerable.ElementAt%2A>, <xref:System.Linq.Enumerable.ElementAtOrDefault%2A>|SQL sorguları, dizine eklenebilir diziler üzerinde değil, çoklu kümeler üzerinde çalışır.|
|<xref:System.Linq.Enumerable.DefaultIfEmpty%2A> (varsayılan bağımsız değişken ile aşırı yükleme)|Genel olarak, rastgele bir tanımlama grubu için varsayılan bir değer belirtilemez. Dış birleştirmeler aracılığıyla bazı durumlarda, diziler için null değerler mümkündür.|

## <a name="expression-translation"></a>İfade çevirisi

### <a name="null-semantics"></a>Null semantiği

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] SQL üzerinde null karşılaştırma semantiğini uygulamaz. Karşılaştırma işleçleri, sözdizimsel olarak SQL eşdeğerlerine çevrilir. Bu nedenle, semantik, sunucu veya bağlantı ayarları tarafından tanımlanan SQL semantiğini yansıtır. Örneğin, iki null değer varsayılan SQL Server ayarları altında eşit olarak değerlendirilir, ancak semantiğini değiştirmek için ayarları değiştirebilirsiniz. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sorguları çevirdiğinde sunucu ayarlarını kabul etmez.

Null değerli bir karşılaştırma uygun SQL sürümüne (`is null` veya `is not null`) çevrilir.

Harmanlama `null` değeri SQL Server tarafından tanımlanır. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] harmanlamayı değiştirmez.

### <a name="aggregates"></a>Toplamalar

@No__t-0 standart sorgu Işleci toplama yöntemi boş bir sıra veya yalnızca null değer içeren bir sıra için sıfır olarak değerlendirilir. @No__t-0 ' da, SQL 'in semantiği değişmeden bırakılır ve <xref:System.Linq.Enumerable.Sum%2A> boş bir sıra veya yalnızca null değerleri içeren bir sıra için 0 yerine `null` olarak değerlendirilir.

Ara sonuçlarda SQL sınırlamaları [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ' daki toplamalar için geçerlidir. 32 bitlik tamsayı miktarları <xref:System.Linq.Enumerable.Sum%2A> ' ın 64 bit sonuçlar kullanılarak hesaplanmaz. Standart sorgu Işleci uygulamasının karşılık gelen bellek içi dizide taşma olmasına neden olmasa bile, <xref:System.Linq.Enumerable.Sum%2A> ' in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] çevirisi için taşma oluşabilir.

Benzer şekilde, <xref:System.Linq.Enumerable.Average%2A> ' in tamsayı değerlerinin [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] çevirisi, @no__t 3 olarak değil `integer` olarak hesaplanır.

### <a name="entity-arguments"></a>Varlık bağımsız değişkenleri

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], <xref:System.Linq.Enumerable.GroupBy%2A> ve <xref:System.Linq.Enumerable.OrderBy%2A> yöntemlerinde varlık türlerinin kullanılmasını sağlar. Bu işleçlerin çevirisinde, bir türün bağımsız değişkeninin kullanımı, bu türün tüm üyelerini belirtmeye eşdeğer olarak kabul edilir. Örneğin, aşağıdaki kod eşdeğerdir:

[!code-csharp[DLinqSQOTranslation#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#2)]
[!code-vb[DLinqSQOTranslation#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#2)]

### <a name="equatable--comparable-arguments"></a>Equatable/karşılaştırılabilir bağımsız değişkenler

Aşağıdaki yöntemlerin uygulanmasında bağımsız değişkenlerin eşitliği gereklidir:

- <xref:System.Linq.Enumerable.Contains%2A>

- <xref:System.Linq.Enumerable.Skip%2A>

- <xref:System.Linq.Enumerable.Union%2A>

- <xref:System.Linq.Enumerable.Intersect%2A>

- <xref:System.Linq.Enumerable.Except%2A>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], *düz* bağımsız değişkenler için eşitlik ve karşılaştırmayı destekler, ancak dizileri olan veya içeren bağımsız değişkenler için değildir. Düz bir bağımsız değişken, bir SQL satırına eşlenebilir bir türdür. Statik olarak belirlenebileceği bir veya daha fazla varlık türünün projeksiyonu düz bir bağımsız değişken olarak kabul edilir.

Düz bağımsız değişkenlerin örnekleri aşağıda verilmiştir:

[!code-csharp[DLinqSQOTranslation#3](~/samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#3)]
[!code-vb[DLinqSQOTranslation#3](~/samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#3)]

Aşağıda, düz olmayan (hiyerarşik) bağımsız değişkenlerin örnekleri verilmiştir:

[!code-csharp[DLinqSQOTranslation#4](~/samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#4)]
[!code-vb[DLinqSQOTranslation#4](~/samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#4)]

### <a name="visual-basic-function-translation"></a>Visual Basic Işlev çevirisi

Visual Basic Derleyicisi tarafından kullanılan aşağıdaki yardımcı işlevler, karşılık gelen SQL işleçleri ve işlevlerine çevrilir:

- `CompareString`

- `DateTime.Compare`

- `Decimal.Compare`

- `IIf (in Microsoft.VisualBasic.Interaction)`

Dönüştürme yöntemleri:

|||||
|-|-|-|-|
|ToBoolean|ToSByte|ToByte|ToChar|
|ToCharArrayRankOne|ToDate|ToDecimal|ToDouble|
|ToInteger|ToUInteger|ToLong|ToULong|
|ToShort|ToUShort|ToSingle|Yönte|

## <a name="inheritance-support"></a>Devralma desteği

### <a name="inheritance-mapping-restrictions"></a>Devralma eşleme kısıtlamaları

Daha fazla bilgi için bkz. [nasıl yapılır: harita devralma hiyerarşileri](how-to-map-inheritance-hierarchies.md).

### <a name="inheritance-in-queries"></a>Sorgularda devralma

C#Atamalar yalnızca projeksiyde desteklenir. Başka bir yerde kullanılan yayınlar çevrilmez ve yok sayılır. SQL işlev adlarından de, SQL aslında yalnızca ortak dil çalışma zamanının (CLR) <xref:System.Convert> ' ı kullanır. Diğer bir deyişle, SQL bir tür değerini başka bir türe değiştirebilir. Başka bir türden farklı bitleri yeniden yorumlama kavramı olmadığından, CLR cast ' ın eşdeğeri yoktur. Bu, bir C# dönüştürmenin yalnızca yerel olarak çalışmasına neden olur. Bu uzak değildir.

İşleçler, `is` ve `as` ve `GetType` yöntemi `Select` işleciyle kısıtlanmaz. Bunlar aynı zamanda diğer sorgu işleçleri içinde de kullanılabilir.

## <a name="sql-server-2008-support"></a>SQL Server 2008 desteği

.NET Framework 3,5 SP1 ile başlayarak LINQ to SQL, SQL Server 2008 ile tanıtılan yeni tarih ve saat türleriyle eşlemeyi destekler. Ancak, bu yeni türlere eşlenen değerlere karşı çalışırken kullanabileceğiniz LINQ to SQL sorgu işleçleri için bazı sınırlamalar vardır.

### <a name="unsupported-query-operators"></a>Desteklenmeyen sorgu Işleçleri

Aşağıdaki sorgu işleçleri yeni SQL Server Tarih ve saat türleriyle eşlenen değerlerde desteklenmez: `DATETIME2`, `DATE`, `TIME` ve `DATETIMEOFFSET`.

- `Aggregate`

- `Average`

- `LastOrDefault`

- `OfType`

- `Sum`

Bu SQL Server Tarih ve saat türleriyle eşleştirme hakkında daha fazla bilgi için bkz. [SQL-CLR tür eşleme](sql-clr-type-mapping.md).

## <a name="sql-server-2005-support"></a>SQL Server 2005 desteği

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], aşağıdaki SQL Server 2005 özelliklerini desteklemez:

- SQL CLR için yazılan saklı yordamlar.

- Kullanıcı tanımlı tür.

- XML sorgu özellikleri.

## <a name="sql-server-2000-support"></a>SQL Server 2000 desteği

Aşağıdaki SQL Server 2000 sınırlamaları (Microsoft SQL Server 2005 ile karşılaştırıldığında) [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] desteğini etkiler.

### <a name="cross-apply-and-outer-apply-operators"></a>Çapraz uygulama ve dış uygulama Işleçleri

Bu işleçler SQL Server 2000 ' de kullanılamaz. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], uygun birleştirmelere göre değiştirmek için bir dizi yeniden yazmaya çalışır.

`Cross Apply` ve `Outer Apply` ilişki gezginlerini için oluşturulur. Bu tür yeniden yazar mümkün olan sorgu kümesi iyi tanımlanmamıştır. Bu nedenle, SQL Server 2000 için desteklenen minimum sorgu kümesi ilişki gezintisi içermeyen bir kümesidir.

### <a name="text--ntext"></a>Text/ntext

@No__t-0 @ no__t-1 @ no__t-2 veri türleri Microsoft SQL Server 2005 tarafından desteklenen `varchar(max)` @ no__t-4 @ no__t-5 ' teki belirli sorgu işlemlerinde kullanılamaz.

Bu sınırlama için hiçbir çözüm yok. Özellikle, `text` veya `ntext` sütunlarına eşlenen Üyeler içeren herhangi bir sonuç üzerinde `Distinct()` kullanamazsınız.

### <a name="behavior-triggered-by-nested-queries"></a>Iç Içe geçmiş sorgular tarafından tetiklenen davranış

SQL Server 2000 (SP4) bağlayıcı, iç içe geçmiş sorgular tarafından tetiklenen bazı idosynyenilere sahiptir. Bu deyimi tetikleyen SQL sorguları kümesi iyi tanımlanmamıştır. Bu nedenle, SQL Server özel durumlara neden olabilecek [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sorgularının kümesini tanımlayamazsınız.

### <a name="skip-and-take-operators"></a>Atla ve Al Işleçleri

<xref:System.Linq.Enumerable.Take%2A> ve <xref:System.Linq.Enumerable.Skip%2A> SQL Server 2000 ' de sorgularda kullanıldıkları zaman belirli sınırlamalara sahiptir. Daha fazla bilgi için bkz. [sorun giderme](troubleshooting.md)içindeki "SQL Server 2000 'de özel durumları atla ve al" girişi.

## <a name="object-materialization"></a>Nesne materialization

Materialization bir veya daha fazla SQL sorgusu tarafından döndürülen satırlardan CLR nesneleri oluşturur.

- Aşağıdaki çağrılar, materialization 'ın bir parçası olarak *yerel olarak yürütülür* :

  - Kurucu

  - tahminlerdeki `ToString` yöntemleri

  - Yansıtmalarda tür atamaları

- @No__t-0 yöntemini izleyen Yöntemler *yerel olarak yürütülür*. Bu yöntem, hemen yürütmeye neden olmaz.

- Bir sorgu sonucunun dönüş türü olarak veya sonuç türünün bir üyesi olarak bir `struct` kullanabilirsiniz. Varlıkların sınıflar olması gerekir. Anonim türler sınıf örnekleri olarak gerçekleştirilir, ancak adlandırılmış yapılar (varlık olmayan) projeksiyonde kullanılabilir.

- Bir sorgu sonucunun dönüş türünün bir üyesi <xref:System.Linq.IQueryable%601> türünde olabilir. Yerel bir koleksiyon olarak gerçekleştirilmiş olur.

- Aşağıdaki yöntemler, yöntemlerin uygulandığı dizinin *hemen* bir şekilde oluşturulmasına neden olur:

  - <xref:System.Linq.Enumerable.ToList%2A>

  - <xref:System.Linq.Enumerable.ToDictionary%2A>

  - <xref:System.Linq.Enumerable.ToArray%2A>

## <a name="see-also"></a>Ayrıca bkz.

- [Başvuru](reference.md)
- [Bir dizideki öğeleri döndürün veya atlayın](return-or-skip-elements-in-a-sequence.md)
- [Iki diziyi birleştirme](concatenate-two-sequences.md)
- [Iki sıra arasındaki küme farkını döndürür](return-the-set-difference-between-two-sequences.md)
- [Iki sıranın küme kesişimini döndürür](return-the-set-intersection-of-two-sequences.md)
- [Iki sıranın küme birleşimini döndürün](return-the-set-union-of-two-sequences.md)
