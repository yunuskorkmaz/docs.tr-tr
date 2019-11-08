---
title: Null Değerleri İşleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f18b288f-b265-4bbe-957f-c6833c0645ef
ms.openlocfilehash: 091fde9a6149f72577e0cf38c8ebf1536abdf6ea
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738207"
---
# <a name="handling-null-values"></a>Null Değerleri İşleme
Bir sütundaki değer bilinmiyorsa veya eksik olduğunda, ilişkisel veritabanında null değer kullanılır. Null, boş bir dize (karakter veya tarih saat veri türleri için) veya sıfır değeri (sayısal veri türleri için) değil. ANSI SQL-92 belirtimi, tüm null değerleri tutarlı bir şekilde işlenebilmesi için null değeri tüm veri türleri için aynı olması gerektiğini belirtir. <xref:System.Data.SqlTypes> ad alanı <xref:System.Data.SqlTypes.INullable> arabirimini uygulayarak null semantikler sağlar. <xref:System.Data.SqlTypes> içindeki her bir veri türü kendi `IsNull` özelliğine sahiptir ve bu veri türünün bir örneğine atanabilecek bir `Null` değeri vardır.  
  
> [!NOTE]
> .NET Framework sürüm 2,0,, programcıların bir değer türünü temel alınan türün tüm değerlerini temsil edecek şekilde genişletmesine izin veren null yapılabilir türler için destek sunmuştur. Bu CLR null yapılabilir türleri <xref:System.Nullable> yapısının bir örneğini temsil eder. Bu özellik, özellikle değer türleri kutulanmış ve kutulandığında, nesne türleriyle gelişmiş uyumluluk sağlayan yararlı olur. ANSI SQL null, `null` başvurusuyla (veya Visual Basic `Nothing`) aynı şekilde davranmadığından, CLR null yapılabilir türler, veritabanı boşları depolaması için tasarlanmamıştır. Veritabanı ANSI SQL null değerleriyle çalışma için, <xref:System.Nullable>yerine <xref:System.Data.SqlTypes> null değerleri kullanın. Visual Basic içinde CLR null yapılabilir türleriyle çalışma hakkında daha fazla bilgi için bkz. [Nullable değer türlerini](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)gör C# ve için bkz. [Nullable değer türlerini](../../../../csharp/language-reference/builtin-types/nullable-value-types.md)görüntüleyin.  
  
## <a name="nulls-and-three-valued-logic"></a>Null değerler ve üç değerli mantık  
 Sütun tanımlarında null değerlere izin verilmesi, uygulamanıza üç değerli mantık getirir. Karşılaştırma, üç koşuldan birini değerlendirebilir:  
  
- Doğru  
  
- False  
  
- Bilinmiyor  
  
 Null değeri bilinmiyor olarak değerlendirildiğinden, birbirleriyle karşılaştırılan iki null değer eşit kabul edilmez. Aritmetik işleçleri kullanan ifadelerde, İşlenenlerden herhangi biri null ise sonuç de null olur.  
  
## <a name="nulls-and-sqlboolean"></a>Null değerler ve SqlBoolean  
 Herhangi bir <xref:System.Data.SqlTypes> karşılaştırma <xref:System.Data.SqlTypes.SqlBoolean>döndürür. Her `SqlType` için `IsNull` işlevi bir <xref:System.Data.SqlTypes.SqlBoolean> döndürür ve null değerleri denetlemek için kullanılabilir. Aşağıdaki Truth tablolarında, ve, veya DEĞIL işleçlerinin bir null değer varlığı içinde nasıl çalıştığı gösterilmektedir. (T = true, F = false, ve U = Unknown veya null.)  
  
 ![Truth tablosu](./media/truthtable-bpuedev11.gif "TruthTable_bpuedev11")  
  
