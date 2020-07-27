---
title: UI Otomasyonu Parça Sağlayıcıyıda Gezinmeyi Etkinleştirme
description: Bir parçadaki bir öğe için UI Otomasyon sağlayıcısında gezintiyi nasıl etkinleştireceğinizi gösteren bir örnek okuyun.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, enabling navigation in provider
- navigation, enabling in UI Automation provider
ms.assetid: 3cb6092a-58c9-4ca0-84a5-0e54d5d00a0d
ms.openlocfilehash: bf9e43e9d70b9191fba93e5efa4eae544196c735
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168493"
---
# <a name="enable-navigation-in-a-ui-automation-fragment-provider"></a>UI Otomasyonu Parça Sağlayıcıyıda Gezinmeyi Etkinleştirme
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu, bir parçadaki bir öğe için UI Otomasyon sağlayıcısında gezintiyi nasıl etkinleştireceğinizi gösteren örnek kodu içerir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kod, <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A> liste içindeki bir liste öğesi için uygular. Üst öğe liste kutusu öğesidir ve eşdüzey öğeler liste koleksiyonundaki diğer öğelerdir. Yöntemi, `null` `Nothing` geçerli olmayan yönler için (Visual Basic olarak) döndürür; bu durumda, <xref:System.Windows.Automation.Provider.NavigateDirection.FirstChild> ve <xref:System.Windows.Automation.Provider.NavigateDirection.LastChild> öğesi alt öğeye sahip değil.  
  
 [!code-csharp[UIAFragmentProvider_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListItemFragment.cs#103)]
 [!code-vb[UIAFragmentProvider_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListItemFragment.vb#103)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyon Sağlayıcılara Genel Bakış](ui-automation-providers-overview.md)
- [Sunucu Tarafı UI Otomasyonu Sağlayıcıyı Uygulama](server-side-ui-automation-provider-implementation.md)
