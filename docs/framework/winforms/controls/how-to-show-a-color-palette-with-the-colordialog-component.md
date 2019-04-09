---
title: 'Nasıl yapılır: ColorDialog Bileşeni ile Renk Paleti Gösterme'
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
ms.openlocfilehash: fcaf5da9958cf66fb63bd753dc94cba9c10f62f6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59096042"
---
# <a name="how-to-show-a-color-palette-with-the-colordialog-component"></a><span data-ttu-id="c7459-102">Nasıl yapılır: ColorDialog Bileşeni ile Renk Paleti Gösterme</span><span class="sxs-lookup"><span data-stu-id="c7459-102">How to: Show a Color Palette with the ColorDialog Component</span></span>
<span data-ttu-id="c7459-103">[ColorDialog](colordialog-component-windows-forms.md) bileşeni bir renk paletini görüntüler ve kullanıcının seçtiği bir renk içeren bir özelliğini döndürür.</span><span class="sxs-lookup"><span data-stu-id="c7459-103">The [ColorDialog](colordialog-component-windows-forms.md) component displays a palette of colors and returns a property containing the color the user has selected.</span></span>  
  
### <a name="to-choose-a-color-using-the-colordialog-component"></a><span data-ttu-id="c7459-104">ColorDialog bileşeni kullanarak bir renk seçmek için</span><span class="sxs-lookup"><span data-stu-id="c7459-104">To choose a color using the ColorDialog component</span></span>  
  
1.  <span data-ttu-id="c7459-105">İletişim kutusunu kullanarak görüntüleme <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c7459-105">Display the dialog box using the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span>  
  
2.  <span data-ttu-id="c7459-106">Kullanım <xref:System.Windows.Forms.DialogResult> özelliği iletişim kutusu nasıl kapatıldığı belirler.</span><span class="sxs-lookup"><span data-stu-id="c7459-106">Use the <xref:System.Windows.Forms.DialogResult> property to determine how the dialog box was closed.</span></span>  
  
3.  <span data-ttu-id="c7459-107">Kullanım <xref:System.Windows.Forms.ColorDialog.Color%2A> özelliği <xref:System.Windows.Forms.ColorDialog> seçilen rengini ayarlamak için bileşen.</span><span class="sxs-lookup"><span data-stu-id="c7459-107">Use the <xref:System.Windows.Forms.ColorDialog.Color%2A> property of the <xref:System.Windows.Forms.ColorDialog> component to set the chosen color.</span></span>  
  
     <span data-ttu-id="c7459-108">Aşağıdaki örnekte <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Click> olay işleyicisi açılır bir <xref:System.Windows.Forms.ColorDialog> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="c7459-108">In the example below, the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler opens a <xref:System.Windows.Forms.ColorDialog> component.</span></span> <span data-ttu-id="c7459-109">Bir renk seçilen ve kullanıcı olduğunda tıkladığında **Tamam**, <xref:System.Windows.Forms.Button> denetimin arka plan rengi seçilen renge ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c7459-109">When a color is chosen and the user clicks **OK**, the <xref:System.Windows.Forms.Button> control's background color is set to the chosen color.</span></span> <span data-ttu-id="c7459-110">Formunuza sahip örnek varsayar bir <xref:System.Windows.Forms.Button> denetimi ve bir <xref:System.Windows.Forms.ColorDialog> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="c7459-110">The example assumes your form has a <xref:System.Windows.Forms.Button> control and a <xref:System.Windows.Forms.ColorDialog> component.</span></span>  
  
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
  
     <span data-ttu-id="c7459-111">(Visual C# [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) formun oluşturucuda olay işleyicisi kaydetmek için aşağıdaki kodu yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="c7459-111">(Visual C#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=   
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="c7459-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c7459-112">See also</span></span>

- <xref:System.Windows.Forms.ColorDialog>
- [<span data-ttu-id="c7459-113">ColorDialog Bileşeni</span><span class="sxs-lookup"><span data-stu-id="c7459-113">ColorDialog Component</span></span>](colordialog-component-windows-forms.md)
