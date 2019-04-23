---
ms.openlocfilehash: cf1a8169351e29c18d85303fb32d4394877448f4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59805315"
---
### <a name="log-file-name-created-by-the-objectcontextcreatedatabase-method-has-changed-to-match-sql-server-specifications"></a>SQL Server spesifikasyonlarına eşleştirilecek ObjectContext.CreateDatabase yöntemi tarafından oluşturulan günlük dosyası adı değiştirildi

|   |   |
|---|---|
|Ayrıntılar|Zaman <xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=name> yöntemi çağrıldığında ya da doğrudan ya da Code First SqlClient sağlayıcısı ve bağlantı dizesinde AttachDBFilename değeri ile kullanarak (dosya adı olduğu adını filename_log.ldf filename.ldf yerine adlandırılmış bir günlük dosyası oluşturur AttachDBFilename değeri tarafından belirtilen dosya). Bu değişiklik, SQL Server spesifikasyonlarına uygun olarak adlandırılan bir günlük dosyası sağlayarak hata ayıklamayı geliştirir.|
|Öneri|Günlük dosyası adı bir uygulama için önemli ise, uygulama standart _log.ldf dosya adı biçimi beklenir güncelleştirilmelidir.|
|Kapsam|Kenar|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=nameWithType></li></ul>|
