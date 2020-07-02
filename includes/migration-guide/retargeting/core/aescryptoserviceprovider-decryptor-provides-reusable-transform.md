---
ms.openlocfilehash: 36a9db601f7637185bf48dfcbe2233b4489fcdcf
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614655"
---
### <a name="aescryptoserviceprovider-decryptor-provides-a-reusable-transform"></a>AesCryptoServiceProvider şifre çözücü yeniden kullanılabilir bir dönüşüm sağlar

#### <a name="details"></a>Ayrıntılar

.NET Framework 4.6.2 hedefleyen uygulamalarla başlayarak, <xref:System.Security.Cryptography.AesCryptoServiceProvider> şifre çözücü yeniden kullanılabilir bir dönüşüm sağlar. Bir çağrısından sonra <xref:System.Security.Cryptography.CryptoAPITransform.TransformFinalBlock(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName> dönüşüm yeniden başlatılır ve yeniden kullanılabilir. .NET Framework önceki sürümlerini hedefleyen uygulamalar için, bir çağrısından sonra çağrı yaparak şifre çözücü yeniden kullanılmaya çalışılıyor <xref:System.Security.Cryptography.CryptoAPITransform.TransformBlock(System.Byte[],System.Int32,System.Int32,System.Byte[],System.Int32)?displayProperty=fullName> <xref:System.Security.Cryptography.CryptoAPITransform.TransformFinalBlock(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName> <xref:System.Security.Cryptography.CryptographicException> veya bozuk veriler oluşturur.

#### <a name="suggestion"></a>Öneri

Beklenen davranış olduğundan bu değişikliğin etkisi en az olmalıdır. Önceki davranışa bağımlı olan uygulamalar `<runtime>` , uygulamanın yapılandırma dosyasının bölümüne aşağıdaki yapılandırma ayarını ekleyerek onu kullanarak devre dışı bırakabilirsiniz:

```xml
<runtime>
<AppContextSwitchOverrides value="Switch.System.Security.Cryptography.AesCryptoServiceProvider.DontCorrectlyResetDecryptor=true"/>
</runtime>
```

Ayrıca, .NET Framework önceki bir sürümünü hedefleyen, ancak .NET Framework bir sürümü altında çalışan uygulamalar .NET Framework 4.6.2, `<runtime>` uygulamanın yapılandırma dosyasının bölümüne aşağıdaki yapılandırma ayarını ekleyerek bunu kabul edebilir:

```xml
<runtime>
<AppContextSwitchOverrides value="Switch.System.Security.Cryptography.AesCryptoServiceProvider.DontCorrectlyResetDecryptor=false"/>
</runtime>
```

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | İkincil       |
| Sürüm | 4.6.2       |
| Tür    | Yeniden Hedefleme |

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Security.Cryptography.AesCryptoServiceProvider.CreateDecryptor?displayProperty=nameWithType>
