---
title: UI Otomasyonu Kullanarak Karışık Metin Özniteliği Ayrıntılarını Alma
description: .NET API 'nin System. Windows. Automation ad alanındaki yönetilen UI Otomasyon sınıflarını kullanarak karışık metin özniteliği ayrıntılarını alın.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d0e4c005-abd1-42bb-92a4-5faf87097311
ms.openlocfilehash: 111d110be9365c4a58f2bd2b033c1ff4e3a6a95d
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903863"
---
# <a name="obtain-mixed-text-attribute-details-using-ui-automation"></a>UI Otomasyonu Kullanarak Karışık Metin Özniteliği Ayrıntılarını Alma
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konuda [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] , birden çok öznitelik değerini kapsayan bir metin aralığından metin özniteliği ayrıntıları elde etmek için nasıl kullanılacağı gösterilmektedir. Bir metin aralığı, bir belge içinde giriş işaretinin (veya seçimi kaldırma) geçerli konumuna, bitişik metin seçimine, ayrık metin seçimlerinin bir koleksiyonuna veya bir belgenin tüm metinsel içeriğine karşılık gelir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, <xref:System.Windows.Automation.TextPattern.FontNameAttribute> bir nesne döndüren bir metin aralığından nasıl alınacağını gösterir <xref:System.Windows.Automation.Text.TextPatternRange.GetAttributeValue%2A> <xref:System.Windows.Automation.TextPattern.MixedAttributeValue> .  
  
[!code-csharp[FindText#RetrieveMixedAttributes](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#retrievemixedattributes)]
[!code-vb[FindText#RetrieveMixedAttributes](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#retrievemixedattributes)]  
  
 <xref:System.Windows.Automation.TextPattern>Sınıf ile birlikte bulunan denetim deseninin <xref:System.Windows.Automation.Text.TextPatternRange> temel metin öznitelikleri, özellikleri ve yöntemleri desteklenir. Veya tarafından desteklenmeyen denetime özgü işlevsellik için <xref:System.Windows.Automation.TextPattern> <xref:System.Windows.Automation.Text.TextPatternRange> , <xref:System.Windows.Automation.AutomationElement> sınıfı, Kullanıcı Arabirimi Otomasyonu istemcisinin karşılık gelen yerel nesne modeline erişmesi için yöntemler sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyon TextPattern Öğesine Genel Bakış](ui-automation-textpattern-overview.md)
- [UI Otomasyonu Kullanarak Metin Kutusuna İçerik Ekleme](add-content-to-a-text-box-using-ui-automation.md)
- [UI Otomasyonunu Kullanarak Metin Bulma ve Vurgulama](find-and-highlight-text-using-ui-automation.md)
- [UI Otomasyonu Denetim Desenlerine Genel Bakış](ui-automation-control-patterns-overview.md)
- [İstemciler İçin UI Otomasyonu Denetim Düzenleri](ui-automation-control-patterns-for-clients.md)
- [UI Otomasyonu Kullanarak Metin Özniteliklerini Alma](obtain-text-attributes-using-ui-automation.md)
