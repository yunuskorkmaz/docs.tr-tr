---
title: "Disk belleği (varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba4f334d-03e5-4a7b-9d42-628f4639b9a2
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6188587a8b588128092f5d9f02f6962159b928e4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="paging-entity-sql"></a>Disk belleği (varlık SQL)
Fiziksel disk belleği kullanılarak yapılabilir [atla](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) ve [sınırı](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) alt yan tümceleri içinde [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) yan tümcesi. Belirleyici biçimde fiziksel disk belleği gerçekleştirmek için atla ve sınırı kullanmanız gerekir. Yalnızca bir determinsitic olmayan şekilde sonuç satır sayısı kısıtlamak istiyorsanız, kullanması gereken [üst](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md). TOP ve SKIP/LIMIT karşılıklı olarak birbirini dışlar.  
  
## <a name="top-overview"></a>ÜST genel bakış  
 SELECT yan tümcesi, isteğe bağlı tüm/DISTINCT değiştiricisi izleyen bir isteğe bağlı TOP alt yan tümcesinin olabilir. TOP alt yan tümcesi, yalnızca ilk satır kümesini sorgu sonuç döndürülür belirtir. Daha fazla bilgi için bkz: [üst](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md).  
  
## <a name="skip-and-limit-overview"></a>ATLA ve sınırı genel bakış  
 ATLA ve sınırı ORDER BY yan tümcesi parçasıdır. SKIP ifadesi alt yan bir ORDER BY yan tümcesinde varsa, sonuçları sıralama belirtimine göre sıralanır ve sonuç kümesi hemen sonra SKIP ifadesi sonraki satırdan başlayan satırlara dahil edilir. Örneğin, Atla 5 ilk beş satırını atlar ve İleri altıncı satırdaki döndürür. İfade LIMIT alt yan ORDER BY yan tümcesinde varsa, sorgu sıralama belirtimine göre sıralanır ve sonuçta elde edilen satır sayısı sınırı ifadeyle kısıtlanmış olabilir. Örneğin, sınır 5 sonuç beş örneği veya satır kümesini kısıtlar. ATLA ve sınırı birlikte kullanılması gerekmez; yalnızca atlayın veya yalnızca ORDER BY yan tümcesi ile SINIRLAYABİLİRSİNİZ. Daha fazla bilgi için aşağıdaki konulara bakın:  
  
-   [ATLA](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)  
  
-   [SINIRI](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)  
  
-   [SIRALAMA ÖLÇÜTÜ](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Varlık SQL Başvurusu](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Varlık SQL genel bakış](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [Nasıl yapılır: sonuçları sorgu aracılığıyla sayfası](http://msdn.microsoft.com/en-us/ffc0f920-e7de-42e0-9b12-ef356421d030)
