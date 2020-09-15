---
ms.openlocfilehash: e3c9f23ca73ed9b85d09680ec15251ebe02c7f8e
ms.sourcegitcommit: a69d548f90a03e105ee6701236c38390ecd9ccd1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2020
ms.locfileid: "90065214"
---
### <a name="ca1416-platform-compatibility"></a>CA1416: platform uyumluluğu

.Net Code Analyzer Rule CA1416, varsayılan olarak .NET 5,0 ' den başlayarak etkindir. İşletim sistemini doğrulamaktan gelen çağrı sitelerinden platforma özel API 'lere çağrılar için bir derleme uyarısı oluşturur.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET SDK, .NET 5,0 'den başlayarak [.net kaynak kodu Çözümleyicileri](../../../../docs/fundamentals/productivity/code-analysis.md)içerir. Bu kuralların bazıları varsayılan olarak CA1416 dahil olmak üzere etkindir. Projeniz bu kuralı ihlal eden ve uyarıları hata olarak işleyecek şekilde yapılandırılan kodu içeriyorsa, bu değişiklik yapınızı bozabilir. Rule CA1416, platform bağlamının doğrulanmadığı yerlerden platforma özel API 'Ler kullandığınızda size bildirir.

CA1416 kuralı, platform uyumluluğu Çözümleyicisi, .NET 5,0 ' de yeni olan diğer özelliklerle birlikte çalışmaktadır. .NET 5,0 `SupportedOSPlatformAttribute` `UnsupportedOSPlatformAttribute` <xref:System.Runtime.Versioning.MinimumOSPlatformAttribute> <xref:System.Runtime.Versioning.RemovedInOSPlatformAttribute> , bir API *'nin* üzerinde veya desteklenmeyen platformları belirtmenize olanak tanıyan ve öznitelikleri (önceki bir önizleme sürümünde ve olarak adlandırılır). *isn't* Bu özniteliklerin yokluğunda, tüm platformlarda desteklenen bir API 'nin olduğu varsayılır. Bu öznitelikler, çekirdek .NET kitaplıklarında platforma özel API 'lere uygulandı.

Kullandıkları API 'Leri hedefleyen projelerde, kural CA1416 platform bağlamının doğrulanmadığı herhangi bir platforma özgü API çağrısını işaretler. Artık ve öznitelikleri ile donatılmış API 'lerin çoğu, `SupportedOSPlatformAttribute` `UnsupportedOSPlatformAttribute` <xref:System.PlatformNotSupportedException> Desteklenmeyen bir işletim sisteminde çağrıldığında özel durumlar oluşturur. Artık bu API 'Lerin platforma özel olarak işaretlendiğinden, kural CA1416, <xref:System.PlatformNotSupportedException> çağrı sitelerinize işletim sistemi denetimleri ekleyerek çalışma zamanı özel durumlarını engellemenize yardımcı olur.

#### <a name="examples"></a>Örnekler

- <xref:System.Console.Beep(System.Int32,System.Int32)?displayProperty=nameWithType>Yöntemi yalnızca Windows 'ta desteklenir (ile tasarlanmıştır `[SupportedOSPlatform("windows")]` ). Aşağıdaki kod, proje [hedefliyorsa](../../../../docs/standard/frameworks.md) `net5.0` (ancak yoksa) derleme zamanında bir CA1416 uyarısı oluşturur `net5.0-windows` . Uyarı oluşmasını önlemek için gerçekleştirebileceğiniz eylemler için bkz. [Önerilen eylem](#recommended-action).

  ```csharp
  public void PlayCMajor()
  {
      Console.Beep(261, 1000);
  }
  ```

