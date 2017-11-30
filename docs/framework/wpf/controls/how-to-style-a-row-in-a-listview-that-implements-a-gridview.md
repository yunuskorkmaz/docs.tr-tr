---
title: "Nasıl yapılır: GridView Uygulayan ListView İçinde bir Satıra Stil Ekleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GridView controls [WPF], styling rows
- styling rows in ListViews implementing GridViews [WPF]
- ListView controls [WPF], styling rows with GridViews
ms.assetid: 2e406ba2-70a0-4e62-841f-0934859de76e
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c51f6cc5c35200267aa84960655fd734a937a7c5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-style-a-row-in-a-listview-that-implements-a-gridview"></a>Nasıl yapılır: GridView Uygulayan ListView İçinde bir Satıra Stil Ekleme
Bu örnek bir satırda stil gösterilmektedir bir <xref:System.Windows.Controls.ListView> uygulayan denetim bir <xref:System.Windows.Controls.GridView> <xref:System.Windows.Controls.ListView.View%2A> modu.  
  
## <a name="example"></a>Örnek  
 Bir satır stili bir <xref:System.Windows.Controls.ListView> ayarlayarak denetimi bir <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> üzerinde <xref:System.Windows.Controls.ListView> denetim. Stil olarak temsil edilir öğelerinden için ayarlanmış <xref:System.Windows.Controls.ListViewItem> nesneleri. <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> Başvuruları <xref:System.Windows.Controls.ControlTemplate> satır içeriği görüntülemek için kullanılan nesne.  
  
 Aşağıdaki örneklerde ayıklandığı tam örnek depolanan şarkı bilgilerinin koleksiyonunu görüntüleyen bir [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] veritabanı. Veritabanındaki her şarkının derecelendirme alanı vardır ve bu alanın değeri bir satır şarkı bilgilerinin görüntülemek nasıl belirtir.  
  
 Aşağıdaki örnekte nasıl tanımlanacağı gösterilmektedir <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> için <xref:System.Windows.Controls.ListViewItem> şarkı koleksiyonundaki şarkıya temsil eden nesne. <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> Başvuruları <xref:System.Windows.Controls.ControlTemplate> şarkı bilgilerini satırının görüntülemek nasıl belirtin nesneleri.  
  
 [!code-xaml[ListViewItemStyleSnippet#ItemContainerStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#itemcontainerstyle)]  
  
 Aşağıdaki örnekte gösterildiği bir <xref:System.Windows.Controls.ControlTemplate> metin dizesini ekleyen `"Strongly Recommended"` satır. Bu şablon başvuru <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> ve şarkının derecesi 5 (beş) değerine sahip olduğunda görüntüler. <xref:System.Windows.Controls.ControlTemplate> İçeren bir <xref:System.Windows.Controls.GridViewRowPresenter> sütunlarda sıranın içeriğini tarafından tanımlandığı şekilde yerleştirir nesne <xref:System.Windows.Controls.GridView> görüntüleme modu.  
  
 [!code-xaml[ListViewItemStyleSnippet#ControlTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#controltemplate)]  
  
 Aşağıdaki örnek tanımlar <xref:System.Windows.Controls.GridView>.  
  
 [!code-xaml[ListViewItemStyleSnippet#GridView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#gridview)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [ListView Genel Bakış](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [Stil ve şablon oluşturma](../../../../docs/framework/wpf/controls/styling-and-templating.md)
