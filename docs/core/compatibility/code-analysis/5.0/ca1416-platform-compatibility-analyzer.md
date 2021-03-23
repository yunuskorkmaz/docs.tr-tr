---
title: 'Son değişiklik: CA1416: platform uyumluluğu'
description: Kod Analizi kuralı CA1416 'nin etkinleştirilmesi nedeniyle .NET 5 ' teki önemli değişiklik hakkında bilgi edinin.
ms.date: 09/29/2020
ms.openlocfilehash: b1d8c9115d5ad0bc97b6ba68cc058de195d01584
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104874361"
---
# <a name="warning-ca1416-platform-compatibility"></a>Uyarı CA1416: platform uyumluluğu

.Net Code Analyzer Rule [CA1416](/visualstudio/code-quality/ca1416) , varsayılan olarak .NET 5,0 ' den başlayarak etkindir. İşletim sistemini doğrulamaktan gelen çağrı sitelerinden platforma özel API 'lere çağrılar için bir derleme uyarısı oluşturur.

## <a name="change-description"></a>Açıklamayı Değiştir

.NET 5 ' den başlayarak .NET SDK [.net kaynak kodu Çözümleyicileri](../../../../fundamentals/code-analysis/overview.md)içerir. Bu kuralların bazıları varsayılan olarak [CA1416](/visualstudio/code-quality/ca1416)dahil olmak üzere etkindir. Projeniz bu kuralı ihlal eden ve uyarıları hata olarak işleyecek şekilde yapılandırılan kodu içeriyorsa, bu değişiklik yapınızı bozabilir. Rule CA1416, platform bağlamının doğrulanmadığı yerlerden platforma özel API 'Ler kullandığınızda size bildirir.

[CA1416](/visualstudio/code-quality/ca1416)kuralı, platform uyumluluğu Çözümleyicisi, .NET 5,0 ' de yeni olan diğer özelliklerle birlikte çalışmaktadır. .NET 5, <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> ve <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute> ' de desteklenmeyen platformları belirtmenize olanak sağlayan ve öğesini tanıtır.   Bu özniteliklerin yokluğunda, tüm platformlarda desteklenen bir API 'nin olduğu varsayılır. Bu öznitelikler, çekirdek .NET kitaplıklarında platforma özel API 'lere uygulandı.

Kullandıkları API 'Leri hedefleyen projelerde, kural [CA1416](/visualstudio/code-quality/ca1416) platform bağlamının doğrulanmadığı herhangi bir platforma özgü API çağrısını işaretler. Artık ve öznitelikleri ile donatılmış API 'lerin çoğu, <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute> <xref:System.PlatformNotSupportedException> Desteklenmeyen bir işletim sisteminde çağrıldığında özel durumlar oluşturur. Artık bu API 'Lerin platforma özel olarak işaretlendiğinden, kural [CA1416](/visualstudio/code-quality/ca1416) , <xref:System.PlatformNotSupportedException> çağrı sitelerinize işletim sistemi denetimleri ekleyerek çalışma zamanı özel durumlarını engellemenize yardımcı olur.

## <a name="examples"></a>Örnekler

- <xref:System.Console.Beep(System.Int32,System.Int32)?displayProperty=nameWithType>Yöntemi yalnızca Windows 'ta desteklenir ve ile tasarlanmıştır `[SupportedOSPlatform("windows")]` . Aşağıdaki kod, proje [hedefliyorsa](../../../../standard/frameworks.md) `net5.0` (ancak yoksa) derleme zamanında bir CA1416 uyarısı oluşturur `net5.0-windows` . Uyarı oluşmasını önlemek için gerçekleştirebileceğiniz eylemler için bkz. [Önerilen eylem](#recommended-action).

  ```csharp
  public void PlayCMajor()
  {
      Console.Beep(261, 1000);
  }
  ```

