---
title: Null değişmez değerler ve tür çıkarımı (varlık SQL)
ms.date: 03/30/2017
ms.assetid: edd56afb-af1b-4e7d-b210-cb8998143426
ms.openlocfilehash: 3fea03146549f3d42bf08bbd5e7ce355d25bd4eb
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64641820"
---
# <a name="null-literals-and-type-inference-entity-sql"></a>Null değişmez değerler ve tür çıkarımı (varlık SQL)
Null değişmez değerler herhangi bir türü ile uyumlu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tür sistemi. Ancak, doğru bir şekilde çıkarılan bir null sabit değer türü için [!INCLUDE[esql](../../../../../../includes/esql-md.md)] üzerinde bir null sabit değer kullanıldığı bazı kısıtlamalar getirir.  
  
## <a name="typed-nulls"></a>Türü belirlenmiş null  
 Türü belirlenmiş null değerlere her yerde kullanılabilir. Türü bilinen için tür çıkarımı yazılı null değerler için gerekli değildir. Örneğin, aşağıdaki Int16 türü null oluşturabilirsiniz [!INCLUDE[esql](../../../../../../includes/esql-md.md)] oluşturun:  
  
 `(cast(null as Int16))`  
  
## <a name="free-floating-null-literals"></a>Takılı Null değişmez değerler  
 Takılı null değişmez değerler, aşağıdaki bağlamlarında kullanılabilir:  
  
- Tür dönüştürme veya kabul ifade bir bağımsız değişken. Türü belirtilmiş bir null ifadesi oluşturmak için önerilen yöntem budur.  
  
- Bağımsız değişken olarak bir yöntem veya işlev. Standart aşırı kuralları geçerlidir.  
  
- Tek bir aritmetik ifade gibi bağımsız değişken olarak +, -, veya /. Null değişmez değerler diğer bağımsız değişkenleri olamaz, aksi takdirde tür çıkarımı mümkün değildir.  
  
- Mantıksal bir ifadeyi bağımsız değişkenlerden biri olarak (AND, OR veya değil). Tüm bağımsız değişkenler'Boolean türünde bilinmektedir.  
  
- Bağımsız değişken boş veya NULL değil bir ifade.  
  
- Bir veya daha fazla bağımsız değişken gibi bir ifade. Tüm bağımsız değişkenler, dizeleri olmaları beklenir.  
  
- Bir veya daha fazla bir adlandırılmış Tür oluşturucu bağımsız değişken.  
  
- Bir veya daha fazla multıset oluşturucu bağımsız değişken. Multıset Oluşturucu en az bir bağımsız değişkeni null bir sabit değer olmayan bir ifade olmalıdır.  
  
- Bir veya daha fazla sonra veya başka bir CASE ifadesi ifadelerinde. CASE ifadesi ifadelerinde yoksa daha sonra en az biri null bir sabit değer dışında bir ifade olmalıdır.  
  
 Diğer senaryolarda takılı null değişmez değerler kullanılamaz. Örneğin, bunlar bir satır oluşturucusunda bağımsız değişken olarak kullanılamaz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL’e Genel Bakış](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
