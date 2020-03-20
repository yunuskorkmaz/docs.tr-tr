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
ms.openlocfilehash: 9074aedb81a485267dc4faff92e0fe8d0d3b467f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182168"
---
# <a name="how-to-disable-tab-pages"></a>Nasıl yapılır: Sekme Sayfalarını Devre Dışı Bırakma
Bazı durumlarda, Windows Forms uygulamanızda bulunan verilere erişimi kısıtlamak isteyebilirsiniz. Bunun bir örneği, sekme denetiminin sekme sayfalarında görüntülenen veriler olduğunda olabilir; yöneticilerin bir sekme sayfasında konuk veya alt düzey kullanıcılardan kısıtlamak isteyeceğiniz bilgilere sahip olabilir.  
  
### <a name="to-disable-tab-pages-programmatically"></a>Sekme sayfalarını programlı olarak devre dışı atmak için  
  
1. Sekme denetiminin <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> olayını işlemek için kod yazın. Bu, kullanıcı bir sekmeden diğerine geçtiğinde ortaya çıkan olaydır.  
  
2. Kimlik bilgilerini kontrol edin. Sunulan bilgilere bağlı olarak, kullanıcının sekmeyi görüntülemesine izin vermeden önce kullanıcının oturum açtığı kullanıcı adını veya başka bir kimlik bilgisi formunu denetlemek isteyebilirsiniz.  
  
3. Kullanıcının uygun kimlik bilgileri varsa, tıklanan sekmeyi görüntüleyin. Kullanıcının uygun kimlik bilgileri yoksa, erişimi olmadığını belirten bir ileti kutusu veya başka bir kullanıcı arabirimi görüntüleyin ve ilk sekmeye dönün.  
  
    > [!NOTE]
    > Bu işlevselliği üretim uygulamalarınızda uyguladığınızda, formun <xref:System.Windows.Forms.Form.Load> olayı sırasında bu kimlik bilgisi denetimini gerçekleştirebilirsiniz. Bu, programlamaya çok daha temiz bir yaklaşım olan herhangi bir kullanıcı arabirimi gösterilmeden önce sekmeyi gizlemenize olanak tanır. Aşağıda kullanılan metodoloji (kimlik bilgilerini denetlemek ve <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> olay sırasında sekmeyi devre dışı bırakmak) açıklayıcı amaçlar içindir.  
  
4. İsteğe bağlı olarak, ikiden fazla sekme sayfanız varsa, orijinalinden farklı bir sekme sayfası görüntüleyin.  
  
     Aşağıdaki örnekte, <xref:System.Windows.Forms.CheckBox> sekmeye erişim ölçütleri uygulamaya göre değişeceği için kimlik bilgilerini denetlemek yerine bir denetim kullanılır. <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> Olay yükseltildiğinde, kimlik bilgisi denetimi doğruysa (diğer bir deyişle, onay kutusu işaretlenir) ve `TabPage2` seçili sekme (bu örnekte `TabPage2` gizli bilgilerin yer alan sekmesi) görüntülenir. Aksi `TabPage3` takdirde, görüntülenir ve kullanıcıya uygun erişim ayrıcalıkları olmadığını belirten bir ileti kutusu gösterilir. Aşağıdaki kod, denetimi olan <xref:System.Windows.Forms.CheckBox> bir`CredentialCheck`form ( <xref:System.Windows.Forms.TabControl> ) ve üç sekme sayfası olan bir denetim varsayar.  
  
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
  
     (Görsel C#, Görsel C++) Olay işleyicisini kaydetmek için aşağıdaki kodu formun oluşturucusuna yerleştirin.  
  
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
- [Nasıl yapılır: Sekme Sayfasına Denetim Ekleme](how-to-add-a-control-to-a-tab-page.md)
- [Nasıl yapılır: Windows Forms TabControl' ile Sekme Ekleme ve Kaldırma](how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
- [Nasıl yapılır: Windows Forms TabControl’un Görünüşünü Değiştirme](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
