---
title: "Nasıl yapılır: DataGrid Denetimine Satır Ayrıntıları Ekleme"
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
- DataTemplate [WPF], DataGrid
- row details [WPF], DataGrid
- DataGrid [WPF], row details
ms.assetid: 0bdc6f50-9b4c-483f-9df6-a47a1fde998b
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f65eb9e916fad83deb1476c1d8f0def4981d08d8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-row-details-to-a-datagrid-control"></a>Nasıl yapılır: DataGrid Denetimine Satır Ayrıntıları Ekleme
Kullanırken <xref:System.Windows.Controls.DataGrid> denetimi, bir satır ayrıntıları bölümü ekleyerek veri sunumunu özelleştirebilirsiniz. Bir sıra ayrıntıları bölümü ekleyerek, bazı veriler, isteğe bağlı olarak görünür mü yoksa daraltılmış olan bir şablon gruplamanıza olanak sağlar. Örneğin, satır ayrıntıları ekleyebilirsiniz bir <xref:System.Windows.Controls.DataGrid> her satır için verileri yalnızca bir özetini sunar <xref:System.Windows.Controls.DataGrid>, ancak daha fazla veri alanı kullanıcı bir satır seçtiğinde gösterir. Şablon için satır Ayrıntılar bölümünde tanımladığınız <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> özelliği. Aşağıdaki çizimde bir satır ayrıntıları bölümü örneği gösterir.  
  
 ![Satır ayrıntılarıyla gösterilen DataGrid](../../../../docs/framework/wpf/controls/media/ndp-rowdetails.png "NDP_RowDetails")  
  
 Sıra ayrıntıları şablonunu ya da satır içi XAML veya bir kaynak olarak tanımlayın. Her iki yaklaşımın aşağıdaki yordamlarda gösterilir. Bir kaynak olarak eklenen veri şablonu proje boyunca şablonu yeniden oluşturmaya gerek kalmadan kullanılabilir. Satır içi olarak eklenen veri şablonu XAML yalnızca tanımlandığı denetimden erişilebilir.  
  
### <a name="to-display-row-details-by-using-inline-xaml"></a>Satır içi XAML kullanarak satır ayrıntıları görüntülemek için  
  
1.  Oluşturma bir <xref:System.Windows.Controls.DataGrid> bir veri kaynağından görüntüler.  
  
2.  İçinde <xref:System.Windows.Controls.DataGrid> öğesi ekleme bir <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> öğesi.  
  
3.  Oluşturma bir <xref:System.Windows.DataTemplate> satır ayrıntıları bölümü görünümünü tanımlar.  
  
     Aşağıdaki XAML gösterildiği <xref:System.Windows.Controls.DataGrid> ve nasıl tanımlanacağını <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> satır içi. <xref:System.Windows.Controls.DataGrid> Görüntüler üç değerleri her satır, üç daha fazla değer satır seçili olduğunda.  
  
     [!code-xaml[DataGrid_RowDetails#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml#1)]  
  
     Aşağıdaki kod görüntülenen verileri seçmek için kullanılan sorgu gösterir <xref:System.Windows.Controls.DataGrid>. Bu örnekte sorgu müşteri bilgilerini içeren bir varlık veri seçer.  
  
     [!code-csharp[DataGrid_RowDetails#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml.cs#2)]
     [!code-vb[DataGrid_RowDetails#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_rowdetails/vb/mainwindow.xaml.vb#2)]  
  
### <a name="to-display-row-details-by-using-a-resource"></a>Bir kaynağı kullanarak satır ayrıntıları görüntülemek için  
  
1.  Oluşturma bir <xref:System.Windows.Controls.DataGrid> bir veri kaynağından görüntüler.  
  
2.  Ekleme bir <xref:System.Windows.FrameworkElement.Resources%2A> öğesi kök öğesi için gibi bir <xref:System.Windows.Window> denetim veya <xref:System.Windows.Controls.Page> denetlemek veya ekleme bir <xref:System.Windows.Application.Resources%2A> öğesine <xref:System.Windows.Application> App.xaml (veya Application.xaml) dosyasındaki sınıfı.  
  
3.  Kaynaklar öğesinde oluşturma bir <xref:System.Windows.DataTemplate> satır ayrıntıları bölümü görünümünü tanımlar.  
  
     Aşağıdaki XAML gösterildiği <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> tanımlanan <xref:System.Windows.Application> sınıfı.  
  
     [!code-xaml[DataGrid_RowDetails#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/app.xaml#3)]  
  
4.  Üzerinde <xref:System.Windows.DataTemplate>ayarlayın [x: Key yönergesi](../../../../docs/framework/xaml-services/x-key-directive.md) veri şablonunu benzersiz olarak tanımlayan bir değer.  
  
5.  İçinde <xref:System.Windows.Controls.DataGrid> öğe, ayarladığınız <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> önceki adımlarda tanımlanan kaynağa özelliği. Kaynak statik bir kaynak olarak atayın.  
  
     Aşağıdaki XAML gösterildiği <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> önceki örnekten kaynağa nasıl ayarlanacağını özelliği.  
  
     [!code-xaml[DataGrid_RowDetails#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/window2.xaml#4)]  
  
### <a name="to-set-visibility-and-prevent-horizontal-scrolling-for-row-details"></a>Görünürlüğü ayarlamak ve yatay satır ayrıntılarını kaydırmayı önlemek için  
  
1.  Gerekirse, ayarlayın <xref:System.Windows.Controls.DataGrid.RowDetailsVisibilityMode%2A> özelliğine bir <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode> değeri.  
  
     Varsayılan değer ayarlamak <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.VisibleWhenSelected>. Ayarlayabilirsiniz <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Visible> tüm satırların ayrıntılarını göstermek için veya <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Collapsed> tüm satırların ayrıntılarını gizlemek için.  
  
2.  Gerekirse, ayarlayın <xref:System.Windows.Controls.DataGrid.AreRowDetailsFrozen%2A> özelliğine `true` satır önlemek için yatay olarak kaymasını bölüm ayrıntıları.
