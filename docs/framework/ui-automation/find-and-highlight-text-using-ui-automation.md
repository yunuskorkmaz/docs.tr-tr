---
title: UI Otomasyonunu Kullanarak Metin Bulma ve Vurgulama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text, highlighting
- finding text
- text, finding
- UI automation, highlighting text
- UI automation, finding text
- highlighting text
ms.assetid: b77693f5-87bb-4b29-a297-05ff882e2044
ms.openlocfilehash: 0e5f856c69fab45a4c92e12746f357320d2e323c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435753"
---
# <a name="find-and-highlight-text-using-ui-automation"></a><span data-ttu-id="c5c33-102">UI Otomasyonunu Kullanarak Metin Bulma ve Vurgulama</span><span class="sxs-lookup"><span data-stu-id="c5c33-102">Find and Highlight Text Using UI Automation</span></span>
> [!NOTE]
> <span data-ttu-id="c5c33-103">Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="c5c33-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="c5c33-104">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="c5c33-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="c5c33-105">Bu konu başlığı altında, bir metin denetiminin içeriği içindeki her bir dizenin her oluşumunu, [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]kullanarak nasıl sıralı olarak arayacağını ve vurgulayabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="c5c33-105">This topic demonstrates how to sequentially search for and highlight each occurrence of a string within the content of a text control using [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)].</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5c33-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="c5c33-106">Example</span></span>  
 <span data-ttu-id="c5c33-107">Aşağıdaki örnek bir metin denetiminden bir <xref:System.Windows.Automation.TextPattern> nesnesi edinir.</span><span class="sxs-lookup"><span data-stu-id="c5c33-107">The following example obtains a <xref:System.Windows.Automation.TextPattern> object from a text control.</span></span> <span data-ttu-id="c5c33-108">Tüm belgenin metin içeriğini temsil eden bir <xref:System.Windows.Automation.Text.TextPatternRange> nesnesi daha sonra bu <xref:System.Windows.Automation.TextPattern><xref:System.Windows.Automation.TextPattern.DocumentRange%2A> özelliği kullanılarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c5c33-108">A <xref:System.Windows.Automation.Text.TextPatternRange> object, representing the textual content of the entire document, is then created using the <xref:System.Windows.Automation.TextPattern.DocumentRange%2A> property of this <xref:System.Windows.Automation.TextPattern>.</span></span> <span data-ttu-id="c5c33-109">Daha sonra sıralı arama ve vurgulama işlevselliği için iki ek <xref:System.Windows.Automation.Text.TextPatternRange> nesnesi oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c5c33-109">Two additional <xref:System.Windows.Automation.Text.TextPatternRange> objects are then created for the sequential search and highlight functionality.</span></span>  
  
[!code-csharp[FindText#StartApp](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#startapp)]
[!code-vb[FindText#StartApp](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#startapp)]  
[!code-csharp[FindText#FindTextProvider](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#findtextprovider)]
[!code-vb[FindText#FindTextProvider](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#findtextprovider)]  
[!code-csharp[FindText#SearchTarget](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#searchtarget)]
[!code-vb[FindText#SearchTarget](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#searchtarget)]  
  
## <a name="see-also"></a><span data-ttu-id="c5c33-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c5c33-110">See also</span></span>

- [<span data-ttu-id="c5c33-111">UI Otomasyonunu Kullanarak Metin Bulma ve Vurgulama</span><span class="sxs-lookup"><span data-stu-id="c5c33-111">Find and Highlight Text Using UI Automation</span></span>](find-and-highlight-text-using-ui-automation.md)
