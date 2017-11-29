---
title: "Nasıl yapılır: ScrollBar Üzerinde Parmak Boyutunu Özelleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ScrollBar control [WPF]
- customizing thumb size [WPF]
- thumb size [WPF]
ms.assetid: fa32b866-5ca1-4e73-85e7-2ac64b80d194
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c550aa425eedf4b434e061f05326bf6a6de91f9d
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-customize-the-thumb-size-on-a-scrollbar"></a><span data-ttu-id="7dca8-102">Nasıl yapılır: ScrollBar Üzerinde Parmak Boyutunu Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="7dca8-102">How to: Customize the Thumb Size on a ScrollBar</span></span>
<span data-ttu-id="7dca8-103">Bu konuda nasıl ayarlanacağını açıklar <xref:System.Windows.Controls.Primitives.Thumb> , bir <xref:System.Windows.Controls.Primitives.ScrollBar> sabit bir boyuta ve için en az bir boyut belirlemek nasıl <xref:System.Windows.Controls.Primitives.Thumb> , bir <xref:System.Windows.Controls.Primitives.ScrollBar>.</span><span class="sxs-lookup"><span data-stu-id="7dca8-103">This topic explains how to set the <xref:System.Windows.Controls.Primitives.Thumb> of a <xref:System.Windows.Controls.Primitives.ScrollBar> to a fixed size and how to specify a minimum size for the <xref:System.Windows.Controls.Primitives.Thumb> of a <xref:System.Windows.Controls.Primitives.ScrollBar>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7dca8-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="7dca8-104">Example</span></span>  
  
## <a name="description"></a><span data-ttu-id="7dca8-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7dca8-105">Description</span></span>  
 <span data-ttu-id="7dca8-106">Aşağıdaki örnekte bir <xref:System.Windows.Controls.Primitives.ScrollBar> olan bir <xref:System.Windows.Controls.Primitives.Thumb> sabit bir boyuta sahip.</span><span class="sxs-lookup"><span data-stu-id="7dca8-106">The following example creates a <xref:System.Windows.Controls.Primitives.ScrollBar> that has a <xref:System.Windows.Controls.Primitives.Thumb> with a fixed size.</span></span> <span data-ttu-id="7dca8-107">Örnek <xref:System.Windows.Controls.Primitives.Track.ViewportSize%2A> özelliği <xref:System.Windows.Controls.Primitives.Thumb> için <xref:System.Double.NaN> ve yüksekliğini ayarlar <xref:System.Windows.Controls.Primitives.Thumb>.</span><span class="sxs-lookup"><span data-stu-id="7dca8-107">The example sets the <xref:System.Windows.Controls.Primitives.Track.ViewportSize%2A> property of the <xref:System.Windows.Controls.Primitives.Thumb> to <xref:System.Double.NaN> and sets the height of the <xref:System.Windows.Controls.Primitives.Thumb>.</span></span>  <span data-ttu-id="7dca8-108">Yatay oluşturmak için <xref:System.Windows.Controls.Primitives.ScrollBar> ile bir <xref:System.Windows.Controls.Primitives.Thumb> sabit genişliği olan, genişliğini ayarla <xref:System.Windows.Controls.Primitives.Thumb>.</span><span class="sxs-lookup"><span data-stu-id="7dca8-108">To create a horizontal <xref:System.Windows.Controls.Primitives.ScrollBar> with a <xref:System.Windows.Controls.Primitives.Thumb> that has a fixed width, set the width of the <xref:System.Windows.Controls.Primitives.Thumb>.</span></span>  
  
## <a name="code"></a><span data-ttu-id="7dca8-109">Kod</span><span class="sxs-lookup"><span data-stu-id="7dca8-109">Code</span></span>  
 [!code-xaml[ScrollBarCustomThumbSize#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollBarCustomThumbSize/CS/Window1.xaml#1)]  
  
## <a name="description"></a><span data-ttu-id="7dca8-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7dca8-110">Description</span></span>  
 <span data-ttu-id="7dca8-111">Aşağıdaki örnekte bir <xref:System.Windows.Controls.Primitives.ScrollBar> olan bir <xref:System.Windows.Controls.Primitives.Thumb> minimum boyutu.</span><span class="sxs-lookup"><span data-stu-id="7dca8-111">The following example creates a <xref:System.Windows.Controls.Primitives.ScrollBar> that has a <xref:System.Windows.Controls.Primitives.Thumb> with a minimum size.</span></span> <span data-ttu-id="7dca8-112">Örnek değerini ayarlar <xref:System.Windows.SystemParameters.VerticalScrollBarButtonHeightKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="7dca8-112">The example sets the value of <xref:System.Windows.SystemParameters.VerticalScrollBarButtonHeightKey%2A>.</span></span> <span data-ttu-id="7dca8-113">Yatay oluşturmak için <xref:System.Windows.Controls.Primitives.ScrollBar> ile bir <xref:System.Windows.Controls.Primitives.Thumb> en küçük genişliği olan, Ayarla <xref:System.Windows.SystemParameters.HorizontalScrollBarButtonWidthKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="7dca8-113">To create a horizontal <xref:System.Windows.Controls.Primitives.ScrollBar> with a <xref:System.Windows.Controls.Primitives.Thumb> that has a minimum width, set the <xref:System.Windows.SystemParameters.HorizontalScrollBarButtonWidthKey%2A>.</span></span>  
  
## <a name="code"></a><span data-ttu-id="7dca8-114">Kod</span><span class="sxs-lookup"><span data-stu-id="7dca8-114">Code</span></span>  
 [!code-xaml[ScrollBarCustomThumbSize#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollBarCustomThumbSize/CS/Window1.xaml#2)]  
  
## <a name="see-also"></a><span data-ttu-id="7dca8-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7dca8-115">See Also</span></span>  
 [<span data-ttu-id="7dca8-116">Kaydırma çubuğu stilleri ve şablonları</span><span class="sxs-lookup"><span data-stu-id="7dca8-116">ScrollBar Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/scrollbar-styles-and-templates.md)
