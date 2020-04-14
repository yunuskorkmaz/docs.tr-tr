---
title: 'Nasıl yapılır: ListView için Özel Görünüm Modu Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], creating custom View mode
ms.assetid: 71077349-eeb9-4344-ab29-b5df96df3314
ms.openlocfilehash: 3b9ca17bddcecb1895205fca76f0a489ecf25c4f
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243225"
---
# <a name="how-to-create-a-custom-view-mode-for-a-listview"></a><span data-ttu-id="6789b-102">Nasıl yapilir: ListView için özel bir görünüm modu oluşturma</span><span class="sxs-lookup"><span data-stu-id="6789b-102">How to: Create a custom view mode for a ListView</span></span>

<span data-ttu-id="6789b-103">Bu örnek, denetim <xref:System.Windows.Controls.ListView.View%2A> <xref:System.Windows.Controls.ListView> için özel bir modun nasıl oluşturulurunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="6789b-103">This example shows how to create a custom <xref:System.Windows.Controls.ListView.View%2A> mode for a <xref:System.Windows.Controls.ListView> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6789b-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="6789b-104">Example</span></span>  
 <span data-ttu-id="6789b-105">Denetim için <xref:System.Windows.Controls.ViewBase> özel bir görünüm oluştururken sınıfı kullanmanız gerekir. <xref:System.Windows.Controls.ListView></span><span class="sxs-lookup"><span data-stu-id="6789b-105">You must use the <xref:System.Windows.Controls.ViewBase> class when you create a custom view for the <xref:System.Windows.Controls.ListView> control.</span></span> <span data-ttu-id="6789b-106">Aşağıdaki örnek, `PlainView` <xref:System.Windows.Controls.ViewBase> sınıftan türetilen bir görünüm modu gösterir.</span><span class="sxs-lookup"><span data-stu-id="6789b-106">The following example shows a view mode called `PlainView` that's derived from the <xref:System.Windows.Controls.ViewBase> class.</span></span>  
  
 [!code-csharp[ListViewCustomView#PlainView](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/PlainView.cs#plainview)]
 [!code-vb[ListViewCustomView#PlainView](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/plainview.vb#plainview)]  
  
 <span data-ttu-id="6789b-107">Özel görünüme stil uygulamak için <xref:System.Windows.Style> sınıfı kullanın.</span><span class="sxs-lookup"><span data-stu-id="6789b-107">To apply a style to the custom view, use the <xref:System.Windows.Style> class.</span></span> <span data-ttu-id="6789b-108">Aşağıdaki örnekte <xref:System.Windows.Style> `PlainView` görünüm modu için bir tanımvardır.</span><span class="sxs-lookup"><span data-stu-id="6789b-108">The following example defines a <xref:System.Windows.Style> for the `PlainView` view mode.</span></span> <span data-ttu-id="6789b-109">Önceki örnekte, bu stil için <xref:System.Windows.Controls.ViewBase.DefaultStyleKey%2A> `PlainView`tanımlanan özelliğin değeri olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="6789b-109">In the previous example, this style is set as the value of the <xref:System.Windows.Controls.ViewBase.DefaultStyleKey%2A> property that's defined for `PlainView`.</span></span>  
  
 [!code-xaml[ListViewCustomView#PlainViewStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Themes/Generic.xaml#plainviewstyle)]  
  
 <span data-ttu-id="6789b-110">Özel görünüm modunda verilerin düzenini tanımlamak için <xref:System.Windows.DataTemplate> bir nesne tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="6789b-110">To define the layout of data in a custom view mode, define a <xref:System.Windows.DataTemplate> object.</span></span> <span data-ttu-id="6789b-111">Aşağıdaki örnek, <xref:System.Windows.DataTemplate> `PlainView` görünüm modunda verileri görüntülemek için kullanılabilecek bir tanım tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6789b-111">The following example defines a <xref:System.Windows.DataTemplate> that can be used to display data in the `PlainView` view mode.</span></span>  
  
 [!code-xaml[ListViewCustomView#PlainViewDataTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewdatatemplate)]  
  
 <span data-ttu-id="6789b-112">Aşağıdaki örnek, önceki örnekte `PlainView` tanımlananı kullanan <xref:System.Windows.DataTemplate> görünüm moduiçin bir <xref:System.Windows.ResourceKey> modelin nasıl tanımlanır gösteriş yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6789b-112">The following example shows how to define a <xref:System.Windows.ResourceKey> for the `PlainView` view mode that uses the <xref:System.Windows.DataTemplate> that is defined in the previous example.</span></span>  
  
 [!code-xaml[ListViewCustomView#PlainViewtileView](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewtileview)]  
  
 <span data-ttu-id="6789b-113"><xref:System.Windows.Controls.ListView.View%2A> Özelliği <xref:System.Windows.Controls.ListView> kaynak anahtarına ayarlarsanız denetim özel bir görünüm kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="6789b-113">A <xref:System.Windows.Controls.ListView> control can use a custom view if you set the <xref:System.Windows.Controls.ListView.View%2A> property to the resource key.</span></span> <span data-ttu-id="6789b-114">Aşağıdaki örnekte, bir `PlainView` <xref:System.Windows.Controls.ListView>. için görünüm modu olarak nasıl belirtilir gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6789b-114">The following example shows how to specify `PlainView` as the view mode for a <xref:System.Windows.Controls.ListView>.</span></span>  
  
 [!code-csharp[ListViewCustomView#ListViewtileViewmode](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml.cs#listviewtileviewmode)]
 [!code-vb[ListViewCustomView#ListViewtileViewmode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/window1.xaml.vb#listviewtileviewmode)]  
  
 <span data-ttu-id="6789b-115">Tam örnek için, [Birden Çok Görüntülemeli ListView (C#)](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp) veya [Birden Çok Görüntülemeli ListView (Visual Basic)](https://github.com/dotnet/docs/tree/master/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic)bakın.</span><span class="sxs-lookup"><span data-stu-id="6789b-115">For the complete sample, see [ListView with Multiple Views (C#)](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp) or [ListView with Multiple Views (Visual Basic)](https://github.com/dotnet/docs/tree/master/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6789b-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6789b-116">See also</span></span>

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [<span data-ttu-id="6789b-117">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="6789b-117">How-to Topics</span></span>](listview-how-to-topics.md)
- [<span data-ttu-id="6789b-118">ListView Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="6789b-118">ListView Overview</span></span>](listview-overview.md)
- [<span data-ttu-id="6789b-119">GridView Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="6789b-119">GridView Overview</span></span>](gridview-overview.md)
