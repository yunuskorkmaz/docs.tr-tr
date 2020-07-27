---
title: UI Otomasyonu Kullanarak Tablo İçeriğini Kullanıma Sunma
description: UI Otomasyonu kullanarak bir tablonun içeriğini kullanıma sunma bölümüne bakın. Tablosal denetim içindeki her hücrenin içerik ve iç özellikleri gösterilir.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tables, exposing content of
- UI Automation, exposing content of tables
- exposing content of tables using UI Automation
ms.assetid: ac3c5eaa-49c7-4653-b83e-532e2a2604a2
ms.openlocfilehash: c6ceb05421547a7e84f612ed6da2bd7002bf095b
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168464"
---
# <a name="expose-the-content-of-a-table-using-ui-automation"></a>UI Otomasyonu Kullanarak Tablo İçeriğini Kullanıma Sunma
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu başlığı altında [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] , her hücrenin içeriğini ve iç özelliklerini tablosal denetim içinde göstermek için nasıl kullanılabilecekleri gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, bir tablo hücresinin içeriğini temsil eden bir öğesinin nasıl elde edileceği gösterilmektedir <xref:System.Windows.Automation.AutomationElement> ; satır ve sütun dizinleri, satır ve sütun yayılmaları gibi hücre özellikleri, satır ve sütun başlığı bilgileri de alınır. Bu örnek, uygulayan tablolu bir denetimin klavye çapraz geçişinin benzetimini yapmak için bir odak değişikliği olay işleyicisi kullanır [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] . Her tablo öğesi için bilgi, bir odak değişikliği olayında gösterilir.  
  
> [!NOTE]
> Odak değişiklikleri genel Masaüstü olayları olduğundan, tablo dışındaki odak değişikliği olayları filtrelenmelidir. İlgili bir uygulama için [TrackFocus örneğine](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771428(v=vs.90)) bakın.  
  
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

- [UI Otomasyon Denetim Düzenlerine Genel Bakış](ui-automation-control-patterns-overview.md)
- [İstemciler İçin UI Otomasyon Denetim Düzenleri](ui-automation-control-patterns-for-clients.md)
- [UI Otomasyonu Tablo Denetim Düzenini Uygulama](implementing-the-ui-automation-table-control-pattern.md)
- [UI Otomasyon TableItem Denetim Düzeni Uygulama](implementing-the-ui-automation-tableitem-control-pattern.md)
- [UI Otomasyon Kılavuz Denetim Düzenini Uygulama](implementing-the-ui-automation-grid-control-pattern.md)
- [UI Otomasyon GridItem Denetim Düzeni Uygulama](implementing-the-ui-automation-griditem-control-pattern.md)
