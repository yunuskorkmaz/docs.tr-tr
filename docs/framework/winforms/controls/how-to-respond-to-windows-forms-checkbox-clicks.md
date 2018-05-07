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
ms.openlocfilehash: aa8a15d4f55fb1dd47fdf004fa05091ec88fe03e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-respond-to-windows-forms-checkbox-clicks"></a>Nasıl yapılır: Windows Forms CheckBox Tıklamalarına Yanıt Verme
Her bir kullanıcı, bir Windows Forms <xref:System.Windows.Forms.CheckBox> denetimi <xref:System.Windows.Forms.Control.Click> olayı oluşur. Onay kutusunun durumunu bağlı olarak bazı eylemleri gerçekleştirmek için uygulamanızın programlama yapabilirsiniz.  
  
### <a name="to-respond-to-checkbox-clicks"></a>CheckBox tıklamalarına yanıt verme için  
  
1.  İçinde <xref:System.Windows.Forms.Control.Click> olay işleyicisi, kullanım <xref:System.Windows.Forms.CheckBox.Checked%2A> denetimin durumunu belirlemek ve gerekli herhangi bir eylemi gerçekleştirmek için özellik.  
  
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
    >  Kullanıcı çift çalışırsa <xref:System.Windows.Forms.CheckBox> denetim, her tıklatma ayrı ayrı işlenir; Bu, <xref:System.Windows.Forms.CheckBox> denetimi çift olay desteklemez.  
  
    > [!NOTE]
    >  Zaman <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> özelliği `true` (varsayılan), <xref:System.Windows.Forms.CheckBox> otomatik olarak seçilir veya tıklandığında temizlenir. Aksi takdirde, el ile ayarlamanız gerekir <xref:System.Windows.Forms.CheckBox.Checked%2A> özelliği zaman <xref:System.Windows.Forms.Control.Click> olayı oluşur.  
  
     Aynı zamanda <xref:System.Windows.Forms.CheckBox> bir eylem gerektiğini belirlemek için denetim.  
  
### <a name="to-determine-a-course-of-action-when-a-check-box-is-clicked"></a>Bir eylem bir onay kutusu seçildiğinde gerektiğini belirlemek için tıklattığınız  
  
1.  Değerini sorgulamak için case deyimi kullanın <xref:System.Windows.Forms.CheckBox.CheckState%2A> bir eylem gerektiğini belirlemek için özellik. Zaman <xref:System.Windows.Forms.CheckBox.ThreeState%2A> özelliği ayarlanmış `true`, <xref:System.Windows.Forms.CheckBox.CheckState%2A> özellik, denetlenen kutusunu temsil, üç olası değerler döndürebilir kutusu görüntülenir kutusunun işaretlenmemiş olması ya da üçüncü belirlenmemiş bir durum ile bir devre dışı görünüm seçeneği belirtmek için kullanılamaz.  
  
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
    >  Zaman <xref:System.Windows.Forms.CheckBox.ThreeState%2A> özelliği ayarlanmış `true`, <xref:System.Windows.Forms.CheckBox.Checked%2A> özelliği döndürür `true` her ikisi için de <xref:System.Windows.Forms.CheckState.Checked> ve <xref:System.Windows.Forms.CheckState.Indeterminate>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.CheckBox>  
 [CheckBox Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/checkbox-control-overview-windows-forms.md)  
 [Nasıl yapılır: Windows Forms CheckBox Denetimleriyle Seçenekleri Ayarlama](../../../../docs/framework/winforms/controls/how-to-set-options-with-windows-forms-checkbox-controls.md)  
 [CheckBox Denetimi](../../../../docs/framework/winforms/controls/checkbox-control-windows-forms.md)
