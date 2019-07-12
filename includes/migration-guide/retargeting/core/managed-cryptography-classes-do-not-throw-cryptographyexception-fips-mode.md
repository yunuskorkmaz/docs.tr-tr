---
ms.openlocfilehash: 2b768047a8b08501a8de4666d240072318427f28
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67803546"
---
### <a name="managed-cryptography-classes-do-not-throw-a-cryptographyexception-in-fips-mode"></a>Yönetilen bir şifreleme sınıflarını FIPS modunda bir CryptographyException oluşturması beklenmiyor

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.7.2 ve önceki sürümlerinde şifreleme sağlayıcısı sınıfları gibi yönetilen <xref:System.Security.Cryptography.SHA256Managed> throw bir <xref:System.Security.Cryptography.CryptographicException> sistem şifreleme kitaplıkları FIPS modunda yapılandırılmış zaman. Yönetilen sürümleri onaylanması dikkate alınmıyordu şifreleme algoritmalarını engellemek için 140-2 sertifikası, de FIPS kurallara göre FIPS (Federal Bilgi işleme standartları) yapılmamıştır çünkü bu özel durumlar.  Bazı geliştiriciler, geliştirme makinelerinde FIPS modunda olduğundan, bu genellikle yalnızca üretim sistemlerine özel durumlar. Otomatik olarak .NET Framework 4.8 ve sonraki sürümlerini hedefleyen uygulamalar geçiş daha yeni ve esnek ilkeyi, böylece bir <xref:System.Security.Cryptography.CryptographicException> artık varsayılan olarak bu gibi durumlarda oluşturulur. Bunun yerine, yönetilen şifreleme sınıflarını şifreleme işlemleri için bir sistem şifreleme kitaplığı yönlendirin. Bu ilke değişikliğini etkili bir şekilde olası karmaşık birbirinden Geliştirici ortamlarını ve üretim ortamlarını kaldırır ve yerel bileşenlerin yapar ve yönetilen bileşenleri aynı şifreleme ilkesi altında çalışır.|
|Öneri|Bu davranışı istenmeyen ise ve önceki davranış geri yükleme bu nedenle, geri çevirebilirsiniz bir <xref:System.Security.Cryptography.CryptographicException> aşağıdakileri ekleyerek FIPS modunda oluşturulan [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) yapılandırma ayarı [ <runtime> ](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) , uygulama yapılandırma dosyasının:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.UseLegacyFipsThrow=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Uygulamanızı .NET Framework 4.7.2 hedefler ya da daha önce de bu değişiklik aşağıdaki ekleyerek kabul [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) yapılandırma ayarı [ <runtime> ](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) Uygulama yapılandırma dosyanızda bölümü:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.UseLegacyFipsThrow=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Kapsam|Kenar|
|Sürüm|4.8|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.Security.Cryptography.AesManaged?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.MD5Cng?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.MD5CryptoServiceProvider?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RC2CryptoServiceProvider?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RijndaelManaged?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RIPEMD160Managed?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.SHA1Managed?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.SHA256Managed?displayProperty=nameWithType></li></ul>|

