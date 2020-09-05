---
ms.openlocfilehash: 4416a7c09f2d163961fe2fe3d6dfaa8bd5e66f93
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496707"
---
### <a name="change-in-behavior-in-data-definition-language-ddl-apis"></a>Veri tanımlama dili (DDL) API 'Lerinde davranış değişikliği

#### <a name="details"></a>Ayrıntılar

AttachDBFilename belirtildiğinde DDL API 'lerinin davranışı şu şekilde değiştirilmiştir:<ul><li>Bağlantı dizeleri bir Ilk katalog değeri belirtmemelidir. Daha önce hem AttachDBFilename hem de Initial Catalog gerekiyordu.</li><li>Hem AttachDBFilename hem de Initial Catalog belirtilmişse ve verilen MDF dosyası varsa, <xref:System.Data.Objects.ObjectContext.DatabaseExists%2A> yöntemi döndürür <code>true</code> . Daha önce döndürüldü <code>false</code> .</li><li>Hem AttachDBFilename hem de Initial Catalog belirtilmişse ve verilen MDF dosyası varsa, <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A> yöntemini çağırmak dosyaları siler.</li><li><xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A>Bağlantı dizesi mevcut olmayan BIR MDF ve mevcut olmayan bir Ilk katalog içeren bir AttachDBFilename değeri belirttiğinde çağrılırsa, yöntem bir <xref:System.InvalidOperationException> özel durum oluşturur. Daha önce bir <xref:System.Data.SqlClient.SqlException> özel durum oluşturdu.</li></ul>

#### <a name="suggestion"></a>Öneri

Bu değişiklikler, DDL API'larını kullanan araçlar ve uygulamalar oluşturmayı kolaylaştırır. Bu değişiklikler, aşağıdaki senaryolarda uygulama uyumluluğunu etkileyebilir:<ul><li>Kullanıcı, <code>DROP DATABASE</code> şunu döndürürse bir komutu doğrudan yürüten kodu yazar <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A> <xref:System.Data.Objects.ObjectContext.DatabaseExists%2A> <code>true</code> . Bu, veritabanı bağlı olmadığında, ancak MDF dosyası mevcut olduğunda mevcut kodu kırar.</li><li>Kullanıcı, <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A> <xref:System.Data.SqlClient.SqlException> <xref:System.InvalidOperationException> Başlangıç kataloğu ve MDF dosyası mevcut olmadığında, yönteminin bir yerine oluşturmasını bekleyen kodu yazar.</li></ul>

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |İkincil|
|Sürüm|4,5|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

API analizi aracılığıyla algılanamaz.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
