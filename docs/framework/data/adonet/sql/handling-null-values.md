---
title: Null Değerleri İşleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f18b288f-b265-4bbe-957f-c6833c0645ef
ms.openlocfilehash: c64f11c00174981925342f1493ef0b809a57ecb0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148653"
---
# <a name="handling-null-values"></a>Null Değerleri İşleme
Bir sütundaki değer bilinmiyor veya eksik olduğunda ilişkisel veritabanındaki null değeri kullanılır. Null ne boş bir dize (karakter veya datetime veri türleri için) ne de sıfır değeri (sayısal veri türleri için) olduğunu. ANSI SQL-92 belirtimi, tüm veri türleri için bir null'un aynı olması gerektiğini, böylece tüm null'ların tutarlı bir şekilde işleneceğini belirtir. Ad <xref:System.Data.SqlTypes> alanı <xref:System.Data.SqlTypes.INullable> arabirimi uygulayarak null semantik sağlar. Veri <xref:System.Data.SqlTypes> türlerinin her birinin `IsNull` kendi özelliği `Null` ve bu veri türünün bir örneğine atanabilecek bir değeri vardır.  
  
> [!NOTE]
> .NET Framework sürüm 2.0, programcıların temel türün tüm değerlerini temsil edecek bir değer türünü genişletmesine olanak tanıyan boşta kalınan türler için destek sunmuyor. Bu CLR geçersiz türleri yapının <xref:System.Nullable> bir örneğini temsil ediyor. Bu özellik, özellikle değer türleri kutulandığında ve kutudan çözüldüğünde, nesne türleri ile gelişmiş uyumluluk sağlar. BIR ANSI SQL null `null` bir başvuru (veya `Nothing` Visual Basic) aynı şekilde tedavi etmez, çünkü CLR nullable türleri veritabanı nulls depolama için tasarlanmamıştır. Veritabanı ANSI SQL null değerleri <xref:System.Data.SqlTypes> ile çalışmak <xref:System.Nullable>için, yerine nulls kullanın. Visual Basic'teki CLR nullable türleri ile çalışma hakkında daha fazla bilgi için [Nullable Value Types'a](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)ve C# için [Nullable değer türlerine](../../../../csharp/language-reference/builtin-types/nullable-value-types.md)bakın.  
  
## <a name="nulls-and-three-valued-logic"></a>Nulls ve Üç Değerli Mantık  
 Sütun tanımlarında null değerlerine izin vermek, uygulamanıza üç değerli mantık sunar. Bir karşılaştırma üç koşuldan birine değerlendirilebilir:  
  
- True  
  
- False  
  
- Bilinmiyor  
  
 Null bilinmeyen olarak kabul edilir, birbirlerine göre iki null değerleri eşit olarak kabul edilmez. Aritmetik işleçler kullanılarak yapılan ifadelerde, operandlardan herhangi biri null ise, sonuç da null'dur.  
  
## <a name="nulls-and-sqlboolean"></a>Nulls ve SqlBoolean  
 Herhangi <xref:System.Data.SqlTypes> bir döndürecek arasında karşılaştırma bir <xref:System.Data.SqlTypes.SqlBoolean>. Her `IsNull` `SqlType` bir a <xref:System.Data.SqlTypes.SqlBoolean> döndürür ve null değerleri denetlemek için kullanılabilir işlevi. Aşağıdaki doğruluk tabloları, AND, OR ve NOT işleçlerinin null bir değerin varlığında nasıl çalıştığını gösterir. (T=true, F=false ve U=bilinmeyen veya null.)  
  
 ![Hakikat Tablosu](./media/truthtable-bpuedev11.gif "TruthTable_bpuedev11")  
  
### <a name="understanding-the-ansi_nulls-option"></a>ANSI_NULLS Seçeneğini Anlama  
 <xref:System.Data.SqlTypes>ANSI_NULLS seçeneği SQL Server'da ayarlandığında olduğu gibi aynı anlambilimi sağlar. Tüm aritmetik işleçler \*(+, -, ,,,%), \|bitwise işleçleri (~, &, ), ve çoğu fonksiyon, `IsNull`operands veya bağımsız değişkenlerden herhangi biri geçersiz ise, özellik dışında geçersiz dir.  
  
 ANSI SQL-92 standardı WHERE yan tümcesindeki *columnName* = NULL'u desteklemez. SQL Server'da, ANSI_NULLS seçeneği hem veritabanındaki varsayılan nullability'ı hem de null değerlerle karşılaştırmaların değerlendirilmesini denetler. ANSI_NULLS açıksa (varsayılan), null değerleri sınarken IS NULL işleci ifadelerde kullanılmalıdır. Örneğin, aşağıdaki karşılaştırma her zaman ANSI_NULLS olduğunda bilinmeyen verir:  
  
