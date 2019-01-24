---
title: UI Otomasyonu Kullanarak Metin Özniteliklerini Alma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting, text attributes
- UI Automation, getting text attributes
- text attributes, getting
ms.assetid: fdefc6c3-b836-4cfe-8dec-1484bfdc5551
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 62abb18e9ef43e78c0e908b94f3ed9fc69861c7b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54512586"
---
# <a name="obtain-text-attributes-using-ui-automation"></a>UI Otomasyonu Kullanarak Metin Özniteliklerini Alma
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu nasıl kullanılacağını gösterir [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] bir metin aralığındaki metin özniteliklerini alma için. Metin aralığı bir belge içinde metin, ayrık metin seçimi koleksiyonunu veya tüm metin içeriği belgenin bir aralık seçimi giriş işaretini (veya bozuk seçimi) geçerli konumuna karşılık gelebilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde nasıl alınacağı gösterilmektedir <xref:System.Windows.Automation.TextPattern.FontNameAttribute> metin aralığından.  
  
 [!code-csharp[UIATextPattern_snip#StartTarget](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#starttarget)]
 [!code-vb[UIATextPattern_snip#StartTarget](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#starttarget)]  
[!code-csharp[UIATextPattern_snip#GetTextElement](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#gettextelement)]
[!code-vb[UIATextPattern_snip#GetTextElement](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#gettextelement)]  
[!code-csharp[UIATextPattern_snip#FontName](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#fontname)]
[!code-vb[UIATextPattern_snip#FontName](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#fontname)]  
  
 <xref:System.Windows.Automation.TextPattern> Dağıtımınızla birlikte denetim düzeni <xref:System.Windows.Automation.Text.TextPatternRange> sınıfı, temel metin özniteliklerini destekler, özellikleri ve yöntemleri. Tarafından desteklenmeyen özel denetim işlevselliği için <xref:System.Windows.Automation.TextPattern> veya <xref:System.Windows.Automation.Text.TextPatternRange> <xref:System.Windows.Automation.AutomationElement>, sınıfı karşılık gelen yerel nesne modeli erişmek UI Otomasyonu istemci için yöntemler sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [UI Otomasyonu TextPattern Öğesine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-textpattern-overview.md)
- [UI Otomasyonu Kullanarak Metin Kutusuna İçerik Ekleme](../../../docs/framework/ui-automation/add-content-to-a-text-box-using-ui-automation.md)
- [UI Otomasyonunu Kullanarak Metin Bulma ve Vurgulama](../../../docs/framework/ui-automation/find-and-highlight-text-using-ui-automation.md)
- [UI Otomasyonu Denetim Desenlerine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [İstemciler İçin UI Otomasyonu Denetim Düzenleri](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [UI Otomasyonu Kullanarak Karışık Metin Özniteliği Ayrıntılarını Alma](../../../docs/framework/ui-automation/obtain-mixed-text-attribute-details-using-ui-automation.md)
