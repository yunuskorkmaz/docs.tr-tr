---
title: Standart sorgu işleci çevirisi
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a60c30fa-1e68-45fe-b984-f6abb9ede40e
ms.openlocfilehash: fb4910e48af58463c5c851173f8e3caf4594cc3a
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44197478"
---
# <a name="standard-query-operator-translation"></a>Standart sorgu işleci çevirisi
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Standart sorgu işleçleri SQL komutlara çevirir. Sorgu işlemcisi veritabanının SQL çeviri yürütme semantikleri belirler.  
  
 Standart sorgu işleçleri karşı tanımlanmış *dizileri*. Bir sıra *sıralı* ve dizinin her öğesi için başvuru kimliği kullanır. Daha fazla bilgi için [standart sorgu işleçlerine genel bakış](https://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).  
  
 SQL ilgilenen öncelikli olarak *değer kümeleri sıralanmamış*. Sıralamadır genellikle bir açıkça belirtilen, bir sorgu sonucunu yerine Ara sonuçlar uygulanan sonrası işlem. Kimlik değerleri tarafından tanımlanır. Bu nedenle SQL sorguları multisets ile dağıtılacak anlaşılabilir (*paketleri*) yerine *ayarlar*.  
  
 Standart sorgu işleçleri ve kendi SQL çeviri için SQL Server sağlayıcısı arasındaki farklar aşağıdaki paragraflara açıklayan [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
## <a name="operator-support"></a>İşleç desteği  
  
### <a name="concat"></a>concat  
 <xref:System.Linq.Enumerable.Concat%2A> Yöntemi alıcı sırası ve bağımsız değişken sırası olduğu aynı sıralı multisets için tanımlanır. <xref:System.Linq.Enumerable.Concat%2A> gibi çalışır `UNION ALL` genel sıraya göre ve ardından multisets üzerinden.  
  
 Son adım, sonuçları üretti önce SQL sıralaması. <xref:System.Linq.Enumerable.Concat%2A> bağımsız değişkenlerinin sırası korumaz. Uygun sıralama emin olmak için açıkça sonuçlarını sıralamanız gerekir <xref:System.Linq.Enumerable.Concat%2A>.  
  
### <a name="intersect-except-union"></a>INTERSECT, birleşim dışında  
 <xref:System.Linq.Enumerable.Intersect%2A> Ve <xref:System.Linq.Enumerable.Except%2A> yöntemlerdir kümelerinde yalnızca iyi tanımlanmış. Semantiği multisets için tanımlı değil.  
  
 <xref:System.Linq.Enumerable.Union%2A> Yöntemi multisets için (etkili bir şekilde SQL UNION ALL yan tümcesinin sonucu) multisets sırasız birleşimi olarak tanımlanır.  
  
### <a name="take-skip"></a>Sınav zamanı, Atla  
 <xref:System.Linq.Enumerable.Take%2A> ve <xref:System.Linq.Enumerable.Skip%2A> yöntemlerdir karşı yalnızca iyi tanımlanmış *kümeleri sıralı*. Sırasız kümeleri veya multisets semantiği tanımsızdır.  
  
> [!NOTE]
>  <xref:System.Linq.Enumerable.Take%2A> ve <xref:System.Linq.Enumerable.Skip%2A> SQL Server 2000 sorguları içinde kullanıldığında belirli sınırlamaları vardır. "Atla ve SQL Server 2000'de özel durumlar'ı Al" girdisinde daha fazla bilgi için bkz. [sorun giderme](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).  
  
 SQL'de sıralama sınırlamaları nedeniyle [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] bağımsız değişkeni yöntemin sonucu için bu yöntemlerin sıralama taşımak çalışır. Örneğin, aşağıdakileri dikkate alın [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sorgu:  
  
 [!code-csharp[DLinqSQOTranslation#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#1)]
 [!code-vb[DLinqSQOTranslation#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#1)]  
  
 Bu kod için oluşturulan SQL gibi sonuna sıralama taşır:  
  
```  
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
  
 Tüm belirtilen sıralama ne zaman tutarlı olmasını belirgin hale gelir <xref:System.Linq.Enumerable.Take%2A> ve <xref:System.Linq.Enumerable.Skip%2A> birbirine zincirlenmiş. Aksi takdirde, sonuçlar tanımsızdır.  
  
 Her ikisi de <xref:System.Linq.Enumerable.Take%2A> ve <xref:System.Linq.Enumerable.Skip%2A> standart sorgu işleci belirtimine göre negatif olmayan, sabit tamsayı bağımsız değişkenler için iyi tanımlanmış olması.  
  
### <a name="operators-with-no-translation"></a>Çeviri sahip işleçler  
 Aşağıdaki yöntemleri tarafından bunların çevirisi yapılmaz [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. En yaygın nedeni, sırasız multisets dizileri arasındaki farktır.  
  
|İşleçler|Stratejinin|  
|---------------|---------------|  
|<xref:System.Linq.Enumerable.TakeWhile%2A>, <xref:System.Linq.Enumerable.SkipWhile%2A>|Diziler üzerinde değil, multisets üzerinde SQL sorguları çalışır. `ORDER BY` Son yan tümce sonuçları uygulanması gerekir. Bu nedenle, bu iki yöntem için genel amaçlı çeviri yoktur.|  
|<xref:System.Linq.Enumerable.Reverse%2A>|Bu yöntemin çeviri sıralı bir küme için mümkündür, ancak şu anda tarafından çevrilmez [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].|  
|<xref:System.Linq.Enumerable.Last%2A>, <xref:System.Linq.Enumerable.LastOrDefault%2A>|Bu yöntemlerin çeviri sıralı bir küme için mümkündür, ancak şu anda tarafından çevrilmez [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].|  
|<xref:System.Linq.Enumerable.ElementAt%2A>, <xref:System.Linq.Enumerable.ElementAtOrDefault%2A>|SQL sorguları dizinlenebilir dizileri göre değil, multisets üzerinde çalışır.|  
|<xref:System.Linq.Enumerable.DefaultIfEmpty%2A> (varsayılan bağımsız değişken ile aşırı yükleme)|Genel olarak, rastgele bir demet için bir varsayılan değer belirtilemez. Diziler için null değerler, bazı durumlarda dış birleştirmeler ile mümkündür.|  
  
## <a name="expression-translation"></a>İfade çevirisi  
  
### <a name="null-semantics"></a>Null semantikler  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] SQL null karşılaştırma semantiği uygulamaz. Karşılaştırma işleçleri sözdizimsel olarak SQL eşdeğerlerine dönüştürülür. Bu nedenle, sunucu veya bağlantı ayarları tarafından tanımlanan SQL semantiği semantiği yansıtır. Örneğin, iki null değerler varsayılan SQL Server Ayarları altında eşit olarak kabul edilir, ancak semantiği değiştirmek için ayarları değiştirebilirsiniz. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sorguları dönüştürdüğünde sunucu ayarlarını dikkate almaz.  
  
 Değişmez değeri null ile bir karşılaştırması için uygun SQL sürümü çevrilir (`is null` veya `is not null`).  
  
 Değerini `null` harmanlamasında SQL Server tarafından tanımlanır. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] harmanlama değiştirmez.  
  
### <a name="aggregates"></a>Toplamlar  
 Standart sorgu işleci toplama yöntemi <xref:System.Linq.Enumerable.Sum%2A> sıfıra yalnızca null içeren bir dizi veya boş bir dizi için değerlendirir. İçinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], SQL semantiği sol değiştirmeden, ve <xref:System.Linq.Enumerable.Sum%2A> değerlendiren `null` yerine yalnızca null içeren bir dizi veya boş bir dizi için sıfır.  
  
 Toplamalar Ara sonuçlar SQL sınırlamalar uygulanır [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. <xref:System.Linq.Enumerable.Sum%2A> 32-bit tamsayı miktarlar hesaplanan 64-bit sonuçları kullanarak. Taşma için oluşabilir bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] çevirisi <xref:System.Linq.Enumerable.Sum%2A>bile standart sorgu işleci uygulaması karşılık gelen bir bellek içi dizisi taşmaya neden olmaz.  
  
 Benzer şekilde, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] çevirisi <xref:System.Linq.Enumerable.Average%2A> tamsayı değerleri olarak hesaplanır bir `integer`, olarak değil bir `double`.  
  
### <a name="entity-arguments"></a>Varlık bağımsız değişkenleri  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] varlık türleri kullanılmak üzere etkinleştirir <xref:System.Linq.Enumerable.GroupBy%2A> ve <xref:System.Linq.Enumerable.OrderBy%2A> yöntemleri. Bu işleçler çeviriyi türünde bir bağımsız değişken kullanımı belirterek bu türün tüm üyeleri için eşdeğer olarak kabul edilir. Örneğin, aşağıdaki kod eşdeğerdir:  
  
 [!code-csharp[DLinqSQOTranslation#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#2)]
 [!code-vb[DLinqSQOTranslation#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#2)]  
  
### <a name="equatable--comparable-arguments"></a>Equatable / karşılaştırılabilir bağımsız değişkenleri  
 Aşağıdaki yöntemlerden birini uygulamasında eşitlik bağımsız değişkenleri gereklidir:  
  
 <xref:System.Linq.Enumerable.Contains%2A>  
  
 <xref:System.Linq.Enumerable.Skip%2A>  
  
 <xref:System.Linq.Enumerable.Union%2A>  
  
 <xref:System.Linq.Enumerable.Intersect%2A>  
  
 <xref:System.Linq.Enumerable.Except%2A>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Eşitlik ve karşılaştırma için destekleyen *düz* bağımsız değişkenler, ancak veya dizileri içeren olmayan bağımsız değişkenler için. Düz bir bağımsız değişken için bir SQL satırını eşlenmiş bir türdür. Bir projeksiyon bir dizisini içermez statik olarak belirlenebilir bir veya daha fazla varlık türleri, düz bir bağımsız değişken olarak kabul edilir.  
  
 Düz bağımsız değişkenleri örnekleri aşağıda verilmiştir:  
  
 [!code-csharp[DLinqSQOTranslation#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#3)]
 [!code-vb[DLinqSQOTranslation#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#3)]  
  
 Olmayan-düz (hiyerarşik) bağımsız örnekleri aşağıda verilmiştir.  
  
 [!code-csharp[DLinqSQOTranslation#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#4)]
 [!code-vb[DLinqSQOTranslation#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#4)]  
  
### <a name="visual-basic-function-translation"></a>Visual Basic işlevi çeviri  
 Visual Basic derleyici tarafından kullanılan aşağıdaki yardımcı İşlevler, karşılık gelen SQL işleç ve işlevlerini için çevrilir:  
  
 `CompareString`  
  
 `DateTime.Compare`  
  
 `Decimal.Compare`  
  
 `IIf (in Microsoft.VisualBasic.Interaction)`  
  
 Dönüştürme yöntemleri:  
  
|||||  
|-|-|-|-|  
|ToBoolean|ToSByte|ToByte|ToChar|  
|ToCharArrayRankOne|ToDate|ToDecimal|ToDouble|  
|ToInteger|ToUInteger|ToLong|ToULong|  
|ToShort|ToUShort|ToSingle|ToString|  
  
## <a name="inheritance-support"></a>Devralma desteği  
  
### <a name="inheritance-mapping-restrictions"></a>Devralma eşleme kısıtlamaları  
 Daha fazla bilgi için [nasıl yapılır: devralma hiyerarşilerini eşleme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-inheritance-hierarchies.md).  
  
### <a name="inheritance-in-queries"></a>Sorgularda devralma  
 C# atamalar yalnızca yansıtma içinde desteklenir. Başka bir yerde kullanılan atamaları değil çevrilir ve göz ardı edilir. SQL yanı sıra işlev adlarını, SQL gerçekten yalnızca ortak dil çalışma zamanı (CLR) eşdeğerini gerçekleştirir <xref:System.Convert>. Diğer bir deyişle, SQL, bir tür değeri diğerine değiştirebilirsiniz. Başka bir tür olarak aynı bitleri yeniden yorumlamak güvenli olmayabilecek bir kavram yoktur çünkü cast CLR eşdeğeri yoktur. Bir C# dönüştürme works neden yalnızca yerel olarak olmasıdır. Düğümlerde değil.  
  
 İşleçler `is` ve `as`ve `GetType` yöntemi sınırlı olmayan `Select` işleci. Bunlar ayrıca diğer sorgu işleçleri kullanılabilir.  
  
## <a name="sql-server-2008-support"></a>SQL Server 2008 desteği  
 .NET Framework 3.5 SP1 ile başlayarak, LINQ to SQL eşlemesi yeni tarih ve saat türleri SQL Server 2008 ile sunulan destekler. Ancak, bu yeni türleri için eşlenen değerleri karşı çalışırken kullanabileceğiniz SQL sorgu işleçleri için LINQ için bazı sınırlamalar vardır.  
  
### <a name="unsupported-query-operators"></a>Desteklenmeyen sorgu işleçleri  
 Yeni SQL Server tarih ve saat türlerinin eşlenen değerleri aşağıdaki sorgu işleçleri desteklenmez: `DATETIME2`, `DATE`, `TIME`, ve `DATETIMEOFFSET`.  
  
-   `Aggregate`  
  
-   `Average`  
  
-   `LastOrDefault`  
  
-   `OfType`  
  
-   `Sum`  
  
 Bu SQL Server tarih ve saat türlerinin eşleme hakkında daha fazla bilgi için bkz. [SQL-CLR tür eşlemesi](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).  
  
## <a name="sql-server-2005-support"></a>SQL Server 2005 desteği  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Aşağıdaki SQL Server 2005 özellikleri desteklemez:  
  
-   Saklı yordamlar SQL CLR için yazılır.  
  
-   Kullanıcı tanımlı tür.  
  
-   XML sorgu özellikleri.  
  
## <a name="sql-server-2000-support"></a>SQL Server 2000 desteği  
 Aşağıdaki [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] sınırlamaları (karşılaştırıldığında [!INCLUDE[sqprsqext](../../../../../../includes/sqprsqext-md.md)]) etkileyen [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] destekler.  
  
### <a name="cross-apply-and-outer-apply-operators"></a>Çapraz Uygula ve dış işleçleri Uygula  
 Bu işleçler kullanılamaz [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)]. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] bir dizi uygun birleştirmelerle değiştirilecek yeniden dener.  
  
 `Cross Apply` ve `Outer Apply` ilişki gezintiler için oluşturulur. Bu tür yeniden olası sorgu kümesi iyi tanımlı değil. Bu nedenle, en küçük grup için desteklenen sorgu [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] ilişki Gezinti içermeyen kümesidir.  
  
### <a name="text--ntext"></a>Text / ntext  
 Veri türleri `text`  /  `ntext` karşı belirli sorgu işlemleri kullanılamaz `varchar(max)`  /  `nvarchar(max)`, tarafından hangi desteklendiği [!INCLUDE[sqprsqext](../../../../../../includes/sqprsqext-md.md)].  
  
 Bu sınırlama için herhangi bir çözüm kullanılabilir. Özellikle, kullanamazsınız `Distinct()` eşlendiğine üyeleri içeren herhangi bir sonuç üzerinde `text` veya `ntext` sütunları.  
  
### <a name="behavior-triggered-by-nested-queries"></a>İç içe geçmiş sorgular tarafından tetiklenen davranışı  
 [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] (SP4), bağlayıcı iç içe geçmiş sorgular tarafından tetiklenen olmasını sağlayan bazı özelliklere sahiptir. Bu idiosyncrasies tetikleyen SQL sorguları kümesini, iyi tanımlanmış değil. Bu nedenle, bir dizi tanımlanamaz [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sorguları SQL Server özel durumlarına neden.  
  
### <a name="skip-and-take-operators"></a>Skip ve Take işleçleri  
 <xref:System.Linq.Enumerable.Take%2A> ve <xref:System.Linq.Enumerable.Skip%2A> sorguları içinde kullanıldığında belirli sınırlamaları vardır [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)]. "Atla ve SQL Server 2000'de özel durumlar'ı Al" girdisinde daha fazla bilgi için bkz. [sorun giderme](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).  
  
## <a name="object-materialization"></a>Nesne gerçekleştirme  
 Materialization bir veya daha fazla SQL sorguları tarafından döndürülen satırlar CLR nesnesi oluşturur.  
  
-   Aşağıdaki çağrıları *yerel olarak yürütüldüğü* materialization bir parçası olarak:  
  
    -   Oluşturucular  
  
    -   `ToString` projeksiyonlar yöntemleri  
  
    -   Projeksiyonlar içinde tür atamaları  
  
-   Aşağıdaki yöntemleri <xref:System.Linq.Enumerable.AsEnumerable%2A> yöntemdir *yerel olarak yürütüldüğü*. Bu yöntem, anında yürütülmesine neden olmaz.  
  
-   Kullanabileceğiniz bir `struct` dönüş türü bir sorgu sonucunun veya sonuç türünün bir üyesi olarak. Varlık sınıfları için gereklidir. Anonim türler sınıf örneklerinin gerçekleştirilmiş ancak projeksiyonda adlandırılmış yapıları (varlıklar olmayan) kullanılabilir.  
  
-   Dönüş türü bir sorgu sonucunun üyesi türünde olabilir <xref:System.Linq.IQueryable%601>. Yerel koleksiyon olarak gerçekleştirilip.  
  
-   Aşağıdaki yöntemlerden neden *hemen materialization* yöntemleri uygulanan dizisi:  
  
    -   <xref:System.Linq.Enumerable.ToList%2A>  
  
    -   <xref:System.Linq.Enumerable.ToDictionary%2A>  
  
    -   <xref:System.Linq.Enumerable.ToArray%2A>  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Başvuru](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)  
 [Dizideki Öğeleri Döndürme veya Atlama](../../../../../../docs/framework/data/adonet/sql/linq/return-or-skip-elements-in-a-sequence.md)  
 [İki Diziyi Birleştirme](../../../../../../docs/framework/data/adonet/sql/linq/concatenate-two-sequences.md)  
 [İki Dizi Arasındaki Küme Farkını Döndürme](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-difference-between-two-sequences.md)  
 [İki Dizinin Küme Kesişimini Döndürme](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-intersection-of-two-sequences.md)  
 [İki Dizinin Küme Birleşimini Döndürme](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-union-of-two-sequences.md)
