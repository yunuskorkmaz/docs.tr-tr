---
title: UI Otomasyonunu Kullanarak Çapraz Geçiş Yapma
description: Microsoft UI Otomasyonu kullanarak bir belgenin metin içeriğinin nasıl gezilmesine ilişkin bir örnek olan TextUnit artışlarına bakın.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, traversing text
- text, traversing
- traversing text
ms.assetid: 3ddb3b7b-1d6b-4dba-8678-5a68e868aadb
ms.openlocfilehash: 0b4269d043fd6cd0cc5da9825714aab4ead701f9
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168092"
---
# <a name="traverse-text-using-ui-automation"></a><span data-ttu-id="665e0-103">UI Otomasyonunu Kullanarak Çapraz Geçiş Yapma</span><span class="sxs-lookup"><span data-stu-id="665e0-103">Traverse Text Using UI Automation</span></span>
> [!NOTE]
> <span data-ttu-id="665e0-104">Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> .</span><span class="sxs-lookup"><span data-stu-id="665e0-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="665e0-105">Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="665e0-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="665e0-106">Bu konu başlığı altında [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] , bir belgenin metin içeriğini artışlarla çapraz geçiş için nasıl kullanılacağı gösterilmektedir <xref:System.Windows.Automation.Text.TextUnit> .</span><span class="sxs-lookup"><span data-stu-id="665e0-106">This topic shows how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to traverse the textual content of a document by <xref:System.Windows.Automation.Text.TextUnit> increments.</span></span>  
  
## <a name="example"></a><span data-ttu-id="665e0-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="665e0-107">Example</span></span>  
 <span data-ttu-id="665e0-108">Aşağıdaki kod örneğinde, bir UI Otomasyon metin sağlayıcısı içeriğinin nasıl gezeceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="665e0-108">The following code example demonstrates how to traverse the content of a UI Automation text provider.</span></span> <span data-ttu-id="665e0-109"><xref:System.Windows.Automation.Text.TextPatternRange.Move%2A>Yöntemi <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> ' <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> a ait ve uç noktalarını taşıdıkça <xref:System.Windows.Automation.Text.TextPatternRange> .</span><span class="sxs-lookup"><span data-stu-id="665e0-109">The <xref:System.Windows.Automation.Text.TextPatternRange.Move%2A> method moves the <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> and <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> endpoints of a <xref:System.Windows.Automation.Text.TextPatternRange>.</span></span> <span data-ttu-id="665e0-110">Bu metin aralığı genellikle metin ekleme noktasını temsil eden bir bozuk aralığıdır.</span><span class="sxs-lookup"><span data-stu-id="665e0-110">This text range is typically a degenerate range representing the text insertion point.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="665e0-111">Yalnızca metin tabanlı katıştırılmış nesneler metin akışının parçası olarak kabul edildiğinden, resimler gibi katıştırılmış nesneler `Move` veya dönüş değeri etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="665e0-111">Since only text-based embedded objects are considered part of the text stream, embedded objects such as images do not affect `Move` or its return value.</span></span>  
  
[!code-csharp[FindText#StartApp](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#startapp)]
[!code-vb[FindText#StartApp](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#startapp)]  
[!code-csharp[FindText#FindTextProvider](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#findtextprovider)]
[!code-vb[FindText#FindTextProvider](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#findtextprovider)]  
[!code-csharp[FindText#Navigate](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#navigate)]
[!code-vb[FindText#Navigate](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#navigate)]  
  
 <span data-ttu-id="665e0-112">Kullanılan herhangi bir yöntem, <xref:System.Windows.Automation.Text.TextUnit> <xref:System.Windows.Automation.Text.TextUnit> verilen <xref:System.Windows.Automation.Text.TextUnit> Denetim tarafından desteklenmiyorsa, desteklenen bir sonraki en büyük öğesine ertelenecek.</span><span class="sxs-lookup"><span data-stu-id="665e0-112">Any method using <xref:System.Windows.Automation.Text.TextUnit> will defer to the next largest <xref:System.Windows.Automation.Text.TextUnit> supported if the given <xref:System.Windows.Automation.Text.TextUnit> is not supported by the control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="665e0-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="665e0-113">See also</span></span>

- [<span data-ttu-id="665e0-114">UI Otomasyon TextPattern Öğesine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="665e0-114">UI Automation TextPattern Overview</span></span>](ui-automation-textpattern-overview.md)
- [<span data-ttu-id="665e0-115">UI Otomasyonu Kullanarak Metin Kutusuna İçerik Ekleme</span><span class="sxs-lookup"><span data-stu-id="665e0-115">Add Content to a Text Box Using UI Automation</span></span>](add-content-to-a-text-box-using-ui-automation.md)
- [<span data-ttu-id="665e0-116">UI Otomasyonunu Kullanarak Metin Bulma ve Vurgulama</span><span class="sxs-lookup"><span data-stu-id="665e0-116">Find and Highlight Text Using UI Automation</span></span>](find-and-highlight-text-using-ui-automation.md)
- [<span data-ttu-id="665e0-117">UI Otomasyon Denetim Düzenlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="665e0-117">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="665e0-118">İstemciler İçin UI Otomasyon Denetim Düzenleri</span><span class="sxs-lookup"><span data-stu-id="665e0-118">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
