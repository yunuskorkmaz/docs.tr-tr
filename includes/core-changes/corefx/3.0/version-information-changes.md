---
ms.openlocfilehash: 5612ebce67946e22aaeeba861115ce4f8967e1f5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75344442"
---
### <a name="apis-that-report-version-now-report-product-and-not-file-version"></a>Rapor sürümünü rapor eden API'ler artık ürünü rapor eder, dosya sürümünü bildirmez

.NET Core'da sürümleri döndüren API'lerin çoğu artık dosya sürümü yerine ürün sürümünü döndürüyor.

#### <a name="change-description"></a>Açıklamayı değiştir

.NET Core 2.2 ve önceki sürümlerde <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>, , , ve .NET Core derlemeleri için dosya özellikleri iletişim kutusu gibi <xref:System.Environment.Version?displayProperty=nameWithType>yöntemler dosya sürümünü yansıtır. .NET Core 3.0 ile başlayarak ürün sürümünü yansıtırlar.

Aşağıdaki şekilde *System.Runtime.dll* assemblyi için .NET Core 2.2 (solda) ve .NET Core 3.0 (sağda) için windows **explorer** dosya özellikleri iletişim kutusunda görüntülenen sürüm bilgileri arasındaki farkı gösterilmektedir.

![Ürün sürüm bilgilerindeki fark](~/docs/images/core-changes/corefx/version-information-changes/file-details.png)

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3,0

#### <a name="recommended-action"></a>Önerilen eylem

Yok. Bu değişiklik, sürüm algılamayı kalın kullanmaktan çok sezgisel hale getirmelidir.

#### <a name="category"></a>Kategori

CoreFx

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Environment.Version?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>

<!--

### Affected APIs

- `P:System.Environment.Version`
- `P:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription`

-->
