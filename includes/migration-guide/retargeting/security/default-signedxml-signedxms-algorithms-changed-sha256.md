---
ms.openlocfilehash: e2ae329d027d605e6331afe422e550990fab1042
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614814"
---
### <a name="default-signedxml-and-signedxms-algorithms-changed-to-sha256"></a>Varsayılan SignedXML ve SignedXMS algoritmaları SHA256 olarak değiştirildi

#### <a name="details"></a>Ayrıntılar

.NET Framework 4,7 ve önceki sürümlerde, SignedXML ve SignedCMS varsayılan olarak bazı işlemler için SHA1 ' ya yöneliktir. .NET Framework 4.7.1 başlayarak, bu işlemler için SHA256 varsayılan olarak etkinleştirilir. Bu değişiklik gereklidir çünkü SHA1 artık güvenli olarak kabul edilmez.

#### <a name="suggestion"></a>Öneri

Varsayılan olarak SHA1 (güvensiz) veya SHA256 kullanılıp kullanılmayacağını denetlemek için iki yeni bağlam anahtarı değeri vardır:

- Switch.System.Security.Cryptography.Xml. Useınsecurehashalgoritmalarını
- Switch.SysTem. Security. Cryptography. Pkcs. Useınsecurehashalgoritmalarını .NET Framework 4.7.1 ve sonraki sürümlerini hedefleyen uygulamalar Için, SHA256 kullanımı istenmeyen bir değer değilse, uygulama yapılandırma dosyanızın [çalışma zamanı](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) bölümüne aşağıdaki yapılandırma anahtarını ekleyerek varsayılan değeri SHA1 olarak geri yükleyebilirsiniz:

```xml
<AppContextSwitchOverrides value="Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms=true;Switch.System.Security.Cryptography.Pkcs.UseInsecureHashAlgorithms=true" />
```

.NET Framework 4,7 ve önceki sürümlerini hedefleyen uygulamalar için, uygulama yapılandırma dosyanızın [çalışma zamanı](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) bölümüne aşağıdaki yapılandırma anahtarını ekleyerek bu değişikliği tercih edebilirsiniz:

```xml
<AppContextSwitchOverrides value="Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms=false;Switch.System.Security.Cryptography.Pkcs.UseInsecureHashAlgorithms=false" />
```

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | İkincil       |
| Sürüm | 4.7.1       |
| Tür    | Yeniden Hedefleme |

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Security.Cryptography.Pkcs.CmsSigner?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.Xml.SignedXml?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.Xml.Reference?displayProperty=nameWithType>
