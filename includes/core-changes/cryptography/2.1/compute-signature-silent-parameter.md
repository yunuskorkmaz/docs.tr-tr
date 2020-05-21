---
ms.openlocfilehash: b861dbaa02c97a03c015fdf4e63d25c40c90ea0a
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721553"
---
### <a name="boolean-parameter-of-signedcmscomputesignature-is-respected"></a>SignedCms. ComputeSignature Boolean parametresi dikkate alındı

.NET Core 'da `silent` yöntemin Boolean parametresi <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> dikkate alındı. Bu parametre olarak ayarlandıysa, bir PIN istemi gösterilmez `true` .

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Framework, `silent` <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> yönteminin parametresi yok sayılır ve sağlayıcı tarafından GEREKLIYSE bir PIN istemi her zaman gösterilir. .NET Core 'da `silent` parametre dikkate alınsa da, olarak ayarlandıysa `true` , sağlayıcı için gerekli olsa bıle bir PIN istemi hiçbir şekilde gösterilmez.

CMS/PKCS #7 iletileri için destek, sürüm 2,1 ' de .NET Core ' a eklenmiştir.

#### <a name="version-introduced"></a>Sunulan sürüm

2.1

#### <a name="recommended-action"></a>Önerilen eylem

Gerekirse, bir PIN isteminin göründüğünden emin olmak için, masaüstü uygulamaları, <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> Boole parametresini çağırmalıdır ve olarak ayarlanmalıdır `false` . Elde edilen davranış, sessiz bağlamın orada devre dışı bırakılıp bırakılmadığına bakılmaksızın .NET Framework.

#### <a name="category"></a>Kategori

Şifreleme

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)`

-->
