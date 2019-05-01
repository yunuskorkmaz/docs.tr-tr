---
title: 'Nasıl yapılır: Windows Forms RichTextBox Denetimi İçin Yazı Tipi Özniteliklerini Ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- .rtf files [Windows Forms], formatting in RichTextBox control
- fonts [Windows Forms], changing attributes in RichTextBox control
- RTF files [Windows Forms], formatting in RichTextBox control
- RichTextBox control [Windows Forms], setting font attributes
- text [Windows Forms]
- text boxes [Windows Forms], formatting text
- formatting [Windows Forms]
ms.assetid: 2bc23ddb-0529-4489-a1a2-ad253cb43f9a
ms.openlocfilehash: a6fe5b30c457fae2d53c946092b214f492fe5e9b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013276"
---
# <a name="how-to-set-font-attributes-for-the-windows-forms-richtextbox-control"></a><span data-ttu-id="00124-102">Nasıl yapılır: Windows Forms RichTextBox Denetimi İçin Yazı Tipi Özniteliklerini Ayarlama</span><span class="sxs-lookup"><span data-stu-id="00124-102">How to: Set Font Attributes for the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="00124-103">Windows Forms <xref:System.Windows.Forms.RichTextBox> denetimin görüntülediği metni biçimlendirmek için çok sayıda seçeneği vardır.</span><span class="sxs-lookup"><span data-stu-id="00124-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control has numerous options for formatting the text it displays.</span></span> <span data-ttu-id="00124-104">Seçilen karakterleri kalın, altı çizili veya italik kullanarak yapabileceğiniz <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="00124-104">You can make the selected characters bold, underlined, or italic, using the <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> property.</span></span> <span data-ttu-id="00124-105">Bu özellik, boyutunu ve yazı tipi seçili karakterleri değiştirmek için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="00124-105">You can also use this property to change the size and typeface of the selected characters.</span></span> <span data-ttu-id="00124-106"><xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> Özelliği Seçilen karakterleri rengini değiştirmek etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="00124-106">The <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> property enables you to change the selected characters' color.</span></span>  
  
### <a name="to-change-the-appearance-of-characters"></a><span data-ttu-id="00124-107">Karakter görünümünü değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="00124-107">To change the appearance of characters</span></span>  
  
1. <span data-ttu-id="00124-108">Ayarlama <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> özelliğini uygun bir yazı tipi.</span><span class="sxs-lookup"><span data-stu-id="00124-108">Set the <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> property to an appropriate font.</span></span>  
  
     <span data-ttu-id="00124-109">Yazı tipi ailesi, boyut ve yazı tipi uygulamada ayarlamak kullanıcıları etkinleştirmek için genellikle kullanacağınız <xref:System.Windows.Forms.FontDialog> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="00124-109">To enable users to set the font family, size, and typeface in an application, you would typically use the <xref:System.Windows.Forms.FontDialog> component.</span></span> <span data-ttu-id="00124-110">Genel bakış için bkz. [FontDialog bileşenine genel bakış](fontdialog-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="00124-110">For an overview, see [FontDialog Component Overview](fontdialog-component-overview-windows-forms.md).</span></span>  
  
2. <span data-ttu-id="00124-111">Ayarlama <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> özelliğini uygun bir renk.</span><span class="sxs-lookup"><span data-stu-id="00124-111">Set the <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> property to an appropriate color.</span></span>  
  
     <span data-ttu-id="00124-112">Bir uygulamada rengini ayarlamak kullanıcıları etkinleştirmek için genellikle kullanacağınız <xref:System.Windows.Forms.ColorDialog> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="00124-112">To enable users to set the color in an application, you would typically use the <xref:System.Windows.Forms.ColorDialog> component.</span></span> <span data-ttu-id="00124-113">Genel bakış için bkz. [ColorDialog bileşenine genel bakış](colordialog-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="00124-113">For an overview, see [ColorDialog Component Overview](colordialog-component-overview-windows-forms.md).</span></span>  
  
    ```vb  
    RichTextBox1.SelectionFont = New Font("Tahoma", 12, FontStyle.Bold)  
    RichTextBox1.SelectionColor = System.Drawing.Color.Red  
    ```  
  
    ```csharp  
    richTextBox1.SelectionFont = new Font("Tahoma", 12, FontStyle.Bold);  
    richTextBox1.SelectionColor = System.Drawing.Color.Red;  
    ```  
  
    ```cpp  
    richTextBox1->SelectionFont =  
       gcnew System::Drawing::Font("Tahoma", 12, FontStyle::Bold);  
    richTextBox1->SelectionColor = System::Drawing::Color::Red;  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="00124-114">Bu özellikler, yalnızca seçili metni etkiler veya hiç metin seçili değilse, metin olan ekleme noktasının geçerli konumda yazdınız.</span><span class="sxs-lookup"><span data-stu-id="00124-114">These properties only affect selected text, or, if no text is selected, the text that is typed at the current location of the insertion point.</span></span> <span data-ttu-id="00124-115">Program aracılığıyla metni seçme hakkında daha fazla bilgi için bkz: <xref:System.Windows.Forms.TextBoxBase.Select%2A>.</span><span class="sxs-lookup"><span data-stu-id="00124-115">For information on selecting text programmatically, see <xref:System.Windows.Forms.TextBoxBase.Select%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00124-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="00124-116">See also</span></span>

- <xref:System.Windows.Forms.RichTextBox>
- [<span data-ttu-id="00124-117">RichTextBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="00124-117">RichTextBox Control</span></span>](richtextbox-control-windows-forms.md)
- [<span data-ttu-id="00124-118">Windows Forms'da Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="00124-118">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
