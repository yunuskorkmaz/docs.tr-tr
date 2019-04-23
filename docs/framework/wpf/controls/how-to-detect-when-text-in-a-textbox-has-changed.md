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
ms.openlocfilehash: 1adadb0f071815930d34f40ddf244ffc8c19131b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59091154"
---
# <a name="how-to-detect-when-text-in-a-textbox-has-changed"></a><span data-ttu-id="9ad20-102">Nasıl yapılır: TextBox İçindeki Metin Değiştirildiğinde Algılama</span><span class="sxs-lookup"><span data-stu-id="9ad20-102">How to: Detect When Text in a TextBox Has Changed</span></span>
<span data-ttu-id="9ad20-103">Bu örnekte kullanılacak yollarından biri gösterilmektedir <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> bir yöntem yürütülmeye çalışıldı olay olduğunda metinde bir <xref:System.Windows.Controls.TextBox> denetim değişti.</span><span class="sxs-lookup"><span data-stu-id="9ad20-103">This example shows one way to use the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event to execute a method whenever the text in a <xref:System.Windows.Controls.TextBox> control has changed.</span></span>  
  
 <span data-ttu-id="9ad20-104">Arka plan kod sınıfında [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] içeren <xref:System.Windows.Controls.TextBox> değişiklikler için izlemek istediğiniz denetimi ekleme çağrılacak bir yöntem <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> olay harekete geçirilir.</span><span class="sxs-lookup"><span data-stu-id="9ad20-104">In the code-behind class for the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] that contains the <xref:System.Windows.Controls.TextBox> control that you want to monitor for changes, insert a method to call whenever the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event fires.</span></span>  <span data-ttu-id="9ad20-105">Bu yöntem tarafından beklenenle eşleşen bir imza içermelidir <xref:System.Windows.Controls.TextChangedEventHandler> temsilci.</span><span class="sxs-lookup"><span data-stu-id="9ad20-105">This method must have a signature that matches what is expected by the <xref:System.Windows.Controls.TextChangedEventHandler> delegate.</span></span>  
  
 <span data-ttu-id="9ad20-106">Olay işleyicisinde çağrılır her içeriğini <xref:System.Windows.Controls.TextBox> denetim değiştirilirse, bir kullanıcı veya program aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="9ad20-106">The event handler is called whenever the contents of the <xref:System.Windows.Controls.TextBox> control are changed, either by a user or programmatically.</span></span>  
  
 <span data-ttu-id="9ad20-107">**Not:** Bu olay tetiklenen <xref:System.Windows.Controls.TextBox> denetim oluşturulur ve başlangıçta metin ile doldurulur.</span><span class="sxs-lookup"><span data-stu-id="9ad20-107">**Note:** This event fires when the <xref:System.Windows.Controls.TextBox> control is created and initially populated with text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ad20-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="9ad20-108">Example</span></span>  
 <span data-ttu-id="9ad20-109">İçinde [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] tanımlayan, <xref:System.Windows.Controls.TextBox> belirtin, kontrolünde <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> olay işleyicisi yöntemi adıyla eşleşen bir değere sahip bir öznitelik.</span><span class="sxs-lookup"><span data-stu-id="9ad20-109">In the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] that defines your <xref:System.Windows.Controls.TextBox> control, specify the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> attribute with a value that matches the event handler method name.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_TextChangedXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textchangedxaml)]  
  
## <a name="example"></a><span data-ttu-id="9ad20-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="9ad20-110">Example</span></span>  
 <span data-ttu-id="9ad20-111">Arka plan kod sınıfında [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] içeren <xref:System.Windows.Controls.TextBox> değişiklikler için izlemek istediğiniz denetimi ekleme çağrılacak bir yöntem <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> olay harekete geçirilir.</span><span class="sxs-lookup"><span data-stu-id="9ad20-111">In the code-behind class for the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] that contains the <xref:System.Windows.Controls.TextBox> control that you want to monitor for changes, insert a method to call whenever the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event fires.</span></span>  <span data-ttu-id="9ad20-112">Bu yöntem tarafından beklenenle eşleşen bir imza içermelidir <xref:System.Windows.Controls.TextChangedEventHandler> temsilci.</span><span class="sxs-lookup"><span data-stu-id="9ad20-112">This method must have a signature that matches what is expected by the <xref:System.Windows.Controls.TextChangedEventHandler> delegate.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textchangedeventhandler)]
 [!code-vb[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textchangedeventhandler)]  
  
 <span data-ttu-id="9ad20-113">Olay işleyicisinde çağrılır her içeriğini <xref:System.Windows.Controls.TextBox> denetim değiştirilirse, bir kullanıcı veya program aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="9ad20-113">The event handler is called whenever the contents of the <xref:System.Windows.Controls.TextBox> control are changed, either by a user or programmatically.</span></span>  
  
 <span data-ttu-id="9ad20-114">**Not:** Bu olay tetiklenen <xref:System.Windows.Controls.TextBox> denetim oluşturulur ve başlangıçta metin ile doldurulur.</span><span class="sxs-lookup"><span data-stu-id="9ad20-114">**Note:** This event fires when the <xref:System.Windows.Controls.TextBox> control is created and initially populated with text.</span></span>  
  
 <span data-ttu-id="9ad20-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9ad20-115">Comments</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ad20-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9ad20-116">See also</span></span>

- <xref:System.Windows.Controls.TextChangedEventArgs>
- [<span data-ttu-id="9ad20-117">TextBox Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9ad20-117">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="9ad20-118">RichTextBox Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9ad20-118">RichTextBox Overview</span></span>](richtextbox-overview.md)
