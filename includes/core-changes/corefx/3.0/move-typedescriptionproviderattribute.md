---
ms.openlocfilehash: 7a2617f27dfd6bb527ff6d408fae6382075f24ae
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721361"
---
### <a name="typedescriptionproviderattribute-moved-to-another-assembly"></a>TypeDescriptionProviderAttribute başka bir derlemeye taşındı

<xref:System.ComponentModel.TypeDescriptionProviderAttribute>Sınıf taşınmış.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Core 2,2 ve önceki sürümlerinde, <xref:System.ComponentModel.TypeDescriptionProviderAttribute> sınıfı *System. ComponentModel. TypeConverter* derlemesinde bulunur.

.NET Core 3,0 ile başlayarak, *System. ObjectModel* derlemesinde bulunur.

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="recommended-action"></a>Önerilen eylem

Bu değişiklik yalnızca, <xref:System.ComponentModel.TypeDescriptionProviderAttribute> <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> veya <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> türü belirli bir derlemede olduğunu varsayan bir aşırı yüklemesi çağırarak, türü yüklemek için yansıma kullanan uygulamaları etkiler. Bu durumda, yöntem çağrısında başvurulan derleme, türün yeni derleme konumunu yansıtacak şekilde güncellenmelidir.

#### <a name="category"></a>Kategori

Windows Forms

#### <a name="affected-apis"></a>Etkilenen API’ler

Yok.

<!--

#### Affected APIs

- Not detectable via API analysis

-->
