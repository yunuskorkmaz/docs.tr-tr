---
title: Mayı Yol noktalı virgül denetimleri
ms.date: 03/30/2017
ms.assetid: a0bb52de-d279-419d-8f23-4b12d1a3f36e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a74c25a9bf4dd8b9ab86bd280881fe1a7999e1d5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70789982"
---
# <a name="mitigation-path-colon-checks"></a>Mayı Yol noktalı virgül denetimleri
.NET Framework 4.6.2 hedefleyen uygulamalarla başlayarak, daha önce desteklenmeyen yolları (hem uzunluk hem de biçim bakımından) desteklemeye yönelik bir dizi değişiklik yapılmıştır. Özellikle, uygun sürücü ayırıcı söz dizimini (iki nokta üst üste) denetler.  
  
## <a name="impact"></a>Etki  
 Bu değişiklikler, <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> ve <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> yöntemlerinin daha önce desteklediği bazı URI yollarını engeller.  
  
## <a name="mitigation"></a>Azaltma  
 Daha önce <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> ve <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> yöntemleri tarafından desteklenmeyen önceden kabul edilebilir bir yol sorununu geçici olarak çözmek için aşağıdakileri yapabilirsiniz:  
  
- Düzeni bir URL 'den el ile kaldırın. Örneğin, bir URL `file://` 'den kaldırın.  
  
- URI 'yi bir <xref:System.Uri> oluşturucuya geçirin ve <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType> özelliğin değerini alın.  
  
- <xref:System.AppContext> Anahtarı `Switch.System.IO.UseLegacyPathHandling` olarak`true`ayarlayarak yeni yol normalleştirmesini geri çevirin.  
  
    ```xml  
    <runtime>  
        <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
    </runtime>  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Hedefleme Değişiklikleri](retargeting-changes-in-the-net-framework-4-6-2.md)
