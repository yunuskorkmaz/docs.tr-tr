---
title: Null Değerleri İşleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f18b288f-b265-4bbe-957f-c6833c0645ef
ms.openlocfilehash: 763b048fcb517987931b0bdb4f5b9c5a613a05e8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794114"
---
# <a name="handling-null-values"></a>Null Değerleri İşleme
Bir sütundaki değer bilinmiyorsa veya eksik olduğunda, ilişkisel veritabanında null değer kullanılır. Null, boş bir dize (karakter veya tarih saat veri türleri için) veya sıfır değeri (sayısal veri türleri için) değil. ANSI SQL-92 belirtimi, tüm null değerleri tutarlı bir şekilde işlenebilmesi için null değeri tüm veri türleri için aynı olması gerektiğini belirtir. Ad <xref:System.Data.SqlTypes> alanı, <xref:System.Data.SqlTypes.INullable> arabirimini uygulayarak null semantikler sağlar. İçindeki <xref:System.Data.SqlTypes> veri türlerinin her biri kendi `IsNull` özelliğine sahiptir ve bu veri türü `Null` örneğine atanabilecek bir değerdir.  
  
> [!NOTE]
> .NET Framework sürüm 2,0,, programcıların bir değer türünü temel alınan türün tüm değerlerini temsil edecek şekilde genişletmesine izin veren null yapılabilir türler için destek sunmuştur. Bu clr null yapılabilir türleri <xref:System.Nullable> yapının bir örneğini temsil eder. Bu özellik, özellikle değer türleri kutulanmış ve kutulandığında, nesne türleriyle gelişmiş uyumluluk sağlayan yararlı olur. ANSI SQL null, bir `null` başvuruya (veya `Nothing` Visual Basic) göre aynı şekilde davranmadığından, clr null yapılabilir türler, veritabanı boşları depolaması için tasarlanmamıştır. Veritabanı ANSI SQL null değerleriyle çalışma için yerine null <xref:System.Data.SqlTypes> <xref:System.Nullable>değerleri kullanın. Visual Basic ' de CLR null yapılabilir türleriyle çalışma hakkında daha fazla bilgi için bkz. [Nullable değer türlerini](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) C# ve [null yapılabilir türler kullanmayı](../../../../csharp/programming-guide/nullable-types/using-nullable-types.md)görmek için.  
  
## <a name="nulls-and-three-valued-logic"></a>Null değerler ve üç değerli mantık  
 Sütun tanımlarında null değerlere izin verilmesi, uygulamanıza üç değerli mantık getirir. Karşılaştırma, üç koşuldan birini değerlendirebilir:  
  
- Doğru  
  
- False  
  
- Bilinmiyor  
  
 Null değeri bilinmiyor olarak değerlendirildiğinden, birbirleriyle karşılaştırılan iki null değer eşit kabul edilmez. Aritmetik işleçleri kullanan ifadelerde, İşlenenlerden herhangi biri null ise sonuç de null olur.  
  
## <a name="nulls-and-sqlboolean"></a>Null değerler ve SqlBoolean  
 Aralarında <xref:System.Data.SqlTypes> karşılaştırma, <xref:System.Data.SqlTypes.SqlBoolean>döndürür. <xref:System.Data.SqlTypes.SqlBoolean> Her `IsNull` biri `SqlType` için işlevi bir döndürür ve null değerleri denetlemek için kullanılabilir. Aşağıdaki Truth tablolarında, ve, veya DEĞIL işleçlerinin bir null değer varlığı içinde nasıl çalıştığı gösterilmektedir. (T = true, F = false, ve U = Unknown veya null.)  
  
 ![Truth tablosu](./media/truthtable-bpuedev11.gif "TruthTable_bpuedev11")  
  
### <a name="understanding-the-ansi_nulls-option"></a>ANSI_NULLS seçeneğini anlama  
 <xref:System.Data.SqlTypes>SQL Server ' de ANSI_NULLS seçeneğinin ayarlandığı zaman anlamlarını sağlar. Tüm aritmetik işleçler (+,-, \*,/,%), bit düzeyinde işleçler (~, & \|,) ve çoğu işlev, özellik `IsNull`hariç, işlenen veya bağımsız değişkenlerden biri null ise null döndürür.  
  
 ANSI SQL-92 standardı, WHERE yan tümcesinde *ColumnName* = null değerini desteklemez. SQL Server, ANSI_NULLS seçeneği veritabanında hem varsayılan null değer alabilme durumunu hem de null değerlere karşı karşılaştırmalar değerlendirmesini denetler. ANSI_NULLS açıksa (varsayılan), null değerleri için test edilirken deyimlerde NULL işleci kullanılmalıdır. Örneğin, ANSI_NULLS açık olduğunda aşağıdaki karşılaştırma her zaman bilinmiyor değerini verir:  
  
