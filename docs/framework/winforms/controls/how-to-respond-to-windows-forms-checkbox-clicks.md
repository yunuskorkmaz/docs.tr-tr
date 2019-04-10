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
ms.openlocfilehash: 77f93dae2a91f282c6746c3fec3fb5f567cae2e3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59211991"
---
# <a name="how-to-respond-to-windows-forms-checkbox-clicks"></a>Nasıl yapılır: Windows Forms CheckBox Tıklamalarına Yanıt Verme
Her bir kullanıcı bir Windows Forms tıkladığında <xref:System.Windows.Forms.CheckBox> denetimi <xref:System.Windows.Forms.Control.Click> olayı oluşur. Onay kutusunun durumunu olarak bazı eylemleri gerçekleştirmek için uygulamanızı programlayabilirsiniz.  
  
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
    >  Kullanıcının çift çalışırsa <xref:System.Windows.Forms.CheckBox> denetimi her tıklatma ayrı ayrı işlenir; diğer bir deyişle, <xref:System.Windows.Forms.CheckBox> denetimi çift olay desteklemez.  
  
    > [!NOTE]
    >  Zaman <xref:System.Windows.Forms.CheckBox.AutoCheck%2A> özelliği `true` (varsayılan), <xref:System.Windows.Forms.CheckBox> otomatik olarak seçilir veya tıklandığında temizlenir. Aksi takdirde, el ile ayarlamanız gerekir <xref:System.Windows.Forms.CheckBox.Checked%2A> özelliği olduğunda <xref:System.Windows.Forms.Control.Click> olayı oluşur.  
  
     Ayrıca <xref:System.Windows.Forms.CheckBox> denetim bir eylemi belirlemek için.  
  
### <a name="to-determine-a-course-of-action-when-a-check-box-is-clicked"></a>Bir eylemi bir onay kutusu seçildiğinde belirlemek için tıklandı  
  
1.  Case deyimi değerini sorgulamanıza <xref:System.Windows.Forms.CheckBox.CheckState%2A> özelliğini bir eyleme belirlemek için. Zaman <xref:System.Windows.Forms.CheckBox.ThreeState%2A> özelliği `true`, <xref:System.Windows.Forms.CheckBox.CheckState%2A> özelliği, kutunun denetlenen temsil eder ve üç olası değer döndürebilir kutusu görüntülenir kutusu denetlenmeyen durdurulmasını veya üçüncü belirlenmemiş duruma sahip bir devre dışı Görünüm seçeneğini belirtmek için kullanılamaz.  
  
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
    >  Zaman <xref:System.Windows.Forms.CheckBox.ThreeState%2A> özelliği `true`, <xref:System.Windows.Forms.CheckBox.Checked%2A> özelliği döndürür `true` hem <xref:System.Windows.Forms.CheckState.Checked> ve <xref:System.Windows.Forms.CheckState.Indeterminate>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.CheckBox>
- [CheckBox Denetimine Genel Bakış](checkbox-control-overview-windows-forms.md)
- [Nasıl yapılır: Windows Forms CheckBox Denetimleriyle Seçenekleri Ayarlama](how-to-set-options-with-windows-forms-checkbox-controls.md)
- [CheckBox Denetimi](checkbox-control-windows-forms.md)
