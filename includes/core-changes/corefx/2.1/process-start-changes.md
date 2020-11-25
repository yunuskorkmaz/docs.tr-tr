---
ms.openlocfilehash: 9544b65f31772d0f4cee918528a73171fec4de99
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032050"
---
### <a name="change-in-default-value-of-useshellexecute"></a>UseShellExecute varsayılan değerindeki değişiklik

<xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> , .NET Core üzerinde varsayılan bir değer içerir `false` . .NET Framework, varsayılan değeri ' dir `true` .

#### <a name="change-description"></a>Açıklamayı Değiştir

<xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> bir uygulamayı doğrudan başlatmanıza olanak tanır. Örneğin, Paint 'i Başlatan gibi kodla `Process.Start("mspaint.exe")` . Ayrıca, olarak ayarlandıysa ilişkili bir uygulamayı dolaylı olarak başlatmanıza olanak tanır <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> `true` . .NET Framework ' de, varsayılan değeri, <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> `true` `Process.Start("mytextfile.txt")` *. txt* dosyalarını bu düzenleyici ile ilişkilendirdiyseniz Not defteri 'ni başlatacağı anlamına gelir. .NET Framework bir uygulamanın dolaylı olarak başlatılmasını engellemek için, açıkça olarak ayarlamanız gerekir <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> `false` . .NET Core 'da, için varsayılan değer <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> `false` . Bu, varsayılan olarak ilişkili uygulamaların, çağırdığınızda başlatılmayacağı anlamına gelir `Process.Start` .

Bu değişiklik, performans nedenleriyle .NET Core 'da sunulmuştur. Genellikle, <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> bir uygulamayı doğrudan başlatmak için kullanılır. Bir uygulamayı doğrudan başlatmak, Windows kabuğunu dahil etmek ve ilişkili performans maliyetine tabi olmak zorunda değildir. Bu varsayılan örneği daha hızlı hale getirmek için, .NET Core varsayılan değerini <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> olarak değiştirir `false` . Gerekirse, daha yavaş yolu kabul edebilirsiniz.

#### <a name="version-introduced"></a>Sunulan sürüm

2.1

> [!NOTE]
> .NET Core 'un önceki sürümlerinde `UseShellExecute` Windows için uygulanmadı.

#### <a name="recommended-action"></a>Önerilen eylem

Uygulamanız eski davranışı kullanıyorsa, <xref:System.Diagnostics.Process.Start(System.Diagnostics.ProcessStartInfo)?displayProperty=nameWithType> <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute> nesne üzerinde olarak ayarla ' yı çağırın `true` <xref:System.Diagnostics.ProcessStartInfo> .

#### <a name="category"></a>Kategori

Core .NET kitaplıkları

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.ProcessStartInfo?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Diagnostics.Process.Start`
- `M:System.Diagnostics.ProcessStartInfo`

-->
