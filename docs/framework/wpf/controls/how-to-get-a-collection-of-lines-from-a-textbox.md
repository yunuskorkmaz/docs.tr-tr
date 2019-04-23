---
title: "Nasıl yapılır: TextBox'tan Satır Koleksiyonu Alma"
ms.date: 03/30/2017
helpviewer_keywords:
- lines [WPF], getting collection of
- TextBox control [WPF], getting collection of lines
ms.assetid: a12f529d-b926-47f6-92bf-cad5f17b532a
ms.openlocfilehash: b7b2f1c2e071388635fb50b1e3573fd7f44334dd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59224643"
---
# <a name="how-to-get-a-collection-of-lines-from-a-textbox"></a><span data-ttu-id="273ac-102">Nasıl yapılır: TextBox'tan Satır Koleksiyonu Alma</span><span class="sxs-lookup"><span data-stu-id="273ac-102">How to: Get a Collection of Lines from a TextBox</span></span>
<span data-ttu-id="273ac-103">Bu örnekte, metni satır koleksiyonu alma işlemi gösterilmektedir bir <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="273ac-103">This example shows how to get a collection of lines of text from a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="273ac-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="273ac-104">Example</span></span>  
 <span data-ttu-id="273ac-105">Aşağıdaki örnek, alan basit bir yöntemi gösterir. bir <xref:System.Windows.Controls.TextBox> döndürür ve bağımsız değişkeni olarak bir <xref:System.Collections.Specialized.StringCollection> metin satırlarını içeren **TextBox**.</span><span class="sxs-lookup"><span data-stu-id="273ac-105">The following example shows a simple method that takes a <xref:System.Windows.Controls.TextBox> as the argument, and returns a <xref:System.Collections.Specialized.StringCollection> containing the lines of text in the **TextBox**.</span></span>  <span data-ttu-id="273ac-106"><xref:System.Windows.Controls.TextBox.LineCount%2A> Kaç satır şu anda kullanımda olduğunu belirlemek için kullanılan özellik **TextBox**ve <xref:System.Windows.Controls.TextBox.GetLineText%2A> yöntemi ardından her satırı ayıklamak ve koleksiyona satır eklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="273ac-106">The <xref:System.Windows.Controls.TextBox.LineCount%2A> property is used to determine how many lines are currently in the **TextBox**, and the <xref:System.Windows.Controls.TextBox.GetLineText%2A> method is then used to extract each line and add it to the collection of lines.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_TextBox_GetLines](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textbox_getlines)]  
  
## <a name="see-also"></a><span data-ttu-id="273ac-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="273ac-107">See also</span></span>

- [<span data-ttu-id="273ac-108">TextBox Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="273ac-108">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="273ac-109">RichTextBox Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="273ac-109">RichTextBox Overview</span></span>](richtextbox-overview.md)