```sql
colname > NULL  
```  
  
 Null değeri içeren bir değişkenle karşılaştırıldığında da bilinmeyen verir:  
  
```sql
colname > @MyVariable  
```  
  
 Null değeri için test etmek için IS NULL veya NOT NULL yüklemi kullanın. Bu, WHERE yan tümcesine karmaşıklık ekleyebilir. Örneğin, AdventureWorks Müşteri tablosundaki TerritoryID sütunu null değerlere izin verir. SELECT deyimi diğerlerine ek olarak null değerleri sınamak için sınanacaksa, bir IS NULL yüklemi içermelidir:  
  
```sql
SELECT CustomerID, AccountNumber, TerritoryID  
FROM AdventureWorks.Sales.Customer  
WHERE TerritoryID IN (1, 2, 3)  
   OR TerritoryID IS NULL  
```  
  
 ANSI_NULLS SQL Server'da ayarlarsanız, null ile karşılaştırmak için eşitlik işlecikullanan ifadeler oluşturabilirsiniz. Ancak, farklı bağlantıların bu bağlantı için null seçenekleri ayarlamasını engelleyemezsiniz. Null değerlerini sınamak için IS NULL'u kullanmak, bağlantı ayarlarının ANSI_NULLS bakılmaksızın her zaman çalışır.  
  
 ANSI_NULLS'yi kapatma, her `DataSet`zaman null değerlerini işlemek için ANSI SQL-92 <xref:System.Data.SqlTypes>standardını izleyen bir ' de desteklenmez.  
  
## <a name="assigning-null-values"></a>Null Değerleri Atama  
 Null değerleri özeldir ve depolama ve atama semantikfarklı tip sistemleri ve depolama sistemleri arasında farklılık gösterir. A `Dataset` farklı tip ve depolama sistemleri ile kullanılmak üzere tasarlanmıştır.  
  
 Bu bölümde, farklı tür sistemlerinde bir null <xref:System.Data.DataColumn> <xref:System.Data.DataRow> değerleri atamak için null semantics açıklanır.  
  
 `DBNull.Value`  
 Bu atama herhangi `DataColumn` bir tür için geçerlidir. Tür `INullable`uygularsa, `DBNull.Value` uygun güçlü olarak yazılan Null değerine zorlanılır.  
  
 `SqlType.Null`  
 Tüm <xref:System.Data.SqlTypes> veri `INullable`türleri uygular. Güçlü bir şekilde yazılan null değeri, örtülü döküm işleçleri kullanılarak sütunun veri türüne dönüştürülebilirse, atama geçmelidir. Aksi takdirde geçersiz bir döküm özel durum atılır.  
  
 `null`  
 'Null' verilen `DataColumn` `DbNull.Value` veri türü için yasal bir değerse, uygun veya `Null` `INullable` türle ilişkili`SqlType.Null`olarak zorlanır ( )  
  
 `derivedUdt.Null`  
 UDT sütunları için nulls her zaman . `DataColumn` Alt sınıfı uygularken uygulanmayan `DataColumn` `INullable` bir UDT'nin durumunu göz önünde bulundurun. Bu durumda, türemiş sınıfla ilişkili güçlü bir şekilde yazılan null değeri atanmışsa, null depolama her zaman DataColumn'un veri türüyle tutarlı olduğundan, bu değer yazılmamış `DbNull.Value`olarak depolanır.  
  
> [!NOTE]
> Veya `Nullable<T>` <xref:System.Nullable> yapı şu anda `DataSet`desteklenmiyor.  
  
### <a name="multiple-column-row-assignment"></a>Çoklu Sütun (Satır) Atama  
 `DataTable.Add`, `DataTable.LoadDataRow`' veya bir satıra eşlenen bir <xref:System.Data.DataRow.ItemArray%2A> kabul eden diğer API'ler, DataColumn'un varsayılan değerine 'null' eşle. Dizideki bir nesne `DbNull.Value` veya güçlü bir şekilde yazılan karşıtlığını içeriyorsa, yukarıda açıklandığı gibi aynı kurallar uygulanır.  
  
 Buna ek olarak, boş atamaların `DataRow.["columnName"]` bir örneği için aşağıdaki kurallar geçerlidir:  
  
