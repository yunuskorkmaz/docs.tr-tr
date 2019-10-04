---
title: Entity SQL hızlı başvuru
ms.date: 03/30/2017
ms.assetid: e53dad9e-5e83-426e-abb4-be3e78e3d6dc
ms.openlocfilehash: 9ccfc461d394af8804c960ebf460e7fbfb025b64
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833868"
---
# <a name="entity-sql-quick-reference"></a>Entity SQL hızlı başvuru
Bu konu, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgularına hızlı bir başvuru sağlar. Bu konudaki sorgular AdventureWorks Sales Model ' i temel alır.  
  
## <a name="literals"></a>Leri  
  
### <a name="string"></a>Dize  
 Unicode ve Unicode olmayan karakter dizesi değişmez değerleri vardır. Unicode dizeleri, N ile sona erer. Örneğin, `N'hello'`.  
  
 Aşağıda Unicode olmayan bir dize sabit değeri örneği verilmiştir:  
  
```sql  
'hello'  
--same as  
"hello"  
```  
  
 Çıktı:  
  
|Değer|  
|-----------|  
|Herkese|  
  
### <a name="datetime"></a>Tarih Saat  
 DateTime değişmez değerlerinde hem tarih hem de saat kısımları zorunludur. Varsayılan değer yok.  
  
 Örnek:  
  
```sql  
DATETIME '2006-12-25 01:01:00.000'   
--same as  
DATETIME '2006-12-25 01:01'  
```  
  
 Çıktı:  
  
|Değer|  
|-----------|  
|12/25/2006 1:01:00|  
  
### <a name="integer"></a>Tamsayı  
 Tamsayı sabit değerleri Int32 (123), UInt32 (123U), Int64 (123L) ve UInt64 (123UL) türünde olabilir.  
  
 Örnek:  
  
```sql  
--a collection of integers  
{1, 2, 3}  
```  
  
 Çıktı:  
  
|Değer|  
|-----------|  
|1|  
|2|  
|3|  
  
### <a name="other"></a>Diğer  
 @No__t-0 tarafından desteklenen diğer sabit değerler GUID, Ikili, float/double, Decimal ve `null` ' dir. @No__t-0 ' daki null sabit değerler kavramsal modeldeki diğer her türle uyumlu olarak değerlendirilir.  
  
## <a name="type-constructors"></a>Tür oluşturucuları  
  
### <a name="row"></a>SıRADA  
 [Satır](row-entity-sql.md) , şu şekilde bir anonim, yapısal olarak yazılmış (kayıt) değeri oluşturur: `ROW(1 AS myNumber, ‘Name’ AS myName).`  
  
 Örnek:  
  
```sql  
SELECT VALUE row (product.ProductID AS ProductID, product.Name
    AS ProductName) FROM AdventureWorksEntities.Product AS product
```  
  
 Çıktı:  
  
|ProductID|Adı|  
|---------------|----------|  
|1|Ayarlanabilir yarış|  
|879|Tüm amaç bisiklet Standı|  
|712|AWC logosu üst sınırı|  
|...|...|  
  
### <a name="multiset"></a>DEĞERLERDEN  
 [Çoklu küme](multiset-entity-sql.md) yapıları, örneğin:  
  
 `MULTISET(1,2,2,3)` `--same as` @ no__t-2 @ no__t-3  
  
 Örnek:  
  
```sql  
SELECT VALUE product FROM AdventureWorksEntities.Product AS product WHERE product.ListPrice IN MultiSet (125, 300)  
```  
  
 Çıktı:  
  
|ProductID|Adı|ProductNumber|...|  
|---------------|----------|-------------------|-------|  
|842|Touring-Panniler, büyük|PA-T100|...|  
  
### <a name="object"></a>Nesne  
 [Adlandırılmış tür Oluşturucu](named-type-constructor-entity-sql.md) yapıları (adlandırılmış) `person("abc", 12)` gibi Kullanıcı tanımlı nesneler oluşturur.  
  
 Örnek:  
  
```sql  
SELECT VALUE AdventureWorksModel.SalesOrderDetail (o.SalesOrderDetailID, o.CarrierTrackingNumber, o.OrderQty,   
o.ProductID, o.SpecialOfferID, o.UnitPrice, o.UnitPriceDiscount,   
o.rowguid, o.ModifiedDate) FROM AdventureWorksEntities.SalesOrderDetail   
AS o  
```  
  
 Çıktı:  
  
