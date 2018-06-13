---
title: 'Nasıl yapılır: Otomatik Düzen için Kılavuz Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- grids [WPF], automatic layout
- automatic layout [WPF], grid use
ms.assetid: ab9de407-e0c1-4047-bdf0-24951bf73879
ms.openlocfilehash: 6ea0b64af07924867c2de97baf5a81f8e8da6a56
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544628"
---
# <a name="how-to-use-a-grid-for-automatic-layout"></a><span data-ttu-id="05325-102">Nasıl yapılır: Otomatik Düzen için Kılavuz Kullanma</span><span class="sxs-lookup"><span data-stu-id="05325-102">How to: Use a Grid for Automatic Layout</span></span>
<span data-ttu-id="05325-103">Bu örnek, otomatik düzen yaklaşımı yerelleştirilebilir bir uygulama oluşturmak için bir kılavuz kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="05325-103">This example describes how to use a grid in the automatic layout approach to creating a localizable application.</span></span>  
  
 <span data-ttu-id="05325-104">Yerelleştirme bir [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] uzun süren bir işlem olabilir.</span><span class="sxs-lookup"><span data-stu-id="05325-104">Localization of a [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] can be a time consuming process.</span></span> <span data-ttu-id="05325-105">Yeniden Boyutlandır ve metin çevirme yanı sıra öğeleri yeniden konumlandırmak genellikle çevirmenlerin gerekir.</span><span class="sxs-lookup"><span data-stu-id="05325-105">Often localizers need to re-size and reposition elements in addition to translating text.</span></span> <span data-ttu-id="05325-106">Geçmişte her dil, bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] için gerekli ayarlama uyarlandığı.</span><span class="sxs-lookup"><span data-stu-id="05325-106">In the past each language that a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] was adapted for required adjustment.</span></span> <span data-ttu-id="05325-107">Şimdi özelliklerini ile [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ayarlama gereksinimini azaltan öğeler tasarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="05325-107">Now with the capabilities of [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] you can design elements that reduce the need for adjustment.</span></span> <span data-ttu-id="05325-108">Daha kolay yeniden boyutlandırılmış ve konumlandırılabilir uygulamaları yazma yaklaşımına adlı `auto layout`.</span><span class="sxs-lookup"><span data-stu-id="05325-108">The approach to writing applications that can be more easily re-sized and repositioned is called `auto layout`.</span></span>  
  
 <span data-ttu-id="05325-109">Aşağıdaki [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] örnek, bazı düğmeler ve metin konumlandırmak için kılavuz kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="05325-109">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] example demonstrates using a grid to position some buttons and text.</span></span> <span data-ttu-id="05325-110">Hücrelerin genişliği ve yüksekliği ayarlanır bildirimi `Auto`; bu nedenle bir görüntüyle düğmeyi içeren hücre Resmi sığacak şekilde ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="05325-110">Notice that the height and width of the cells are set to `Auto`; therefore the cell that contains the button with an image adjusts to fit the image.</span></span> <span data-ttu-id="05325-111">Çünkü <xref:System.Windows.Controls.Grid> öğesi içeriğini yararlı olabilir yerelleştirilebilir uygulamalar tasarlamada için otomatik düzen yaklaşımını almak için ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="05325-111">Because the <xref:System.Windows.Controls.Grid> element can adjust to its content it can be useful when taking the automatic layout approach to designing applications that can be localized.</span></span>  
  
## <a name="example"></a><span data-ttu-id="05325-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="05325-112">Example</span></span>  
 <span data-ttu-id="05325-113">Aşağıdaki örnekte bir kılavuz kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="05325-113">The following example shows how to use a grid.</span></span>  
  
 [!code-xaml[LocalizationGrid#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#1)]  
  
 <span data-ttu-id="05325-114">Aşağıdaki grafikte kod örneği çıktısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="05325-114">The following graphic shows the output of the code sample.</span></span>  
  
 <span data-ttu-id="05325-115">![Kılavuz örnek](../../../../docs/framework/wpf/advanced/media/glob-grid.png "glob_grid")</span><span class="sxs-lookup"><span data-stu-id="05325-115">![Grid example](../../../../docs/framework/wpf/advanced/media/glob-grid.png "glob_grid")</span></span>  
<span data-ttu-id="05325-116">Kılavuz</span><span class="sxs-lookup"><span data-stu-id="05325-116">Grid</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05325-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="05325-117">See Also</span></span>  
 [<span data-ttu-id="05325-118">Otomatik Düzen Kullanımına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="05325-118">Use Automatic Layout Overview</span></span>](../../../../docs/framework/wpf/advanced/use-automatic-layout-overview.md)  
 [<span data-ttu-id="05325-119">Düğme Oluşturmak için Otomatik Düzeni Kullanma</span><span class="sxs-lookup"><span data-stu-id="05325-119">Use Automatic Layout to Create a Button</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-automatic-layout-to-create-a-button.md)
