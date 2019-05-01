---
title: 'Nasıl yapılır: ScrollBar Üzerinde Parmak Boyutunu Özelleştirme'
ms.date: 03/30/2017
helpviewer_keywords:
- ScrollBar control [WPF]
- customizing thumb size [WPF]
- thumb size [WPF]
ms.assetid: fa32b866-5ca1-4e73-85e7-2ac64b80d194
ms.openlocfilehash: 60ae7c4e95801036c5deb0c485645297509b830c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61911059"
---
# <a name="how-to-customize-the-thumb-size-on-a-scrollbar"></a><span data-ttu-id="72dd0-102">Nasıl yapılır: ScrollBar Üzerinde Parmak Boyutunu Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="72dd0-102">How to: Customize the Thumb Size on a ScrollBar</span></span>
<span data-ttu-id="72dd0-103">Bu konu nasıl ayarlanacağını açıklar <xref:System.Windows.Controls.Primitives.Thumb> , bir <xref:System.Windows.Controls.Primitives.ScrollBar> sabit bir boyuta ve için en az bir boyut belirlemek nasıl <xref:System.Windows.Controls.Primitives.Thumb> , bir <xref:System.Windows.Controls.Primitives.ScrollBar>.</span><span class="sxs-lookup"><span data-stu-id="72dd0-103">This topic explains how to set the <xref:System.Windows.Controls.Primitives.Thumb> of a <xref:System.Windows.Controls.Primitives.ScrollBar> to a fixed size and how to specify a minimum size for the <xref:System.Windows.Controls.Primitives.Thumb> of a <xref:System.Windows.Controls.Primitives.ScrollBar>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="72dd0-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="72dd0-104">Example</span></span>  
  
## <a name="description"></a><span data-ttu-id="72dd0-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="72dd0-105">Description</span></span>  
 <span data-ttu-id="72dd0-106">Aşağıdaki örnek, oluşturur bir <xref:System.Windows.Controls.Primitives.ScrollBar> olan bir <xref:System.Windows.Controls.Primitives.Thumb> sabit bir boyuta sahip.</span><span class="sxs-lookup"><span data-stu-id="72dd0-106">The following example creates a <xref:System.Windows.Controls.Primitives.ScrollBar> that has a <xref:System.Windows.Controls.Primitives.Thumb> with a fixed size.</span></span> <span data-ttu-id="72dd0-107">Örnek <xref:System.Windows.Controls.Primitives.Track.ViewportSize%2A> özelliği <xref:System.Windows.Controls.Primitives.Thumb> için <xref:System.Double.NaN> ve yüksekliğini ayarlar <xref:System.Windows.Controls.Primitives.Thumb>.</span><span class="sxs-lookup"><span data-stu-id="72dd0-107">The example sets the <xref:System.Windows.Controls.Primitives.Track.ViewportSize%2A> property of the <xref:System.Windows.Controls.Primitives.Thumb> to <xref:System.Double.NaN> and sets the height of the <xref:System.Windows.Controls.Primitives.Thumb>.</span></span>  <span data-ttu-id="72dd0-108">Yatay oluşturmak için <xref:System.Windows.Controls.Primitives.ScrollBar> ile bir <xref:System.Windows.Controls.Primitives.Thumb> genişliğini ayarlamak, sabit genişlik olan <xref:System.Windows.Controls.Primitives.Thumb>.</span><span class="sxs-lookup"><span data-stu-id="72dd0-108">To create a horizontal <xref:System.Windows.Controls.Primitives.ScrollBar> with a <xref:System.Windows.Controls.Primitives.Thumb> that has a fixed width, set the width of the <xref:System.Windows.Controls.Primitives.Thumb>.</span></span>  
  
## <a name="code"></a><span data-ttu-id="72dd0-109">Kod</span><span class="sxs-lookup"><span data-stu-id="72dd0-109">Code</span></span>  
 [!code-xaml[ScrollBarCustomThumbSize#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ScrollBarCustomThumbSize/CS/Window1.xaml#1)]  
  
## <a name="description"></a><span data-ttu-id="72dd0-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="72dd0-110">Description</span></span>  
 <span data-ttu-id="72dd0-111">Aşağıdaki örnek, oluşturur bir <xref:System.Windows.Controls.Primitives.ScrollBar> olan bir <xref:System.Windows.Controls.Primitives.Thumb> en küçük boyutu.</span><span class="sxs-lookup"><span data-stu-id="72dd0-111">The following example creates a <xref:System.Windows.Controls.Primitives.ScrollBar> that has a <xref:System.Windows.Controls.Primitives.Thumb> with a minimum size.</span></span> <span data-ttu-id="72dd0-112">Örnek ayarlar <xref:System.Windows.SystemParameters.VerticalScrollBarButtonHeightKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="72dd0-112">The example sets the value of <xref:System.Windows.SystemParameters.VerticalScrollBarButtonHeightKey%2A>.</span></span> <span data-ttu-id="72dd0-113">Yatay oluşturmak için <xref:System.Windows.Controls.Primitives.ScrollBar> ile bir <xref:System.Windows.Controls.Primitives.Thumb> ayarlayın, en küçük genişliği olan <xref:System.Windows.SystemParameters.HorizontalScrollBarButtonWidthKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="72dd0-113">To create a horizontal <xref:System.Windows.Controls.Primitives.ScrollBar> with a <xref:System.Windows.Controls.Primitives.Thumb> that has a minimum width, set the <xref:System.Windows.SystemParameters.HorizontalScrollBarButtonWidthKey%2A>.</span></span>  
  
## <a name="code"></a><span data-ttu-id="72dd0-114">Kod</span><span class="sxs-lookup"><span data-stu-id="72dd0-114">Code</span></span>  
 [!code-xaml[ScrollBarCustomThumbSize#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ScrollBarCustomThumbSize/CS/Window1.xaml#2)]  
  
## <a name="see-also"></a><span data-ttu-id="72dd0-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="72dd0-115">See also</span></span>

- [<span data-ttu-id="72dd0-116">ScrollBar Stilleri ve Şablonları</span><span class="sxs-lookup"><span data-stu-id="72dd0-116">ScrollBar Styles and Templates</span></span>](scrollbar-styles-and-templates.md)