### <a name="understanding-the-ansi_nulls-option"></a>ANSI_NULLS seçeneğini anlama  
 <xref:System.Data.SqlTypes>, ANSI_NULLS seçeneğinin SQL Server ' de ayarlandığı zaman aynı semantiğini sağlar. Tüm aritmetik işleçler (+,-, \*,/,%), bit düzeyinde işleçler (~, &, \|) ve çoğu işlev, özellik `IsNull`hariç, işlenen veya bağımsız değişkenlerden biri null ise null döndürür.  
  
 ANSI SQL-92 standardı, WHERE yan tümcesinde *ColumnName* = null değerini desteklemez. SQL Server, ANSI_NULLS seçeneği veritabanında hem varsayılan null değer alabilme durumunu hem de null değerlere karşı karşılaştırmalar değerlendirmesini denetler. ANSI_NULLS açıksa (varsayılan), null değerleri için test edilirken deyimlerde NULL işleci kullanılmalıdır. Örneğin, ANSI_NULLS açık olduğunda aşağıdaki karşılaştırma her zaman bilinmiyor değerini verir:  
  
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
  
 SQL Server ANSI_NULLS OFF olarak ayarlarsanız, null ile karşılaştırmak için eşitlik işlecini kullanan ifadeler oluşturabilirsiniz. Ancak, bu bağlantı için farklı bağlantıların null seçeneklerini ayarlamamasını önleyebilirsiniz. Bir bağlantı için ANSI_NULLS ayarlarından bağımsız olarak, null değerler test etmek için using NULL değeri her zaman işe yarar.  
  
 ANSI_NULLS OFF ayarı `DataSet`desteklenmez ve bu, <xref:System.Data.SqlTypes>null değerleri işlemek için her zaman ANSI SQL-92 standardını izler.  
  
## <a name="assigning-null-values"></a>Null değerler atama  
 Null değerler özeldir ve depolama ve atama semantiği farklı tür sistemleri ve depolama sistemleri arasında farklılık gösterir. `Dataset`, farklı tür ve depolama sistemleriyle kullanılmak üzere tasarlanmıştır.  
  
 Bu bölümde, farklı tür sistemleri genelinde bir <xref:System.Data.DataRow> <xref:System.Data.DataColumn> null değerler atamaya yönelik null semantik açıklar açıklanmaktadır.  
  
 `DBNull.Value`  
 Bu atama, herhangi bir türdeki `DataColumn` için geçerlidir. Tür `INullable`uygularsa, `DBNull.Value` uygun türü kesin belirlenmiş null değere zorlanır.  
  
 `SqlType.Null`  
 Tüm <xref:System.Data.SqlTypes> veri türleri `INullable`uygular. Türü kesin belirlenmiş null değer, örtük atama işleçleri kullanılarak sütunun veri türüne dönüştürülebiliyorsanız, atama devam etmelidir. Aksi takdirde geçersiz bir tür dönüştürme özel durumu oluşturulur.  
  
 `null`  
 ' Null ', verili `DataColumn` veri türü için geçerli bir değer ise, `INullable` türüyle ilişkili uygun `DbNull.Value` veya `Null` zorlanır (`SqlType.Null`)  
  
 `derivedUdt.Null`  
 UDT sütunlarında, null değerler her zaman `DataColumn`ilişkili türe göre saklanır. Alt sınıfı yaparken `INullable` uygulamayan bir `DataColumn` ilişkili bir UDT durumunu göz önünde bulundurun. Bu durumda, türetilmiş sınıfla ilişkili kesin türü belirtilmiş null değeri atanırsa, null depolama her zaman DataColumn 'ın veri türüyle tutarlı olduğundan türsüz bir `DbNull.Value`olarak depolanır.  
  
> [!NOTE]
> `Nullable<T>` veya <xref:System.Nullable> yapısı `DataSet`Şu anda desteklenmiyor.  
  
### <a name="multiple-column-row-assignment"></a>Birden çok sütun (satır) ataması  
 `DataTable.Add`, `DataTable.LoadDataRow`veya bir satıra eşlenen <xref:System.Data.DataRow.ItemArray%2A> kabul eden diğer API 'Ler, ' null ' değerini DataColumn 'ın varsayılan değerine eşleyin. Dizideki bir nesne `DbNull.Value` veya türü kesin belirlenmiş karşılığı içeriyorsa, yukarıda açıklanan kurallar uygulanır.  
  
 Ayrıca, aşağıdaki kurallar `DataRow.["columnName"]` null atamalarının bir örneği için geçerlidir:  
  
