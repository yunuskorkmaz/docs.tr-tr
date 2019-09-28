---
title: Null Değerleri İşleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f18b288f-b265-4bbe-957f-c6833c0645ef
ms.openlocfilehash: 26b7e3a287c00f103129632ae8b0db882d468ef3
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71352982"
---
# <a name="handling-null-values"></a>Null Değerleri İşleme
Bir sütundaki değer bilinmiyorsa veya eksik olduğunda, ilişkisel veritabanında null değer kullanılır. Null, boş bir dize (karakter veya tarih saat veri türleri için) veya sıfır değeri (sayısal veri türleri için) değil. ANSI SQL-92 belirtimi, tüm null değerleri tutarlı bir şekilde işlenebilmesi için null değeri tüm veri türleri için aynı olması gerektiğini belirtir. @No__t-0 ad alanı <xref:System.Data.SqlTypes.INullable> arabirimini uygulayarak null semantiği sağlar. @No__t-0 ' daki veri türlerinin her biri kendi `IsNull` özelliğine ve bu veri türünün bir örneğine atanabilecek `Null` değerine sahiptir.  
  
> [!NOTE]
> .NET Framework sürüm 2,0,, programcıların bir değer türünü temel alınan türün tüm değerlerini temsil edecek şekilde genişletmesine izin veren null yapılabilir türler için destek sunmuştur. Bu CLR null yapılabilir türleri <xref:System.Nullable> yapısının bir örneğini temsil eder. Bu özellik, özellikle değer türleri kutulanmış ve kutulandığında, nesne türleriyle gelişmiş uyumluluk sağlayan yararlı olur. Bir ANSI SQL null değeri `null` başvurusuyla aynı şekilde davranmadığından (@no__t veya Visual Basic), CLR null yapılabilir türler, veritabanı boşları depolaması için tasarlanmamıştır. Veritabanı ANSI SQL null değerleriyle çalışma için, <xref:System.Nullable> yerine <xref:System.Data.SqlTypes> null değerleri kullanın. Visual Basic CLR null yapılabilir türleriyle çalışma hakkında daha fazla bilgi için bkz. [Nullable değer türlerini](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)kullanma ve C# bkz. [Nullable değer türlerini kullanma](../../../../csharp/programming-guide/nullable-types/using-nullable-types.md).  
  
## <a name="nulls-and-three-valued-logic"></a>Null değerler ve üç değerli mantık  
 Sütun tanımlarında null değerlere izin verilmesi, uygulamanıza üç değerli mantık getirir. Karşılaştırma, üç koşuldan birini değerlendirebilir:  
  
- Doğru  
  
- False  
  
- Bilinmiyor  
  
 Null değeri bilinmiyor olarak değerlendirildiğinden, birbirleriyle karşılaştırılan iki null değer eşit kabul edilmez. Aritmetik işleçleri kullanan ifadelerde, İşlenenlerden herhangi biri null ise sonuç de null olur.  
  
## <a name="nulls-and-sqlboolean"></a>Null değerler ve SqlBoolean  
 @No__t-0 arasında karşılaştırma, bir @no__t döndürür. Her `SqlType` için `IsNull` işlevi, bir <xref:System.Data.SqlTypes.SqlBoolean> döndürür ve null değerleri denetlemek için kullanılabilir. Aşağıdaki Truth tablolarında, ve, veya DEĞIL işleçlerinin bir null değer varlığı içinde nasıl çalıştığı gösterilmektedir. (T = true, F = false, ve U = Unknown veya null.)  
  
 ![Truth tablosu](./media/truthtable-bpuedev11.gif "TruthTable_bpuedev11")  
  
### <a name="understanding-the-ansi_nulls-option"></a>ANSI_NULLS seçeneğini anlama  
 <xref:System.Data.SqlTypes>, ANSI_NULLS seçeneğinin SQL Server ' de ayarlandığı zaman ile aynı semantiğini sağlar. Tüm aritmetik işleçler (+,-, \*,/,%), bit düzeyinde işleçler (~, &, \|) ve çoğu işlev, işlenen veya bağımsız değişkenlerden herhangi biri null ise null döndürür. Bu özellik, `IsNull` ' dir.  
  
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
  
 @No__t-1 ' de null değerleri işlemek için her zaman ANSI SQL-92 standardını izleyen `DataSet` ' da ANSI_NULLS OFF ayarı desteklenmez.  
  
## <a name="assigning-null-values"></a>Null değerler atama  
 Null değerler özeldir ve depolama ve atama semantiği farklı tür sistemleri ve depolama sistemleri arasında farklılık gösterir. @No__t-0, farklı tür ve depolama sistemleriyle kullanılmak üzere tasarlanmıştır.  
  
 Bu bölümde, farklı tür sistemleri arasında bir <xref:System.Data.DataRow> ' de <xref:System.Data.DataColumn> ' a null değerler atamaya yönelik null semantik açıklanmaktadır.  
  
 `DBNull.Value`  
 Bu atama, herhangi bir türdeki `DataColumn` için geçerlidir. Tür @no__t uygularsa, `DBNull.Value` uygun türü kesin belirlenmiş null değere zorlanır.  
  
 `SqlType.Null`  
 Tüm <xref:System.Data.SqlTypes> veri türleri @no__t uygular-1. Türü kesin belirlenmiş null değer, örtük atama işleçleri kullanılarak sütunun veri türüne dönüştürülebiliyorsanız, atama devam etmelidir. Aksi takdirde geçersiz bir tür dönüştürme özel durumu oluşturulur.  
  
 `null`  
 ' Null ', verilen `DataColumn` veri türü için geçerli bir değer ise, `INullable` türüyle ilişkili `DbNull.Value` veya `Null` ' ye (`SqlType.Null`) zorlanır  
  
 `derivedUdt.Null`  
 UDT sütunlarında, null değerler her zaman `DataColumn` ile ilişkili türe göre depolanır. Alt sınıfı yaparken `INullable` uygulamayan `DataColumn` ile ilişkili bir UDT 'nin durumunu göz önünde bulundurun. Bu durumda, türetilmiş sınıfla ilişkili kesin türü belirtilmiş null değeri atanırsa, null depolama her zaman DataColumn 'ın veri türüyle tutarlı olduğundan, türü belirsiz `DbNull.Value` olarak depolanır.  
  
