---
title: "Nasıl yapılır: GridView Kullanarak ListView İçeriklerini Görüntüleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ListView controls [WPF], displaying contents with GridView
- GridView [WPF], displaying ListView contents
ms.assetid: 5bc1e767-ab46-4f14-bd41-3d5d39e1d000
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 24560a1e9b663a3145b589b5a03af8a8b72236ec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-listview-contents-by-using-a-gridview"></a><span data-ttu-id="7b315-102">Nasıl yapılır: GridView Kullanarak ListView İçeriklerini Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="7b315-102">How to: Display ListView Contents by Using a GridView</span></span>
<span data-ttu-id="7b315-103">Bu örnek nasıl tanımlanacağı gösterilmektedir bir <xref:System.Windows.Controls.GridView> görüntüleme modu için bir <xref:System.Windows.Controls.ListView> denetim.</span><span class="sxs-lookup"><span data-stu-id="7b315-103">This example shows how to define a <xref:System.Windows.Controls.GridView> view mode for a <xref:System.Windows.Controls.ListView> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7b315-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="7b315-104">Example</span></span>  
 <span data-ttu-id="7b315-105">Görünüm modunu tanımlayabilirsiniz bir <xref:System.Windows.Controls.GridView> belirterek <xref:System.Windows.Controls.GridViewColumn> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="7b315-105">You can define the view mode of a <xref:System.Windows.Controls.GridView> by specifying <xref:System.Windows.Controls.GridViewColumn> objects.</span></span> <span data-ttu-id="7b315-106">Aşağıdaki örnekte nasıl tanımlanacağı gösterilmektedir <xref:System.Windows.Controls.GridViewColumn> için belirtilen veri içeriğine bağlanan nesneleri <xref:System.Windows.Controls.ListView> denetim.</span><span class="sxs-lookup"><span data-stu-id="7b315-106">The following example shows how to define <xref:System.Windows.Controls.GridViewColumn> objects that bind to the data content that is specified for the <xref:System.Windows.Controls.ListView> control.</span></span> <span data-ttu-id="7b315-107">Bu <xref:System.Windows.Controls.GridView> örnek belirtir üç <xref:System.Windows.Controls.GridViewColumn> Eşle nesneleri `FirstName`, `LastName`, ve `EmployeeNumber` alanlarının `EmployeeInfoDataSource` olarak ayarlanmış <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> , <xref:System.Windows.Controls.ListView> denetim.</span><span class="sxs-lookup"><span data-stu-id="7b315-107">This <xref:System.Windows.Controls.GridView> example specifies three <xref:System.Windows.Controls.GridViewColumn> objects that map to the `FirstName`, `LastName`, and `EmployeeNumber` fields of the `EmployeeInfoDataSource` that is set as the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> of the <xref:System.Windows.Controls.ListView> control.</span></span>  
  
 [!code-xaml[ListViewCode#ListViewEmployee](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 <span data-ttu-id="7b315-108">Aşağıdaki çizimde, bu örnek nasıl göründüğünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="7b315-108">The following illustration shows how this example appears.</span></span>  
  
 <span data-ttu-id="7b315-109">![GridView çıkışıyla ListView](../../../../docs/framework/wpf/controls/media/listviewgridview.JPG "ListViewGridView")</span><span class="sxs-lookup"><span data-stu-id="7b315-109">![ListView with GridView output](../../../../docs/framework/wpf/controls/media/listviewgridview.JPG "ListViewGridView")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b315-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7b315-110">See Also</span></span>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [<span data-ttu-id="7b315-111">ListView Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="7b315-111">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [<span data-ttu-id="7b315-112">GridView genel bakış</span><span class="sxs-lookup"><span data-stu-id="7b315-112">GridView Overview</span></span>](../../../../docs/framework/wpf/controls/gridview-overview.md)  
 [<span data-ttu-id="7b315-113">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="7b315-113">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)
