---
title: "İşlev aşırı yükleme çözümü (varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9c648054-3808-4a69-9d3e-98e6a4f9c5ca
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: cafbdd1a06ce506516fa985e9af147f55b4ea3d4
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="function-overload-resolution-entity-sql"></a>İşlev aşırı yükleme çözümü (varlık SQL)
Bu konuda açıklanmaktadır nasıl [!INCLUDE[esql](../../../../../../includes/esql-md.md)] işlevleri giderilmiştir.  
  
 Benzersiz imzaları işlevleri olduğu sürece aynı ada sahip birden fazla işlev tanımlanabilir.  
  
 Bu durumda, hangi işlevi, belirtilen ifade tarafından başvurulan belirlemek için aşağıdaki ölçütleri uygulanmış olması gerekir. Bu ölçütler sırayla uygulanır. Yalnızca tek bir işleve uygulayan ilk ölçütü çözümlenen bir işlevdir.  
  
1.  **Numaralı parametre**. Aynı deyimde parametre sayısı belirtilmiş işlevi içeriyor.  
  
2.  **Tam eşleşme türündeki**. Her bağımsız değişken türü işlevinin tam olarak parametre türüyle eşleşen veya null sabit değer olmalıdır.  
  
3.  **Alt eşleşme**. Her bağımsız değişken türü işlevinin tam olarak eşleşen veya parametre türü bir alt türü ya da bağımsız değişkeni null sabit değer olmalıdır. Çeşitli işlevler yalnızca farklı gerektiğinde, alt türü dönüştürme sayısı gerekli, en az işlev çözümlenmiş işlevi alt türü dönüşümleri sayısıdır.  
  
4.  **Alt türü veya türü yükseltme eşleşme**. Her bağımsız değişken türü işlevinin tam olarak eşleşir, bir alt türü veya parametre türüne yükseltilebilir ya da bağımsız değişkeni null sabit değer olmalıdır. Tekrar sayısı alt tür dönüştürmeleri ve promosyonlar, en az işlev içinde yalnızca bazı işlevler farklı olay alt tür dönüştürmeleri ve promosyonlar sayısıdır çözümlenmiş işlevi.  
  
 Bu ölçütler hiçbiri seçilmesini tek bir işlevinde sağlamazsa, işlev çağırma ifadesi belirsiz.  
  
 Bu kurallar kullanarak tek bir işlev ayıklanabilir olsa bile, bağımsız değişkenler parametreleri hala eşleşmeyebilir. Bu durumda bir hata ortaya çıkar.  
  
 Bile, kullanıcı tanımlı işlev için daha iyi bir eşleşme imzayla modeli tanımlı bir işlev mevcut olduğunda kullanıcı tanımlı işlevler, satır içi bir sorgu işlev tanımı önceliklidir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Entity SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Entity SQL’e Genel Bakış](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [İşlevler](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)
