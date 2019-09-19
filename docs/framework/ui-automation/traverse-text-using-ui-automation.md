---
title: UI Otomasyonunu Kullanarak Çapraz Geçiş Yapma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, traversing text
- text, traversing
- traversing text
ms.assetid: 3ddb3b7b-1d6b-4dba-8678-5a68e868aadb
ms.openlocfilehash: b22da8575fdc4360601946c3cba136466a393895
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71042557"
---
# <a name="traverse-text-using-ui-automation"></a>UI Otomasyonunu Kullanarak Çapraz Geçiş Yapma
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir. Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu başlığı altında, bir [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] <xref:System.Windows.Automation.Text.TextUnit> belgenin metin içeriğini artışlarla çapraz geçiş için nasıl kullanılacağı gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde, bir UI Otomasyon metin sağlayıcısı içeriğinin nasıl gezeceği gösterilmektedir. <xref:System.Windows.Automation.Text.TextPatternRange.Move%2A> Yöntemi <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> ' <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> a aitveuçnoktalarınıtaşıdıkça<xref:System.Windows.Automation.Text.TextPatternRange>. Bu metin aralığı genellikle metin ekleme noktasını temsil eden bir bozuk aralığıdır.  
  
> [!NOTE]
> Yalnızca metin tabanlı katıştırılmış nesneler metin akışının parçası olarak kabul edildiğinden, resimler gibi katıştırılmış nesneler veya dönüş değeri etkilenmez `Move` .  
  
[!code-csharp[FindText#StartApp](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#startapp)]
[!code-vb[FindText#StartApp](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#startapp)]  
[!code-csharp[FindText#FindTextProvider](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#findtextprovider)]
[!code-vb[FindText#FindTextProvider](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#findtextprovider)]  
[!code-csharp[FindText#Navigate](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#navigate)]
[!code-vb[FindText#Navigate](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#navigate)]  
  
 Kullanılan <xref:System.Windows.Automation.Text.TextUnit> herhangi bir yöntem, verilen <xref:System.Windows.Automation.Text.TextUnit> denetim tarafından desteklenmiyorsa <xref:System.Windows.Automation.Text.TextUnit> , desteklenen bir sonraki en büyük öğesine ertelenecek.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu TextPattern Öğesine Genel Bakış](ui-automation-textpattern-overview.md)
- [UI Otomasyonu Kullanarak Metin Kutusuna İçerik Ekleme](add-content-to-a-text-box-using-ui-automation.md)
- [UI Otomasyonunu Kullanarak Metin Bulma ve Vurgulama](find-and-highlight-text-using-ui-automation.md)
- [UI Otomasyonu Denetim Desenlerine Genel Bakış](ui-automation-control-patterns-overview.md)
- [İstemciler İçin UI Otomasyonu Denetim Düzenleri](ui-automation-control-patterns-for-clients.md)
