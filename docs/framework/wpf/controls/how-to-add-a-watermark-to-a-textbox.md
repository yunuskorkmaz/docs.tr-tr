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
ms.openlocfilehash: abe276c686d394ded13ec03f08deae65e4098d03
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923571"
---
# <a name="how-to-add-a-watermark-to-a-textbox"></a><span data-ttu-id="560fd-102">Nasıl yapılır: TextBox'a Filigran Ekleme</span><span class="sxs-lookup"><span data-stu-id="560fd-102">How to: Add a Watermark to a TextBox</span></span>
<span data-ttu-id="560fd-103">Aşağıdaki örnek, Kullanıcı metin girişi <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.TextBox> yapılıncaya kadar ' ın içinde açıklayıcı bir arka plan görüntüsü görüntüleyerek bir öğesinin kullanılabilirliğine nasıl yardımcı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="560fd-103">The following example shows how to aid usability of a <xref:System.Windows.Controls.TextBox> by displaying an explanatory background image inside of the <xref:System.Windows.Controls.TextBox> until the user inputs text, at which point the image is removed.</span></span> <span data-ttu-id="560fd-104">Ayrıca, Kullanıcı girişlerini kaldırırsa arka plan görüntüsü yeniden geri yüklenir.</span><span class="sxs-lookup"><span data-stu-id="560fd-104">In addition, the background image is restored again if the user removes their input.</span></span> <span data-ttu-id="560fd-105">Aşağıdaki çizime bakın.</span><span class="sxs-lookup"><span data-stu-id="560fd-105">See illustration below.</span></span>  
  
 <span data-ttu-id="560fd-106">![Arka plan resmi olan bir metin kutusu](./media/editing-textbox-using-background-image.png "Editing_TextBox_using_background_image")</span><span class="sxs-lookup"><span data-stu-id="560fd-106">![A TextBox with a background image](./media/editing-textbox-using-background-image.png "Editing_TextBox_using_background_image")</span></span>  
  
> [!NOTE]
> <span data-ttu-id="560fd-107">Bu örnekte, bir arka plan resminin, <xref:System.Windows.Controls.TextBox.Text%2A> <xref:System.Windows.Controls.TextBox>özelliğini işlemek yerine kullanıldığı neden, arka plan resminin veri bağlamayı etkilememesini sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="560fd-107">The reason a background image is used in this example rather then simply manipulating the <xref:System.Windows.Controls.TextBox.Text%2A> property of <xref:System.Windows.Controls.TextBox>, is that a background image will not interfere with data binding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="560fd-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="560fd-108">Example</span></span>  
 [!code-xaml[TextBoxMiscSnippets_snip#TextBoxBackgroundExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/textbox_with_background_image.xaml#textboxbackgroundexamplewholepage)]  
  
 [!code-csharp[TextBoxMiscSnippets_snip#TextBoxBackgroundCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/textbox_with_background_image.xaml.cs#textboxbackgroundcodeexamplewholepage)]
 [!code-vb[TextBoxMiscSnippets_snip#TextBoxBackgroundCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/visualbasic/textbox_with_background_image.xaml.vb#textboxbackgroundcodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="560fd-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="560fd-109">See also</span></span>

- [<span data-ttu-id="560fd-110">TextBox Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="560fd-110">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="560fd-111">RichTextBox Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="560fd-111">RichTextBox Overview</span></span>](richtextbox-overview.md)
