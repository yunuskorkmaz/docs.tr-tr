---
title: "Nasıl yapılır: Windows Forms CheckBox Tıklamalarına Yanıt Verme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fe7826d1081f69bae1d220c22447886511cf58e3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-respond-to-windows-forms-checkbox-clicks"></a><span data-ttu-id="c1da9-102">Nasıl yapılır: Windows Forms CheckBox Tıklamalarına Yanıt Verme</span><span class="sxs-lookup"><span data-stu-id="c1da9-102">How to: Respond to Windows Forms CheckBox Clicks</span></span>
<span data-ttu-id="c1da9-103">Her bir kullanıcı, bir Windows Forms <xref:System.Windows.Forms.CheckBox> denetimi <xref:System.Windows.Forms.Control.Click> olayı oluşur.</span><span class="sxs-lookup"><span data-stu-id="c1da9-103">Whenever a user clicks a Windows Forms <xref:System.Windows.Forms.CheckBox> control, the <xref:System.Windows.Forms.Control.Click> event occurs.</span></span> <span data-ttu-id="c1da9-104">Onay kutusunun durumunu bağlı olarak bazı eylemleri gerçekleştirmek için uygulamanızın programlama yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c1da9-104">You can program your application to perform some action depending upon the state of the check box.</span></span>  
  
### <a name="to-respond-to-checkbox-clicks"></a><span data-ttu-id="c1da9-105">CheckBox tıklamalarına yanıt verme için</span><span class="sxs-lookup"><span data-stu-id="c1da9-105">To respond to CheckBox clicks</span></span>  
  
1.  <span data-ttu-id="c1da9-106">İçinde <xref:System.Windows.Forms.Control.Click> olay işleyicisi, kullanım <xref:System.Windows.Forms.CheckBox.Checked%2A> denetimin durumunu belirlemek ve gerekli herhangi bir eylemi gerçekleştirmek için özellik.</span><span class="sxs-lookup"><span data-stu-id="c1da9-106">In the <xref:System.Windows.Forms.Control.Click> event handler, use the <xref:System.Windows.Forms.CheckBox.Checked%2A> property to determine the control's state, and perform any necessary action.</span></span>  
  
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
    >  <span data-ttu-id="c1da9-107">Kullanıcı çift çalışırsa <xref:System.Windows.Forms.CheckBox> denetim, her tıklatma ayrı ayrı işlenir; Bu, <xref:System.Windows.Forms.CheckBox> denetimi çift olay desteklemez.</span><span class="sxs-lookup"><span data-stu-id="c1da9-107">If the user attempts to double-click the <xref:System.Windows.Forms.CheckBox> control, each click will be processed separately; that is, the <xref:System.Windows.Forms.CheckBox> control does not support the double-click event.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c1da9-108">Zaman <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> özelliği `true` (varsayılan), <xref:System.Windows.Forms.CheckBox> otomatik olarak seçilir veya tıklandığında temizlenir.</span><span class="sxs-lookup"><span data-stu-id="c1da9-108">When the <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> property is `true` (the default), the <xref:System.Windows.Forms.CheckBox> is automatically selected or cleared when it is clicked.</span></span> <span data-ttu-id="c1da9-109">Aksi takdirde, el ile ayarlamanız gerekir <xref:System.Windows.Forms.CheckBox.Checked%2A> özelliği zaman <xref:System.Windows.Forms.Control.Click> olayı oluşur.</span><span class="sxs-lookup"><span data-stu-id="c1da9-109">Otherwise, you must manually set the <xref:System.Windows.Forms.CheckBox.Checked%2A> property when the <xref:System.Windows.Forms.Control.Click> event occurs.</span></span>  
  
     <span data-ttu-id="c1da9-110">Aynı zamanda <xref:System.Windows.Forms.CheckBox> bir eylem gerektiğini belirlemek için denetim.</span><span class="sxs-lookup"><span data-stu-id="c1da9-110">You can also use the <xref:System.Windows.Forms.CheckBox> control to determine a course of action.</span></span>  
  
### <a name="to-determine-a-course-of-action-when-a-check-box-is-clicked"></a><span data-ttu-id="c1da9-111">Bir eylem bir onay kutusu seçildiğinde gerektiğini belirlemek için tıklattığınız</span><span class="sxs-lookup"><span data-stu-id="c1da9-111">To determine a course of action when a check box is clicked</span></span>  
  
1.  <span data-ttu-id="c1da9-112">Değerini sorgulamak için case deyimi kullanın <xref:System.Windows.Forms.CheckBox.CheckState%2A> bir eylem gerektiğini belirlemek için özellik.</span><span class="sxs-lookup"><span data-stu-id="c1da9-112">Use a case statement to query the value of the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property to determine a course of action.</span></span> <span data-ttu-id="c1da9-113">Zaman <xref:System.Windows.Forms.CheckBox.ThreeState%2A> özelliği ayarlanmış `true`, <xref:System.Windows.Forms.CheckBox.CheckState%2A> özellik, denetlenen kutusunu temsil, üç olası değerler döndürebilir kutusu görüntülenir kutusunun işaretlenmemiş olması ya da üçüncü belirlenmemiş bir durum ile bir devre dışı görünüm seçeneği belirtmek için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="c1da9-113">When the <xref:System.Windows.Forms.CheckBox.ThreeState%2A> property is set to `true`, the <xref:System.Windows.Forms.CheckBox.CheckState%2A> property may return three possible values, which represent the box being checked, the box being unchecked, or a third indeterminate state in which the box is displayed with a dimmed appearance to indicate the option is unavailable.</span></span>  
  
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
    >  <span data-ttu-id="c1da9-114">Zaman <xref:System.Windows.Forms.CheckBox.ThreeState%2A> özelliği ayarlanmış `true`, <xref:System.Windows.Forms.CheckBox.Checked%2A> özelliği döndürür `true` her ikisi için de <xref:System.Windows.Forms.CheckState.Checked> ve <xref:System.Windows.Forms.CheckState.Indeterminate>.</span><span class="sxs-lookup"><span data-stu-id="c1da9-114">When the <xref:System.Windows.Forms.CheckBox.ThreeState%2A> property is set to `true`, the <xref:System.Windows.Forms.CheckBox.Checked%2A> property returns `true` for both <xref:System.Windows.Forms.CheckState.Checked> and <xref:System.Windows.Forms.CheckState.Indeterminate>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1da9-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c1da9-115">See Also</span></span>  
 <xref:System.Windows.Forms.CheckBox>  
 [<span data-ttu-id="c1da9-116">CheckBox Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c1da9-116">CheckBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/checkbox-control-overview-windows-forms.md)  
 [<span data-ttu-id="c1da9-117">Nasıl yapılır: Windows Forms CheckBox Denetimleriyle Seçenekleri Ayarlama</span><span class="sxs-lookup"><span data-stu-id="c1da9-117">How to: Set Options with Windows Forms CheckBox Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-set-options-with-windows-forms-checkbox-controls.md)  
 [<span data-ttu-id="c1da9-118">CheckBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="c1da9-118">CheckBox Control</span></span>](../../../../docs/framework/winforms/controls/checkbox-control-windows-forms.md)
