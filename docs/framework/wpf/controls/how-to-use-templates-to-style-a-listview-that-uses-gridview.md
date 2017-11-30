---
title: "Nasıl yapılır: GridView Kullanan ListView'da Stil Oluşturmak için Şablonları Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: ListView controls [WPF], styling
ms.assetid: 94bf964b-96c8-4bdf-a0c3-f5271b7cb565
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 246c144a18d7c1014096a6e37ad09b6eec5ad932
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-templates-to-style-a-listview-that-uses-gridview"></a>Nasıl yapılır: GridView Kullanan ListView'da Stil Oluşturmak için Şablonları Kullanma
Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.DataTemplate> ve <xref:System.Windows.Style> nesnelerinin görünümünü belirtmek için bir <xref:System.Windows.Controls.ListView> kullanan denetim bir <xref:System.Windows.Controls.GridView> görüntüleme modu.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örneklerde gösterildiği <xref:System.Windows.Style> ve <xref:System.Windows.DataTemplate> için sütun başlığını görünüşünü özelleştirme nesneleri bir <xref:System.Windows.Controls.GridViewColumn>.  
  
 [!code-xaml[ListViewTemplate#GridViewHeaderStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewheaderstyle)]  
  
 [!code-xaml[ListViewTemplate#GridViewHeaderTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewheadertemplate)]  
  
 Aşağıdaki örnekte bu kullanmayı gösterir <xref:System.Windows.Style> ve <xref:System.Windows.DataTemplate> ayarlamak için nesneleri <xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A> ve <xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> özelliklerini bir <xref:System.Windows.Controls.GridViewColumn>. <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> Özelliği sütun hücrelerinin içeriğini tanımlar.  
  
 [!code-xaml[ListViewTemplate#GridViewColumnTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcolumntemplate)]  
  
 <xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A> Ve <xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> yalnızca iki sütun üstbilgisi görünümünü özelleştirmek için kullanabileceğiniz çeşitli özelliklerin bir <xref:System.Windows.Controls.GridView> denetim. Daha fazla bilgi için bkz: [GridView sütun üstbilgi stilleri ve şablonlarına genel bakış](../../../../docs/framework/wpf/controls/gridview-column-header-styles-and-templates-overview.md).  
  
 Aşağıdaki örnekte nasıl tanımlanacağı gösterilmektedir bir <xref:System.Windows.DataTemplate> hücrelerde görünümünü özelleştiren bir <xref:System.Windows.Controls.GridViewColumn>.  
  
 [!code-xaml[ListViewTemplate#GridViewCellTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcelltemplate)]  
  
 Aşağıdaki örnekte bu kullanmayı gösterir <xref:System.Windows.DataTemplate> içeriğini tanımlamak için bir <xref:System.Windows.Controls.GridViewColumn> hücre. Bu şablon yerine kullanılır <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> önceki gösterilen özelliği <xref:System.Windows.Controls.GridViewColumn> örnek.  
  
 [!code-xaml[ListViewTemplate#CellTemplateProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#celltemplateproperty)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [GridView genel bakış](../../../../docs/framework/wpf/controls/gridview-overview.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [ListView Genel Bakış](../../../../docs/framework/wpf/controls/listview-overview.md)
