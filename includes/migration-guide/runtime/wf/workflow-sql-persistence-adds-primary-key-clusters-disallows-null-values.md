---
ms.openlocfilehash: 566a3e0455b30e901b09be88b4256ffe67bdc2b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67802454"
---
### <a name="workflow-sql-persistence-adds-primary-key-clusters-and-disallows-null-values-in-some-columns"></a>İş akışı SQL kalıcılığı birincil anahtar kümeleri ekler ve bazı sütunlarda null değerleri izin vermez

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.7 ile başlayarak, SQLWorkflowInstanceStoreSchema.sql komut dosyası tarafından SQL İş Akışı Örnek Deposu (SWIS) için oluşturulan tablolar kümelenmiş birincil tuşları kullanır. Bu nedenle, kimlikler değerleri <code>null</code> desteklemez. SWIS'in çalışması bu değişiklikten etkilenmez. Güncelleştirmeler SQL Server Transactional Replication desteklemek için yapıldı.|
|Öneri|Sql dosyası SqlWorkflowInstanceStoreSchemaUpgrade.sql bu değişikliği deneyimlemek için varolan yüklemelere uygulanmalıdır. Yeni veritabanı yüklemeleri otomatik olarak değişiklik olacaktır.|
|Kapsam|Edge|
|Sürüm|4.7|
|Tür|Çalışma Zamanı|
