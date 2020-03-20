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
ms.openlocfilehash: 6ff20c443519446d3804b325924cb3c5cbedea97
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141932"
---
# <a name="how-to-respond-to-windows-forms-checkbox-clicks"></a><span data-ttu-id="3046c-102">Nasıl yapılır: Windows Forms CheckBox Tıklamalarına Yanıt Verme</span><span class="sxs-lookup"><span data-stu-id="3046c-102">How to: Respond to Windows Forms CheckBox Clicks</span></span>
<span data-ttu-id="3046c-103">Bir kullanıcı Windows Forms <xref:System.Windows.Forms.CheckBox> denetimini <xref:System.Windows.Forms.Control.Click> tıklattığında, olay oluşur.</span><span class="sxs-lookup"><span data-stu-id="3046c-103">Whenever a user clicks a Windows Forms <xref:System.Windows.Forms.CheckBox> control, the <xref:System.Windows.Forms.Control.Click> event occurs.</span></span> <span data-ttu-id="3046c-104">Başvurunuzu, onay kutusunun durumuna bağlı olarak bazı eylemler gerçekleştirecek şekilde programlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3046c-104">You can program your application to perform some action depending upon the state of the check box.</span></span>  
  
### <a name="to-respond-to-checkbox-clicks"></a><span data-ttu-id="3046c-105">CheckBox tıklamalarına yanıt vermek için</span><span class="sxs-lookup"><span data-stu-id="3046c-105">To respond to CheckBox clicks</span></span>  
  
1. <span data-ttu-id="3046c-106">Olay <xref:System.Windows.Forms.Control.Click> işleyicisi, <xref:System.Windows.Forms.CheckBox.Checked%2A> denetimdurumunu belirlemek için özelliği kullanın ve gerekli eylemi gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="3046c-106">In the <xref:System.Windows.Forms.Control.Click> event handler, use the <xref:System.Windows.Forms.CheckBox.Checked%2A> property to determine the control's state, and perform any necessary action.</span></span>  
  
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
    > <span data-ttu-id="3046c-107">Kullanıcı <xref:System.Windows.Forms.CheckBox> denetimi çift tıklatmaya çalışırsa, her tıklama ayrı ayrı işlenir; diğer bir <xref:System.Windows.Forms.CheckBox> diğer olarak, denetim çift tıklatma olayını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="3046c-107">If the user attempts to double-click the <xref:System.Windows.Forms.CheckBox> control, each click will be processed separately; that is, the <xref:System.Windows.Forms.CheckBox> control does not support the double-click event.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="3046c-108"><xref:System.Windows.Forms.CheckBox.AutoCheck%2A> Özellik (varsayılan) olduğunda, `true` <xref:System.Windows.Forms.CheckBox> tıklatıldığında otomatik olarak seçilir veya temizlenir.</span><span class="sxs-lookup"><span data-stu-id="3046c-108">When the <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> property is `true` (the default), the <xref:System.Windows.Forms.CheckBox> is automatically selected or cleared when it is clicked.</span></span> <span data-ttu-id="3046c-109">Aksi takdirde, <xref:System.Windows.Forms.CheckBox.Checked%2A> <xref:System.Windows.Forms.Control.Click> olay gerçekleştiğinde özelliği el ile ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3046c-109">Otherwise, you must manually set the <xref:System.Windows.Forms.CheckBox.Checked%2A> property when the <xref:System.Windows.Forms.Control.Click> event occurs.</span></span>  
  
     <span data-ttu-id="3046c-110">Denetimi <xref:System.Windows.Forms.CheckBox> bir eylem rotasını belirlemek için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3046c-110">You can also use the <xref:System.Windows.Forms.CheckBox> control to determine a course of action.</span></span>  
  
### <a name="to-determine-a-course-of-action-when-a-check-box-is-clicked"></a><span data-ttu-id="3046c-111">Onay kutusu tıklatıldığında eylem rotasını belirlemek için</span><span class="sxs-lookup"><span data-stu-id="3046c-111">To determine a course of action when a check box is clicked</span></span>  
  
1. <span data-ttu-id="3046c-112">Bir eylem kursunu belirlemek için <xref:System.Windows.Forms.CheckBox.CheckState%2A> özelliğin değerini sorgulamak için bir servis talebi deyimi kullanın.</span><span class="sxs-lookup"><span data-stu-id="3046c-112">Use a case statement to query the value of the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property to determine a course of action.</span></span> <span data-ttu-id="3046c-113"><xref:System.Windows.Forms.CheckBox.ThreeState%2A> Özellik `true`ayarlandığında, <xref:System.Windows.Forms.CheckBox.CheckState%2A> özellik işaretlenen kutuyu temsil eden üç olası değer, işaretlenmemiş kutuyu veya seçeneğin kullanılmayabileceğini belirtmek için kutunun soluk bir görünümle görüntülendiği üçüncü bir belirsiz durumu döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="3046c-113">When the <xref:System.Windows.Forms.CheckBox.ThreeState%2A> property is set to `true`, the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property may return three possible values, which represent the box being checked, the box being unchecked, or a third indeterminate state in which the box is displayed with a dimmed appearance to indicate the option is unavailable.</span></span>  
  
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
    > <span data-ttu-id="3046c-114"><xref:System.Windows.Forms.CheckBox.ThreeState%2A> `true`Özellik ayarlandığında, <xref:System.Windows.Forms.CheckBox.Checked%2A> özellik hem `true` de <xref:System.Windows.Forms.CheckState.Checked> . <xref:System.Windows.Forms.CheckState.Indeterminate></span><span class="sxs-lookup"><span data-stu-id="3046c-114">When the <xref:System.Windows.Forms.CheckBox.ThreeState%2A> property is set to `true`, the <xref:System.Windows.Forms.CheckBox.Checked%2A> property returns `true` for both <xref:System.Windows.Forms.CheckState.Checked> and <xref:System.Windows.Forms.CheckState.Indeterminate>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3046c-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3046c-115">See also</span></span>

- <xref:System.Windows.Forms.CheckBox>
- [<span data-ttu-id="3046c-116">CheckBox Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="3046c-116">CheckBox Control Overview</span></span>](checkbox-control-overview-windows-forms.md)
- [<span data-ttu-id="3046c-117">Nasıl yapılır: Windows Forms CheckBox Denetimleriyle Seçenekleri Ayarlama</span><span class="sxs-lookup"><span data-stu-id="3046c-117">How to: Set Options with Windows Forms CheckBox Controls</span></span>](how-to-set-options-with-windows-forms-checkbox-controls.md)
- [<span data-ttu-id="3046c-118">CheckBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="3046c-118">CheckBox Control</span></span>](checkbox-control-windows-forms.md)
