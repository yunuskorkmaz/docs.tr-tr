---
title: "Nasıl yapılır: RichTextBox'dan Metin İçeriği Ayıklama"
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
- text content [WPF], extracting
- RichTextBox control [WPF], extracting text content
- content [WPF], extracting
- extracting text content [WPF]
ms.assetid: f13c093f-1a05-45b3-ac8f-c9ea5e4a11c5
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 36a34e8f5a96f8b45a6c830ec3c1edeea816bd3b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-extract-the-text-content-from-a-richtextbox"></a><span data-ttu-id="9c53b-102">Nasıl yapılır: RichTextBox'dan Metin İçeriği Ayıklama</span><span class="sxs-lookup"><span data-stu-id="9c53b-102">How to: Extract the Text Content from a RichTextBox</span></span>
<span data-ttu-id="9c53b-103">Bu örnek, içeriği ayıklamak gösterilmiştir bir <xref:System.Windows.Controls.RichTextBox> düz metin olarak.</span><span class="sxs-lookup"><span data-stu-id="9c53b-103">This example shows how to extract the contents of a <xref:System.Windows.Controls.RichTextBox> as plain text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c53b-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="9c53b-104">Example</span></span>  
 <span data-ttu-id="9c53b-105">Aşağıdaki [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] kodu tanımlayan bir adlandırılmış <xref:System.Windows.Controls.RichTextBox> denetim basit içeriğe sahip.</span><span class="sxs-lookup"><span data-stu-id="9c53b-105">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] code describes a named <xref:System.Windows.Controls.RichTextBox> control with simple content.</span></span>  
  
 [!code-xaml[RichTextBoxSnippets#_RTB_XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxSnippets/CSharp/Window1.xaml#_rtb_xaml)]  
  
## <a name="example"></a><span data-ttu-id="9c53b-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="9c53b-106">Example</span></span>  
 <span data-ttu-id="9c53b-107">Aşağıdaki kodu alan bir yöntem uygulayan bir <xref:System.Windows.Controls.RichTextBox> bir bağımsız değişken olarak ve düz metin içeriğini temsil eden bir dize döndürür <xref:System.Windows.Controls.RichTextBox>.</span><span class="sxs-lookup"><span data-stu-id="9c53b-107">The following code implements a method that takes a <xref:System.Windows.Controls.RichTextBox> as an argument, and returns a string representing the plain text contents of the <xref:System.Windows.Controls.RichTextBox>.</span></span>  
  
 <span data-ttu-id="9c53b-108">Yöntem yeni bir oluşturur <xref:System.Windows.Documents.TextRange> içeriğinden <xref:System.Windows.Controls.RichTextBox>kullanarak <xref:System.Windows.Documents.FlowDocument.ContentStart%2A> ve <xref:System.Windows.Documents.FlowDocument.ContentEnd%2A> ayıklanacak içeriğin aralığını belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="9c53b-108">The method creates a new <xref:System.Windows.Documents.TextRange> from the contents of the <xref:System.Windows.Controls.RichTextBox>, using the <xref:System.Windows.Documents.FlowDocument.ContentStart%2A> and <xref:System.Windows.Documents.FlowDocument.ContentEnd%2A> to indicate the range of the contents to extract.</span></span>  <span data-ttu-id="9c53b-109"><xref:System.Windows.Documents.FlowDocument.ContentStart%2A>ve <xref:System.Windows.Documents.FlowDocument.ContentEnd%2A> özellikler her bir <xref:System.Windows.Documents.TextPointer>ve içeriğini temsil eden arka plandaki FlowDocument üzerinde erişilebilir <xref:System.Windows.Controls.RichTextBox>.</span><span class="sxs-lookup"><span data-stu-id="9c53b-109"><xref:System.Windows.Documents.FlowDocument.ContentStart%2A> and <xref:System.Windows.Documents.FlowDocument.ContentEnd%2A> properties each return a <xref:System.Windows.Documents.TextPointer>, and are accessible on the underlying FlowDocument that represents the contents of the <xref:System.Windows.Controls.RichTextBox>.</span></span>  <span data-ttu-id="9c53b-110"><xref:System.Windows.Documents.TextRange>düz metin bölümlerini döndüren bir metin özelliğini sağlar <xref:System.Windows.Documents.TextRange> dize olarak.</span><span class="sxs-lookup"><span data-stu-id="9c53b-110"><xref:System.Windows.Documents.TextRange> provides a Text property, which returns the plain text portions of the <xref:System.Windows.Documents.TextRange> as a string.</span></span>  
  
 [!code-csharp[RichTextBoxSnippets#_RTB_StringFrom](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxSnippets/CSharp/Window1.xaml.cs#_rtb_stringfrom)]
 [!code-vb[RichTextBoxSnippets#_RTB_StringFrom](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxSnippets/visualbasic/window1.xaml.vb#_rtb_stringfrom)]  
  
## <a name="see-also"></a><span data-ttu-id="9c53b-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9c53b-111">See Also</span></span>  
 [<span data-ttu-id="9c53b-112">RichTextBox Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9c53b-112">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)  
 [<span data-ttu-id="9c53b-113">TextBox Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9c53b-113">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)
