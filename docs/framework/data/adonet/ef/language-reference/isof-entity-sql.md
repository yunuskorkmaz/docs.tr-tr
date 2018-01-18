---
title: "ISOF (varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5b2b0d34-d0a7-4bcd-baf2-58aa8456d00b
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 24abe7be9acb01b81f4d2a76d74c2f75bdb7786f
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="isof-entity-sql"></a>ISOF (varlık SQL)
İfade türü belirtilen türe veya onun alt türlerinden birini olup olmadığını belirler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
expression IS [ NOT ] OF ( [ ONLY ] type )  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Türü belirlemek için tüm geçerli sorgu ifadesi.  
  
 NOT  
 EDM üzerindeki geçersiz kılar. Boolean sonucu olduğundan.  
  
 YALNIZCA  
 OLDUĞUNDAN, döndüren belirtir `true` yalnızca `expression` türü `type` ve herhangi bir alt türleri.  
  
 `type`  
 Test etmek için türü `expression` karşı. Türü, ad alanı nitelenmiş olmalıdır.  
  
## <a name="return-value"></a>Dönüş Değeri  
 `true`varsa `expression` olan T ve T bir taban türü veya türetilmiş bir tür türünde `type`; null ise `expression` çalışma zamanında null; Aksi takdirde, `false`.  
  
## <a name="remarks"></a>Açıklamalar  
 İfadeleri `expression IS NOT OF (type)` ve `expression IS NOT OF (ONLY type)` sözdizimsel olarak eşdeğerdir `NOT (expression IS OF (type))` ve `NOT (expression IS OF (ONLY type))`sırasıyla.  
  
 Aşağıdaki tabloda davranışını gösterilmektedir `IS OF` bazı tipik - ve köşe desenleri üzerinden işleci. Sağlayıcı çağrılır önce tüm istemci tarafındaki özel durumlar:  
  
|Desen|Davranış|  
|-------------|--------------|  
|null olduğundan, (EntityType)|Oluşturur|  
|null olduğundan, (ComplexType)|Oluşturur|  
|null olduğundan, (RowType)|Oluşturur|  
|KABUL (null AS EntityType) olduğundan, (EntityType)|DBNull döndürür|  
|KABUL (null AS ComplexType) olduğundan, (ComplexType)|Oluşturur|  
|KABUL (null AS RowType) olduğundan, (RowType)|Oluşturur|  
|EntityType olan (ENTİTYTYPE)|True/false değerini döndürür|  
|ComplexType olduğu (COMPLEXTYPE)|Oluşturur|  
|RowType olduğu (RowType),|Oluşturur|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu bir sorgu ifadesinde türü belirlemek için olduğundan, işleci kullanır ve indirmelere türünde bir nesne OnsiteCourse türündeki nesneler koleksiyonuna dönüştürmek için kabul işleci kullanır. Sorgu dayanır [Okul modeli](http://msdn.microsoft.com/en-us/859a9587-81ea-4a45-9bc0-f8d330e1adac).  
  
 [!code-csharp[DP EntityServices Concepts 2#TREAT_ISOF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#treat_isof)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
