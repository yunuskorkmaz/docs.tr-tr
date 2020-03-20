---
title: İstemciler İçin UI Otomasyon Denetim Düzenleri
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, control patterns for clients
- control patterns, UI Automation clients
ms.assetid: 571561d8-5f49-43a9-a054-87735194e013
ms.openlocfilehash: 1ee0df5b133f08ec3cf6ba617c80c480e207ddf6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179955"
---
# <a name="ui-automation-control-patterns-for-clients"></a>İstemciler İçin UI Otomasyon Denetim Düzenleri
> [!NOTE]
> Bu dokümantasyon, ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıfları kullanmak <xref:System.Windows.Automation> isteyen .NET Framework geliştiricileri için tasarlanmıştır. Hakkında en son [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]bilgi için [Bkz. Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu genel bakış, UI Automation istemcileri için denetim desenleri sunar. Bir Kullanıcı Aracı Otomasyon istemcisi hakkında bilgilere erişmek için [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)]denetim desenleri nasıl kullanabileceğine ilişkin bilgileri içerir.  
  
 Denetim desenleri, denetim türünden veya denetimin görünümünden bağımsız olarak bir denetimin işlevselliğini kategorilere ayırmak ve ortaya çıkarmak için bir yol sağlar. UI Automation istemcileri, hangi denetim düzenlerinin desteklenebileceğini belirlemek ve denetimin davranışından emin olmak için bir <xref:System.Windows.Automation.AutomationElement> inceleme yapabilir.  
  
 Denetim desenlerinin tam listesi için [UI Otomasyon Denetim Modellerine Genel Bakış](ui-automation-control-patterns-overview.md)bölümüne bakın.  
  
<a name="uiautomation_getting_control_patterns"></a>
## <a name="getting-control-patterns"></a>Kontrol Desenlerini Alma  
 İstemciler bir denetim <xref:System.Windows.Automation.AutomationElement> deseni <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A?displayProperty=nameWithType> <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A?displayProperty=nameWithType>ya da arayarak bir denetim deseni almak .  
  
 İstemciler <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> yöntemi veya `IsPatternAvailable` tek bir özelliği <xref:System.Windows.Automation.AutomationElement.IsTextPatternAvailableProperty>(örneğin,) bir desen veya desen grubu <xref:System.Windows.Automation.AutomationElement>üzerinde desteklenir olup olmadığını belirlemek için kullanabilirsiniz . Ancak, desteklenen özellikleri denetlemek ve daha az çapraz `null` işlem çağrıları ile sonuçlandığından denetim deseni almak yerine, denetim deseni ve başvuru için test etmek daha etkilidir.  
  
 Aşağıdaki örnek, bir <xref:System.Windows.Automation.TextPattern> <xref:System.Windows.Automation.AutomationElement>denetim deseninin nasıl elde edilebildiğini gösterir.  
  
 [!code-csharp[UIATextPattern_snip#1037](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#1037)]  
  
<a name="uiautomation_properties_on_control_patterns"></a>
## <a name="retrieving-properties-on-control-patterns"></a>Kontrol Desenleri Özellikleri Alma  
 İstemciler, denetim desenleri üzerindeki <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType> özellik <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType> değerlerini, uygun bir türe çağırarak veya nesneyi döküme alarak alabilir. Özellikler hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] daha fazla bilgi [için, Müşteriler için Kullanıcı Arabirimi Otomasyon Özellikleri'ne](ui-automation-properties-for-clients.md)bakın.  
  
 Yöntemlere `GetPropertyValue` ek olarak, özellik değerleri ortak dil çalışma zamanı (CLR) erişime [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sahip ler aracılığıyla bir desen üzerindeki özelliklere erişmek için alınabilir.  
  
<a name="uiautomation_with_variable_patterns"></a>
## <a name="controls-with-variable-patterns"></a>Değişken Desenli Denetimler  
 Bazı denetim türleri durumlarına veya denetimin kullanılma şekline bağlı olarak farklı desenleri destekler. Değişken desenleri olan denetimlere örnek olarak liste görünümleri (küçük resimler, döşemeler, simgeler, liste, ayrıntılar), Microsoft Excel Grafikleri (Pasta, Satır, Çubuk, formüllü Hücre Değeri), Microsoft Word'ün belge alanı (Normal, Web Düzeni, Anahat, Yazdırma Düzeni, Yazdırma Önizleme) ve Microsoft Windows Media Player kaplamaları.  
  
 Özel denetim türlerini uygulayan denetimler, işlevselliklerini temsil etmek için gereken denetim desenleri kümesine sahip olabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyon Denetim Düzenleri](ui-automation-control-patterns.md)
- [UI Otomasyon Metin Düzeni](ui-automation-text-pattern.md)
- [UI Otomasyonu Kullanarak Denetim Çağırma](invoke-a-control-using-ui-automation.md)
- [UI Otomasyonunu Kullanarak Onay Kutusunun Değiştir Durumunu Alma](get-the-toggle-state-of-a-check-box-using-ui-automation.md)
- [UI Otomasyon İstemcileri İçin Denetim Düzeni Eşleştirmesi](control-pattern-mapping-for-ui-automation-clients.md)
- [TextPattern Ekle Metin Örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InsertText)
- [TextPattern Arama ve Seçim Örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/FindText)
- [InvokePattern, ExpandCollapsePattern ve TogglePattern Örnek](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InvokePattern)
