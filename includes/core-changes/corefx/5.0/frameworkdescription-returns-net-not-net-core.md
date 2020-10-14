---
ms.openlocfilehash: 80d13609f1b02ae0ac875b2028e745670bb8f503
ms.sourcegitcommit: 39b1d5f2978be15409c189a66ab30781d9082cd8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/14/2020
ms.locfileid: "92050578"
---
### <a name="frameworkdescriptions-value-is-net-instead-of-net-core"></a>FrameworkDescription 'un değeri .NET Core yerine .NET

<xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> Şimdi ".NET Core" yerine ".NET" döndürür.

#### <a name="change-description"></a>Açıklamayı Değiştir

Önceki .NET sürümlerinde, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> Açıklama dizesinin parçası olarak ".NET Core" döndürür. Örneğin, `.NET Core 3.1.1` .

.NET 5,0 ' den başlayarak, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> Açıklama dizesinin parçası olarak ".net" döndürür. Örneğin, `.NET 5.0.0` .

#### <a name="reason-for-change"></a>Değişiklik nedeni

.NET 5 ile, `netcoreapp` `net` kısa hedef çerçeve bilinen adıyla değiştirilmiştir. Tutarlılık için çerçevenin açıklaması da güncelleştirilmiştir. Değişiklik, `FrameworkName` özelliğin dışında herhangi bir yerde kodlanmadığından, yüzeysel <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> .

#### <a name="version-introduced"></a>Sunulan sürüm

5.0

#### <a name="recommended-action"></a>Önerilen eylem

Tarafından döndürülen dizedeki ".NET Core" için arama yapan tüm kodları güncelleştirin <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription> .

#### <a name="category"></a>Kategori

Core .NET kitaplıkları

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription`

-->
