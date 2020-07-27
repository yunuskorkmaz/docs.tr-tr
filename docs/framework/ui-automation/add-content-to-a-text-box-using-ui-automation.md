---
title: UI Otomasyonu Kullanarak Metin Kutusuna İçerik Ekleme
description: .NET 'te Microsoft UI Otomasyonu 'Nu kullanarak tek satırlık bir metin kutusuna içerik ekleme örneğine örnek olarak bakın.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adding content to text boxes
- text boxes, adding content
- UI Automation, adding content to text boxes
ms.assetid: 8bdd1a73-1ecb-4a05-a891-a7827ebb767f
ms.openlocfilehash: 4136d460de7091a515580cade16f06e54699727a
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166919"
---
# <a name="add-content-to-a-text-box-using-ui-automation"></a><span data-ttu-id="952f9-103">UI Otomasyonu Kullanarak Metin Kutusuna İçerik Ekleme</span><span class="sxs-lookup"><span data-stu-id="952f9-103">Add Content to a Text Box Using UI Automation</span></span>
> [!NOTE]
> <span data-ttu-id="952f9-104">Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> .</span><span class="sxs-lookup"><span data-stu-id="952f9-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="952f9-105">Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="952f9-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="952f9-106">Bu konu başlığı altında, [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] tek satırlık bir metin kutusuna metin eklemek için kullanmayı gösteren örnek kod yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="952f9-106">This topic contains example code that demonstrates how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to insert text into a single-line text box.</span></span> <span data-ttu-id="952f9-107">Uygun olmayan çok satırlı ve zengin metin denetimleri için alternatif bir yöntem sağlanır [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="952f9-107">An alternate method is provided for multi-line and rich text controls where [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] is not applicable.</span></span> <span data-ttu-id="952f9-108">Örnek, karşılaştırma amacıyla aynı zamanda Win32 yöntemlerinin aynı sonuçları başarmak için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="952f9-108">For comparison purposes, the example also demonstrates how to use Win32 methods to accomplish the same results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="952f9-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="952f9-109">Example</span></span>  
 <span data-ttu-id="952f9-110">Aşağıdaki örnek, bir hedef uygulamadaki metin denetimleri dizisi boyunca adımlar halinde yapılır.</span><span class="sxs-lookup"><span data-stu-id="952f9-110">The following example steps through a sequence of text controls in a target application.</span></span> <span data-ttu-id="952f9-111">Her metin denetimi <xref:System.Windows.Automation.ValuePattern> , yöntemi kullanılarak bir nesnenin elde edilebilir olup olmadığını görmek için test edilmiştir <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> .</span><span class="sxs-lookup"><span data-stu-id="952f9-111">Each text control is tested to see if a <xref:System.Windows.Automation.ValuePattern> object can be obtained from it using the <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> method.</span></span> <span data-ttu-id="952f9-112">Metin denetimi destekliyorsa <xref:System.Windows.Automation.ValuePattern> , <xref:System.Windows.Automation.ValuePattern.SetValue%2A> yöntemi metin denetimine Kullanıcı tanımlı bir dize eklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="952f9-112">If the text control does support <xref:System.Windows.Automation.ValuePattern>, the <xref:System.Windows.Automation.ValuePattern.SetValue%2A> method is used to insert a user-defined string into the text control.</span></span> <span data-ttu-id="952f9-113">Aksi takdirde, <xref:System.Windows.Forms.SendKeys.SendWait%2A?displayProperty=nameWithType> yöntemi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="952f9-113">Otherwise, the <xref:System.Windows.Forms.SendKeys.SendWait%2A?displayProperty=nameWithType> method is used.</span></span>  
  
 [!code-csharp[InsertText#InsertText](../../../samples/snippets/csharp/VS_Snippets_Wpf/InsertText/CSharp/Window1.xaml.cs#inserttext)]
 [!code-vb[InsertText#InsertText](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InsertText/VisualBasic/Window1.xaml.vb#inserttext)]  
  
## <a name="see-also"></a><span data-ttu-id="952f9-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="952f9-114">See also</span></span>

- <span data-ttu-id="952f9-115">[TextModel metin ekleme örneği](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771478(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="952f9-115">[TextPattern Insert Text Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771478(v=vs.90))</span></span>
