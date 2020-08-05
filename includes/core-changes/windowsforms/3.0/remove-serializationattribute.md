---
ms.openlocfilehash: 4fb1ffed97a5b7f906bed13a69f1e71563d11dae
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556219"
---
### <a name="serializableattribute-removed-from-some-windows-forms-types"></a>SerializableAttribute bazı Windows Forms türlerinden kaldırıldı

, <xref:System.SerializableAttribute> Bilinen bir ikili serileştirme senaryosu olmayan bazı Windows Forms sınıflarından kaldırılmıştır.

#### <a name="change-description"></a>Açıklamayı Değiştir

Aşağıdaki türler <xref:System.SerializableAttribute> .NET Framework içindeki ile tasarlanmıştır, ancak öznitelik .NET Core 'da kaldırılmıştır:

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

Tarihsel olarak, bu serileştirme mekanizması ciddi bakım ve güvenlik sorunlarına sahipti. `SerializableAttribute`Türlerin sürdürülmesi, bu türlerin sürümden sürüme serileştirme değişiklikleri ve potansiyel olarak çerçeve serileştirme değişiklikleri için test olması gerektiği anlamına gelir. Bu, bu türleri daha da gelişmesini zorlaştırır ve bakım açısından maliyetli olabilir. Bu türlerin bilinen bir ikili serileştirme senaryosu yoktur, bu da özniteliği kaldırmanın etkilerini en aza indirir.

Daha fazla bilgi için bkz. [ikili serileştirme](~/docs/standard/serialization/binary-serialization.md).

#### <a name="version-introduced"></a>Sunulan sürüm

3,0

#### <a name="recommended-action"></a>Önerilen eylem

Seri hale getirilebilir olarak işaretlenmekte olan bu türlere bağlı olabilecek tüm kodları güncelleştirin.

#### <a name="category"></a>Kategori

Windows Forms

#### <a name="affected-apis"></a>Etkilenen API’ler

- Hiçbiri

<!--

#### Affected APIs

- Not detectable via API analysis

-->
