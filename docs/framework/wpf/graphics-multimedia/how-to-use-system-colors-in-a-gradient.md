---
title: "Nasıl yapılır: Sistem Renklerinin Gradyan İçinde Kullanımı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- gradients [WPF], system colors in
- system colors in gradients [WPF]
ms.assetid: 11942e7e-6300-4b50-8ed1-f50e8d20e7d2
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 105e22588f68d999811f5482342d53851a4d25eb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-system-colors-in-a-gradient"></a><span data-ttu-id="2a826-102">Nasıl yapılır: Sistem Renklerinin Gradyan İçinde Kullanımı</span><span class="sxs-lookup"><span data-stu-id="2a826-102">How to: Use System Colors in a Gradient</span></span>
<span data-ttu-id="2a826-103">Bir gradyan içerisinde sistem rengi kullanmak için kullandığınız  *\<SystemColor >*renk ve  *\<SystemColor >*ColorKey statik özelliklerini <xref:System.Windows.SystemColors> elde etmek için sınıf bir renk referansı nerede  *\<SystemColor >* istenen sistem rengi adıdır.</span><span class="sxs-lookup"><span data-stu-id="2a826-103">To use a system color in a gradient, you use the *\<SystemColor>*Color and *\<SystemColor>*ColorKey static properties of the <xref:System.Windows.SystemColors> class to obtain a reference to the color, where *\<SystemColor>* is the name of the desired system color.</span></span> <span data-ttu-id="2a826-104">Kullanım  *\<SystemColor >*sistem teması değiştiğinde otomatik olarak güncelleştiren bir dinamik başvuru oluşturmak istediğinizde ColorKey özellikleri.</span><span class="sxs-lookup"><span data-stu-id="2a826-104">Use the *\<SystemColor>*ColorKey properties when you want to create a dynamic reference that updates automatically as the system theme changes.</span></span> <span data-ttu-id="2a826-105">Aksi takdirde kullanın  *\<SystemColor >*renk özellikleri.</span><span class="sxs-lookup"><span data-stu-id="2a826-105">Otherwise, use the *\<SystemColor>*Color properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a826-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="2a826-106">Example</span></span>  
 <span data-ttu-id="2a826-107">Aşağıdaki örnek, bir gradyan oluşturmak için dinamik sistem renk kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="2a826-107">The following example uses dynamic system color resources to create a gradient.</span></span>  
  
 [!code-xaml[brushsamples_snip#GraphicsMMDynamicSystemColorGradientExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/DynamicSystemColorExample.xaml#graphicsmmdynamicsystemcolorgradientexamplewholepage)]  
  
 <span data-ttu-id="2a826-108">Sonraki örnek gradyan oluşturmak için statik sistem renk kaynakları kullanır.</span><span class="sxs-lookup"><span data-stu-id="2a826-108">The next example uses static system color resources to create a gradient.</span></span>  
  
 [!code-xaml[brushsamples_snip#GraphicsMMStaticSystemColorGradientExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/StaticSystemColorExample.xaml#graphicsmmstaticsystemcolorgradientexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="2a826-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2a826-109">See Also</span></span>  
 <xref:System.Windows.SystemColors>  
 [<span data-ttu-id="2a826-110">Sistem fırçası ile bir alanı boyama</span><span class="sxs-lookup"><span data-stu-id="2a826-110">Paint an Area with a System Brush</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [<span data-ttu-id="2a826-111">Boyama düz renklerle ve gradyan genel bakış</span><span class="sxs-lookup"><span data-stu-id="2a826-111">Painting with Solid Colors and Gradients Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
