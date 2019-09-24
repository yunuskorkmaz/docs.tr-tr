---
ms.openlocfilehash: 4d479636f41095610eaf39f92ad0dad4863ab8b5
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216374"
---
### <a name="typedescriptionproviderattribute-moved-to-another-assembly"></a>TypeDescriptionProviderAttribute başka bir derlemeye taşındı

<xref:System.ComponentModel.TypeDescriptionProviderAttribute> Sınıf taşınmış.

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Core 2,2 ve önceki sürümlerinde, <xref:System.ComponentModel.TypeDescriptionProviderAttribute> sınıfı *System. ComponentModel. TypeConverter* derlemesinde bulunur.

.NET Core 3,0 ile başlayarak, *System. ObjectModel* derlemesinde bulunur.

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="recommended-action"></a>Önerilen eylem

Bu değişiklik yalnızca, <xref:System.ComponentModel.TypeDescriptionProviderAttribute> <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> veya türü belirli bir derlemede olduğunu varsayan bir aşırı yüklemesi <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> çağırarak, türü yüklemek için yansıma kullanan uygulamaları etkiler. Bu durumda, yöntem çağrısında başvurulan derleme, türün yeni derleme konumunu yansıtacak şekilde güncellenmelidir.

#### <a name="category"></a>Kategori

Windows Forms

#### <a name="affected-apis"></a>Etkilenen API’ler

- Yok.

<!--

### Affected APIs

- Not detectable via API analysis

-->
