---
title: "Boş değerler işleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: f18b288f-b265-4bbe-957f-c6833c0645ef
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 8467d1748cec216c01756049d889ea29f02c3c7c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="handling-null-values"></a>Boş değerler işleme
Bir sütundaki değeri bilinmeyen ya da eksik olduğunda ilişkisel bir veritabanındaki bir null değer kullanılır. Bir null, boş bir dize (karakter veya tarih/saat veri türleri) ne (sayısal veri türleri için) sıfır değeri olur. Böylece tüm null değerlere tutarlı bir şekilde işlenir ANSI SQL-92 belirtimi null tüm veri türleri için aynı olması gerektiğini belirtir. <xref:System.Data.SqlTypes> Ad alanı uygulayarak null semantiği sağlar <xref:System.Data.SqlTypes.INullable> arabirimi. Her veri türlerini <xref:System.Data.SqlTypes> kendi `IsNull` özelliği ve `Null` bu veri türünün bir örneğine atanan değer.  
  
> [!NOTE]
>  Temel alınan türü tüm değerleri temsil etmek için bir değer türü genişletmek programcıları izin boş değer atanabilir türler için .NET Framework 2.0 sürümünde sunulan desteği. Bu CLR boş değer atanabilir türler örneği temsil eden <xref:System.Nullable> yapısı. Nesne türleri ile uyumluluk türleri Kutulu ve, yürütmeyi sarmalanmamış değeri Gelişmiş olduğunda bu beceri özellikle yararlı olur. CLR boş değer atanabilir türler belirtmezseniz veritabanı null değerlere depolama için bir ANSI SQL null aynı şekilde davranır değil çünkü bir `null` başvurusu (veya `Nothing` Visual Basic'te). Veritabanı ANSI SQL null değerler ile çalışmak için kullanmak <xref:System.Data.SqlTypes> null değerlere yerine <xref:System.Nullable>. CLR ile çalışma hakkında daha fazla bilgi için bkz: Visual Basic'te boş değer atanabilir türleri [boş değer atanabilir değer türlerinin](~/docs/visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)ve C# bakın [kullanarak boş değer atanabilir türler](~/docs/csharp/programming-guide/nullable-types/using-nullable-types.md).  
  
## <a name="nulls-and-three-valued-logic"></a>Null değerler ve üç değerli mantığı  
 Sütun tanımlarında null değerlere izin veren üç değerli mantığı uygulamanıza tanıtır. Bir karşılaştırma üç koşullardan biri değerlendirilebilir:  
  
-   Doğru  
  
-   False  
  
-   Bilinmiyor  
  
 Null bilinmeyen olarak kabul edilir çünkü birbirlerine Karşılaştırılan iki null değerleri eşit dikkate alınmaz. İşlenen hiçbirinde null ise aritmetik işleçler kullanarak da ifadeler de null sonucudur.  
  
## <a name="nulls-and-sqlboolean"></a>Null değerler ve SqlBoolean  
 Herhangi bir karşılaştırması <xref:System.Data.SqlTypes> döndürülecek bir <xref:System.Data.SqlTypes.SqlBoolean>. `IsNull` İşlevi her `SqlType` döndüren bir <xref:System.Data.SqlTypes.SqlBoolean> ve null değerler için denetlemek için kullanılabilir. Aşağıdaki gerçekte Göster nasıl tabloları ve OR ve NOT işleçleri işlevi null değeri varlığında. (T = true, F = false ve U = bilinmeyen ya da null.)  
  
 ![Doğru tablosu](../../../../../docs/framework/data/adonet/sql/media/truthtable-bpuedev11.gif "TruthTable_bpuedev11")  
  
### <a name="understanding-the-ansinulls-option"></a>ANSI_NULLS seçeneği anlama  
 <xref:System.Data.SqlTypes>ANSI_NULLS seçeneği açık SQL Server'da ayarlandığında olarak aynı semantiği sağlar. Tüm aritmetik işleçler (+, -, *, /, %), bit düzeyinde işleçler (~ &, &#124;), ve çoğu işlevler işlenen veya bağımsız değişkenler hariç özelliği null ise null döndürür `IsNull`.  
  
 ANSI SQL-92 standart desteklemediği *columnName* WHERE yan tümcesinde = NULL. SQL Server'da ANSI_NULLS seçeneği hem varsayılan NULL atanabilirlik veritabanı ve değerlendirme karşılaştırma null değerler karşı denetler. ANSI_NULLS (varsayılan) etkinleştirdiyseniz, IS NULL işleci için null değerler sınarken ifadelerinde kullanılmalıdır. Örneğin, ANSI_NULLS açık olduğunda aşağıdaki karşılaştırmaya her zaman bilinmeyen verir:  
  
```  
colname > NULL  
```  
  
 Bir null değeri de içeren bir değişken karşılaştırma bilinmeyen verir:  
  
```  
colname > @MyVariable  
```  
  
 IS NULL veya IS NOT NULL karşılaştırma için bir null değer sınamak için kullanın. WHERE yan tümcesine bu karmaşıklık ekleyebilirsiniz. Örneğin, AdventureWorks Müşteri tablosundaki TerritoryID sütunu null değerlere izin verir. Bir SELECT deyimi, diğerlerinin yanı sıra null değerler için test etmek için ise, boş bir koşulu şunları içermelidir:  
  
```  
SELECT CustomerID, AccountNumber, TerritoryID  
FROM AdventureWorks.Sales.Customer  
WHERE TerritoryID IN (1, 2, 3)  
   OR TerritoryID IS NULL  
```  
  
 ANSI_NULLS SQL Server ayarlarsanız, null karşılaştırma için eşitlik işleci kullanan ifadeler oluşturabilirsiniz. Ancak, bu bağlantı için null seçeneklerini ayarlama farklı bağlantıların engelleyemez. Null değerler için her zaman bağlantı ANSI_NULLS ayarlarına bakılmaksızın works sınamak için IS NULL kullanma.  
  
 Ayarını devre dışı ANSI_NULLS desteklenmez bir `DataSet`, hangi her zaman uyar null değerleri işlemek için ANSI SQL-92 standart <xref:System.Data.SqlTypes>.  
  
## <a name="assigning-null-values"></a>Null değerler atama  
 Null değerler özel ve kendi depolama ve atama semantiği farklı türde sistemleri ve depolama sistemlerini arasında farklılık gösterir. A `Dataset` farklı türü ve depolama sistemlerini ile kullanılmak üzere tasarlanmıştır.  
  
 Bu bölüm için null değerler atama için null semantiğini açıklar bir <xref:System.Data.DataColumn> içinde bir <xref:System.Data.DataRow> farklı sistemler arasında.  
  
 `DBNull.Value`  
 Bu atama için geçerli bir `DataColumn` herhangi bir türde. Türü uyguluyorsa `INullable`, `DBNull.Value` uygun kesin türü belirtilmiş Null değeri yüklenen.  
  
 `SqlType.Null`  
 Tüm <xref:System.Data.SqlTypes> veri türleri uygulayan `INullable`. Sütunun veri türüne örtük atama işleçleri kullanarak kesin türü belirtilmiş null değeri dönüştürülebilir ise atama geçtikleri. Aksi takdirde geçersiz yayın özel durum oluşur.  
  
 `null`  
 'Null' geçerli bir değer ise verilen `DataColumn` veri türü, bunu uygun yüklenen `DbNull.Value` veya `Null` ile ilişkili `INullable` türü (`SqlType.Null`)  
  
 `derivedUdt.Null`  
 UDT sütunlar için null değerler her zaman ilişkili türüne göre depolanan `DataColumn`. İle ilişkili bir UDT durumunu göz önünde bulundurun bir `DataColumn` , uygulamıyor `INullable` kendi alt sınıfı değil ancak. Bu durumda, türetilmiş sınıf ile ilişkili kesin türü belirtilmiş bir null değer atanmazsa depolandığı bir türsüz olarak `DbNull.Value`, null depolama her zaman DataColumn nesnesinin veri türüyle tutarlı olduğundan.  
  
> [!NOTE]
>  `Nullable<T>` Veya <xref:System.Nullable> yapısı şu anda desteklenmez `DataSet`.  
  
### <a name="multiple-column-row-assignment"></a>Birden çok sütun (satır) atama  
 `DataTable.Add`, `DataTable.LoadDataRow`, ya da kabul diğer API'leri bir <xref:System.Data.DataRow.ItemArray%2A> satır eşlenen, 'DataColumn nesnesinin varsayılan değer olarak null' harita. Bir dizi nesnesi içeriyorsa `DbNull.Value` veya kesin türü belirtilmiş karşılığı, yukarıdaki aynı kuralları açıklandığı uygulanır.  
  
 Ayrıca, bir örneği için aşağıdaki kurallar geçerli `DataRow.["columnName"]` null atamaları:  
  
1.  Varsayılan *varsayılan* değer `DbNull.Value` tümü olduğu uygun kesinlikle kesin türü belirtilmiş null sütunlar null değer belirtilmiş dışında.  
  
2.  Null değerler hiçbir zaman XML dosyaları (olduğu gibi "xsi: nil") için serileştirme sırasında yazılır.  
  
3.  Varsayılan değerleri dahil olmak üzere tüm null olmayan değerler her zaman XML serileştirirken yazılır. Burada bir null değer (xsi: nil) açık ve varsayılan değer örtük XSD/XML semantiği budur (XML içinde mevcut değil, doğrulama ayrıştırıcı, ilişkili bir XSD şemadan alabilirsiniz varsa). Tersidir için doğru bir `DataTable`: bir null değer örtük ve açık varsayılan değerdir.  
  
4.  XML girdiden okunan satırlar için tüm eksik sütun değerleri NULL atanır. Kullanılarak oluşturulan satırları <xref:System.Data.DataTable.NewRow%2A> veya benzer yöntemler DataColumn nesnesinin varsayılan değeri atanır.  
  
5.  <xref:System.Data.DataRow.IsNull%2A> Yöntemi döndürür `true` her ikisi için de `DbNull.Value` ve `INullable.Null`.  
  
## <a name="assigning-null-values"></a>Null değerler atama  
 Varsayılan değer herhangi <xref:System.Data.SqlTypes> örneği null.  
  
 İçinde null değerlere <xref:System.Data.SqlTypes> türüne özgü ve tek bir değer tarafından gibi gösterilemez `DbNull`. Kullanım `IsNull` özelliği için null değerler denetleyin.  
  
 Null değerler atanabilen bir <xref:System.Data.DataColumn> aşağıdaki kod örneğinde gösterildiği gibi. Null değerler için doğrudan atayabilir `SqlTypes` bir özel durum harekete olmadan değişkenleri.  
  
### <a name="example"></a>Örnek  
 Aşağıdaki kod örneği oluşturur bir <xref:System.Data.DataTable> olarak tanımlanan iki sütunlarla <xref:System.Data.SqlTypes.SqlInt32> ve <xref:System.Data.SqlTypes.SqlString>. Kod bilinen değerlerin bir satır ekler, bir satır null değerler ve ardından dolaşır <xref:System.Data.DataTable>değişkenlere değerler atama ve çıkış konsol penceresinde görüntüler.  
  
 [!code-csharp[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/VB/source.vb#1)]  
  
 Bu örnekte aşağıdaki sonuçları görüntüler:  
  
```  
isColumnNull=False, ID=123, Description=Side Mirror  
isColumnNull=True, ID=Null, Description=Null  
```  
  
## <a name="comparing-null-values-with-sqltypes-and-clr-types"></a>Null değerler SqlTypes ve CLR Türleri ile karşılaştırma  
 Null değerler karşılaştırılırken biçimini arasındaki farkı anlamak önemlidir `Equals` yöntemi null değerlerini değerlendirir <xref:System.Data.SqlTypes> CLR türleriyle çalışma şeklini karşılaştırıldığında. Tüm <xref:System.Data.SqlTypes> `Equals` yöntemleri null değerler değerlendirmesi için veritabanı semantiği kullanın: birini veya ikisini değerleri ise null, null karşılaştırma verir. Diğer taraftan, CLR kullanarak `Equals` iki yöntemi <xref:System.Data.SqlTypes> her ikisi de null olduğunda true sunacak. Bu CLR gibi örnek yöntemi kullanarak arasındaki farkı yansıtır `String.Equals` yöntemi ve statik ve paylaşılan yöntemini kullanarak `SqlString.Equals`.  
  
 Aşağıdaki örnek, sonuçları farkı gösterir `SqlString.Equals` yöntemi ve `String.Equals` her bir değer çifti null ve boş dizeler çifti geçirildiğinde yöntemi.  
  
 [!code-csharp[DataWorks SqlTypes.CompareNulls#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.CompareNulls/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.CompareNulls#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.CompareNulls/VB/source.vb#1)]  
  
 Kod şu çıkışı üretir:  
  
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
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
