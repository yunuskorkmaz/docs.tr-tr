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
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 8f9b43a2c2d58df77d739baf897ddd4562523d13
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50181036"
---
# <a name="enable-navigation-in-a-ui-automation-fragment-provider"></a>UI Otomasyonu Parça Sağlayıcıyıda Gezinmeyi Etkinleştirme
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu içinde bir parçası olan bir öğe için UI Otomasyonu sağlayıcıyıda gezinmeyi etkinleştirme gösteren kod örneği içerir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği uygulayan <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A> bir listede bir liste öğesi için. Liste kutusu öğesinin üst öğedir ve diğer öğeleri listesi koleksiyonundaki eşdüzey öğeler. Yöntem döndürür `null` (`Nothing` Visual Basic'te) için geçerli olmayan yönergeleri; Bu durumda, <xref:System.Windows.Automation.Provider.NavigateDirection.FirstChild> ve <xref:System.Windows.Automation.Provider.NavigateDirection.LastChild>, öğenin alt öğesi yok.  
  
 [!code-csharp[UIAFragmentProvider_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListItemFragment.cs#103)]
 [!code-vb[UIAFragmentProvider_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListItemFragment.vb#103)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UI Otomasyonu Sağlayıcılara Genel Bakış](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)  
 [Sunucu Tarafı UI Otomasyonu Sağlayıcısı Uygulama](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)
