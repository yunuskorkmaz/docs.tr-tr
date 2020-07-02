---
ms.openlocfilehash: 809ca85b347fabc44573e2e0c5a43261d68590d3
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621395"
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
