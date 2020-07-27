---
title: 'Nasıl yapılır: DataGrid Denetimine Satır Ayrıntıları Ekleme'
description: Bir satır ayrıntıları bölümü ekleyerek Windows Presentation Foundation DataGrid denetimini kullanırken veri sunumunu özelleştirmeyi öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataTemplate [WPF], DataGrid
- row details [WPF], DataGrid
- DataGrid [WPF], row details
ms.assetid: 0bdc6f50-9b4c-483f-9df6-a47a1fde998b
ms.openlocfilehash: 8fd6b07f454681a0eed70d7a6208cfcc426dc920
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164955"
---
# <a name="how-to-add-row-details-to-a-datagrid-control"></a>Nasıl yapılır: DataGrid Denetimine Satır Ayrıntıları Ekleme
<xref:System.Windows.Controls.DataGrid>Denetimi kullanırken, bir satır ayrıntıları bölümü ekleyerek veri sunumunu özelleştirebilirsiniz. Satır ayrıntıları bölümü eklemek, bazı verileri isteğe bağlı olarak görünür veya daraltılmış bir şablonda gruplandırmanızı sağlar. Örneğin, <xref:System.Windows.Controls.DataGrid> yalnızca içindeki her bir satır için verilerin bir özetini sunan öğesine satır ayrıntıları ekleyebilirsiniz <xref:System.Windows.Controls.DataGrid> , ancak kullanıcı bir satır seçtiğinde daha fazla veri alanı sunar. Özelliği içindeki satır ayrıntıları bölümünün şablonunu tanımlarsınız <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> . Aşağıdaki çizimde, bir satır ayrıntıları Bölümü örneği gösterilmektedir.  
  
 ![Satır ayrıntılarıyla gösterilen DataGrid](./media/ndp-rowdetails.png "NDP_RowDetails")  
  
 Satır ayrıntıları şablonunu satır içi XAML veya kaynak olarak tanımlarsınız. Aşağıdaki yordamlarda her iki yaklaşım da gösterilmiştir. Kaynak olarak eklenen bir veri şablonu, şablonu yeniden oluşturmadan proje genelinde kullanılabilir. Satır içi XAML olarak eklenen bir veri şablonuna yalnızca tanımlandığı denetimden erişilebilir.  
  
### <a name="to-display-row-details-by-using-inline-xaml"></a>Satır içi XAML kullanarak satır ayrıntılarını görüntüleme  
  
1. <xref:System.Windows.Controls.DataGrid>Bir veri kaynağından verileri görüntüleyen bir oluştur.  
  
2. <xref:System.Windows.Controls.DataGrid>Öğesinde, bir <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> öğesi ekleyin.  
  
3. <xref:System.Windows.DataTemplate>Satır ayrıntıları bölümünün görünümünü tanımlayan bir oluştur.  
  
     Aşağıdaki XAML, <xref:System.Windows.Controls.DataGrid> ve satır içi 'nin nasıl tanımlanacağını gösterir <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> . <xref:System.Windows.Controls.DataGrid>Her satırda üç değer ve satır seçildiğinde üç daha fazla değer görüntüler.  
  
     [!code-xaml[DataGrid_RowDetails#1](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml#1)]  
  
     Aşağıdaki kod, içinde görüntülenen verileri seçmek için kullanılan sorguyu gösterir <xref:System.Windows.Controls.DataGrid> . Bu örnekte sorgu, müşteri bilgilerini içeren bir varlıktan veri seçer.  
  
     [!code-csharp[DataGrid_RowDetails#2](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml.cs#2)]
     [!code-vb[DataGrid_RowDetails#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_rowdetails/vb/mainwindow.xaml.vb#2)]  
  
### <a name="to-display-row-details-by-using-a-resource"></a>Kaynak kullanarak satır ayrıntılarını görüntüleme  
  
1. <xref:System.Windows.Controls.DataGrid>Bir veri kaynağından verileri görüntüleyen bir oluştur.  
  
2. Bir <xref:System.Windows.FrameworkElement.Resources%2A> Denetim veya denetim gibi kök öğeye bir öğe ekleyin <xref:System.Windows.Window> <xref:System.Windows.Controls.Page> veya <xref:System.Windows.Application.Resources%2A> <xref:System.Windows.Application> app. xaml (veya Application. xaml) dosyasındaki sınıfa bir öğe ekleyin.  
  
3. Resources öğesinde, <xref:System.Windows.DataTemplate> satır ayrıntıları bölümünün görünümünü tanımlayan bir oluştur.  
  
     Aşağıdaki XAML, <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> sınıfında tanımlanan öğesini gösterir <xref:System.Windows.Application> .  
  
     [!code-xaml[DataGrid_RowDetails#3](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/app.xaml#3)]  
  
4. Üzerinde <xref:System.Windows.DataTemplate> , [X:Key yönergesini](../../../desktop-wpf/xaml-services/xkey-directive.md) veri şablonunu benzersiz bir şekilde tanımlayan bir değere ayarlayın.  
  
5. <xref:System.Windows.Controls.DataGrid>Öğesinde, <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> özelliğini önceki adımlarda tanımlanan kaynak olarak ayarlayın. Kaynağı bir statik kaynak olarak atayın.  
  
     Aşağıdaki XAML, <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> önceki örnekteki kaynak olarak ayarlanan özelliği gösterir.  
  
     [!code-xaml[DataGrid_RowDetails#4](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/window2.xaml#4)]  
  
### <a name="to-set-visibility-and-prevent-horizontal-scrolling-for-row-details"></a>Görünürlük ayarlamak ve satır ayrıntıları için yatay kaydırmayı engellemek için  
  
1. Gerekirse, <xref:System.Windows.Controls.DataGrid.RowDetailsVisibilityMode%2A> özelliği bir değer olarak ayarlayın <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode> .  
  
     Varsayılan olarak, değeri olarak ayarlanır <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.VisibleWhenSelected> . Tüm <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Visible> satırların ayrıntılarını gösterecek şekilde veya <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Collapsed> tüm satırların ayrıntılarını gizleyecek şekilde ayarlayabilirsiniz.  
  
2. Gerekirse, <xref:System.Windows.Controls.DataGrid.AreRowDetailsFrozen%2A> `true` satır ayrıntıları bölümünün yatay olarak kaymasını engellemek için özelliğini olarak ayarlayın.