- <xref:System.Drawing.Image.FromFile(System.String)?displayProperty=nameWithType>Yöntemi tarayıcıda desteklenmez ve ile donatılmış `[UnsupportedOSPlatform("browser")]` . Aşağıdaki kod, proje tarayıcı platformunu destekliyorsa derleme zamanında bir CA1416 uyarısı oluşturur.

  ```csharp
  public void CreateImage()
  {
      Image newImage = Image.FromFile("SampImag.jpg");
  }
  ```

  > [!TIP]
  >
  > - Blazor WebAssembly projeleri ve Razor sınıf kitaplığı projeleri otomatik olarak tarayıcı desteği içerir.
  > - Tarayıcınızı projeniz için desteklenen bir platform olarak el ile eklemek için, proje dosyanıza aşağıdaki girişi ekleyin:
  >
  >  ```xml
  >  <ItemGroup>
  >    <SupportedPlatform Include="browser" />
  >  </ItemGroup>
  >  ```

## <a name="version-introduced"></a>Sunulan sürüm

5.0

## <a name="recommended-action"></a>Önerilen eylem

Platforma özgü API 'Lerin yalnızca kod uygun bir platformda çalışırken çağrıldığından emin olun. Geçerli işletim sistemini, sınıfındaki yöntemlerden birini kullanarak (örneğin, `Is<Platform>` <xref:System.OperatingSystem?displayProperty=nameWithType> <xref:System.OperatingSystem.IsWindows?displayProperty=nameWithType> platforma özgü bir API çağrılmadan önce) kontrol edebilirsiniz.

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

Bir kitaplık yazıyorsanız, API 'nizi platforma özel olarak işaretleyebilirsiniz. Bu durumda, gereksinimlerin denetim yükü çağıranlarınızın üzerine düşer. Belirli yöntemleri veya türleri ya da tüm derlemeyi işaretleyebilirsiniz.

```csharp
[SupportedOSPlatform("windows")]
public void PlayCMajor()
{
    Console.Beep(261, 1000);
}
```

Tüm çağrı sitelerinizi onarmak istemiyorsanız, uyarıyı bastırmak için aşağıdaki seçeneklerden birini belirleyebilirsiniz:

- Kural CA1416 ' ı bastırmak için, `#pragma` veya [**disableduyarılar**](../../../../csharp/language-reference/compiler-options/errors-warnings.md#disabledwarnings) derleyici bayrağını kullanarak ya da [kuralın önem derecesini](../../../../fundamentals/code-analysis/configuration-options.md#severity-level) `none` bir. editorconfig dosyasında olarak ayarlayarak yapabilirsiniz.

  ```csharp
  public void PlayCMajor()
  {
  #pragma warning disable CA1416
      Console.Beep(261, 1000);
  #pragma warning restore CA1416
  }
  ```

- Kod analizini tamamen devre dışı bırakmak için `EnableNETAnalyzers` , `false` proje dosyanızda olarak ayarlayın. Daha fazla bilgi için bkz. [Enablenetçözümleyiciler](../../../project-sdk/msbuild-props.md#enablenetanalyzers).

## <a name="affected-apis"></a>Etkilenen API’ler

Windows platformu için:

- Üzerinde listelenen tüm API 'Ler <https://github.com/dotnet/designs/blob/main/accepted/2020/windows-specific-apis/windows-specific-apis.md> .
- <xref:System.Security.Cryptography.DSAOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDsaOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.RSAOpenSsl?displayProperty=fullName>

Blazor WebAssembly platformu için:

- Üzerinde listelenen tüm API 'Ler <https://github.com/dotnet/runtime/issues/41087> .

<!--

### Affected APIs

- ``

### Category

- Code analysis
- Core .NET libraries

-->

## <a name="see-also"></a>Ayrıca bkz.

- [CA1416: Platform uyumluluğunu doğrula](/visualstudio/code-quality/ca1416)
- [.NET API Çözümleyicisi](../../../../standard/analyzers/api-analyzer.md)
