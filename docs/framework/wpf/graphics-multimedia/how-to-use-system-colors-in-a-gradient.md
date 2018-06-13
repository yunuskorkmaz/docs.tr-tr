---
title: 'Nasıl yapılır: Sistem Renklerinin Gradyan İçinde Kullanımı'
ms.date: 03/30/2017
helpviewer_keywords:
- gradients [WPF], system colors in
- system colors in gradients [WPF]
ms.assetid: 11942e7e-6300-4b50-8ed1-f50e8d20e7d2
ms.openlocfilehash: 4c3fca1db031b0dc397e9db58195b9714ff8aa9a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33562186"
---
# <a name="how-to-use-system-colors-in-a-gradient"></a><span data-ttu-id="fbbcd-102">Nasıl yapılır: Sistem Renklerinin Gradyan İçinde Kullanımı</span><span class="sxs-lookup"><span data-stu-id="fbbcd-102">How to: Use System Colors in a Gradient</span></span>
<span data-ttu-id="fbbcd-103">Bir gradyan içerisinde sistem rengi kullanmak için kullandığınız  *\<SystemColor >* renk ve  *\<SystemColor >* ColorKey statik özelliklerini <xref:System.Windows.SystemColors> elde etmek için sınıf bir renk referansı nerede  *\<SystemColor >* istenen sistem rengi adıdır.</span><span class="sxs-lookup"><span data-stu-id="fbbcd-103">To use a system color in a gradient, you use the *\<SystemColor>* Color and *\<SystemColor>* ColorKey static properties of the <xref:System.Windows.SystemColors> class to obtain a reference to the color, where *\<SystemColor>* is the name of the desired system color.</span></span> <span data-ttu-id="fbbcd-104">Kullanım  *\<SystemColor >* sistem teması değiştiğinde otomatik olarak güncelleştiren bir dinamik başvuru oluşturmak istediğinizde ColorKey özellikleri.</span><span class="sxs-lookup"><span data-stu-id="fbbcd-104">Use the *\<SystemColor>* ColorKey properties when you want to create a dynamic reference that updates automatically as the system theme changes.</span></span> <span data-ttu-id="fbbcd-105">Aksi takdirde kullanın  *\<SystemColor >* renk özellikleri.</span><span class="sxs-lookup"><span data-stu-id="fbbcd-105">Otherwise, use the *\<SystemColor>* Color properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fbbcd-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="fbbcd-106">Example</span></span>  
 <span data-ttu-id="fbbcd-107">Aşağıdaki örnek, bir gradyan oluşturmak için dinamik sistem renk kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="fbbcd-107">The following example uses dynamic system color resources to create a gradient.</span></span>  
  
 [!code-xaml[brushsamples_snip#GraphicsMMDynamicSystemColorGradientExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/DynamicSystemColorExample.xaml#graphicsmmdynamicsystemcolorgradientexamplewholepage)]  
  
 <span data-ttu-id="fbbcd-108">Sonraki örnek gradyan oluşturmak için statik sistem renk kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="fbbcd-108">The next example uses static system color resources to create a gradient.</span></span>  
  
 [!code-xaml[brushsamples_snip#GraphicsMMStaticSystemColorGradientExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/StaticSystemColorExample.xaml#graphicsmmstaticsystemcolorgradientexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="fbbcd-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fbbcd-109">See Also</span></span>  
 <xref:System.Windows.SystemColors>  
 [<span data-ttu-id="fbbcd-110">Sistem Fırçası ile bir Alanı Boyama</span><span class="sxs-lookup"><span data-stu-id="fbbcd-110">Paint an Area with a System Brush</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [<span data-ttu-id="fbbcd-111">Düz Renkler ve Gradyanlar ile Boyamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="fbbcd-111">Painting with Solid Colors and Gradients Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
