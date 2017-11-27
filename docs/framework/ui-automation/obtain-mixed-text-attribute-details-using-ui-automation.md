---
title: "UI Otomasyonu Kullanarak Karışık Metin Özniteliği Ayrıntılarını Alma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: d0e4c005-abd1-42bb-92a4-5faf87097311
caps.latest.revision: "11"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 0588ec764aabf5aa0e88477838d949a294f3064e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="obtain-mixed-text-attribute-details-using-ui-automation"></a>UI Otomasyonu Kullanarak Karışık Metin Özniteliği Ayrıntılarını Alma
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konuda nasıl kullanılacağını gösterir [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] metin özniteliği ayrıntılarını birden çok öznitelik değerleri yayılan bir metin aralığından elde edilir. Bir metin aralığını geçerli konumunu şapka (veya bozuk seçimi) için bir belge içinde metin, ayrık metin seçimleri koleksiyonu veya bir belgenin tüm metin içeriği bitişik seçimi karşılık gelebilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde elde etme gösterilmektedir <xref:System.Windows.Automation.TextPattern.FontNameAttribute> metin aralığından nerede <xref:System.Windows.Automation.Text.TextPatternRange.GetAttributeValue%2A> döndürür bir <xref:System.Windows.Automation.TextPattern.MixedAttributeValue> nesnesi.  
  
 [!code-csharp[FindText#RetrieveMixedAttributes](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#retrievemixedattributes)]
 [!code-vb[FindText#RetrieveMixedAttributes](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#retrievemixedattributes)]  
  
 <xref:System.Windows.Automation.TextPattern> Dağıtımınızla birlikte denetim düzeni <xref:System.Windows.Automation.Text.TextPatternRange> sınıfı, temel metin özniteliklerini destekler, özellikleri ve yöntemleri. Tarafından desteklenmeyen özel denetim işlevselliği için <xref:System.Windows.Automation.TextPattern> veya <xref:System.Windows.Automation.Text.TextPatternRange>, <xref:System.Windows.Automation.AutomationElement> sınıfı, karşılık gelen yerel nesne modeline erişmek UI otomasyon istemci için yöntemleri sağlar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UI Otomasyon textpattern öğesine genel bakış](../../../docs/framework/ui-automation/ui-automation-textpattern-overview.md)  
 [UI Otomasyonu kullanarak metin kutusuna içerik ekleme](../../../docs/framework/ui-automation/add-content-to-a-text-box-using-ui-automation.md)  
 [UI Otomasyonu kullanarak metin bulma ve vurgulama](../../../docs/framework/ui-automation/find-and-highlight-text-using-ui-automation.md)  
 [UI Otomasyon denetim düzenlerine genel bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [İstemciler için UI Otomasyon denetim düzenleri](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [UI Otomasyonu kullanarak metin özniteliklerini alma](../../../docs/framework/ui-automation/obtain-text-attributes-using-ui-automation.md)
