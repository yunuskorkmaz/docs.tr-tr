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
ms.openlocfilehash: 26e0119ee82646f466c3567881bf33350fe59d17
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33560925"
---
# <a name="how-to-hit-test-geometry-in-a-visual"></a><span data-ttu-id="acf19-102">Nasıl yapılır: Görselde Tıklama Testi Geometrisi</span><span class="sxs-lookup"><span data-stu-id="acf19-102">How to: Hit Test Geometry in a Visual</span></span>
<span data-ttu-id="acf19-103">Bu örnek, bir veya daha fazla oluşan görsel bir nesne üzerinde bir isabet testi yapmak gösterilmiştir <xref:System.Windows.Media.Geometry> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="acf19-103">This example shows how to perform a hit test on a visual object that is composed of one or more <xref:System.Windows.Media.Geometry> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="acf19-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="acf19-104">Example</span></span>  
 <span data-ttu-id="acf19-105">Aşağıdaki örnekte nasıl alınacağını gösterir <xref:System.Windows.Media.DrawingGroup> kullanan bir görsel nesnesinden <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="acf19-105">The following example shows how to retrieve the <xref:System.Windows.Media.DrawingGroup> from a visual object that uses the <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> method.</span></span> <span data-ttu-id="acf19-106">İsabet testi her çizimin işlenmiş içeriğinde gerçekleştirilir <xref:System.Windows.Media.DrawingGroup> hangi geometrinin isabet belirlemek için.</span><span class="sxs-lookup"><span data-stu-id="acf19-106">A hit test is then performed on the rendered content of each drawing in the <xref:System.Windows.Media.DrawingGroup> to determine which geometry was hit.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="acf19-107">Çoğu durumda, kullanacağınız <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> bir nokta herhangi bir görsel işlenmiş içeriğiyle kesiştiğinden olup olmadığını belirlemek amacıyla yöntemi.</span><span class="sxs-lookup"><span data-stu-id="acf19-107">In most cases, you would use the <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> method to determine whether a point intersects any of the rendered content of a visual.</span></span>  
  
 [!code-csharp[VisualsOverview#VisualsOverviewSnippet4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#visualsoverviewsnippet4)]
 [!code-vb[VisualsOverview#VisualsOverviewSnippet4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#visualsoverviewsnippet4)]  
  
 <span data-ttu-id="acf19-108"><xref:System.Windows.Media.Geometry.FillContains%2A> Yöntemdir belirtilen kullanarak isabet testi olanak tanıyan bir aşırı yüklenmiş yöntemin <xref:System.Windows.Point> veya <xref:System.Windows.Media.Geometry>.</span><span class="sxs-lookup"><span data-stu-id="acf19-108">The <xref:System.Windows.Media.Geometry.FillContains%2A> method is an overloaded method that allows you to hit test by using a specified <xref:System.Windows.Point> or <xref:System.Windows.Media.Geometry>.</span></span> <span data-ttu-id="acf19-109">Geometri vuruş, vuruş dolgu sınırlarının dışına genişletebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="acf19-109">If a geometry is stroked, the stroke can extend outside the fill bounds.</span></span> <span data-ttu-id="acf19-110">Bu durumda, çağrı yapmak isteyebilirsiniz <xref:System.Windows.Media.Geometry.StrokeContains%2A> ek olarak <xref:System.Windows.Media.Geometry.FillContains%2A>.</span><span class="sxs-lookup"><span data-stu-id="acf19-110">In which case, you may want to call <xref:System.Windows.Media.Geometry.StrokeContains%2A> in addition to <xref:System.Windows.Media.Geometry.FillContains%2A>.</span></span>  
  
 <span data-ttu-id="acf19-111">Ayrıca, sağlayabilirsiniz bir <xref:System.Windows.Media.ToleranceType> Bezier düzleştirme amacıyla kullanılır.</span><span class="sxs-lookup"><span data-stu-id="acf19-111">You can also provide a <xref:System.Windows.Media.ToleranceType> that is used for the purposes of Bezier flattening.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="acf19-112">Bu örnek dönüşümleri dikkate almaz veya kırpmayı geometriye uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="acf19-112">This sample does not take into account any transforms or clipping that may be applied to the geometry.</span></span> <span data-ttu-id="acf19-113">Ayrıca, doğrudan ilişkili çizimler olmadığından bu örnek bir stilde denetimi ile çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="acf19-113">In addition, this sample will not work with a styled control, since it does not have any drawings directly associated with it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acf19-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="acf19-114">See Also</span></span>  
 [<span data-ttu-id="acf19-115">Görsel Katmanda Tıklama Testi</span><span class="sxs-lookup"><span data-stu-id="acf19-115">Hit Testing in the Visual Layer</span></span>](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)  
 [<span data-ttu-id="acf19-116">Geometriyi Parametre Olarak Kullanan Tıklama Testi</span><span class="sxs-lookup"><span data-stu-id="acf19-116">Hit Test Using Geometry as a Parameter</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-hit-test-using-geometry-as-a-parameter.md)
