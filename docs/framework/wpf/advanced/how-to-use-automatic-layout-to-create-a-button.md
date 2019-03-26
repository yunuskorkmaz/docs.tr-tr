---
title: 'Nasıl yapılır: Düğme Oluşturmak için Otomatik Düzeni Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- Button controls [WPF], creating with automatic layout
- automatic layout [WPF], creating buttons
ms.assetid: 96c206d0-9e77-4784-9d2d-5045aed2021c
ms.openlocfilehash: 8eb1e93dd87c210812c9b7758c744a616ef2d862
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2019
ms.locfileid: "58409789"
---
# <a name="how-to-use-automatic-layout-to-create-a-button"></a><span data-ttu-id="190fd-102">Nasıl yapılır: Düğme Oluşturmak için Otomatik Düzeni Kullanma</span><span class="sxs-lookup"><span data-stu-id="190fd-102">How to: Use Automatic Layout to Create a Button</span></span>
<span data-ttu-id="190fd-103">Bu örnek, bir yerelleştirilebilir uygulamasında bir düğme oluşturmak için otomatik düzen yaklaşımı kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="190fd-103">This example describes how to use the automatic layout approach to create a button in a localizable application.</span></span>  
  
 <span data-ttu-id="190fd-104">Yerelleştirme bir [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] zaman alıcı bir işlem olabilir.</span><span class="sxs-lookup"><span data-stu-id="190fd-104">Localization of a [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] can be a time consuming process.</span></span> <span data-ttu-id="190fd-105">Yerelleştiriciler genellikle, yeniden boyutlandırabilir ve metin çevirme yanı sıra öğeleri yeniden konumlandırmak gerekir.</span><span class="sxs-lookup"><span data-stu-id="190fd-105">Often localizers need to resize and reposition elements in addition to translating text.</span></span> <span data-ttu-id="190fd-106">Geçmişteki her dil, bir [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] gerekli ayarlamaya yönelik uyarlandığı.</span><span class="sxs-lookup"><span data-stu-id="190fd-106">In the past each language that a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] was adapted for required adjustment.</span></span> <span data-ttu-id="190fd-107">Artık yeteneklerini ile [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ayarlama gereksinimini azaltan öğeleri tasarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="190fd-107">Now with the capabilities of [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] you can design elements that reduce the need for adjustment.</span></span> <span data-ttu-id="190fd-108">Daha kolay yeniden boyutlandırılan ve konumlandırılabilir uygulamaları yazma yaklaşımı adlı `automatic layout`.</span><span class="sxs-lookup"><span data-stu-id="190fd-108">The approach to writing applications that can be more easily resized and repositioned is called `automatic layout`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="190fd-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="190fd-109">Example</span></span>  

<span data-ttu-id="190fd-110">Aşağıdaki iki [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] örnekler bir düğme; İngilizce metni ile diğeri yaratır örneği uygulamalar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="190fd-110">The following two [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] examples create applications that instantiate a button; one with English text and one with Spanish text.</span></span> <span data-ttu-id="190fd-111">Kod metni dışında aynı olduğuna dikkat edin; Düğme metin sığdırmak için ayarlar.</span><span class="sxs-lookup"><span data-stu-id="190fd-111">Notice that the code is the same except for the text; the button adjusts to fit the text.</span></span>

[!code-xaml[LocalizationBtn_snip#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn_snip/CS/Pane1.xaml#1)]  
  
[!code-xaml[LocalizationBtn#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn/CS/Pane1.xaml#1)]  
  
 <span data-ttu-id="190fd-112">Aşağıdaki grafikte, otomatik yeniden boyutlandırılabilir düğmelerle kod örnekleri çıktısını gösterir:</span><span class="sxs-lookup"><span data-stu-id="190fd-112">The following graphic shows the output of the code samples with auto-resizable buttons:</span></span>
  
 ![Farklı dillerde metinle aynı düğmesi](./media/use-automatic-layout-overview/auto-resizable-button.png)  
  
## <a name="see-also"></a><span data-ttu-id="190fd-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="190fd-114">See also</span></span>

- [<span data-ttu-id="190fd-115">Otomatik Düzen Kullanımına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="190fd-115">Use Automatic Layout Overview</span></span>](use-automatic-layout-overview.md)
- [<span data-ttu-id="190fd-116">Otomatik Düzen için Kılavuz Kullanma</span><span class="sxs-lookup"><span data-stu-id="190fd-116">Use a Grid for Automatic Layout</span></span>](how-to-use-a-grid-for-automatic-layout.md)
