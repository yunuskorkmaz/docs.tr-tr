---
ms.openlocfilehash: bb264e406c6604c3606e564d99018eda0f9e8d89
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721238"
---
### <a name="apis-that-report-version-now-report-product-and-not-file-version"></a>Sürümü şimdi rapor eden API 'Ler rapor ürünü ve dosya sürümü değil

.NET Core sürümlerini döndüren API 'lerin birçoğu, artık dosya sürümü yerine ürün sürümünü döndürüyor.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Core 2,2 ve önceki sürümlerde,,, <xref:System.Environment.Version?displayProperty=nameWithType> <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> ve .NET Core derlemeleri için dosya özellikleri iletişim kutusu gibi yöntemler dosya sürümünü yansıtır. .NET Core 3,0 ile başlayarak ürün sürümünü yansıtmaktadır.

Aşağıdaki şekilde, **Windows Gezgini** dosya özellikleri iletişim kutusunda gösterildiği gibi .net Core 2,2 (solda) ve .net Core 3,0 (sağdaki) için *System. Runtime. dll* derlemesi için sürüm bilgileri arasındaki fark gösterilmektedir.

![Ürün sürümü bilgilerinde fark](~/docs/images/core-changes/corefx/version-information-changes/file-details.png)

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="recommended-action"></a>Önerilen eylem

Yok. Bu değişiklik, sürüm algılamayı obtuse yerine sezgisel hale getirir.

#### <a name="category"></a>Kategori

Core .NET kitaplıkları

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Environment.Version?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.Environment.Version`
- `P:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription`

-->
