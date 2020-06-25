---
ms.openlocfilehash: d21b2e092d460fdfc367d0f490228ed44ad5c6cc
ms.sourcegitcommit: 63bb83322814f5e5e5c5b69939b14a3139a6ca7e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85365667"
---
### <a name="built-in-support-for-winrt-is-removed-from-net"></a>WinRT için yerleşik destek .NET 'ten kaldırılmıştır

.NET 'te [Windows çalışma zamanı (WinRT)](/uwp/winrt-cref/winrt-type-system) API 'leri tüketimi için yerleşik destek kaldırılmıştır.

#### <a name="version-introduced"></a>Sunulan sürüm

5,0 Preview 6

#### <a name="change-description"></a>Açıklamayı Değiştir

Daha önce CoreCLR, etkin ve WinRT türlerini tüketen [Windows meta verileri (WinMD) dosyalarını](/uwp/winrt-cref/winmd-files) tüketebilir. .NET 5,0 ' den başlayarak CoreCLR artık WinMD dosyalarını doğrudan tüketmez.

Desteklenmeyen bir derlemeye başvuru yapmaya çalışırsanız, bir ile karşılaşırsınız <xref:System.IO.FileNotFoundException> . Bir WinRT sınıfını etkinleştirirseniz bir ile karşılaşırsınız <xref:System.PlatformNotSupportedException> .

Bu son değişiklik aşağıdaki nedenlerden dolayı yapılmıştır:

- Bu nedenle, WinRT .NET çalışma zamanından ayrı olarak geliştirilebilir ve artırılabilir.
- İOS ve Android gibi diğer işletim sistemleri için sunulan birlikte çalışma sistemlerine sahip simetri için.
- C# özellikleri, ara dil (IL) bağlama ve zaman içinde (AOT) derleme gibi diğer .NET özelliklerinden yararlanmak için.
- .NET çalışma zamanı kod temelinin basitleşmesini sağlar.

#### <a name="recommended-action"></a>Önerilen eylem

- [Microsoft. Windows. SDK. Contracts paketine](https://www.nuget.org/packages/Microsoft.Windows.SDK.Contracts) başvuruları kaldırın ve [Microsoft.Windows.SDK.net paketine](https://www.nuget.org/packages/microsoft.windows.sdk.net)yönelik başvurularla değiştirin.

- .NET 5,0 ve sonraki sürümlerde WinRT API 'Leri ve türlerini oluşturmak veya özelleştirmek için [C#/wınrt](/windows/uwp/csharp-winrt/) araç zincirini kullanın.

#### <a name="category"></a>Kategori

Interop

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.IO.WindowsRuntimeStorageExtensions?displayProperty=fullName>
- <xref:System.IO.WindowsRuntimeStreamExtensions?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.WindowsRuntime?displayProperty=fullName>
- <xref:System.WindowsRuntimeSystemExtensions?displayProperty=fullName>
- <xref:Windows.Foundation.Point?displayProperty=fullName>
- <xref:Windows.Foundation.Size?displayProperty=fullName>
- <xref:Windows.UI.Color?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.IO.WindowsRuntimeStorageExtensions`
- `T: System.IO.WindowsRuntimeStreamExtensions`
- `N:System.Runtime.InteropServices.WindowsRuntime`
- `T:System.WindowsRuntimeSystemExtensions`
- `T:Windows.Foundation.Point`
- `T:Windows.Foundation.Size`
- `T:Windows.UI.Color`

-->
