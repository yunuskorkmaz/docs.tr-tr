---
ms.openlocfilehash: c008809606372c84b05a2facd1cac1293382aed4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234996"
---
### <a name="aescryptoserviceprovider-decryptor-provides-a-reusable-transform"></a>Yeniden kullanılabilir bir dönüşüm AesCryptoServiceProvider şifre çözücü sağlar

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6.2, hedefleyen uygulamaları ile başlayan <xref:System.Security.Cryptography.AesCryptoServiceProvider> şifre çözücü yeniden kullanılabilir bir dönüştürme sağlar. Çağrısı yapıldıktan sonra <xref:System.Security.Cryptography.CryptoAPITransform.TransformFinalBlock(System.Byte[],System.Int32,System.Int32)?displayProperty=name>, dönüştürme işlemi başlatılır ve yeniden kullanılabilir. .NET Framework'ün önceki sürümlerini hedefleyen uygulamalar için şifre çözücü çağırarak yeniden çalışılıyor <xref:System.Security.Cryptography.CryptoAPITransform.TransformBlock(System.Byte[],System.Int32,System.Int32,System.Byte[],System.Int32)?displayProperty=name> çağrısı yapıldıktan sonra <xref:System.Security.Cryptography.CryptoAPITransform.TransformFinalBlock(System.Byte[],System.Int32,System.Int32)?displayProperty=name> oluşturur bir <xref:System.Security.Cryptography.CryptographicException> ya da bozuk veriler üretir.|
|Öneri|Bu beklenen bir davranış olduğundan bu değişikliğin etkisini en az olmalıdır. Önceki davranışı bağlı uygulamalar için şu yapılandırma ayarı ekleyerek kullanarak dışında özelliğini <code>&lt;runtime&gt;</code> uygulamanın yapılandırma dosyası bölümünü:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.AesCryptoServiceProvider.DontCorrectlyResetDecryptor=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Ayrıca, .NET Framework'ün önceki bir sürümü hedeflemesini ancak bir sürümü .NET Framework 4.6.2 ile başlayarak .NET Framework'ün altında çalışan uygulamalar için aşağıdaki yapılandırma ayarı ekleyerek kabul et <code>&lt;runtime&gt;</code> bölümü Uygulamanın yapılandırma dosyası:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.AesCryptoServiceProvider.DontCorrectlyResetDecryptor=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Kapsam|İkincil|
|Sürüm|4.6.2|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.Security.Cryptography.AesCryptoServiceProvider.CreateDecryptor?displayProperty=nameWithType></li></ul>|
