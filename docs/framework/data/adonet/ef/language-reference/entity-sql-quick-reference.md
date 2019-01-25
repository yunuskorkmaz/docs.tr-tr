---
title: Entity SQL hızlı başvurusu
ms.date: 03/30/2017
ms.assetid: e53dad9e-5e83-426e-abb4-be3e78e3d6dc
ms.openlocfilehash: 20d8d1cb1e4b5cbf37dffcce6a7e79c2a4c265d3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54539409"
---
# <a name="entity-sql-quick-reference"></a>Entity SQL hızlı başvurusu
Bu konu, hızlı başvuru sağlar. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgular. Sorgular, bu konuda, AdventureWorks satış modeline dayanır.  
  
## <a name="literals"></a>Sabit değerler  
  
### <a name="string"></a>Dize  
 Unicode ve Unicode olmayan karakter dize değişmez değerleri vardır. Unicode dizelerini ile n tanımlandıkları Örneğin, `N'hello'`.  
  
 Unicode olmayan dize sabitinin bir örnek verilmiştir:  
  
```  
'hello'  
--same as  
"hello"  
```  
  
 Çıktı:  
  
|Değer|  
|-----------|  
|Merhaba|  
  
### <a name="datetime"></a>DateTime  
 DateTime değişmez değerlerine, tarih ve saat bölümleri zorunludur. Varsayılan değerler yoktur.  
  
 Örnek:  
  
```  
DATETIME '2006-12-25 01:01:00.000'   
--same as  
DATETIME '2006-12-25 01:01'  
```  
  
 Çıktı:  
  
|Değer|  
|-----------|  
|12/25/2006 01:01: 00'DA|  
  
### <a name="integer"></a>Tamsayı  
 Tamsayı sabit değerlerinde Int32 türünü olabilir (123) UInt32 (123U), Int64 (123L) ve UInt64 (123UL).  
  
 Örnek:  
  
```  
--a collection of integers  
{1, 2, 3}  
```  
  
 Çıktı:  
  
|Değer|  
|-----------|  
|1.|  
|2|  
|3|  
  
