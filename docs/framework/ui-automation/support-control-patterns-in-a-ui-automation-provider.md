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
ms.openlocfilehash: 67f37dfe1fe63f2130646cb227fec855ccc7bf75
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71042599"
---
# <a name="support-control-patterns-in-a-ui-automation-provider"></a>UI Otomasyon Sağlayıcısında Denetim Düzenleri Desteği

> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir. Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).

Bu konu, bir kullanıcı arabirimi Otomasyon sağlayıcısında bir veya daha fazla denetim desenlerinin nasıl uygulanacağını gösterir. böylece, istemci uygulamaların denetimleri işleyebilir ve onlardan veri alabilir.

## <a name="support-control-patterns"></a>Destek Denetim desenleri

1. Öğesinin, <xref:System.Windows.Automation.Provider.IInvokeProvider> <xref:System.Windows.Automation.InvokePattern>gibi desteklemesi gereken denetim desenleri için uygun arabirimleri uygulayın.

2. Uygulamanızda her denetim arabiriminin uygulamasını içeren nesneyi döndürün<xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A?displayProperty=nameWithType>

## <a name="example"></a>Örnek

Aşağıdaki örnek, tek seçimli bir özel <xref:System.Windows.Automation.Provider.ISelectionProvider> liste kutusu için uygulamasının bir uygulamasını gösterir. Üç özellik döndürür ve şu anda seçili öğeyi alır.

[!code-csharp[UIAFragmentProvider_snip#119](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListPattern.cs#119)]
[!code-vb[UIAFragmentProvider_snip#119](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListPattern.vb#119)]

## <a name="example"></a>Örnek

Aşağıdaki örnek, uygulayan <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A> <xref:System.Windows.Automation.Provider.ISelectionProvider>sınıfını döndüren uygulamasının bir uygulamasını gösterir. Çoğu liste kutusu denetimleri diğer desenleri de destekleyecektir, ancak bu örnekte, diğer tüm desen tanımlayıcıları için`Nothing` bir null başvurusu (Microsoft Visual Basic .net 'te) döndürülür.

[!code-csharp[UIAFragmentProvider_snip#120](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListFragment.cs#120)]
[!code-vb[UIAFragmentProvider_snip#120](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListFragment.vb#120)]

## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu Sağlayıcılara Genel Bakış](ui-automation-providers-overview.md)
- [Sunucu Tarafı UI Otomasyonu Sağlayıcısı Uygulama](server-side-ui-automation-provider-implementation.md)
