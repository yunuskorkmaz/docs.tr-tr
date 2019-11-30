---
ms.openlocfilehash: 2a751acc129ebd1c917b87f8083ffef72c7d8c17
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568159"
---
### <a name="apis-that-report-version-now-report-product-and-not-file-version"></a>Sürümü şimdi rapor eden API 'Ler rapor ürünü ve dosya sürümü değil

.NET Core sürümlerini döndüren API 'lerin birçoğu, artık dosya sürümü yerine ürün sürümünü döndürdü.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Core 2,2 ve önceki sürümlerde, .NET Core derlemeleri için <xref:System.Environment.Version?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>ve dosya özellikleri iletişim kutusu gibi yöntemler dosya sürümünü yansıtır. .NET Core 3,0 ile başlayarak ürün sürümünü yansıtmaktadır.

Aşağıdaki şekilde, **Windows Gezgini** dosya özellikleri iletişim kutusunda gösterildiği gibi .net Core 2,2 (solda) ve .net Core 3,0 (sağdaki) için *System. Runtime. dll* derlemesi için sürüm bilgileri arasındaki fark gösterilmektedir.

![Ürün sürümü bilgilerinde fark](~/docs/images/core-changes/corefx/version-information-changes/file-details.png)

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="recommended-action"></a>Önerilen eylem

Yok. Bu değişiklik, sürüm algılamayı obtuse yerine sezgisel hale getirir.

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
