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
ms.openlocfilehash: 21592fdd74c43d40310e0fcbc96af6565a42e08b
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59336076"
---
# <a name="how-to-disable-tab-pages"></a>Nasıl yapılır: Sekme Sayfalarını Devre Dışı Bırakma
Bazı durumlarda, Windows Forms uygulamanızın içinden kullanılabilir verilere erişimi kısıtlamak isteyebilirsiniz. Sekme denetimi sekmesi sayfalarında görüntülenen verileri varsa, bunun bir örneği olabilir; Yöneticiler, konuk veya alt düzey kullanıcılardan kısıtlamak istiyorsanız bir sekme sayfası hakkında bilgi olabilir.  
  
### <a name="to-disable-tab-pages-programmatically"></a>Program aracılığıyla sekme sayfalarını devre dışı bırakmak için  
  
1. Sekme denetim işlemek için kod yazma <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> olay. Kullanıcı sekmeden diğerine geçtiğinde başlatan olay budur.  
  
2. Kimlik bilgilerini denetleyin. Sunulan bilgilere bağlı olarak, sekmesini görüntülemek kullanıcı izin vermeden önce kullanıcı ile oturum açmış kullanıcı adı veya diğer türde bir kimlik bilgileri denetlemek isteyebilirsiniz.  
  
3. Kullanıcı kimlik bilgilerinin doğru olduğundan, tıklandığını sekmeyi görüntüler. Kullanıcı uygun kimlik bilgilerine sahip değilse, bir ileti kutusu görüntülemek veya gösteren başka bir kullanıcı arabirimi olmayan erişimi ve ilk sekmesine geri dönün.  
  
    > [!NOTE]
    >  Üretim uygulamalarınızı bu işlevselliği uygulamak, formun sırasında bu kimlik bilgisi denetimi gerçekleştirebilir <xref:System.Windows.Forms.Form.Load> olay. Bu, bir çok daha net yaklaşım programlamaya olduğu herhangi bir kullanıcı arabirimi gösterilmeden önce sekmesini gizlemek olanak tanır. Aşağıda kullanılan metodolojiyi (kimlik denetimi ve sekme sırasında devre dışı bırakma <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> olay) yalnızca tanım amaçlıdır.  
  
4. İkiden fazla sekme sayfaları varsa, isteğe bağlı olarak orijinal olandan arklı bir sekme sayfası görüntüler.  
  
     Aşağıdaki örnekte bir <xref:System.Windows.Forms.CheckBox> denetimi, uygulama tarafından erişim için sekmesinde değişir için kimlik bilgileri ölçüt olarak denetimi yerine kullanılır. Zaman <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> olayı oluşturulur, kimlik bilgisi onay true ise (diğer bir deyişle, onay kutusu işaretliyse) ve seçili `TabPage2` (Bu örnekte, gizli bilgilerle sekme), ardından `TabPage2` görüntülenir. Aksi takdirde, `TabPage3` görüntülenir ve bunlar yoktu uygun erişim ayrıcalıkları belirten kullanıcıya bir ileti kutusu gösterilir. Aşağıdaki kod bir formla varsayar bir <xref:System.Windows.Forms.CheckBox> denetimi (`CredentialCheck`) ve bir <xref:System.Windows.Forms.TabControl> üç sekme sayfaları denetimi.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [TabControl Denetimine Genel Bakış](tabcontrol-control-overview-windows-forms.md)
- [Nasıl yapılır: Sekme Sayfasına Denetim Ekleme](how-to-add-a-control-to-a-tab-page.md)
- [Nasıl yapılır: Windows Forms TabControl ile Sekme Ekleme ve Kaldırma](how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
- [Nasıl yapılır: Windows Forms TabControl Görünümünü Değiştirme](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
