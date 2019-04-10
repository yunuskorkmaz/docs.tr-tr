---
ms.openlocfilehash: 1f06a185939c40274adad1ceac6990719069167a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235897"
---
### <a name="change-in-behavior-in-data-definition-language-ddl-apis"></a>Veri tanımlama dili (DDL) API'ler de davranışını değiştir

|   |   |
|---|---|
|Ayrıntılar|AttachDBFilename belirtildiğinde DDL API'lerinin davranışı şu şekilde değişmiştir:<ul><li>Bağlantı dizeleri bir ilk katalog değerinin belirtmemeniz gerekir. Daha önce AttachDBFilename hem Initial Catalog gerekiyordu.</li><li>AttachDBFilename hem Initial Catalog belirtilir ve verilen bir MDF dosyası varsa, <xref:System.Data.Objects.ObjectContext.DatabaseExists%2A> yöntemi döndürür <code>true</code>. Daha önce döndürülen <code>false</code>.</li><li>AttachDBFilename hem Initial Catalog belirtilir ve verilen bir MDF dosyası varsa, çağrıyı yapan <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A> yöntemi dosyaları siler.</li><li>Varsa <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A> bağlantı dizesi varolmayan bir MDF ile AttachDBFilename değeri belirtir ve bir başlangıç mevcut olmayan Kataloğu çağırılıyorsa yöntem tamamlandığında aranan bir <xref:System.InvalidOperationException> özel durum. Daha önce oluşturuyordu bir <xref:System.Data.SqlClient.SqlException> özel durum.</li></ul>|
|Öneri|Bu değişiklikler, DDL API'larını kullanan araçlar ve uygulamalar oluşturmayı kolaylaştırır. Bu değişiklikler, aşağıdaki senaryolarda uygulama uyumluluğunu etkileyebilir:<ul><li>Kullanıcı yürüten bir kod yazar bir <code>DROP DATABASE</code> komutu çağırmak yerine doğrudan <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A> varsa <xref:System.Data.Objects.ObjectContext.DatabaseExists%2A> döndürür <code>true</code>. Bu, veritabanı bağlı olmadığında, ancak MDF dosyası mevcut olduğunda mevcut kodu kırar.</li><li>Kullanıcı kod yazar <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A> yönteminin bir <xref:System.Data.SqlClient.SqlException> yerine <xref:System.InvalidOperationException> Initial Catalog ve MDF dosyası mevcut olduğunda.</li></ul>|
|Kapsam|İkincil|
|Sürüm|4,5|
|Tür|Çalışma zamanı|
