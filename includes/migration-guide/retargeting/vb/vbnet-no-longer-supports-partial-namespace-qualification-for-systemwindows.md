---
ms.openlocfilehash: cef8096c971da8ae245ff974697022f350cb9195
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616071"
---
### <a name="vbnet-no-longer-supports-partial-namespace-qualification-for-systemwindows-apis"></a>VB.NET artık System. Windows API 'Leri için kısmi ad alanı nitelemesini desteklemiyor

#### <a name="details"></a>Ayrıntılar

.NET Framework 4.5.2 ' den başlayarak, VB.NET projeleri kısmen nitelenmiş ad alanları olan System. Windows API 'Lerini belirtemez. Örneğin, öğesine başvurma `Windows.Forms.DialogResult` başarısız olur. Bunun yerine, kod tam olarak nitelenmiş ada () başvurmalıdır <xref:System.Windows.Forms.DialogResult> veya belirli ad alanını içeri aktarıp yalnızca öğesine başvurmalıdır <xref:System.Windows.Forms.DialogResult?displayProperty=fullName> .

#### <a name="suggestion"></a>Öneri

Kod `System.Windows` , basit adlarla (ve ilgili ad alanını içeri aktararak) veya tam nitelikli adlara sahip API 'lere başvuracak şekilde güncelleştirilmelidir.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | İkincil       |
| Sürüm | 4.5.2       |
| Tür    | Yeniden Hedefleme |
