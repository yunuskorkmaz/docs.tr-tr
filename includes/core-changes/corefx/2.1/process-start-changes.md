---
ms.openlocfilehash: 58cb3580c8701773452ae8338f036a94bbee80c5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449417"
---
### <a name="change-in-default-value-of-useshellexecute"></a>UseShellExecute'ın varsayılan değerindeki değişiklik

<xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType>.NET Core `false` üzerinde varsayılan değeri vardır. .NET Framework'de varsayılan `true`değeri .

#### <a name="change-description"></a>Açıklamayı değiştir

<xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>örneğin Paint'i başlatan gibi `Process.Start("mspaint.exe")` kodlarla doğrudan bir uygulama başlatmanızı sağlar. Ayrıca, '' olarak ayarlanmışsa, <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> dolaylı `true`olarak ilişkili bir uygulamayı başlatmanızı sağlar. .NET Framework'de, *.txt* dosyalarını `Process.Start("mytextfile.txt")` bu düzenleyiciyle ilişkilendirdiyseniz, not defteri gibi kodun başlatılması anlamına gelen varsayılan <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> değerdir. `true` .NET Framework'de dolaylı olarak bir uygulama başlatılmasını <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> `false`önlemek için, açıkça . .NET Core'da varsayılan <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> `false`değer. Bu, varsayılan olarak, ilişkili uygulamaların . `Process.Start`

Bu değişiklik performans nedenleriyle .NET Core'da kullanılmaya başlandı. Genellikle, <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> doğrudan bir uygulama başlatmak için kullanılır. Doğrudan bir uygulama başlatmanın Windows kabuğunu içermesi ve ilişkili performans maliyetine tabi olması gerekmez. Bu varsayılan durumu daha hızlı yapmak için ,NET Core varsayılan değerini <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute?displayProperty=nameWithType> `false`. İhtiyacınız olduğunda daha yavaş yolu tercih edebilirsiniz.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

2.1

> [!NOTE]
> .NET Core'un önceki `UseShellExecute` sürümlerinde, Windows için uygulanmadı.

#### <a name="recommended-action"></a>Önerilen eylem

Uygulamanız eski davranışa <xref:System.Diagnostics.Process.Start(System.Diagnostics.ProcessStartInfo)?displayProperty=nameWithType> dayanıyorsa, <xref:System.Diagnostics.ProcessStartInfo.UseShellExecute> `true` <xref:System.Diagnostics.ProcessStartInfo> nesneüzerinde ayarla'yı arayın.

#### <a name="category"></a>Kategori

CoreFx

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.ProcessStartInfo?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Diagnostics.Process.Start`
- `M:System.Diagnostics.ProcessStartInfo`

-->
