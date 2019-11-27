---
title: UI Otomasyonu Kullanarak Metin Kutusuna İçerik Ekleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adding content to text boxes
- text boxes, adding content
- UI Automation, adding content to text boxes
ms.assetid: 8bdd1a73-1ecb-4a05-a891-a7827ebb767f
ms.openlocfilehash: 71385690c01d261b4ff1b495674bab377232e81d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447255"
---
# <a name="add-content-to-a-text-box-using-ui-automation"></a><span data-ttu-id="6f3b2-102">UI Otomasyonu Kullanarak Metin Kutusuna İçerik Ekleme</span><span class="sxs-lookup"><span data-stu-id="6f3b2-102">Add Content to a Text Box Using UI Automation</span></span>
> [!NOTE]
> <span data-ttu-id="6f3b2-103">Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="6f3b2-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="6f3b2-104">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="6f3b2-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="6f3b2-105">Bu konu, tek satırlık bir metin kutusuna metin eklemek için [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] kullanmayı gösteren örnek kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="6f3b2-105">This topic contains example code that demonstrates how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to insert text into a single-line text box.</span></span> <span data-ttu-id="6f3b2-106">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] geçerli olmayan çok satırlı ve zengin metin denetimleri için alternatif bir yöntem sağlanır.</span><span class="sxs-lookup"><span data-stu-id="6f3b2-106">An alternate method is provided for multi-line and rich text controls where [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] is not applicable.</span></span> <span data-ttu-id="6f3b2-107">Örnek, karşılaştırma amacıyla aynı zamanda Win32 yöntemlerinin aynı sonuçları başarmak için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6f3b2-107">For comparison purposes, the example also demonstrates how to use Win32 methods to accomplish the same results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f3b2-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="6f3b2-108">Example</span></span>  
 <span data-ttu-id="6f3b2-109">Aşağıdaki örnek, bir hedef uygulamadaki metin denetimleri dizisi boyunca adımlar halinde yapılır.</span><span class="sxs-lookup"><span data-stu-id="6f3b2-109">The following example steps through a sequence of text controls in a target application.</span></span> <span data-ttu-id="6f3b2-110">Her metin denetimi, <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> yöntemi kullanılarak <xref:System.Windows.Automation.ValuePattern> nesnenin elde edilebilir olup olmadığını görmek için test edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6f3b2-110">Each text control is tested to see if a <xref:System.Windows.Automation.ValuePattern> object can be obtained from it using the <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> method.</span></span> <span data-ttu-id="6f3b2-111">Metin denetimi <xref:System.Windows.Automation.ValuePattern>destekliyorsa, metin denetimine Kullanıcı tanımlı bir dize eklemek için <xref:System.Windows.Automation.ValuePattern.SetValue%2A> yöntemi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6f3b2-111">If the text control does support <xref:System.Windows.Automation.ValuePattern>, the <xref:System.Windows.Automation.ValuePattern.SetValue%2A> method is used to insert a user-defined string into the text control.</span></span> <span data-ttu-id="6f3b2-112">Aksi takdirde <xref:System.Windows.Forms.SendKeys.SendWait%2A?displayProperty=nameWithType> yöntemi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6f3b2-112">Otherwise, the <xref:System.Windows.Forms.SendKeys.SendWait%2A?displayProperty=nameWithType> method is used.</span></span>  
  
 [!code-csharp[InsertText#InsertText](../../../samples/snippets/csharp/VS_Snippets_Wpf/InsertText/CSharp/Window1.xaml.cs#inserttext)]
 [!code-vb[InsertText#InsertText](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InsertText/VisualBasic/Window1.xaml.vb#inserttext)]  
  
## <a name="see-also"></a><span data-ttu-id="6f3b2-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f3b2-113">See also</span></span>

- <span data-ttu-id="6f3b2-114">[TextModel metin ekleme örneği](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771478(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="6f3b2-114">[TextPattern Insert Text Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771478(v=vs.90))</span></span>
