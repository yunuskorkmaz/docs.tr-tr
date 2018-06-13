---
title: Standart sorgu işleci çevirisi
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a60c30fa-1e68-45fe-b984-f6abb9ede40e
ms.openlocfilehash: b05cd427bc1b3b13b68fe7c38a798c8c2baa0af1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33365819"
---
# <a name="standard-query-operator-translation"></a>Standart sorgu işleci çevirisi
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Standart sorgu işleçleri için SQL komutlarını çevirir. Sorgu işlemcisi veritabanının SQL çeviri yürütme semantiği belirler.  
  
 Standart sorgu işleçleri karşı tanımlanmış *sıraları*. Bir sıra *sıralı* ve dizideki her öğe için başvuru kimliği dayanır. Daha fazla bilgi için bkz: [standart sorgu işleçlerine genel bakış](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).  
  
 SQL ilgilenir öncelikli olarak *değerlerin kümeleri sıralanmamış*. Sıralama olan genellikle bir açıkça belirtilen, bir sorgu sonucunu yerine Ara sonuçların uygulanan sonrası işlem. Kimlik değerleri tarafından tanımlanır. Bu nedenle, multisets ile mücadele etmek için SQL sorguları anlaşılır (*paketler*) yerine *ayarlar*.  
  
 Standart sorgu işleçleri ve SQL Server sağlayıcısı için kendi SQL çevirisi arasındaki farklar aşağıdaki paragraflara açıklamak [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
## <a name="operator-support"></a>İşleç desteği  
  
### <a name="concat"></a>concat  
 <xref:System.Linq.Enumerable.Concat%2A> Yöntemi alıcı sırasını ve bağımsız değişkeni sırasını nerede aynı sıralı multisets için tanımlanır. <xref:System.Linq.Enumerable.Concat%2A> olarak çalışır `UNION ALL` genel sıraya göre ve ardından multisets üzerinden.  
  
 Sonuçları üretilen önce son adım SQL'de sıralama. <xref:System.Linq.Enumerable.Concat%2A> bağımsız değişkenlerini sırasını korumaz. Uygun sıralama emin olmak için açıkça sonuçlarını sıralama gerekir <xref:System.Linq.Enumerable.Concat%2A>.  
  
### <a name="intersect-except-union"></a>Dışında UNION, INTERSECT  
 <xref:System.Linq.Enumerable.Intersect%2A> Ve <xref:System.Linq.Enumerable.Except%2A> yöntemleri yalnızca kümeleri üzerinde iyi tanımlanmış. Multisets anlamları tanımlanmamıştır.  
  
 <xref:System.Linq.Enumerable.Union%2A> Yöntemi multisets için (etkili bir şekilde UNION ALL yan tümcesi SQL sonuç) multisets sırasız birleşimini olarak tanımlanır.  
  
### <a name="take-skip"></a>Al, Atla  
 <xref:System.Linq.Enumerable.Take%2A> ve <xref:System.Linq.Enumerable.Skip%2A> yöntemleri yalnızca karşı iyi tanımlanmış *kümeleri sıralı*. Sırasız kümeleri veya multisets anlamları tanımlanmamış.  
  
> [!NOTE]
>  <xref:System.Linq.Enumerable.Take%2A> ve <xref:System.Linq.Enumerable.Skip%2A> SQL Server 2000 karşı sorgularda kullanıldığında belirli sınırlamaları vardır. Daha fazla bilgi için "Atlayın ve SQL Server 2000'de özel durumlar alın" girdisinde bkz [sorun giderme](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).  
  
 SQL'de sıralama sınırlamalar nedeniyle [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] yöntemi için bu yöntemlerin bağımsız değişkeni sıralama taşımayı dener. Örneğin, aşağıdakileri göz önünde bulundurun [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sorgu:  
  
 [!code-csharp[DLinqSQOTranslation#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#1)]
 [!code-vb[DLinqSQOTranslation#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#1)]  
  
 Bu kodun oluşturulan SQL gibi sonuna sıralama taşır:  
  
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
  
 Tüm belirtilen sıralama ne zaman tutarlı olması gerektiğini belirgin hale <xref:System.Linq.Enumerable.Take%2A> ve <xref:System.Linq.Enumerable.Skip%2A> birbirine zincirlenmiş. Aksi takdirde, sonuçları tanımlanmamış.  
  
 Her ikisi de <xref:System.Linq.Enumerable.Take%2A> ve <xref:System.Linq.Enumerable.Skip%2A> standart sorgu işleci belirtimine dayalı negatif olmayan, sabit tamsayı bağımsız değişkenler için iyi tanımlanmış olması.  
  
### <a name="operators-with-no-translation"></a>Çeviri işleçleri  
 Aşağıdaki yöntemlerden tarafından çevrilmesi değil [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. En yaygın nedeni, sırasız multisets ve dizilerinin arasındaki farktır.  
  
|İşleçler|Stratejinin|  
|---------------|---------------|  
|<xref:System.Linq.Enumerable.TakeWhile%2A>, <xref:System.Linq.Enumerable.SkipWhile%2A>|SQL sorguları sıraları üzerinde multisets çalışmayabilir. `ORDER BY` Son yan tümce sonuçları uygulanmış olması gerekir. Bu nedenle, bu iki yöntem için genel amaçlı çeviri yok.|  
|<xref:System.Linq.Enumerable.Reverse%2A>|Bu yöntemin çeviri sıralanmış bir küme için mümkün olmakla birlikte tarafından şu anda çevrilmemiştir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].|  
|<xref:System.Linq.Enumerable.Last%2A>, <xref:System.Linq.Enumerable.LastOrDefault%2A>|Bu yöntemlerin çeviri sıralanmış bir küme için mümkün olmakla birlikte tarafından şu anda çevrilmemiştir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].|  
|<xref:System.Linq.Enumerable.ElementAt%2A>, <xref:System.Linq.Enumerable.ElementAtOrDefault%2A>|SQL sorguları dizine sıraları üzerinde multisets çalışmayabilir.|  
|<xref:System.Linq.Enumerable.DefaultIfEmpty%2A> (varsayılan arg ile aşırı yükleme)|Genel olarak, varsayılan bir değer için rasgele bir tanımlama grubu belirtilemez. Diziler için null değerler dış birleştirmeler aracılığıyla bazı durumlarda mümkün olabilir.|  
  
## <a name="expression-translation"></a>İfade çevirisi  
  
### <a name="null-semantics"></a>Null semantiği  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] SQL'de null karşılaştırma semantiği getirmez. Karşılaştırma işleçleri sözdizimsel olarak SQL eşdeğerlerine çevrilir. Bu nedenle, sunucu veya bağlantı ayarları tarafından tanımlanan SQL semantiği semantiğini yansıtır. Örneğin, iki null değerler varsayılan SQL Server Ayarları altında eşit olarak kabul edilir, ancak semantiğini değiştirmek için ayarları değiştirebilirsiniz. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sorguları dönüştürdüğünde sunucu ayarlarını dikkate almaz.  
  
 Değişmez değer null ile bir karşılaştırması için uygun SQL sürümü çevrilir (`is null` veya `is not null`).  
  
 Değeri `null` harmanlamasında SQL Server tarafından tanımlanır. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] harmanlama değiştirmez.  
  
### <a name="aggregates"></a>Toplamlar  
 Standart sorgu işleci toplama yöntemi <xref:System.Linq.Enumerable.Sum%2A> sıfır yalnızca null içeren bir dizi veya boş bir dizi için değerlendirir. İçinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], SQL semantiği sol değiştirmeden, ve <xref:System.Linq.Enumerable.Sum%2A> değerlendiren `null` sıfır boş bir dizi veya yalnızca null içeren bir dizi yerine.  
  
 Ara sonuçların SQL sınırlamalar uygulanır Toplamaların [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. <xref:System.Linq.Enumerable.Sum%2A> 32 bit tamsayı miktarları hesaplanan 64-bit sonuçları kullanarak. Taşma için oluşabilir bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] çevrilmesi <xref:System.Linq.Enumerable.Sum%2A>standart sorgu işleci uygulama karşılık gelen bellek içi dizisi taşma neden olmaz olsa bile.  
  
 Benzer şekilde, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] çevrilmesi <xref:System.Linq.Enumerable.Average%2A> değerler tamsayı hesaplanan olarak bir `integer`, olarak değil bir `double`.  
  
### <a name="entity-arguments"></a>Varlık bağımsız değişkenler  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] varlık türleri kullanılmak üzere etkinleştirir <xref:System.Linq.Enumerable.GroupBy%2A> ve <xref:System.Linq.Enumerable.OrderBy%2A> yöntemleri. Bu işleçlere çeviriyi türünde bir bağımsız değişken kullanımını bu türdeki tüm üyelerin belirtmek için eşdeğer olarak kabul edilir. Örneğin, aşağıdaki kodu eşdeğerdir:  
  
 [!code-csharp[DLinqSQOTranslation#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#2)]
 [!code-vb[DLinqSQOTranslation#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#2)]  
  
### <a name="equatable--comparable-arguments"></a>Equatable / karşılaştırılabilir bağımsız değişkenler  
 Bağımsız değişkenleri eşitlik için aşağıdaki yöntemlerden birini uygulamasında gereklidir:  
  
 <xref:System.Linq.Enumerable.Contains%2A>  
  
 <xref:System.Linq.Enumerable.Skip%2A>  
  
 <xref:System.Linq.Enumerable.Union%2A>  
  
 <xref:System.Linq.Enumerable.Intersect%2A>  
  
 <xref:System.Linq.Enumerable.Except%2A>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Eşitlik ve karşılaştırma için destekleyen *düz* bağımsız değişkenleri, ancak değil veya sıraları içeriyor bağımsız. Düz bir bağımsız değişken için bir SQL satır eşlenebilir. bir türüdür. Statik olarak bir dizi içermemesi belirlenebilir bir veya daha fazla varlık türlerinin bir yansıtma düz bir bağımsız değişken olarak kabul edilir.  
  
 Düz bağımsız değişkenleri örnekleri şunlardır:  
  
 [!code-csharp[DLinqSQOTranslation#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#3)]
 [!code-vb[DLinqSQOTranslation#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#3)]  
  
 Olmayan-düz (hiyerarşik) bağımsız değişkenleri örnekleri verilmiştir.  
  
 [!code-csharp[DLinqSQOTranslation#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#4)]
 [!code-vb[DLinqSQOTranslation#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#4)]  
  
### <a name="visual-basic-function-translation"></a>Visual Basic işlevi çevirisi  
 Visual Basic derleyici tarafından kullanılan aşağıdaki yardımcı işlevleri karşılık gelen SQL işleçler ve işlevleri dönüştürülür:  
  
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
 Daha fazla bilgi için bkz: [nasıl yapılır: eşleme devralma hiyerarşileri](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-inheritance-hierarchies.md).  
  
### <a name="inheritance-in-queries"></a>Sorgularda devralma  
 C# atamalar yalnızca projeksiyon desteklenir. Başka bir yerde kullanılan atamalar dönüştürülmez ve göz ardı edilir. SQL yanı sıra işlev adları, SQL gerçekten yalnızca ortak dil çalışma zamanı (CLR) denk gerçekleştirir <xref:System.Convert>. Diğer bir deyişle, SQL bir türü değeri diğerine değiştirebilirsiniz. Başka bir tür olarak aynı BITS reinterpreting hiçbir kavramı olduğundan cast CLR'ın eşdeğeri yoktur. C# cast works neden yalnızca yerel olarak olmasıdır. Düğümlerde değil.  
  
 İşleçler `is` ve `as`ve `GetType` yöntem sınırlı değildir `Select` işleci. Bunlar ayrıca diğer sorgu işleçleri kullanılabilir.  
  
## <a name="sql-server-2008-support"></a>SQL Server 2008 desteği  
 LINQ-SQL, .NET Framework 3.5 SP1 ile başlayarak, yeni bir tarih ve saat türleri SQL Server 2008 ile sunulan eşleme destekler. Ancak, bu yeni tür eşlenen değerleri karşı çalışırken kullanabileceğiniz SQL sorgu işleçleri için LINQ için bazı kısıtlamalar vardır.  
  
### <a name="unsupported-query-operators"></a>Desteklenmeyen sorgu işleçleri  
 Aşağıdaki sorgu işleçleri yeni SQL Server tarih ve saat türleri eşlenen değerler desteklenmez: `DATETIME2`, `DATE`, `TIME`, ve `DATETIMEOFFSET`.  
  
-   `Aggregate`  
  
-   `Average`  
  
-   `LastOrDefault`  
  
-   `OfType`  
  
-   `Sum`  
  
 Bu SQL Server tarih ve saat türler için eşleme hakkında daha fazla bilgi için bkz: [SQL CLR türü eşlemesi](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).  
  
## <a name="sql-server-2005-support"></a>SQL Server 2005 desteği  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Aşağıdaki SQL Server 2005 özellikleri desteklemez:  
  
-   Saklı yordamlar SQL CLR yazılır.  
  
-   Kullanıcı tanımlı tür.  
  
-   XML sorgu özellikleri.  
  
## <a name="sql-server-2000-support"></a>SQL Server 2000 desteği  
 Aşağıdaki [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] sınırlamaları (karşılaştırılan [!INCLUDE[sqprsqext](../../../../../../includes/sqprsqext-md.md)]) etkileyen [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] destekler.  
  
### <a name="cross-apply-and-outer-apply-operators"></a>Çapraz uygulama ve dış işleçleri Uygula  
 Bu işleçlere kullanılamayan [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)]. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] bir dizi bunları uygun birleştirmeler ile değiştirmek için yeniden çalışır.  
  
 `Cross Apply` ve `Outer Apply` ilişki gezintilerini için oluşturulur. Bu tür yeniden yazdırmaya olası sorgu kümesini iyi tanımlanmış değil. Bu nedenle, desteklenen sorguları en az sayıda [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] ilişki Gezinti içermeyen kümesidir.  
  
### <a name="text--ntext"></a>Text / ntext  
 Veri türleri `text`  /  `ntext` belirli sorgu işlemleri karşı kullanılamaz `varchar(max)`  /  `nvarchar(max)`, tarafından desteklenen [!INCLUDE[sqprsqext](../../../../../../includes/sqprsqext-md.md)].  
  
 Herhangi bir çözüm, bu sınırlamaya için kullanılabilir. Özellikle, kullanamazsınız `Distinct()` eşlendiği üyeleri içeren sonuç üzerinde `text` veya `ntext` sütun.  
  
### <a name="behavior-triggered-by-nested-queries"></a>İç içe geçmiş sorgular tarafından tetiklenen davranışı  
 [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] (SP4) bağlayıcı iç içe geçmiş sorgular tarafından tetiklenen olmasını sağlayan bazı özelliklere sahiptir. Bu idiosyncrasies tetikler SQL sorguları kümesini iyi tanımlanmış değil. Bu nedenle, kümesini tanımlayamazsınız [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sorguları SQL Server özel durumlara neden olabilir.  
  
### <a name="skip-and-take-operators"></a>Atla ve Al işleçleri  
 <xref:System.Linq.Enumerable.Take%2A> ve <xref:System.Linq.Enumerable.Skip%2A> karşı sorgularda kullanıldığında belirli sınırlamaları vardır [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)]. Daha fazla bilgi için "Atlayın ve SQL Server 2000'de özel durumlar alın" girdisinde bkz [sorun giderme](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).  
  
## <a name="object-materialization"></a>Nesne Materialization  
 Materialization bir veya daha fazla SQL sorguları tarafından döndürülen satır CLR nesneleri oluşturur.  
  
-   Aşağıdaki çağrıları *yerel olarak yürütülen* materialization bir parçası olarak:  
  
    -   Oluşturucular  
  
    -   `ToString` projeksiyonlar yöntemleri  
  
    -   Projeksiyonlar tür atamaları  
  
-   İzleyin yöntemleri <xref:System.Linq.Enumerable.AsEnumerable%2A> yönteminin *yerel olarak çalıştırılan*. Bu yöntem, hemen yürütülmesine neden olmaz.  
  
-   Kullanabileceğiniz bir `struct` sonuç türünün bir üyesi olarak veya bir sorgu sonucunun dönüş türü. Varlıkları sınıfları olması gerekir. Anonim türler sınıf örnekleri gerçekleştirilip ancak projeksiyon adlandırılmış yapılar (varlıklar olmayan) kullanılabilir.  
  
-   Dönüş türü bir sorgu sonucunun üyesi türde olabilir <xref:System.Linq.IQueryable%601>. Yerel bir koleksiyon olarak gerçekleştirildiği.  
  
-   Aşağıdaki yöntemlerden neden *hemen materialization* yöntemleri uygulanır dizisi:  
  
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
