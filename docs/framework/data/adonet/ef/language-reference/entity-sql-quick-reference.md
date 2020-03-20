---
title: Entity SQL Hızlı Başvurusu
ms.date: 03/30/2017
ms.assetid: e53dad9e-5e83-426e-abb4-be3e78e3d6dc
ms.openlocfilehash: fc7cf8f8f692f9dc4230569d5f575b6d5fad19fa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150356"
---
# <a name="entity-sql-quick-reference"></a>Entity SQL Hızlı Başvurusu
Bu konu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgulara hızlı bir başvuru sağlar. Bu konudaki sorgular AdventureWorks Satış modeline dayanır.  
  
## <a name="literals"></a>Sabit değerler  
  
### <a name="string"></a>Dize  
 Unicode ve unicode olmayan karakter dize literals vardır. Unicode dizeleri N ile hazırlanır. Örneğin, `N'hello'`.  
  
 Aşağıdaki bir Unicode olmayan dize literal bir örnektir:  
  
```sql  
'hello'  
--same as  
"hello"  
```  
  
 Çıktı:  
  
|Değer|  
|-----------|  
|hello|  
  
### <a name="datetime"></a>DateTime  
 DateTime literals'de hem tarih hem de saat bölümleri zorunludur. Varsayılan değer yok.  
  
 Örnek:  
  
```sql  
DATETIME '2006-12-25 01:01:00.000'
--same as  
DATETIME '2006-12-25 01:01'  
```  
  
 Çıktı:  
  
|Değer|  
|-----------|  
|25.12.2006 01:01:00|  
  
