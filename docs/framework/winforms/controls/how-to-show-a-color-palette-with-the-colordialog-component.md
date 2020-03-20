---
title: 'Nasıl Yapılır: ColorDialog Bileşeni ile Renk Paleti Gösterme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- palettes [Windows Forms], showing color
- color dialog box [Windows Forms], showing color palettes
- colors [Windows Forms], allowing users to select
- color palettes [Windows Forms], dialog box
- ColorDialog component [Windows Forms], showing color palettes
- color palettes [Windows Forms], showing in ColorDialog component
- colors [Windows Forms], showing palettes
ms.assetid: ee050f61-dbc8-4436-ba22-51360981ab48
ms.openlocfilehash: 0406ef7a32678bd149c0024348a7adf1f0b72926
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141789"
---
# <a name="how-to-show-a-color-palette-with-the-colordialog-component"></a><span data-ttu-id="db271-102">Nasıl Yapılır: ColorDialog Bileşeni ile Renk Paleti Gösterme</span><span class="sxs-lookup"><span data-stu-id="db271-102">How to: Show a Color Palette with the ColorDialog Component</span></span>
<span data-ttu-id="db271-103">[ColorDialog](colordialog-component-windows-forms.md) bileşeni bir renk paleti görüntüler ve kullanıcının seçtiği rengi içeren bir özellik döndürür.</span><span class="sxs-lookup"><span data-stu-id="db271-103">The [ColorDialog](colordialog-component-windows-forms.md) component displays a palette of colors and returns a property containing the color the user has selected.</span></span>  
  
### <a name="to-choose-a-color-using-the-colordialog-component"></a><span data-ttu-id="db271-104">ColorDialog bileşenini kullanarak bir renk seçmek için</span><span class="sxs-lookup"><span data-stu-id="db271-104">To choose a color using the ColorDialog component</span></span>  
  
1. <span data-ttu-id="db271-105">Yöntemi kullanarak iletişim kutusunu <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="db271-105">Display the dialog box using the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span>  
  
2. <span data-ttu-id="db271-106">İletişim <xref:System.Windows.Forms.DialogResult> kutusunun nasıl kapatıldığını belirlemek için özelliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="db271-106">Use the <xref:System.Windows.Forms.DialogResult> property to determine how the dialog box was closed.</span></span>  
  
3. <span data-ttu-id="db271-107">Seçilen <xref:System.Windows.Forms.ColorDialog.Color%2A> rengi ayarlamak <xref:System.Windows.Forms.ColorDialog> için bileşenin özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="db271-107">Use the <xref:System.Windows.Forms.ColorDialog.Color%2A> property of the <xref:System.Windows.Forms.ColorDialog> component to set the chosen color.</span></span>  
  
     <span data-ttu-id="db271-108">Aşağıdaki örnekte, <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Click> olay işleyicisi bir <xref:System.Windows.Forms.ColorDialog> bileşeni açar.</span><span class="sxs-lookup"><span data-stu-id="db271-108">In the example below, the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler opens a <xref:System.Windows.Forms.ColorDialog> component.</span></span> <span data-ttu-id="db271-109">Bir renk seçildiğinde ve kullanıcı **Tamam'ı**tıklattığında, denetimin <xref:System.Windows.Forms.Button> arka plan rengi seçilen renge ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="db271-109">When a color is chosen and the user clicks **OK**, the <xref:System.Windows.Forms.Button> control's background color is set to the chosen color.</span></span> <span data-ttu-id="db271-110">Örnek, formunuzun bir <xref:System.Windows.Forms.Button> denetimi <xref:System.Windows.Forms.ColorDialog> ve bileşeni olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="db271-110">The example assumes your form has a <xref:System.Windows.Forms.Button> control and a <xref:System.Windows.Forms.ColorDialog> component.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
    ByVal e As System.EventArgs) Handles Button1.Click  
       If ColorDialog1.ShowDialog() = DialogResult.OK Then  
          Button1.BackColor = ColorDialog1.Color  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       if(colorDialog1.ShowDialog() == DialogResult.OK)  
       {  
          button1.BackColor = colorDialog1.Color;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,
          System::EventArgs ^ e)  
       {  
          if(colorDialog1->ShowDialog() == DialogResult::OK)  
          {  
             button1->BackColor = colorDialog1->Color;  
          }  
       }  
    ```  
  
     <span data-ttu-id="db271-111">(Görsel C#, Görsel C++) Olay işleyicisini kaydetmek için aşağıdaki kodu formun oluşturucusuna yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="db271-111">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="db271-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="db271-112">See also</span></span>

- <xref:System.Windows.Forms.ColorDialog>
- [<span data-ttu-id="db271-113">ColorDialog Bileşeni</span><span class="sxs-lookup"><span data-stu-id="db271-113">ColorDialog Component</span></span>](colordialog-component-windows-forms.md)