```  
colname > NULL  
```  
  
 Null değer içeren bir değişkene karşılaştırma de bilinmeyen bir değer verir:  
  
```  
colname > @MyVariable  
```  
  
 Null değer için test etmek üzere null veya NULL koşulunu kullanın. Burada WHERE yan tümcesine karmaşıklık eklenebilir. Örneğin, AdventureWorks Customer tablosundaki TerritoryID sütunu null değerlere izin verir. Bir SELECT ifadesinin diğer kullanıcılara ek olarak null değerler için test olması gerekiyorsa, bir IS NULL koşulu içermelidir:  
  
```  
SELECT CustomerID, AccountNumber, TerritoryID  
FROM AdventureWorks.Sales.Customer  
WHERE TerritoryID IN (1, 2, 3)  
   OR TerritoryID IS NULL  
```  
  
 SQL Server ANSI_NULLS OFF olarak ayarlarsanız, null ile karşılaştırmak için eşitlik işlecini kullanan ifadeler oluşturabilirsiniz. Ancak, bu bağlantı için farklı bağlantıların null seçeneklerini ayarlamamasını önleyebilirsiniz. Bir bağlantı için ANSI_NULLS ayarlarından bağımsız olarak, null değerler test etmek için using NULL değeri her zaman işe yarar.  
  
 ANSI_NULLS OFF ayarı, içinde null `DataSet` <xref:System.Data.SqlTypes>değerleri işlemek için her zaman ANSI SQL-92 standardını izleyen bir içinde desteklenmez.  
  
## <a name="assigning-null-values"></a>Null değerler atama  
 Null değerler özeldir ve depolama ve atama semantiği farklı tür sistemleri ve depolama sistemleri arasında farklılık gösterir. `Dataset` , Farklı tür ve depolama sistemleriyle kullanılmak üzere tasarlanmıştır.  
  
 Bu bölüm, farklı tür sistemlerinde bir <xref:System.Data.DataColumn> <xref:System.Data.DataRow> içindeki öğesine null değerler atamaya yönelik null semantiğini açıklamaktadır.  
  
 `DBNull.Value`  
 Bu atama herhangi bir `DataColumn` tür için geçerlidir. Tür uygularsa `INullable`, `DBNull.Value` uygun kesin türü belirtilmiş null değere zorlanır.  
  
 `SqlType.Null`  
 Tüm <xref:System.Data.SqlTypes> veri türleri uygular `INullable`. Türü kesin belirlenmiş null değer, örtük atama işleçleri kullanılarak sütunun veri türüne dönüştürülebiliyorsanız, atama devam etmelidir. Aksi takdirde geçersiz bir tür dönüştürme özel durumu oluşturulur.  
  
 `null`  
 ' Null `DataColumn` ' verili veri türü için geçerli bir değer ise, ilgili `DbNull.Value` veya `INullable` türü (`SqlType.Null`) ile ilişkili olan veya `Null` ilişkilendirilen  
  
 `derivedUdt.Null`  
 UDT sütunlarında, null değerler her zaman ile `DataColumn`ilişkili türüne göre saklanır. Alt sınıfı yaparken uygulamayana `DataColumn` `INullable` bir udt ile ilişkili bir udt durumunu göz önünde bulundurun. Bu durumda, türetilmiş sınıfla ilişkili kesin olarak belirlenmiş null değeri atanırsa, null depolama her zaman DataColumn 'ın veri türüyle tutarlı olduğundan türsüz `DbNull.Value`olarak depolanır.  
  
> [!NOTE]
> Veya yapısı ' de şu anda desteklenmemektedir. `DataSet` `Nullable<T>` <xref:System.Nullable>  
  
### <a name="multiple-column-row-assignment"></a>Birden çok sütun (satır) ataması  
 `DataTable.Add`, `DataTable.LoadDataRow`veya bir satıra eşlenmiş bir <xref:System.Data.DataRow.ItemArray%2A> satırı kabul eden diğer API 'ler, ' null ' değerini DataColumn 'ın varsayılan değerine eşleyin. Dizideki bir nesne veya türü kesin belirlenmiş `DbNull.Value` karşılığı içeriyorsa, yukarıda açıklanan kurallar uygulanır.  
  
 Ayrıca, aşağıdaki kurallar `DataRow.["columnName"]` null atamalarının bir örneği için geçerlidir:  
  
