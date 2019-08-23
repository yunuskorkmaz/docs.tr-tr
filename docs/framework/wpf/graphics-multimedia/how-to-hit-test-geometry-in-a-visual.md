---
title: 'Nasıl yapılır: Görselde Tıklama Testi Geometrisi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [WPF], on visual objects comprising Geometry objects [WPF]
- visual objects [WPF], hit tests on
- Geometry objects [WPF], visual objects comprising
ms.assetid: 8bf2643f-d7f9-4cb4-9ea6-5b893c23200d
ms.openlocfilehash: 52b9b99b0af38d797e4a3c98dc0979211c930c1f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923374"
---
# <a name="how-to-hit-test-geometry-in-a-visual"></a><span data-ttu-id="378e2-102">Nasıl yapılır: Görselde Tıklama Testi Geometrisi</span><span class="sxs-lookup"><span data-stu-id="378e2-102">How to: Hit Test Geometry in a Visual</span></span>
<span data-ttu-id="378e2-103">Bu örnek, bir veya daha fazla <xref:System.Windows.Media.Geometry> nesneden oluşan bir görsel nesne üzerinde isabet testinin nasıl gerçekleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="378e2-103">This example shows how to perform a hit test on a visual object that is composed of one or more <xref:System.Windows.Media.Geometry> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="378e2-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="378e2-104">Example</span></span>  
 <span data-ttu-id="378e2-105">Aşağıdaki örnek, <xref:System.Windows.Media.DrawingGroup> <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> yöntemini kullanan bir görsel nesneden nasıl alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="378e2-105">The following example shows how to retrieve the <xref:System.Windows.Media.DrawingGroup> from a visual object that uses the <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> method.</span></span> <span data-ttu-id="378e2-106">Ardından, <xref:System.Windows.Media.DrawingGroup> hangi geometrinin isabet olduğunu anlamak için içindeki her çizimin işlenmiş içeriği üzerinde bir isabet testi gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="378e2-106">A hit test is then performed on the rendered content of each drawing in the <xref:System.Windows.Media.DrawingGroup> to determine which geometry was hit.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="378e2-107">Çoğu durumda, bir noktanın bir görselin <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> işlenmiş içeriğiyle kesişip kesişmediğini anlamak için yöntemini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="378e2-107">In most cases, you would use the <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> method to determine whether a point intersects any of the rendered content of a visual.</span></span>  
  
 [!code-csharp[VisualsOverview#VisualsOverviewSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#visualsoverviewsnippet4)]
 [!code-vb[VisualsOverview#VisualsOverviewSnippet4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#visualsoverviewsnippet4)]  
  
 <span data-ttu-id="378e2-108">Yöntemi, belirtilen <xref:System.Windows.Point> veya<xref:System.Windows.Media.Geometry>kullanarak test 'e isabet etmenize olanak tanıyan aşırı yüklenmiş bir yöntemdir. <xref:System.Windows.Media.Geometry.FillContains%2A></span><span class="sxs-lookup"><span data-stu-id="378e2-108">The <xref:System.Windows.Media.Geometry.FillContains%2A> method is an overloaded method that allows you to hit test by using a specified <xref:System.Windows.Point> or <xref:System.Windows.Media.Geometry>.</span></span> <span data-ttu-id="378e2-109">Bir geometri konturluysa, vuruş, dolgulu sınırların dışına genişletebilir.</span><span class="sxs-lookup"><span data-stu-id="378e2-109">If a geometry is stroked, the stroke can extend outside the fill bounds.</span></span> <span data-ttu-id="378e2-110">Bu durumda, öğesine <xref:System.Windows.Media.Geometry.StrokeContains%2A> <xref:System.Windows.Media.Geometry.FillContains%2A>ek olarak çağırmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="378e2-110">In which case, you may want to call <xref:System.Windows.Media.Geometry.StrokeContains%2A> in addition to <xref:System.Windows.Media.Geometry.FillContains%2A>.</span></span>  
  
 <span data-ttu-id="378e2-111">Ayrıca, Bezier düzleştirme amacıyla <xref:System.Windows.Media.ToleranceType> kullanılan bir de sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="378e2-111">You can also provide a <xref:System.Windows.Media.ToleranceType> that is used for the purposes of Bezier flattening.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="378e2-112">Bu örnek, geometriye uygulanabilen dönüşümler veya kırpma işlemleri hesaba eklemez.</span><span class="sxs-lookup"><span data-stu-id="378e2-112">This sample does not take into account any transforms or clipping that may be applied to the geometry.</span></span> <span data-ttu-id="378e2-113">Buna ek olarak, doğrudan ilişkili bir çizim olmadığından, bu örnek stilli bir denetimle çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="378e2-113">In addition, this sample will not work with a styled control, since it does not have any drawings directly associated with it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="378e2-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="378e2-114">See also</span></span>

- [<span data-ttu-id="378e2-115">Görsel Katmanda Tıklama Testi</span><span class="sxs-lookup"><span data-stu-id="378e2-115">Hit Testing in the Visual Layer</span></span>](hit-testing-in-the-visual-layer.md)
- [<span data-ttu-id="378e2-116">Geometriyi Parametre Olarak Kullanan Tıklama Testi</span><span class="sxs-lookup"><span data-stu-id="378e2-116">Hit Test Using Geometry as a Parameter</span></span>](how-to-hit-test-using-geometry-as-a-parameter.md)
