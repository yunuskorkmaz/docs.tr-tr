---
title: 'Nasıl yapılır: Otomatik Düzen için Kılavuz Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- grids [WPF], automatic layout
- automatic layout [WPF], grid use
ms.assetid: ab9de407-e0c1-4047-bdf0-24951bf73879
ms.openlocfilehash: 0eda70a7d8cc5abb70b5043cbaa1d4fc418bb1f4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54611429"
---
# <a name="how-to-use-a-grid-for-automatic-layout"></a><span data-ttu-id="16456-102">Nasıl yapılır: Otomatik Düzen için Kılavuz Kullanma</span><span class="sxs-lookup"><span data-stu-id="16456-102">How to: Use a Grid for Automatic Layout</span></span>
<span data-ttu-id="16456-103">Bu örnek, bir kılavuz yerelleştirilebilir bir uygulama oluşturmak için otomatik düzeni yaklaşımda kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="16456-103">This example describes how to use a grid in the automatic layout approach to creating a localizable application.</span></span>  
  
 <span data-ttu-id="16456-104">Yerelleştirme bir [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] zaman alıcı bir işlem olabilir.</span><span class="sxs-lookup"><span data-stu-id="16456-104">Localization of a [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] can be a time consuming process.</span></span> <span data-ttu-id="16456-105">Yerelleştiriciler genellikle, yeniden boyutlandırabilir ve metin çevirme yanı sıra öğeleri yeniden konumlandırmak gerekir.</span><span class="sxs-lookup"><span data-stu-id="16456-105">Often localizers need to re-size and reposition elements in addition to translating text.</span></span> <span data-ttu-id="16456-106">Geçmişteki her dil, bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] gerekli ayarlamaya yönelik uyarlandığı.</span><span class="sxs-lookup"><span data-stu-id="16456-106">In the past each language that a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] was adapted for required adjustment.</span></span> <span data-ttu-id="16456-107">Artık yeteneklerini ile [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ayarlama gereksinimini azaltan öğeleri tasarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16456-107">Now with the capabilities of [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] you can design elements that reduce the need for adjustment.</span></span> <span data-ttu-id="16456-108">Daha kolay yeniden boyutlandırılmış ve konumlandırılabilir uygulamaları yazma yaklaşımı adlı `auto layout`.</span><span class="sxs-lookup"><span data-stu-id="16456-108">The approach to writing applications that can be more easily re-sized and repositioned is called `auto layout`.</span></span>  
  
 <span data-ttu-id="16456-109">Aşağıdaki [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] örnek, bazı düğme ve metin konumlandırmak için bir kılavuz kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="16456-109">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] example demonstrates using a grid to position some buttons and text.</span></span> <span data-ttu-id="16456-110">Hücre genişliği ve yüksekliği ayarlandığından bildirimi `Auto`; bu nedenle resim sığacak şekilde düğmesi bir görüntü içeren hücreye ayarlar.</span><span class="sxs-lookup"><span data-stu-id="16456-110">Notice that the height and width of the cells are set to `Auto`; therefore the cell that contains the button with an image adjusts to fit the image.</span></span> <span data-ttu-id="16456-111">Çünkü <xref:System.Windows.Controls.Grid> öğesi yararlı olabilir yerelleştirilebilen uygulamalar tasarlama için otomatik düzeni yaklaşımı, içeriği ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16456-111">Because the <xref:System.Windows.Controls.Grid> element can adjust to its content it can be useful when taking the automatic layout approach to designing applications that can be localized.</span></span>  
  
## <a name="example"></a><span data-ttu-id="16456-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="16456-112">Example</span></span>  
 <span data-ttu-id="16456-113">Aşağıdaki örnek, bir kılavuz kullanma işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="16456-113">The following example shows how to use a grid.</span></span>  
  
 [!code-xaml[LocalizationGrid#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#1)]  
  
 <span data-ttu-id="16456-114">Aşağıdaki kod örneği çıktısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="16456-114">The following graphic shows the output of the code sample.</span></span>  
  
 <span data-ttu-id="16456-115">![Grid örneği](../../../../docs/framework/wpf/advanced/media/glob-grid.png "glob_grid")</span><span class="sxs-lookup"><span data-stu-id="16456-115">![Grid example](../../../../docs/framework/wpf/advanced/media/glob-grid.png "glob_grid")</span></span>  
<span data-ttu-id="16456-116">Kılavuz</span><span class="sxs-lookup"><span data-stu-id="16456-116">Grid</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16456-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="16456-117">See also</span></span>
- [<span data-ttu-id="16456-118">Otomatik Düzen Kullanımına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="16456-118">Use Automatic Layout Overview</span></span>](../../../../docs/framework/wpf/advanced/use-automatic-layout-overview.md)
- [<span data-ttu-id="16456-119">Düğme Oluşturmak için Otomatik Düzeni Kullanma</span><span class="sxs-lookup"><span data-stu-id="16456-119">Use Automatic Layout to Create a Button</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-automatic-layout-to-create-a-button.md)
