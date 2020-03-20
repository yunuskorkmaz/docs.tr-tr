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
# <a name="how-to-respond-to-windows-forms-checkbox-clicks"></a>Nasıl yapılır: Windows Forms CheckBox Tıklamalarına Yanıt Verme
Bir kullanıcı Windows Forms <xref:System.Windows.Forms.CheckBox> denetimini <xref:System.Windows.Forms.Control.Click> tıklattığında, olay oluşur. Başvurunuzu, onay kutusunun durumuna bağlı olarak bazı eylemler gerçekleştirecek şekilde programlayabilirsiniz.  
  
### <a name="to-respond-to-checkbox-clicks"></a>CheckBox tıklamalarına yanıt vermek için  
  
1. Olay <xref:System.Windows.Forms.Control.Click> işleyicisi, <xref:System.Windows.Forms.CheckBox.Checked%2A> denetimdurumunu belirlemek için özelliği kullanın ve gerekli eylemi gerçekleştirin.  
  
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
    > Kullanıcı <xref:System.Windows.Forms.CheckBox> denetimi çift tıklatmaya çalışırsa, her tıklama ayrı ayrı işlenir; diğer bir <xref:System.Windows.Forms.CheckBox> diğer olarak, denetim çift tıklatma olayını desteklemez.  
  
    > [!NOTE]
    > <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> Özellik (varsayılan) olduğunda, `true` <xref:System.Windows.Forms.CheckBox> tıklatıldığında otomatik olarak seçilir veya temizlenir. Aksi takdirde, <xref:System.Windows.Forms.CheckBox.Checked%2A> <xref:System.Windows.Forms.Control.Click> olay gerçekleştiğinde özelliği el ile ayarlamanız gerekir.  
  
     Denetimi <xref:System.Windows.Forms.CheckBox> bir eylem rotasını belirlemek için de kullanabilirsiniz.  
  
### <a name="to-determine-a-course-of-action-when-a-check-box-is-clicked"></a>Onay kutusu tıklatıldığında eylem rotasını belirlemek için  
  
1. Bir eylem kursunu belirlemek için <xref:System.Windows.Forms.CheckBox.CheckState%2A> özelliğin değerini sorgulamak için bir servis talebi deyimi kullanın. <xref:System.Windows.Forms.CheckBox.ThreeState%2A> Özellik `true`ayarlandığında, <xref:System.Windows.Forms.CheckBox.CheckState%2A> özellik işaretlenen kutuyu temsil eden üç olası değer, işaretlenmemiş kutuyu veya seçeneğin kullanılmayabileceğini belirtmek için kutunun soluk bir görünümle görüntülendiği üçüncü bir belirsiz durumu döndürebilir.  
  
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
    > <xref:System.Windows.Forms.CheckBox.ThreeState%2A> `true`Özellik ayarlandığında, <xref:System.Windows.Forms.CheckBox.Checked%2A> özellik hem `true` de <xref:System.Windows.Forms.CheckState.Checked> . <xref:System.Windows.Forms.CheckState.Indeterminate>  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.CheckBox>
- [CheckBox Denetimine Genel Bakış](checkbox-control-overview-windows-forms.md)
- [Nasıl yapılır: Windows Forms CheckBox Denetimleriyle Seçenekleri Ayarlama](how-to-set-options-with-windows-forms-checkbox-controls.md)
- [CheckBox Denetimi](checkbox-control-windows-forms.md)
