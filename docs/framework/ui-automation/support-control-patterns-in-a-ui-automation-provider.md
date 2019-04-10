---
title: UI Otomasyon Sağlayıcısında Denetim Düzenleri Desteği
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- control patterns, supporting in UI Automation provider
- UI Automation, supporting control patterns in provider
ms.assetid: 0d635c35-ffa8-4dc8-bbc9-12fcd5445776
ms.openlocfilehash: 65ec0f85bf0a63d0051ff9491623a65abee7a05c
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59336687"
---
# <a name="support-control-patterns-in-a-ui-automation-provider"></a>UI Otomasyon Sağlayıcısında Denetim Düzenleri Desteği
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konuda, böylece istemci uygulamaları denetimleri işlemenizi ve onlardan veri almak, UI Otomasyon sağlayıcısında bir veya daha fazla denetim desenlerini uygulamak gösterilmektedir.  
  
### <a name="support-control-patterns"></a>Denetim düzenleri desteği  
  
1. Öğe, gibi desteklemelidir denetim desenleri için uygun arabirimi uygulayan <xref:System.Windows.Automation.Provider.IInvokeProvider> için <xref:System.Windows.Automation.InvokePattern>.  
  
2. Uygulamanızı her denetim arabiriminin uygulamanızda içeren nesneyi döndürür <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A?displayProperty=nameWithType>  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir uygulamasını gösterir <xref:System.Windows.Automation.Provider.ISelectionProvider> tek seçimli özel liste kutusu için. Bu üç özellik döndürür ve şu anda seçili öğeyi alır.  
  
 [!code-csharp[UIAFragmentProvider_snip#119](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListPattern.cs#119)]
 [!code-vb[UIAFragmentProvider_snip#119](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListPattern.vb#119)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir uygulamasını gösterir <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A> uygulayan sınıf döndüren <xref:System.Windows.Automation.Provider.ISelectionProvider>. Çoğu liste kutusu denetimleri diğer desenleri de ancak bu örnekte bir null başvuru destekleyecektir (`Nothing` Microsoft Visual Basic. NET'te) için diğer tüm düzeni tanımlayıcıları döndürülür.  
  
 [!code-csharp[UIAFragmentProvider_snip#120](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListFragment.cs#120)]
 [!code-vb[UIAFragmentProvider_snip#120](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListFragment.vb#120)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyon Sağlayıcılara Genel Bakış](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)
- [Sunucu Tarafı UI Otomasyonu Sağlayıcıyı Uygulama](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)
