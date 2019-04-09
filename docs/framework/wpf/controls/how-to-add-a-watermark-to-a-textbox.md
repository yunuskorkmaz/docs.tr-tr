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
ms.openlocfilehash: ef2536f03ba6ed08e27d2fcf30cd1f72df2cf460
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59142421"
---
# <a name="how-to-add-a-watermark-to-a-textbox"></a><span data-ttu-id="1d7cf-102">Nasıl yapılır: TextBox'a Filigran Ekleme</span><span class="sxs-lookup"><span data-stu-id="1d7cf-102">How to: Add a Watermark to a TextBox</span></span>
<span data-ttu-id="1d7cf-103">Aşağıdaki örnek ın kullanılabilirliğine yardımcı olma gösterilmiştir bir <xref:System.Windows.Controls.TextBox> açıklayıcı arka plan görüntüsü içinde görüntüleyerek <xref:System.Windows.Controls.TextBox> metin kullanıcı girişlerinin kadar bu noktada görüntü kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="1d7cf-103">The following example shows how to aid usability of a <xref:System.Windows.Controls.TextBox> by displaying an explanatory background image inside of the <xref:System.Windows.Controls.TextBox> until the user inputs text, at which point the image is removed.</span></span> <span data-ttu-id="1d7cf-104">Ayrıca, kullanıcının kendi giriş kaldırırsa arka plan resmini yeniden geri yüklenir.</span><span class="sxs-lookup"><span data-stu-id="1d7cf-104">In addition, the background image is restored again if the user removes their input.</span></span> <span data-ttu-id="1d7cf-105">Aşağıdaki resme bakın.</span><span class="sxs-lookup"><span data-stu-id="1d7cf-105">See illustration below.</span></span>  
  
 <span data-ttu-id="1d7cf-106">![TextBox ile arka plan görüntüsü](./media/editing-textbox-using-background-image.png "Editing_TextBox_using_background_image")</span><span class="sxs-lookup"><span data-stu-id="1d7cf-106">![A TextBox with a background image](./media/editing-textbox-using-background-image.png "Editing_TextBox_using_background_image")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1d7cf-107">Arka plan görüntüsü yerine sonra yalnızca düzenleme Bu örnekte kullanılan nedeni <xref:System.Windows.Controls.TextBox.Text%2A> özelliği <xref:System.Windows.Controls.TextBox>, olan bir arka plan görüntüsü ile veri bağlaması müdahale etmez.</span><span class="sxs-lookup"><span data-stu-id="1d7cf-107">The reason a background image is used in this example rather then simply manipulating the <xref:System.Windows.Controls.TextBox.Text%2A> property of <xref:System.Windows.Controls.TextBox>, is that a background image will not interfere with data binding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d7cf-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="1d7cf-108">Example</span></span>  
 [!code-xaml[TextBoxMiscSnippets_snip#TextBoxBackgroundExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/textbox_with_background_image.xaml#textboxbackgroundexamplewholepage)]  
  
 [!code-csharp[TextBoxMiscSnippets_snip#TextBoxBackgroundCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/textbox_with_background_image.xaml.cs#textboxbackgroundcodeexamplewholepage)]
 [!code-vb[TextBoxMiscSnippets_snip#TextBoxBackgroundCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/visualbasic/textbox_with_background_image.xaml.vb#textboxbackgroundcodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="1d7cf-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1d7cf-109">See also</span></span>

- [<span data-ttu-id="1d7cf-110">TextBox Genel Bakışı</span><span class="sxs-lookup"><span data-stu-id="1d7cf-110">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="1d7cf-111">RichTextBox Genel Bakışı</span><span class="sxs-lookup"><span data-stu-id="1d7cf-111">RichTextBox Overview</span></span>](richtextbox-overview.md)
