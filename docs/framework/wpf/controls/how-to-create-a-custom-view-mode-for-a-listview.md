---
title: "Nasıl yapılır: ListView için Özel Görünüm Modu Oluşturma"
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
helpviewer_keywords: ListView controls [WPF], creating custom View mode
ms.assetid: 71077349-eeb9-4344-ab29-b5df96df3314
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c62bcb14f444490991b36dc21eb7676a67007906
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-custom-view-mode-for-a-listview"></a><span data-ttu-id="7c34c-102">Nasıl yapılır: ListView için Özel Görünüm Modu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="7c34c-102">How to: Create a Custom View Mode for a ListView</span></span>
<span data-ttu-id="7c34c-103">Bu örnek özel bir oluşturulacağını gösterir <xref:System.Windows.Controls.ListView.View%2A> modu için bir <xref:System.Windows.Controls.ListView> denetim.</span><span class="sxs-lookup"><span data-stu-id="7c34c-103">This example shows how to create a custom <xref:System.Windows.Controls.ListView.View%2A> mode for a <xref:System.Windows.Controls.ListView> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c34c-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="7c34c-104">Example</span></span>  
 <span data-ttu-id="7c34c-105">Kullanmalısınız <xref:System.Windows.Controls.ViewBase> sınıfı için özel bir görünüm oluşturduğunuzda <xref:System.Windows.Controls.ListView> denetim.</span><span class="sxs-lookup"><span data-stu-id="7c34c-105">You must use the <xref:System.Windows.Controls.ViewBase> class when you create a custom view for the <xref:System.Windows.Controls.ListView> control.</span></span> <span data-ttu-id="7c34c-106">Aşağıdaki örnek adı verilen bir görüntüleme modunu gösterir `PlainView`, türetilen <xref:System.Windows.Controls.ViewBase> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7c34c-106">The following example shows a view mode that is called `PlainView`, which is derived from the <xref:System.Windows.Controls.ViewBase> class.</span></span>  
  
 [!code-csharp[ListViewCustomView#PlainView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/PlainView.cs#plainview)]
 [!code-vb[ListViewCustomView#PlainView](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/plainview.vb#plainview)]  
  
 <span data-ttu-id="7c34c-107">Özel Görünüm için bir stil uygulamak için kullanmak <xref:System.Windows.Style> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7c34c-107">To apply a style to the custom view, use the <xref:System.Windows.Style> class.</span></span> <span data-ttu-id="7c34c-108">Aşağıdaki örnek tanımlayan bir <xref:System.Windows.Style> için `PlainView` görüntüleme modu.</span><span class="sxs-lookup"><span data-stu-id="7c34c-108">The following example defines a <xref:System.Windows.Style> for the `PlainView` view mode.</span></span> <span data-ttu-id="7c34c-109">Önceki örnekte bu stili değeri olarak ayarlanır <xref:System.Windows.Controls.ViewBase.DefaultStyleKey%2A> için tanımlı özellik `PlainView`.</span><span class="sxs-lookup"><span data-stu-id="7c34c-109">In the previous example, this style is set as the value of the <xref:System.Windows.Controls.ViewBase.DefaultStyleKey%2A> property that is defined for `PlainView`.</span></span>  
  
 [!code-xaml[ListViewCustomView#PlainViewStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Themes/Generic.xaml#plainviewstyle)]  
  
 <span data-ttu-id="7c34c-110">Özel Görünüm modunda veri düzenini tanımlamak için tanımlayan bir <xref:System.Windows.DataTemplate> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="7c34c-110">To define the layout of data in a custom view mode, define a <xref:System.Windows.DataTemplate> object.</span></span> <span data-ttu-id="7c34c-111">Aşağıdaki örnek tanımlayan bir <xref:System.Windows.DataTemplate> verileri görüntülemek için kullanılabilir `PlainView` görüntüleme modu.</span><span class="sxs-lookup"><span data-stu-id="7c34c-111">The following example defines a <xref:System.Windows.DataTemplate> that can be used to display data in the `PlainView` view mode.</span></span>  
  
 [!code-xaml[ListViewCustomView#PlainViewDataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewdatatemplate)]  
  
 <span data-ttu-id="7c34c-112">Aşağıdaki örnekte nasıl tanımlanacağı gösterilmektedir bir <xref:System.Windows.ResourceKey> için `PlainView` kullanan görüntüleme modu <xref:System.Windows.DataTemplate> önceki örnekte tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="7c34c-112">The following example shows how to define a <xref:System.Windows.ResourceKey> for the `PlainView` view mode that uses the <xref:System.Windows.DataTemplate> that is defined in the previous example.</span></span>  
  
 [!code-xaml[ListViewCustomView#PlainViewtileView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewtileview)]  
  
 <span data-ttu-id="7c34c-113">A <xref:System.Windows.Controls.ListView> denetimi, özel bir görünüm kullanabilir, ayarlarsanız <xref:System.Windows.Controls.ListView.View%2A> özelliği için kaynak anahtarı.</span><span class="sxs-lookup"><span data-stu-id="7c34c-113">A <xref:System.Windows.Controls.ListView> control can use a custom view if you set the <xref:System.Windows.Controls.ListView.View%2A> property to the resource key.</span></span> <span data-ttu-id="7c34c-114">Aşağıdaki örnekte nasıl belirtileceğini gösterir `PlainView` için görüntüleme modu olarak bir <xref:System.Windows.Controls.ListView>.</span><span class="sxs-lookup"><span data-stu-id="7c34c-114">The following example shows how to specify `PlainView` as the view mode for a <xref:System.Windows.Controls.ListView>.</span></span>  
  
 [!code-csharp[ListViewCustomView#ListViewtileViewmode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml.cs#listviewtileviewmode)]
 [!code-vb[ListViewCustomView#ListViewtileViewmode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/window1.xaml.vb#listviewtileviewmode)]  
  
 <span data-ttu-id="7c34c-115">Tam bir örnek için bkz: [ListView birden çok görünümler örnek ile](http://go.microsoft.com/fwlink/?LinkID=160013).</span><span class="sxs-lookup"><span data-stu-id="7c34c-115">For the complete sample, see [ListView with Multiple Views Sample](http://go.microsoft.com/fwlink/?LinkID=160013).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c34c-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7c34c-116">See Also</span></span>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [<span data-ttu-id="7c34c-117">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="7c34c-117">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [<span data-ttu-id="7c34c-118">ListView Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="7c34c-118">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [<span data-ttu-id="7c34c-119">GridView genel bakış</span><span class="sxs-lookup"><span data-stu-id="7c34c-119">GridView Overview</span></span>](../../../../docs/framework/wpf/controls/gridview-overview.md)
