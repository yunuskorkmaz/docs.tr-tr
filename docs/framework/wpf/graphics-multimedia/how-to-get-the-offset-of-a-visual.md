---
title: 'Nasıl yapılır: Görselin Sapmasını Alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting offset values from visual objects [WPF]
- offset values [WPF], retrieving from visual objects [WPF]
- visual objects [WPF], retrieving offset values from
- retrieving offset values from visual objects [WPF]
ms.assetid: 889a1dd6-1b11-445a-b351-fbb04c53ee34
ms.openlocfilehash: 4787b771c7e59a8b033b9267079c068a5845a1e6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59093416"
---
# <a name="how-to-get-the-offset-of-a-visual"></a><span data-ttu-id="f3830-102">Nasıl yapılır: Görselin Sapmasını Alma</span><span class="sxs-lookup"><span data-stu-id="f3830-102">How to: Get the Offset of a Visual</span></span>
<span data-ttu-id="f3830-103">Bu örnekler bir görsel nesnesinin veya tüm üst veya alt öğesi üst göre bir uzaklık değeri almak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="f3830-103">These examples show how to retrieve the offset value of a visual object that is relative to its parent, or any ancestor or descendant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3830-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="f3830-104">Example</span></span>  
 <span data-ttu-id="f3830-105">Aşağıdaki biçimlendirme örnekte gösterildiği bir <xref:System.Windows.Controls.TextBlock> ile tanımlanan <xref:System.Windows.FrameworkElement.Margin%2A> değeri 4.</span><span class="sxs-lookup"><span data-stu-id="f3830-105">The following markup example shows a <xref:System.Windows.Controls.TextBlock> that is defined with <xref:System.Windows.FrameworkElement.Margin%2A> value of 4.</span></span>  
  
 [!code-xaml[VisualSnippets#VisualSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml#visualsnippet1)]  
  
 <span data-ttu-id="f3830-106">Aşağıdaki kod örneği kullanma işlemini gösterir <xref:System.Windows.Media.VisualTreeHelper.GetOffset%2A> uzaklığı alınacak yöntemi <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="f3830-106">The following code example shows how to use the <xref:System.Windows.Media.VisualTreeHelper.GetOffset%2A> method to retrieve the offset of the <xref:System.Windows.Controls.TextBlock>.</span></span> <span data-ttu-id="f3830-107">Uzaklık değerleri içerdiği döndürülen içinde <xref:System.Windows.Vector> değeri.</span><span class="sxs-lookup"><span data-stu-id="f3830-107">The offset values are contained within the returned <xref:System.Windows.Vector> value.</span></span>  
  
 [!code-csharp[VisualSnippets#VisualSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml.cs#visualsnippet2)]
 [!code-vb[VisualSnippets#VisualSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualSnippets/visualbasic/window1.xaml.vb#visualsnippet2)]  
  
 <span data-ttu-id="f3830-108">Uzaklık dikkate <xref:System.Windows.FrameworkElement.Margin%2A> değeri.</span><span class="sxs-lookup"><span data-stu-id="f3830-108">The offset takes into account the <xref:System.Windows.FrameworkElement.Margin%2A> value.</span></span> <span data-ttu-id="f3830-109">Bu durumda, <xref:System.Windows.Vector.X%2A> 4'tür ve <xref:System.Windows.Vector.Y%2A> 4'tür.</span><span class="sxs-lookup"><span data-stu-id="f3830-109">In this case, <xref:System.Windows.Vector.X%2A> is 4, and <xref:System.Windows.Vector.Y%2A> is 4.</span></span>  
  
 <span data-ttu-id="f3830-110">Döndürülen uzaklık değeri üst göreli olan <xref:System.Windows.Media.Visual>.</span><span class="sxs-lookup"><span data-stu-id="f3830-110">The returned offset value is relative to the parent of the <xref:System.Windows.Media.Visual>.</span></span> <span data-ttu-id="f3830-111">Üst göreli değil bir uzaklık değeri döndürmek isterseniz bir <xref:System.Windows.Media.Visual>, kullanın <xref:System.Windows.Media.Visual.TransformToAncestor%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f3830-111">If you want to return an offset value that is not relative to the parent of a <xref:System.Windows.Media.Visual>, use the <xref:System.Windows.Media.Visual.TransformToAncestor%2A> method.</span></span>  
  
## <a name="getting-the-offset-relative-to-an-ancestor"></a><span data-ttu-id="f3830-112">Uzaklık bir üst aynı göreli alma</span><span class="sxs-lookup"><span data-stu-id="f3830-112">Getting the Offset Relative to an Ancestor</span></span>  
 <span data-ttu-id="f3830-113">Aşağıdaki biçimlendirme örnekte gösterildiği bir <xref:System.Windows.Controls.TextBlock> iç içe geçmiş iki içinde <xref:System.Windows.Controls.StackPanel> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="f3830-113">The following markup example shows a <xref:System.Windows.Controls.TextBlock> that is nested within two <xref:System.Windows.Controls.StackPanel> objects.</span></span>  
  
 [!code-xaml[VisualSnippets#VisualSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window2.xaml#visualsnippet7)]  
  
 <span data-ttu-id="f3830-114">Aşağıdaki çizim, biçimlendirme sonuçları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f3830-114">The following illustration shows the results of the markup.</span></span>  
  
 <span data-ttu-id="f3830-115">![Nesnelerin uzaklık değerleri](./media/visualoffset-01.png "VisualOffset_01")</span><span class="sxs-lookup"><span data-stu-id="f3830-115">![Offset values of objects](./media/visualoffset-01.png "VisualOffset_01")</span></span>  
<span data-ttu-id="f3830-116">İki StackPanels'in içine TextBlock</span><span class="sxs-lookup"><span data-stu-id="f3830-116">TextBlock nested within two StackPanels</span></span>  
  
 <span data-ttu-id="f3830-117">Aşağıdaki kod örneği kullanma işlemini gösterir <xref:System.Windows.Media.Visual.TransformToAncestor%2A> uzaklığı alınacak yöntemi <xref:System.Windows.Controls.TextBlock> içeren göre <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="f3830-117">The following code example shows how to use the <xref:System.Windows.Media.Visual.TransformToAncestor%2A> method to retrieve the offset of the <xref:System.Windows.Controls.TextBlock> relative to the containing <xref:System.Windows.Window>.</span></span> <span data-ttu-id="f3830-118">Uzaklık değerleri içerdiği döndürülen içinde <xref:System.Windows.Media.GeneralTransform> değeri.</span><span class="sxs-lookup"><span data-stu-id="f3830-118">The offset values are contained within the returned <xref:System.Windows.Media.GeneralTransform> value.</span></span>  
  
 [!code-csharp[VisualSnippets#VisualSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml.cs#visualsnippet5)]
 [!code-vb[VisualSnippets#VisualSnippet5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualSnippets/visualbasic/window1.xaml.vb#visualsnippet5)]  
  
 <span data-ttu-id="f3830-119">Uzaklık dikkate <xref:System.Windows.FrameworkElement.Margin%2A> değerleri içeren içindeki tüm nesneleri için <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="f3830-119">The offset takes into account the <xref:System.Windows.FrameworkElement.Margin%2A> values for all objects within the containing <xref:System.Windows.Window>.</span></span> <span data-ttu-id="f3830-120">Bu durumda, <xref:System.Windows.Vector.X%2A> 28 (16 + 8 +), 4 ve <xref:System.Windows.Vector.Y%2A> 28'dir.</span><span class="sxs-lookup"><span data-stu-id="f3830-120">In this case, <xref:System.Windows.Vector.X%2A> is 28 (16 + 8 + 4), and <xref:System.Windows.Vector.Y%2A> is 28.</span></span>  
  
 <span data-ttu-id="f3830-121">Döndürülen uzaklık değeri üst göreli olan <xref:System.Windows.Media.Visual>.</span><span class="sxs-lookup"><span data-stu-id="f3830-121">The returned offset value is relative to the ancestor of the <xref:System.Windows.Media.Visual>.</span></span> <span data-ttu-id="f3830-122">Alt öğesi için göreli bir uzaklık değeri döndürmek isterseniz bir <xref:System.Windows.Media.Visual>, kullanın <xref:System.Windows.Media.Visual.TransformToDescendant%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f3830-122">If you want to return an offset value that is relative to the descendant of a <xref:System.Windows.Media.Visual>, use the <xref:System.Windows.Media.Visual.TransformToDescendant%2A> method.</span></span>  
  
## <a name="getting-the-offset-relative-to-a-descendant"></a><span data-ttu-id="f3830-123">Uzaklık bir alt öğesi için göreli alma</span><span class="sxs-lookup"><span data-stu-id="f3830-123">Getting the Offset Relative to a Descendant</span></span>  
 <span data-ttu-id="f3830-124">Aşağıdaki biçimlendirme örnekte gösterildiği bir <xref:System.Windows.Controls.TextBlock> içinde bulunan bir <xref:System.Windows.Controls.StackPanel> nesne.</span><span class="sxs-lookup"><span data-stu-id="f3830-124">The following markup example shows a <xref:System.Windows.Controls.TextBlock> that is contained within a <xref:System.Windows.Controls.StackPanel> object.</span></span>  
  
 [!code-xaml[VisualSnippets#VisualSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml#visualsnippet4)]  
  
 <span data-ttu-id="f3830-125">Aşağıdaki kod örneği kullanma işlemini gösterir <xref:System.Windows.Media.Visual.TransformToDescendant%2A> uzaklığı alınacak yöntemi <xref:System.Windows.Controls.StackPanel> göreli alt <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="f3830-125">The following code example shows how to use the <xref:System.Windows.Media.Visual.TransformToDescendant%2A> method to retrieve the offset of the <xref:System.Windows.Controls.StackPanel> relative to its child <xref:System.Windows.Controls.TextBlock>.</span></span> <span data-ttu-id="f3830-126">Uzaklık değerleri içerdiği döndürülen içinde <xref:System.Windows.Media.GeneralTransform> değeri.</span><span class="sxs-lookup"><span data-stu-id="f3830-126">The offset values are contained within the returned <xref:System.Windows.Media.GeneralTransform> value.</span></span>  
  
 [!code-csharp[VisualSnippets#VisualSnippet9](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml.cs#visualsnippet9)]
 [!code-vb[VisualSnippets#VisualSnippet9](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualSnippets/visualbasic/window1.xaml.vb#visualsnippet9)]  
  
 <span data-ttu-id="f3830-127">Uzaklık dikkate <xref:System.Windows.FrameworkElement.Margin%2A> tüm nesneleri için değerler.</span><span class="sxs-lookup"><span data-stu-id="f3830-127">The offset takes into account the <xref:System.Windows.FrameworkElement.Margin%2A> values for all objects.</span></span> <span data-ttu-id="f3830-128">Bu durumda, <xref:System.Windows.Vector.X%2A> -4, ve <xref:System.Windows.Vector.Y%2A> -4'tür.</span><span class="sxs-lookup"><span data-stu-id="f3830-128">In this case, <xref:System.Windows.Vector.X%2A> is -4, and <xref:System.Windows.Vector.Y%2A> is -4.</span></span> <span data-ttu-id="f3830-129">Uzaklık değerleri negatif değerler olduğundan üst nesne olumsuz kendi alt nesneye göre uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="f3830-129">The offset values are negative values, since the parent object is negatively offset relative to its child object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3830-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f3830-130">See also</span></span>

- <xref:System.Windows.Media.Visual>
- <xref:System.Windows.Media.VisualTreeHelper>
- [<span data-ttu-id="f3830-131">WPF Grafik İşlemeye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f3830-131">WPF Graphics Rendering Overview</span></span>](wpf-graphics-rendering-overview.md)
