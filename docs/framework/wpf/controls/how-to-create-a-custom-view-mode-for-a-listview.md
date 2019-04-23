---
title: 'Nasıl yapılır: ListView için Özel Görünüm Modu Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], creating custom View mode
ms.assetid: 71077349-eeb9-4344-ab29-b5df96df3314
ms.openlocfilehash: de11250a2e7529fba3b262e42b6714262738fa90
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59092896"
---
# <a name="how-to-create-a-custom-view-mode-for-a-listview"></a><span data-ttu-id="60bcb-102">Nasıl yapılır: ListView için Özel Görünüm Modu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="60bcb-102">How to: Create a Custom View Mode for a ListView</span></span>
<span data-ttu-id="60bcb-103">Bu örnekte, özel bir oluşturma işlemi gösterilmektedir <xref:System.Windows.Controls.ListView.View%2A> modu için bir <xref:System.Windows.Controls.ListView> denetimi.</span><span class="sxs-lookup"><span data-stu-id="60bcb-103">This example shows how to create a custom <xref:System.Windows.Controls.ListView.View%2A> mode for a <xref:System.Windows.Controls.ListView> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="60bcb-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="60bcb-104">Example</span></span>  
 <span data-ttu-id="60bcb-105">Kullanmalısınız <xref:System.Windows.Controls.ViewBase> sınıfı için özel bir görünüm oluşturduğunuzda <xref:System.Windows.Controls.ListView> denetimi.</span><span class="sxs-lookup"><span data-stu-id="60bcb-105">You must use the <xref:System.Windows.Controls.ViewBase> class when you create a custom view for the <xref:System.Windows.Controls.ListView> control.</span></span> <span data-ttu-id="60bcb-106">Aşağıdaki örnekte adlı bir görünüm modu `PlainView`, türetilen <xref:System.Windows.Controls.ViewBase> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="60bcb-106">The following example shows a view mode that is called `PlainView`, which is derived from the <xref:System.Windows.Controls.ViewBase> class.</span></span>  
  
 [!code-csharp[ListViewCustomView#PlainView](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/PlainView.cs#plainview)]
 [!code-vb[ListViewCustomView#PlainView](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/plainview.vb#plainview)]  
  
 <span data-ttu-id="60bcb-107">Özel Görünüm için bir stil uygulamak için kullanma <xref:System.Windows.Style> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="60bcb-107">To apply a style to the custom view, use the <xref:System.Windows.Style> class.</span></span> <span data-ttu-id="60bcb-108">Aşağıdaki örnekte tanımlayan bir <xref:System.Windows.Style> için `PlainView` görünüm modu.</span><span class="sxs-lookup"><span data-stu-id="60bcb-108">The following example defines a <xref:System.Windows.Style> for the `PlainView` view mode.</span></span> <span data-ttu-id="60bcb-109">Önceki örnekte, bu stil değeri olarak ayarlanır <xref:System.Windows.Controls.ViewBase.DefaultStyleKey%2A> için tanımlanan özellik `PlainView`.</span><span class="sxs-lookup"><span data-stu-id="60bcb-109">In the previous example, this style is set as the value of the <xref:System.Windows.Controls.ViewBase.DefaultStyleKey%2A> property that is defined for `PlainView`.</span></span>  
  
 [!code-xaml[ListViewCustomView#PlainViewStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Themes/Generic.xaml#plainviewstyle)]  
  
 <span data-ttu-id="60bcb-110">Bir özel görünüm modunda verilerin düzeni tanımlamak için tanımladığınız bir <xref:System.Windows.DataTemplate> nesne.</span><span class="sxs-lookup"><span data-stu-id="60bcb-110">To define the layout of data in a custom view mode, define a <xref:System.Windows.DataTemplate> object.</span></span> <span data-ttu-id="60bcb-111">Aşağıdaki örnekte tanımlayan bir <xref:System.Windows.DataTemplate> verileri görüntülemek için kullanılabilecek `PlainView` görünüm modu.</span><span class="sxs-lookup"><span data-stu-id="60bcb-111">The following example defines a <xref:System.Windows.DataTemplate> that can be used to display data in the `PlainView` view mode.</span></span>  
  
 [!code-xaml[ListViewCustomView#PlainViewDataTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewdatatemplate)]  
  
 <span data-ttu-id="60bcb-112">Aşağıdaki örnek nasıl tanımlanacağını gösterir bir <xref:System.Windows.ResourceKey> için `PlainView` kullanan görünüm modu <xref:System.Windows.DataTemplate> önceki örnekte tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="60bcb-112">The following example shows how to define a <xref:System.Windows.ResourceKey> for the `PlainView` view mode that uses the <xref:System.Windows.DataTemplate> that is defined in the previous example.</span></span>  
  
 [!code-xaml[ListViewCustomView#PlainViewtileView](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewtileview)]  
  
 <span data-ttu-id="60bcb-113">A <xref:System.Windows.Controls.ListView> denetimi, özel bir görünüm kullanabilirsiniz, ayarlarsanız <xref:System.Windows.Controls.ListView.View%2A> özelliğini kaynak anahtarı.</span><span class="sxs-lookup"><span data-stu-id="60bcb-113">A <xref:System.Windows.Controls.ListView> control can use a custom view if you set the <xref:System.Windows.Controls.ListView.View%2A> property to the resource key.</span></span> <span data-ttu-id="60bcb-114">Aşağıdaki örnek nasıl belirtileceğini gösterir `PlainView` görünüm modu için bir <xref:System.Windows.Controls.ListView>.</span><span class="sxs-lookup"><span data-stu-id="60bcb-114">The following example shows how to specify `PlainView` as the view mode for a <xref:System.Windows.Controls.ListView>.</span></span>  
  
 [!code-csharp[ListViewCustomView#ListViewtileViewmode](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml.cs#listviewtileviewmode)]
 [!code-vb[ListViewCustomView#ListViewtileViewmode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/window1.xaml.vb#listviewtileviewmode)]  
  
 <span data-ttu-id="60bcb-115">Tam bir örnek için bkz. [ListView birden çok görünüm ile (C#)](https://github.com/dotnet/samples/tree/master/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp) veya [ListView ile birden çok Views(Visual Basic)](https://github.com/dotnet/samples/tree/master/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic).</span><span class="sxs-lookup"><span data-stu-id="60bcb-115">For the complete sample, see [ListView with Multiple Views(C#)](https://github.com/dotnet/samples/tree/master/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp) or [ListView with Multiple Views(Visual Basic)](https://github.com/dotnet/samples/tree/master/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60bcb-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="60bcb-116">See also</span></span>

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [<span data-ttu-id="60bcb-117">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="60bcb-117">How-to Topics</span></span>](listview-how-to-topics.md)
- [<span data-ttu-id="60bcb-118">ListView Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="60bcb-118">ListView Overview</span></span>](listview-overview.md)
- [<span data-ttu-id="60bcb-119">GridView Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="60bcb-119">GridView Overview</span></span>](gridview-overview.md)
