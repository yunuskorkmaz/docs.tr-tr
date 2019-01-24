---
title: 'Nasıl yapılır: Düğme Oluşturmak için Otomatik Düzeni Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- Button controls [WPF], creating with automatic layout
- automatic layout [WPF], creating buttons
ms.assetid: 96c206d0-9e77-4784-9d2d-5045aed2021c
ms.openlocfilehash: 501341f0e71e6e5a224c51e4ae01c68ce6b845cb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54543493"
---
# <a name="how-to-use-automatic-layout-to-create-a-button"></a><span data-ttu-id="e9a86-102">Nasıl yapılır: Düğme Oluşturmak için Otomatik Düzeni Kullanma</span><span class="sxs-lookup"><span data-stu-id="e9a86-102">How to: Use Automatic Layout to Create a Button</span></span>
<span data-ttu-id="e9a86-103">Bu örnek, bir yerelleştirilebilir uygulamasında bir düğme oluşturmak için otomatik düzen yaklaşımı kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="e9a86-103">This example describes how to use the automatic layout approach to create a button in a localizable application.</span></span>  
  
 <span data-ttu-id="e9a86-104">Yerelleştirme bir [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] zaman alıcı bir işlem olabilir.</span><span class="sxs-lookup"><span data-stu-id="e9a86-104">Localization of a [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] can be a time consuming process.</span></span> <span data-ttu-id="e9a86-105">Yerelleştiriciler genellikle, yeniden boyutlandırabilir ve metin çevirme yanı sıra öğeleri yeniden konumlandırmak gerekir.</span><span class="sxs-lookup"><span data-stu-id="e9a86-105">Often localizers need to resize and reposition elements in addition to translating text.</span></span> <span data-ttu-id="e9a86-106">Geçmişteki her dil, bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] gerekli ayarlamaya yönelik uyarlandığı.</span><span class="sxs-lookup"><span data-stu-id="e9a86-106">In the past each language that a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] was adapted for required adjustment.</span></span> <span data-ttu-id="e9a86-107">Artık yeteneklerini ile [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ayarlama gereksinimini azaltan öğeleri tasarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e9a86-107">Now with the capabilities of [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] you can design elements that reduce the need for adjustment.</span></span> <span data-ttu-id="e9a86-108">Daha kolay yeniden boyutlandırılan ve konumlandırılabilir uygulamaları yazma yaklaşımı adlı `automatic layout`.</span><span class="sxs-lookup"><span data-stu-id="e9a86-108">The approach to writing applications that can be more easily resized and repositioned is called `automatic layout`.</span></span>  
  
 <span data-ttu-id="e9a86-109">Aşağıdaki iki [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] örnekler bir düğme; İngilizce metni ile diğeri yaratır örneği uygulamalar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e9a86-109">The following two [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] examples create applications that instantiate a button; one with English text and one with Spanish text.</span></span> <span data-ttu-id="e9a86-110">Kod metni dışında aynı olduğuna dikkat edin; Düğme metin sığdırmak için ayarlar.</span><span class="sxs-lookup"><span data-stu-id="e9a86-110">Notice that the code is the same except for the text; the button adjusts to fit the text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e9a86-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="e9a86-111">Example</span></span>  
 [!code-xaml[LocalizationBtn_snip#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn_snip/CS/Pane1.xaml#1)]  
  
 [!code-xaml[LocalizationBtn#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn/CS/Pane1.xaml#1)]  
  
 <span data-ttu-id="e9a86-112">Aşağıdaki grafikte, kod örnekleri çıktısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e9a86-112">The following graphic shows the output of the code samples.</span></span>  
  
 <span data-ttu-id="e9a86-113">![Farklı dillerde aynı düğmenin](../../../../docs/framework/wpf/advanced/media/globalizationbutton.png "GlobalizationButton")</span><span class="sxs-lookup"><span data-stu-id="e9a86-113">![The same button with text in different languages](../../../../docs/framework/wpf/advanced/media/globalizationbutton.png "GlobalizationButton")</span></span>  
<span data-ttu-id="e9a86-114">Otomatik yeniden boyutlandırılabilir düğmesi</span><span class="sxs-lookup"><span data-stu-id="e9a86-114">Auto Resizable Button</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9a86-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e9a86-115">See also</span></span>
- [<span data-ttu-id="e9a86-116">Otomatik Düzen Kullanımına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e9a86-116">Use Automatic Layout Overview</span></span>](../../../../docs/framework/wpf/advanced/use-automatic-layout-overview.md)
- [<span data-ttu-id="e9a86-117">Otomatik Düzen için Kılavuz Kullanma</span><span class="sxs-lookup"><span data-stu-id="e9a86-117">Use a Grid for Automatic Layout</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-a-grid-for-automatic-layout.md)
