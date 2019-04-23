---
title: UI Otomasyonu Kullanarak Tablo İçeriğini Kullanıma Sunma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tables, exposing content of
- UI Automation, exposing content of tables
- exposing content of tables using UI Automation
ms.assetid: ac3c5eaa-49c7-4653-b83e-532e2a2604a2
ms.openlocfilehash: a9867a07207f825f3f4a781f1c05607fc6b071b9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59174713"
---
# <a name="expose-the-content-of-a-table-using-ui-automation"></a>UI Otomasyonu Kullanarak Tablo İçeriğini Kullanıma Sunma
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu başlığı altında gösterilir nasıl [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] her hücre bir tablo denetimi içinde içerik ve gerçek özelliklerini göstermek için kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde nasıl alınacağını gösterir. bir <xref:System.Windows.Automation.AutomationElement> tablo hücresi içeriğini temsil eden; satır ve sütun dizinler, satır ve sütun yayılma ve satır ve sütun üst bilgileri gibi hücre özellikleri de elde edilir. Bu örnek, klavye geçişi uygulayan bir tablo denetimi benzetimini yapmak için odak değiştirme olay işleyicisi kullanır. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. Bilgi her tablo öğesi için bir odak değişiklik olayı kullanıma sunulur.  
  
> [!NOTE]
>  Odak değişiklikleri genel Masaüstü olaylar olduğundan, tablo dışında odak değişikliği olayları filtrelenmelidir. Bkz: [TrackFocus örnek](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771428(v=vs.90)) ilgili bir uygulama.  
  
 [!code-csharp[UIATableItemPattern_snip#StartTarget](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATableItemPattern_snip/CSharp/UIATableItemPattern_snippets.cs#starttarget)]
 [!code-vb[UIATableItemPattern_snip#StartTarget](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATableItemPattern_snip/VisualBasic/UIATableItemPattern_snippets.vb#starttarget)]  
[!code-csharp[UIATableItemPattern_snip#GetTableElement](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATableItemPattern_snip/CSharp/UIATableItemPattern_snippets.cs#gettableelement)]
[!code-vb[UIATableItemPattern_snip#GetTableElement](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATableItemPattern_snip/VisualBasic/UIATableItemPattern_snippets.vb#gettableelement)]  
[!code-csharp[UIATableItemPattern_snip#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATableItemPattern_snip/CSharp/UIATableItemPattern_snippets.cs#101)]
[!code-vb[UIATableItemPattern_snip#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATableItemPattern_snip/VisualBasic/UIATableItemPattern_snippets.vb#101)]  
[!code-csharp[UIATableItemPattern_snip#1015](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATableItemPattern_snip/CSharp/UIATableItemPattern_snippets.cs#1015)]
[!code-vb[UIATableItemPattern_snip#1015](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATableItemPattern_snip/VisualBasic/UIATableItemPattern_snippets.vb#1015)]  
[!code-csharp[UIATableItemPattern_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATableItemPattern_snip/CSharp/UIATableItemPattern_snippets.cs#102)]
[!code-vb[UIATableItemPattern_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATableItemPattern_snip/VisualBasic/UIATableItemPattern_snippets.vb#102)]  
[!code-csharp[UIATableItemPattern_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATableItemPattern_snip/CSharp/UIATableItemPattern_snippets.cs#103)]
[!code-vb[UIATableItemPattern_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATableItemPattern_snip/VisualBasic/UIATableItemPattern_snippets.vb#103)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu Denetim Desenlerine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [İstemciler İçin UI Otomasyonu Denetim Düzenleri](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [UI Otomasyonu Table Denetim Desenini Uygulama](../../../docs/framework/ui-automation/implementing-the-ui-automation-table-control-pattern.md)
- [UI Otomasyonu TableItem Denetim Desenini Uygulama](../../../docs/framework/ui-automation/implementing-the-ui-automation-tableitem-control-pattern.md)
- [UI Otomasyonu Grid Denetim Desenini Uygulama](../../../docs/framework/ui-automation/implementing-the-ui-automation-grid-control-pattern.md)
- [UI Otomasyonu GridItem Denetim Desenini Uygulama](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md)
