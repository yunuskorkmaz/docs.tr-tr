---
title: "Nasıl yapılır: StreamGeometry Kullanarak Şekil Oluşturma"
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
helpviewer_keywords:
- graphics [WPF], shapes
- shapes [WPF], creating with StreamGeometry class
ms.assetid: 08f7c8ce-074b-49cd-9aba-cc9592d4ee51
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: caa97d0dbd4c847892e164ecb168349c38f7f271
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-shape-using-a-streamgeometry"></a><span data-ttu-id="c2a67-102">Nasıl yapılır: StreamGeometry Kullanarak Şekil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c2a67-102">How to: Create a Shape Using a StreamGeometry</span></span>
<span data-ttu-id="c2a67-103"><xref:System.Windows.Media.StreamGeometry>için hafif alternatif <xref:System.Windows.Media.PathGeometry> geometrik şekiller oluşturma.</span><span class="sxs-lookup"><span data-stu-id="c2a67-103"><xref:System.Windows.Media.StreamGeometry> is light-weight alternative to <xref:System.Windows.Media.PathGeometry> for creating geometric shapes.</span></span> <span data-ttu-id="c2a67-104">Kullanım bir <xref:System.Windows.Media.StreamGeometry> karmaşık geometri açıklamak gerektiğinde ancak veri bağlama, animasyon veya değişimi destekleme ek yükünü istemiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="c2a67-104">Use a <xref:System.Windows.Media.StreamGeometry> when you need to describe a complex geometry but do not want the overhead of supporting data binding, animation, or modification.</span></span> <span data-ttu-id="c2a67-105">Örneğin, verimlilik nedeniyle <xref:System.Windows.Media.StreamGeometry> sınıftır donarıcıları açıklamak için iyi bir seçimdir.</span><span class="sxs-lookup"><span data-stu-id="c2a67-105">For example, because of its efficiency, the <xref:System.Windows.Media.StreamGeometry> class is a good choice for describing adorners.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2a67-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="c2a67-106">Example</span></span>  
 <span data-ttu-id="c2a67-107">Aşağıdaki örnek, bir üçgen oluşturmak için öznitelik sözdizimini kullanır. <xref:System.Windows.Media.StreamGeometry> içinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c2a67-107">The following example uses attribute syntax to create a triangular <xref:System.Windows.Media.StreamGeometry> in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 [!code-xaml[GeometriesMiscSnippets_snip#StreamGeometryTriangleExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/StreamGeometryExample.xaml#streamgeometrytriangleexamplewholepage)]  
  
 <span data-ttu-id="c2a67-108">Hakkında daha fazla bilgi için <xref:System.Windows.Media.StreamGeometry> öznitelik sözdizimi, bkz: [biçimlendirme sözdizimi yolu](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) sayfası.</span><span class="sxs-lookup"><span data-stu-id="c2a67-108">For more information about <xref:System.Windows.Media.StreamGeometry> attribute syntax, see the [Path Markup Syntax](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) page.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2a67-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="c2a67-109">Example</span></span>  
 <span data-ttu-id="c2a67-110">Sonraki örnek kullanan bir <xref:System.Windows.Media.StreamGeometry> kodda bir üçgen tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="c2a67-110">The next example uses a <xref:System.Windows.Media.StreamGeometry> to define a triangle in code.</span></span> <span data-ttu-id="c2a67-111">İlk olarak, örnek oluşturur bir <xref:System.Windows.Media.StreamGeometry>, ardından alacağı bir <xref:System.Windows.Media.StreamGeometryContext> ve üçgen tanımlamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="c2a67-111">First, the example creates a <xref:System.Windows.Media.StreamGeometry>, then obtains a <xref:System.Windows.Media.StreamGeometryContext> and uses it to describe the triangle.</span></span>  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#StreamGeometryTriangleExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/StreamGeometryTriangleExample.cs#streamgeometrytriangleexamplewholepage)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#StreamGeometryTriangleExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/streamgeometrytriangleexample.vb#streamgeometrytriangleexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="c2a67-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="c2a67-112">Example</span></span>  
 <span data-ttu-id="c2a67-113">Sonraki örnek kullanan bir yöntem oluşturur bir <xref:System.Windows.Media.StreamGeometry> ve <xref:System.Windows.Media.StreamGeometryContext> belirtilen parametrelere göre bir geometrik şekil tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="c2a67-113">The next example creates a method that uses a <xref:System.Windows.Media.StreamGeometry> and <xref:System.Windows.Media.StreamGeometryContext> to define a geometric shape based on specified parameters.</span></span>  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#StreamGeometryExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/StreamGeometryExample.cs#streamgeometryexamplewholepage)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#StreamGeometryExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/streamgeometryexample.vb#streamgeometryexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="c2a67-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c2a67-114">See Also</span></span>  
 <xref:System.Windows.Media.PathGeometry>  
 <xref:System.Windows.Media.StreamGeometry>  
 <xref:System.Windows.Media.StreamGeometryContext>  
 [<span data-ttu-id="c2a67-115">Bir şekli PathGeometry kullanarak oluşturma</span><span class="sxs-lookup"><span data-stu-id="c2a67-115">Create a Shape by Using a PathGeometry</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)  
 [<span data-ttu-id="c2a67-116">Geometri genel bakış</span><span class="sxs-lookup"><span data-stu-id="c2a67-116">Geometry Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)
