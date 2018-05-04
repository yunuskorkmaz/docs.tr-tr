---
title: (Varlık SQL) gidin
ms.date: 03/30/2017
ms.assetid: f107f29d-005f-4e39-a898-17f163abb1d0
ms.openlocfilehash: c374261ad3702294f5720edb7881e21ba79d85bc
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="navigate-entity-sql"></a>(Varlık SQL) gidin
Varlıklar arasında kurulan ilişki üzerinden gider.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
navigate(instance-expresssion, [relationship-type], [to-end [, from-end] ])  
```  
  
## <a name="arguments"></a>Arguments  
 `instance-expresssion`  
 Bir varlık örneği.  
  
 `relationship-type`  
 Kavramsal şema tanım dili (CSDL) dosyasından ilişki türü adı. `relationship-type` Olarak nitelenmiş \<ad alanı >.\< ilişki türü adı >.  
  
 `to`  
 İlişki sonu.  
  
 `from`  
 İlişki başlangıcı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Varsa önemi sona erdirmek için 1 ise, dönüş değeri olacaktır `Ref<T>`. Varsa önemi sonuna n ise, dönüş değeri olacaktır `Collection<Ref<T>>`.  
  
## <a name="remarks"></a>Açıklamalar  
 İlişkileri olan birinci sınıf yapılardan [!INCLUDE[adonet_edm](../../../../../../includes/adonet-edm-md.md)] (EDM). İki veya daha fazla varlık türleri ilişkileri oluşturulabilir ve kullanıcılar bir uç (varlık) arasında ilişki üzerinden gezinebilir. `from` ve `to` ilişki içinde ad çözümlemesi belirsizlik olmaz olduğunda koşullu isteğe bağlıdır.  
  
 Bul O ve C alanı geçerli değil.  
  
 Bir gezinti yapısı genel form aşağıda verilmiştir:  
  
 gidin (`instance-expresssion`, `relationship-type`, [ `to-end` [, `from-end` ]])  
  
 Örneğin:  
  
```  
Select o.Id, navigate(o, OrderCustomer, Customer, Order)  
From LOB.Orders as o  
```  
  
 OrderCustomer olduğu `relationship`, müşteri ve sipariş `to-end` (müşteri) ve `from-end` (sırasıyla) ilişkisinin. OrderCustomer edildi n: 1 ilişki sonra Ref Bul ifade sonuç türü olan\<Müşteri >.  
  
 Bu ifade basit biçimidir aşağıda verilmiştir:  
  
```  
Select o.Id, navigate(o, OrderCustomer)  
From LOB.Orders as o  
```  
  
 Benzer şekilde, aşağıdaki biçimde bir sorguya Bul ifade bir koleksiyon oluşturur < Ref\<sipariş >>.  
  
```  
Select c.Id, navigate(c, OrderCustomer, Order, Customer)  
From LOB.Customers as c  
```  
  
 Örnek ifadesi, bir varlık/ref türü olmalıdır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki varlık SQL sorgusunu Bul işleci oluşturulan adresi ve SalesOrderHeader varlık türleri ilişkinin üzerinden gitmek için kullanır. Sorgu AdventureWorks satış modelini temel alır. Derlemek ve bu sorguyu çalıştırmak için aşağıdaki adımları izleyin:  
  
1.  Yordamı izleyin [nasıl yapılır: Sorgu döndürür StructuralType sonucu](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Aşağıdaki sorgu bağımsız değişken olarak geçirmek `ExecuteStructuralTypeQuery` yöntemi:  
  
 [!code-csharp[DP EntityServices Concepts 2#NAVIGATE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#navigate)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Nasıl yapılır: gidin ilişkileriyle gidin işleci](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md)
