---
title: 'Azaltma: Yol iki nokta üst üste denetimleri'
ms.date: 03/30/2017
ms.assetid: a0bb52de-d279-419d-8f23-4b12d1a3f36e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 342c3ce59ad80c9a60f2a2b69b30f77ff0549415
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59176767"
---
# <a name="mitigation-path-colon-checks"></a>Azaltma: Yol iki nokta üst üste denetimleri
Hedefleyen uygulamalar ile başlayan [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], daha önce desteklenmeyen yolları (hem de uzunluğu ve biçim açısından) desteklemek için bir dizi değişiklik yapıldı. Özellikle, denetimleri uygun sürücü ayırıcı sözdizimi (iki nokta üst üste) için daha doğru yapıldı.  
  
## <a name="impact"></a>Etki  
 Bazı URI yollarını bu değişiklikleri engellemeye <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> ve <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> daha önce desteklenen yöntemleri.  
  
## <a name="mitigation"></a>Azaltma  
 Tarafından artık desteklenmeyen daha önce kabul edilebilir bir yolu, sorunu gidermek için <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> ve <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> yöntemleri, aşağıdakileri yapabilirsiniz:  
  
-   El ile bir URL'den düzeni kaldırın. Örneğin, kaldırma `file://` bir URL'den.  
  
-   URI başarılı bir <xref:System.Uri> oluşturucusu ve değerini alma <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType> özelliği.  
  
-   Yeni yol normalleştirme dışında ayarlayarak iyileştirilmiş `Switch.System.IO.UseLegacyPathHandling` <xref:System.AppContext> geçin `true`.  
  
    ```xml  
    <runtime>  
        <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
    </runtime>  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Hedefleme Değişiklikleri](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-2.md)
