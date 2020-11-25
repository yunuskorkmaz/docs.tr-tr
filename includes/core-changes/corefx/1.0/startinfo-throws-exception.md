---
ms.openlocfilehash: 92c03328414410d56a2ff5f445639757367b42c7
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032063"
---
### <a name="processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start"></a>Process. StartInfo, başlatmadığınız işlemler için InvalidOperationException 'yi oluşturur

<xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType>Kodunuzun başlatmadığınız işlemlere yönelik özelliği okuma bir atar <xref:System.InvalidOperationException> .

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Framework, <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> kodunuzun başlatmadığınız işlemlere yönelik özelliğe erişim bir kukla <xref:System.Diagnostics.ProcessStartInfo> nesne döndürür. Kukla nesne, hariç tüm özellikleri için varsayılan değerleri içerir <xref:System.Diagnostics.ProcessStartInfo.EnvironmentVariables> .

.NET Core 1,0 ' den başlayarak, <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> başlatmadığınız bir işlemin özelliğini (çağırarak, çağırarak <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> ) okuduğunuzda, bir oluşturulur <xref:System.InvalidOperationException> .

#### <a name="version-introduced"></a>Sunulan sürüm

1,0

#### <a name="recommended-action"></a>Önerilen eylem

<xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType>Kodunuzun başlamadığınız işlemlere yönelik özelliğe erişmeyin. Örneğin, tarafından döndürülen işlemlere yönelik bu özelliği okumayın <xref:System.Diagnostics.Process.GetProcesses%2A?displayProperty=nameWithType> .

#### <a name="category"></a>Kategori

Core .NET kitaplıkları

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Diagnostics.Process.StartInfo?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Diagnostics.Process.StartInfo`

-->
