---
title: Null Değerleri İşleme
description: SQL Server için .NET Framework Veri Sağlayıcısı null işleme hakkında bilgi edinin ve null ve SqlBoolean, üç değerli mantığı ve null değerler atamayı okuyun.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f18b288f-b265-4bbe-957f-c6833c0645ef
ms.openlocfilehash: 2ed2a88b91f06bb02c72d3e310ae09d58637205f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197475"
---
# <a name="handling-null-values"></a>Null Değerleri İşleme

Bir sütundaki değer bilinmiyorsa veya eksik olduğunda, ilişkisel veritabanında null değer kullanılır. Null, boş bir dize (karakter veya tarih saat veri türleri için) veya sıfır değeri (sayısal veri türleri için) değil. ANSI SQL-92 belirtimi, tüm null değerleri tutarlı bir şekilde işlenebilmesi için null değeri tüm veri türleri için aynı olması gerektiğini belirtir. <xref:System.Data.SqlTypes>Ad alanı, arabirimini uygulayarak null semantikler sağlar <xref:System.Data.SqlTypes.INullable> . İçindeki veri türlerinin her biri <xref:System.Data.SqlTypes> kendi `IsNull` özelliğine sahiptir ve `Null` Bu veri türü örneğine atanabilecek bir değerdir.  
  
> [!NOTE]
> .NET Framework sürüm 2,0,, programcıların bir değer türünü temel alınan türün tüm değerlerini temsil edecek şekilde genişletmesine izin veren null yapılabilir değer türleri için destek sunmuştur. Bu CLR null yapılabilir değer türleri yapının bir örneğini temsil eder <xref:System.Nullable> . Bu özellik, özellikle değer türleri kutulanmış ve kutulandığında, nesne türleriyle gelişmiş uyumluluk sağlayan yararlı olur. ANSI SQL null değeri bir `null` başvuru (veya Visual Basic) ile aynı şekilde davranmadığından, clr null yapılabilir değer türleri veritabanı boş değerlerini depolamak için tasarlanmamıştır `Nothing` . Veritabanı ANSI SQL null değerleriyle çalışma için yerine null değerleri kullanın <xref:System.Data.SqlTypes> <xref:System.Nullable> . Visual Basic ' de CLR değeri null yapılabilir türleriyle çalışma hakkında daha fazla bilgi için bkz. [Nullable değer türlerini](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)görüntüle ve C# için bkz. [Nullable değer türleri](../../../../csharp/language-reference/builtin-types/nullable-value-types.md).  
  
## <a name="nulls-and-three-valued-logic"></a>Null değerler ve üç değerli mantık  

 Sütun tanımlarında null değerlere izin verilmesi, uygulamanıza üç değerli mantık getirir. Karşılaştırma, üç koşuldan birini değerlendirebilir:  
  
- Doğru  
  
- Yanlış  
  
- Bilinmiyor  
  
 Null değeri bilinmiyor olarak değerlendirildiğinden, birbirleriyle karşılaştırılan iki null değer eşit kabul edilmez. Aritmetik işleçleri kullanan ifadelerde, İşlenenlerden herhangi biri null ise sonuç de null olur.  
  
## <a name="nulls-and-sqlboolean"></a>Null değerler ve SqlBoolean  

 Aralarında karşılaştırma <xref:System.Data.SqlTypes> , döndürür <xref:System.Data.SqlTypes.SqlBoolean> . `IsNull`Her biri için işlevi `SqlType` bir döndürür <xref:System.Data.SqlTypes.SqlBoolean> ve null değerleri denetlemek için kullanılabilir. Aşağıdaki Truth tablolarında, ve, veya DEĞIL işleçlerinin bir null değer varlığı içinde nasıl çalıştığı gösterilmektedir. (T = true, F = false, ve U = Unknown veya null.)  
  
 ![Truth tablosu](./media/truthtable-bpuedev11.gif "TruthTable_bpuedev11")  
  
### <a name="understanding-the-ansi_nulls-option"></a>ANSI_NULLS seçeneğini anlama  

 <xref:System.Data.SqlTypes> SQL Server ' de ANSI_NULLS seçeneğinin ayarlandığı anlamlarını sağlar. Tüm aritmetik işleçler (+,-, \* ,/,%), bit düzeyinde işleçler (~, &, \| ) ve çoğu işlev, özellik hariç, işlenen veya bağımsız değişkenlerden biri null ise null döndürür `IsNull` .  
  
 ANSI SQL-92 standardı, WHERE yan tümcesinde *ColumnName* = null değerini desteklemez. SQL Server, ANSI_NULLS seçeneği veritabanında hem varsayılan null değer alabilme durumunu hem de null değerlere karşı karşılaştırmalar değerlendirmesini denetler. ANSI_NULLS açıksa (varsayılan), null değerleri için test edilirken deyimlerde NULL işleci kullanılmalıdır. Örneğin, ANSI_NULLS olduğunda aşağıdaki karşılaştırma her zaman bilinmiyor olarak verir:  
  
