---
title: TextBox Denetimine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- TextBox
helpviewer_keywords:
- TextBox control [Windows Forms], about TextBox controls
- text boxes [Windows Forms], adding
ms.assetid: d1a9c7f5-fa53-480a-a75c-158f8649ea2f
ms.openlocfilehash: b15de762b166fb66ff926706e93cbac6d0c6ba9b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33539873"
---
# <a name="textbox-control-overview-windows-forms"></a><span data-ttu-id="08646-102">TextBox Denetimine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="08646-102">TextBox Control Overview (Windows Forms)</span></span>
<span data-ttu-id="08646-103">Windows Forms metin kutuları kullanıcıdan giriş almak veya metni görüntülemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="08646-103">Windows Forms text boxes are used to get input from the user or to display text.</span></span> <span data-ttu-id="08646-104"><xref:System.Windows.Forms.TextBox> Salt okunur ayrıca çalışabilmesine rağmen denetim düzenlenebilir metin için genellikle kullanılır.</span><span class="sxs-lookup"><span data-stu-id="08646-104">The <xref:System.Windows.Forms.TextBox> control is generally used for editable text, although it can also be made read-only.</span></span> <span data-ttu-id="08646-105">Metin kutuları birden çok satır görüntüleme, denetimin boyutunu metni kaydırma ve temel biçimlendirme ekleyin.</span><span class="sxs-lookup"><span data-stu-id="08646-105">Text boxes can display multiple lines, wrap text to the size of the control, and add basic formatting.</span></span> <span data-ttu-id="08646-106"><xref:System.Windows.Forms.TextBox> Denetimi görüntülenen veya denetime girilen metin için bir tek biçimi stili sağlar.</span><span class="sxs-lookup"><span data-stu-id="08646-106">The <xref:System.Windows.Forms.TextBox> control provides a single format style for text displayed or entered into the control.</span></span> <span data-ttu-id="08646-107">Biçimlendirilmiş metin birden çok türde görüntülemek için kullanın <xref:System.Windows.Forms.RichTextBox> denetim.</span><span class="sxs-lookup"><span data-stu-id="08646-107">To display multiple types of formatted text, use the <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="08646-108">Daha fazla bilgi için bkz: [RichTextBox denetimine genel bakış](../../../../docs/framework/winforms/controls/richtextbox-control-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="08646-108">For more information, see [RichTextBox Control Overview](../../../../docs/framework/winforms/controls/richtextbox-control-overview-windows-forms.md).</span></span>  
  
## <a name="working-with-the-textbox-control"></a><span data-ttu-id="08646-109">TextBox denetimi ile çalışma</span><span class="sxs-lookup"><span data-stu-id="08646-109">Working with the TextBox Control</span></span>  
 <span data-ttu-id="08646-110">Denetimi tarafından görüntülenen metni yer <xref:System.Windows.Forms.TextBox.Text%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="08646-110">The text displayed by the control is contained in the <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span> <span data-ttu-id="08646-111">Varsayılan olarak, en çok 2048 karakter metin kutusuna girebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="08646-111">By default, you can enter up to 2048 characters in a text box.</span></span> <span data-ttu-id="08646-112">Ayarlarsanız <xref:System.Windows.Forms.TextBox.Multiline%2A> özelliğine `true`, en çok 32 KB metin girin.</span><span class="sxs-lookup"><span data-stu-id="08646-112">If you set the <xref:System.Windows.Forms.TextBox.Multiline%2A> property to `true`, you can enter up to 32 KB of text.</span></span> <span data-ttu-id="08646-113"><xref:System.Windows.Forms.TextBox.Text%2A> Özelliği, tasarım zamanında Özellikler penceresi ile çalışma zamanında kod veya kullanıcı girişi tarafından çalışma zamanında ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="08646-113">The <xref:System.Windows.Forms.TextBox.Text%2A> property can be set at design time with the Properties Window, at run time in code, or by user input at run time.</span></span> <span data-ttu-id="08646-114">Geçerli bir metin kutusunun içeriğini okuyarak çalışma zamanında alınabilir <xref:System.Windows.Forms.TextBox.Text%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="08646-114">The current contents of a text box can be retrieved at run time by reading the <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span>  
  
 <span data-ttu-id="08646-115">Aşağıdaki kod örneğinde metin denetiminde çalışma zamanında ayarlar.</span><span class="sxs-lookup"><span data-stu-id="08646-115">The following code example sets text in the control at run time.</span></span> <span data-ttu-id="08646-116">`InitializeMyControl` Yordamı değil yürütülecek otomatik olarak; çağrılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="08646-116">The `InitializeMyControl` procedure will not execute automatically; it must be called.</span></span>  
  
```vb  
Private Sub InitializeMyControl()  
   ' Put some text into the control first.  
   TextBox1.Text = "This is a TextBox control."  
End Sub  
```  
  
```csharp  
private void InitializeMyControl() {  
   // Put some text into the control first.  
   textBox1.Text = "This is a TextBox control.";  
}  
```  
  
```cpp  
private:  
   void InitializeMyControl()  
   {  
      // Put some text into the control first.  
      textBox1->Text = "This is a TextBox control.";  
   }  
```  
  
## <a name="see-also"></a><span data-ttu-id="08646-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="08646-117">See Also</span></span>  
 <xref:System.Windows.Forms.TextBox>  
 [<span data-ttu-id="08646-118">Nasıl yapılır: Windows Forms TextBox Denetiminde Ekleme Noktasını Belirleme</span><span class="sxs-lookup"><span data-stu-id="08646-118">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [<span data-ttu-id="08646-119">Nasıl yapılır: Windows Forms TextBox Denetimi ile Parola Metin Kutusu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="08646-119">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="08646-120">Nasıl yapılır: Salt Okunur Metin Kutusu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="08646-120">How to: Create a Read-Only Text Box</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 [<span data-ttu-id="08646-121">Nasıl yapılır: Dizeye Tırnak İşaretleri Koyma</span><span class="sxs-lookup"><span data-stu-id="08646-121">How to: Put Quotation Marks in a String</span></span>](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 [<span data-ttu-id="08646-122">Nasıl yapılır: Windows Forms TextBox Denetiminde Metni Seçme</span><span class="sxs-lookup"><span data-stu-id="08646-122">How to: Select Text in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="08646-123">Nasıl yapılır: Windows Forms TextBox Denetiminde Birden Fazla Çizgiyi Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="08646-123">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="08646-124">TextBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="08646-124">TextBox Control</span></span>](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
