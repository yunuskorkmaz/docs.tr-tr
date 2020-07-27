---
title: UI Otomasyonunu Kullanarak Çapraz Geçiş Yapma
description: Microsoft UI Otomasyonu kullanarak bir belgenin metin içeriğinin nasıl gezilmesine ilişkin bir örnek olan TextUnit artışlarına bakın.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, traversing text
- text, traversing
- traversing text
ms.assetid: 3ddb3b7b-1d6b-4dba-8678-5a68e868aadb
ms.openlocfilehash: 0b4269d043fd6cd0cc5da9825714aab4ead701f9
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168092"
---
# <a name="traverse-text-using-ui-automation"></a>UI Otomasyonunu Kullanarak Çapraz Geçiş Yapma
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu başlığı altında [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] , bir belgenin metin içeriğini artışlarla çapraz geçiş için nasıl kullanılacağı gösterilmektedir <xref:System.Windows.Automation.Text.TextUnit> .  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde, bir UI Otomasyon metin sağlayıcısı içeriğinin nasıl gezeceği gösterilmektedir. <xref:System.Windows.Automation.Text.TextPatternRange.Move%2A>Yöntemi <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> ' <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> a ait ve uç noktalarını taşıdıkça <xref:System.Windows.Automation.Text.TextPatternRange> . Bu metin aralığı genellikle metin ekleme noktasını temsil eden bir bozuk aralığıdır.  
  
> [!NOTE]
> Yalnızca metin tabanlı katıştırılmış nesneler metin akışının parçası olarak kabul edildiğinden, resimler gibi katıştırılmış nesneler `Move` veya dönüş değeri etkilenmez.  
  
[!code-csharp[FindText#StartApp](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#startapp)]
[!code-vb[FindText#StartApp](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#startapp)]  
[!code-csharp[FindText#FindTextProvider](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#findtextprovider)]
[!code-vb[FindText#FindTextProvider](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#findtextprovider)]  
[!code-csharp[FindText#Navigate](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#navigate)]
[!code-vb[FindText#Navigate](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#navigate)]  
  
 Kullanılan herhangi bir yöntem, <xref:System.Windows.Automation.Text.TextUnit> <xref:System.Windows.Automation.Text.TextUnit> verilen <xref:System.Windows.Automation.Text.TextUnit> Denetim tarafından desteklenmiyorsa, desteklenen bir sonraki en büyük öğesine ertelenecek.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyon TextPattern Öğesine Genel Bakış](ui-automation-textpattern-overview.md)
- [UI Otomasyonu Kullanarak Metin Kutusuna İçerik Ekleme](add-content-to-a-text-box-using-ui-automation.md)
- [UI Otomasyonunu Kullanarak Metin Bulma ve Vurgulama](find-and-highlight-text-using-ui-automation.md)
- [UI Otomasyon Denetim Düzenlerine Genel Bakış](ui-automation-control-patterns-overview.md)
- [İstemciler İçin UI Otomasyon Denetim Düzenleri](ui-automation-control-patterns-for-clients.md)
