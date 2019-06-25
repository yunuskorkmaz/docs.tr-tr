---
title: 'Nasıl yapılır: StreamGeometry Kullanarak Şekil Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], shapes
- shapes [WPF], creating with StreamGeometry class
ms.assetid: 08f7c8ce-074b-49cd-9aba-cc9592d4ee51
ms.openlocfilehash: ce2097568349ad376540163f5fe05d6a3e5b0643
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2019
ms.locfileid: "67348027"
---
# <a name="how-to-create-a-shape-using-a-streamgeometry"></a><span data-ttu-id="02bc0-102">Nasıl yapılır: StreamGeometry Kullanarak Şekil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="02bc0-102">How to: Create a Shape Using a StreamGeometry</span></span>
<span data-ttu-id="02bc0-103"><xref:System.Windows.Media.StreamGeometry> Basit alternatifi <xref:System.Windows.Media.PathGeometry> geometrik şekiller oluşturma.</span><span class="sxs-lookup"><span data-stu-id="02bc0-103"><xref:System.Windows.Media.StreamGeometry> is lightweight alternative to <xref:System.Windows.Media.PathGeometry> for creating geometric shapes.</span></span> <span data-ttu-id="02bc0-104">Kullanım bir <xref:System.Windows.Media.StreamGeometry> karmaşık geometri açıklamak gerektiğinde ancak destekleme veri bağlama, animasyon veya değişikliği yükü istemiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="02bc0-104">Use a <xref:System.Windows.Media.StreamGeometry> when you need to describe a complex geometry but do not want the overhead of supporting data binding, animation, or modification.</span></span> <span data-ttu-id="02bc0-105">Örneğin, verimlilik, nedeniyle <xref:System.Windows.Media.StreamGeometry> sınıftır donatıcıları açıklamak için iyi bir seçimdir.</span><span class="sxs-lookup"><span data-stu-id="02bc0-105">For example, because of its efficiency, the <xref:System.Windows.Media.StreamGeometry> class is a good choice for describing adorners.</span></span>  
  
## <a name="example"></a><span data-ttu-id="02bc0-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="02bc0-106">Example</span></span>  
 <span data-ttu-id="02bc0-107">Aşağıdaki örnek, bir üçgen oluşturmak için öznitelik sözdizimi kullanır. <xref:System.Windows.Media.StreamGeometry> içinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="02bc0-107">The following example uses attribute syntax to create a triangular <xref:System.Windows.Media.StreamGeometry> in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 [!code-xaml[GeometriesMiscSnippets_snip#StreamGeometryTriangleExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/StreamGeometryExample.xaml#streamgeometrytriangleexamplewholepage)]  
  
 <span data-ttu-id="02bc0-108">Hakkında daha fazla bilgi için <xref:System.Windows.Media.StreamGeometry> öznitelik sözdizimi için bkz: [yol işaretleme söz dizimi](path-markup-syntax.md) sayfası.</span><span class="sxs-lookup"><span data-stu-id="02bc0-108">For more information about <xref:System.Windows.Media.StreamGeometry> attribute syntax, see the [Path Markup Syntax](path-markup-syntax.md) page.</span></span>  
  
## <a name="example"></a><span data-ttu-id="02bc0-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="02bc0-109">Example</span></span>  
 <span data-ttu-id="02bc0-110">Sonraki örnekte bir <xref:System.Windows.Media.StreamGeometry> kodda bir üçgen tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="02bc0-110">The next example uses a <xref:System.Windows.Media.StreamGeometry> to define a triangle in code.</span></span> <span data-ttu-id="02bc0-111">İlk olarak, örnek, oluşturur bir <xref:System.Windows.Media.StreamGeometry>, ardından alır bir <xref:System.Windows.Media.StreamGeometryContext> ve bu üçgen tanımlamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="02bc0-111">First, the example creates a <xref:System.Windows.Media.StreamGeometry>, then obtains a <xref:System.Windows.Media.StreamGeometryContext> and uses it to describe the triangle.</span></span>  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#StreamGeometryTriangleExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/StreamGeometryTriangleExample.cs#streamgeometrytriangleexamplewholepage)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#StreamGeometryTriangleExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/streamgeometrytriangleexample.vb#streamgeometrytriangleexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="02bc0-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="02bc0-112">Example</span></span>  
 <span data-ttu-id="02bc0-113">Sonraki örnekte kullanan bir yöntem oluşturur bir <xref:System.Windows.Media.StreamGeometry> ve <xref:System.Windows.Media.StreamGeometryContext> belirtilen parametrelere göre bir geometrik şekil tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="02bc0-113">The next example creates a method that uses a <xref:System.Windows.Media.StreamGeometry> and <xref:System.Windows.Media.StreamGeometryContext> to define a geometric shape based on specified parameters.</span></span>  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#StreamGeometryExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/StreamGeometryExample.cs#streamgeometryexamplewholepage)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#StreamGeometryExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/streamgeometryexample.vb#streamgeometryexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="02bc0-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="02bc0-114">See also</span></span>

- <xref:System.Windows.Media.PathGeometry>
- <xref:System.Windows.Media.StreamGeometry>
- <xref:System.Windows.Media.StreamGeometryContext>
- [<span data-ttu-id="02bc0-115">PathGeometry Kullanarak Şekil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="02bc0-115">Create a Shape by Using a PathGeometry</span></span>](how-to-create-a-shape-by-using-a-pathgeometry.md)
- [<span data-ttu-id="02bc0-116">Geometriye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="02bc0-116">Geometry Overview</span></span>](geometry-overview.md)
