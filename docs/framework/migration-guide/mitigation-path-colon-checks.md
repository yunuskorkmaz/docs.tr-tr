---
title: 'Azaltma: Yol Kolon Denetimleri'
ms.date: 03/30/2017
ms.assetid: a0bb52de-d279-419d-8f23-4b12d1a3f36e
ms.openlocfilehash: c6e1106b6f5d8457417992941b9f28712d484442
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181240"
---
# <a name="mitigation-path-colon-checks"></a>Azaltma: Yol Kolon Denetimleri
.NET Framework 4.6.2'yi hedefleyen uygulamalardan başlayarak, daha önce desteklenmeyen yolları (hem uzunluk hem de biçim açısından) desteklemek için bir dizi değişiklik yapıldı. Özellikle, uygun sürücü ayırıcı sözdizimi (iki nokta üst üste) için denetimler daha doğru yapıldı.  
  
## <a name="impact"></a>Etki  
 Bu değişiklikler, daha <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> önce <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> desteklenen bazı URI yollarını ve yöntemleri engeller.  
  
## <a name="mitigation"></a>Risk azaltma  
 Artık <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> yöntemler ve <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> yöntemler tarafından desteklenen daha önce kabul edilebilir bir yol sorununu çözüme getirmek için aşağıdakileri yapabilirsiniz:  
  
- Düzeni bir URL'den el ile kaldırın. Örneğin, bir `file://` URL'den kaldırın.  
  
- URI'yi bir <xref:System.Uri> oluşturucuya geçirin ve <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType> özelliğin değerini alın.  
  
- Anahtarı `Switch.System.IO.UseLegacyPathHandling` <xref:System.AppContext> `true`' ya ayarlayarak yeni yol normalleştirmesi dışında  
  
    ```xml  
    <runtime>  
        <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />
    </runtime>  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama uyumluluğu](application-compatibility.md)
