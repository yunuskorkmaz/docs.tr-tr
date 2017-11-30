---
title: "Nasıl yapılır: Düğme Oluşturmak için Otomatik Düzeni Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Button controls [WPF], creating with automatic layout
- automatic layout [WPF], creating buttons
ms.assetid: 96c206d0-9e77-4784-9d2d-5045aed2021c
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7d55dc1330c21e7eb9f7cfd7f554234dccd6f274
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-automatic-layout-to-create-a-button"></a><span data-ttu-id="2b52e-102">Nasıl yapılır: Düğme Oluşturmak için Otomatik Düzeni Kullanma</span><span class="sxs-lookup"><span data-stu-id="2b52e-102">How to: Use Automatic Layout to Create a Button</span></span>
<span data-ttu-id="2b52e-103">Bu örnek, otomatik düzen yaklaşımı yerelleştirilebilir bir uygulamada bir düğme oluşturmak için nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="2b52e-103">This example describes how to use the automatic layout approach to create a button in a localizable application.</span></span>  
  
 <span data-ttu-id="2b52e-104">Yerelleştirme bir [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] uzun süren bir işlem olabilir.</span><span class="sxs-lookup"><span data-stu-id="2b52e-104">Localization of a [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] can be a time consuming process.</span></span> <span data-ttu-id="2b52e-105">Yeniden boyutlandırma ve metin çevirme yanı sıra öğeleri yeniden konumlandırmak genellikle çevirmenlerin gerekir.</span><span class="sxs-lookup"><span data-stu-id="2b52e-105">Often localizers need to resize and reposition elements in addition to translating text.</span></span> <span data-ttu-id="2b52e-106">Geçmişte her dil, bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] için gerekli ayarlama uyarlandığı.</span><span class="sxs-lookup"><span data-stu-id="2b52e-106">In the past each language that a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] was adapted for required adjustment.</span></span> <span data-ttu-id="2b52e-107">Şimdi özelliklerini ile [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ayarlama gereksinimini azaltan öğeler tasarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2b52e-107">Now with the capabilities of [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] you can design elements that reduce the need for adjustment.</span></span> <span data-ttu-id="2b52e-108">Daha kolay yeniden boyutlandırılan ve konumlandırılabilir uygulamaları yazma yaklaşımına adlı `automatic layout`.</span><span class="sxs-lookup"><span data-stu-id="2b52e-108">The approach to writing applications that can be more easily resized and repositioned is called `automatic layout`.</span></span>  
  
 <span data-ttu-id="2b52e-109">Aşağıdaki iki [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] örnekler bir düğme; İngilizce metinle diğeri İspanyolca metinle örneği uygulamalar oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2b52e-109">The following two [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] examples create applications that instantiate a button; one with English text and one with Spanish text.</span></span> <span data-ttu-id="2b52e-110">Kod metni dışında aynı olduğuna dikkat edin; Düğme metni uyacak şekilde ayarlar.</span><span class="sxs-lookup"><span data-stu-id="2b52e-110">Notice that the code is the same except for the text; the button adjusts to fit the text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b52e-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="2b52e-111">Example</span></span>  
 [!code-xaml[LocalizationBtn_snip#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn_snip/CS/Pane1.xaml#1)]  
  
 [!code-xaml[LocalizationBtn#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn/CS/Pane1.xaml#1)]  
  
 <span data-ttu-id="2b52e-112">Aşağıdaki grafikte kod örnekleri çıktısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2b52e-112">The following graphic shows the output of the code samples.</span></span>  
  
 <span data-ttu-id="2b52e-113">![Farklı dillerde aynı düğmenin](../../../../docs/framework/wpf/advanced/media/globalizationbutton.png "GlobalizationButton")</span><span class="sxs-lookup"><span data-stu-id="2b52e-113">![The same button with text in different languages](../../../../docs/framework/wpf/advanced/media/globalizationbutton.png "GlobalizationButton")</span></span>  
<span data-ttu-id="2b52e-114">Otomatik yeniden boyutlandırılabilir düğmesi</span><span class="sxs-lookup"><span data-stu-id="2b52e-114">Auto Resizable Button</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b52e-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2b52e-115">See Also</span></span>  
 [<span data-ttu-id="2b52e-116">Otomatik Düzen Kullanım genel bakış</span><span class="sxs-lookup"><span data-stu-id="2b52e-116">Use Automatic Layout Overview</span></span>](../../../../docs/framework/wpf/advanced/use-automatic-layout-overview.md)  
 [<span data-ttu-id="2b52e-117">Bir kılavuz için otomatik düzenini kullanın</span><span class="sxs-lookup"><span data-stu-id="2b52e-117">Use a Grid for Automatic Layout</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-a-grid-for-automatic-layout.md)
