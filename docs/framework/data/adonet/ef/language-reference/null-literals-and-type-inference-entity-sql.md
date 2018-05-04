---
title: Değişmez değerler ve tür çıkarma (varlık SQL) null
ms.date: 03/30/2017
ms.assetid: edd56afb-af1b-4e7d-b210-cb8998143426
ms.openlocfilehash: 74ff2b459488f896c5ea6af4f7d1e045da5a7983
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="null-literals-and-type-inference-entity-sql"></a>Değişmez değerler ve tür çıkarma (varlık SQL) null
Null değişmez değerleri herhangi bir türü ile uyumlu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sistem yazın. Ancak, bir null hazır değeri doğru çıkarımı yapılan tür için [!INCLUDE[esql](../../../../../../includes/esql-md.md)] bir null hazır değeri kullanıldığı belirli kısıtlamaları getirir.  
  
## <a name="typed-nulls"></a>Tür null  
 Tür null her yerde kullanılabilir. Türü bilindiğinden tür çıkarımı tür null için gerekli değildir. Örneğin, aşağıdaki Int16 türünde bir null oluşturabileceğiniz [!INCLUDE[esql](../../../../../../includes/esql-md.md)] oluşturun:  
  
 `(cast(null as Int16))`  
  
## <a name="free-floating-null-literals"></a>Serbest kaydırılan Null değişmez değerleri  
 Serbest kaydırılan null değişmez değerleri aşağıdaki bağlamlarında kullanılabilir:  
  
-   Bir bağımsız değişkeni bir CAST veya kabul ifadesi. Türü belirtilmiş bir null ifadesi üretmek için önerilen yöntem budur.  
  
-   Bağımsız değişken olarak bir yöntem veya bir işlev. Standart aşırı kurallar geçerlidir.  
  
-   Gibi aritmetik bir ifade bağımsız değişkenlerinden biri olarak +, -, veya /. Başka bir bağımsız değişken null değişmez değerleri olamaz, aksi takdirde tür çıkarımı mümkün değildir.  
  
-   Mantıksal bir ifade bağımsız değişkenlerden biri olarak (AND, OR veya değil). Tüm bağımsız değişkenler, Boolean türünde bilinmektedir.  
  
-   Bağımsız değişkeni bir IS NULL veya IS NOT NULL ifadesi.  
  
-   Bir veya daha fazlası için benzer bir ifade bağımsız. Tüm bağımsız değişkenler dizeleri olması beklenir.  
  
-   Bir veya daha fazla adlı Tür oluşturucu bağımsız.  
  
-   Bir veya daha çok kümeli oluşturucuya bağımsız. Çok kümeli Oluşturucusu en az bir bağımsız değişkeni bir null hazır değeri olmayan bir ifade olmalıdır.  
  
-   Bir veya daha fazla sonra veya başka bir servis talebi ifadesinde ifadeleri. SONRA veya başka büyük ifade ifadelerinde en az biri null sabit değer dışında bir ifade olmalıdır.  
  
 Diğer senaryolarda serbest kaydırılan null değişmez değerler kullanılamaz. Örneğin, bunlar bir satır oluşturucusunda bağımsız değişken olarak kullanılamaz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Entity SQL’e Genel Bakış](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
