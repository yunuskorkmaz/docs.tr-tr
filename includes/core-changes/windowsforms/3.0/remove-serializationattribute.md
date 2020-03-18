---
ms.openlocfilehash: d48ced9d0201a33f9149aba155ddd3d8bc04c93f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74643958"
---
### <a name="serializableattribute-removed-from-some-windows-forms-types"></a>SerializableAttribute bazı Windows Forms türlerinden kaldırıldı

Bilinen <xref:System.SerializableAttribute> ikili serileştirme senaryoları olmayan bazı Windows Forms sınıflarından kaldırıldı.

#### <a name="change-description"></a>Açıklamayı değiştir

Aşağıdaki türler .NET Framework <xref:System.SerializableAttribute> ile dekore edilmiştir, ancak öznitelik .NET Core kaldırıldı:

- `System.InvariantComparer`
- <xref:System.ComponentModel.Design.ExceptionCollection?displayProperty=nameWithType>
- <xref:System.ComponentModel.Design.Serialization.CodeDomSerializerException?displayProperty=nameWithType>
- `System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService.CodeDomSerializationStore`
- <xref:System.Drawing.Design.ToolboxItem?displayProperty=nameWithType>
- `System.Resources.ResXNullRef`
- `System.Resources.ResXDataNode`
- `System.Resources.ResXFileRef`
- <xref:System.Windows.Forms.Cursor?displayProperty=nameWithType>
- `System.Windows.Forms.NativeMethods.MSOCRINFOSTRUCT`
- `System.Windows.Forms.NativeMethods.MSG`

Tarihsel olarak, bu serileştirme mekanizması ciddi bakım ve güvenlik endişeleri olmuştur. `SerializableAttribute` Türleri korumak, bu türlerin sürümden sürüme serileştirme değişiklikleri ve potansiyel olarak çerçeveden çerçeveye serileştirme değişiklikleri için sınanması gerektiği anlamına gelir. Bu, bu tür geliştirmek için daha zor hale getirir ve korumak için pahalıya mal olabilir. Bu türler, özniteliği kaldırmanın etkisini en aza indiren bilinen ikili serileştirme senaryolarına sahip değildir.

Daha fazla bilgi için [Ikili serileştirme](~/docs/standard/serialization/binary-serialization.md)ye bakın.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3.0 Önizleme 9

#### <a name="recommended-action"></a>Önerilen eylem

Bu tür serileştirilebilir olarak işaretlenmiş bağlı olabilecek tüm kodu güncelleştirin.

#### <a name="category"></a>Kategori

Windows Forms

#### <a name="affected-apis"></a>Etkilenen API’ler

- None

<!--

### Affected APIs

- Not detectable via API analysis

-->