- <xref:System.Drawing.Image.FromFile(System.String)?displayProperty=nameWithType>Yöntem tarayıcıda desteklenmez (ile donatılmış `[UnsupportedOSPlatform("browser")]` ). Aşağıdaki kod, proje dosyasında Blazor WebAssembly SDK ( `<Project Sdk="Microsoft.NET.Sdk.BlazorWebAssembly">` ) veya `browser` desteklenen platform () olarak içeriyorsa derleme ZAMANıNDA bir CA1416 uyarısı oluşturur `<SupportedPlatform Include="browser" />` .

  ```csharp
  public void CreateImage()
  {
      Image newImage = Image.FromFile("SampImag.jpg");
  }
  ```

#### <a name="version-introduced"></a>Sunulan sürüm

5,0 RC1

#### <a name="recommended-action"></a>Önerilen eylem

Platforma özgü API 'Lerin yalnızca kod uygun bir platformda çalışırken çağrıldığından emin olun. Geçerli işletim sistemini, sınıfındaki yöntemlerden birini kullanarak (örneğin, `Is<Platform>` <xref:System.OperatingSystem?displayProperty=nameWithType> `System.OperatingSystem.IsWindows()` platforma özgü bir API çağrılmadan önce) kontrol edebilirsiniz.

`Is<Platform>`Bir deyimin koşulunda yöntemlerden birini kullanabilirsiniz `if` :

```csharp
public void PlayCMajor()
{
    if (OperatingSystem.IsWindows())
    {
        Console.Beep(261, 1000);
    }
}
```

Ya da çalışma zamanında ek bir deyimin ek yükünü istemiyorsanız `if` , şunu çağırın <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType> :

```csharp
public void PlayCMajor()
{
    Debug.Assert(OperatingSystem.IsWindows());
    Console.Beep(261, 1000);
}
```

Ayrıca, API 'nizi platforma özel olarak işaretleyebilirsiniz. Bu durumda, gereksinimleri denetleme yükü çağıranlarınızın üzerine düşer. Belirli yöntemleri veya türleri ya da tüm derlemeyi işaretleyebilirsiniz.

```csharp
[SupportedOSPlatform("windows")]
public void PlayCMajor()
{
    Console.Beep(261, 1000);
}
```

Tüm çağrı sitelerinizi onarmak istemiyorsanız, uyarıyı bastırmak için aşağıdaki seçeneklerden birini belirleyebilirsiniz:

- Rule CA1416 'ı bastırmak için ya da `#pragma` [-nowarn](../../../../docs/csharp/language-reference/compiler-options/nowarn-compiler-option.md) derleyici bayrağını kullanarak ya da [kuralın önem derecesini](../../../../docs/fundamentals/productivity/configure-code-analysis-rules.md#suppress-violations) `none` bir. editorconfig dosyasında olarak ayarlayarak yapabilirsiniz.

  ```csharp
  public void PlayCMajor()
  {
  #pragma warning disable CA1416
      Console.Beep(261, 1000);
  #pragma warning restore CA1416
  }
  ```

- Kod analizini tamamen devre dışı bırakmak için `EnableNETAnalyzers` , `false` proje dosyanızda olarak ayarlayın. Daha fazla bilgi için bkz. [Enablenetçözümleyiciler](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers).

#### <a name="category"></a>Kategori

- Kod analizi
- Core .NET kitaplıkları

#### <a name="affected-apis"></a>Etkilenen API’ler

Windows platformu için:

- Üzerinde listelenen tüm API 'Ler <https://github.com/dotnet/designs/blob/master/accepted/2020/windows-specific-apis/windows-specific-apis.md> .
- <xref:System.Security.Cryptography.DSAOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDsaOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.RSAOpenSsl?displayProperty=fullName>

Blazor WebAssembly platformu için:

- Üzerinde listelenen tüm API 'Ler <https://github.com/dotnet/runtime/issues/41087> .

<!--

#### Affected APIs

- ``

-->

#### <a name="see-also"></a>Ayrıca bkz.

- [.NET API Çözümleyicisi](../../../../docs/standard/analyzers/api-analyzer.md)
