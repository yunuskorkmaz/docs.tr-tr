---
title: "Nasıl yapılır: Win32 Konak Kapsayıcısı Kullanan Tıklama Testi"
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
- hit tests [WPF], using Win32 host containers
- visual objects [WPF], hit tests on
- Win32 host containers [WPF], hit tests using
ms.assetid: 9491f7f3-d8ba-4573-a888-2f064d1349dc
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 142c2faa01c32ac6602e80eaef18779f93154aea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-hit-test-using-a-win32-host-container"></a><span data-ttu-id="b3771-102">Nasıl yapılır: Win32 Konak Kapsayıcısı Kullanan Tıklama Testi</span><span class="sxs-lookup"><span data-stu-id="b3771-102">How to: Hit Test Using a Win32 Host Container</span></span>
<span data-ttu-id="b3771-103">Görsel nesneler içinde oluşturduğunuz bir [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] görsel nesneler için bir konak pencere kapsayıcı sağlayarak penceresi.</span><span class="sxs-lookup"><span data-stu-id="b3771-103">You can create visual objects within a [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] window by providing a host window container for the visual objects.</span></span> <span data-ttu-id="b3771-104">Olay kapsanan görsel nesneler için işleme sağlamak için konak penceresi kapsayıcının ileti filtre döngüsüne geçirilen iletileri işleyin.</span><span class="sxs-lookup"><span data-stu-id="b3771-104">To provide event handling for the contained visual objects you process the messages passed to the host window container’s message filter loop.</span></span> <span data-ttu-id="b3771-105">Başvurmak [Öğreticisi: görsel nesneleri bir Win32 uygulaması barındırma](../../../../docs/framework/wpf/graphics-multimedia/tutorial-hosting-visual-objects-in-a-win32-application.md) görsel nesneleri barındırmak hakkında daha fazla bilgi için bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] penceresi.</span><span class="sxs-lookup"><span data-stu-id="b3771-105">Refer to [Tutorial: Hosting Visual Objects in a Win32 Application](../../../../docs/framework/wpf/graphics-multimedia/tutorial-hosting-visual-objects-in-a-win32-application.md) for more information on how to host visual objects in a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3771-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="b3771-106">Example</span></span>  
 <span data-ttu-id="b3771-107">Aşağıdaki kod için fare olay işleyicilerini ayarlama gösterilmektedir bir [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] konak kapsayıcısı olarak görsel nesneler için kullanılan penceresi.</span><span class="sxs-lookup"><span data-stu-id="b3771-107">The following code shows how to set up mouse event handlers for a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] window that is used as a host container for visual objects.</span></span>  
  
 [!code-csharp[VisualsHitTesting#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
 <span data-ttu-id="b3771-108">Aşağıdaki örnek, belirli fare olayları yakalama yanıt isabet testi ayarlama gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b3771-108">The following example shows how to set up a hit test in response to trapping specific mouse events.</span></span>  
  
 [!code-csharp[VisualsHitTesting#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 <span data-ttu-id="b3771-109"><xref:System.Windows.Interop.HwndSource> Nesne sunar [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] içinde içerik bir [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] penceresi.</span><span class="sxs-lookup"><span data-stu-id="b3771-109">The <xref:System.Windows.Interop.HwndSource> object presents [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] content within a [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] window.</span></span> <span data-ttu-id="b3771-110">Değeri <xref:System.Windows.Interop.HwndSource.RootVisual%2A> özelliği <xref:System.Windows.Interop.HwndSource> nesnesi görsel ağaç hiyerarşideki en üst düğümü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b3771-110">The value of the <xref:System.Windows.Interop.HwndSource.RootVisual%2A> property of the <xref:System.Windows.Interop.HwndSource> object represents the top-most node in the visual tree hierarchy.</span></span>  
  
 <span data-ttu-id="b3771-111">Win32 Konak Kapsayıcısı kullanarak isabet sınaması tam örnek nesneleri için bkz: [isabet testi Win32 birlikte çalışabilirlik örneği ile](http://go.microsoft.com/fwlink/?LinkID=159995).</span><span class="sxs-lookup"><span data-stu-id="b3771-111">For the complete sample on hit testing objects using a Win32 host container, see [Hit Test with Win32 Interoperation Sample](http://go.microsoft.com/fwlink/?LinkID=159995).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3771-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b3771-112">See Also</span></span>  
 <xref:System.Windows.Interop.HwndSource>  
 [<span data-ttu-id="b3771-113">Görsel Katmanda Tıklama Testi</span><span class="sxs-lookup"><span data-stu-id="b3771-113">Hit Testing in the Visual Layer</span></span>](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)  
 [<span data-ttu-id="b3771-114">Eğitmen: Win32 Uygulamasında Görsel Nesneler Barındırma</span><span class="sxs-lookup"><span data-stu-id="b3771-114">Tutorial: Hosting Visual Objects in a Win32 Application</span></span>](../../../../docs/framework/wpf/graphics-multimedia/tutorial-hosting-visual-objects-in-a-win32-application.md)
