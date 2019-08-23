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
ms.openlocfilehash: 7ff6b2aad9ef0775547af57f11af28839e69637c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914975"
---
# <a name="how-to-respond-to-windows-forms-checkbox-clicks"></a>Nasıl yapılır: Windows Forms CheckBox Tıklamalarına Yanıt Verme
Kullanıcı Windows Forms <xref:System.Windows.Forms.CheckBox> denetimine <xref:System.Windows.Forms.Control.Click> tıkladığında olay oluşur. Onay kutusunun durumuna bağlı olarak, uygulamanızı bazı eylemler gerçekleştirecek şekilde programlayabilirsiniz.  
  
### <a name="to-respond-to-checkbox-clicks"></a>Onay kutusu tıklamalarına yanıt vermek için  
  
1. Olay işleyicisinde, denetimin durumunu öğrenmek için <xref:System.Windows.Forms.CheckBox.Checked%2A> özelliğini kullanın ve gerekli tüm eylemleri gerçekleştirin. <xref:System.Windows.Forms.Control.Click>  
  
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
    > Kullanıcı <xref:System.Windows.Forms.CheckBox> denetime çift tıkladenerse, her tıklama ayrı olarak işlenir; diğer bir deyişle <xref:System.Windows.Forms.CheckBox> , denetim çift tıklama olayını desteklemez.  
  
    > [!NOTE]
    > Özellik (varsayılan )<xref:System.Windows.Forms.CheckBox> olduğunda, tıklandığında otomatik olarak seçilir veya temizlenir. `true` <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> Aksi takdirde, <xref:System.Windows.Forms.CheckBox.Checked%2A> <xref:System.Windows.Forms.Control.Click> olay gerçekleştiğinde özelliği el ile ayarlamanız gerekir.  
  
     Ayrıca, <xref:System.Windows.Forms.CheckBox> bir eylem kursu tespit etmek için denetimi de kullanabilirsiniz.  
  
### <a name="to-determine-a-course-of-action-when-a-check-box-is-clicked"></a>Bir onay kutusu tıklandığında bir eylem kursu belirleme  
  
1. Bir eylem kursu belirleme <xref:System.Windows.Forms.CheckBox.CheckState%2A> özelliğinin değerini sorgulamak için Case ifadesini kullanın. Özelliği olarak `true`ayarlandığında ,<xref:System.Windows.Forms.CheckBox.CheckState%2A> özelliği denetlenen kutuyu, işaretlenmekte olan kutuyu veya kutunun soluk olarak görüntülendiği üçüncü bir belirsiz durumu temsil eden üç olası değeri döndürebilir <xref:System.Windows.Forms.CheckBox.ThreeState%2A> seçeneğin kullanılamadığını belirten görünüm.  
  
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
    > <xref:System.Windows.Forms.CheckBox.ThreeState%2A> Özelliği olarak `true`ayarlandığında, <xref:System.Windows.Forms.CheckBox.Checked%2A> özelliği hem hem de `true` <xref:System.Windows.Forms.CheckState.Checked> için döndürür .<xref:System.Windows.Forms.CheckState.Indeterminate>  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.CheckBox>
- [CheckBox Denetimine Genel Bakış](checkbox-control-overview-windows-forms.md)
- [Nasıl yapılır: Seçenekleri Windows Forms onay kutusu denetimleriyle ayarlama](how-to-set-options-with-windows-forms-checkbox-controls.md)
- [CheckBox Denetimi](checkbox-control-windows-forms.md)
