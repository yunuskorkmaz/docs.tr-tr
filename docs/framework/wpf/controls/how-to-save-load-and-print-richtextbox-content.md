---
title: 'Nasıl yapılır: RichTextBox İçeriğini Kaydetme, Yükleme ve Yazdırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- saving RichTextBox controls [WPF]
- printing RichTextBox controls [WPF]
- loading RichTextBox controls [WPF]
- RichTextBox control [WPF], saving
- RichTextBox control [WPF], printing
- RichTextBox control [WPF], loading
ms.assetid: ffb113d3-c68a-47ca-8ac0-882283f38326
ms.openlocfilehash: c1f5b1d33518d19f6c0976e883500d27cf9adbec
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54562134"
---
# <a name="how-to-save-load-and-print-richtextbox-content"></a><span data-ttu-id="25bfa-102">Nasıl yapılır: RichTextBox İçeriğini Kaydetme, Yükleme ve Yazdırma</span><span class="sxs-lookup"><span data-stu-id="25bfa-102">How to: Save, Load, and Print RichTextBox Content</span></span>
<span data-ttu-id="25bfa-103">Aşağıdaki örnek nasıl kaydedileceğini içeriğini gösterir bir <xref:System.Windows.Controls.RichTextBox> , içerik tekrar içine bir dosyaya yük <xref:System.Windows.Controls.RichTextBox>ve içeriği yazdır.</span><span class="sxs-lookup"><span data-stu-id="25bfa-103">The following example shows how to save content of a <xref:System.Windows.Controls.RichTextBox> to a file, load that content back into the <xref:System.Windows.Controls.RichTextBox>, and print the contents.</span></span>  
  
## <a name="example"></a><span data-ttu-id="25bfa-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="25bfa-104">Example</span></span>  
 <span data-ttu-id="25bfa-105">Bu örnek için biçimlendirme aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="25bfa-105">Below is the markup for the example.</span></span>  
  
 [!code-xaml[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/SaveLoadPrintRTB.xaml#saveloadprintrtbexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="25bfa-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="25bfa-106">Example</span></span>  
 <span data-ttu-id="25bfa-107">Arka plan kod örnek için aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="25bfa-107">Below is the code behind for the example.</span></span>  
  
 [!code-csharp[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/SaveLoadPrintRTB.xaml.cs#saveloadprintrtbcodeexamplewholepage)]
 [!code-vb[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/VisualBasic/SaveLoadPrintRTB.xaml.vb#saveloadprintrtbcodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="25bfa-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="25bfa-108">See also</span></span>
- [<span data-ttu-id="25bfa-109">RichTextBox Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="25bfa-109">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
- [<span data-ttu-id="25bfa-110">TextBox Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="25bfa-110">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)
