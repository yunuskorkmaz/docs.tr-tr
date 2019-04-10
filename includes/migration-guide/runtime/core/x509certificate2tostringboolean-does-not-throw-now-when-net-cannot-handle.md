---
ms.openlocfilehash: 0dfc87201b9b31cd9d936f2c965c7d0ca0140cab
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234317"
---
### <a name="x509certificate2tostringboolean-does-not-throw-now-when-net-cannot-handle-the-certificate"></a>Artık .NET sertifika olduğunda işleyemiyor X509Certificate2.ToString(Boolean) oluşturmaz

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.5.2 ve önceki sürümlerinde, bu yöntem, alanlarına <code>true</code> ayrıntılı parametresi için geçirilen ve yüklü olan ve .NET Framework tarafından desteklenen olmayan sertifikalar. Şimdi, yöntem başarılı ve sertifika erişilemez kısımlarını atlayarak geçerli bir dize döndürür.|
|Öneri|Bağlı herhangi bir kod <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType> döndürülen dizeyi bazı sertifika verilerini (örneğin, ortak anahtar, özel anahtarı ve Uzantılar) hariç tutabilir, API daha önce oluşturulan bazı durumlarda beklediğiniz şekilde güncelleştirilmesi.|
|Kapsam|Kenar|
|Sürüm|4.6|
|Tür|Çalışma zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType></li></ul>|
