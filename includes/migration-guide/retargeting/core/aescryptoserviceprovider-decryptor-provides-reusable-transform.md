---
ms.openlocfilehash: c008809606372c84b05a2facd1cac1293382aed4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859273"
---
### <a name="aescryptoserviceprovider-decryptor-provides-a-reusable-transform"></a>AesCryptoServiceProvider şifre çözücü yeniden kullanılabilir bir dönüşüm sağlar

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6.2'yi hedefleyen uygulamalardan başlayarak şifre <xref:System.Security.Cryptography.AesCryptoServiceProvider> çözücü yeniden kullanılabilir bir dönüşüm sağlar. Bir çağrıdan <xref:System.Security.Cryptography.CryptoAPITransform.TransformFinalBlock(System.Byte[],System.Int32,System.Int32)?displayProperty=name>sonra, dönüştürme yeniden başharflenir ve yeniden kullanılabilir. .NET Framework'ün önceki sürümlerini hedefleyen uygulamalar için, <xref:System.Security.Cryptography.CryptoAPITransform.TransformBlock(System.Byte[],System.Int32,System.Int32,System.Byte[],System.Int32)?displayProperty=name> <xref:System.Security.Cryptography.CryptoAPITransform.TransformFinalBlock(System.Byte[],System.Int32,System.Int32)?displayProperty=name> bir aramadan sonra bir aramadan <xref:System.Security.Cryptography.CryptographicException> sonra arayarak şifre çözücüyu yeniden kullanmaya çalışmak veya bozuk veri üretir.|
|Öneri|Bu beklenen davranış olduğundan, bu değişikliğin etkisi en az olmalıdır. Önceki davranışa bağlı olan uygulamalar, uygulamanın yapılandırma <code>&lt;runtime&gt;</code> dosyasının bölümüne aşağıdaki yapılandırma ayarını ekleyerek bu uygulamayı kullanarak bu uygulamayı devre dışı layabilir:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.AesCryptoServiceProvider.DontCorrectlyResetDecryptor=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Buna ek olarak, .NET Framework'ün önceki bir sürümünü hedefleyen ancak .NET Framework 4.6.2 ile başlayan bir sürümü altında çalışan uygulamalar, <code>&lt;runtime&gt;</code> uygulamanın yapılandırma dosyasının bölümüne aşağıdaki yapılandırma ayarını ekleyerek bu çerçeveyi seçebilir:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.AesCryptoServiceProvider.DontCorrectlyResetDecryptor=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Kapsam|İkincil|
|Sürüm|4.6.2|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.Security.Cryptography.AesCryptoServiceProvider.CreateDecryptor?displayProperty=nameWithType></li></ul>|
