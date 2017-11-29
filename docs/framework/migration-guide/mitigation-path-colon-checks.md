---
title: "Azaltma: Yolu iki nokta üst üste denetimleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a0bb52de-d279-419d-8f23-4b12d1a3f36e
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a387e02c9d754db6af7fa2d2ba5f2ea6d96d4301
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="mitigation-path-colon-checks"></a>Azaltma: Yolu iki nokta üst üste denetimleri
Hedefleyen uygulamalar ile başlayan [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], daha önce desteklenmeyen yolları (her ikisi de uzunluğu ve biçim açısından) desteklemek için yapılan değişiklik sayısı. Özellikle, uygun sürücü ayırıcı sözdizimi (iki nokta üst üste) denetler daha doğru yapıldı.  
  
## <a name="impact"></a>Etki  
 Bu değişiklikler bazı URI yollarını engellemeye <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> ve <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> daha önce desteklenen yöntemleri.  
  
## <a name="mitigation"></a>Azaltma  
 Artık tarafından desteklenen daha önce kabul edilebilir bir yolu sorunu gidermek için <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> ve <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> yöntemleri, aşağıdakileri yapabilirsiniz:  
  
-   El ile bir URL'den düzeni kaldırın. Örneğin, kaldırma `file://` bir URL'den.  
  
-   URI geçirmek bir <xref:System.Uri> oluşturucusu ve değerini almak <xref:System.Uri.LocalPath%2A?displayProperty=nameWithType> özelliği.  
  
-   Yeni yol normalleştirme dışında ayarlayarak opt `Switch.System.IO.UseLegacyPathHandling` <xref:System.AppContext> geçiş `true`.  
  
    ```xml  
    <runtime>  
        <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
    </runtime>  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yeniden hedefleme değişiklikleri](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-2.md)
