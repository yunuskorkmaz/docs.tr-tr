---
title: UI Otomasyonu Kullanarak Karışık Metin Özniteliği Ayrıntılarını Alma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d0e4c005-abd1-42bb-92a4-5faf87097311
ms.openlocfilehash: 13ebc6aefe925ecefe48a9b0fa8cf7a6ecd3c454
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71042947"
---
# <a name="obtain-mixed-text-attribute-details-using-ui-automation"></a>UI Otomasyonu Kullanarak Karışık Metin Özniteliği Ayrıntılarını Alma
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir. Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konuda, birden çok öznitelik [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] değerini kapsayan bir metin aralığından metin özniteliği ayrıntıları elde etmek için nasıl kullanılacağı gösterilmektedir. Bir metin aralığı, bir belge içinde giriş işaretinin (veya seçimi kaldırma) geçerli konumuna, bitişik metin seçimine, ayrık metin seçimlerinin bir koleksiyonuna veya bir belgenin tüm metinsel içeriğine karşılık gelir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, <xref:System.Windows.Automation.TextPattern.FontNameAttribute> bir <xref:System.Windows.Automation.TextPattern.MixedAttributeValue> nesne <xref:System.Windows.Automation.Text.TextPatternRange.GetAttributeValue%2A> döndüren bir metin aralığından nasıl alınacağını gösterir.  
  
[!code-csharp[FindText#RetrieveMixedAttributes](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#retrievemixedattributes)]
[!code-vb[FindText#RetrieveMixedAttributes](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#retrievemixedattributes)]  
  
 Sınıf ile birlikte bulunan <xref:System.Windows.Automation.TextPattern> denetim deseninin temel metin öznitelikleri, özellikleri ve <xref:System.Windows.Automation.Text.TextPatternRange> yöntemleri desteklenir. Veya <xref:System.Windows.Automation.TextPattern> <xref:System.Windows.Automation.AutomationElement> tarafından desteklenmeyen denetime özgü işlevsellik için, sınıfı, Kullanıcı Arabirimi Otomasyonu istemcisinin karşılık gelen yerel nesne modeline erişmesi için yöntemler sağlar. <xref:System.Windows.Automation.Text.TextPatternRange>  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu TextPattern Öğesine Genel Bakış](ui-automation-textpattern-overview.md)
- [UI Otomasyonu Kullanarak Metin Kutusuna İçerik Ekleme](add-content-to-a-text-box-using-ui-automation.md)
- [UI Otomasyonunu Kullanarak Metin Bulma ve Vurgulama](find-and-highlight-text-using-ui-automation.md)
- [UI Otomasyonu Denetim Desenlerine Genel Bakış](ui-automation-control-patterns-overview.md)
- [İstemciler İçin UI Otomasyonu Denetim Düzenleri](ui-automation-control-patterns-for-clients.md)
- [UI Otomasyonu Kullanarak Metin Özniteliklerini Alma](obtain-text-attributes-using-ui-automation.md)
