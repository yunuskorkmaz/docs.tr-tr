---
title: "Nasıl yapılır: RichTextBox Denetimine Bırakılan bir Dosyayı Açma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drag-and-drop [WPF], RichTextBox
- RichTextBox [WPF], drag-and-drop
- drag-and-drop [WPF], open a dropped file
ms.assetid: 6bb8bb54-f576-41db-a9a7-24102ddeb490
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f65ecaf9c6ef34176967e1ebf9134ceee195036b
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-open-a-file-that-is-dropped-on-a-richtextbox-control"></a><span data-ttu-id="81846-102">Nasıl yapılır: RichTextBox Denetimine Bırakılan bir Dosyayı Açma</span><span class="sxs-lookup"><span data-stu-id="81846-102">How to: Open a File That is Dropped on a RichTextBox Control</span></span>
<span data-ttu-id="81846-103">İçinde [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.RichTextBox>, ve <xref:System.Windows.Documents.FlowDocument> tüm denetimleriniz yerleşik bir Sürükle ve bırak işlevi.</span><span class="sxs-lookup"><span data-stu-id="81846-103">In [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], the <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.RichTextBox>, and <xref:System.Windows.Documents.FlowDocument> controls all have built-in drag-and-drop functionality.</span></span> <span data-ttu-id="81846-104">Sürükle ve bırak metin içinde ve arasında denetimleri yerleşik işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="81846-104">The built-in functionality enables drag-and-drop of text within and between the controls.</span></span> <span data-ttu-id="81846-105">Ancak, dosyanın denetimindeki bırakarak bir dosyanın açılması etkinleştirmez.</span><span class="sxs-lookup"><span data-stu-id="81846-105">However, it does not enable opening a file by dropping the file on the control.</span></span> <span data-ttu-id="81846-106">Bu denetimler, sürükle ve bırak olayları da işlenmiş olarak işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="81846-106">These controls also mark the drag-and-drop events as handled.</span></span> <span data-ttu-id="81846-107">Sonuç olarak, varsayılan olarak, bırakılan dosyaları açmaya işlevselliği sağlamak için kendi olay işleyicileri ekleyemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="81846-107">As a result, by default, you cannot add your own event handlers to provide functionality to open dropped files.</span></span>  
  
 <span data-ttu-id="81846-108">Bu denetimlerin sürükle ve bırak olayları için ek işleme eklemek için kullanın <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29> sürükle ve bırak olayları için olay işleyicileri ekleme yöntemi.</span><span class="sxs-lookup"><span data-stu-id="81846-108">To add additional handling for drag-and-drop events in these controls, use the <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29> method to add your event handlers for the drag-and-drop events.</span></span> <span data-ttu-id="81846-109">Ayarlama `handledEventsToo` parametresi `true` zaten olay yol boyunca başka bir öğe tarafından işlenmiş olarak işaretlenmiş yönlendirilmiş bir olay için çağrılan belirtilen işleyici sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="81846-109">Set the `handledEventsToo` parameter to `true` to have the specified handler be invoked for a routed event that has already been marked as handled by another element along the event route.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="81846-110">Yerleşik sürükle ve bırak işlevselliğini değiştirebilirsiniz <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.RichTextBox>, ve <xref:System.Windows.Documents.FlowDocument> sürükle ve bırak olayları önizleme sürümleri işleme ve önizleme olayları işlenmiş olarak işaretleme.</span><span class="sxs-lookup"><span data-stu-id="81846-110">You can replace the built-in drag-and-drop functionality of <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.RichTextBox>, and <xref:System.Windows.Documents.FlowDocument> by handling the preview versions of the drag-and-drop events and marking the preview events as handled.</span></span> <span data-ttu-id="81846-111">Ancak, bu yerleşik bir Sürükle ve bırak işlevi devre dışı bırakır ve önerilmez.</span><span class="sxs-lookup"><span data-stu-id="81846-111">However, this will disable the built-in drag-and-drop functionality, and is not recommended.</span></span>  
  
## <a name="example"></a><span data-ttu-id="81846-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="81846-112">Example</span></span>  
 <span data-ttu-id="81846-113">Aşağıdaki örnek işleyicileri eklemek gösterilmiştir <xref:System.Windows.DragDrop.DragOver> ve <xref:System.Windows.DragDrop.Drop> olaylarına bir <xref:System.Windows.Controls.RichTextBox>.</span><span class="sxs-lookup"><span data-stu-id="81846-113">The following example demonstrates how to add handlers for the <xref:System.Windows.DragDrop.DragOver> and <xref:System.Windows.DragDrop.Drop> events on a <xref:System.Windows.Controls.RichTextBox>.</span></span> <span data-ttu-id="81846-114">Bu örnekte <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29> yöntemi ve kümelerini `handledEventsToo` parametresi `true` böylece olay işleyicilerini rağmen çağrılacak <xref:System.Windows.Controls.RichTextBox> bu olayları işlenmiş olarak işaretler.</span><span class="sxs-lookup"><span data-stu-id="81846-114">This example uses the <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29> method and sets the `handledEventsToo` parameter to `true` so that the events handlers will be invoked even though the <xref:System.Windows.Controls.RichTextBox> marks these events as handled.</span></span> <span data-ttu-id="81846-115">Olay işleyicileri kodunda üzerinde bırakılan bir metin dosyasını açmak için işlevsellik ekler <xref:System.Windows.Controls.RichTextBox>.</span><span class="sxs-lookup"><span data-stu-id="81846-115">The code in the event handlers adds functionality to open a text file that is dropped on the <xref:System.Windows.Controls.RichTextBox>.</span></span>  
  
 <span data-ttu-id="81846-116">Bu örneği test etmek için bir metin dosyası veya zengin metin biçimi (RTF) dosyası için Windows Gezgini'nden sürükleyin <xref:System.Windows.Controls.RichTextBox>.</span><span class="sxs-lookup"><span data-stu-id="81846-116">To test this example, drag a text file or a rich text format (RTF) file from Windows Explorer to the <xref:System.Windows.Controls.RichTextBox>.</span></span> <span data-ttu-id="81846-117">Dosya açılacak <xref:System.Windows.Controls.RichTextBox>.</span><span class="sxs-lookup"><span data-stu-id="81846-117">The file will be opened in the <xref:System.Windows.Controls.RichTextBox>.</span></span> <span data-ttu-id="81846-118">Bırakma önce SHIFT tuşuna basarsanız, dosyanın dosya düz metin olarak açılacak.</span><span class="sxs-lookup"><span data-stu-id="81846-118">If you press the SHIFT key before the dropping the file, the file will be opened as plain text.</span></span>  
  
 [!code-xaml[DragDropSnippets#RtbXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml#rtbxaml)]  
  
 [!code-csharp[DragDropSnippets#RtbHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#rtbhandlers)]
 [!code-vb[DragDropSnippets#RtbHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#rtbhandlers)]
