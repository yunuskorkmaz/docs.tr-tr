---
title: UI Otomasyonu Parça Sağlayıcıyıda Gezinmeyi Etkinleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, enabling navigation in provider
- navigation, enabling in UI Automation provider
ms.assetid: 3cb6092a-58c9-4ca0-84a5-0e54d5d00a0d
ms.openlocfilehash: e97494e01a81ad75820cd3cffa51b5a508152355
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59176000"
---
# <a name="enable-navigation-in-a-ui-automation-fragment-provider"></a>UI Otomasyonu Parça Sağlayıcıyıda Gezinmeyi Etkinleştirme
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu içinde bir parçası olan bir öğe için UI Otomasyonu sağlayıcıyıda gezinmeyi etkinleştirme gösteren kod örneği içerir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği uygulayan <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A> bir listede bir liste öğesi için. Liste kutusu öğesinin üst öğedir ve diğer öğeleri listesi koleksiyonundaki eşdüzey öğeler. Yöntem döndürür `null` (`Nothing` Visual Basic'te) için geçerli olmayan yönergeleri; Bu durumda, <xref:System.Windows.Automation.Provider.NavigateDirection.FirstChild> ve <xref:System.Windows.Automation.Provider.NavigateDirection.LastChild>, öğenin alt öğesi yok.  
  
 [!code-csharp[UIAFragmentProvider_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListItemFragment.cs#103)]
 [!code-vb[UIAFragmentProvider_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListItemFragment.vb#103)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu Sağlayıcılara Genel Bakış](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)
- [Sunucu Tarafı UI Otomasyonu Sağlayıcısı Uygulama](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)
