---
title: "İstemciler İçin UI Otomasyon Denetim Düzenleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation, control patterns for clients
- control patterns, UI Automation clients
ms.assetid: 571561d8-5f49-43a9-a054-87735194e013
caps.latest.revision: "24"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 1d556b3da13b70a0a5e69eb72905e04a01dffa9b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ui-automation-control-patterns-for-clients"></a>İstemciler İçin UI Otomasyon Denetim Düzenleri
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu genel bakışta UI Otomasyon istemcileri için Denetim desenleri tanıtır. UI Otomasyonu istemci hakkındaki bilgilere erişmek için Denetim düzenleri nasıl kullanabileceğinizi hakkında bilgi içeren [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)].  
  
 Denetim desenleri kategorilere ayırmak ve Denetim türü veya denetiminin görünümünü bağımsız bir denetimin işlevselliği kullanıma sunmak için bir yol sağlar. UI Otomasyon istemcileri inceleyin bir <xref:System.Windows.Automation.AutomationElement> denetleyen belirlemek için desenleri desteklenir ve Denetim davranışını gösterilmeyeceği.  
  
 Denetim desenleri tam bir listesi için bkz: [UI Otomasyon denetim düzenlerine genel bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
<a name="uiautomation_getting_control_patterns"></a>   
## <a name="getting-control-patterns"></a>Denetim desenlerini alma  
 İstemcileri almak alınan denetim deseni bir <xref:System.Windows.Automation.AutomationElement> ya da çağırarak <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A?displayProperty=nameWithType> veya <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A?displayProperty=nameWithType>.  
  
 İstemcileri kullanabilir <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> yöntem veya tek bir `IsPatternAvailable` özelliği (örneğin, <xref:System.Windows.Automation.AutomationElement.IsTextPatternAvailableProperty>) üzerinde bir desen veya desenleri grubunun desteklenip desteklenmediğini belirlemek için <xref:System.Windows.Automation.AutomationElement>. Ancak, Denetim düzeni almak ve için test etme girişiminde daha verimli bir `null` desteklenen özellikleri işaretleyin ve daha az işlem içi çağrılarında sonuçları beri denetim düzeni almak için daha başvuru.  
  
 Aşağıdaki örnekte nasıl alındığını anlatan bir <xref:System.Windows.Automation.TextPattern> denetim düzeni gelen bir <xref:System.Windows.Automation.AutomationElement>.  
  
 [!code-csharp[UIATextPattern_snip#1037](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#1037)]  
  
<a name="uiautomation_properties_on_control_patterns"></a>   
## <a name="retrieving-properties-on-control-patterns"></a>Denetim desenleri özelliklerini alma  
 İstemciler, ya da çağırarak denetim düzenleri özellik değerlerini alabilir <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType> veya <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType> ve nesne atama için uygun bir tür döndürdü. Daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellikleri, görmek [istemciler için UI Otomasyon özellikleri](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
 Ek olarak `GetPropertyValue` yöntemleri, özellik değerlerini alınabilir aracılığıyla [!INCLUDE[TLA#tla_clr](../../../includes/tlasharptla-clr-md.md)] erişmek için erişimcileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bir desen özellikleri.  
  
<a name="uiautomation_with_variable_patterns"></a>   
## <a name="controls-with-variable-patterns"></a>Değişken desenlerle denetimleri  
 Bazı denetim türleri durumlarına veya denetimi kullanılıyor şekilde bağlı olarak farklı desenleri destekler. Değişken desenleri olabilir denetimleri örnekler liste görünümleri (küçük resimleri, kutucukları, simgeler, listesi, Ayrıntılar) [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] grafikleri (pasta, çubuk, hücre değerini bir formülü olan satır), [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)]ait belge alan (Normal, Web düzeni anahat, yazdırma düzeni, yazdırma Önizleme), ve [!INCLUDE[TLA#tla_wmp](../../../includes/tlasharptla-wmp-md.md)] kaplamaları.  
  
 Özel denetim türlerini uygulayan denetimlerin işlevleri temsil etmek için gereken denetim düzenleri herhangi bir kümesi olabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UI Otomasyon denetim düzenleri](../../../docs/framework/ui-automation/ui-automation-control-patterns.md)  
 [UI Otomasyon metin düzeni](../../../docs/framework/ui-automation/ui-automation-text-pattern.md)  
 [UI Otomasyonu kullanarak denetim çağırma](../../../docs/framework/ui-automation/invoke-a-control-using-ui-automation.md)  
 [UI otomasyonunu kullanarak onay kutusunun Değiştir durumunu alma](../../../docs/framework/ui-automation/get-the-toggle-state-of-a-check-box-using-ui-automation.md)  
 [UI Otomasyon istemcileri için Denetim düzeni eşleştirmesi](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)  
 [TextPattern Ekle metin örneği](http://msdn.microsoft.com/en-us/67353f93-7ee2-42f2-ab76-5c078cf6ca16)  
 [TextPattern arama ve seçim örneği](http://msdn.microsoft.com/en-us/0a3bca57-8b72-489d-a57c-da85b7a22c7f)  
 [InvokePattern'ı ve ExpandCollapsePattern'ı menü öğesi örneği](http://msdn.microsoft.com/en-us/b7fa141c-e2d1-4da2-a27f-81a7d1172210)
