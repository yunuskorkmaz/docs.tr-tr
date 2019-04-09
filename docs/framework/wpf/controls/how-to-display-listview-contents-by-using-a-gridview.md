---
title: 'Nasıl yapılır: GridView Kullanarak ListView İçeriklerini Görüntüleme'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], displaying contents with GridView
- GridView [WPF], displaying ListView contents
ms.assetid: 5bc1e767-ab46-4f14-bd41-3d5d39e1d000
ms.openlocfilehash: 9b467c95d541c326a41d1ed4bd9eb5c87e25bd5c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59112794"
---
# <a name="how-to-display-listview-contents-by-using-a-gridview"></a><span data-ttu-id="5327d-102">Nasıl yapılır: GridView Kullanarak ListView İçeriklerini Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="5327d-102">How to: Display ListView Contents by Using a GridView</span></span>
<span data-ttu-id="5327d-103">Bu örnek nasıl tanımlanacağını gösterir bir <xref:System.Windows.Controls.GridView> görünüm modu için bir <xref:System.Windows.Controls.ListView> denetimi.</span><span class="sxs-lookup"><span data-stu-id="5327d-103">This example shows how to define a <xref:System.Windows.Controls.GridView> view mode for a <xref:System.Windows.Controls.ListView> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5327d-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="5327d-104">Example</span></span>  
 <span data-ttu-id="5327d-105">Görünüm modu, tanımladığınız bir <xref:System.Windows.Controls.GridView> belirterek <xref:System.Windows.Controls.GridViewColumn> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="5327d-105">You can define the view mode of a <xref:System.Windows.Controls.GridView> by specifying <xref:System.Windows.Controls.GridViewColumn> objects.</span></span> <span data-ttu-id="5327d-106">Aşağıdaki örnek nasıl tanımlanacağını gösterir <xref:System.Windows.Controls.GridViewColumn> için belirtilen veri içeriği bağlama nesnelerini <xref:System.Windows.Controls.ListView> denetimi.</span><span class="sxs-lookup"><span data-stu-id="5327d-106">The following example shows how to define <xref:System.Windows.Controls.GridViewColumn> objects that bind to the data content that is specified for the <xref:System.Windows.Controls.ListView> control.</span></span> <span data-ttu-id="5327d-107">Bu <xref:System.Windows.Controls.GridView> örnek üç belirtir <xref:System.Windows.Controls.GridViewColumn> eşleyen nesneleri `FirstName`, `LastName`, ve `EmployeeNumber` alanlarının `EmployeeInfoDataSource` olarak ayarlanan <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> , <xref:System.Windows.Controls.ListView> denetimi.</span><span class="sxs-lookup"><span data-stu-id="5327d-107">This <xref:System.Windows.Controls.GridView> example specifies three <xref:System.Windows.Controls.GridViewColumn> objects that map to the `FirstName`, `LastName`, and `EmployeeNumber` fields of the `EmployeeInfoDataSource` that is set as the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> of the <xref:System.Windows.Controls.ListView> control.</span></span>  
  
 [!code-xaml[ListViewCode#ListViewEmployee](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 <span data-ttu-id="5327d-108">Bu örnek nasıl göründüğü aşağıda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="5327d-108">The following illustration shows how this example appears.</span></span>  
  
 ![Bir ListView GridView çıktıyla gösteren ekran görüntüsü.](./media/gridview-overview/listview-gridview-output.jpg)  
  
## <a name="see-also"></a><span data-ttu-id="5327d-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5327d-110">See also</span></span>

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [<span data-ttu-id="5327d-111">ListView Genel Bakışı</span><span class="sxs-lookup"><span data-stu-id="5327d-111">ListView Overview</span></span>](listview-overview.md)
- [<span data-ttu-id="5327d-112">GridView Genel Bakışı</span><span class="sxs-lookup"><span data-stu-id="5327d-112">GridView Overview</span></span>](gridview-overview.md)
- [<span data-ttu-id="5327d-113">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="5327d-113">How-to Topics</span></span>](listview-how-to-topics.md)
