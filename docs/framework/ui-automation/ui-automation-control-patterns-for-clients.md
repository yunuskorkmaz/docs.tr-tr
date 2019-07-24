---
title: İstemciler İçin UI Otomasyon Denetim Düzenleri
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, control patterns for clients
- control patterns, UI Automation clients
ms.assetid: 571561d8-5f49-43a9-a054-87735194e013
ms.openlocfilehash: 2f6fccf828552fbd4102c16bde7ffbaf394b69ac
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68400684"
---
# <a name="ui-automation-control-patterns-for-clients"></a>İstemciler İçin UI Otomasyon Denetim Düzenleri
> [!NOTE]
>  Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir. Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu genel bakış, UI Otomasyonu istemcilerinin denetim desenlerini tanıtır. UI Otomasyon istemcisinin, [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)]ile ilgili bilgilere erişmek için denetim desenlerini nasıl kullanabileceği hakkında bilgi içerir.  
  
 Denetim desenleri denetim türünden veya denetimin görünümünün bağımsız olarak bir denetimin işlevini kategorilere ayırma ve kullanıma sunma için bir yol sağlar. UI Otomasyonu istemcileri, hangi denetim <xref:System.Windows.Automation.AutomationElement> desenlerinin desteklendiğini ve denetimin davranışından emin olduğunu tespit etmek için bir öğesini inceleyebilir.  
  
 Denetim desenlerinin tüm listesi için bkz. [UI Otomasyonu Denetim desenlerine genel bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
<a name="uiautomation_getting_control_patterns"></a>   
## <a name="getting-control-patterns"></a>Denetim desenleri alma  
 İstemciler, ya <xref:System.Windows.Automation.AutomationElement> <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A?displayProperty=nameWithType> da<xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A?displayProperty=nameWithType>çağırarak bir denetim modelini alır.  
  
 <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> İstemciler, `IsPatternAvailable` <xref:System.Windows.Automation.AutomationElement.IsTextPatternAvailableProperty>üzerinde birdesenveyadesengrubunundesteklenipdesteklenmediğinianlamakiçinyönteminiveyabağımsızbirözelliği(örneğin,)kullanabilir.<xref:System.Windows.Automation.AutomationElement> Ancak, desteklenen özellikleri kontrol etmek ve daha az işlem arası çağrıya neden olduğundan denetim modelini almak `null` yerine, bir başvuru için denetim modelini ve test almayı denemek daha etkilidir.  
  
 Aşağıdaki örnek, <xref:System.Windows.Automation.TextPattern> <xref:System.Windows.Automation.AutomationElement>öğesinden bir denetim deseninin nasıl alınacağını gösterir.  
  
 [!code-csharp[UIATextPattern_snip#1037](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#1037)]  
  
<a name="uiautomation_properties_on_control_patterns"></a>   
## <a name="retrieving-properties-on-control-patterns"></a>Denetim desenlerinde özellikleri alma  
 İstemciler, <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType> veya <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType> öğesini çağırarak ve uygun bir türe döndürülen nesneyi kaldırarak denetim desenlerindeki özellik değerlerini alabilir. Özellikler hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] daha fazla bilgi için bkz. [istemciler için UI Otomasyon özellikleri](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
 `GetPropertyValue` Yöntemlerin yanı sıra, bir düzendeki [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özelliklere erişmek için ortak dil çalışma zamanı (CLR) erişimcileri aracılığıyla özellik değerleri alınabilir.  
  
<a name="uiautomation_with_variable_patterns"></a>   
## <a name="controls-with-variable-patterns"></a>Değişken desenleri olan denetimler  
 Bazı denetim türleri, durumlarına veya denetimin kullanılmakta olmasına bağlı olarak farklı desenleri destekler. Değişken desenleri olan denetim örnekleri, liste görünümleridir (küçük resimler, Kutucuklar, simgeler, liste, Ayrıntılar), [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] grafikler (pasta, çizgi, çubuk, formül içeren hücre değeri), [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)]belge alanı (normal, Web düzeni, ana hat, yazdırma düzeni, yazdırma Önizleme) ve [!INCLUDE[TLA#tla_wmp](../../../includes/tlasharptla-wmp-md.md)] kaplamalar.  
  
 Özel denetim türlerini uygulayan denetimler, işlevlerini temsil etmek için gereken herhangi bir denetim deseni kümesine sahip olabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu Denetim Desenleri](../../../docs/framework/ui-automation/ui-automation-control-patterns.md)
- [UI Otomasyonu Metin Deseni](../../../docs/framework/ui-automation/ui-automation-text-pattern.md)
- [UI Otomasyonu Kullanarak Denetim Çağırma](../../../docs/framework/ui-automation/invoke-a-control-using-ui-automation.md)
- [UI Otomasyonunu Kullanarak Onay Kutusunun Değiştir Durumunu Alma](../../../docs/framework/ui-automation/get-the-toggle-state-of-a-check-box-using-ui-automation.md)
- [UI Otomasyonu İstemcileri İçin Denetim Düzeni Eşlemesi](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)
- [TextModel metin ekleme örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InsertText)
- [TextModel arama ve seçim örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/FindText)
- [Invokemodel, ExpandCollapsePattern ve Togglemodel örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InvokePattern)