### <a name="integer"></a>Tamsayı  
 İnt32 (123), UInt32 (123U), Int64 (123L) ve UInt64 (123UL) türünden olabilir.  
  
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
 Guid, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] İkili, Float/Double, Ondalık ve `null`. Null literals [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kavramsal modelde her tür ile uyumlu olarak kabul edilir.  
  
## <a name="type-constructors"></a>Tip Yapıcılar  
  
### <a name="row"></a>ROW  
 [ROW,](row-entity-sql.md) anonim, yapısal olarak yazılan (kayıt) bir değer şunları yla inşa eder:`ROW(1 AS myNumber, ‘Name’ AS myName).`  
  
 Örnek:  
  
```sql  
SELECT VALUE row (product.ProductID AS ProductID, product.Name
    AS ProductName) FROM AdventureWorksEntities.Product AS product
```  
  
 Çıktı:  
  
|ProductID|Adı|  
|---------------|----------|  
|1|Ayarlanabilir Yarış|  
|879|Çok Amaçlı Bisiklet Standı|  
|712|AWC Logo Kapağı|  
|...|...|  
  
### <a name="multiset"></a>MULTISET  
 [MULTISET,](multiset-entity-sql.md) şu gibi koleksiyonlar inşa eder:  
  
 `MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`  
  
 Örnek:  
  
```sql  
SELECT VALUE product FROM AdventureWorksEntities.Product AS product WHERE product.ListPrice IN MultiSet (125, 300)  
```  
  
 Çıktı:  
  
|ProductID|Adı|Productnumber|…|  
|---------------|----------|-------------------|-------|  
|842|Touring-Panniers, Büyük|PA-T100|…|  
  
### <a name="object"></a>Nesne  
 [Adlandırılmış Tür Oluşturucu](named-type-constructor-entity-sql.md) , kullanıcı tanımlı nesneler `person("abc", 12)`(adlandırılmış) yapıları gibi.  
  
 Örnek:  
  
```sql  
SELECT VALUE AdventureWorksModel.SalesOrderDetail (o.SalesOrderDetailID, o.CarrierTrackingNumber, o.OrderQty,
o.ProductID, o.SpecialOfferID, o.UnitPrice, o.UnitPriceDiscount,
o.rowguid, o.ModifiedDate) FROM AdventureWorksEntities.SalesOrderDetail
AS o  
```  
  
 Çıktı:  
  
|Satış SiparişdetayID|TaşıyıcıTakip Numarası|OrderQty|ProductID|...|  
|------------------------|---------------------------|--------------|---------------|---------|  
|1|4911-403C-98|1|776|...|  
|2|4911-403C-98|3|777|...|  
|...|...|...|...|...|  
  
## <a name="references"></a>Başvurular  
  
### <a name="ref"></a>REF  
 [REF,](ref-entity-sql.md) varlık türü örneğine bir başvuru oluşturur. Örneğin, aşağıdaki sorgu, Siparişler varlık kümesindeki her Sipariş varlığına başvuruları döndürür:  
  
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
  
 Aşağıdaki örnek, bir varlığın özelliğine erişmek için özellik ayıklama işleci (.) kullanır. Özellik ayıklama işleci kullanıldığında, başvuru otomatik olarak başvurudan çıkarılatır.  
  
 Örnek:  
  
```sql  
SELECT VALUE REF(p).Name FROM
    AdventureWorksEntities.Product AS p
```  
  
 Çıktı:  
  
|Değer|  
|-----------|  
|Ayarlanabilir Yarış|  
|Çok Amaçlı Bisiklet Standı|  
|AWC Logo Kapağı|  
|...|  
  
### <a name="deref"></a>DEREF  
 [DEREF](deref-entity-sql.md) bir referans değerini dereferences ve bu dereference sonucu üretir. Örneğin, aşağıdaki sorgu, Siparişler varlık kümesindeki her Sipariş `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`için Sipariş varlıklarını üretir: ..  
  
 Örnek:  
  
```sql  
SELECT VALUE DEREF(REF(p)).Name FROM
    AdventureWorksEntities.Product AS p
```  
  
 Çıktı:  
  
|Değer|  
|-----------|  
|Ayarlanabilir Yarış|  
|Çok Amaçlı Bisiklet Standı|  
|AWC Logo Kapağı|  
|...|  
  
### <a name="createref-and-key"></a>CREATEREF VE ANAHTAR  
 [CREATEREF](createref-entity-sql.md) bir anahtar geçen bir başvuru oluşturur. [KEY,](key-entity-sql.md) bir ifadenin tür başvurusu yla anahtar kısmını ayıklar.  
  
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
 [Kanonik işlevler](canonical-functions.md) için ad alanı Edm'dir. `Edm.Length("string")` Kanonik bir işlevle aynı ada sahip bir işlev içeren başka bir ad alanı içe aktarılmadığı sürece ad alanını belirtmeniz gerekmez. İki ad alanı aynı işleve sahipse, kullanıcı tam adı belirli yormalıdır.  
  
 Örnek:  
  
```sql  
SELECT Length(c. FirstName) AS NameLen FROM
    AdventureWorksEntities.Contact AS c
    WHERE c.ContactID BETWEEN 10 AND 12  
```  
  
 Çıktı:  
  
|NameLen|  
|-------------|  
|6|  
|6|  
|5|  
  
### <a name="microsoft-provider-specific"></a>Microsoft Sağlayıcıya Özel  
 [Microsoft sağlayıcıya](../sqlclient-for-ef-functions.md) `SqlServer` özgü işlevler ad alanındadır.  
  
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
 [USING,](using-entity-sql.md) sorgu ifadesinde kullanılan ad alanlarını belirtir.  
  
 Örnek:  
  
```sql  
using SqlServer; LOWER('AA');  
```  
  
 Çıktı:  
  
|Değer|  
|-----------|  
|aa|  
  
## <a name="paging"></a>Sayfalama  
 Sayfalama, [ORDER BY](order-by-entity-sql.md) yan tümcesine BIR [SKIP](skip-entity-sql.md) ve [LIMIT](limit-entity-sql.md) alt yan tümcesi belirtilerek ifade edilebilir.  
  
 Örnek:  
  
```sql  
SELECT c.ContactID as ID, c.LastName AS Name FROM
    AdventureWorks.Contact AS c ORDER BY c.ContactID SKIP 9 LIMIT 3;  
```  
  
 Çıktı:  
  
|Kimlik|Adı|  
|--------|----------|  
|10|Adina|  
|11|Alkan|  
|12|Aguilar|  
  
## <a name="grouping"></a>Gruplandırma  
 [GROUPING By,](group-by-entity-sql.md) sorgu[(SELECT](select-entity-sql.md)) ifadesi ile döndürülen nesnelerin yerleştirileceğini belirten gruplar dır.  
  
 Örnek:  
  
```sql  
SELECT VALUE name FROM AdventureWorksEntities.Product AS P
    GROUP BY P.Name HAVING MAX(P.ListPrice) > 5  
```  
  
 Çıktı:  
  
|ad|  
|----------|  
|LL Dağ Koltuk Montajı|  
|ML Dağ Koltuk Montajı|  
|HL Dağ Koltuk Montajı|  
|...|  
  
## <a name="navigation"></a>Gezinti  
 İlişki gezintisi işleci, bir varlıktan (uçtan uca) ilişki üzerinde gezinmenizi sağlar. [NAVIGATE,](navigate-entity-sql.md) ad alanı \<olarak nitelikli ilişki türünü> alır. \<ilişki türü adı>. Gezinme,\<sonuna kadar olan ın kardinalliği 1 ise Ref T> döndürür. Sonuna kadar olan kardinallik n ise, Ref\<T>><Tahsilat ı iade edilir.  
  
 Örnek:  
  
```sql  
SELECT a.AddressID, (SELECT VALUE DEREF(v) FROM
    NAVIGATE(a, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS v)
    FROM AdventureWorksEntities.Address AS a  
```  
  
 Çıktı:  
  
|Addressıd|  
|---------------|  
|1|  
|2|  
|3|  
|...|  
  
## <a name="select-value-and-select"></a>DEĞER SEÇIN VE SEÇIN  
  
### <a name="select-value"></a>DEĞER SEÇ  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]örtülü satır yapımını atlamak için SELECT VALUE yan tümcesini sağlar. SELECT VALUE yan tümcesinde yalnızca bir öğe belirtilebilir. Böyle bir yan tümce kullanıldığında, SELECT yan tümcesindeki öğelerin etrafına satır sarıcı oluşturulmaz `SELECT VALUE a`ve örneğin istenen şeklin bir koleksiyonu oluşturulabilir: .  
  
 Örnek:  
  
```sql  
SELECT VALUE p.Name FROM AdventureWorksEntities.Product AS p
```  
  
 Çıktı:  
  
|Adı|  
|----------|  
|Ayarlanabilir Yarış|  
|Çok Amaçlı Bisiklet Standı|  
|AWC Logo Kapağı|  
|...|  
  
### <a name="select"></a>SELECT  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]ayrıca satır oluşturucuya rasgele satırlar oluşturmasını sağlar. SELECT projeksiyonda bir veya daha fazla öğe alır ve örneğin `SELECT a, b, c`alanları içeren bir veri kaydıyla sonuçlanır: .  
  
 Örnek:  
  
 SELECT p.Name, p.ProductID FROM AdventureWorksEntities.Product as p Output:  
  
|Adı|ProductID|  
|----------|---------------|  
|Ayarlanabilir Yarış|1|  
|Çok Amaçlı Bisiklet Standı|879|  
|AWC Logo Kapağı|712|  
|...|...|  
  
## <a name="case-expression"></a>BÜYÜK/KÜÇÜK HARF İfadeSI  
 [Örnek durum ifadesi](case-entity-sql.md) sonucu belirlemek için Boolean ifadeler kümesini değerlendirir.  
  
 Örnek:  
  
```sql  
CASE WHEN AVG({25,12,11}) < 100 THEN TRUE ELSE FALSE END  
```  
  
 Çıktı:  
  
|Değer|  
|-----------|  
|TRUE|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
- [Entity SQL’e Genel Bakış](entity-sql-overview.md)
