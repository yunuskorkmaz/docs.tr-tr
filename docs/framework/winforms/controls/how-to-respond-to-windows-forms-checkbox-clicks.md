---
title: CheckBox Tıklamalarına Yanıt Verme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Click event [Windows Forms], CheckBox control
- CheckBox control [Windows Forms], Click events
- events [Windows Forms], Click events
- double-clicks
- check boxes [Windows Forms], responding to events
ms.assetid: c39f901e-8899-43b6-aa31-939cbf7089fb
ms.openlocfilehash: ba2afb52939a6274978ce725dac19b5622419b99
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735667"
---
# <a name="how-to-respond-to-windows-forms-checkbox-clicks"></a><span data-ttu-id="c19c0-102">Nasıl yapılır: Windows Forms CheckBox Tıklamalarına Yanıt Verme</span><span class="sxs-lookup"><span data-stu-id="c19c0-102">How to: Respond to Windows Forms CheckBox Clicks</span></span>
<span data-ttu-id="c19c0-103">Kullanıcı Windows Forms <xref:System.Windows.Forms.CheckBox> denetimine tıkladığında <xref:System.Windows.Forms.Control.Click> olay oluşur.</span><span class="sxs-lookup"><span data-stu-id="c19c0-103">Whenever a user clicks a Windows Forms <xref:System.Windows.Forms.CheckBox> control, the <xref:System.Windows.Forms.Control.Click> event occurs.</span></span> <span data-ttu-id="c19c0-104">Onay kutusunun durumuna bağlı olarak, uygulamanızı bazı eylemler gerçekleştirecek şekilde programlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c19c0-104">You can program your application to perform some action depending upon the state of the check box.</span></span>  
  
### <a name="to-respond-to-checkbox-clicks"></a><span data-ttu-id="c19c0-105">Onay kutusu tıklamalarına yanıt vermek için</span><span class="sxs-lookup"><span data-stu-id="c19c0-105">To respond to CheckBox clicks</span></span>  
  
