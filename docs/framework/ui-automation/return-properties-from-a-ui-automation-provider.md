---
title: UI Otomasyon Sağlayıcı Dönüş Özellikleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- providers, UI Automation, returning properties
- properties, returned by UI Automation providers
- UI Automation, providers returning properties
ms.assetid: 5eba950e-b9e1-48eb-ab8e-b69db76bf589
ms.openlocfilehash: 742c84bf0e8e9413c83048bce32f29b899c1d339
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446865"
---
# <a name="return-properties-from-a-ui-automation-provider"></a>UI Otomasyon Sağlayıcı Dönüş Özellikleri
> [!NOTE]
> Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu, bir UI Otomasyon sağlayıcısının bir öğenin özelliklerini istemci uygulamalarına nasıl döndüregösterdiğini gösteren örnek kodu içerir.  
  
 Açıkça desteklenmeyen herhangi bir özellik için, sağlayıcının `null` döndürmesi gerekir (`Nothing` Visual Basic). Bu, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özelliği, ana bilgisayar pencere sağlayıcısı gibi başka bir kaynaktan almayı dener.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[UIAFragmentProvider_snip#117](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListFragment.cs#117)]
 [!code-vb[UIAFragmentProvider_snip#117](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListFragment.vb#117)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu Sağlayıcılara Genel Bakış](ui-automation-providers-overview.md)
- [Sunucu Tarafı UI Otomasyonu Sağlayıcısı Uygulama](server-side-ui-automation-provider-implementation.md)
