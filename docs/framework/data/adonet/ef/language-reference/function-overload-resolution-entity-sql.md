---
title: İşlev aşırı yükleme çözümü (varlık SQL)
ms.date: 03/30/2017
ms.assetid: 9c648054-3808-4a69-9d3e-98e6a4f9c5ca
ms.openlocfilehash: e7e80704da9657dccfbfea548df074a95327cdc1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59082049"
---
# <a name="function-overload-resolution-entity-sql"></a>İşlev aşırı yükleme çözümü (varlık SQL)
Bu konu açıklar nasıl [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işlevleri giderilmiştir.  
  
 Benzersiz imzaları işlevleri olduğu sürece, aynı ada sahip birden fazla işlev tanımlanabilir.  
  
 Bu durumda, hangi işlevi, belirtilen bir ifade tarafından başvurulan belirlemek için aşağıdaki ölçütleri uygulanması gerekir. Bu ölçütler sırayla uygulanır. Yalnızca tek bir işleve uygulayan bir ilk ölçütü çözümlenen bir işlevdir.  
  
1.  **Parametre numarası**. Aynı deyimde parametre sayısı belirtilmiş işlevi vardır.  
  
2.  **Tam eşleşme türü**. Her işlevin bağımsız değişken türü tam olarak parametre türüyle eşleşen veya null bir sabit değer olmalıdır.  
  
3.  **Alt eşleşme**. İşlev bağımsız değişken türlerinin tam olarak eşleşen veya parametre türü bir alt tür ya da bağımsız değişken null bir sabit değer olmalıdır. Çeşitli işlevler yalnızca farklı olay, alt tür dönüştürmeleri sayısı gerekli, en az işlev çözümlenen işlevi alt tür dönüştürmeleri sayısıdır.  
  
4.  **Alt tür veya tür promosyonu eşleşmeye**. İşlev bağımsız değişken türlerinin tam olarak eşleşir, bir alt tür veya parametre türüne yükseltilebilir veya bağımsız değişken null bir sabit değer olmalıdır. Yeniden çeşitli işlevler yalnızca alt tür dönüştürmeleri ve promosyonlar, en az işlev sayısı, farklı olay alt tür dönüştürmeleri ve promosyonlar sayısıdır çözümlenen işlevi.  
  
 İşlev çağrısı ifadesi, bu ölçütlerin hiçbiri seçili tek bir işlevde yol açarsa belirsiz.  
  
 Bu kuralları kullanarak tek bir işlev ayıklanabileceği olsa bile, bağımsız değişkenler parametrelerini hala eşleşmeyebilir. Bu durumda bir hata ortaya çıkar.  
  
 Daha iyi bir eşleşme için kullanıcı tanımlı işlev imzası ile model tanımlı bir işlev mevcut olduğunda kullanıcı tanımlı işlevler için bir satır içi sorgu işlev tanımı önceliklidir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Entity SQL’e Genel Bakış](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [İşlevler](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)
