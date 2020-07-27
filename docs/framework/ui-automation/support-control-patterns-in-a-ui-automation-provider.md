---
title: UI Otomasyon Sağlayıcısında Denetim Düzenleri Desteği
description: İstemci uygulamalarının denetimleri ve onlardan veri almasını sağlamak için bir UI Otomasyon sağlayıcısında destek denetim desenlerinin nasıl uygulanacağını anlayın.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- control patterns, supporting in UI Automation provider
- UI Automation, supporting control patterns in provider
ms.assetid: 0d635c35-ffa8-4dc8-bbc9-12fcd5445776
ms.openlocfilehash: 82300499520be6b820b361ebdeb56bbf3716afab
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87163505"
---
# <a name="support-control-patterns-in-a-ui-automation-provider"></a>UI Otomasyon Sağlayıcısında Denetim Düzenleri Desteği

> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).

Bu konu, bir kullanıcı arabirimi Otomasyon sağlayıcısında bir veya daha fazla denetim desenlerinin nasıl uygulanacağını gösterir. böylece, istemci uygulamaların denetimleri işleyebilir ve onlardan veri alabilir.

## <a name="support-control-patterns"></a>Destek Denetim desenleri

1. Öğesinin, gibi desteklemesi gereken denetim desenleri için uygun arabirimleri uygulayın <xref:System.Windows.Automation.Provider.IInvokeProvider> <xref:System.Windows.Automation.InvokePattern> .

2. Uygulamanızda her denetim arabiriminin uygulamasını içeren nesneyi döndürün<xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A?displayProperty=nameWithType>

## <a name="example"></a>Örnek

Aşağıdaki örnek, <xref:System.Windows.Automation.Provider.ISelectionProvider> tek seçimli bir özel liste kutusu için uygulamasının bir uygulamasını gösterir. Üç özellik döndürür ve şu anda seçili öğeyi alır.

[!code-csharp[UIAFragmentProvider_snip#119](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListPattern.cs#119)]
[!code-vb[UIAFragmentProvider_snip#119](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListPattern.vb#119)]

## <a name="example"></a>Örnek

Aşağıdaki örnek, uygulayan sınıfını döndüren uygulamasının bir uygulamasını gösterir <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A> <xref:System.Windows.Automation.Provider.ISelectionProvider> . Çoğu liste kutusu denetimleri diğer desenleri de destekleyecektir, ancak bu örnekte, `Nothing` diğer tüm desen tanımlayıcıları için bir null başvurusu (Microsoft Visual Basic .net 'te) döndürülür.

[!code-csharp[UIAFragmentProvider_snip#120](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListFragment.cs#120)]
[!code-vb[UIAFragmentProvider_snip#120](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListFragment.vb#120)]

## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyon Sağlayıcılara Genel Bakış](ui-automation-providers-overview.md)
- [Sunucu Tarafı UI Otomasyonu Sağlayıcıyı Uygulama](server-side-ui-automation-provider-implementation.md)
