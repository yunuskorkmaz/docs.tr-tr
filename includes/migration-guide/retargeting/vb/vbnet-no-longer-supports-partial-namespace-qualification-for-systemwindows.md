---
ms.openlocfilehash: 8db115a46df3fcea103e8fa6896542d0116aa256
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804667"
---
### <a name="vbnet-no-longer-supports-partial-namespace-qualification-for-systemwindows-apis"></a>VB.NET artık System.Windows API'leri için kısmi ad alanı niteliğini desteklemiyor

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.5.2'den başlayarak, VB.NET projeler system.windows API'lerini kısmen nitelikli ad boşluklarıyla belirtemez. Örneğin, atıfta başarısız <code>Windows.Forms.DialogResult</code> olur. Bunun yerine, kod tam nitelikli<xref:System.Windows.Forms.DialogResult>adı () veya belirli ad <xref:System.Windows.Forms.DialogResult?displayProperty=name>alanını alma ve yalnızca .|
|Öneri|Kod, <code>System.Windows</code> BASIT adlarla (ve ilgili ad alanını alma) veya tam nitelikli adlarla API'lere başvurmak üzere güncelleştirilmelidir.|
|Kapsam|İkincil|
|Sürüm|4.5.2|
|Tür|Yeniden Hedefleme|
