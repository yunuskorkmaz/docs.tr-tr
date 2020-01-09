---
ms.openlocfilehash: 7c0930f6606aa96d2863dc740aef8e9cab724b37
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344857"
---
### <a name="change-in-default-value-of-useshellexecute"></a>UseShellExecute varsayılan değerindeki değişiklik

<xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> `false` varsayılan değeri .NET Core üzerinde vardır. .NET Framework, varsayılan değeri `true`' dir.

#### <a name="change-description"></a>Açıklamayı Değiştir

<xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>, bir uygulamayı doğrudan başlatmanıza olanak tanır. Örneğin, Paint 'i Başlatan `Process.Start("mspaint.exe")` gibi kodla. Ayrıca, <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> `true`olarak ayarlandıysa ilişkili uygulamayı dolaylı olarak başlatmanıza olanak tanır. .NET Framework, <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> için varsayılan değer `true`, yani *. txt* dosyalarını bu düzenleyici ile ilişkilendirdiyseniz, `Process.Start("mytextfile.txt")` gibi kodun Not defteri 'ni başlatacağı anlamına gelir. .NET Framework bir uygulamanın dolaylı olarak başlatılmasını engellemek için <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> açıkça `false`olarak ayarlamanız gerekir. .NET Core 'da, <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> için varsayılan değer `false`. Bu, varsayılan olarak, `Process.Start`çağırdığınızda ilişkili uygulamaların başlatılmayacağı anlamına gelir.

Bu değişiklik, performans nedenleriyle .NET Core 'da sunulmuştur. Genellikle, <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> doğrudan bir uygulamayı başlatmak için kullanılır. Bir uygulamayı doğrudan başlatmak, Windows kabuğunu dahil etmek ve ilişkili performans maliyetine tabi olmak zorunda değildir. Bu varsayılan örneği daha hızlı hale getirmek için, .NET Core <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> varsayılan değerini `false`olarak değiştirir. Gerekirse, daha yavaş yolu kabul edebilirsiniz.

#### <a name="version-introduced"></a>Sunulan sürüm

2.1

> [!NOTE]
> .NET Core 'un önceki sürümlerinde `UseShellExecute` Windows için uygulanmadı.

#### <a name="recommended-action"></a>Önerilen eylem

Uygulamanız eski davranışı kullanıyorsa, <xref:System.Diagnostics.ProcessStartInfo> nesnesi üzerinde `true` olarak ayarlanan <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute> <xref:System.Diagnostics.Process.Start(System.Diagnostics.ProcessStartInfo)?displayProperty=nameWithType> çağırın.

#### <a name="category"></a>Kategori

CoreFx

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.ProcessStartInfo?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Diagnostics.Process.Start`
- `M:System.Diagnostics.ProcessStartInfo`

-->
