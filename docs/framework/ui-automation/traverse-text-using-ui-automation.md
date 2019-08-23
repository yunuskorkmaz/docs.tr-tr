---
title: UI Otomasyonunu Kullanarak Çapraz Geçiş Yapma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, traversing text
- text, traversing
- traversing text
ms.assetid: 3ddb3b7b-1d6b-4dba-8678-5a68e868aadb
ms.openlocfilehash: fe0b27e1185412a09bafc1ecdcf94d3f3c586c51
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946367"
---
# <a name="traverse-text-using-ui-automation"></a><span data-ttu-id="15e6b-102">UI Otomasyonunu Kullanarak Çapraz Geçiş Yapma</span><span class="sxs-lookup"><span data-stu-id="15e6b-102">Traverse Text Using UI Automation</span></span>
> [!NOTE]
> <span data-ttu-id="15e6b-103">Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="15e6b-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="15e6b-104">Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="15e6b-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="15e6b-105">Bu konu başlığı altında, bir [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] <xref:System.Windows.Automation.Text.TextUnit> belgenin metin içeriğini artışlarla çapraz geçiş için nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="15e6b-105">This topic shows how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to traverse the textual content of a document by <xref:System.Windows.Automation.Text.TextUnit> increments.</span></span>  
  
## <a name="example"></a><span data-ttu-id="15e6b-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="15e6b-106">Example</span></span>  
 <span data-ttu-id="15e6b-107">Aşağıdaki kod örneğinde, bir UI Otomasyon metin sağlayıcısı içeriğinin nasıl gezeceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="15e6b-107">The following code example demonstrates how to traverse the content of a UI Automation text provider.</span></span> <span data-ttu-id="15e6b-108"><xref:System.Windows.Automation.Text.TextPatternRange.Move%2A> Yöntemi <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> ' <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> a aitveuçnoktalarınıtaşıdıkça<xref:System.Windows.Automation.Text.TextPatternRange>.</span><span class="sxs-lookup"><span data-stu-id="15e6b-108">The <xref:System.Windows.Automation.Text.TextPatternRange.Move%2A> method moves the <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> and <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> endpoints of a <xref:System.Windows.Automation.Text.TextPatternRange>.</span></span> <span data-ttu-id="15e6b-109">Bu metin aralığı genellikle metin ekleme noktasını temsil eden bir bozuk aralığıdır.</span><span class="sxs-lookup"><span data-stu-id="15e6b-109">This text range is typically a degenerate range representing the text insertion point.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="15e6b-110">Yalnızca metin tabanlı katıştırılmış nesneler metin akışının parçası olarak kabul edildiğinden, resimler gibi katıştırılmış nesneler veya dönüş değeri etkilenmez `Move` .</span><span class="sxs-lookup"><span data-stu-id="15e6b-110">Since only text-based embedded objects are considered part of the text stream, embedded objects such as images do not affect `Move` or its return value.</span></span>  
  
[!code-csharp[FindText#StartApp](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#startapp)]
[!code-vb[FindText#StartApp](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#startapp)]  
[!code-csharp[FindText#FindTextProvider](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#findtextprovider)]
[!code-vb[FindText#FindTextProvider](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#findtextprovider)]  
[!code-csharp[FindText#Navigate](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#navigate)]
[!code-vb[FindText#Navigate](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#navigate)]  
  
 <span data-ttu-id="15e6b-111">Kullanılan <xref:System.Windows.Automation.Text.TextUnit> herhangi bir yöntem, verilen <xref:System.Windows.Automation.Text.TextUnit> denetim tarafından desteklenmiyorsa <xref:System.Windows.Automation.Text.TextUnit> , desteklenen bir sonraki en büyük öğesine ertelenecek.</span><span class="sxs-lookup"><span data-stu-id="15e6b-111">Any method using <xref:System.Windows.Automation.Text.TextUnit> will defer to the next largest <xref:System.Windows.Automation.Text.TextUnit> supported if the given <xref:System.Windows.Automation.Text.TextUnit> is not supported by the control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15e6b-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="15e6b-112">See also</span></span>

- [<span data-ttu-id="15e6b-113">UI Otomasyonu TextPattern Öğesine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="15e6b-113">UI Automation TextPattern Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-textpattern-overview.md)
- [<span data-ttu-id="15e6b-114">UI Otomasyonu Kullanarak Metin Kutusuna İçerik Ekleme</span><span class="sxs-lookup"><span data-stu-id="15e6b-114">Add Content to a Text Box Using UI Automation</span></span>](../../../docs/framework/ui-automation/add-content-to-a-text-box-using-ui-automation.md)
- [<span data-ttu-id="15e6b-115">UI Otomasyonunu Kullanarak Metin Bulma ve Vurgulama</span><span class="sxs-lookup"><span data-stu-id="15e6b-115">Find and Highlight Text Using UI Automation</span></span>](../../../docs/framework/ui-automation/find-and-highlight-text-using-ui-automation.md)
- [<span data-ttu-id="15e6b-116">UI Otomasyonu Denetim Desenlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="15e6b-116">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="15e6b-117">İstemciler İçin UI Otomasyonu Denetim Düzenleri</span><span class="sxs-lookup"><span data-stu-id="15e6b-117">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