> [!NOTE]
> @No__t-0 veya <xref:System.Nullable> yapısı şu anda `DataSet` ' de desteklenmemektedir.  
  
### <a name="multiple-column-row-assignment"></a>Birden çok sütun (satır) ataması  
 `DataTable.Add`, `DataTable.LoadDataRow` veya bir satıra eşlenen <xref:System.Data.DataRow.ItemArray%2A> kabul eden diğer API 'Ler, ' null ' değerini DataColumn 'ın varsayılan değerine eşleyin. Dizideki bir nesne `DbNull.Value` veya türü kesin belirlenmiş karşılığı içeriyorsa, yukarıda açıklanan kurallar uygulanır.  
  
 Ayrıca, aşağıdaki kurallar `DataRow.["columnName"]` null atamalarının bir örneği için geçerlidir:  
  
1. Varsayılan *varsayılan* değer, kesin türü belirtilmiş null sütunları hariç tüm için `DbNull.Value` ' dir ve uygun türü kesin belirlenmiş null değer olur.  
  
2. XML dosyalarına serileştirme sırasında null değerler hiçbir şekilde yazılmaz ("xsi: Nil" içinde olduğu gibi).  
  
3. Varsayılanlar dahil tüm null olmayan değerler, XML 'e serileştirilirken her zaman yazılır. Bu, null bir değer (xsi: Nil) açık ve varsayılan değer örtük (XML 'de yoksa, bir doğrulama ayrıştırıcısı onu ilişkili bir XSD şemasından alabilir) olduğu XSD/XML semantiğinin aksine. @No__t-0 için ters değer true: null değeri örtük ve varsayılan değer açık olur.  
  
4. XML girişinden okunan satırlar için eksik olan tüm sütun değerlerine NULL atanır. @No__t-0 veya benzer yöntemler kullanılarak oluşturulan satırlara, DataColumn 'ın varsayılan değeri atanır.  
  
5. @No__t-0 yöntemi, hem `DbNull.Value` hem de `INullable.Null` için `true` döndürür.  
  
## <a name="assigning-null-values"></a>Null değerler atama  
 Herhangi bir <xref:System.Data.SqlTypes> örneği için varsayılan değer null.  
  
 @No__t-0 ' daki null değerlere tür özgüdür ve `DbNull` gibi tek bir değerle temsil edilemez. Null değerleri denetlemek için `IsNull` özelliğini kullanın.  
  
 Aşağıdaki kod örneğinde gösterildiği gibi, <xref:System.Data.DataColumn> ' a null değerler atanabilir. Bir özel durum tetiklemeden, `SqlTypes` değişkenlerine doğrudan null değerler atayabilirsiniz.  
  
### <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, <xref:System.Data.SqlTypes.SqlInt32> ve <xref:System.Data.SqlTypes.SqlString> olarak tanımlanmış iki sütunlu <xref:System.Data.DataTable> oluşturur. Kod, bir dizi null değeri olan bilinen değerlerin bir satırını ekler ve sonra <xref:System.Data.DataTable> ' ı yineler, değerleri değişkenlere atayarak ve çıktıyı konsol penceresinde görüntülüyor.  
  
 [!code-csharp[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/VB/source.vb#1)]  
  
 Bu örnek aşağıdaki sonuçları görüntüler:  
  
```  
isColumnNull=False, ID=123, Description=Side Mirror  
isColumnNull=True, ID=Null, Description=Null  
```  
  
## <a name="comparing-null-values-with-sqltypes-and-clr-types"></a>Null değerleri SqlTypes ve CLR türleriyle karşılaştırma  
 Null değerleri karşılaştırırken, `Equals` yönteminin, CLR türleriyle çalışma yöntemiyle karşılaştırıldığında <xref:System.Data.SqlTypes> ' deki null değerleri nasıl değerlendirdiği ile ilgili farkı anlamak önemlidir. @No__t-0 @ no__t-1 yöntemleri, null değerlerini değerlendirmek için veritabanı semantiğini kullanır: herhangi biri veya her ikisi birden null ise, karşılaştırma null değerini verir. Diğer taraftan, her ikisi de null olduğunda, CLR `Equals` yönteminin iki <xref:System.Data.SqlTypes> ile kullanılması true olarak işlenir. Bu, CLR `String.Equals` yöntemi gibi bir örnek yöntemi kullanma ve statik/paylaşılan yöntemi `SqlString.Equals` ile arasındaki farkı yansıtır.  
  
 Aşağıdaki örnek, her biri null değer çifti ve daha sonra boş dizeler çifti geçirildiğinde `SqlString.Equals` yöntemi ile `String.Equals` yöntemi arasındaki sonuçların farkını gösterir.  
  
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
