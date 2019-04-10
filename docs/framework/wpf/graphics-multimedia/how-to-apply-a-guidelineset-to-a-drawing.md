---
title: 'Nasıl yapılır: Çizime GuidelineSet Uygulama'
ms.date: 03/30/2017
helpviewer_keywords:
- GuidelineSet property [WPF], applying to drawings
- graphics [WPF], GuidelineSet property
ms.assetid: 45f3e0b4-8820-45a7-b865-b8ea5b17b0c8
ms.openlocfilehash: 134236c5beca806b747d45f20764cc82ddd8a4e8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59217815"
---
# <a name="how-to-apply-a-guidelineset-to-a-drawing"></a><span data-ttu-id="7e418-102">Nasıl yapılır: Çizime GuidelineSet Uygulama</span><span class="sxs-lookup"><span data-stu-id="7e418-102">How to: Apply a GuidelineSet to a Drawing</span></span>
<span data-ttu-id="7e418-103">Bu örnek nasıl uygulanacağını gösterir. bir <xref:System.Windows.Media.GuidelineSet> için bir <xref:System.Windows.Media.DrawingGroup>.</span><span class="sxs-lookup"><span data-stu-id="7e418-103">This example shows how to apply a <xref:System.Windows.Media.GuidelineSet> to a <xref:System.Windows.Media.DrawingGroup>.</span></span>  
  
 <span data-ttu-id="7e418-104"><xref:System.Windows.Media.DrawingGroup> Sınıfı, yalnızca türü <xref:System.Windows.Media.Drawing> olan bir <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="7e418-104">The <xref:System.Windows.Media.DrawingGroup> class is the only type of <xref:System.Windows.Media.Drawing> that has a <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A> property.</span></span> <span data-ttu-id="7e418-105">Uygulanacak bir <xref:System.Windows.Media.GuidelineSet> başka türde <xref:System.Windows.Media.Drawing>, ekleyebilmek için bir <xref:System.Windows.Media.DrawingGroup> ve daha sonra uygulamanızı <xref:System.Windows.Media.GuidelineSet> için <xref:System.Windows.Media.DrawingGroup>.</span><span class="sxs-lookup"><span data-stu-id="7e418-105">To apply a <xref:System.Windows.Media.GuidelineSet> to another type of <xref:System.Windows.Media.Drawing>, add it to a <xref:System.Windows.Media.DrawingGroup> and then apply the <xref:System.Windows.Media.GuidelineSet> to your <xref:System.Windows.Media.DrawingGroup>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7e418-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="7e418-106">Example</span></span>  
 <span data-ttu-id="7e418-107">Aşağıdaki örnek iki oluşturur <xref:System.Windows.Media.DrawingGroup> tek fark neredeyse aynı; olan nesneler: ikinci <xref:System.Windows.Media.DrawingGroup> sahip bir <xref:System.Windows.Media.GuidelineSet> ve ilk desteklemez.</span><span class="sxs-lookup"><span data-stu-id="7e418-107">The following example creates two <xref:System.Windows.Media.DrawingGroup> objects that are almost identical; the only difference is: the second <xref:System.Windows.Media.DrawingGroup> has a <xref:System.Windows.Media.GuidelineSet> and the first does not.</span></span>  
  
 <span data-ttu-id="7e418-108">Örneğin çıktısında aşağıda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7e418-108">The following illustration shows the output from the example.</span></span> <span data-ttu-id="7e418-109">İşleme çünkü arasında iki <xref:System.Windows.Media.DrawingGroup> nesneleri, küçük, çizimler bölümlerini genişletilir.</span><span class="sxs-lookup"><span data-stu-id="7e418-109">Because the rendering difference between the two <xref:System.Windows.Media.DrawingGroup> objects is so subtle, portions of the drawings are enlarged.</span></span>  
  
 <span data-ttu-id="7e418-110">![DrawingGroup GuidelineSet olmadan ve](./media/graphicsmm-drawinggroup-guidelineset.png "graphicsmm_drawinggroup_guidelineset")</span><span class="sxs-lookup"><span data-stu-id="7e418-110">![A DrawingGroup with and without a GuidelineSet](./media/graphicsmm-drawinggroup-guidelineset.png "graphicsmm_drawinggroup_guidelineset")</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMDrawingGroupGuidelineSetExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupGuidelineSetExample.cs#graphicsmmdrawinggroupguidelinesetexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMDrawingGroupGuidelineSetExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupGuidelineSetExample.xaml#graphicsmmdrawinggroupguidelinesetexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="7e418-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7e418-111">See also</span></span>

- <xref:System.Windows.Media.DrawingGroup>
- <xref:System.Windows.Media.GuidelineSet>
- [<span data-ttu-id="7e418-112">Çizim Nesnelerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="7e418-112">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
