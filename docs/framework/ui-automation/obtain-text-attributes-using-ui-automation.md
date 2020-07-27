---
title: UI Otomasyonu Kullanarak Metin Özniteliklerini Alma
description: UI Otomasyonu kullanarak metin özniteliklerini edinmeyi öğrenin. Metin aralığından metin özniteliklerini alan bir kod örneğine bakın.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting, text attributes
- UI Automation, getting text attributes
- text attributes, getting
ms.assetid: fdefc6c3-b836-4cfe-8dec-1484bfdc5551
ms.openlocfilehash: b48f773e27088ba4b33ad01b299d77a0992a9159
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168004"
---
# <a name="obtain-text-attributes-using-ui-automation"></a>UI Otomasyonu Kullanarak Metin Özniteliklerini Alma
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu başlığı altında, [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] bir metin aralığından metin özniteliklerini elde etmek için nasıl kullanılacağı gösterilmektedir. Bir metin aralığı, bir belge içinde giriş işaretinin (veya seçimi kaldırma) geçerli konumuna, bitişik metin seçimine, ayrık metin seçimlerinin bir koleksiyonuna veya bir belgenin tüm metinsel içeriğine karşılık gelir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, <xref:System.Windows.Automation.TextPattern.FontNameAttribute> bir metin aralığından nasıl alınacağını gösterir.  
  
 [!code-csharp[UIATextPattern_snip#StartTarget](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#starttarget)]
 [!code-vb[UIATextPattern_snip#StartTarget](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#starttarget)]  
[!code-csharp[UIATextPattern_snip#GetTextElement](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#gettextelement)]
[!code-vb[UIATextPattern_snip#GetTextElement](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#gettextelement)]  
[!code-csharp[UIATextPattern_snip#FontName](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#fontname)]
[!code-vb[UIATextPattern_snip#FontName](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#fontname)]  
  
 <xref:System.Windows.Automation.TextPattern>Sınıf ile birlikte bulunan denetim deseninin <xref:System.Windows.Automation.Text.TextPatternRange> temel metin öznitelikleri, özellikleri ve yöntemleri desteklenir. Veya tarafından desteklenmeyen denetime özgü işlevsellik için <xref:System.Windows.Automation.TextPattern> <xref:System.Windows.Automation.Text.TextPatternRange> <xref:System.Windows.Automation.AutomationElement> , sınıfı, Kullanıcı Arabirimi Otomasyonu istemcisinin karşılık gelen yerel nesne modeline erişmesi için yöntemler sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyon TextPattern Öğesine Genel Bakış](ui-automation-textpattern-overview.md)
- [UI Otomasyonu Kullanarak Metin Kutusuna İçerik Ekleme](add-content-to-a-text-box-using-ui-automation.md)
- [UI Otomasyonunu Kullanarak Metin Bulma ve Vurgulama](find-and-highlight-text-using-ui-automation.md)
- [UI Otomasyon Denetim Düzenlerine Genel Bakış](ui-automation-control-patterns-overview.md)
- [İstemciler İçin UI Otomasyon Denetim Düzenleri](ui-automation-control-patterns-for-clients.md)
- [UI Otomasyonu Kullanarak Karışık Metin Özniteliği Ayrıntılarını Alma](obtain-mixed-text-attribute-details-using-ui-automation.md)
