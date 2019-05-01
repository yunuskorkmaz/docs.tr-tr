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
ms.openlocfilehash: f3d5776441f1d4848adbb0a5f9435274f118a0da
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61983001"
---
# <a name="return-properties-from-a-ui-automation-provider"></a>UI Otomasyon Sağlayıcı Dönüş Özellikleri
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu nasıl öğenin özelliklerini istemci uygulamaları için UI Otomasyon sağlayıcısında döndürebilir gösteren örnek kodu içerir.  
  
 Bu açıkça desteklemiyor herhangi bir özelliği için sağlayıcı döndürmelidir `null` (`Nothing` Visual Basic'te). Bu, sağlar [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ana penceresi sağlayıcısı gibi başka bir kaynaktan özellik almayı dener.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[UIAFragmentProvider_snip#117](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListFragment.cs#117)]
 [!code-vb[UIAFragmentProvider_snip#117](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListFragment.vb#117)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu Sağlayıcılara Genel Bakış](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)
- [Sunucu Tarafı UI Otomasyonu Sağlayıcısı Uygulama](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)
