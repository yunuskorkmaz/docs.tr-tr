---
title: İstemciler İçin UI Otomasyon Denetim Düzenleri
description: UI Otomasyonu istemcilerinin Denetim desenleri hakkında genel bakış konusunu okuyun. Kullanıcı arabirimi (UI) hakkındaki bilgilere erişmek için denetim desenlerini kullanın.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, control patterns for clients
- control patterns, UI Automation clients
ms.assetid: 571561d8-5f49-43a9-a054-87735194e013
ms.openlocfilehash: f2def328228a30ace6d0edc0661d6e79f237d6f4
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87163867"
---
# <a name="ui-automation-control-patterns-for-clients"></a>İstemciler İçin UI Otomasyon Denetim Düzenleri
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu genel bakış, UI Otomasyonu istemcilerinin denetim desenlerini tanıtır. UI Otomasyon istemcisinin, ile ilgili bilgilere erişmek için denetim desenlerini nasıl kullanabileceği hakkında bilgi içerir [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] .  
  
 Denetim desenleri denetim türünden veya denetimin görünümünün bağımsız olarak bir denetimin işlevini kategorilere ayırma ve kullanıma sunma için bir yol sağlar. UI Otomasyonu istemcileri, <xref:System.Windows.Automation.AutomationElement> Hangi denetim desenlerinin desteklendiğini ve denetimin davranışından emin olduğunu tespit etmek için bir öğesini inceleyebilir.  
  
 Denetim desenlerinin tüm listesi için bkz. [UI Otomasyonu Denetim desenlerine genel bakış](ui-automation-control-patterns-overview.md).  
  
<a name="uiautomation_getting_control_patterns"></a>
## <a name="getting-control-patterns"></a>Denetim desenleri alma  
 İstemciler, ya da çağırarak bir denetim modelini alır <xref:System.Windows.Automation.AutomationElement> <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A?displayProperty=nameWithType> <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A?displayProperty=nameWithType> .  
  
 İstemciler <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> `IsPatternAvailable` <xref:System.Windows.Automation.AutomationElement.IsTextPatternAvailableProperty> , üzerinde bir desen veya desen grubunun desteklenip desteklenmediğini anlamak için yöntemini veya bağımsız bir özelliği (örneğin,) kullanabilir <xref:System.Windows.Automation.AutomationElement> . Ancak, `null` desteklenen özellikleri kontrol etmek ve daha az işlem arası çağrıya neden olduğundan denetim modelini almak yerine, bir başvuru için denetim modelini ve test almayı denemek daha etkilidir.  
  
 Aşağıdaki örnek, öğesinden bir denetim deseninin nasıl alınacağını gösterir <xref:System.Windows.Automation.TextPattern> <xref:System.Windows.Automation.AutomationElement> .  
  
 [!code-csharp[UIATextPattern_snip#1037](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#1037)]  
  
<a name="uiautomation_properties_on_control_patterns"></a>
## <a name="retrieving-properties-on-control-patterns"></a>Denetim desenlerinde özellikleri alma  
 İstemciler, veya öğesini çağırarak <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType> <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType> ve uygun bir türe döndürülen nesneyi kaldırarak denetim desenlerindeki özellik değerlerini alabilir. Özellikler hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [Istemciler Için UI Otomasyon özellikleri](ui-automation-properties-for-clients.md).  
  
 Yöntemlerin yanı sıra `GetPropertyValue` , bir düzendeki özelliklere erişmek için ortak dil çalışma zamanı (CLR) erişimcileri aracılığıyla özellik değerleri alınabilir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .  
  
<a name="uiautomation_with_variable_patterns"></a>
## <a name="controls-with-variable-patterns"></a>Değişken desenleri olan denetimler  
 Bazı denetim türleri, durumlarına veya denetimin kullanılmakta olmasına bağlı olarak farklı desenleri destekler. Değişken desenleri olan denetim örnekleri, liste görünümleridir (küçük resimler, Kutucuklar, simgeler, liste, Ayrıntılar), Microsoft Excel grafikleri (pasta, çizgi, çubuk, formül içeren hücre değeri), Microsoft Word 'Ün belge alanı (normal, Web düzeni, ana hat, yazdırma düzeni, Baskı Önizleme) ve Microsoft Windows Media Player kaplamaları.  
  
 Özel denetim türlerini uygulayan denetimler, işlevlerini temsil etmek için gereken herhangi bir denetim deseni kümesine sahip olabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyon Denetim Düzenleri](ui-automation-control-patterns.md)
- [UI Otomasyon Metin Düzeni](ui-automation-text-pattern.md)
- [UI Otomasyonu Kullanarak Denetim Çağırma](invoke-a-control-using-ui-automation.md)
- [UI Otomasyonunu Kullanarak Onay Kutusunun Değiştir Durumunu Alma](get-the-toggle-state-of-a-check-box-using-ui-automation.md)
- [UI Otomasyon İstemcileri İçin Denetim Düzeni Eşleştirmesi](control-pattern-mapping-for-ui-automation-clients.md)
- [TextModel metin ekleme örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InsertText)
- [TextModel arama ve seçim örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/FindText)
- [Invokemodel, ExpandCollapsePattern ve Togglemodel örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InvokePattern)