|Salesorderdetailıd|CarrierTrackingNumber|Ordermik|ProductID|...|  
|------------------------|---------------------------|--------------|---------------|---------|  
|1|4911-403C-98|1|776|...|  
|2|4911-403C-98|3|777|...|  
|...|...|...|...|...|  
  
## <a name="references"></a>Başvurular  
  
### <a name="ref"></a>REF  
 [Ref](ref-entity-sql.md) bir varlık türü örneğine başvuru oluşturur. Örneğin, aşağıdaki sorgu, siparişler varlık kümesindeki her bir order varlığına başvuruları döndürür:  
  
```sql  
SELECT REF(o) AS OrderID FROM Orders AS o  
```  
  
 Çıktı:  
  
|Değer|  
|-----------|  
|1|  
|2|  
|3|  
|...|  
  
 Aşağıdaki örnek, bir varlığın bir özelliğine erişmek için özellik ayıklama işleci (.) kullanır. Özellik ayıklama işleci kullanıldığında, başvuru otomatik olarak başvuru yapılır.  
  
 Örnek:  
  
```sql  
SELECT VALUE REF(p).Name FROM   
    AdventureWorksEntities.Product AS p
```  
  
 Çıktı:  
  
|Değer|  
|-----------|  
|Ayarlanabilir yarış|  
|Tüm amaç bisiklet Standı|  
|AWC logosu üst sınırı|  
|...|  
  
### <a name="deref"></a>DEREF  
 [Deref](deref-entity-sql.md) bir başvuru değerine başvurur ve başvurunun sonucunu üretir. Örneğin, aşağıdaki sorgu, siparişler varlık kümesindeki her bir sıra için sıralama varlıklarını üretir: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`..  
  
 Örnek:  
  
```sql  
SELECT VALUE DEREF(REF(p)).Name FROM   
    AdventureWorksEntities.Product AS p
```  
  
 Çıktı:  
  
|Değer|  
|-----------|  
|Ayarlanabilir yarış|  
|Tüm amaç bisiklet Standı|  
|AWC logosu üst sınırı|  
|...|  
  
### <a name="createref-and-key"></a>CREATEREF VE ANAHTAR  
 [CreateRef](createref-entity-sql.md) anahtar geçirerek bir başvuru oluşturur. [Anahtar](key-entity-sql.md) , tür başvurusu olan bir ifadenin anahtar kısmını ayıklar.  
  
 Örnek:  
  
```sql  
SELECT VALUE Key(CreateRef(AdventureWorksEntities.Product, row(p.ProductID)))   
    FROM AdventureWorksEntities.Product AS p
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
 [Kurallı işlevler](canonical-functions.md) için ad alanı, `Edm.Length("string")` ' de olduğu gibi EDM ' dir. Kurallı bir işlevle aynı ada sahip bir işlev içeren başka bir ad alanı içeri aktarılmadığı sürece, ad alanını belirtmeniz gerekmez. İki ad alanı aynı işleve sahip ise, Kullanıcı tam adı özel olmalıdır.  
  
 Örnek:  
  
```sql  
SELECT Length(c. FirstName) AS NameLen FROM
    AdventureWorksEntities.Contact AS c   
    WHERE c.ContactID BETWEEN 10 AND 12  
```  
  
 Çıktı:  
  
|Ad uzunluğu|  
|-------------|  
|6|  
|6|  
|5|  
  
### <a name="microsoft-provider-specific"></a>Microsoft sağlayıcıya özgü  
 [Microsoft sağlayıcıya özgü işlevler](../sqlclient-for-ef-functions.md) `SqlServer` ad alanıdır.  
  
 Örnek:  
  
```sql  
SELECT SqlServer.LEN(c.EmailAddress) AS EmailLen FROM
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
 [USING](using-entity-sql.md) , bir sorgu ifadesinde kullanılan ad alanlarını belirtir.  
  
 Örnek:  
  
```sql  
using SqlServer; LOWER('AA');  
```  
  
 Çıktı:  
  
|Değer|  
|-----------|  
|aa|  
  
## <a name="paging"></a>Sayfalama  
 Sayfalama, bir [SKIP](skip-entity-sql.md) ve [LIMIT](limit-entity-sql.md) alt tümceleri [order by](order-by-entity-sql.md) yan tümcesine bildirerek ifade edilebilir.  
  
 Örnek:  
  
```sql  
SELECT c.ContactID as ID, c.LastName AS Name FROM
    AdventureWorks.Contact AS c ORDER BY c.ContactID SKIP 9 LIMIT 3;  
