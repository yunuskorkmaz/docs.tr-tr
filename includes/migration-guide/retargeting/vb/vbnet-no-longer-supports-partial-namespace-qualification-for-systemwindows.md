---
ms.openlocfilehash: 8db115a46df3fcea103e8fa6896542d0116aa256
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59236740"
---
### <a name="vbnet-no-longer-supports-partial-namespace-qualification-for-systemwindows-apis"></a>VB.NET kısmi ad niteliği System.Windows API'leri için artık desteklemektedir.

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.5.2 başlayarak VB.NET projeleri System.Windows API'leri kısmen nitelenmiş ad alanları ile belirtemezsiniz. Örneğin, söz konusu <code>Windows.Forms.DialogResult</code> başarısız olur. Bunun yerine, kod tam adına başvurmak gerekir (<xref:System.Windows.Forms.DialogResult>) veya belirli ad alanını içeri aktarır ve başvurmak için yalnızca <xref:System.Windows.Forms.DialogResult?displayProperty=name>.|
|Öneri|Kod başvurmak için güncelleştirilmesi gerektiğini <code>System.Windows</code> API'leri basit adları (ve ilgili ad alanı alma) veya tam olarak nitelenmiş adlar.|
|Kapsam|İkincil|
|Sürüm|4.5.2|
|Tür|Yeniden Hedefleme|
