---
title: İşlev aşırı yükleme çözünürlüğü (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 9c648054-3808-4a69-9d3e-98e6a4f9c5ca
ms.openlocfilehash: d37cd9342d1fb3b60d5a2c05d373fb7e71f54b1f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189402"
---
# <a name="function-overload-resolution-entity-sql"></a>İşlev aşırı yükleme çözünürlüğü (Entity SQL)

Bu konu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] , işlevlerin nasıl çözümlendiğini açıklar.  
  
 İşlevlerin benzersiz imzaları olduğu sürece, birden fazla işlev aynı adla tanımlanabilir.  
  
 Bu durum söz konusu olduğunda, belirli bir ifade tarafından hangi işlevin başvurulduğunu belirleyen aşağıdaki kriterlerin uygulanması gerekir. Bu ölçütler sırayla uygulanır. Yalnızca tek bir işlev için geçerli olan ilk ölçüt çözümlenen işlevdir.  
  
1. **Parametre numarası**. İşlev, ifadede belirtilen sayıda parametreye sahip.  
  
2. **Tür üzerinde tam eşleşme**. İşlevin her bağımsız değişken türü parametre türüyle tam olarak eşleşir veya null değişmez değerdir.  
  
3. **Alt tür Ile Eşleştir**. İşlevin her bağımsız değişken türü tam olarak eşleşir veya parametre türünün bir alt türü veya bağımsız değişkeni null değişmez değerdir. Birkaç işlevin yalnızca gereken alt tür dönüştürmelerde farklı olması durumunda, en az sayıda alt tür Dönüştürmelere sahip işlev çözümlenmiş işlevdir.  
  
4. **Alt tür veya tür promosyonu eşleştirin**. İşlevin her bağımsız değişken türü tam olarak eşleşir, bir alt türüdür, veya parametre türüne yükseltilebilir veya bağımsız değişken null değişmez değerdir. Bu durumda, birkaç işlevin yalnızca alt tür dönüştürmeleri ve yükseltmeleri sayısında farklı olması durumunda, en az sayıda alt tür dönüştürmeleri ve promosyonları çözümlenen işlevdir.  
  
 Bu ölçütlerden hiçbiri seçili olmayan tek bir işlev ile sonuçlanmadığı takdirde, işlev çağırma ifadesi belirsizdir.  
  
 Tek bir işlev bu kurallar kullanılarak ayıklanabileceği halde, bağımsız değişkenler parametrelerle eşleşmeyebilir. Bu durumda bir hata ortaya çıkar.  
  
 Kullanıcı tanımlı işlevler için, bir satır içi sorgu işlevinin tanımı, Kullanıcı tanımlı işlev için daha iyi bir eşleşme olan imzaya sahip, model tanımlı bir işlev olduğunda bile öncelik kazanır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Başvurusu](entity-sql-reference.md)
- [Entity SQL’e Genel Bakış](entity-sql-overview.md)
- [İşlevler](functions-entity-sql.md)
