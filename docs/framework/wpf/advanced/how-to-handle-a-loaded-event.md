---
title: 'Nasıl yapılır: Yüklü Bir Olayı İşleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XAML [WPF], Loaded events
- events [WPF], Loaded
- Loaded events [WPF]
ms.assetid: 0cf8d003-8441-4df4-807a-6db09347e829
ms.openlocfilehash: a4916d3cfd20d082a8466f61fc74e16db2f0f346
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57353354"
---
# <a name="how-to-handle-a-loaded-event"></a><span data-ttu-id="ec273-102">Nasıl yapılır: Yüklü Bir Olayı İşleme</span><span class="sxs-lookup"><span data-stu-id="ec273-102">How to: Handle a Loaded Event</span></span>
<span data-ttu-id="ec273-103">Bu örnek nasıl işleneceğini gösterir <xref:System.Windows.FrameworkElement.Loaded?displayProperty=nameWithType> olay ve olay işleme için uygun bir senaryo.</span><span class="sxs-lookup"><span data-stu-id="ec273-103">This example shows how to handle the <xref:System.Windows.FrameworkElement.Loaded?displayProperty=nameWithType> event, and an appropriate scenario for handling that event.</span></span> <span data-ttu-id="ec273-104">İşleyici oluşturur bir <xref:System.Windows.Controls.Button> Sayfa yüklediğinde.</span><span class="sxs-lookup"><span data-stu-id="ec273-104">The handler  creates a <xref:System.Windows.Controls.Button> when the page loads.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec273-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="ec273-105">Example</span></span>  
 <span data-ttu-id="ec273-106">Aşağıdaki örnekte [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] birlikte bir arka plan kod dosyası.</span><span class="sxs-lookup"><span data-stu-id="ec273-106">The following example uses [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] together with a code-behind file.</span></span>  
  
 [!code-xaml[FELoaded#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FELoaded/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[FELoaded#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/FELoaded/CSharp/default.xaml.cs#handler)]
 [!code-vb[FELoaded#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FELoaded/VisualBasic/default.xaml.vb#handler)]  
  
## <a name="see-also"></a><span data-ttu-id="ec273-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ec273-107">See also</span></span>
- <xref:System.Windows.FrameworkElement>
- [<span data-ttu-id="ec273-108">Nesne Yaşam Süresi Olayları</span><span class="sxs-lookup"><span data-stu-id="ec273-108">Object Lifetime Events</span></span>](object-lifetime-events.md)
- [<span data-ttu-id="ec273-109">Yönlendirilmiş Olaylara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ec273-109">Routed Events Overview</span></span>](routed-events-overview.md)
- [<span data-ttu-id="ec273-110">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="ec273-110">How-to Topics</span></span>](base-elements-how-to-topics.md)
