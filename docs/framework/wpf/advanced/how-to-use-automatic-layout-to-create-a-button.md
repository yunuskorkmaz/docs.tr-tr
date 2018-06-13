---
title: 'Nasıl yapılır: Düğme Oluşturmak için Otomatik Düzeni Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- Button controls [WPF], creating with automatic layout
- automatic layout [WPF], creating buttons
ms.assetid: 96c206d0-9e77-4784-9d2d-5045aed2021c
ms.openlocfilehash: 34b372e886b31e801b5598da90299f9815c47620
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545220"
---
# <a name="how-to-use-automatic-layout-to-create-a-button"></a><span data-ttu-id="aeda0-102">Nasıl yapılır: Düğme Oluşturmak için Otomatik Düzeni Kullanma</span><span class="sxs-lookup"><span data-stu-id="aeda0-102">How to: Use Automatic Layout to Create a Button</span></span>
<span data-ttu-id="aeda0-103">Bu örnek, otomatik düzen yaklaşımı yerelleştirilebilir bir uygulamada bir düğme oluşturmak için nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="aeda0-103">This example describes how to use the automatic layout approach to create a button in a localizable application.</span></span>  
  
 <span data-ttu-id="aeda0-104">Yerelleştirme bir [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] uzun süren bir işlem olabilir.</span><span class="sxs-lookup"><span data-stu-id="aeda0-104">Localization of a [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] can be a time consuming process.</span></span> <span data-ttu-id="aeda0-105">Yeniden boyutlandırma ve metin çevirme yanı sıra öğeleri yeniden konumlandırmak genellikle çevirmenlerin gerekir.</span><span class="sxs-lookup"><span data-stu-id="aeda0-105">Often localizers need to resize and reposition elements in addition to translating text.</span></span> <span data-ttu-id="aeda0-106">Geçmişte her dil, bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] için gerekli ayarlama uyarlandığı.</span><span class="sxs-lookup"><span data-stu-id="aeda0-106">In the past each language that a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] was adapted for required adjustment.</span></span> <span data-ttu-id="aeda0-107">Şimdi özelliklerini ile [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ayarlama gereksinimini azaltan öğeler tasarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aeda0-107">Now with the capabilities of [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] you can design elements that reduce the need for adjustment.</span></span> <span data-ttu-id="aeda0-108">Daha kolay yeniden boyutlandırılan ve konumlandırılabilir uygulamaları yazma yaklaşımına adlı `automatic layout`.</span><span class="sxs-lookup"><span data-stu-id="aeda0-108">The approach to writing applications that can be more easily resized and repositioned is called `automatic layout`.</span></span>  
  
 <span data-ttu-id="aeda0-109">Aşağıdaki iki [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] örnekler bir düğme; İngilizce metinle diğeri İspanyolca metinle örneği uygulamalar oluşturun.</span><span class="sxs-lookup"><span data-stu-id="aeda0-109">The following two [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] examples create applications that instantiate a button; one with English text and one with Spanish text.</span></span> <span data-ttu-id="aeda0-110">Kod metni dışında aynı olduğuna dikkat edin; Düğme metni uyacak şekilde ayarlar.</span><span class="sxs-lookup"><span data-stu-id="aeda0-110">Notice that the code is the same except for the text; the button adjusts to fit the text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aeda0-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="aeda0-111">Example</span></span>  
 [!code-xaml[LocalizationBtn_snip#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn_snip/CS/Pane1.xaml#1)]  
  
 [!code-xaml[LocalizationBtn#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn/CS/Pane1.xaml#1)]  
  
 <span data-ttu-id="aeda0-112">Aşağıdaki grafikte kod örnekleri çıktısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="aeda0-112">The following graphic shows the output of the code samples.</span></span>  
  
 <span data-ttu-id="aeda0-113">![Farklı dillerde aynı düğmenin](../../../../docs/framework/wpf/advanced/media/globalizationbutton.png "GlobalizationButton")</span><span class="sxs-lookup"><span data-stu-id="aeda0-113">![The same button with text in different languages](../../../../docs/framework/wpf/advanced/media/globalizationbutton.png "GlobalizationButton")</span></span>  
<span data-ttu-id="aeda0-114">Otomatik yeniden boyutlandırılabilir düğmesi</span><span class="sxs-lookup"><span data-stu-id="aeda0-114">Auto Resizable Button</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aeda0-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="aeda0-115">See Also</span></span>  
 [<span data-ttu-id="aeda0-116">Otomatik Düzen Kullanımına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="aeda0-116">Use Automatic Layout Overview</span></span>](../../../../docs/framework/wpf/advanced/use-automatic-layout-overview.md)  
 [<span data-ttu-id="aeda0-117">Otomatik Düzen için Kılavuz Kullanma</span><span class="sxs-lookup"><span data-stu-id="aeda0-117">Use a Grid for Automatic Layout</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-a-grid-for-automatic-layout.md)