```sql
colname > NULL  
```  
  
 Null değer içeren bir değişkene karşılaştırma de bilinmeyen bir değer verir:  
  
```sql
colname > @MyVariable  
```  
  
 Null değer için test etmek üzere null veya NULL koşulunu kullanın. Burada WHERE yan tümcesine karmaşıklık eklenebilir. Örneğin, AdventureWorks Customer tablosundaki TerritoryID sütunu null değerlere izin verir. Bir SELECT ifadesinin diğer kullanıcılara ek olarak null değerler için test olması gerekiyorsa, bir IS NULL koşulu içermelidir:  
  
```sql
SELECT CustomerID, AccountNumber, TerritoryID  
FROM AdventureWorks.Sales.Customer  
WHERE TerritoryID IN (1, 2, 3)  
   OR TerritoryID IS NULL  
```  
  
 SQL Server ANSI_NULLS devre dışı bırakırsanız, null ile karşılaştırmak için eşitlik işlecini kullanan ifadeler oluşturabilirsiniz. Ancak, bu bağlantı için farklı bağlantıların null seçeneklerini ayarlamamasını önleyebilirsiniz. Bir bağlantı için ANSI_NULLS ayarlarından bağımsız olarak, null değerler test etmek için using NULL değeri her zaman işe yarar.  
  
 ANSI_NULLS OFF ayarı, içinde `DataSet` null değerleri işlemek için her zaman ANSI SQL-92 standardını izleyen bir içinde desteklenmez <xref:System.Data.SqlTypes> .  
  
## <a name="assigning-null-values"></a>Null değerler atama  

 Null değerler özeldir ve depolama ve atama semantiği farklı tür sistemleri ve depolama sistemleri arasında farklılık gösterir. `Dataset`, Farklı tür ve depolama sistemleriyle kullanılmak üzere tasarlanmıştır.  
  
 Bu bölüm <xref:System.Data.DataColumn> <xref:System.Data.DataRow> , farklı tür sistemlerinde bir içindeki öğesine null değerler atamaya yönelik null semantiğini açıklamaktadır.  
  
 `DBNull.Value`  
 Bu atama herhangi bir tür için geçerlidir `DataColumn` . Tür uygularsa `INullable` , `DBNull.Value` uygun kesin türü belirtilmiş null değere zorlanır.  
  
 `SqlType.Null`  
 Tüm <xref:System.Data.SqlTypes> veri türleri uygular `INullable` . Türü kesin belirlenmiş null değer, örtük atama işleçleri kullanılarak sütunun veri türüne dönüştürülebiliyorsanız, atama devam etmelidir. Aksi takdirde geçersiz bir tür dönüştürme özel durumu oluşturulur.  
  
 `null`  
 ' Null ' verili veri türü için geçerli bir değer ise `DataColumn` , ilgili `DbNull.Value` veya `Null` `INullable` türü () ile ilişkili olan veya ilişkilendirilen `SqlType.Null`  
  
 `derivedUdt.Null`  
 UDT sütunlarında, null değerler her zaman ile ilişkili türüne göre saklanır `DataColumn` . `DataColumn`Alt sınıfı yaparken uygulamayana BIR udt ile ilişkili BIR udt durumunu göz önünde bulundurun `INullable` . Bu durumda, türetilmiş sınıfla ilişkili kesin olarak belirlenmiş null değeri atanırsa, `DbNull.Value` null depolama her zaman DataColumn 'ın veri türüyle tutarlı olduğundan türsüz olarak depolanır.  
  
> [!NOTE]
> `Nullable<T>`Veya <xref:System.Nullable> yapısı ' de şu anda desteklenmemektedir `DataSet` .  
  
