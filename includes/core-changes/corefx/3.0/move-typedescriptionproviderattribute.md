---
ms.openlocfilehash: 4d479636f41095610eaf39f92ad0dad4863ab8b5
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568125"
---
### <a name="typedescriptionproviderattribute-moved-to-another-assembly"></a>TypeDescriptionProviderAttribute başka bir derlemeye taşındı

<xref:System.ComponentModel.TypeDescriptionProviderAttribute> sınıfı taşındı.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Core 2,2 ve önceki sürümlerinde <xref:System.ComponentModel.TypeDescriptionProviderAttribute> sınıfı *System. ComponentModel. TypeConverter* derlemesinde bulunur.

.NET Core 3,0 ile başlayarak, *System. ObjectModel* derlemesinde bulunur.

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="recommended-action"></a>Önerilen eylem

Bu değişiklik yalnızca, <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> gibi bir metodu veya türün belirli bir derlemede olduğunu varsayan <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> aşırı yüklemesini çağırarak <xref:System.ComponentModel.TypeDescriptionProviderAttribute> türünü yüklemek için yansıma kullanan uygulamaları etkiler. Bu durumda, yöntem çağrısında başvurulan derleme, türün yeni derleme konumunu yansıtacak şekilde güncellenmelidir.

#### <a name="category"></a>Kategori

Windows Forms

#### <a name="affected-apis"></a>Etkilenen API’ler

- Yok.

<!--

### Affected APIs

- Not detectable via API analysis

-->
