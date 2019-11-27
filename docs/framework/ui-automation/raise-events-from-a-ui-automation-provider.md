---
title: UI Otomasyon Sağlayıcıda Olay Tetikleme
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, raising events
- raising UI Automation events
ms.assetid: 9fe2f01b-f7d8-49a8-a185-d4472b9976c0
ms.openlocfilehash: 1a940cbb99ac068dad6c366520a544035270da3e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446880"
---
# <a name="raise-events-from-a-ui-automation-provider"></a>UI Otomasyon Sağlayıcıda Olay Tetikleme
> [!NOTE]
> Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu, bir UI Otomasyon sağlayıcısından bir olayın nasıl oluşturulacağını gösteren örnek kodu içerir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olayı özel bir düğme denetimi uygulamasında tetiklenir. Uygulama, bir Kullanıcı Arabirimi Otomasyonu istemci uygulamasının bir düğme tıklamalarını benzetimini sağlar.  
  
 Gereksiz işleme engel olmak için örnek, olayların yapılıp yapılmayacağını görmek için <xref:System.Windows.Automation.Provider.AutomationInteropProvider.ClientsAreListening%2A> denetler.  
  
 [!code-csharp[UIAProvider_snip#150](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAProvider_snip/CSharp/FragmentRoot.cs#150)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu Sağlayıcılara Genel Bakış](ui-automation-providers-overview.md)