### <a name="multiple-column-row-assignment"></a>Birden çok sütun (satır) ataması  

 `DataTable.Add`, `DataTable.LoadDataRow` veya bir satıra eşlenmiş bir satırı kabul eden diğer API 'ler <xref:System.Data.DataRow.ItemArray%2A> , ' null ' değerini DataColumn 'ın varsayılan değerine eşleyin. Dizideki bir nesne `DbNull.Value` veya türü kesin belirlenmiş karşılığı içeriyorsa, yukarıda açıklanan kurallar uygulanır.  
  
 Ayrıca, aşağıdaki kurallar null atamalarının bir örneği için geçerlidir `DataRow.["columnName"]` :  
  
1. Varsayılan *varsayılan* değer, kesin tür belirtilmiş null sütunları hariç, kesin olarak belirlenmiş null `DbNull.Value` değer olan null sütunlarıdır.  
  
2. XML dosyalarına serileştirme sırasında null değerler hiçbir şekilde yazılmaz ("xsi: Nil" içinde olduğu gibi).  
  
3. Varsayılanlar dahil tüm null olmayan değerler, XML 'e serileştirilirken her zaman yazılır. Bu, null bir değer (xsi: Nil) açık ve varsayılan değer örtük (XML 'de yoksa, bir doğrulama ayrıştırıcısı onu ilişkili bir XSD şemasından alabilir) olduğu XSD/XML semantiğinin aksine. Bunun için ters değer true 'dur `DataTable` : null değeri örtük ve varsayılan değer açıktır.  
  
4. XML girişinden okunan satırlar için eksik olan tüm sütun değerlerine NULL atanır. <xref:System.Data.DataTable.NewRow%2A>Veya benzer yöntemler kullanılarak oluşturulan satırlara, DataColumn 'ın varsayılan değeri atanır.  
  
5. <xref:System.Data.DataRow.IsNull%2A>Yöntemi hem hem `true` de için `DbNull.Value` döndürür `INullable.Null` .  
  
## <a name="assigning-null-values"></a>Null değerler atama  

 Herhangi bir örnek için varsayılan değer <xref:System.Data.SqlTypes> null.  
  
 İçindeki null değerlere <xref:System.Data.SqlTypes> tür özgüdür ve gibi tek bir değerle temsil edilemez `DbNull` . Null değerleri `IsNull` denetlemek için özelliğini kullanın.  
  
 <xref:System.Data.DataColumn>Aşağıdaki kod örneğinde gösterildiği gibi, null değerler öğesine atanabilir. `SqlTypes`Özel durum tetiklemeden, değişkenlere doğrudan null değerler atayabilirsiniz.  
  
### <a name="example"></a>Örnek  

 Aşağıdaki kod örneği, <xref:System.Data.DataTable> ve şeklinde tanımlanmış iki sütunlu bir ile <xref:System.Data.SqlTypes.SqlInt32> oluşturur <xref:System.Data.SqlTypes.SqlString> . Kod, bir dizi null değeri olan bilinen değerlerin bir satırını ekler ve sonra, <xref:System.Data.DataTable> değerlerini değişkenlere atayarak ve çıktıyı konsol penceresinde görüntüleyerek ' de dolaşır.  
  
 [!code-csharp[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/VB/source.vb#1)]  
  
 Bu örnek aşağıdaki sonuçları görüntüler:  
  
```output
isColumnNull=False, ID=123, Description=Side Mirror  
isColumnNull=True, ID=Null, Description=Null  
```  
  
## <a name="comparing-null-values-with-sqltypes-and-clr-types"></a>Null değerleri SqlTypes ve CLR türleriyle karşılaştırma  

 Null değerleri karşılaştırırken, `Equals` YÖNTEMIN clr türleriyle çalışma yöntemiyle karşılaştırıldığında ' de null değerleri değerlendirme şekli arasındaki farkı anlamak önemlidir <xref:System.Data.SqlTypes> . Tüm <xref:System.Data.SqlTypes> `Equals` Yöntemler null değerlerini değerlendirmek için veritabanı semantiğini kullanır: değerlerden biri veya her ikisi null ise, karşılaştırma null değerini verir. Öte yandan, `Equals` her ikisi de null ise, clr yönteminin ikisi üzerinde kullanılması <xref:System.Data.SqlTypes> true olur. Bu, CLR yöntemi gibi bir örnek yöntemi kullanma `String.Equals` ve statik/paylaşılan yöntemi kullanma arasındaki farkı yansıtır `SqlString.Equals` .  
  
 Aşağıdaki örnek, `SqlString.Equals` `String.Equals` her biri null değer çifti ve daha sonra boş dizeler çifti geçirildiğinde yöntemi ve yöntemi arasındaki sonuçların farkını gösterir.  
  
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
