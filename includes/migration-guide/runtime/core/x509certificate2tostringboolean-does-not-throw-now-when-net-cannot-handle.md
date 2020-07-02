---
ms.openlocfilehash: 51208762cea2a5688c5d43e5d444d4e014e5f0b4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621429"
---
### <a name="x509certificate2tostringboolean-does-not-throw-now-when-net-cannot-handle-the-certificate"></a>.NET sertifikayı işleyemezse X509Certificate2. ToString (Boolean) şimdi oluşturmaz

#### <a name="details"></a>Ayrıntılar

.NET Framework 4.5.2 ve önceki sürümlerde, bu yöntem <code>true</code> verbose parametresi için başarılı olduysa ve .NET Framework tarafından desteklenmeyen sertifikalar yüklüyse, bu yöntem oluşturur. Şimdi Yöntem başarılı olur ve sertifikanın erişilemeyen bölümlerini atlayacak geçerli bir dize döndürür.

#### <a name="suggestion"></a>Öneri

<xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType>Döndürülen dizenin, API 'nin daha önce oluşturulduğu bazı durumlarda bazı sertifika verilerini (ortak anahtar, özel anahtar ve uzantılar gibi) Dışlamayacağını beklemek için güncelleştirilmeleri gerekir.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Edge|
|Sürüm|4.6|
|Tür|Çalışma Zamanı

#### <a name="affected-apis"></a>Etkilenen API’ler

-<xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType></li></ul>|
