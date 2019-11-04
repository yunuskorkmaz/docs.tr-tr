---
title: İstemciler İçin UI Otomasyon Denetim Düzenleri
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, control patterns for clients
- control patterns, UI Automation clients
ms.assetid: 571561d8-5f49-43a9-a054-87735194e013
ms.openlocfilehash: c7d9eeceaba2ed8b624d3001dae86868ef626c08
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458108"
---
# <a name="ui-automation-control-patterns-for-clients"></a>İstemciler İçin UI Otomasyon Denetim Düzenleri
> [!NOTE]
> Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu genel bakış, UI Otomasyonu istemcilerinin denetim desenlerini tanıtır. UI Otomasyon istemcisinin [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)]hakkındaki bilgilere erişmek için denetim düzenlerini nasıl kullanabileceği hakkında bilgi içerir.  
  
 Denetim desenleri denetim türünden veya denetimin görünümünün bağımsız olarak bir denetimin işlevini kategorilere ayırma ve kullanıma sunma için bir yol sağlar. UI Otomasyonu istemcileri, hangi denetim desenlerinin desteklendiğini ve denetimin davranışından emin olduğunu tespit etmek için bir <xref:System.Windows.Automation.AutomationElement> inceleyebilir.  
  
 Denetim desenlerinin tüm listesi için bkz. [UI Otomasyonu Denetim desenlerine genel bakış](ui-automation-control-patterns-overview.md).  
  
<a name="uiautomation_getting_control_patterns"></a>   
## <a name="getting-control-patterns"></a>Denetim desenleri alma  
 İstemciler, <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A?displayProperty=nameWithType> veya <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A?displayProperty=nameWithType>çağırarak <xref:System.Windows.Automation.AutomationElement> bir denetim modelini alır.  
  
 İstemciler, <xref:System.Windows.Automation.AutomationElement>bir desen veya bir desen grubunun desteklenip desteklenmediğini anlamak için <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> yöntemini veya bağımsız bir `IsPatternAvailable` özelliğini (örneğin, <xref:System.Windows.Automation.AutomationElement.IsTextPatternAvailableProperty>) kullanabilir. Ancak, desteklenen özellikleri kontrol etmek ve daha az işlem arası çağrıya neden olduğundan denetim modelini almak yerine `null` başvuru için denetim modelini ve testini almak daha verimlidir.  
  
 Aşağıdaki örnek, bir <xref:System.Windows.Automation.AutomationElement><xref:System.Windows.Automation.TextPattern> denetim deseninin nasıl alınacağını gösterir.  
  
 [!code-csharp[UIATextPattern_snip#1037](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#1037)]  
  
<a name="uiautomation_properties_on_control_patterns"></a>   
## <a name="retrieving-properties-on-control-patterns"></a>Denetim desenlerinde özellikleri alma  
 İstemciler, <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType> ya da <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType> çağırarak ve uygun bir türe döndürülen nesneyi vurarak denetim desenlerindeki özellik değerlerini alabilir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellikleri hakkında daha fazla bilgi için bkz. [istemciler Için UI Otomasyon özellikleri](ui-automation-properties-for-clients.md).  
  
 `GetPropertyValue` yöntemlerine ek olarak, bir düzende [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özelliklerine erişmek için ortak dil çalışma zamanı (CLR) erişimcileri aracılığıyla özellik değerleri alınabilir.  
  
<a name="uiautomation_with_variable_patterns"></a>   
## <a name="controls-with-variable-patterns"></a>Değişken desenleri olan denetimler  
 Bazı denetim türleri, durumlarına veya denetimin kullanılmakta olmasına bağlı olarak farklı desenleri destekler. Değişken desenleri olan denetim örnekleri, liste görünümleridir (küçük resimler, Kutucuklar, simgeler, liste, Ayrıntılar), Microsoft Excel grafikleri (pasta, çizgi, çubuk, formül içeren hücre değeri), Microsoft Word 'Ün belge alanı (normal, Web düzeni, ana hat, yazdırma düzeni, yazdırma Önizleme) ve Microsoft Windows Media Player kaplamaları.  
  
 Özel denetim türlerini uygulayan denetimler, işlevlerini temsil etmek için gereken herhangi bir denetim deseni kümesine sahip olabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu Denetim Desenleri](ui-automation-control-patterns.md)
- [UI Otomasyonu Metin Deseni](ui-automation-text-pattern.md)
- [UI Otomasyonu Kullanarak Denetim Çağırma](invoke-a-control-using-ui-automation.md)
- [UI Otomasyonunu Kullanarak Onay Kutusunun Değiştir Durumunu Alma](get-the-toggle-state-of-a-check-box-using-ui-automation.md)
- [UI Otomasyonu İstemcileri İçin Denetim Düzeni Eşlemesi](control-pattern-mapping-for-ui-automation-clients.md)
- [TextModel metin ekleme örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InsertText)
- [TextModel arama ve seçim örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/FindText)
- [Invokemodel, ExpandCollapsePattern ve Togglemodel örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InvokePattern)
