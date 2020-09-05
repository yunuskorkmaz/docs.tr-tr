---
ms.openlocfilehash: e77e37156de759856c8a6f2e0c009caf9e1fe826
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497446"
---
### <a name="log-file-name-created-by-the-objectcontextcreatedatabase-method-has-changed-to-match-sql-server-specifications"></a>ObjectContext. CreateDatabase yöntemi tarafından oluşturulan günlük dosyası adı SQL Server belirtimlerle eşleşecek şekilde değiştirildi

#### <a name="details"></a>Ayrıntılar

<xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=fullName>Yöntemi doğrudan Code First veya bağlantı dizesinde SqlClient sağlayıcısı ve AttachDBFilename değeri ile birlikte çağrıldığında, filename. ldf yerine filename_log. ldf adlı bir günlük dosyası oluşturur (dosya adı, AttachDBFilename değeri tarafından belirtilen dosyanın adıdır). Bu değişiklik, SQL Server spesifikasyonlarına uygun olarak adlandırılan bir günlük dosyası sağlayarak hata ayıklamayı geliştirir.

#### <a name="suggestion"></a>Öneri

Günlük dosyası adı bir uygulama için önemliyse, uygulamanın standart _log. ldf dosya adı biçimini beklediği için güncelleştirilmeleri gerekir.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Edge|
|Sürüm|4,5|
|Tür|Çalışma Zamanı

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Data.Objects.ObjectContext.CreateDatabase`

-->
