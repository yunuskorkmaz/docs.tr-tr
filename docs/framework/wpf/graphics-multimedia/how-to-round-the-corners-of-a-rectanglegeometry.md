---
title: "Nasıl yapılır: RectangleGeometry'nin Köşelerini Yuvarlama"
ms.date: 03/30/2017
helpviewer_keywords:
- corners [WPF], rounding
- RectangleGeometry class [WPF], rounding corners
- graphics [WPF], rounding corners of RectangleGeometry objects [WPF]
- rounding corners of RectangleGeometry objects [WPF]
ms.assetid: 926644bc-1357-4c0b-ac81-694bd090ae87
ms.openlocfilehash: eb2f173bedb903e12b2795264c684524cfa09825
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59089139"
---
# <a name="how-to-round-the-corners-of-a-rectanglegeometry"></a><span data-ttu-id="7d76f-102">Nasıl yapılır: RectangleGeometry'nin Köşelerini Yuvarlama</span><span class="sxs-lookup"><span data-stu-id="7d76f-102">How to: Round the Corners of a RectangleGeometry</span></span>
<span data-ttu-id="7d76f-103">Köşelerini yuvarlatmak için bir <xref:System.Windows.Media.RectangleGeometry>ayarlayın, <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> ve <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> sıfırdan büyük bir değere özellikleri.</span><span class="sxs-lookup"><span data-stu-id="7d76f-103">To round the corners of a <xref:System.Windows.Media.RectangleGeometry>, set its <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> and <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> properties to a value greater than zero.</span></span> <span data-ttu-id="7d76f-104">Daha büyük değerler, yuvarlaklaşır dikdörtgenin köşelerini.</span><span class="sxs-lookup"><span data-stu-id="7d76f-104">The larger the values, the rounder the rectangle's corners.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7d76f-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="7d76f-105">Example</span></span>  
 <span data-ttu-id="7d76f-106">Aşağıdaki örnek, çeşitli gösterir <xref:System.Windows.Media.RectangleGeometry> farklı nesneleriyle <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> ve <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> ayarları.</span><span class="sxs-lookup"><span data-stu-id="7d76f-106">The following example shows several <xref:System.Windows.Media.RectangleGeometry> objects with different <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> and <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> settings.</span></span> <span data-ttu-id="7d76f-107"><xref:System.Windows.Media.RectangleGeometry> Nesneler kullanarak görüntülenir <xref:System.Windows.Shapes.Path> öğeleri.</span><span class="sxs-lookup"><span data-stu-id="7d76f-107">The <xref:System.Windows.Media.RectangleGeometry> objects are displayed using <xref:System.Windows.Shapes.Path> elements.</span></span>  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRoundedRectangleGeometryExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/RectangleGeometryRoundedCornerExample.xaml#graphicsmmroundedrectanglegeometryexamplewholepage)]  
  
 <span data-ttu-id="7d76f-108">![Farklı RadiusX dikdörtgenin&#47;RadiusY ayarları](./media/graphicsmm-rounded.png "graphicsmm_rounded")</span><span class="sxs-lookup"><span data-stu-id="7d76f-108">![Rectangles with different RadiusX&#47;RadiusY settings](./media/graphicsmm-rounded.png "graphicsmm_rounded")</span></span>  
<span data-ttu-id="7d76f-109">Yuvarlak köşeli dikdörtgen</span><span class="sxs-lookup"><span data-stu-id="7d76f-109">Rectangles with Rounded Corners</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d76f-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7d76f-110">See also</span></span>

- [<span data-ttu-id="7d76f-111">Geometriye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="7d76f-111">Geometry Overview</span></span>](geometry-overview.md)
- [<span data-ttu-id="7d76f-112">Bileşik Şekil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="7d76f-112">Create a Composite Shape</span></span>](how-to-create-a-composite-shape.md)
- [<span data-ttu-id="7d76f-113">PathGeometry Kullanarak Şekil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="7d76f-113">Create a Shape by Using a PathGeometry</span></span>](how-to-create-a-shape-by-using-a-pathgeometry.md)
