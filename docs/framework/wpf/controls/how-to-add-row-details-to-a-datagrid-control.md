---
title: 'Nasıl yapılır: DataGrid Denetimine Satır Ayrıntıları Ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataTemplate [WPF], DataGrid
- row details [WPF], DataGrid
- DataGrid [WPF], row details
ms.assetid: 0bdc6f50-9b4c-483f-9df6-a47a1fde998b
ms.openlocfilehash: 4db414e1907d42071f7251c390077d4020fa577c
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/31/2019
ms.locfileid: "75559683"
---
# <a name="how-to-add-row-details-to-a-datagrid-control"></a>Nasıl yapılır: DataGrid Denetimine Satır Ayrıntıları Ekleme
<xref:System.Windows.Controls.DataGrid> denetimini kullanırken, veri sunumunu bir satır ayrıntıları bölümü ekleyerek özelleştirebilirsiniz. Satır ayrıntıları bölümü eklemek, bazı verileri isteğe bağlı olarak görünür veya daraltılmış bir şablonda gruplandırmanızı sağlar. Örneğin, <xref:System.Windows.Controls.DataGrid>her satır için yalnızca verilerin özetini sunan bir <xref:System.Windows.Controls.DataGrid> satır ayrıntıları ekleyebilirsiniz, ancak kullanıcı bir satır seçtiğinde daha fazla veri alanı sunar. <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> özelliğindeki satır ayrıntıları bölümünün şablonunu tanımlarsınız. Aşağıdaki çizimde, bir satır ayrıntıları Bölümü örneği gösterilmektedir.  
  
 ![Satır ayrıntılarıyla gösterilen DataGrid](./media/ndp-rowdetails.png "NDP_RowDetails")  
  
 Satır ayrıntıları şablonunu satır içi XAML veya kaynak olarak tanımlarsınız. Aşağıdaki yordamlarda her iki yaklaşım da gösterilmiştir. Kaynak olarak eklenen bir veri şablonu, şablonu yeniden oluşturmadan proje genelinde kullanılabilir. Satır içi XAML olarak eklenen bir veri şablonuna yalnızca tanımlandığı denetimden erişilebilir.  
  
### <a name="to-display-row-details-by-using-inline-xaml"></a>Satır içi XAML kullanarak satır ayrıntılarını görüntüleme  
  
1. Veri kaynağındaki verileri görüntüleyen bir <xref:System.Windows.Controls.DataGrid> oluşturun.  
  
2. İçinde <xref:System.Windows.Controls.DataGrid> öğe, Ekle bir <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> öğesi.  
  
3. Satır ayrıntıları bölümünün görünümünü tanımlayan bir <xref:System.Windows.DataTemplate> oluşturun.  
  
     Aşağıdaki XAML <xref:System.Windows.Controls.DataGrid> ve <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> satır içi olarak nasıl tanımlanacağını göstermektedir. <xref:System.Windows.Controls.DataGrid> her satırdaki üç değeri ve satır seçildiğinde üç daha fazla değeri görüntüler.  
  
     [!code-xaml[DataGrid_RowDetails#1](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml#1)]  
  
     Aşağıdaki kod, <xref:System.Windows.Controls.DataGrid>görüntülenen verileri seçmek için kullanılan sorguyu gösterir. Bu örnekte sorgu, müşteri bilgilerini içeren bir varlıktan veri seçer.  
  
     [!code-csharp[DataGrid_RowDetails#2](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml.cs#2)]
     [!code-vb[DataGrid_RowDetails#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_rowdetails/vb/mainwindow.xaml.vb#2)]  
  
### <a name="to-display-row-details-by-using-a-resource"></a>Kaynak kullanarak satır ayrıntılarını görüntüleme  
  
1. Veri kaynağındaki verileri görüntüleyen bir <xref:System.Windows.Controls.DataGrid> oluşturun.  
  
2. Kök öğeye bir <xref:System.Windows.Window> denetimi veya <xref:System.Windows.Controls.Page> denetimi gibi bir <xref:System.Windows.FrameworkElement.Resources%2A> öğesi ekleyin veya App. xaml (veya Application. xaml) dosyasındaki <xref:System.Windows.Application> sınıfına bir <xref:System.Windows.Application.Resources%2A> öğesi ekleyin.  
  
3. Resources öğesinde, satır ayrıntıları bölümünün görünümünü tanımlayan bir <xref:System.Windows.DataTemplate> oluşturun.  
  
     Aşağıdaki XAML <xref:System.Windows.Application> sınıfında tanımlanan <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> gösterir.  
  
     [!code-xaml[DataGrid_RowDetails#3](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/app.xaml#3)]  
  
4. <xref:System.Windows.DataTemplate>, [X:Key yönergesini](../../../desktop-wpf/xaml-services/xkey-directive.md) veri şablonunu benzersiz bir şekilde tanımlayan bir değere ayarlayın.  
  
5. <xref:System.Windows.Controls.DataGrid> öğesinde, <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> özelliğini önceki adımlarda tanımlanan kaynak olarak ayarlayın. Kaynağı bir statik kaynak olarak atayın.  
  
     Aşağıdaki XAML, önceki örnekteki kaynak olarak ayarlanan <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> özelliğini gösterir.  
  
     [!code-xaml[DataGrid_RowDetails#4](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/window2.xaml#4)]  
  
### <a name="to-set-visibility-and-prevent-horizontal-scrolling-for-row-details"></a>Görünürlük ayarlamak ve satır ayrıntıları için yatay kaydırmayı engellemek için  
  
1. Gerekirse <xref:System.Windows.Controls.DataGrid.RowDetailsVisibilityMode%2A> özelliğini bir <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode> değeri olarak ayarlayın.  
  
     Varsayılan olarak, değer <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.VisibleWhenSelected>olarak ayarlanır. Tüm satırların ayrıntılarını göstermek için <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Visible>, tüm satırların ayrıntılarını gizlemek için <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Collapsed> ayarlayabilirsiniz.  
  
2. Gerekirse, satır ayrıntıları bölümünün yatay olarak kaymasını engellemek için <xref:System.Windows.Controls.DataGrid.AreRowDetailsFrozen%2A> özelliğini `true` olarak ayarlayın.
