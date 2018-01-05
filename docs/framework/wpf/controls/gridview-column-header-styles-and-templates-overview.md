---
title: "GridView Sütun Üstbilgi Stil ve Şablonlarına Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- column headers [WPF], customizing
- ListView controls [WPF], GridView column header styles
- controls [WPF], ListView
- headers [WPF], customizing
- GridView view mode [WPF], customizing column headers
ms.assetid: 74835674-a39e-4ab5-9418-ad7f6ab7b956
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 996d6d5f531a866d4fc80acc3848cdf264901032
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="gridview-column-header-styles-and-templates-overview"></a>GridView Sütun Üstbilgi Stil ve Şablonlarına Genel Bakış
Bu genel bir sütun başlığını özelleştirmek için kullandığınız özellikler için öncelik sırasını açıklar <xref:System.Windows.Controls.GridView> görüntüleme modu, bir <xref:System.Windows.Controls.ListView> denetim.  
  
## <a name="customizing-a-column-header-in-a-gridview"></a>GridView içinde bir sütun başlığını özelleştirme  
 İçerik, Düzen ve bir sütun başlığına stilini tanımlayan özellikleri bir <xref:System.Windows.Controls.GridView> üzerinde birçok ilişkili sınıflar bulunur. Bu özelliklerden bazıları, benzer işlevselliği veya aynı sahiptir.  
  
 Aşağıdaki tabloda satır grupları aynı işlevi gerçekleştirir özellikleri gösterir. Bu özellikler sütun başlıklarının özelleştirmek için kullanabileceğiniz bir <xref:System.Windows.Controls.GridView>. Sağdan sola özelliği sağdan sağ sütundaki en yüksek önceliğe sahip olduğu ilgili özellikler için öncelik sırasını değil. Örneğin, bir <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> üzerinde ayarlanmış <xref:System.Windows.Controls.GridViewColumnHeader> nesne ve <xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A> ilişkili üzerinde ayarlandı <xref:System.Windows.Controls.GridViewColumn>, <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> önceliklidir. Bu senaryoda, <xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A> hiçbir etkisi olmaz.  
  
 **GridView içinde sütun üstbilgilerinin ilgili özellikleri**  
  
|||||  
|-|-|-|-|  
|**Sınıflar**|<xref:System.Windows.Controls.GridView>|<xref:System.Windows.Controls.GridViewColumn>|<xref:System.Windows.Controls.GridViewColumnHeader>|  
|**Bağlam Menüsü Özellikleri**|<xref:System.Windows.Controls.GridView.ColumnHeaderContextMenu%2A>|Geçerli değil|<xref:System.Windows.FrameworkElement.ContextMenu%2A>|  
|**Araç İpucu**<br /><br /> **Özellikler**|<xref:System.Windows.Controls.GridView.ColumnHeaderToolTip%2A>|Geçerli değil|<xref:System.Windows.FrameworkElement.ToolTip%2A>|  
|**Üstbilgi şablonu**<br /><br /> **Özellikler**|<xref:System.Windows.Controls.GridView.ColumnHeaderTemplate%2A> <sup>1</sup>/<br /><br /> <xref:System.Windows.Controls.GridView.ColumnHeaderTemplateSelector%2A>|<xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> <sup>1</sup>/<br /><br /> <xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A>|<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> <sup>1</sup>/<br /><br /> <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A>|  
|**Stil özellikleri**|<xref:System.Windows.Controls.GridView.ColumnHeaderContainerStyle%2A>|<xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A>|<xref:System.Windows.FrameworkElement.Style%2A>|  
  
 <sup>1</sup>için **Üstbilgi Şablon Özellikleri**, ayarlarsanız şablonu ve şablon seçici özelliklerini, şablon özelliği önceliğe. Örneğin, her ikisini de ayarlarsanız <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> ve <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A> özelliklerini <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> özelliği önceliklidir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [ListView Genel Bakış](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [GridView Genel Bakış](../../../../docs/framework/wpf/controls/gridview-overview.md)
