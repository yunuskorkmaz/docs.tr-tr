---
title: Null değerleri işleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f18b288f-b265-4bbe-957f-c6833c0645ef
ms.openlocfilehash: 039a6f5aab2f1b857f98803f8b3d6425cc549877
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43486047"
---
# <a name="handling-null-values"></a>Null değerleri işleme
Bir sütundaki değer bilinmeyen veya eksik olduğunda, ilişkisel bir veritabanındaki bir null değer kullanılır. Bir null, boş bir dize (karakter veya tarih/saat veri türleri için) ya da sıfır değeri (sayısal veri türleri için) olur. Tüm null değerlere tutarlı bir şekilde işlenir böylece ANSI SQL 92 belirtimi boş tüm veri türleri için aynı olması gerektiğini belirtir. <xref:System.Data.SqlTypes> Uygulayarak ad alanı null bir semantik sağlar <xref:System.Data.SqlTypes.INullable> arabirimi. Her veri türlerini <xref:System.Data.SqlTypes> kendi `IsNull` özelliği ve `Null` veri türü örneğine atanabilir değer.  
  
> [!NOTE]
>  Temel türün tüm değerlerini temsil etmek için bir değer türü genişletmek programcılar izin boş değer atanabilir türler için .NET Framework 2.0 sürümünde sunulan desteği. Bu CLR boş değer atanabilir türleri temsil eden bir örneğini <xref:System.Nullable> yapısı. Bu özellik türleri Kutulu ve sağlanması, kutudan değeri Gelişmiş nesne türleri ile uyumluluk özellikle yararlı olur. CLR boş değer atanabilir türler ANSI SQL null aynı şekilde davranmaz çünkü veritabanı null değerlere depolanmasında amaçlanmayan bir `null` başvurusu (veya `Nothing` Visual Basic'te). Veritabanı ANSI SQL null değerleri ile çalışmak için kullanmak <xref:System.Data.SqlTypes> null değerler yerine <xref:System.Nullable>. CLR ile çalışma hakkında daha fazla bilgi için bkz: Visual Basic'te boş değer atanabilir türler [boş değer atanabilir değer türleri](~/docs/visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)ve C# bakın [kullanarak boş değer atanabilir türler](~/docs/csharp/programming-guide/nullable-types/using-nullable-types.md).  
  
## <a name="nulls-and-three-valued-logic"></a>Null değerler ve üç değerli mantığı  
 Null değerlere izin verecek sütun tanımlarında üç değerli mantıksal uygulamanıza tanıtır. Bir karşılaştırma üç koşullardan birini değerlendirebilirsiniz:  
  
-   Doğru  
  
-   False  
  
-   Bilinmiyor  
  
 Null bilinmeyen olarak kabul edilir çünkü birbirine Karşılaştırılan iki null değeri eşit olacak şekilde dikkate alınmaz. Aritmetik işleçler işlenenlerin null ise kullanarak da ifadeleri sonucu de null olur.  
  
## <a name="nulls-and-sqlboolean"></a>Null değerler ve SqlBoolean  
 Herhangi bir karşılaştırmasını <xref:System.Data.SqlTypes> döndüreceği bir <xref:System.Data.SqlTypes.SqlBoolean>. `IsNull` İşlevi her `SqlType` döndürür bir <xref:System.Data.SqlTypes.SqlBoolean> ve denetlemek için null değerler için kullanılabilir. Aşağıdaki basit programı nasıl tabloları ve, veya ve değil işleçleri işlevi bir null değer saklanacaktır. (T = true, F = false ve U = bilinmeyen ya da null.)  
  
 ![Doğru tablosu](../../../../../docs/framework/data/adonet/sql/media/truthtable-bpuedev11.gif "TruthTable_bpuedev11")  
  
### <a name="understanding-the-ansinulls-option"></a>ANSI_NULLS seçeneği anlama  
 <xref:System.Data.SqlTypes> ANSI_NULLS seçeneği SQL Server üzerinde ayarlandığında, aynı semantiklere sağlar. Tüm aritmetik işleçler (+, -, *, /, %), bit düzeyinde işleçler (~ &, &#124;), ve çoğu işlev işlenen ya da bağımsız değişkenler hariç özelliği null ise null dönüş `IsNull`.  
  
 ANSI SQL 92 standart desteklemediği *columnName* WHERE yan tümcesinde = NULL. SQL Server veritabanı ve null değerlere karşı karşılaştırma değerlendirme hem varsayılan öğesinin ANSI_NULLS seçeneği denetler. ANSI_NULLS (varsayılan) etkinleştirdiyseniz, IS NULL işleci ifadelerinde boş değerler için test ederken kullanılması gerekir. Örneğin, aşağıdaki karşılaştırma, her zaman ANSI_NULLS açık olduğunda bilinmeyen verir:  
  
```  
colname > NULL  
```  
  
 Bilinmeyen bir null değeri de içeren bir değişkene karşılaştırma verir:  
  
```  
colname > @MyVariable  
```  
  
 IS NULL ya da IS NOT NULL koşul null değerini test etmek için kullanın. Bu, WHERE yan tümcesine karmaşıklığı ekleyebilirsiniz. Örneğin, AdventureWorks müşteri tablosu TerritoryID sütunda null değerlere izin verir. Bir SELECT deyimi, diğerlerinin yanı sıra null değerler için test etmek için ise, boş bir koşul bulunmalıdır:  
  
```  
SELECT CustomerID, AccountNumber, TerritoryID  
FROM AdventureWorks.Sales.Customer  
WHERE TerritoryID IN (1, 2, 3)  
   OR TerritoryID IS NULL  
```  
  
 SQL Server'da ANSI_NULLS kalanından null olarak karşılaştırmak için eşitlik işlecini kullanan ifadelerde oluşturabilirsiniz. Ancak, bu bağlantı için null seçeneklerini ayarlama farklı bağlantıların önleyemez. Null değerler için her zaman bağlantı ANSI_NULLS ayarlarından bağımsız olarak çalıştığı sınamak için IS NULL kullanma.  
  
 Ayarını devre dışı ANSI_NULLS içinde desteklenmiyor bir `DataSet`, hangi her zaman aşağıdaki null değerleri işleme için ANSI SQL 92 standart <xref:System.Data.SqlTypes>.  
  
## <a name="assigning-null-values"></a>Null değerler atama  
 Null değerler özel ve kendi depolama ve atama semantiği farklı tür sistemleri ve depolama sistemleri arasında farklılık gösterir. A `Dataset` farklı türü ve depolama sistemleri ile kullanılmak üzere tasarlanmıştır.  
  
 Bu bölüm için null değerler atama için null semantikler açıklar bir <xref:System.Data.DataColumn> içinde bir <xref:System.Data.DataRow> farklı sistemler arasında.  
  
 `DBNull.Value`  
 Bu atama için geçerli olan bir `DataColumn` herhangi bir türde. Türü uyguluyorsa `INullable`, `DBNull.Value` uygun türü kesin belirlenmiş Null değeri durumunda bırakılması.  
  
 `SqlType.Null`  
 Tüm <xref:System.Data.SqlTypes> veri türleri uygulayan `INullable`. Sütunun veri türüne örtük dönüştürme işleçlerini kullanarak türü kesin belirlenmiş null değeri dönüştürülebilir ise, atama Git. Aksi takdirde, bir geçersiz dönüştürme özel durum oluşturulur.  
  
 `null`  
 'Null' geçerli bir değer ise belirtilen `DataColumn` veri türü, bunu uygun durumunda bırakılması `DbNull.Value` veya `Null` ilişkili `INullable` türü (`SqlType.Null`)  
  
 `derivedUdt.Null`  
 UDT sütunlar için null değerler her zaman ilişkili türüne göre depolanır `DataColumn`. İle ilişkili bir UDT durumunu göz önünde bulundurun bir `DataColumn` , uygulamıyor `INullable` kahvenizi alt sınıfı. Bu durumda, türetilmiş sınıfla ilişkili kesin türü belirtilmiş bir null değer atanmazsa, depolandığını yazılmamış bir olarak `DbNull.Value`, null depolama her zaman DataColumn nesnesinin veri türü ile tutarlı olduğundan.  
  
> [!NOTE]
>  `Nullable<T>` Veya <xref:System.Nullable> yapısı şu anda desteklenmiyor `DataSet`.  
  
### <a name="multiple-column-row-assignment"></a>Birden çok sütun (satır) atama  
 `DataTable.Add`, `DataTable.LoadDataRow`, ya da kabul diğer API'ler bir <xref:System.Data.DataRow.ItemArray%2A> bir satıra eşlendi, 'DataColumn nesnesinin varsayılan değer olarak null' harita. Bir dizi nesnesi içeriyorsa `DbNull.Value` veya türü kesin belirlenmiş karşılığı, yukarıdaki aynı kurallara açıklandığı uygulanır.  
  
 Ayrıca, bir örneği için aşağıdaki kurallar geçerli `DataRow.["columnName"]` atamaları null:  
  
1.  Varsayılan *varsayılan* değer `DbNull.Value` tümü null değer olduğu uygun kesin türü kesin belirlenmiş null sütunları yazdınız dışında.  
  
2.  Null değerler hiçbir zaman XML dosyaları (olduğu gibi "xsi: nil") için serileştirme sırasında yazılır.  
  
3.  Varsayılan, dahil olmak üzere tüm null olmayan değerler her zaman XML seri hale getirilirken yazılır. Burada bir null değer (xsi: nil) açık ve varsayılan değer örtük XSD/XML semantiği budur (XML içinde mevcut değil, doğrulama ayrıştırıcı, ilişkili bir XSD şema alamayacağınızı). Bunun tersi için de geçerlidir bir `DataTable`: bir null değer örtük ve açık varsayılan değerdir.  
  
4.  XML girdiden okunan satır için tüm eksik sütun değerlerini NULL olarak atanır. Kullanılarak oluşturulan satırları <xref:System.Data.DataTable.NewRow%2A> veya benzer yöntemler DataColumn nesnesinin varsayılan değer atanır.  
  
5.  <xref:System.Data.DataRow.IsNull%2A> Yöntemi döndürür `true` hem `DbNull.Value` ve `INullable.Null`.  
  
## <a name="assigning-null-values"></a>Null değerler atama  
 Herhangi biri için varsayılan değer <xref:System.Data.SqlTypes> örneği null.  
  
 İçinde null değerlere <xref:System.Data.SqlTypes> türe özgü olan ve tek bir değer gibi gösterilemez `DbNull`. Kullanım `IsNull` null değerler için denetlenecek özellik.  
  
 Boş değerler atanabilen bir <xref:System.Data.DataColumn> aşağıdaki kod örneğinde gösterildiği gibi. Null değerler için doğrudan atayabilir `SqlTypes` bir özel durum harekete olmadan değişkenleri.  
  
### <a name="example"></a>Örnek  
 Aşağıdaki kod örneği oluşturur bir <xref:System.Data.DataTable> olarak tanımlı iki sütunlu <xref:System.Data.SqlTypes.SqlInt32> ve <xref:System.Data.SqlTypes.SqlString>. Bilinen değerler bir satır kod ekler, bir satır null değerler ve ardından gezinir <xref:System.Data.DataTable>, değerleri değişkenlere atamak ve çıktıyı konsol penceresinde görüntüler.  
  
 [!code-csharp[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/VB/source.vb#1)]  
  
 Bu örnek, aşağıdaki sonuçları gösterir:  
  
```  
isColumnNull=False, ID=123, Description=Side Mirror  
isColumnNull=True, ID=Null, Description=Null  
```  
  
## <a name="comparing-null-values-with-sqltypes-and-clr-types"></a>SqlTypes ve CLR Türleri ile null değerleri karşılaştırma  
 Null değerler karşılaştırılırken biçimini arasındaki farkı anlamak önemlidir `Equals` yöntemi null değerleri değerlendirir <xref:System.Data.SqlTypes> CLR türleriyle çalışma şeklini değiştirmeyen. Tüm <xref:System.Data.SqlTypes> `Equals` yöntemleri null değerlerini değerlendirmek için veritabanı semantiğini kullanın: ya da değerler, null, null karşılaştırma verir. Öte yandan, CLR kullanarak `Equals` yöntemi iki <xref:System.Data.SqlTypes> her ikisi de null ise true verir. Bu bir örnek yöntemi gibi CLR'ın kullanımı arasındaki fark gösterdiğinden `String.Equals` yöntemi ve statik ve paylaşılan yöntemi kullanarak `SqlString.Equals`.  
  
 Aşağıdaki örnek, sonuç farkı gösterir `SqlString.Equals` yöntemi ve `String.Equals` her bir null değer çiftinin ve bir çift boş dizeler geçirildiğinde yöntemi.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [SQL Server Veri Türleri ve ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
