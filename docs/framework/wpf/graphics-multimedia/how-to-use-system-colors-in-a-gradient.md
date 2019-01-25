---
title: 'Nasıl yapılır: Sistem Renklerinin Gradyan İçinde Kullanımı'
ms.date: 03/30/2017
helpviewer_keywords:
- gradients [WPF], system colors in
- system colors in gradients [WPF]
ms.assetid: 11942e7e-6300-4b50-8ed1-f50e8d20e7d2
ms.openlocfilehash: 44dfd30dc8d21e638855a383f1c9360a61ce81f9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54726422"
---
# <a name="how-to-use-system-colors-in-a-gradient"></a><span data-ttu-id="f3d1d-102">Nasıl yapılır: Sistem Renklerinin Gradyan İçinde Kullanımı</span><span class="sxs-lookup"><span data-stu-id="f3d1d-102">How to: Use System Colors in a Gradient</span></span>
<span data-ttu-id="f3d1d-103">Gradyan içinde sistem renk kullanmak için kullandığınız  *\<SystemColor >* renk ve  *\<SystemColor >* ColorKey statik özelliklerini <xref:System.Windows.SystemColors> almak için bir renk başvuru yeri  *\<SystemColor >* istenen sistem renk adıdır.</span><span class="sxs-lookup"><span data-stu-id="f3d1d-103">To use a system color in a gradient, you use the *\<SystemColor>* Color and *\<SystemColor>* ColorKey static properties of the <xref:System.Windows.SystemColors> class to obtain a reference to the color, where *\<SystemColor>* is the name of the desired system color.</span></span> <span data-ttu-id="f3d1d-104">Kullanım  *\<SystemColor >* sistem tema değiştiğinde otomatik olarak güncelleştiren bir dinamik başvuru oluşturmak istediğinizde ColorKey özellikleri.</span><span class="sxs-lookup"><span data-stu-id="f3d1d-104">Use the *\<SystemColor>* ColorKey properties when you want to create a dynamic reference that updates automatically as the system theme changes.</span></span> <span data-ttu-id="f3d1d-105">Aksi takdirde kullanın  *\<SystemColor >* Color özelliklerini.</span><span class="sxs-lookup"><span data-stu-id="f3d1d-105">Otherwise, use the *\<SystemColor>* Color properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3d1d-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="f3d1d-106">Example</span></span>  
 <span data-ttu-id="f3d1d-107">Aşağıdaki örnek, bir gradyan oluşturmak için dinamik sistem renk kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="f3d1d-107">The following example uses dynamic system color resources to create a gradient.</span></span>  
  
 [!code-xaml[brushsamples_snip#GraphicsMMDynamicSystemColorGradientExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/DynamicSystemColorExample.xaml#graphicsmmdynamicsystemcolorgradientexamplewholepage)]  
  
 <span data-ttu-id="f3d1d-108">Sonraki örnek, bir gradyan oluşturmak için statik bir sistem renk kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="f3d1d-108">The next example uses static system color resources to create a gradient.</span></span>  
  
 [!code-xaml[brushsamples_snip#GraphicsMMStaticSystemColorGradientExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/StaticSystemColorExample.xaml#graphicsmmstaticsystemcolorgradientexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="f3d1d-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f3d1d-109">See also</span></span>
- <xref:System.Windows.SystemColors>
- [<span data-ttu-id="f3d1d-110">Sistem Fırçası ile bir Alanı Boyama</span><span class="sxs-lookup"><span data-stu-id="f3d1d-110">Paint an Area with a System Brush</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [<span data-ttu-id="f3d1d-111">Düz Renkler ve Gradyanlar ile Boyamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f3d1d-111">Painting with Solid Colors and Gradients Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
