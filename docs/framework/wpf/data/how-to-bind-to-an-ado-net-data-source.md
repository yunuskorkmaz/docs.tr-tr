---
title: "Nasıl yapılır: ADO.NET Veri Kaynağına Bağlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], binding to ADO.NET data sources
- ADO.NET data sources [WPF], binding to
- binding [WPF], to ADO.NET data sources
ms.assetid: a70c6d7b-7b38-4fdf-b655-4804db7c8315
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0eb555bb9f21385d2d0b66fe0dd39112c8350dec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-bind-to-an-adonet-data-source"></a>Nasıl yapılır: ADO.NET Veri Kaynağına Bağlama
Bu örnek nasıl bağlanacağını gösterir bir [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.ListBox> denetimini bir [!INCLUDE[TLA#tla_adonet](../../../../includes/tlasharptla-adonet-md.md)] `DataSet`.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, bir `OleDbConnection` nesne olan veri kaynağına bağlanmak için kullanılan bir `Access MDB` bağlantı dizesinde belirtilen dosya. Bağlantı kurulduktan sonra bir `OleDbDataAdpater` nesnesi oluşturulur. `OleDbDataAdpater` Nesne yürüten bir select [!INCLUDE[TLA#tla_sql](../../../../includes/tlasharptla-sql-md.md)] veritabanından kayıt kümesi almak için bildirimi. Sonuçlardan [!INCLUDE[TLA2#tla_sql](../../../../includes/tla2sharptla-sql-md.md)] komutu depolanır bir `DataTable` , `DataSet` çağırarak `Fill` yöntemi `OleDbDataAdapter`. `DataTable` Bu örnekte adlı `BookTable`. Bu örnek daha sonra Ayarlar <xref:System.Windows.FrameworkElement.DataContext%2A> özelliği <xref:System.Windows.Controls.ListBox> için `DataSet` nesnesi.  
  
 [!code-csharp[ADODataSet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 Biz sonra bağlayabilirsiniz <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> özelliği <xref:System.Windows.Controls.ListBox> için `BookTable` , `DataSet`:  
  
 [!code-xaml[ADODataSet#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#2)]  
  
 `BookItemTemplate`olan <xref:System.Windows.DataTemplate> verinin nasıl göründüğünü tanımlar:  
  
 [!code-xaml[ADODataSet#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#3)]  
  
 `IntColorConverter` Dönüştüren bir `int` bir renk. Bu dönüştürücü kullanarak <xref:System.Windows.Controls.TextBlock.Background%2A> üçüncü rengini <xref:System.Windows.Controls.TextBlock> yeşil görünür değilse değerini `NumPages` Aksi takdirde değerinden 350 ve kırmızı olur. Dönüştürücü uyarlamasını burada gösterilmiyor.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Data.BindingListCollectionView>  
 [Veri bağlama genel bakış](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
