---
ms.openlocfilehash: 3f330d5e601d599231ef0336b785e677fe1d114e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616084"
---
### <a name="dataobjectgetdata-now-retrieves-data-as-utf-8"></a>DataObject. GetData artık verileri UTF-8 olarak alıyor

#### <a name="details"></a>Ayrıntılar

.NET Framework 4 ' ü hedefleyen veya .NET Framework 4.5.1 veya önceki sürümlerde çalışan uygulamalar için `DataObject.GetData` HTML biçimli verileri BIR ASCII dizesi olarak alır. Sonuç olarak, ASCII olmayan karakterler (ASCII kodları 0x7F 'den büyük olan karakterler) iki rastgele karakterle temsil edilir.<p/>.NET Framework 4,5 veya üstünü hedefleyen ve .NET Framework 4.5.2 üzerinde çalışan uygulamalar için, `DataObject.GetData` HTML biçimli verileri 0x7F 'den büyük karakterleri temsil eden UTF-8 olarak alır.

#### <a name="suggestion"></a>Öneri

HTML biçimli dizelerdeki kodlama sorunu için geçici bir çözüm uyguladıysanız (örneğin, panodan alınan HTML dizesini açıkça kodlayarak <xref:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName> ) ve uygulamanızı sürüm 4 ' ten 4,5 ' ye yeniden hedefliyorsanız, bu geçici çözüm kaldırılmalıdır. Bazı nedenlerle eski davranış gerekiyorsa, uygulama bu davranışı almak için .NET Framework 4,0 ' i hedefleyebilir.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | Edge        |
| Sürüm | 4.5.2       |
| Tür    | Yeniden Hedefleme |

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Windows.DataObject.GetData(System.String)?displayProperty=nameWithType>
- <xref:System.Windows.DataObject.GetData(System.Type)?displayProperty=nameWithType>
- <xref:System.Windows.DataObject.GetData(System.String,System.Boolean)?displayProperty=nameWithType>
