---
title: 'Nasıl yapılır: Sekme Sayfalarını Devre Dışı Bırakma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tab pages [Windows Forms], hiding in forms
- TabControl control [Windows Forms], disabling pages
ms.assetid: adcc6618-8a34-4ee1-bbe3-47e732de6a59
ms.openlocfilehash: 94d8522a71fcd565ae8f994d73ffe4c46fcf7ce3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-disable-tab-pages"></a>Nasıl yapılır: Sekme Sayfalarını Devre Dışı Bırakma
Bazı durumlarda, Windows Forms uygulamanızdaki kullanılabilir verilere erişimi kısıtlamak isteyeceksiniz. Sekme denetimi sekmesi sayfalarında görüntülenen verileri varsa, bunun bir örneği olabilir; Yöneticiler, konuk veya alt düzey kullanıcılara kısıtlamak istediğiniz bir sekme sayfası hakkında bilgi olabilir.  
  
### <a name="to-disable-tab-pages-programmatically"></a>Sekme sayfaları program aracılığıyla devre dışı bırakmak için  
  
1.  Sekme denetiminin işlemek için kod yazma <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> olay. Kullanıcı bir sekmeye diğerine geçtiğinde olayı budur.  
  
2.  Kimlik bilgilerini denetleyin. Sunulan bilgilerine bağlı olarak, sekmesini görüntülemek kullanıcı izin vermeden önce kullanıcı ile oturum açmış kullanıcı adı veya başka bir form kimlik bilgileri denetlemek isteyebilirsiniz.  
  
3.  Kullanıcı kimlik bilgilerinin doğru olduğundan, tıklandığını sekmesini görüntüleyin. Kullanıcı uygun kimlik bilgilerine sahip değilse, bir ileti kutusu görüntüleme veya gösteren başka bir kullanıcı arabirimi olmayan erişimi ve ilk sekmesine geri dönün.  
  
    > [!NOTE]
    >  Bu işlev, üretim uygulamalarınızı uyguladığınızda formun sırasında bu kimlik bilgisi denetimi gerçekleştirebilir <xref:System.Windows.Forms.Form.Load> olay. Bu programlama bir temizleyici kadar yaklaşım olduğu herhangi bir kullanıcı arabirimi gösterilir önce sekmesini gizle olanak sağlar. Aşağıda kullanılan yönteme (kimlik bilgileri denetleniyor ve sekme sırasında devre dışı bırakma <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> olay) yalnızca tanım amaçlıdır.  
  
4.  İkiden fazla sekme sayfaları varsa, isteğe bağlı olarak orijinal olandan farklı bir sekme sayfası görüntüler.  
  
     Aşağıdaki örnekte bir <xref:System.Windows.Forms.CheckBox> denetimi, uygulama tarafından erişim sekmesine değişir için kimlik bilgileri, ölçüt olarak denetimi yerine kullanılır. Zaman <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> olayı, kimlik bilgisi onay true ise (diğer bir deyişle, onay kutusu işaretliyse) ve seçili sekmesi `TabPage2` (Bu örnekte, gizli bilgilerle sekmesi), ardından `TabPage2` görüntülenir. Aksi takdirde `TabPage3` görüntülenir ve bunlar yoktu uygun erişim ayrıcalıkları belirten kullanıcıya bir ileti kutusu gösterilir. Aşağıdaki kod bir formla varsayar bir <xref:System.Windows.Forms.CheckBox> denetimi (`CredentialCheck`) ve bir <xref:System.Windows.Forms.TabControl> denetimi üç sekme sayfaları ile.  
  
    ```vb  
    Private Sub TabControl1_SelectedIndexChanged(ByVal sender As Object, ByVal e As System.EventArgs) Handles TabControl1.SelectedIndexChanged  
       ' Check Credentials Here  
  
       If CredentialCheck.Checked = True And _   
       TabControl1.SelectedTab Is TabPage2 Then  
          TabControl1.SelectedTab = TabPage2  
       ElseIf CredentialCheck.Checked = False _   
       And TabControl1.SelectedTab Is TabPage2 Then  
          MessageBox.Show _   
         ("Unable to load tab. You have insufficient access privileges.")  
          TabControl1.SelectedTab = TabPage3  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void tabControl1_SelectedIndexChanged(object sender, System.EventArgs e)  
    {  
        // Check Credentials Here  
  
        if ((CredentialCheck.Checked == true) && (tabControl1.SelectedTab == tabPage2))   
        {  
            tabControl1.SelectedTab = tabPage2;  
        }  
        else if ((CredentialCheck.Checked == false) && (tabControl1.SelectedTab == tabPage2))  
        {  
            MessageBox.Show("Unable to load tab. You have insufficient access privileges.");  
            tabControl1.SelectedTab = tabPage3;  
        }  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void tabControl1_SelectedIndexChanged(  
          System::Object ^ sender,  
          System::EventArgs ^  e)  
       {  
          // Check Credentials Here  
          if ((CredentialCheck->Checked == true) &&  
              (tabControl1->SelectedTab == tabPage2))  
          {  
             tabControl1->SelectedTab = tabPage2;  
          }  
          else if ((CredentialCheck->Checked == false) &&  
                   (tabControl1->SelectedTab == tabPage2))  
          {  
             MessageBox::Show(String::Concat("Unable to load tab. ",  
                "You have insufficient access privileges."));  
             tabControl1->SelectedTab = tabPage3;  
          }  
       }  
    ```  
  
     (Visual C#, Visual C++) Aşağıdaki kod, olay işleyicisi kaydetmek için formun oluşturucuda yerleştirin.  
  
    ```csharp  
    this.tabControl1.SelectedIndexChanged +=   
       new System.EventHandler(this.tabControl1_SelectedIndexChanged);  
    ```  
  
    ```cpp  
    this->tabControl1->SelectedIndexChanged +=  
       gcnew System::EventHandler(this, &Form1::tabControl1_SelectedIndexChanged);  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [TabControl Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)  
 [Nasıl yapılır: Sekme Sayfasına Denetim Ekleme](../../../../docs/framework/winforms/controls/how-to-add-a-control-to-a-tab-page.md)  
 [Nasıl yapılır: Windows Forms TabControl ile Sekme Ekleme ve Kaldırma](../../../../docs/framework/winforms/controls/how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)  
 [Nasıl yapılır: Windows Forms TabControl’un Görünüşünü Değiştirme](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
