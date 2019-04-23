---
title: 'Nasıl yapılır: Windows Forms CheckBox Tıklamalarına Yanıt Verme'
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
ms.openlocfilehash: ce616f45ceaa3db117c6981d2987ac09bba7b3fb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59319904"
---
# <a name="how-to-respond-to-windows-forms-checkbox-clicks"></a><span data-ttu-id="8dbed-102">Nasıl yapılır: Windows Forms CheckBox Tıklamalarına Yanıt Verme</span><span class="sxs-lookup"><span data-stu-id="8dbed-102">How to: Respond to Windows Forms CheckBox Clicks</span></span>
<span data-ttu-id="8dbed-103">Her bir kullanıcı bir Windows Forms tıkladığında <xref:System.Windows.Forms.CheckBox> denetimi <xref:System.Windows.Forms.Control.Click> olayı oluşur.</span><span class="sxs-lookup"><span data-stu-id="8dbed-103">Whenever a user clicks a Windows Forms <xref:System.Windows.Forms.CheckBox> control, the <xref:System.Windows.Forms.Control.Click> event occurs.</span></span> <span data-ttu-id="8dbed-104">Onay kutusunun durumunu olarak bazı eylemleri gerçekleştirmek için uygulamanızı programlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8dbed-104">You can program your application to perform some action depending upon the state of the check box.</span></span>  
  
### <a name="to-respond-to-checkbox-clicks"></a><span data-ttu-id="8dbed-105">CheckBox tıklamalarına yanıt verme için</span><span class="sxs-lookup"><span data-stu-id="8dbed-105">To respond to CheckBox clicks</span></span>  
  
1. <span data-ttu-id="8dbed-106">İçinde <xref:System.Windows.Forms.Control.Click> olay işleyicisi, kullanım <xref:System.Windows.Forms.CheckBox.Checked%2A> denetimin durumunu belirlemek ve gerekli herhangi bir eylemi gerçekleştirmek için özellik.</span><span class="sxs-lookup"><span data-stu-id="8dbed-106">In the <xref:System.Windows.Forms.Control.Click> event handler, use the <xref:System.Windows.Forms.CheckBox.Checked%2A> property to determine the control's state, and perform any necessary action.</span></span>  
  
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
    >  <span data-ttu-id="8dbed-107">Kullanıcının çift çalışırsa <xref:System.Windows.Forms.CheckBox> denetimi her tıklatma ayrı ayrı işlenir; diğer bir deyişle, <xref:System.Windows.Forms.CheckBox> denetimi çift olay desteklemez.</span><span class="sxs-lookup"><span data-stu-id="8dbed-107">If the user attempts to double-click the <xref:System.Windows.Forms.CheckBox> control, each click will be processed separately; that is, the <xref:System.Windows.Forms.CheckBox> control does not support the double-click event.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8dbed-108">Zaman <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> özelliği `true` (varsayılan), <xref:System.Windows.Forms.CheckBox> otomatik olarak seçilir veya tıklandığında temizlenir.</span><span class="sxs-lookup"><span data-stu-id="8dbed-108">When the <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> property is `true` (the default), the <xref:System.Windows.Forms.CheckBox> is automatically selected or cleared when it is clicked.</span></span> <span data-ttu-id="8dbed-109">Aksi takdirde, el ile ayarlamanız gerekir <xref:System.Windows.Forms.CheckBox.Checked%2A> özelliği olduğunda <xref:System.Windows.Forms.Control.Click> olayı oluşur.</span><span class="sxs-lookup"><span data-stu-id="8dbed-109">Otherwise, you must manually set the <xref:System.Windows.Forms.CheckBox.Checked%2A> property when the <xref:System.Windows.Forms.Control.Click> event occurs.</span></span>  
  
     <span data-ttu-id="8dbed-110">Ayrıca <xref:System.Windows.Forms.CheckBox> denetim bir eylemi belirlemek için.</span><span class="sxs-lookup"><span data-stu-id="8dbed-110">You can also use the <xref:System.Windows.Forms.CheckBox> control to determine a course of action.</span></span>  
  
### <a name="to-determine-a-course-of-action-when-a-check-box-is-clicked"></a><span data-ttu-id="8dbed-111">Bir eylemi bir onay kutusu seçildiğinde belirlemek için tıklandı</span><span class="sxs-lookup"><span data-stu-id="8dbed-111">To determine a course of action when a check box is clicked</span></span>  
  
1. <span data-ttu-id="8dbed-112">Case deyimi değerini sorgulamanıza <xref:System.Windows.Forms.CheckBox.CheckState%2A> özelliğini bir eyleme belirlemek için.</span><span class="sxs-lookup"><span data-stu-id="8dbed-112">Use a case statement to query the value of the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property to determine a course of action.</span></span> <span data-ttu-id="8dbed-113">Zaman <xref:System.Windows.Forms.CheckBox.ThreeState%2A> özelliği `true`, <xref:System.Windows.Forms.CheckBox.CheckState%2A> özelliği, kutunun denetlenen temsil eder ve üç olası değer döndürebilir kutusu görüntülenir kutusu denetlenmeyen durdurulmasını veya üçüncü belirlenmemiş duruma sahip bir devre dışı Görünüm seçeneğini belirtmek için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="8dbed-113">When the <xref:System.Windows.Forms.CheckBox.ThreeState%2A> property is set to `true`, the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property may return three possible values, which represent the box being checked, the box being unchecked, or a third indeterminate state in which the box is displayed with a dimmed appearance to indicate the option is unavailable.</span></span>  
  
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
    >  <span data-ttu-id="8dbed-114">Zaman <xref:System.Windows.Forms.CheckBox.ThreeState%2A> özelliği `true`, <xref:System.Windows.Forms.CheckBox.Checked%2A> özelliği döndürür `true` hem <xref:System.Windows.Forms.CheckState.Checked> ve <xref:System.Windows.Forms.CheckState.Indeterminate>.</span><span class="sxs-lookup"><span data-stu-id="8dbed-114">When the <xref:System.Windows.Forms.CheckBox.ThreeState%2A> property is set to `true`, the <xref:System.Windows.Forms.CheckBox.Checked%2A> property returns `true` for both <xref:System.Windows.Forms.CheckState.Checked> and <xref:System.Windows.Forms.CheckState.Indeterminate>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8dbed-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8dbed-115">See also</span></span>

- <xref:System.Windows.Forms.CheckBox>
- [<span data-ttu-id="8dbed-116">CheckBox Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="8dbed-116">CheckBox Control Overview</span></span>](checkbox-control-overview-windows-forms.md)
- [<span data-ttu-id="8dbed-117">Nasıl yapılır: Windows Forms CheckBox denetimleriyle seçenekleri ayarlama</span><span class="sxs-lookup"><span data-stu-id="8dbed-117">How to: Set Options with Windows Forms CheckBox Controls</span></span>](how-to-set-options-with-windows-forms-checkbox-controls.md)
- [<span data-ttu-id="8dbed-118">CheckBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="8dbed-118">CheckBox Control</span></span>](checkbox-control-windows-forms.md)
