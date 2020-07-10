---
title: CheckBox Tıklamalarına Yanıt Verme
description: Windows Forms uygulamanızı, onay kutusunun durumuna bağlı olarak bazı eylemler gerçekleştirmek üzere nasıl programleyeceğinizi öğrenin.
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
ms.openlocfilehash: 58944bc421f990343b6c58484aaab3d79c8bda5e
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174503"
---
# <a name="how-to-respond-to-windows-forms-checkbox-clicks"></a><span data-ttu-id="18663-103">Nasıl yapılır: Windows Forms CheckBox Tıklamalarına Yanıt Verme</span><span class="sxs-lookup"><span data-stu-id="18663-103">How to: Respond to Windows Forms CheckBox Clicks</span></span>
<span data-ttu-id="18663-104">Kullanıcı Windows Forms <xref:System.Windows.Forms.CheckBox> denetimine tıkladığında <xref:System.Windows.Forms.Control.Click> olay oluşur.</span><span class="sxs-lookup"><span data-stu-id="18663-104">Whenever a user clicks a Windows Forms <xref:System.Windows.Forms.CheckBox> control, the <xref:System.Windows.Forms.Control.Click> event occurs.</span></span> <span data-ttu-id="18663-105">Onay kutusunun durumuna bağlı olarak, uygulamanızı bazı eylemler gerçekleştirecek şekilde programlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="18663-105">You can program your application to perform some action depending upon the state of the check box.</span></span>  
  
### <a name="to-respond-to-checkbox-clicks"></a><span data-ttu-id="18663-106">Onay kutusu tıklamalarına yanıt vermek için</span><span class="sxs-lookup"><span data-stu-id="18663-106">To respond to CheckBox clicks</span></span>  
  
1. <span data-ttu-id="18663-107"><xref:System.Windows.Forms.Control.Click>Olay işleyicisinde, <xref:System.Windows.Forms.CheckBox.Checked%2A> denetimin durumunu öğrenmek için özelliğini kullanın ve gerekli tüm eylemleri gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="18663-107">In the <xref:System.Windows.Forms.Control.Click> event handler, use the <xref:System.Windows.Forms.CheckBox.Checked%2A> property to determine the control's state, and perform any necessary action.</span></span>  
  
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
    > <span data-ttu-id="18663-108">Kullanıcı denetime çift tıkladenerse <xref:System.Windows.Forms.CheckBox> , her tıklama ayrı olarak işlenir; diğer bir deyişle, <xref:System.Windows.Forms.CheckBox> Denetim çift tıklama olayını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="18663-108">If the user attempts to double-click the <xref:System.Windows.Forms.CheckBox> control, each click will be processed separately; that is, the <xref:System.Windows.Forms.CheckBox> control does not support the double-click event.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="18663-109"><xref:System.Windows.Forms.CheckBox.AutoCheck%2A>Özellik `true` (varsayılan) olduğunda, <xref:System.Windows.Forms.CheckBox> tıklandığında otomatik olarak seçilir veya temizlenir.</span><span class="sxs-lookup"><span data-stu-id="18663-109">When the <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> property is `true` (the default), the <xref:System.Windows.Forms.CheckBox> is automatically selected or cleared when it is clicked.</span></span> <span data-ttu-id="18663-110">Aksi takdirde, <xref:System.Windows.Forms.CheckBox.Checked%2A> olay gerçekleştiğinde özelliği el ile ayarlamanız gerekir <xref:System.Windows.Forms.Control.Click> .</span><span class="sxs-lookup"><span data-stu-id="18663-110">Otherwise, you must manually set the <xref:System.Windows.Forms.CheckBox.Checked%2A> property when the <xref:System.Windows.Forms.Control.Click> event occurs.</span></span>  
  
     <span data-ttu-id="18663-111">Ayrıca, <xref:System.Windows.Forms.CheckBox> bir eylem kursu tespit etmek için denetimi de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="18663-111">You can also use the <xref:System.Windows.Forms.CheckBox> control to determine a course of action.</span></span>  
  
### <a name="to-determine-a-course-of-action-when-a-check-box-is-clicked"></a><span data-ttu-id="18663-112">Bir onay kutusu tıklandığında bir eylem kursu belirleme</span><span class="sxs-lookup"><span data-stu-id="18663-112">To determine a course of action when a check box is clicked</span></span>  
  
1. <span data-ttu-id="18663-113">Bir eylem kursu belirleme özelliğinin değerini sorgulamak için Case ifadesini kullanın <xref:System.Windows.Forms.CheckBox.CheckState%2A> .</span><span class="sxs-lookup"><span data-stu-id="18663-113">Use a case statement to query the value of the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property to determine a course of action.</span></span> <span data-ttu-id="18663-114"><xref:System.Windows.Forms.CheckBox.ThreeState%2A>Özelliği olarak ayarlandığında `true` , <xref:System.Windows.Forms.CheckBox.CheckState%2A> özelliği denetlenen kutuyu temsil eden üç olası değeri, işaretlenmekte olan kutuyu veya seçeneğin kullanılamaz olduğunu göstermek için kutunun soluk bir görünümle birlikte görüntüleneceği üçüncü bir belirsiz durumu döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="18663-114">When the <xref:System.Windows.Forms.CheckBox.ThreeState%2A> property is set to `true`, the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property may return three possible values, which represent the box being checked, the box being unchecked, or a third indeterminate state in which the box is displayed with a dimmed appearance to indicate the option is unavailable.</span></span>  
  
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
    > <span data-ttu-id="18663-115"><xref:System.Windows.Forms.CheckBox.ThreeState%2A>Özelliği olarak ayarlandığında `true` , <xref:System.Windows.Forms.CheckBox.Checked%2A> özelliği `true` hem hem de için döndürür <xref:System.Windows.Forms.CheckState.Checked> <xref:System.Windows.Forms.CheckState.Indeterminate> .</span><span class="sxs-lookup"><span data-stu-id="18663-115">When the <xref:System.Windows.Forms.CheckBox.ThreeState%2A> property is set to `true`, the <xref:System.Windows.Forms.CheckBox.Checked%2A> property returns `true` for both <xref:System.Windows.Forms.CheckState.Checked> and <xref:System.Windows.Forms.CheckState.Indeterminate>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18663-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="18663-116">See also</span></span>

- <xref:System.Windows.Forms.CheckBox>
- [<span data-ttu-id="18663-117">CheckBox Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="18663-117">CheckBox Control Overview</span></span>](checkbox-control-overview-windows-forms.md)
- [<span data-ttu-id="18663-118">Nasıl yapılır: Windows Forms CheckBox Denetimleriyle Seçenekleri Ayarlama</span><span class="sxs-lookup"><span data-stu-id="18663-118">How to: Set Options with Windows Forms CheckBox Controls</span></span>](how-to-set-options-with-windows-forms-checkbox-controls.md)
- [<span data-ttu-id="18663-119">CheckBox denetimi</span><span class="sxs-lookup"><span data-stu-id="18663-119">CheckBox Control</span></span>](checkbox-control-windows-forms.md)
