---
title: TextBlock Genel Bakışı
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], TextBlock
- TextBlock control [WPF]
ms.assetid: 24720bca-341a-4b03-8a6b-7a678023b10a
ms.openlocfilehash: 2c6865fd4f61146fc7c469c197944561460e81be
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54530302"
---
# <a name="textblock-overview"></a><span data-ttu-id="0772f-102">TextBlock Genel Bakışı</span><span class="sxs-lookup"><span data-stu-id="0772f-102">TextBlock Overview</span></span>
<span data-ttu-id="0772f-103"><xref:System.Windows.Controls.TextBlock> Denetim sağlayan esnek metin desteği [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="0772f-103">The <xref:System.Windows.Controls.TextBlock> control provides flexible text support for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications.</span></span> <span data-ttu-id="0772f-104">Öğe, öncelikli olarak doğru temel hedeflenen [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] metnin birden fazla paragraf gerektirmeyen senaryolar.</span><span class="sxs-lookup"><span data-stu-id="0772f-104">The element is targeted primarily toward basic [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] scenarios that do not require more than one paragraph of text.</span></span> <span data-ttu-id="0772f-105">Bir dizi gibi sunum, kesin bir denetim sağlayan özellikleri destekleyen <xref:System.Windows.Controls.TextBlock.FontFamily%2A>, <xref:System.Windows.Controls.TextBlock.FontSize%2A>, <xref:System.Windows.Controls.TextBlock.FontWeight%2A>, <xref:System.Windows.Controls.TextBlock.TextEffects%2A>, ve <xref:System.Windows.Controls.TextBlock.TextWrapping%2A>.</span><span class="sxs-lookup"><span data-stu-id="0772f-105">It supports a number of properties that enable precise control of presentation, such as <xref:System.Windows.Controls.TextBlock.FontFamily%2A>, <xref:System.Windows.Controls.TextBlock.FontSize%2A>, <xref:System.Windows.Controls.TextBlock.FontWeight%2A>, <xref:System.Windows.Controls.TextBlock.TextEffects%2A>, and <xref:System.Windows.Controls.TextBlock.TextWrapping%2A>.</span></span> <span data-ttu-id="0772f-106">Metin içeriğini kullanarak eklenebilir <xref:System.Windows.Controls.TextBlock.Text%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="0772f-106">Text content can be added using the <xref:System.Windows.Controls.TextBlock.Text%2A> property.</span></span> <span data-ttu-id="0772f-107">Kullanıldığında [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], içeriği açma ve kapatma etiketi arasında örtük olarak öğenin metin olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="0772f-107">When used in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], content between the open and closing tag is implicitly added as the text of the element.</span></span>  
  
 <span data-ttu-id="0772f-108">A <xref:System.Windows.Controls.TextBlock> öğesi çok basit kullanarak oluşturulabilir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0772f-108">A <xref:System.Windows.Controls.TextBlock> element can be instantiated very simply using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 [!code-xaml[TextBlockSnip_XAML#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBlockSnip_XAML/CS/default.xaml#2)]  
  
 <span data-ttu-id="0772f-109">Benzer şekilde, kullanımını <xref:System.Windows.Controls.TextBlock> kod öğesinde oldukça basittir.</span><span class="sxs-lookup"><span data-stu-id="0772f-109">Similarly, usage of the <xref:System.Windows.Controls.TextBlock> element in code is relatively simple.</span></span>  
  
 [!code-csharp[TextBlockSnip#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBlockSnip/CSharp/TextBlockSnips.cs#1)]
 [!code-vb[TextBlockSnip#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBlockSnip/VisualBasic/TextBlockSnips.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="0772f-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0772f-110">See also</span></span>
- <xref:System.Windows.Controls.Label>
