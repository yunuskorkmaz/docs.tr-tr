---
title: 'Azaltma: Özel IMessageFilter.PreFilterMessage uygulamaları'
ms.date: 03/30/2017
ms.assetid: 9cf47c5b-0bb2-45df-9437-61cd7e7c2f4d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c0567ce61a57d5e1575f42ccea332236e3cde987
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54552872"
---
# <a name="mitigation-custom-imessagefilterprefiltermessage-implementations"></a>Azaltma: Özel IMessageFilter.PreFilterMessage uygulamaları
.NET Framework başlayarak sürümlerini hedefleyen Windows Forms uygulamalarında [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], özel bir <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> uygulama için güvenli bir şekilde filtre iletileri <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> yöntemi çağrıldığında, <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> uygulama:  
  
-   Birini veya her ikisini aşağıdakileri yapar:  
  
    -   İleti filtresini çağırarak ekler <xref:System.Windows.Forms.Application.AddMessageFilter%2A> yöntemi.  
  
    -   İleti filtresini çağırarak kaldırır <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A> yöntemi. yöntem.  
  
-   **Ve** pompalara iletileri çağırarak <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> yöntemi.  
  
## <a name="impact"></a>Etki  
 Bu değişiklik, yalnızca .NET Framework başlayarak sürümlerini hedefleyen Windows Forms uygulamaları etkiler [!INCLUDE[net_v461](../../../includes/net-v461-md.md)].  
  
 Bazı durumlarda bu tür uygulamaları .NET Framework'ün önceki sürümlerini hedefleyen Windows Forms uygulamaları için throw bir <xref:System.IndexOutOfRangeException> özel durum olduğunda <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> yöntemi çağrılır  
  
## <a name="mitigation"></a>Azaltma  
 Bu değişiklik, istenmeyen ise, uygulamalar hedef [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] veya sonraki bir sürümü için aşağıdaki yapılandırma ayarı ekleyerek dışında tercih edebilirsiniz [ \<çalışma zamanı >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) uygulamanın yapılandırma dosyası bölümünü:  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=true" />   
</runtime>  
```  
  
 Ayrıca, .NET Framework'ün önceki sürümlerini hedefleyen ancak altında çalışan uygulamalar [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] veya sonraki bir sürümünü, bu davranış için aşağıdaki yapılandırma ayarı ekleyerek seçebilirsiniz [ \<çalışma zamanı >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)uygulamanın yapılandırma dosyası bölümünü:  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=false" />   
</runtime>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Yeniden Hedefleme Değişiklikleri](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-1.md)
