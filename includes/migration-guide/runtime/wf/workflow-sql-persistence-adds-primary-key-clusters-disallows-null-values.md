---
ms.openlocfilehash: cb9305f623044233082286863d2f2d2c7e9d665a
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497900"
---
### <a name="workflow-sql-persistence-adds-primary-key-clusters-and-disallows-null-values-in-some-columns"></a>İş akışı SQL kalıcılığı birincil anahtar kümeleri ekler ve bazı sütunlarda null değerlere izin vermez

#### <a name="details"></a>Ayrıntılar

.NET Framework 4,7 ' den başlayarak, SQL Workflow örnek deposu (SWU) için SqlWorkflowInstanceStoreSchema. SQL betiği tarafından oluşturulan tablolar kümelenmiş birincil anahtarları kullanır. Bu nedenle, kimlikler <code>null</code> değerleri desteklemez. SWSıS işlemi bu değişiklikten etkilenmez. SQL Server Işlemsel çoğaltmayı desteklemek için güncelleştirmeler yapılmıştır.

#### <a name="suggestion"></a>Öneri

Bu değişikliğe yönelik olarak, SqlWorkflowInstanceStoreSchemaUpgrade. sql dosyasının mevcut yüklemelere uygulanması gerekir. Yeni veritabanı yüklemeleri otomatik olarak değişikliğe sahip olur.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Edge|
|Sürüm|4,7|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

API analizi aracılığıyla algılanamaz.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
