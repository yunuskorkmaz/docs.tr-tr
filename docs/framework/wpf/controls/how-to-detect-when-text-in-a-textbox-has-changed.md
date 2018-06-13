---
title: 'Nasıl yapılır: TextBox İçindeki Metin Değiştirildiğinde Algılama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TextBox control [WPF], detecting text change
- text change [WPF], detecting
- detecting text change [WPF]
ms.assetid: 1c39ee14-e37f-49fb-a0d1-a9824ca13584
ms.openlocfilehash: 1befd18220488334319a55bce2ce602aef20d3d6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33552958"
---
# <a name="how-to-detect-when-text-in-a-textbox-has-changed"></a><span data-ttu-id="2743a-102">Nasıl yapılır: TextBox İçindeki Metin Değiştirildiğinde Algılama</span><span class="sxs-lookup"><span data-stu-id="2743a-102">How to: Detect When Text in a TextBox Has Changed</span></span>
<span data-ttu-id="2743a-103">Bu örnek kullanmanın tek yolu gösterir <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> bir yöntem yürütülmeye olay her metinde bir <xref:System.Windows.Controls.TextBox> denetim değişti.</span><span class="sxs-lookup"><span data-stu-id="2743a-103">This example shows one way to use the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event to execute a method whenever the text in a <xref:System.Windows.Controls.TextBox> control has changed.</span></span>  
  
 <span data-ttu-id="2743a-104">Arka plan kodu sınıfında [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] içeren <xref:System.Windows.Controls.TextBox> değişiklikler için izlemek istediğiniz denetimi Ekle olduğunda çağrılacak bir yöntem <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> olay etkinleşir.</span><span class="sxs-lookup"><span data-stu-id="2743a-104">In the code-behind class for the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] that contains the <xref:System.Windows.Controls.TextBox> control that you want to monitor for changes, insert a method to call whenever the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event fires.</span></span>  <span data-ttu-id="2743a-105">Bu yöntem tarafından beklenenle eşleşen bir imzaya sahip olmalıdır <xref:System.Windows.Controls.TextChangedEventHandler> temsilci.</span><span class="sxs-lookup"><span data-stu-id="2743a-105">This method must have a signature that matches what is expected by the <xref:System.Windows.Controls.TextChangedEventHandler> delegate.</span></span>  
  
 <span data-ttu-id="2743a-106">Olay işleyicisi çağrılır her içeriğini <xref:System.Windows.Controls.TextBox> denetim değiştirilirse, bir kullanıcı veya program aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="2743a-106">The event handler is called whenever the contents of the <xref:System.Windows.Controls.TextBox> control are changed, either by a user or programmatically.</span></span>  
  
 <span data-ttu-id="2743a-107">**Not:** bu olay tetiklenen <xref:System.Windows.Controls.TextBox> denetim oluşturulur ve başlangıçta metin ile doldurulur.</span><span class="sxs-lookup"><span data-stu-id="2743a-107">**Note:** This event fires when the <xref:System.Windows.Controls.TextBox> control is created and initially populated with text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2743a-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="2743a-108">Example</span></span>  
 <span data-ttu-id="2743a-109">İçinde [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] tanımlayan, <xref:System.Windows.Controls.TextBox> denetlemek, belirtin <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> özniteliği olay işleyicisi yöntem adıyla eşleşen bir değere sahip.</span><span class="sxs-lookup"><span data-stu-id="2743a-109">In the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] that defines your <xref:System.Windows.Controls.TextBox> control, specify the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> attribute with a value that matches the event handler method name.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_TextChangedXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textchangedxaml)]  
  
## <a name="example"></a><span data-ttu-id="2743a-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="2743a-110">Example</span></span>  
 <span data-ttu-id="2743a-111">Arka plan kodu sınıfında [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] içeren <xref:System.Windows.Controls.TextBox> değişiklikler için izlemek istediğiniz denetimi Ekle olduğunda çağrılacak bir yöntem <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> olay etkinleşir.</span><span class="sxs-lookup"><span data-stu-id="2743a-111">In the code-behind class for the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] that contains the <xref:System.Windows.Controls.TextBox> control that you want to monitor for changes, insert a method to call whenever the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event fires.</span></span>  <span data-ttu-id="2743a-112">Bu yöntem tarafından beklenenle eşleşen bir imzaya sahip olmalıdır <xref:System.Windows.Controls.TextChangedEventHandler> temsilci.</span><span class="sxs-lookup"><span data-stu-id="2743a-112">This method must have a signature that matches what is expected by the <xref:System.Windows.Controls.TextChangedEventHandler> delegate.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_TextChangedEventHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textchangedeventhandler)]
 [!code-vb[TextBox_MiscCode#_TextChangedEventHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textchangedeventhandler)]  
  
 <span data-ttu-id="2743a-113">Olay işleyicisi çağrılır her içeriğini <xref:System.Windows.Controls.TextBox> denetim değiştirilirse, bir kullanıcı veya program aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="2743a-113">The event handler is called whenever the contents of the <xref:System.Windows.Controls.TextBox> control are changed, either by a user or programmatically.</span></span>  
  
 <span data-ttu-id="2743a-114">**Not:** bu olay tetiklenen <xref:System.Windows.Controls.TextBox> denetim oluşturulur ve başlangıçta metin ile doldurulur.</span><span class="sxs-lookup"><span data-stu-id="2743a-114">**Note:** This event fires when the <xref:System.Windows.Controls.TextBox> control is created and initially populated with text.</span></span>  
  
 <span data-ttu-id="2743a-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2743a-115">Comments</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2743a-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2743a-116">See Also</span></span>  
 <xref:System.Windows.Controls.TextChangedEventArgs>  
 [<span data-ttu-id="2743a-117">TextBox Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="2743a-117">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [<span data-ttu-id="2743a-118">RichTextBox Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="2743a-118">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
