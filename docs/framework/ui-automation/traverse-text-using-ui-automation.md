---
title: "UI Otomasyonunu Kullanarak Çapraz Geçiş Yapma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, traversing text
- text, traversing
- traversing text
ms.assetid: 3ddb3b7b-1d6b-4dba-8678-5a68e868aadb
caps.latest.revision: "11"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 5b3d08c0a6293b6621d9b6debfa4d63c8abaf3d0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="traverse-text-using-ui-automation"></a><span data-ttu-id="1efd6-102">UI Otomasyonunu Kullanarak Çapraz Geçiş Yapma</span><span class="sxs-lookup"><span data-stu-id="1efd6-102">Traverse Text Using UI Automation</span></span>
> [!NOTE]
>  <span data-ttu-id="1efd6-103">Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="1efd6-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="1efd6-104">Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="1efd6-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="1efd6-105">Bu konuda nasıl kullanılacağını gösterir [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] tarafından belgenin metinsel içeriği gezinmesine <xref:System.Windows.Automation.Text.TextUnit> artırır.</span><span class="sxs-lookup"><span data-stu-id="1efd6-105">This topic shows how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to traverse the textual content of a document by <xref:System.Windows.Automation.Text.TextUnit> increments.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1efd6-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="1efd6-106">Example</span></span>  
 <span data-ttu-id="1efd6-107">Aşağıdaki kod örneğinde UI Otomasyon metin sağlayıcı içeriğini gezme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1efd6-107">The following code example demonstrates how to traverse the content of a UI Automation text provider.</span></span> <span data-ttu-id="1efd6-108"><xref:System.Windows.Automation.Text.TextPatternRange.Move%2A> Yöntemi taşır <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> ve <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> uç noktalarına bir <xref:System.Windows.Automation.Text.TextPatternRange>.</span><span class="sxs-lookup"><span data-stu-id="1efd6-108">The <xref:System.Windows.Automation.Text.TextPatternRange.Move%2A> method moves the <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> and <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> endpoints of a <xref:System.Windows.Automation.Text.TextPatternRange>.</span></span> <span data-ttu-id="1efd6-109">Bu metin aralığını genellikle metin ekleme noktasını temsil eden bir bozuk aralıktır.</span><span class="sxs-lookup"><span data-stu-id="1efd6-109">This text range is typically a degenerate range representing the text insertion point.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1efd6-110">Katıştırılmış nesneler metin tabanlı metin akış parçası olarak kabul edilen yalnızca görüntüleri etkilemez gibi beri katıştırılmış nesneler `Move` veya dönüş değeri.</span><span class="sxs-lookup"><span data-stu-id="1efd6-110">Since only text-based embedded objects are considered part of the text stream, embedded objects such as images do not affect `Move` or its return value.</span></span>  
  
 [!code-csharp[FindText#StartApp](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#startapp)]
 [!code-vb[FindText#StartApp](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#startapp)]  
[!code-csharp[FindText#FindTextProvider](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#findtextprovider)]
[!code-vb[FindText#FindTextProvider](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#findtextprovider)]  
[!code-csharp[FindText#Navigate](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#navigate)]
[!code-vb[FindText#Navigate](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#navigate)]  
  
 <span data-ttu-id="1efd6-111">Herhangi bir yöntemini kullanarak <xref:System.Windows.Automation.Text.TextUnit> sonraki erteler en büyük <xref:System.Windows.Automation.Text.TextUnit> desteklenen IF verilen <xref:System.Windows.Automation.Text.TextUnit> denetim tarafından desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="1efd6-111">Any method using <xref:System.Windows.Automation.Text.TextUnit> will defer to the next largest <xref:System.Windows.Automation.Text.TextUnit> supported if the given <xref:System.Windows.Automation.Text.TextUnit> is not supported by the control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1efd6-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1efd6-112">See Also</span></span>  
 [<span data-ttu-id="1efd6-113">UI Otomasyon textpattern öğesine genel bakış</span><span class="sxs-lookup"><span data-stu-id="1efd6-113">UI Automation TextPattern Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-textpattern-overview.md)  
 [<span data-ttu-id="1efd6-114">UI Otomasyonu kullanarak metin kutusuna içerik ekleme</span><span class="sxs-lookup"><span data-stu-id="1efd6-114">Add Content to a Text Box Using UI Automation</span></span>](../../../docs/framework/ui-automation/add-content-to-a-text-box-using-ui-automation.md)  
 [<span data-ttu-id="1efd6-115">UI Otomasyonu kullanarak metin bulma ve vurgulama</span><span class="sxs-lookup"><span data-stu-id="1efd6-115">Find and Highlight Text Using UI Automation</span></span>](../../../docs/framework/ui-automation/find-and-highlight-text-using-ui-automation.md)  
 [<span data-ttu-id="1efd6-116">UI Otomasyon denetim düzenlerine genel bakış</span><span class="sxs-lookup"><span data-stu-id="1efd6-116">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="1efd6-117">İstemciler için UI Otomasyon denetim düzenleri</span><span class="sxs-lookup"><span data-stu-id="1efd6-117">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
