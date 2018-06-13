---
title: 'Nasıl yapılır: GridView Kullanarak ListView İçeriklerini Görüntüleme'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], displaying contents with GridView
- GridView [WPF], displaying ListView contents
ms.assetid: 5bc1e767-ab46-4f14-bd41-3d5d39e1d000
ms.openlocfilehash: 103a439b9cee959d0077e5a759364eb9b943905d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33554057"
---
# <a name="how-to-display-listview-contents-by-using-a-gridview"></a><span data-ttu-id="e8f73-102">Nasıl yapılır: GridView Kullanarak ListView İçeriklerini Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="e8f73-102">How to: Display ListView Contents by Using a GridView</span></span>
<span data-ttu-id="e8f73-103">Bu örnek nasıl tanımlanacağı gösterilmektedir bir <xref:System.Windows.Controls.GridView> görüntüleme modu için bir <xref:System.Windows.Controls.ListView> denetim.</span><span class="sxs-lookup"><span data-stu-id="e8f73-103">This example shows how to define a <xref:System.Windows.Controls.GridView> view mode for a <xref:System.Windows.Controls.ListView> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8f73-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="e8f73-104">Example</span></span>  
 <span data-ttu-id="e8f73-105">Görünüm modunu tanımlayabilirsiniz bir <xref:System.Windows.Controls.GridView> belirterek <xref:System.Windows.Controls.GridViewColumn> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="e8f73-105">You can define the view mode of a <xref:System.Windows.Controls.GridView> by specifying <xref:System.Windows.Controls.GridViewColumn> objects.</span></span> <span data-ttu-id="e8f73-106">Aşağıdaki örnekte nasıl tanımlanacağı gösterilmektedir <xref:System.Windows.Controls.GridViewColumn> için belirtilen veri içeriğine bağlanan nesneleri <xref:System.Windows.Controls.ListView> denetim.</span><span class="sxs-lookup"><span data-stu-id="e8f73-106">The following example shows how to define <xref:System.Windows.Controls.GridViewColumn> objects that bind to the data content that is specified for the <xref:System.Windows.Controls.ListView> control.</span></span> <span data-ttu-id="e8f73-107">Bu <xref:System.Windows.Controls.GridView> örnek belirtir üç <xref:System.Windows.Controls.GridViewColumn> Eşle nesneleri `FirstName`, `LastName`, ve `EmployeeNumber` alanlarının `EmployeeInfoDataSource` olarak ayarlanmış <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> , <xref:System.Windows.Controls.ListView> denetim.</span><span class="sxs-lookup"><span data-stu-id="e8f73-107">This <xref:System.Windows.Controls.GridView> example specifies three <xref:System.Windows.Controls.GridViewColumn> objects that map to the `FirstName`, `LastName`, and `EmployeeNumber` fields of the `EmployeeInfoDataSource` that is set as the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> of the <xref:System.Windows.Controls.ListView> control.</span></span>  
  
 [!code-xaml[ListViewCode#ListViewEmployee](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 <span data-ttu-id="e8f73-108">Aşağıdaki çizimde, bu örnek nasıl göründüğünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="e8f73-108">The following illustration shows how this example appears.</span></span>  
  
 <span data-ttu-id="e8f73-109">![GridView çıkışıyla ListView](../../../../docs/framework/wpf/controls/media/listviewgridview.JPG "ListViewGridView")</span><span class="sxs-lookup"><span data-stu-id="e8f73-109">![ListView with GridView output](../../../../docs/framework/wpf/controls/media/listviewgridview.JPG "ListViewGridView")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8f73-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e8f73-110">See Also</span></span>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [<span data-ttu-id="e8f73-111">ListView Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e8f73-111">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [<span data-ttu-id="e8f73-112">GridView Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e8f73-112">GridView Overview</span></span>](../../../../docs/framework/wpf/controls/gridview-overview.md)  
 [<span data-ttu-id="e8f73-113">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="e8f73-113">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)
