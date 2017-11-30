---
title: "Nasıl yapılır: RichTextBox İçeriğini Kaydetme, Yükleme ve Yazdırma"
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
- saving RichTextBox controls [WPF]
- printing RichTextBox controls [WPF]
- loading RichTextBox controls [WPF]
- RichTextBox control [WPF], saving
- RichTextBox control [WPF], printing
- RichTextBox control [WPF], loading
ms.assetid: ffb113d3-c68a-47ca-8ac0-882283f38326
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ca969848ae82d567642cd0f4174c52ebc24ef5d0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-save-load-and-print-richtextbox-content"></a><span data-ttu-id="07801-102">Nasıl yapılır: RichTextBox İçeriğini Kaydetme, Yükleme ve Yazdırma</span><span class="sxs-lookup"><span data-stu-id="07801-102">How to: Save, Load, and Print RichTextBox Content</span></span>
<span data-ttu-id="07801-103">Aşağıdaki örnek, içeriği kaydetmek gösterilmiştir bir <xref:System.Windows.Controls.RichTextBox> bir dosyaya, içerik tekrar içine yük <xref:System.Windows.Controls.RichTextBox>ve içindekileri yazdırın.</span><span class="sxs-lookup"><span data-stu-id="07801-103">The following example shows how to save content of a <xref:System.Windows.Controls.RichTextBox> to a file, load that content back into the <xref:System.Windows.Controls.RichTextBox>, and print the contents.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07801-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="07801-104">Example</span></span>  
 <span data-ttu-id="07801-105">Bu örnek için biçimlendirme aşağıdadır.</span><span class="sxs-lookup"><span data-stu-id="07801-105">Below is the markup for the example.</span></span>  
  
 [!code-xaml[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/SaveLoadPrintRTB.xaml#saveloadprintrtbexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="07801-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="07801-106">Example</span></span>  
 <span data-ttu-id="07801-107">Arka plan kod örneğin aşağıdadır.</span><span class="sxs-lookup"><span data-stu-id="07801-107">Below is the code behind for the example.</span></span>  
  
 [!code-csharp[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/SaveLoadPrintRTB.xaml.cs#saveloadprintrtbcodeexamplewholepage)]
 [!code-vb[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/VisualBasic/SaveLoadPrintRTB.xaml.vb#saveloadprintrtbcodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="07801-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="07801-108">See Also</span></span>  
 [<span data-ttu-id="07801-109">RichTextBox Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="07801-109">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)  
 [<span data-ttu-id="07801-110">TextBox genel bakış</span><span class="sxs-lookup"><span data-stu-id="07801-110">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)
