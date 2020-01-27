---
title: TextBox Denetimine Genel Bakış
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
ms.openlocfilehash: 06ab460d720d17331881b5ba653263160eaf3cb3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742799"
---
# <a name="textbox-control-overview-windows-forms"></a><span data-ttu-id="b8768-102">TextBox Denetimine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="b8768-102">TextBox Control Overview (Windows Forms)</span></span>
<span data-ttu-id="b8768-103">Windows Forms metin kutuları, kullanıcıdan giriş almak veya metin göstermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b8768-103">Windows Forms text boxes are used to get input from the user or to display text.</span></span> <span data-ttu-id="b8768-104"><xref:System.Windows.Forms.TextBox> denetimi genellikle düzenlenebilir metin için kullanılır, ancak salt okunabilir hale getirilebilir.</span><span class="sxs-lookup"><span data-stu-id="b8768-104">The <xref:System.Windows.Forms.TextBox> control is generally used for editable text, although it can also be made read-only.</span></span> <span data-ttu-id="b8768-105">Metin kutuları birden çok satır görüntüleyebilir, metni denetimin boyutuna kaydırabilirler ve temel biçimlendirme ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="b8768-105">Text boxes can display multiple lines, wrap text to the size of the control, and add basic formatting.</span></span> <span data-ttu-id="b8768-106"><xref:System.Windows.Forms.TextBox> denetimi, görüntülenmiş veya denetime girilen metin için tek bir biçim stili sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8768-106">The <xref:System.Windows.Forms.TextBox> control provides a single format style for text displayed or entered into the control.</span></span> <span data-ttu-id="b8768-107">Birden çok biçimli metin türünü göstermek için <xref:System.Windows.Forms.RichTextBox> denetimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="b8768-107">To display multiple types of formatted text, use the <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="b8768-108">Daha fazla bilgi için bkz. [RichTextBox denetimine genel bakış](richtextbox-control-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="b8768-108">For more information, see [RichTextBox Control Overview](richtextbox-control-overview-windows-forms.md).</span></span>  
  
## <a name="working-with-the-textbox-control"></a><span data-ttu-id="b8768-109">TextBox denetimiyle çalışma</span><span class="sxs-lookup"><span data-stu-id="b8768-109">Working with the TextBox Control</span></span>  
 <span data-ttu-id="b8768-110">Denetim tarafından görünen metin, <xref:System.Windows.Forms.TextBox.Text%2A> özelliğinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="b8768-110">The text displayed by the control is contained in the <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span> <span data-ttu-id="b8768-111">Varsayılan olarak, bir metin kutusuna en fazla 2048 karakter girebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b8768-111">By default, you can enter up to 2048 characters in a text box.</span></span> <span data-ttu-id="b8768-112"><xref:System.Windows.Forms.TextBox.Multiline%2A> özelliğini `true`olarak ayarlarsanız, 32 KB 'a kadar metin girebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b8768-112">If you set the <xref:System.Windows.Forms.TextBox.Multiline%2A> property to `true`, you can enter up to 32 KB of text.</span></span> <span data-ttu-id="b8768-113"><xref:System.Windows.Forms.TextBox.Text%2A> özelliği, tasarım zamanında Özellikler penceresiyle, koddaki çalışma zamanında veya çalışma zamanında Kullanıcı girişiyle ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="b8768-113">The <xref:System.Windows.Forms.TextBox.Text%2A> property can be set at design time with the Properties Window, at run time in code, or by user input at run time.</span></span> <span data-ttu-id="b8768-114">Bir metin kutusunun geçerli içeriği, <xref:System.Windows.Forms.TextBox.Text%2A> özelliği okunarak çalışma zamanında alınabilir.</span><span class="sxs-lookup"><span data-stu-id="b8768-114">The current contents of a text box can be retrieved at run time by reading the <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span>  
  
 <span data-ttu-id="b8768-115">Aşağıdaki kod örneği, çalışma zamanında denetimindeki metni ayarlar.</span><span class="sxs-lookup"><span data-stu-id="b8768-115">The following code example sets text in the control at run time.</span></span> <span data-ttu-id="b8768-116">`InitializeMyControl` yordamı otomatik olarak yürütülmez; çağrılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b8768-116">The `InitializeMyControl` procedure will not execute automatically; it must be called.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b8768-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b8768-117">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- [<span data-ttu-id="b8768-118">Nasıl yapılır: Windows Forms TextBox Denetiminde Ekleme Noktasını Belirleme</span><span class="sxs-lookup"><span data-stu-id="b8768-118">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="b8768-119">Nasıl yapılır: Windows Forms TextBox Denetimi ile Parola Metin Kutusu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b8768-119">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="b8768-120">Nasıl yapılır: Salt Okunur Metin Kutusu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b8768-120">How to: Create a Read-Only Text Box</span></span>](how-to-create-a-read-only-text-box-windows-forms.md)
- [<span data-ttu-id="b8768-121">Nasıl yapılır: Dizeye Tırnak İşaretleri Koyma</span><span class="sxs-lookup"><span data-stu-id="b8768-121">How to: Put Quotation Marks in a String</span></span>](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [<span data-ttu-id="b8768-122">Nasıl yapılır: Windows Forms TextBox Denetiminde Metni Seçme</span><span class="sxs-lookup"><span data-stu-id="b8768-122">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="b8768-123">Nasıl yapılır: Windows Forms TextBox Denetiminde Birden Fazla Çizgiyi Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="b8768-123">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="b8768-124">TextBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="b8768-124">TextBox Control</span></span>](textbox-control-windows-forms.md)