1. Varsayılan *varsayılan* değer, kesin tür belirtilmiş null sütunları hariç tüm için `DbNull.Value`, kesin olarak belirlenmiş null değer olan null sütunlarıdır.  
  
2. XML dosyalarına serileştirme sırasında null değerler hiçbir şekilde yazılmaz ("xsi: Nil" içinde olduğu gibi).  
  
3. Varsayılanlar dahil tüm null olmayan değerler, XML 'e serileştirilirken her zaman yazılır. Bu, null bir değer (xsi: Nil) açık ve varsayılan değer örtük (XML 'de yoksa, bir doğrulama ayrıştırıcısı onu ilişkili bir XSD şemasından alabilir) olduğu XSD/XML semantiğinin aksine. `DataTable`için ters değer doğrudur: null değeri örtük ve varsayılan değer açık olur.  
  
4. XML girişinden okunan satırlar için eksik olan tüm sütun değerlerine NULL atanır. <xref:System.Data.DataTable.NewRow%2A> veya benzer yöntemler kullanılarak oluşturulan satırlara, DataColumn 'ın varsayılan değeri atanır.  
  
5. <xref:System.Data.DataRow.IsNull%2A> yöntemi hem `DbNull.Value` hem de `INullable.Null`için `true` döndürür.  
  
## <a name="assigning-null-values"></a>Null değerler atama  
 Herhangi bir <xref:System.Data.SqlTypes> örneği için varsayılan değer null.  
  
 <xref:System.Data.SqlTypes> 'de null değerlere tür özeldir ve `DbNull`gibi tek bir değerle temsil edilemez. Null değerleri denetlemek için `IsNull` özelliğini kullanın.  
  
 Aşağıdaki kod örneğinde gösterildiği gibi, null değerler bir <xref:System.Data.DataColumn> atanabilir. Özel durum tetiklemeden, `SqlTypes` değişkenlerine doğrudan null değerler atayabilirsiniz.  
  
### <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, <xref:System.Data.SqlTypes.SqlInt32> ve <xref:System.Data.SqlTypes.SqlString>olarak tanımlanmış iki sütunlu bir <xref:System.Data.DataTable> oluşturur. Kod, bir dizi null değeri olan bilinen değerlerin bir satırını ekler ve sonra <xref:System.Data.DataTable>, değerlerini değişkenlere atayarak ve çıktıyı konsol penceresinde görüntüleyerek, bu değerleri yineler.  
  
 [!code-csharp[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/VB/source.vb#1)]  
  
 Bu örnek aşağıdaki sonuçları görüntüler:  
  
```output
isColumnNull=False, ID=123, Description=Side Mirror  
isColumnNull=True, ID=Null, Description=Null  
```  
  
## <a name="comparing-null-values-with-sqltypes-and-clr-types"></a>Null değerleri SqlTypes ve CLR türleriyle karşılaştırma  
 Null değerleri karşılaştırırken, `Equals` yönteminin, CLR türleriyle çalışma yöntemiyle karşılaştırıldığında <xref:System.Data.SqlTypes> null değerlerini değerlendirme şekli arasındaki farkı anlamak önemlidir. Tüm <xref:System.Data.SqlTypes>`Equals` yöntemleri, null değerlerini değerlendirmek için veritabanı semantiğini kullanır: herhangi biri veya her ikisi birden null ise, karşılaştırma null değerini verir. Diğer taraftan, her ikisi de null ise, CLR `Equals` yönteminin iki <xref:System.Data.SqlTypes> üzerinde kullanılması true olur. Bu, CLR `String.Equals` yöntemi gibi bir örnek yöntemi kullanma ve statik/paylaşılan Yöntem `SqlString.Equals`kullanma arasındaki farkı yansıtır.  
  
 Aşağıdaki örnek, her biri null değer çifti ve daha sonra boş dizeler çifti geçirildiğinde `SqlString.Equals` yöntemi ve `String.Equals` yöntemi arasındaki sonuçların farkını gösterir.  
  
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