### <a name="other"></a>Diğer  
 Tarafından desteklenen diğer sabitler [!INCLUDE[esql](../../../../../../includes/esql-md.md)] olan GUID, ikili, kayan nokta/Double, Decimal, ve `null`. Null değişmez değerlerine [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kavramsal modeldeki diğer her tür ile uyumlu olarak değerlendirilir.  
  
## <a name="type-constructors"></a>Türü oluşturucuları  
  
### <a name="row"></a>SATIR  
 [Satır](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md) bir anonim, yapısal olarak yazılmış (kayıt) değeri olarak oluşturur: `ROW(1 AS myNumber, ‘Name’ AS myName).`  
  
 Örnek:  
  
```  
SELECT VALUE row (product.ProductID as ProductID, product.Name   
    as ProductName) FROM AdventureWorksEntities.Product AS product  
```  
  
 Çıktı:  
  
|ProductID|Ad|  
|---------------|----------|  
|1.|Ayarlanabilir yarış|  
|879|Çok amaçlı bisiklet bağımsız|  
|712|AWC logolu Kasket|  
|...|...|  
  
### <a name="multiset"></a>MULTISET  
 [MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md) koleksiyonları gibi oluşturur:  
  
 `MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`  
  
 Örnek:  
  
```  
SELECT VALUE product FROM AdventureWorksEntities.Product AS product WHERE product.ListPrice IN MultiSet (125, 300)  
```  
  
 Çıktı:  
  
|ProductID|Ad|ProductNumber|…|  
|---------------|----------|-------------------|-------|  
|842|Yarış Panniers, büyük|PA T100|…|  
  
### <a name="object"></a>Nesne  
 [Konstruktor Typu adlı](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md) gibi kullanıcı tanımlı nesneler (adlandırılmış), yapıları `person("abc", 12)`.  
  
 Örnek:  
  
```  
SELECT VALUE AdventureWorksModel.SalesOrderDetail (o.SalesOrderDetailID, o.CarrierTrackingNumber, o.OrderQty,   
o.ProductID, o.SpecialOfferID, o.UnitPrice, o.UnitPriceDiscount,   
o.rowguid, o.ModifiedDate) FROM AdventureWorksEntities.SalesOrderDetail   
AS o  
```  
  
 Çıktı:  
  
|SalesOrderDetailID|CarrierTrackingNumber|OrderQty|ProductID|...|  
|------------------------|---------------------------|--------------|---------------|---------|  
|1.|4911-403C-98|1.|776|...|  
|2|4911-403C-98|3|777|...|  
|...|...|...|...|...|  
  
## <a name="references"></a>Referanslar  
  
### <a name="ref"></a>BAŞVURU  
 [REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md) bir varlık türü örneğine başvuru oluşturur. Örneğin, aşağıdaki sorgu, siparişler varlık kümesinde her sipariş varlığı için başvuru döndürür:  
  
```  
SELECT REF(o) AS OrderID FROM Orders AS o  
```  
  
 Çıktı:  
  
|Değer|  
|-----------|  
|1.|  
|2|  
|3|  
|...|  
  
 Aşağıdaki örnek, bir varlığın bir özelliğe erişmek için özelliği çıkarma işleci (.) kullanır. Özelliği ayıklama işleci kullanılmadığında otomatik olarak başvurusu kaldırılmış bir başvurudur.  
  
 Örnek:  
  
```  
SELECT VALUE REF(p).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 Çıktı:  
  
|Değer|  
|-----------|  
|Ayarlanabilir yarış|  
|Çok amaçlı bisiklet bağımsız|  
|AWC logolu Kasket|  
|...|  
  
### <a name="deref"></a>DEREF  
 [DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md) başvuru değeri ve bu sonucu başvuru oluşturur başvurusunu kaldırır. Örneğin, aşağıdaki sorguyu siparişler varlık kümesindeki her sipariş için sipariş varlıklara üretir: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`...  
  
 Örnek:  
  
```  
SELECT VALUE DEREF(REF(p)).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 Çıktı:  
  
|Değer|  
|-----------|  
|Ayarlanabilir yarış|  
|Çok amaçlı bisiklet bağımsız|  
|AWC logolu Kasket|  
|...|  
  
### <a name="createref-and-key"></a>CREATEREF VE ANAHTARI  
 [CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md) bir anahtarını geçirerek başvuru oluşturur. [ANAHTAR](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md) ifade türü referansı ile anahtar bölümünü ayıklar.  
  
 Örnek:  
  
```  
SELECT VALUE Key(CreateRef(AdventureWorksEntities.Product, row(p.ProductID)))   
    FROM AdventureWorksEntities.Product as p  
```  
  
 Çıktı:  
  
|ProductID|  
|---------------|  
|980|  
|365|  
|771|  
|...|  
  
## <a name="functions"></a>İşlevler  
  
### <a name="canonical"></a>Canonical  
 Ad alanı için [kurallı işlevler](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) Edm, olarak olduğundan `Edm.Length("string")`. Kurallı işlev ile aynı ada sahip bir işlev içeren başka bir ad alanı içe sürece ad alanını belirtmek zorunda değildir. İki ad alanı aynı işlevi varsa, kullanıcı özel tam adı gerekir.  
  
 Örnek:  
  
```  
SELECT Length(c. FirstName) As NameLen FROM   
    AdventureWorksEntities.Contact AS c   
    WHERE c.ContactID BETWEEN 10 AND 12  
```  
  
 Çıktı:  
  
|NameLen|  
|-------------|  
|6|  
|6|  
|5|  
  
### <a name="microsoft-provider-specific"></a>Microsoft sağlayıcıya özgü  
 [Microsoft sağlayıcısı özel işlevler](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md) bulunan `SqlServer` ad alanı.  
  
 Örnek:  
  
```  
SELECT SqlServer.LEN(c.EmailAddress) As EmailLen FROM   
    AdventureWorksEntities.Contact AS c WHERE   
    c.ContactID BETWEEN 10 AND 12  
```  
  
 Çıktı:  
  
|EmailLen|  
|--------------|  
|27|  
|27|  
|26|  
  
## <a name="namespaces"></a>Ad Alanları  
 [KULLANARAK](../../../../../../docs/framework/data/adonet/ef/language-reference/using-entity-sql.md) sorgu ifadesinde kullanılan ad alanlarını belirtir.  
  
 Örnek:  
  
```  
using SqlServer; LOWER('AA');  
```  
  
 Çıktı:  
  
|Değer|  
|-----------|  
|aa|  
  
## <a name="paging"></a>Disk belleği  
 Disk belleği bildirerek ifade edilen bir [atla](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) ve [sınırı](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) için alt yan tümceleri [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) yan tümcesi.  
  
 Örnek:  
  
```  
SELECT c.ContactID as ID, c.LastName as Name FROM   
    AdventureWorks.Contact AS c ORDER BY c.ContactID SKIP 9 LIMIT 3;  
```  
  
 Çıktı:  
  
|Kimlik|Ad|  
|--------|----------|  
|10|Adina|  
|11|Agcaoili|  
|12|Aguilar|  
  
## <a name="grouping"></a>Gruplandırma  
 [GRUPLANDIRMA tarafından](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) bir sorgu tarafından döndürülen hangi nesnelere grupları belirtir ([seçin](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) ifade olan yerleştirilecek.  
  
 Örnek:  
  
```  
SELECT VALUE name FROM AdventureWorksEntities.Product as P   
    GROUP BY P.Name HAVING MAX(P.ListPrice) > 5  
```  
  
 Çıktı:  
  
|name|  
|----------|  
|Tümünü Sıradağlar bilgisayar bütünleştirilmiş kod|  
|ML Sıradağlar bilgisayar bütünleştirilmiş kod|  
|HL Sıradağlar bilgisayar bütünleştirilmiş kod|  
|...|  
  
## <a name="navigation"></a>Gezinti  
 İlişkinin gezinme işleci bir varlıktan (Bitiş) (sona erdirmek için) başka bir ilişkisi üzerinden gitmenizi sağlar. [NAVIGATE](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md) ilişki türü tam olarak alır \<ad alanı >.\< ilişki türü adı >. Git başvuru dönüşleri\<T >, kardinalitesi sonlandırmak için 1'dir. Varsa önem düzeyini sonlandırmak için n, koleksiyonu olan < Ref\<T >> döndürülür.  
  
 Örnek:  
  
```  
SELECT a.AddressID, (SELECT VALUE DEREF(v) FROM   
    NAVIGATE(a, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS v)   
    FROM AdventureWorksEntities.Address AS a  
```  
  
 Çıktı:  
  
|AddressID|  
|---------------|  
|1.|  
|2|  
|3|  
|...|  
  
## <a name="select-value-and-select"></a>DEĞER VE SEÇ'İ SEÇİN  
  
### <a name="select-value"></a>DEĞER SEÇİN  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] SELECT VALUE yan tümcesi, örtük satır oluşturma atlamayı sağlar. SELECT VALUE yan tümcesinde yalnızca bir öğe belirtilebilir. Böyle bir yan tümcesi kullanıldığında, öğelerin SELECT yan tümcesinde etrafında hiçbir satır sarmalayıcı oluşturulur ve istediğiniz şekle koleksiyonu, örneğin üretilebilir: `SELECT VALUE a`.  
  
 Örnek:  
  
```  
SELECT VALUE p.Name FROM AdventureWorksEntities.Product as p  
```  
  
 Çıktı:  
  
|Ad|  
|----------|  
|Ayarlanabilir yarış|  
|Çok amaçlı bisiklet bağımsız|  
|AWC logolu Kasket|  
|...|  
  
### <a name="select"></a>SEÇ  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] row oluşturucusunda rastgele satırları oluşturmak için de sağlar. SELECT yansıtma bir veya daha fazla öğeleri ve sonuçları bir veri kayıttaki alanları ile örneğin alır: `SELECT a, b, c`.  
  
 Örnek:  
  
 SELECT p.Name, p.ProductID AdventureWorksEntities.Product p çıktı olarak gelen:  
  
|Ad|ProductID|  
|----------|---------------|  
|Ayarlanabilir yarış|1.|  
|Çok amaçlı bisiklet bağımsız|879|  
|AWC logolu Kasket|712|  
|...|...|  
  
## <a name="case-expression"></a>CASE İFADESİ  
 [Case ifadesi](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md) sonucu belirlemek için Boolean ifadeler bir dizi olarak değerlendirilir.  
  
 Örnek:  
  
```  
CASE WHEN AVG({25,12,11}) < 100 THEN TRUE ELSE FALSE END  
```  
  
 Çıktı:  
  
|Değer|  
|-----------|  
|TRUE|  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Entity SQL’e Genel Bakış](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
