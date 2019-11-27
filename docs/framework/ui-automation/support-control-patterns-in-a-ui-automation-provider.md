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
ms.openlocfilehash: 1200ebd42884220d2611729b87f4bf51e7a903a1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446823"
---
# <a name="support-control-patterns-in-a-ui-automation-provider"></a>UI Otomasyon Sağlayıcısında Denetim Düzenleri Desteği

> [!NOTE]
> Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).

Bu konu, bir kullanıcı arabirimi Otomasyon sağlayıcısında bir veya daha fazla denetim desenlerinin nasıl uygulanacağını gösterir. böylece, istemci uygulamaların denetimleri işleyebilir ve onlardan veri alabilir.

## <a name="support-control-patterns"></a>Destek Denetim desenleri

1. Öğenin desteklemesi gereken denetim desenleri için, <xref:System.Windows.Automation.InvokePattern>için <xref:System.Windows.Automation.Provider.IInvokeProvider> gibi uygun arabirimleri uygulayın.

2. <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A?displayProperty=nameWithType> uygulamanızda her denetim arabiriminin uygulamanızı içeren nesneyi döndürün

## <a name="example"></a>Örnek

Aşağıdaki örnek, tek seçimli bir özel liste kutusu için <xref:System.Windows.Automation.Provider.ISelectionProvider> bir uygulamasını gösterir. Üç özellik döndürür ve şu anda seçili öğeyi alır.

[!code-csharp[UIAFragmentProvider_snip#119](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListPattern.cs#119)]
[!code-vb[UIAFragmentProvider_snip#119](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListPattern.vb#119)]

## <a name="example"></a>Örnek

Aşağıdaki örnek, <xref:System.Windows.Automation.Provider.ISelectionProvider>uygulayan sınıfını döndüren <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A> bir uygulamasını gösterir. Çoğu liste kutusu denetimleri diğer desenleri de destekleyecektir, ancak bu örnekte, diğer tüm desen tanımlayıcıları için bir null başvurusu (Microsoft Visual Basic .NET 'te`Nothing`) döndürülür.

[!code-csharp[UIAFragmentProvider_snip#120](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListFragment.cs#120)]
[!code-vb[UIAFragmentProvider_snip#120](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListFragment.vb#120)]

## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu Sağlayıcılara Genel Bakış](ui-automation-providers-overview.md)
- [Sunucu Tarafı UI Otomasyonu Sağlayıcısı Uygulama](server-side-ui-automation-provider-implementation.md)
