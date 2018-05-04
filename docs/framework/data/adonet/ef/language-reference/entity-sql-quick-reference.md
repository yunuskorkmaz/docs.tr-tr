---
title: Varlık SQL hızlı başvuru
ms.date: 03/30/2017
ms.assetid: e53dad9e-5e83-426e-abb4-be3e78e3d6dc
ms.openlocfilehash: 0617ce96acaf5a6eafb2658cfe218cc8f4135f6e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="entity-sql-quick-reference"></a>Varlık SQL hızlı başvuru
Bu konu, hızlı başvuru sağlar [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgular. Bu konuda sorgularda AdventureWorks satış model üzerinde temel alır.  
  
## <a name="literals"></a>Sabit değerler  
  
### <a name="string"></a>Dize  
 Unicode ve Unicode olmayan karakter dize değişmez değerleri vardır. Unicode dizelerini ile n $a Örneğin, `N'hello'`.  
  
 Unicode olmayan dize sabit değeri bir örneği verilmiştir:  
  
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
 DateTime değişmez değerlerine tarih ve saat bölümleri zorunludur. Varsayılan değerler yoktur.  
  
 Örnek:  
  
```  
DATETIME '2006-12-25 01:01:00.000'   
--same as  
DATETIME '2006-12-25 01:01'  
```  
  
 Çıktı:  
  
|Değer|  
|-----------|  
|12/25/2006 1:01:00 AM|  
  
### <a name="integer"></a>Tamsayı  
 Tamsayı değişmez değerleri Int32 türünde olabilir (123) UInt32 (123U) Int64 (123L) ve UInt64 (123UL).  
  
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
 Tarafından desteklenen diğer değişmez değerleri [!INCLUDE[esql](../../../../../../includes/esql-md.md)] olan GUID, ikili, Float/Double, Decimal, ve `null`. Null değişmez değerlerine [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kavramsal modeldeki her bir türü ile uyumlu olduğu kabul edilir.  
  
## <a name="type-constructors"></a>Türü oluşturucuları  
  
### <a name="row"></a>SATIR  
 [Satır](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md) gibi bir anonim, yapısal olarak yazılan (kayıt) değeri oluşturur: `ROW(1 AS myNumber, ‘Name’ AS myName).`  
  
 Örnek:  
  
```  
SELECT VALUE row (product.ProductID as ProductID, product.Name   
    as ProductName) FROM AdventureWorksEntities.Product AS product  
```  
  
 Çıktı:  
  
|ProductID|Ad|  
|---------------|----------|  
|1.|Ayarlanabilir yarış|  
|879|Çok amaçlı bisiklet yedek|  
|712|AWC logosu Cap|  
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
|842|Tur Panniers, büyük|PA T100|…|  
  
### <a name="object"></a>Nesne  
 [Tür oluşturucu adlı](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md) gibi kullanıcı tanımlı (adlandırılmış) nesneleri oluşturur `person("abc", 12)`.  
  
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
  
### <a name="ref"></a>REF  
 [REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md) bir varlık türü örneğine başvuru oluşturur. Örneğin, aşağıdaki sorguyu her sipariş varlık başvuruları siparişleri varlık kümesinde döndürür:  
  
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
  
 Aşağıdaki örnek, bir varlığın bir özelliğe erişmek için özelliği ayıklama işleci (.) kullanır. Özellik ayıklama operatörü kullanıldığında, otomatik olarak dereferenced başvurudur.  
  
 Örnek:  
  
```  
SELECT VALUE REF(p).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 Çıktı:  
  
|Değer|  
|-----------|  
|Ayarlanabilir yarış|  
|Çok amaçlı bisiklet yedek|  
|AWC logosu Cap|  
|...|  
  
### <a name="deref"></a>DEREF  
 [DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md) dereferences bir başvuru değer ve başvuru sonucu, üretir. Örneğin, aşağıdaki sorguyu her siparişleri varlık kümesini sırayla için sipariş varlıklara üretir: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`...  
  
 Örnek:  
  
```  
SELECT VALUE DEREF(REF(p)).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 Çıktı:  
  
|Değer|  
|-----------|  
|Ayarlanabilir yarış|  
|Çok amaçlı bisiklet yedek|  
|AWC logosu Cap|  
|...|  
  
### <a name="createref-and-key"></a>CREATEREF VE ANAHTARI  
 [CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md) bir anahtar geçirme bir başvuru oluşturur. [ANAHTAR](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md) türü başvurusu olan bir ifade anahtar bölümünü ayıklar.  
  
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
  
### <a name="canonical"></a>Kurallı  
 Ad alanı için [kurallı işlevleri](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) Edm, olarak yer `Edm.Length("string")`. Kurallı işlevi olarak aynı ada sahip bir işlevi içeren başka bir ad alanı içe sürece ad belirtmeniz gerekmez. İki ad alanı aynı işlevi varsa, kullanıcı özel tam adı olmalıdır.  
  
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
 [Microsoft sağlayıcıya özgü işlevleri](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md) bulunan `SqlServer` ad alanı.  
  
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
 [KULLANARAK](../../../../../../docs/framework/data/adonet/ef/language-reference/using-entity-sql.md) sorgu ifadesinde kullanılan ad belirtir.  
  
 Örnek:  
  
```  
using SqlServer; LOWER('AA');  
```  
  
 Çıktı:  
  
|Değer|  
|-----------|  
|aa|  
  
## <a name="paging"></a>Disk belleği  
 Disk belleği bildirerek ifade edilen bir [atla](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) ve [sınırı](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) alt yan tümceleri [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) yan tümcesi.  
  
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
 [GRUPLANDIRMA tarafından](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) bir sorgu tarafından döndürülen hangi nesneleri içine grupları belirtir ([seçin](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) ifade olan yerleştirilecek.  
  
 Örnek:  
  
```  
SELECT VALUE name FROM AdventureWorksEntities.Product as P   
    GROUP BY P.Name HAVING MAX(P.ListPrice) > 5  
```  
  
 Çıktı:  
  
|name|  
|----------|  
|ÜM Sıradağlar bilgisayar başına derleme|  
|ML Sıradağlar bilgisayar başına derleme|  
|HL Sıradağlar bilgisayar başına derleme|  
|...|  
  
## <a name="navigation"></a>Gezinme  
 İlişki Gezinti işleci bir varlıktan (Bitiş) (sona erdirmek için) başka bir ilişkiden üzerinden giderek sağlar. [Bul](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md) ilişki türü tam olarak sürer \<ad alanı >.\< ilişki türü adı >. Gidin başvuru dönüşleri\<T >, önemi sona erdirmek için 1'dir. Varsa önemi sonuna n, toplama, < Ref\<T >> döndürülür.  
  
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
  
## <a name="select-value-and-select"></a>DEĞER SEÇİP SEÇİN  
  
### <a name="select-value"></a>DEĞERİNİ SEÇİN  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] örtük satır yapım atlamak için SELECT VALUE yan tümcesi sağlar. SELECT VALUE yan tümcesinde yalnızca bir öğe belirtilebilir. Bu tür bir yan tümcesi kullanıldığında, hiçbir satır sarmalayıcı SELECT yan tümcesinde öğelerin etrafında oluşturulur ve istediğiniz şekli koleksiyonu, örneğin üretilmiş olabilecek: `SELECT VALUE a`.  
  
 Örnek:  
  
```  
SELECT VALUE p.Name FROM AdventureWorksEntities.Product as p  
```  
  
 Çıktı:  
  
|Ad|  
|----------|  
|Ayarlanabilir yarış|  
|Çok amaçlı bisiklet yedek|  
|AWC logosu Cap|  
|...|  
  
### <a name="select"></a>SEÇ  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] row Oluşturucusu rasgele satırları oluşturmak için de sağlar. SELECT yansıtma bir veya daha fazla öğe ve bir veri kaydını alanları ile sonuçlanır örneğin alır: `SELECT a, b, c`.  
  
 Örnek:  
  
 SELECT p.Name, p.ProductID AdventureWorksEntities.Product p çıktı olarak gelen:  
  
|Ad|ProductID|  
|----------|---------------|  
|Ayarlanabilir yarış|1.|  
|Çok amaçlı bisiklet yedek|879|  
|AWC logosu Cap|712|  
|...|...|  
  
## <a name="case-expression"></a>CASE DEYİMİ  
 [Case deyimi](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md) sonucu belirlemek için Boole ifadeleri birtakım değerlendirir.  
  
 Örnek:  
  
```  
CASE WHEN AVG({25,12,11}) < 100 THEN TRUE ELSE FALSE END  
```  
  
 Çıktı:  
  
|Değer|  
|-----------|  
|TRUE|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Entity SQL’e Genel Bakış](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
