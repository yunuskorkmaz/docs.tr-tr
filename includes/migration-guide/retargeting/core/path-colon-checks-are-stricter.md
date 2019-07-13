---
ms.openlocfilehash: 7f551fbc194d2da2fdae6bcc7025c20b03aadda2
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67859348"
---
### <a name="path-colon-checks-are-stricter"></a>Yol iki nokta üst üste denetimleri katı

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6.2, daha önce desteklenmeyen yolları (hem uzunluğu ve biçim) desteklemek için bir dizi değişiklik yapıldı. Denetimleri için uygun sürücü ayırıcı (virgül) sözdizimi, bazı URI yolları kabul edileceği kullanıldıkları birkaç select yolu API'lerde engelleme yan etkisi olan daha doğru yapıldı.|
|Öneri|Bir URI etkilenen API'lerine geçirilirse, dize geçerli bir yol ilk olarak değiştirin.<ul><li>Düzen URL'lerden el ile kaldırın (örneğin kaldırmak <code>file://</code> URL'lerden)</li><li>URI geçirmek <xref:System.Uri> sınıfı ve kullanın <xref:System.Uri.LocalPath></li></ul>Alternatif olarak, ayarlayarak dışında yeni yolu normalleştirme tercih edebilirsiniz <code>Switch.System.IO.UseLegacyPathHandling</code> AppContext anahtar true.|
|`Scope`|Kenar|
|Version|4.6.2|
|Type|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.IO.Path.GetDirectoryName(System.String)?displayProperty=nameWithType></li><li><xref:System.IO.Path.GetPathRoot(System.String)?displayProperty=nameWithType></li></ul>|