```  
  
 Çıktı:  
  
|Kimlik|Adı|  
|--------|----------|  
|10|Adina|  
|11|Agcaoili|  
|12|Agular|  
  
## <a name="grouping"></a>Gruplama  
 [Gruplandırma ölçütü](group-by-entity-sql.md) , sorgu ([Select](select-entity-sql.md)) ifadesi tarafından döndürülen nesnelerin yerleştirileceği grupları belirler.  
  
 Örnek:  
  
```sql  
SELECT VALUE name FROM AdventureWorksEntities.Product AS P
    GROUP BY P.Name HAVING MAX(P.ListPrice) > 5  
```  
  
 Çıktı:  
  
|ad|  
|----------|  
|LL Sıradağlar koltuk derlemesi|  
|ML Sıradağlar koltuk derlemesi|  
|HL Sıradağlar koltuk derlemesi|  
|...|  
  
## <a name="navigation"></a>Gezinme  
 İlişki gezintisi işleci, bir varlıktan (uçtan uca) ilişki üzerinde gezinmenize izin verir. [Git](navigate-entity-sql.md) , \<AD alanı > olarak nitelenmiş ilişki türünü alır. \<ilişki türü adı >. Git, to end 'in kardinalitei 1 ise ref @ no__t-0T > döndürür. To end 'in kardinalite değeri n ise, koleksiyon < ref @ no__t-0T > > döndürülür.  
  
 Örnek:  
  
```sql  
SELECT a.AddressID, (SELECT VALUE DEREF(v) FROM   
    NAVIGATE(a, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS v)   
    FROM AdventureWorksEntities.Address AS a  
```  
  
 Çıktı:  
  
|Adres SID 'si|  
|---------------|  
|1|  
|2|  
|3|  
|...|  
  
## <a name="select-value-and-select"></a>DEĞER ' I SEÇIN VE  
  
### <a name="select-value"></a>DEĞER SEÇIN  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)], örtük satır oluşturmayı atlamak için SELECT VALUE yan tümcesini sağlar. SELECT VALUE yan tümcesinde yalnızca bir öğe belirtilebilir. Böyle bir yan tümce kullanıldığında, SELECT yan tümcesindeki öğelerin çevresine satır sarmalayıcı oluşturulmadı ve istenen şeklin bir koleksiyonu üretile, örneğin: `SELECT VALUE a`.  
  
 Örnek:  
  
```sql  
SELECT VALUE p.Name FROM AdventureWorksEntities.Product AS p
```  
  
 Çıktı:  
  
|Adı|  
|----------|  
|Ayarlanabilir yarış|  
|Tüm amaç bisiklet Standı|  
|AWC logosu üst sınırı|  
|...|  
  
### <a name="select"></a>SELECT  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Ayrıca satır oluşturucusunu rastgele satırlar oluşturmak için de sağlar. Projeksiyde bir veya daha fazla öğe alır ve alanlar içeren bir veri kaydıyla sonuçlanır, örneğin: `SELECT a, b, c`.  
  
 Örnek:  
  
 AdventureWorksEntities. Product öğesinden p çıkışı olarak p.Name, p. ProductID 'yi SEÇIN:  
  
|Adı|ProductID|  
|----------|---------------|  
|Ayarlanabilir yarış|1|  
|Tüm amaç bisiklet Standı|879|  
|AWC logosu üst sınırı|712|  
|...|...|  
  
## <a name="case-expression"></a>CASE IFADESI  
 [Case ifadesi](case-entity-sql.md) sonucu belirleyecek bir dizi Boole ifadesi değerlendirir.  
  
 Örnek:  
  
```sql  
CASE WHEN AVG({25,12,11}) < 100 THEN TRUE ELSE FALSE END  
```  
  
 Çıktı:  
  
|Değer|  
|-----------|  
|DEĞERI|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL başvurusu](entity-sql-reference.md)
- [Entity SQL genel bakış](entity-sql-overview.md)
