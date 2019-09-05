---
title: Entity SQL Hızlı Başvurusu
ms.date: 03/30/2017
ms.assetid: e53dad9e-5e83-426e-abb4-be3e78e3d6dc
ms.openlocfilehash: 7780359d981b130118cb73d4892f3dcb4b6e2e7d
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251023"
---
# <a name="entity-sql-quick-reference"></a>Entity SQL Hızlı Başvurusu
Bu konu, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgulara hızlı bir başvuru sağlar. Bu konudaki sorgular AdventureWorks Sales Model ' i temel alır.  
  
## <a name="literals"></a>Sabit değerler  
  
### <a name="string"></a>Dize  
 Unicode ve Unicode olmayan karakter dizesi değişmez değerleri vardır. Unicode dizeleri, N ile sona erer. Örneğin, `N'hello'`.  
  
 Aşağıda Unicode olmayan bir dize sabit değeri örneği verilmiştir:  
  
```  
'hello'  
--same as  
"hello"  
```  
  
 Çıktı:  
  
|Değer|  
|-----------|  
|herkese|  
  
### <a name="datetime"></a>DateTime  
 DateTime değişmez değerlerinde hem tarih hem de saat kısımları zorunludur. Varsayılan değer yok.  
  
 Örnek:  
  
```  
DATETIME '2006-12-25 01:01:00.000'   
--same as  
DATETIME '2006-12-25 01:01'  
```  
  
 Çıktı:  
  
|Değer|  
|-----------|  
|12/25/2006 1:01:00|  
  
### <a name="integer"></a>Integer  
 Tamsayı sabit değerleri Int32 (123), UInt32 (123U), Int64 (123L) ve UInt64 (123UL) türünde olabilir.  
  
 Örnek:  
  
```  
--a collection of integers  
{1, 2, 3}  
```  
  
 Çıktı:  
  
|Değer|  
|-----------|  
|1\.|  
|2|  
|3|  
  
### <a name="other"></a>Diğer  
 Tarafından [!INCLUDE[esql](../../../../../../includes/esql-md.md)] desteklenen diğer sabit değerler GUID, ikili, float/double, Decimal ve `null`' dir. İçindeki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] null sabit değerler, kavramsal modeldeki diğer her türle uyumlu olarak değerlendirilir.  
  
## <a name="type-constructors"></a>Tür oluşturucuları  
  
### <a name="row"></a>ROW  
 [Satır](row-entity-sql.md) , içinde olduğu gibi anonim, yapısal olarak yazılmış bir (kayıt) değeri oluşturur:`ROW(1 AS myNumber, ‘Name’ AS myName).`  
  
 Örnek:  
  
```  
SELECT VALUE row (product.ProductID as ProductID, product.Name   
    as ProductName) FROM AdventureWorksEntities.Product AS product  
```  
  
 Çıktı:  
  
|ProductID|Ad|  
|---------------|----------|  
|1\.|Ayarlanabilir yarış|  
|879|Tüm amaç bisiklet Standı|  
|712|AWC logosu üst sınırı|  
|...|...|  
  
### <a name="multiset"></a>MULTISET  
 [Çoklu küme](multiset-entity-sql.md) yapıları, örneğin:  
  
 `MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`  
  
 Örnek:  
  
```  
SELECT VALUE product FROM AdventureWorksEntities.Product AS product WHERE product.ListPrice IN MultiSet (125, 300)  
```  
  
 Çıktı:  
  
|ProductID|Ad|ProductNumber|…|  
|---------------|----------|-------------------|-------|  
|842|Touring-Panniler, büyük|PA-T100|…|  
  
### <a name="object"></a>Nesne  
 [Adlandırılmış tür Oluşturucu](named-type-constructor-entity-sql.md) (adlandırılmış), `person("abc", 12)`gibi Kullanıcı tanımlı nesneler oluşturur.  
  
 Örnek:  
  
```  
SELECT VALUE AdventureWorksModel.SalesOrderDetail (o.SalesOrderDetailID, o.CarrierTrackingNumber, o.OrderQty,   
o.ProductID, o.SpecialOfferID, o.UnitPrice, o.UnitPriceDiscount,   
o.rowguid, o.ModifiedDate) FROM AdventureWorksEntities.SalesOrderDetail   
AS o  
```  
  
 Çıktı:  
  
|Salesorderdetailıd|CarrierTrackingNumber|Ordermik|ProductID|...|  
|------------------------|---------------------------|--------------|---------------|---------|  
|1\.|4911-403C-98|1\.|776|...|  
|2|4911-403C-98|3|777|...|  
|...|...|...|...|...|  
  
## <a name="references"></a>Referanslar  
  
### <a name="ref"></a>REF  
 [Ref](ref-entity-sql.md) bir varlık türü örneğine başvuru oluşturur. Örneğin, aşağıdaki sorgu, siparişler varlık kümesindeki her bir order varlığına başvuruları döndürür:  
  
```  
SELECT REF(o) AS OrderID FROM Orders AS o  
```  
  
 Çıktı:  
  
|Değer|  
|-----------|  
|1\.|  
|2|  
|3|  
|...|  
  
 Aşağıdaki örnek, bir varlığın bir özelliğine erişmek için özellik ayıklama işleci (.) kullanır. Özellik ayıklama işleci kullanıldığında, başvuru otomatik olarak başvuru yapılır.  
  
 Örnek:  
  
