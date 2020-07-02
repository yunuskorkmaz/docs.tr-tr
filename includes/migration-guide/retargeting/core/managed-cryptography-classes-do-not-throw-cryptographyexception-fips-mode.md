---
ms.openlocfilehash: 0b62eff8d70873293aafa539f40bf032672df57a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616288"
---
### <a name="managed-cryptography-classes-do-not-throw-a-cryptographyexception-in-fips-mode"></a>Yönetilen şifreleme sınıfları FIPS modunda Cryptographyıexception oluşturmaz

#### <a name="details"></a>Ayrıntılar

.NET Framework 4.7.2 ve önceki sürümlerde, <xref:System.Security.Cryptography.SHA256Managed> <xref:System.Security.Cryptography.CryptographicException> sistem ŞIFRELEME kitaplıkları FIPS modunda yapılandırıldığında bir oluşturma gibi yönetilen şifreleme sağlayıcısı sınıfları. Bu özel durumlar, yönetilen sürümlerin FIPS (Federal bilgi Işleme standartları) 140-2 sertifikası ve FIPS kurallarına göre onaylanmak üzere değerlendirilmediği şifreleme algoritmalarını engellemek için oluşturulur.  Bazı geliştiricilerin geliştirme makineleri FIPS modunda olduğundan, bu özel durumlar genellikle yalnızca üretim sistemlerinde oluşturulur. .NET Framework 4,8 ve sonraki sürümleri hedefleyen uygulamalar otomatik olarak daha yeni ve gevşek ilkeye geçiş yapar, böylece bu, <xref:System.Security.Cryptography.CryptographicException> Varsayılan olarak böyle durumlarda varsayılan olarak oluşturulmaz. Bunun yerine, yönetilen şifreleme sınıfları şifreleme işlemlerini bir sistem şifreleme kitaplığına yönlendirir. Bu ilke değişikliği, geliştirici ortamları ve üretim ortamları arasındaki kafa karıştırıcı bir farkı etkili bir şekilde kaldırır ve yerel bileşenlerin ve yönetilen bileşenlerin aynı şifreleme ilkesi altında çalışmasını sağlar.

#### <a name="suggestion"></a>Öneri

Bu davranış istenmeyen bir davranışsa, <xref:System.Security.Cryptography.CryptographicException> uygulama yapılandırma dosyanızın bölümüne aşağıdaki [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) yapılandırma ayarını ekleyerek FIPS modunda bir, bir önceki davranışı geri yükleyebilirsiniz [\<runtime>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) .

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Security.Cryptography.UseLegacyFipsThrow=true" />
</runtime>
```

Uygulamanız .NET Framework 4.7.2 veya daha önceki bir sürümü hedefliyorsa, [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) [\<runtime>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) uygulama yapılandırma dosyanızın bölümüne aşağıdaki AppContextSwitchOverrides yapılandırma ayarını ekleyerek da bu değişikliği tercih edebilirsiniz:

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Security.Cryptography.UseLegacyFipsThrow=false" />
</runtime>
```

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | Edge        |
| Sürüm | 4,8         |
| Tür    | Yeniden Hedefleme |

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Security.Cryptography.AesManaged?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.MD5Cng?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.MD5CryptoServiceProvider?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RC2CryptoServiceProvider?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RijndaelManaged?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RIPEMD160Managed?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.SHA1Managed?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.SHA256Managed?displayProperty=nameWithType>