1. <span data-ttu-id="c19c0-106"><xref:System.Windows.Forms.Control.Click> olay işleyicisinde, denetimin durumunu öğrenmek için <xref:System.Windows.Forms.CheckBox.Checked%2A> özelliğini kullanın ve gerekli tüm eylemleri gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="c19c0-106">In the <xref:System.Windows.Forms.Control.Click> event handler, use the <xref:System.Windows.Forms.CheckBox.Checked%2A> property to determine the control's state, and perform any necessary action.</span></span>  
  
    ```vb  
    Private Sub CheckBox1_Click(ByVal sender As Object, ByVal e As System.EventArgs) Handles CheckBox1.Click  
       ' The CheckBox control's Text property is changed each time the   
       ' control is clicked, indicating a checked or unchecked state.  
       If CheckBox1.Checked = True Then  
          CheckBox1.Text = "Checked"  
       Else  
          CheckBox1.Text = "Unchecked"  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void checkBox1_Click(object sender, System.EventArgs e)  
    {  
       // The CheckBox control's Text property is changed each time the   
       // control is clicked, indicating a checked or unchecked state.  
       if (checkBox1.Checked)  
       {  
          checkBox1.Text = "Checked";  
       }  
       else  
       {  
          checkBox1.Text = "Unchecked";  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void checkBox1_CheckedChanged(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          if (checkBox1->Checked)  
          {  
             checkBox1->Text = "Checked";  
          }  
          else  
          {  
             checkBox1->Text = "Unchecked";  
          }  
       }  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="c19c0-107">Kullanıcı <xref:System.Windows.Forms.CheckBox> denetimine çift tıkladenerse, her tıklama ayrı olarak işlenir; diğer bir deyişle, <xref:System.Windows.Forms.CheckBox> denetimi çift tıklama olayını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="c19c0-107">If the user attempts to double-click the <xref:System.Windows.Forms.CheckBox> control, each click will be processed separately; that is, the <xref:System.Windows.Forms.CheckBox> control does not support the double-click event.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="c19c0-108"><xref:System.Windows.Forms.CheckBox.AutoCheck%2A> özelliği `true` (varsayılan), tıklandığında <xref:System.Windows.Forms.CheckBox> otomatik olarak seçilir veya temizlenir.</span><span class="sxs-lookup"><span data-stu-id="c19c0-108">When the <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> property is `true` (the default), the <xref:System.Windows.Forms.CheckBox> is automatically selected or cleared when it is clicked.</span></span> <span data-ttu-id="c19c0-109">Aksi takdirde, <xref:System.Windows.Forms.Control.Click> olayı gerçekleştiğinde <xref:System.Windows.Forms.CheckBox.Checked%2A> özelliğini el ile ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c19c0-109">Otherwise, you must manually set the <xref:System.Windows.Forms.CheckBox.Checked%2A> property when the <xref:System.Windows.Forms.Control.Click> event occurs.</span></span>  
  
     <span data-ttu-id="c19c0-110"><xref:System.Windows.Forms.CheckBox> denetimini Ayrıca bir eylem kursu tespit etmek için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c19c0-110">You can also use the <xref:System.Windows.Forms.CheckBox> control to determine a course of action.</span></span>  
  
### <a name="to-determine-a-course-of-action-when-a-check-box-is-clicked"></a><span data-ttu-id="c19c0-111">Bir onay kutusu tıklandığında bir eylem kursu belirleme</span><span class="sxs-lookup"><span data-stu-id="c19c0-111">To determine a course of action when a check box is clicked</span></span>  
  
1. <span data-ttu-id="c19c0-112">Bir eylem kursu belirleme <xref:System.Windows.Forms.CheckBox.CheckState%2A> özelliğinin değerini sorgulamak için Case ifadesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c19c0-112">Use a case statement to query the value of the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property to determine a course of action.</span></span> <span data-ttu-id="c19c0-113"><xref:System.Windows.Forms.CheckBox.ThreeState%2A> özelliği `true`olarak ayarlandığında, <xref:System.Windows.Forms.CheckBox.CheckState%2A> özelliği denetlenen kutuyu temsil eden üç olası değeri, işaretlenmekte olan kutuyu veya seçeneğin kullanılamaz olduğunu göstermek için kutunun soluk bir görünümle birlikte görüntüleneceği üçüncü bir belirsiz durumu döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="c19c0-113">When the <xref:System.Windows.Forms.CheckBox.ThreeState%2A> property is set to `true`, the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property may return three possible values, which represent the box being checked, the box being unchecked, or a third indeterminate state in which the box is displayed with a dimmed appearance to indicate the option is unavailable.</span></span>  
  
    ```vb  
    Private Sub CheckBox1_Click(ByVal sender As Object, ByVal e As System.EventArgs) Handles CheckBox1.Click  
       Select Case CheckBox1.CheckState  
          Case CheckState.Checked  
             ' Code for checked state.  
          Case CheckState.Unchecked  
             ' Code for unchecked state.  
          Case CheckState.Indeterminate  
             ' Code for indeterminate state.  
       End Select   
    End Sub  
    ```  
  
    ```csharp  
    private void checkBox1_Click(object sender, System.EventArgs e)  
    {  
       switch(checkBox1.CheckState)  
       {  
          case CheckState.Checked:  
             // Code for checked state.  
             break;  
          case CheckState.Unchecked:  
             // Code for unchecked state.  
             break;  
          case CheckState.Indeterminate:  
             // Code for indeterminate state.  
             break;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void checkBox1_CheckedChanged(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          switch(checkBox1->CheckState) {  
             case CheckState::Checked:  
                // Code for checked state.  
                break;  
             case CheckState::Unchecked:  
                // Code for unchecked state.  
                break;  
             case CheckState::Indeterminate:  
                // Code for indeterminate state.  
                break;  
          }  
       }  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="c19c0-114"><xref:System.Windows.Forms.CheckBox.ThreeState%2A> özelliği `true`olarak ayarlandığında <xref:System.Windows.Forms.CheckBox.Checked%2A> özelliği hem <xref:System.Windows.Forms.CheckState.Checked> hem de <xref:System.Windows.Forms.CheckState.Indeterminate>için `true` döndürür.</span><span class="sxs-lookup"><span data-stu-id="c19c0-114">When the <xref:System.Windows.Forms.CheckBox.ThreeState%2A> property is set to `true`, the <xref:System.Windows.Forms.CheckBox.Checked%2A> property returns `true` for both <xref:System.Windows.Forms.CheckState.Checked> and <xref:System.Windows.Forms.CheckState.Indeterminate>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c19c0-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c19c0-115">See also</span></span>

- <xref:System.Windows.Forms.CheckBox>
- [<span data-ttu-id="c19c0-116">CheckBox Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c19c0-116">CheckBox Control Overview</span></span>](checkbox-control-overview-windows-forms.md)
- [<span data-ttu-id="c19c0-117">Nasıl yapılır: Windows Forms CheckBox Denetimleriyle Seçenekleri Ayarlama</span><span class="sxs-lookup"><span data-stu-id="c19c0-117">How to: Set Options with Windows Forms CheckBox Controls</span></span>](how-to-set-options-with-windows-forms-checkbox-controls.md)
- [<span data-ttu-id="c19c0-118">CheckBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="c19c0-118">CheckBox Control</span></span>](checkbox-control-windows-forms.md)
