---
title: 'Nasıl yapılır: GridView Kullanarak ListView İçeriklerini Görüntüleme'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], displaying contents with GridView
- GridView [WPF], displaying ListView contents
ms.assetid: 5bc1e767-ab46-4f14-bd41-3d5d39e1d000
ms.openlocfilehash: 9a4bcc8b613637521ee91a11b0bdac8f77f90a03
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57354407"
---
# <a name="how-to-display-listview-contents-by-using-a-gridview"></a><span data-ttu-id="97a05-102">Nasıl yapılır: GridView Kullanarak ListView İçeriklerini Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="97a05-102">How to: Display ListView Contents by Using a GridView</span></span>
<span data-ttu-id="97a05-103">Bu örnek nasıl tanımlanacağını gösterir bir <xref:System.Windows.Controls.GridView> görünüm modu için bir <xref:System.Windows.Controls.ListView> denetimi.</span><span class="sxs-lookup"><span data-stu-id="97a05-103">This example shows how to define a <xref:System.Windows.Controls.GridView> view mode for a <xref:System.Windows.Controls.ListView> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="97a05-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="97a05-104">Example</span></span>  
 <span data-ttu-id="97a05-105">Görünüm modu, tanımladığınız bir <xref:System.Windows.Controls.GridView> belirterek <xref:System.Windows.Controls.GridViewColumn> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="97a05-105">You can define the view mode of a <xref:System.Windows.Controls.GridView> by specifying <xref:System.Windows.Controls.GridViewColumn> objects.</span></span> <span data-ttu-id="97a05-106">Aşağıdaki örnek nasıl tanımlanacağını gösterir <xref:System.Windows.Controls.GridViewColumn> için belirtilen veri içeriği bağlama nesnelerini <xref:System.Windows.Controls.ListView> denetimi.</span><span class="sxs-lookup"><span data-stu-id="97a05-106">The following example shows how to define <xref:System.Windows.Controls.GridViewColumn> objects that bind to the data content that is specified for the <xref:System.Windows.Controls.ListView> control.</span></span> <span data-ttu-id="97a05-107">Bu <xref:System.Windows.Controls.GridView> örnek üç belirtir <xref:System.Windows.Controls.GridViewColumn> eşleyen nesneleri `FirstName`, `LastName`, ve `EmployeeNumber` alanlarının `EmployeeInfoDataSource` olarak ayarlanan <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> , <xref:System.Windows.Controls.ListView> denetimi.</span><span class="sxs-lookup"><span data-stu-id="97a05-107">This <xref:System.Windows.Controls.GridView> example specifies three <xref:System.Windows.Controls.GridViewColumn> objects that map to the `FirstName`, `LastName`, and `EmployeeNumber` fields of the `EmployeeInfoDataSource` that is set as the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> of the <xref:System.Windows.Controls.ListView> control.</span></span>  
  
 [!code-xaml[ListViewCode#ListViewEmployee](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 <span data-ttu-id="97a05-108">Bu örnek nasıl göründüğü aşağıda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="97a05-108">The following illustration shows how this example appears.</span></span>  
  
 <span data-ttu-id="97a05-109">![ListView GridView çıktıyla](./media/listviewgridview.JPG "ListViewGridView")</span><span class="sxs-lookup"><span data-stu-id="97a05-109">![ListView with GridView output](./media/listviewgridview.JPG "ListViewGridView")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97a05-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="97a05-110">See also</span></span>
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [<span data-ttu-id="97a05-111">ListView Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="97a05-111">ListView Overview</span></span>](listview-overview.md)
- [<span data-ttu-id="97a05-112">GridView Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="97a05-112">GridView Overview</span></span>](gridview-overview.md)
- [<span data-ttu-id="97a05-113">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="97a05-113">How-to Topics</span></span>](listview-how-to-topics.md)
