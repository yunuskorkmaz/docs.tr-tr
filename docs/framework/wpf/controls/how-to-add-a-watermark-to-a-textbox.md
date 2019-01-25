---
title: "Nasıl yapılır: TextBox'a Filigran Ekleme"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- displaying a background image inside a text box to aid user input [WPF]
- aid usability of a TextBox using a background image [WPF]
ms.assetid: df89bdd8-a0fb-45e0-b312-dd53332d01a8
ms.openlocfilehash: 1ab8c0f9274f4d461c9c2be04ec0aaca5e753c7d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54531138"
---
# <a name="how-to-add-a-watermark-to-a-textbox"></a><span data-ttu-id="6e4b3-102">Nasıl yapılır: TextBox'a Filigran Ekleme</span><span class="sxs-lookup"><span data-stu-id="6e4b3-102">How to: Add a Watermark to a TextBox</span></span>
<span data-ttu-id="6e4b3-103">Aşağıdaki örnek ın kullanılabilirliğine yardımcı olma gösterilmiştir bir <xref:System.Windows.Controls.TextBox> açıklayıcı arka plan görüntüsü içinde görüntüleyerek <xref:System.Windows.Controls.TextBox> metin kullanıcı girişlerinin kadar bu noktada görüntü kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="6e4b3-103">The following example shows how to aid usability of a <xref:System.Windows.Controls.TextBox> by displaying an explanatory background image inside of the <xref:System.Windows.Controls.TextBox> until the user inputs text, at which point the image is removed.</span></span> <span data-ttu-id="6e4b3-104">Ayrıca, kullanıcının kendi giriş kaldırırsa arka plan resmini yeniden geri yüklenir.</span><span class="sxs-lookup"><span data-stu-id="6e4b3-104">In addition, the background image is restored again if the user removes their input.</span></span> <span data-ttu-id="6e4b3-105">Aşağıdaki resme bakın.</span><span class="sxs-lookup"><span data-stu-id="6e4b3-105">See illustration below.</span></span>  
  
 <span data-ttu-id="6e4b3-106">![TextBox ile arka plan görüntüsü](../../../../docs/framework/wpf/controls/media/editing-textbox-using-background-image.png "Editing_TextBox_using_background_image")</span><span class="sxs-lookup"><span data-stu-id="6e4b3-106">![A TextBox with a background image](../../../../docs/framework/wpf/controls/media/editing-textbox-using-background-image.png "Editing_TextBox_using_background_image")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6e4b3-107">Arka plan görüntüsü yerine sonra yalnızca düzenleme Bu örnekte kullanılan nedeni <xref:System.Windows.Controls.TextBox.Text%2A> özelliği <xref:System.Windows.Controls.TextBox>, olan bir arka plan görüntüsü ile veri bağlaması müdahale etmez.</span><span class="sxs-lookup"><span data-stu-id="6e4b3-107">The reason a background image is used in this example rather then simply manipulating the <xref:System.Windows.Controls.TextBox.Text%2A> property of <xref:System.Windows.Controls.TextBox>, is that a background image will not interfere with data binding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e4b3-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="6e4b3-108">Example</span></span>  
 [!code-xaml[TextBoxMiscSnippets_snip#TextBoxBackgroundExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/textbox_with_background_image.xaml#textboxbackgroundexamplewholepage)]  
  
 [!code-csharp[TextBoxMiscSnippets_snip#TextBoxBackgroundCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/textbox_with_background_image.xaml.cs#textboxbackgroundcodeexamplewholepage)]
 [!code-vb[TextBoxMiscSnippets_snip#TextBoxBackgroundCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/visualbasic/textbox_with_background_image.xaml.vb#textboxbackgroundcodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="6e4b3-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6e4b3-109">See also</span></span>
- [<span data-ttu-id="6e4b3-110">TextBox Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="6e4b3-110">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)
- [<span data-ttu-id="6e4b3-111">RichTextBox Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="6e4b3-111">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
