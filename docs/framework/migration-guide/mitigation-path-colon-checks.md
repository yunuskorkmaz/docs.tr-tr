---
title: 'Risk azaltma: yol Iki nokta denetimleri'
ms.date: 03/30/2017
ms.assetid: a0bb52de-d279-419d-8f23-4b12d1a3f36e
ms.openlocfilehash: e88643fea3bd507289436f41880a2de34117884f
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73457902"
---
# <a name="mitigation-path-colon-checks"></a>Risk azaltma: yol Iki nokta denetimleri
.NET Framework 4.6.2 hedefleyen uygulamalarla başlayarak, daha önce desteklenmeyen yolları (hem uzunluk hem de biçim bakımından) desteklemeye yönelik bir dizi değişiklik yapılmıştır. Özellikle, uygun sürücü ayırıcı söz dizimini (iki nokta üst üste) denetler.  
  
## <a name="impact"></a>Etki  
 Bu değişiklikler <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> ve <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> yöntemlerinin daha önce desteklediği bazı URI yollarını engeller.  
  
## <a name="mitigation"></a>Azaltma  
 Artık <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> ve <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> yöntemleri tarafından desteklenmeyen daha önceden kabul edilebilir bir yolun sorununu çözmek için şunları yapabilirsiniz:  
  
- Düzeni bir URL 'den el ile kaldırın. Örneğin, URL 'den `file://` kaldırın.  
  
- URI 'yi bir <xref:System.Uri> oluşturucusuna geçirin ve <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType> özelliğinin değerini alın.  
  
- `Switch.System.IO.UseLegacyPathHandling`<xref:System.AppContext> anahtarını `true`ayarlayarak yeni yol normalleştirmesini geri çevirin.  
  
    ```xml  
    <runtime>  
        <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
    </runtime>  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama uyumluluğu](application-compatibility.md)