1. Varsayılan *varsayılan* değer, `DbNull.Value` uygun olarak güçlü bir şekilde yazılan null değeri olan güçlü bir şekilde yazılan null sütunlar hariç tüm değerler içindir.  
  
2. Null değerleri XML dosyalarına serileştirme sırasında asla yazılmaz ("xsi:nil"de olduğu gibi).  
  
3. Varsayılanlar da dahil olmak üzere tüm null olmayan değerler, XML'e seri yazarken her zaman yazılır. Bu, null değerinin (xsi:nil) açık olduğu ve varsayılan değerin örtülü olduğu XSD/XML semantiklerinden farklı olarak (XML'de yoksa, doğrulayıcı bir parlayıcı bunu ilişkili bir XSD şemasından alabilir). Tersi bir `DataTable`için geçerlidir: null değeri örtülü ve varsayılan değer açık.  
  
4. XML girişinden okunan satırlar için tüm eksik sütun değerleri NULL atanır. Veri Sütunu <xref:System.Data.DataTable.NewRow%2A> varsayılan değeri kullanılarak oluşturulan satırlara veya benzer yöntemlere atanır.  
  
5. Yöntem <xref:System.Data.DataRow.IsNull%2A> her `true` ikisi `DbNull.Value` `INullable.Null`için de döndürür ve .  
  
## <a name="assigning-null-values"></a>Null Değerleri Atama  
 Herhangi bir <xref:System.Data.SqlTypes> örnek için varsayılan değer null'dur.  
  
 Nulls <xref:System.Data.SqlTypes> türüne özgüdür ve `DbNull`gibi tek bir değerle temsil edilemez. Nulls `IsNull` kontrol etmek için özelliği kullanın.  
  
 Null değerleri aşağıdaki kod <xref:System.Data.DataColumn> örneğinde gösterildiği gibi bir atanabilir. Bir özel durum tetiklemeden değişkenlere `SqlTypes` doğrudan null değerleri atayabilirsiniz.  
  
### <a name="example"></a>Örnek  
 Aşağıdaki kod örneği olarak <xref:System.Data.DataTable> <xref:System.Data.SqlTypes.SqlInt32> tanımlanan iki sütun <xref:System.Data.SqlTypes.SqlString>ve . Kod, bilinen değerlerden oluşan bir satır, bir null değer <xref:System.Data.DataTable>satırı ve ardından değişkenlere değerleri atama ve çıktıyı konsol penceresinde görüntüleme yoluyla yineler.  
  
 [!code-csharp[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/VB/source.vb#1)]  
  
 Bu örnekte aşağıdaki sonuçlar görüntülenir:  
  
```output
isColumnNull=False, ID=123, Description=Side Mirror  
isColumnNull=True, ID=Null, Description=Null  
```  
  
## <a name="comparing-null-values-with-sqltypes-and-clr-types"></a>Null Değerlerini SqlTypes ve CLR Türleri ile Karşılaştırma  
 Null değerleri karşılaştırırken, `Equals` yöntemin null değerleri <xref:System.Data.SqlTypes> CLR türleri ile çalışma şekliyle karşılaştırıldığında değerlendirme şekli arasındaki farkı anlamak önemlidir. <xref:System.Data.SqlTypes> Tüm yöntemler null değerlerini değerlendirmek için veritabanı semantiklerini kullanır: değerlerden biri veya her ikisi de null ise, karşılaştırma null `Equals` verir. Diğer taraftan, clr `Equals` yöntemini iki <xref:System.Data.SqlTypes> de kullanmak, her ikisi de null ise doğru olacaktır. Bu, CLR `String.Equals` yöntemi gibi bir örnek yöntemi kullanarak statik/paylaşılan yöntemi kullanma `SqlString.Equals`arasındaki farkı yansıtır.  
  
 Aşağıdaki örnek, yöntem ve `SqlString.Equals` `String.Equals` yöntem arasındaki sonuçlardaki farkı, her biri bir null değer çifti ve daha sonra boş dizeleri bir çift geçirildiğinde gösterir.  
  
 [!code-csharp[DataWorks SqlTypes.CompareNulls#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.CompareNulls/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.CompareNulls#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.CompareNulls/VB/source.vb#1)]  
  
 Kod aşağıdaki çıktıyı üretir:  
  
```output
SqlString.Equals shared/static method:  
  Two nulls=Null  
  
String.Equals instance method:  
  Two nulls=True  
  
SqlString.Equals shared/static method:  
  Two empty strings=True  
  
String.Equals instance method:  
  Two empty strings=True
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SQL Server Veri Türleri ve ADO.NET](sql-server-data-types.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
