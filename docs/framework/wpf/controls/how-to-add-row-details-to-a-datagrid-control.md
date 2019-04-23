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
ms.openlocfilehash: d5b6539f3d379088528b9654861267988b6fc69b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59768650"
---
# <a name="how-to-add-row-details-to-a-datagrid-control"></a>Nasıl yapılır: DataGrid Denetimine Satır Ayrıntıları Ekleme
Kullanırken <xref:System.Windows.Controls.DataGrid> denetim, satır ayrıntılar bölümüne ekleyerek veri sunumu özelleştirebilirsiniz. Satır ayrıntıları bölümü ekleyerek, bazı veriler, isteğe bağlı olarak görünür veya daraltılmış bir şablonu gruplamanıza olanak sağlar. Satır ayrıntıları ekleme gibi bir <xref:System.Windows.Controls.DataGrid> veri her satır için yalnızca bir özetini sunar <xref:System.Windows.Controls.DataGrid>, ancak kullanıcı bir satır seçtiğinde, daha fazla veri alanı sunar. Şablon için satır Ayrıntılar bölümünde tanımladığınız <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> özelliği. Satır ayrıntıları bölümü bir örneği aşağıda gösterilmiştir.  
  
 ![Satır ayrıntıları ile gösterilen DataGrid](./media/ndp-rowdetails.png "NDP_RowDetails")  
  
 Satır ayrıntıları şablon satır içi XAML veya bir kaynak olarak tanımlayabilirsiniz. Aşağıdaki yordamlarda her iki yaklaşım gösterilmektedir. Bir kaynak olarak eklenen veri şablonu şablonu yeniden oluşturmaya gerek kalmadan proje boyunca kullanılabilir. Satır içi olarak eklenen veri şablonu XAML yalnızca tanımlandığı denetiminden erişilebilir.  
  
### <a name="to-display-row-details-by-using-inline-xaml"></a>Satır içi XAML kullanarak satır ayrıntıları görüntülemek için  
  
1. Oluşturma bir <xref:System.Windows.Controls.DataGrid> , bir veri kaynağındaki verileri görüntüler.  
  
2. İçinde <xref:System.Windows.Controls.DataGrid> öğe, Ekle bir <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> öğesi.  
  
3. Oluşturma bir <xref:System.Windows.DataTemplate> , satır ayrıntıları bölümü görünümünü tanımlar.  
  
     Aşağıdaki XAML gösterildiği <xref:System.Windows.Controls.DataGrid> ve nasıl tanımlanacağını <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> satır içi. <xref:System.Windows.Controls.DataGrid> Görüntüler üç değer her satır ve üç daha fazla değer satır seçildiğinde.  
  
     [!code-xaml[DataGrid_RowDetails#1](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml#1)]  
  
     Aşağıdaki kod görüntülenen verileri seçmek için kullanılan sorgu gösterir <xref:System.Windows.Controls.DataGrid>. Bu örnekte sorgu, müşteri bilgilerini içeren bir varlıktan veri seçer.  
  
     [!code-csharp[DataGrid_RowDetails#2](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml.cs#2)]
     [!code-vb[DataGrid_RowDetails#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_rowdetails/vb/mainwindow.xaml.vb#2)]  
  
### <a name="to-display-row-details-by-using-a-resource"></a>Bir kaynağı kullanarak satır ayrıntıları görüntülemek için  
  
1. Oluşturma bir <xref:System.Windows.Controls.DataGrid> , bir veri kaynağındaki verileri görüntüler.  
  
2. Ekleme bir <xref:System.Windows.FrameworkElement.Resources%2A> öğesi kök öğe gibi bir <xref:System.Windows.Window> denetim veya bir <xref:System.Windows.Controls.Page> denetlemek ya da ekleme bir <xref:System.Windows.Application.Resources%2A> öğesine <xref:System.Windows.Application> App.xaml (veya Application.xaml) dosyasında sınıfı.  
  
3. Kaynaklar öğesinde oluşturma bir <xref:System.Windows.DataTemplate> , satır ayrıntıları bölümü görünümünü tanımlar.  
  
     Aşağıdaki XAML gösterildiği <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> tanımlanan <xref:System.Windows.Application> sınıfı.  
  
     [!code-xaml[DataGrid_RowDetails#3](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/app.xaml#3)]  
  
4. Üzerinde <xref:System.Windows.DataTemplate>ayarlayın [x: Key yönergesi](../../xaml-services/x-key-directive.md) için veri şablonunu benzersiz olarak tanımlayan bir değer.  
  
5. İçinde <xref:System.Windows.Controls.DataGrid> öğe, ayarladığınız <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> önceki adımlarda tanımlanan kaynak için özellik. Kaynak statik bir kaynak olarak atayın.  
  
     Aşağıdaki XAML gösterildiği <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> özelliği önceki örnekte kaynak olarak ayarlayın.  
  
     [!code-xaml[DataGrid_RowDetails#4](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/window2.xaml#4)]  
  
### <a name="to-set-visibility-and-prevent-horizontal-scrolling-for-row-details"></a>Görünürlük ve önlemek için satır ayrıntıları yatay kaydırma  
  
1. Gerekirse, ayarlama <xref:System.Windows.Controls.DataGrid.RowDetailsVisibilityMode%2A> özelliğini bir <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode> değeri.  
  
     Varsayılan olarak, değeri şuna ayarlı <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.VisibleWhenSelected>. Ayarlayabilirsiniz <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Visible> tüm satırlar için ayrıntıları göstermek için veya <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Collapsed> tüm satırları ayrıntılarını gizlemek için.  
  
2. Gerekirse, ayarlama <xref:System.Windows.Controls.DataGrid.AreRowDetailsFrozen%2A> özelliğini `true` ayrıntıları yatay kaydırma gelen bölüm satır önlemek için.
