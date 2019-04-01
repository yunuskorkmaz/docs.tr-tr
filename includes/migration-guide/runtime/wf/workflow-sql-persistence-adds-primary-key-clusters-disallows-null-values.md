---
ms.openlocfilehash: 9e98d3bca645cf82bf4fe99160dd096b0e274ef7
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760445"
---
### <a name="workflow-sql-persistence-adds-primary-key-clusters-and-disallows-null-values-in-some-columns"></a>İş akışı SQL kalıcılığını birincil anahtar kümeleri ve bazı sütunları null değerleri izin vermiyor ekler.

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.7 ile başlayarak, SQL iş akışı örneği Store (SWIS) için SqlWorkflowInstanceStoreSchema.sql betiği tarafından oluşturulan tablolarda kümelenmiş birincil anahtarları kullanın. Bu nedenle, kimlikleri desteklemez <code>null</code> değerleri. SWIS işlemi, bu değişiklikten etkilenmez. SQL Server işlem çoğaltmayı desteklemek için güncelleştirmeleri yapıldı.|
|Öneri|Bu değişiklik deneyimi için SQL dosyası SqlWorkflowInstanceStoreSchemaUpgrade.sql var olan yüklemeler için uygulanması gerekir. Yeni veritabanı yüklemelerini değişikliği otomatik olarak sahip olur.|
|Kapsam|Kenar|
|Sürüm|4.7|
|Tür|Çalışma zamanı|