1. Varsayılan *varsayılan* değer `DbNull.Value` , kesin tür belirtilmiş null sütunları hariç, kesin olarak belirlenmiş null değer olan null sütunlarıdır.  
  
2. XML dosyalarına serileştirme sırasında null değerler hiçbir şekilde yazılmaz ("xsi: Nil" içinde olduğu gibi).  
  
3. Varsayılanlar dahil tüm null olmayan değerler, XML 'e serileştirilirken her zaman yazılır. Bu, null bir değer (xsi: Nil) açık ve varsayılan değer örtük (XML 'de yoksa, bir doğrulama ayrıştırıcısı onu ilişkili bir XSD şemasından alabilir) olduğu XSD/XML semantiğinin aksine. Bunun için `DataTable`ters değer true 'dur: null değeri örtük ve varsayılan değer açıktır.  
  
4. XML girişinden okunan satırlar için eksik olan tüm sütun değerlerine NULL atanır. Veya benzer yöntemler <xref:System.Data.DataTable.NewRow%2A> kullanılarak oluşturulan satırlara, DataColumn 'ın varsayılan değeri atanır.  
  
5. Yöntemi hem hem `true` de `DbNull.Value` için döndürür .`INullable.Null` <xref:System.Data.DataRow.IsNull%2A>  
  
## <a name="assigning-null-values"></a>Null değerler atama  
 Herhangi bir <xref:System.Data.SqlTypes> örnek için varsayılan değer null.  
  
 İçindeki <xref:System.Data.SqlTypes> null değerlere tür özgüdür ve gibi tek bir değerle `DbNull`temsil edilemez. Null değerleri denetlemek için özelliğinikullanın.`IsNull`  
  
 Aşağıdaki kod örneğinde gösterildiği <xref:System.Data.DataColumn> gibi, null değerler öğesine atanabilir. Özel durum tetiklemeden, `SqlTypes` değişkenlere doğrudan null değerler atayabilirsiniz.  
  
### <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, ve <xref:System.Data.DataTable> <xref:System.Data.SqlTypes.SqlString>şeklinde <xref:System.Data.SqlTypes.SqlInt32> tanımlanmış iki sütunlu bir ile oluşturur. Kod, bir dizi null değeri olan bilinen değerlerin bir satırını ekler ve sonra, <xref:System.Data.DataTable>değerlerini değişkenlere atayarak ve çıktıyı konsol penceresinde görüntüleyerek ' de dolaşır.  
  
 [!code-csharp[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/VB/source.vb#1)]  
  
 Bu örnek aşağıdaki sonuçları görüntüler:  
  
```  
isColumnNull=False, ID=123, Description=Side Mirror  
isColumnNull=True, ID=Null, Description=Null  
```  
  
## <a name="comparing-null-values-with-sqltypes-and-clr-types"></a>Null değerleri SqlTypes ve CLR türleriyle karşılaştırma  
 Null değerleri karşılaştırırken, `Equals` yöntemin clr türleriyle çalışma yöntemiyle karşılaştırıldığında ' de <xref:System.Data.SqlTypes> null değerleri değerlendirme şekli arasındaki farkı anlamak önemlidir. <xref:System.Data.SqlTypes> Tümyöntemlernulldeğerlerinideğerlendirmekiçinveritabanısemantiğinikullanır:değerlerdenbiriveyaherikisinullise,`Equals` karşılaştırma null değerini verir. Öte yandan, her ikisi de null ise `Equals` , clr yönteminin <xref:System.Data.SqlTypes> ikisi üzerinde kullanılması true olur. Bu, clr `String.Equals` yöntemi gibi bir örnek yöntemi kullanma ve statik/paylaşılan `SqlString.Equals`yöntemi kullanma arasındaki farkı yansıtır.  
  
 Aşağıdaki örnek, her biri null değer çifti ve daha `SqlString.Equals` sonra boş dizeler `String.Equals` çifti geçirildiğinde yöntemi ve yöntemi arasındaki sonuçların farkını gösterir.  
  
 [!code-csharp[DataWorks SqlTypes.CompareNulls#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.CompareNulls/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.CompareNulls#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.CompareNulls/VB/source.vb#1)]  
  
 Kod aşağıdaki çıktıyı üretir:  
  
```  
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
