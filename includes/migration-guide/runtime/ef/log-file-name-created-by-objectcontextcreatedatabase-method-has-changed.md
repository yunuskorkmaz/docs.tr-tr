---
ms.openlocfilehash: cf1a8169351e29c18d85303fb32d4394877448f4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235963"
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
