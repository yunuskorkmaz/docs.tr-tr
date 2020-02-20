---
title: 'Nasıl yapılır: Win32 Konak Kapsayıcısı Kullanan Tıklama Testi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [WPF], using Win32 host containers
- visual objects [WPF], hit tests on
- Win32 host containers [WPF], hit tests using
ms.assetid: 9491f7f3-d8ba-4573-a888-2f064d1349dc
ms.openlocfilehash: a86c1c36f75fa232d52731959371268a8b2593d7
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452811"
---
# <a name="how-to-hit-test-using-a-win32-host-container"></a><span data-ttu-id="dc15f-102">Nasıl yapılır: Win32 Konak Kapsayıcısı Kullanan Tıklama Testi</span><span class="sxs-lookup"><span data-stu-id="dc15f-102">How to: Hit Test Using a Win32 Host Container</span></span>
<span data-ttu-id="dc15f-103">Görsel nesneler için bir konak pencere kapsayıcısı sunarak, bir Win32 penceresi içinde görsel nesneler oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dc15f-103">You can create visual objects within a Win32 window by providing a host window container for the visual objects.</span></span> <span data-ttu-id="dc15f-104">İçerilen görsel nesnelere olay işleme sağlamak için, ana bilgisayar pencere kapsayıcısının ileti filtresi döngüsüne geçirilen iletileri işleyin.</span><span class="sxs-lookup"><span data-stu-id="dc15f-104">To provide event handling for the contained visual objects you process the messages passed to the host window container’s message filter loop.</span></span> <span data-ttu-id="dc15f-105">Visual Objects 'i bir Win32 penceresinde barındırmak hakkında daha fazla bilgi için bkz. [öğretici: bir Win32 uygulamasında görsel nesneler barındırma](tutorial-hosting-visual-objects-in-a-win32-application.md) .</span><span class="sxs-lookup"><span data-stu-id="dc15f-105">Refer to [Tutorial: Hosting Visual Objects in a Win32 Application](tutorial-hosting-visual-objects-in-a-win32-application.md) for more information on how to host visual objects in a Win32 window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc15f-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="dc15f-106">Example</span></span>  
 <span data-ttu-id="dc15f-107">Aşağıdaki kod, görsel nesneler için konak kapsayıcısı olarak kullanılan bir Win32 penceresi için fare olay işleyicilerini ayarlamayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="dc15f-107">The following code shows how to set up mouse event handlers for a Win32 window that is used as a host container for visual objects.</span></span>  
  
 [!code-csharp[VisualsHitTesting#103](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
 <span data-ttu-id="dc15f-108">Aşağıdaki örnekte, belirli fare olaylarını yakalamaya yönelik yanıt olarak bir isabet testinin nasıl ayarlanacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="dc15f-108">The following example shows how to set up a hit test in response to trapping specific mouse events.</span></span>  
  
 [!code-csharp[VisualsHitTesting#104](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 <span data-ttu-id="dc15f-109"><xref:System.Windows.Interop.HwndSource> nesnesi bir Win32 penceresi içinde [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] içerik sunar.</span><span class="sxs-lookup"><span data-stu-id="dc15f-109">The <xref:System.Windows.Interop.HwndSource> object presents [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] content within a Win32 window.</span></span> <span data-ttu-id="dc15f-110"><xref:System.Windows.Interop.HwndSource> nesnesinin <xref:System.Windows.Interop.HwndSource.RootVisual%2A> özelliğinin değeri, görsel ağaç hiyerarşisindeki en üstteki düğümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="dc15f-110">The value of the <xref:System.Windows.Interop.HwndSource.RootVisual%2A> property of the <xref:System.Windows.Interop.HwndSource> object represents the top-most node in the visual tree hierarchy.</span></span>  
  
 <span data-ttu-id="dc15f-111">Bir Win32 konak kapsayıcısı kullanan isabet sınama nesnelerinde tüm örnek için bkz. Win32 birlikte [çalışabilirlik örneği Ile Isabet testi](https://github.com/microsoft/WPF-Samples/tree/master/Visual%20Layer/VisualsHitTesting).</span><span class="sxs-lookup"><span data-stu-id="dc15f-111">For the complete sample on hit testing objects using a Win32 host container, see [Hit Test with Win32 Interoperation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Visual%20Layer/VisualsHitTesting).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc15f-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dc15f-112">See also</span></span>

- <xref:System.Windows.Interop.HwndSource>
- [<span data-ttu-id="dc15f-113">Görsel Katmanda Tıklama Testi</span><span class="sxs-lookup"><span data-stu-id="dc15f-113">Hit Testing in the Visual Layer</span></span>](hit-testing-in-the-visual-layer.md)
- [<span data-ttu-id="dc15f-114">Eğitmen: Win32 Uygulamasında Görsel Nesneler Barındırma</span><span class="sxs-lookup"><span data-stu-id="dc15f-114">Tutorial: Hosting Visual Objects in a Win32 Application</span></span>](tutorial-hosting-visual-objects-in-a-win32-application.md)
