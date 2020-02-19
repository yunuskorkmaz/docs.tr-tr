---
ms.openlocfilehash: 9583d868ee01117d7bd6e465e7d89a734489d1a8
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449238"
---
### <a name="boolean-parameter-of-signedcmscomputesignature-is-respected"></a>SignedCms. ComputeSignature Boolean parametresi dikkate alındı

.NET Core 'da <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> yönteminin Boole `silent` parametresi kullanılır. Bu parametre `true`olarak ayarlandıysa bir PIN istemi gösterilmez.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Framework, <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> yönteminin `silent` parametresi yok sayılır ve sağlayıcı tarafından gerekliyse bir PIN istemi her zaman gösterilir. .NET Core 'da `silent` parametresi dikkate alınsa da, `true`olarak ayarlanırsa, sağlayıcı için gerekli olsa bile bir PIN istemi gösterilmez.

CMS/PKCS #7 iletileri için destek, sürüm 2,1 ' de .NET Core ' a eklenmiştir.

#### <a name="version-introduced"></a>Sunulan sürüm

2.1

#### <a name="recommended-action"></a>Önerilen eylem

Gerektiğinde bir PIN isteminin göründüğünden emin olmak için, masaüstü uygulamaları <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> çağırmalıdır ve Boole parametresini `false`olarak ayarlar. Elde edilen davranış, sessiz bağlamın orada devre dışı bırakılıp bırakılmadığına bakılmaksızın .NET Framework.

### <a name="category"></a>Kategori

Şifreleme

### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)`

-->
