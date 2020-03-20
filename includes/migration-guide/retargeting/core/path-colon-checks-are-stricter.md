---
ms.openlocfilehash: a51738fa75ba2dd4574549fce2570df8231c4cae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859348"
---
### <a name="path-colon-checks-are-stricter"></a>Yol kolon denetimleri daha sıkıdır

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6.2'de, daha önce desteklenmeyen yolları (hem uzunluk hem de biçim olarak) desteklemek için bir dizi değişiklik yapıldı. Uygun sürücü ayırıcısı (üst üste) sözdizimi için kontroller daha doğru yapıldı, hangi tolere edilmesi için kullanılan birkaç seçin Yol API'lerinde bazı URI yollarını engelleme yan etkisi vardı.|
|Öneri|Etkilenen API'lere bir URI geçiyorsanız, önce dizeyi yasal bir yol olarak değiştirin.<ul><li>Düzeni URL'lerden el ile kaldırma (örn. <code>file://</code> URL'lerden kaldırma)</li><li>URI'yi sınıfa <xref:System.Uri> geçirin ve<xref:System.Uri.LocalPath></li></ul>Alternatif olarak, AppContext anahtarını <code>Switch.System.IO.UseLegacyPathHandling</code> doğru olarak ayarlayarak yeni yol normalleştirmesini devre dışı kullanabilirsiniz.|
|Kapsam|Edge|
|Sürüm|4.6.2|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.IO.Path.GetDirectoryName(System.String)?displayProperty=nameWithType></li><li><xref:System.IO.Path.GetPathRoot(System.String)?displayProperty=nameWithType></li></ul>|
