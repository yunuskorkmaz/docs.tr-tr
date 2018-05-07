---
title: 'Azaltma: Özel IMessageFilter.PreFilterMessage uygulamaları'
ms.date: 03/30/2017
ms.assetid: 9cf47c5b-0bb2-45df-9437-61cd7e7c2f4d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 78d8ba7f872095920e7fda727f46fc10b989ed37
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="mitigation-custom-imessagefilterprefiltermessage-implementations"></a>Azaltma: Özel IMessageFilter.PreFilterMessage uygulamaları
.NET Framework başlayarak sürümlerini hedefleyen Windows Forms uygulamalarında [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], özel bir <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> uygulaması için güvenli bir şekilde filtre iletileri <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> varsa yöntemi çağrıldığında <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> uygulama:  
  
-   Birini veya her ikisini aşağıdakileri yapar:  
  
    -   Bir ileti filtresi çağırarak ekler <xref:System.Windows.Forms.Application.AddMessageFilter%2A> yöntemi.  
  
    -   Bir ileti filtresi çağırarak kaldırır <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A> yöntemi. yöntem.  
  
-   **Ve** Pompalar iletileri çağırarak <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> yöntemi.  
  
## <a name="impact"></a>Etki  
 Bu değişiklik, yalnızca .NET Framework başlayarak sürümlerini hedefleyen Windows Forms uygulamaları etkiler [!INCLUDE[net_v461](../../../includes/net-v461-md.md)].  
  
 .NET Framework'ün önceki sürümlerini hedefleyen Windows Forms uygulamaları için bazı durumlarda bu tür uygulamalar throw bir <xref:System.IndexOutOfRangeException> özel durumu zaman <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> yöntemi çağrılır  
  
## <a name="mitigation"></a>Azaltma  
 Bu değişiklik istenmeyen ise, uygulamalar, hedef [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] veya sonraki bir sürümünü şu yapılandırma ayarı ekleyerek onu dışında tercih edebilirsiniz [ \<çalışma zamanı >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) uygulamanın yapılandırma dosyasının:  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=true" />   
</runtime>  
```  
  
 Buna ek olarak, .NET Framework'ün önceki sürümlerini hedefleyen ancak altında çalışan uygulamalar [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] veya sonraki bir sürümünü de bu davranış için şu yapılandırma ayarı ekleyerek seçebilirsiniz [ \<çalışma zamanı >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)uygulamanın yapılandırma dosyasının:  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=false" />   
</runtime>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yeniden Hedefleme Değişiklikleri](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-1.md)
