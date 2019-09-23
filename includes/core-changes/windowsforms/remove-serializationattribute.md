---
ms.openlocfilehash: e9d76d5907e7d700fc57117ccb43f8c430c615b0
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181712"
---
### <a name="serializableattribute-removed-from-some-windows-forms-types"></a>SerializableAttribute bazı Windows Forms türlerinden kaldırıldı

, <xref:System.SerializableAttribute> Bilinen bir ikili serileştirme senaryosu olmayan bazı Windows Forms sınıflarından kaldırılmıştır.

#### <a name="change-description"></a>Açıklamayı Değiştir

Aşağıdaki türler .NET Framework <xref:System.SerializableAttribute> içindeki ile tasarlanmıştır, ancak öznitelik .NET Core 'da kaldırılmıştır:

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

Tarihsel olarak, bu serileştirme mekanizması ciddi bakım ve güvenlik sorunlarına sahipti. Türlerin `SerializableAttribute` sürdürülmesi, bu türlerin sürümden sürüme serileştirme değişiklikleri ve potansiyel olarak çerçeve serileştirme değişiklikleri için test olması gerektiği anlamına gelir. Bu, bu türleri daha da gelişmesini zorlaştırır ve bakım açısından maliyetli olabilir. Bu türlerin bilinen bir ikili serileştirme senaryosu yoktur, bu da özniteliği kaldırmanın etkilerini en aza indirir.

Daha fazla bilgi için bkz. <https://docs.microsoft.com/en-us/dotnet/standard/serialization/binary-serialization>.

#### <a name="version-introduced"></a>Sunulan sürüm

3,0 Preview 9

#### <a name="recommended-action"></a>Önerilen eylem

Seri hale getirilebilir olarak işaretlenmekte olan bu türlere bağlı olabilecek tüm kodları güncelleştirin.

#### <a name="category"></a>Kategori

Windows Forms

#### <a name="affected-apis"></a>Etkilenen API’ler

- Yok.

<!-- 

### Affected APIs

- Not detectable via API analysis

-->