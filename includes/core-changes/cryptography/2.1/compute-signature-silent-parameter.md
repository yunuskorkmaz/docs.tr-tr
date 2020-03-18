---
ms.openlocfilehash: 9583d868ee01117d7bd6e465e7d89a734489d1a8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449238"
---
### <a name="boolean-parameter-of-signedcmscomputesignature-is-respected"></a>İmzaCms.ComputeSignature boolean parametre saygı duyulur

.NET Core'da yöntemin `silent` Boolean <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> parametresi saygı duyulur. Bu parametre ' ye `true`ayarlanmışsa PIN istemi gösterilmez.

#### <a name="change-description"></a>Açıklamayı değiştir

.NET Framework'de `silent` yöntemin <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> parametresi yoksayılır ve sağlayıcı tarafından gerekirse her zaman pin istemi gösterilir. .NET Core'da `silent` parametreye saygı gösterilir ve `true`ayarlanmışsa, sağlayıcı tarafından gerekli olsa bile pin istemi hiçbir zaman gösterilmez.

CMS/PKCS #7 mesajları için destek .NET Core sürüm 2.1'de tanıtıldı.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

2.1

#### <a name="recommended-action"></a>Önerilen eylem

Gerekirse PIN isteminin görüntülediğinden emin olmak <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> için masaüstü uygulamaları Boolean `false`parametresini aramalı ve 'ye ayarlamalıdır. Ortaya çıkan davranış, sessiz bağlamın devre dışı kalıp olmadığına bakılmaksızın .NET Framework'dekiyle aynıdır.

### <a name="category"></a>Kategori

Şifreleme

### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)`

-->
