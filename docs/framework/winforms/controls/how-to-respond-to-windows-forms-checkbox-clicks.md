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
# <a name="how-to-respond-to-windows-forms-checkbox-clicks"></a>Nasıl yapılır: Windows Forms CheckBox Tıklamalarına Yanıt Verme
Kullanıcı Windows Forms <xref:System.Windows.Forms.CheckBox> denetimine tıkladığında <xref:System.Windows.Forms.Control.Click> olay oluşur. Onay kutusunun durumuna bağlı olarak, uygulamanızı bazı eylemler gerçekleştirecek şekilde programlayabilirsiniz.  
  
### <a name="to-respond-to-checkbox-clicks"></a>Onay kutusu tıklamalarına yanıt vermek için  
  
1. <xref:System.Windows.Forms.Control.Click> olay işleyicisinde, denetimin durumunu öğrenmek için <xref:System.Windows.Forms.CheckBox.Checked%2A> özelliğini kullanın ve gerekli tüm eylemleri gerçekleştirin.  
  
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
    > Kullanıcı <xref:System.Windows.Forms.CheckBox> denetimine çift tıkladenerse, her tıklama ayrı olarak işlenir; diğer bir deyişle, <xref:System.Windows.Forms.CheckBox> denetimi çift tıklama olayını desteklemez.  
  
    > [!NOTE]
    > <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> özelliği `true` (varsayılan), tıklandığında <xref:System.Windows.Forms.CheckBox> otomatik olarak seçilir veya temizlenir. Aksi takdirde, <xref:System.Windows.Forms.Control.Click> olayı gerçekleştiğinde <xref:System.Windows.Forms.CheckBox.Checked%2A> özelliğini el ile ayarlamanız gerekir.  
  
     <xref:System.Windows.Forms.CheckBox> denetimini Ayrıca bir eylem kursu tespit etmek için de kullanabilirsiniz.  
  
### <a name="to-determine-a-course-of-action-when-a-check-box-is-clicked"></a>Bir onay kutusu tıklandığında bir eylem kursu belirleme  
  
1. Bir eylem kursu belirleme <xref:System.Windows.Forms.CheckBox.CheckState%2A> özelliğinin değerini sorgulamak için Case ifadesini kullanın. <xref:System.Windows.Forms.CheckBox.ThreeState%2A> özelliği `true`olarak ayarlandığında, <xref:System.Windows.Forms.CheckBox.CheckState%2A> özelliği denetlenen kutuyu temsil eden üç olası değeri, işaretlenmekte olan kutuyu veya seçeneğin kullanılamaz olduğunu göstermek için kutunun soluk bir görünümle birlikte görüntüleneceği üçüncü bir belirsiz durumu döndürebilir.  
  
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
    > <xref:System.Windows.Forms.CheckBox.ThreeState%2A> özelliği `true`olarak ayarlandığında <xref:System.Windows.Forms.CheckBox.Checked%2A> özelliği hem <xref:System.Windows.Forms.CheckState.Checked> hem de <xref:System.Windows.Forms.CheckState.Indeterminate>için `true` döndürür.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.CheckBox>
- [CheckBox Denetimine Genel Bakış](checkbox-control-overview-windows-forms.md)
- [Nasıl yapılır: Windows Forms CheckBox Denetimleriyle Seçenekleri Ayarlama](how-to-set-options-with-windows-forms-checkbox-controls.md)
- [CheckBox Denetimi](checkbox-control-windows-forms.md)
