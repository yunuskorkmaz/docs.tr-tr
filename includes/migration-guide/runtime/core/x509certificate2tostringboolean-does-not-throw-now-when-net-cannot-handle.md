---
ms.openlocfilehash: d48519443aeee05617538cf2cc12bea49ad3e16d
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858473"
---
### <a name="x509certificate2tostringboolean-does-not-throw-now-when-net-cannot-handle-the-certificate"></a>Artık .NET sertifika olduğunda işleyemiyor X509Certificate2.ToString(Boolean) oluşturmaz

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.5.2 ve önceki sürümlerinde, bu yöntem, alanlarına <code>true</code> ayrıntılı parametresi için geçirilen ve yüklü olan ve .NET Framework tarafından desteklenen olmayan sertifikalar. Şimdi, yöntem başarılı ve sertifika erişilemez kısımlarını atlayarak geçerli bir dize döndürür.|
|Öneri|Bağlı herhangi bir kod <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType> döndürülen dizeyi bazı sertifika verilerini (örneğin, ortak anahtar, özel anahtarı ve Uzantılar) hariç tutabilir, API daha önce oluşturulan bazı durumlarda beklediğiniz şekilde güncelleştirilmesi.|
|`Scope`|Kenar|
|Version|4.6|
|Type|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType></li></ul>|

