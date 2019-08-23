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
ms.openlocfilehash: 888228c28dce591b237be16b6a321afee0105208
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967146"
---
# <a name="how-to-disable-tab-pages"></a>Nasıl yapılır: Sekme Sayfalarını Devre Dışı Bırakma
Bazı durumlarda Windows Forms uygulamanızda bulunan verilere erişimi kısıtlamak isteyeceksiniz. Bunun bir örneği, bir sekme denetiminin sekme sayfalarında görüntülenecek verileriniz olabilir. Yöneticiler, Konuk veya alt düzey kullanıcılardan kısıtlamak istediğiniz bir sekme sayfası hakkında bilgi sağlayabilir.  
  
### <a name="to-disable-tab-pages-programmatically"></a>Sekme sayfalarını programlı olarak devre dışı bırakmak için  
  
1. Sekme denetiminin <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> olayını işlemek için kod yazın. Bu, Kullanıcı bir sekmeden sonrakine geçtiğinde oluşturulan olaydır.  
  
2. Kimlik bilgilerini denetleyin. Sunulan bilgilere bağlı olarak, kullanıcının sekmeyi görüntülemesine izin vermeden önce kullanıcının oturum açtığı Kullanıcı adını veya başka bir kimlik bilgileri biçimini denetlemek isteyebilirsiniz.  
  
3. Kullanıcının uygun kimlik bilgileri varsa, tıklanan sekmeyi görüntüleyin. Kullanıcı uygun kimlik bilgilerine sahip değilse, bir ileti kutusu veya erişimleri olmadığını belirten başka bir kullanıcı arabirimi görüntüleyin ve ilk sekmesine geri dönün.  
  
    > [!NOTE]
    > Bu işlevselliği üretim uygulamalarınızda uyguladığınızda, formun <xref:System.Windows.Forms.Form.Load> olayında bu kimlik bilgisi denetimini gerçekleştirebilirsiniz. Bu, programlama için çok daha temiz bir yaklaşım olan herhangi bir kullanıcı arabirimi gösterilmeden önce sekmeyi gizlemenizi sağlar. Aşağıda kullanılan metodolojide ( <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> olay sırasında, kimlik bilgilerinin denetlenmesi ve sekmenin devre dışı bırakılması) tanım amaçlıdır.  
  
4. İsteğe bağlı olarak, ikiden fazla sekme sayfanız varsa orijinalden farklı bir sekme sayfası görüntüleyin.  
  
     Aşağıdaki örnekte, sekmeye erişim ölçütleri <xref:System.Windows.Forms.CheckBox> uygulamaya göre farklılık gösterebileceğinden, kimlik bilgilerini denetlemek yerine bir denetim kullanılır. Olay ortaya çıktığında, kimlik bilgisi denetimi true ise (yani, onay kutusu işaretliyse) ve seçili sekme (gizli bilgilerin bulunduğu sekme) `TabPage2` ise `TabPage2` görüntülenir. <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> Aksi takdirde `TabPage3` , görüntülenir ve kullanıcıya uygun erişim ayrıcalıklarına sahip olmadığını belirten bir ileti kutusu gösterilir. Aşağıdaki kod, <xref:System.Windows.Forms.CheckBox> denetimi (`CredentialCheck`) ve <xref:System.Windows.Forms.TabControl> üç sekme sayfası olan bir denetimi olan bir formu varsayar.  
  
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
  
     (Görsel C#, görsel C++) Olay işleyicisini kaydetmek için formun oluşturucusuna aşağıdaki kodu yerleştirin.  
  
    ```csharp  
    this.tabControl1.SelectedIndexChanged +=   
       new System.EventHandler(this.tabControl1_SelectedIndexChanged);  
    ```  
  
    ```cpp  
    this->tabControl1->SelectedIndexChanged +=  
       gcnew System::EventHandler(this, &Form1::tabControl1_SelectedIndexChanged);  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [TabControl Denetimine Genel Bakış](tabcontrol-control-overview-windows-forms.md)
- [Nasıl yapılır: Sekme sayfasına denetim ekleme](how-to-add-a-control-to-a-tab-page.md)
- [Nasıl yapılır: Windows Forms TabControl ile sekme ekleme ve kaldırma](how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
- [Nasıl yapılır: Windows Forms TabControl görünümünü değiştirme](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
