---
ms.openlocfilehash: 0dfc87201b9b31cd9d936f2c965c7d0ca0140cab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858473"
---
### <a name="x509certificate2tostringboolean-does-not-throw-now-when-net-cannot-handle-the-certificate"></a>X509Certificate2.ToString(Boolean) şimdi atmıyor .NET sertifikayı işleyemiyor

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.5.2 ve önceki sürümlerinde, <code>true</code> ayrıntılı parametre için geçirilen ve .NET Framework tarafından desteklenmeyen sertifikalar yüklüyse, bu yöntem atılır. Şimdi, yöntem başarılı olacak ve sertifikanın erişilemeyen bölümlerini atlayan geçerli bir dize döndürecek.|
|Öneri|Bağlı olarak herhangi <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType> bir kod, döndürülen dize, API'nin daha önce atmış olacağı bazı durumlarda bazı sertifika verilerini (ortak anahtar, özel anahtar ve uzantılar gibi) dışlayabilen bir şekilde güncelleştirilmelidir.|
|Kapsam|Edge|
|Sürüm|4.6|
|Tür|Çalışma Zamanı|
|Etkilenen API’ler|<ul><li><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType></li></ul>|
