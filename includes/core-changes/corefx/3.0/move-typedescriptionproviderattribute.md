---
ms.openlocfilehash: 57ca2ad839aab8d61da1a929660920efe1190334
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147542"
---
### <a name="typedescriptionproviderattribute-moved-to-another-assembly"></a>TypeDescriptionProviderAttribute başka bir derleme taşındı

Sınıf <xref:System.ComponentModel.TypeDescriptionProviderAttribute> taşındı.

#### <a name="change-description"></a>Açıklamayı değiştir

.NET Core 2.2 ve önceki <xref:System.ComponentModel.TypeDescriptionProviderAttribute> sürümlerinde, class *System.ComponentModel.TypeConverter* derlemesinde bulunur.

.NET Core 3.0 ile başlayarak *System.ObjectModel* derlemesinde bulunur.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3,0

#### <a name="recommended-action"></a>Önerilen eylem

Bu değişiklik yalnızca tür gibi <xref:System.ComponentModel.TypeDescriptionProviderAttribute> <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> bir yöntem veya tür belirli bir derleme <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> olduğunu varsayar aşırı yük çağırarak türü yüklemek için yansıma kullanan uygulamaları etkiler. Bu durumda, yöntem çağrısında başvurulan derleme, türün yeni derleme konumunu yansıtacak şekilde güncelleştirilmelidir.

#### <a name="category"></a>Kategori

Windows Forms

#### <a name="affected-apis"></a>Etkilenen API’ler

Yok.

<!--

### Affected APIs

- Not detectable via API analysis

-->