```  
SELECT VALUE REF(p).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 Çıktı:  
  
|Değer|  
|-----------|  
|Ayarlanabilir yarış|  
|Tüm amaç bisiklet Standı|  
|AWC logosu üst sınırı|  
|...|  
  
### <a name="deref"></a>DEREF  
 [Deref](deref-entity-sql.md) bir başvuru değerine başvurur ve başvurunun sonucunu üretir. Örneğin, aşağıdaki sorgu, siparişler varlık kümesindeki her bir sıra için sıra varlıklarını üretir: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`..  
  
 Örnek:  
  
```  
SELECT VALUE DEREF(REF(p)).Name FROM   
    AdventureWorksEntities.Product as p  
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
 [Kurallı işlevler](canonical-functions.md) için ad alanı, içinde `Edm.Length("string")`olduğu gibi EDM 'dir. Kurallı bir işlevle aynı ada sahip bir işlev içeren başka bir ad alanı içeri aktarılmadığı sürece, ad alanını belirtmeniz gerekmez. İki ad alanı aynı işleve sahip ise, Kullanıcı tam adı özel olmalıdır.  
  
 Örnek:  
  
```  
SELECT Length(c. FirstName) As NameLen FROM   
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
 [USING](using-entity-sql.md) , bir sorgu ifadesinde kullanılan ad alanlarını belirtir.  
  
 Örnek:  
  
```  
using SqlServer; LOWER('AA');  
```  
  
 Çıktı:  
  
|Değer|  
|-----------|  
|aa|  
  
## <a name="paging"></a>Disk Belleği  
 Sayfalama, bir [SKIP](skip-entity-sql.md) ve [LIMIT](limit-entity-sql.md) alt tümceleri [order by](order-by-entity-sql.md) yan tümcesine bildirerek ifade edilebilir.  
  
 Örnek:  
  
```  
SELECT c.ContactID as ID, c.LastName as Name FROM   
    AdventureWorks.Contact AS c ORDER BY c.ContactID SKIP 9 LIMIT 3;  
```  
  
 Çıktı:  
  
|ID|Ad|  
|--------|----------|  
|10|Adina|  
|11|Agcaoili|  
|12|Agular|  
  
## <a name="grouping"></a>Gruplandırma  
 [Gruplandırma ölçütü](group-by-entity-sql.md) , sorgu ([Select](select-entity-sql.md)) ifadesi tarafından döndürülen nesnelerin yerleştirileceği grupları belirler.  
  
 Örnek:  
  
```  
SELECT VALUE name FROM AdventureWorksEntities.Product as P   
    GROUP BY P.Name HAVING MAX(P.ListPrice) > 5  
```  
  
 Çıktı:  
  
|name|  
|----------|  
|LL Sıradağlar koltuk derlemesi|  
|ML Sıradağlar koltuk derlemesi|  
|HL Sıradağlar koltuk derlemesi|  
|...|  
  
## <a name="navigation"></a>Gezinti  
 İlişki gezintisi işleci, bir varlıktan (uçtan uca) ilişki üzerinde gezinmenize izin verir. [Git](navigate-entity-sql.md) > ad alanı olarak \<nitelenmiş ilişki türünü alır.\< ilişki türü adı >. To end 'in\<kardinalite değeri 1 ise, git, ref T > döndürür. To end 'in kardinalitei n ise, < ref\<T > > koleksiyonu döndürülür.  
  
 Örnek:  
  
```  
SELECT a.AddressID, (SELECT VALUE DEREF(v) FROM   
    NAVIGATE(a, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS v)   
    FROM AdventureWorksEntities.Address AS a  
```  
  
 Çıktı:  
  
|Adres SID 'si|  
|---------------|  
|1\.|  
|2|  
|3|  
|...|  
  
## <a name="select-value-and-select"></a>DEĞER ' I SEÇIN VE  
  
### <a name="select-value"></a>DEĞER SEÇIN  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]örtük satır oluşturmayı atlamak için değer Seç yan tümcesini sağlar. SELECT VALUE yan tümcesinde yalnızca bir öğe belirtilebilir. Böyle bir yan tümce kullanıldığında, SELECT yan tümcesindeki öğelerin çevresinde bir satır sarmalayıcı oluşturulmadı ve istenen şeklin bir koleksiyonu üretilebilinir, örneğin: `SELECT VALUE a`.  
  
 Örnek:  
  
```  
SELECT VALUE p.Name FROM AdventureWorksEntities.Product as p  
```  
  
 Çıktı:  
  
|Ad|  
|----------|  
|Ayarlanabilir yarış|  
|Tüm amaç bisiklet Standı|  
|AWC logosu üst sınırı|  
|...|  
  
### <a name="select"></a>SEÇ  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]Ayrıca satır oluşturucusunu rastgele satırlar oluşturmak için de sağlar. Projeksiyde bir veya daha fazla öğe alır ve alanlar içeren bir veri kaydıyla sonuçlanır, örneğin: `SELECT a, b, c`.  
  
 Örnek:  
  
 AdventureWorksEntities. Product öğesinden p çıkışı olarak p.Name, p. ProductID 'yi SEÇIN:  
  
|Ad|ProductID|  
|----------|---------------|  
|Ayarlanabilir yarış|1\.|  
|Tüm amaç bisiklet Standı|879|  
|AWC logosu üst sınırı|712|  
|...|...|  
  
## <a name="case-expression"></a>CASE IFADESI  
 [Case ifadesi](case-entity-sql.md) sonucu belirleyecek bir dizi Boole ifadesi değerlendirir.  
  
 Örnek:  
  
```  
CASE WHEN AVG({25,12,11}) < 100 THEN TRUE ELSE FALSE END  
```  
  
 Çıktı:  
  
|Değer|  
|-----------|  
|TRUE|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
- [Entity SQL’e Genel Bakış](entity-sql-overview.md)
