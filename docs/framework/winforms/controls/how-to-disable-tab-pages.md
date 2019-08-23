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
# <a name="how-to-disable-tab-pages"></a><span data-ttu-id="b1bd6-102">Nasıl yapılır: Sekme Sayfalarını Devre Dışı Bırakma</span><span class="sxs-lookup"><span data-stu-id="b1bd6-102">How to: Disable Tab Pages</span></span>
<span data-ttu-id="b1bd6-103">Bazı durumlarda Windows Forms uygulamanızda bulunan verilere erişimi kısıtlamak isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="b1bd6-103">On some occasions, you will want to restrict access to data that is available within your Windows Forms application.</span></span> <span data-ttu-id="b1bd6-104">Bunun bir örneği, bir sekme denetiminin sekme sayfalarında görüntülenecek verileriniz olabilir. Yöneticiler, Konuk veya alt düzey kullanıcılardan kısıtlamak istediğiniz bir sekme sayfası hakkında bilgi sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="b1bd6-104">One example of this might be when you have data displayed in the tab pages of a tab control; administrators could have information on a tab page that you would want to restrict from guest or lower-level users.</span></span>  
  
### <a name="to-disable-tab-pages-programmatically"></a><span data-ttu-id="b1bd6-105">Sekme sayfalarını programlı olarak devre dışı bırakmak için</span><span class="sxs-lookup"><span data-stu-id="b1bd6-105">To disable tab pages programmatically</span></span>  
  
1. <span data-ttu-id="b1bd6-106">Sekme denetiminin <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> olayını işlemek için kod yazın.</span><span class="sxs-lookup"><span data-stu-id="b1bd6-106">Write code to handle the tab control's <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> event.</span></span> <span data-ttu-id="b1bd6-107">Bu, Kullanıcı bir sekmeden sonrakine geçtiğinde oluşturulan olaydır.</span><span class="sxs-lookup"><span data-stu-id="b1bd6-107">This is the event that is raised when the user switches from one tab to the next.</span></span>  
  
2. <span data-ttu-id="b1bd6-108">Kimlik bilgilerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="b1bd6-108">Check credentials.</span></span> <span data-ttu-id="b1bd6-109">Sunulan bilgilere bağlı olarak, kullanıcının sekmeyi görüntülemesine izin vermeden önce kullanıcının oturum açtığı Kullanıcı adını veya başka bir kimlik bilgileri biçimini denetlemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b1bd6-109">Depending upon the information presented, you may want to check the user name the user has logged in with or some other form of credentials before allowing the user to view the tab.</span></span>  
  
3. <span data-ttu-id="b1bd6-110">Kullanıcının uygun kimlik bilgileri varsa, tıklanan sekmeyi görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="b1bd6-110">If the user has appropriate credentials, display the tab that was clicked.</span></span> <span data-ttu-id="b1bd6-111">Kullanıcı uygun kimlik bilgilerine sahip değilse, bir ileti kutusu veya erişimleri olmadığını belirten başka bir kullanıcı arabirimi görüntüleyin ve ilk sekmesine geri dönün.</span><span class="sxs-lookup"><span data-stu-id="b1bd6-111">If the user does not have appropriate credentials, display a message box or some other user interface indicating that they do not have access, and return to the initial tab.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="b1bd6-112">Bu işlevselliği üretim uygulamalarınızda uyguladığınızda, formun <xref:System.Windows.Forms.Form.Load> olayında bu kimlik bilgisi denetimini gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b1bd6-112">When you implement this functionality in your production applications, you can perform this credential check during the form's <xref:System.Windows.Forms.Form.Load> event.</span></span> <span data-ttu-id="b1bd6-113">Bu, programlama için çok daha temiz bir yaklaşım olan herhangi bir kullanıcı arabirimi gösterilmeden önce sekmeyi gizlemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="b1bd6-113">This will allow you to hide the tab before any user interface is shown, which is a much cleaner approach to programming.</span></span> <span data-ttu-id="b1bd6-114">Aşağıda kullanılan metodolojide ( <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> olay sırasında, kimlik bilgilerinin denetlenmesi ve sekmenin devre dışı bırakılması) tanım amaçlıdır.</span><span class="sxs-lookup"><span data-stu-id="b1bd6-114">The methodology used below (checking credentials and disabling the tab during the <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> event) is for illustrative purposes.</span></span>  
  
4. <span data-ttu-id="b1bd6-115">İsteğe bağlı olarak, ikiden fazla sekme sayfanız varsa orijinalden farklı bir sekme sayfası görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="b1bd6-115">Optionally, if you have more than two tab pages, display a tab page different from the original.</span></span>  
  
     <span data-ttu-id="b1bd6-116">Aşağıdaki örnekte, sekmeye erişim ölçütleri <xref:System.Windows.Forms.CheckBox> uygulamaya göre farklılık gösterebileceğinden, kimlik bilgilerini denetlemek yerine bir denetim kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b1bd6-116">In the example below, a <xref:System.Windows.Forms.CheckBox> control is used in lieu of checking the credentials, as the criteria for access to the tab will vary by application.</span></span> <span data-ttu-id="b1bd6-117">Olay ortaya çıktığında, kimlik bilgisi denetimi true ise (yani, onay kutusu işaretliyse) ve seçili sekme (gizli bilgilerin bulunduğu sekme) `TabPage2` ise `TabPage2` görüntülenir. <xref:System.Windows.Forms.TabControl.SelectedIndexChanged></span><span class="sxs-lookup"><span data-stu-id="b1bd6-117">When the <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> event is raised, if the credential check is true (that is, the check box is checked) and the selected tab is `TabPage2` (the tab with the confidential information, in this example), then `TabPage2` is displayed.</span></span> <span data-ttu-id="b1bd6-118">Aksi takdirde `TabPage3` , görüntülenir ve kullanıcıya uygun erişim ayrıcalıklarına sahip olmadığını belirten bir ileti kutusu gösterilir.</span><span class="sxs-lookup"><span data-stu-id="b1bd6-118">Otherwise, `TabPage3` is displayed and a message box is shown to the user, indicating they did not have appropriate access privileges.</span></span> <span data-ttu-id="b1bd6-119">Aşağıdaki kod, <xref:System.Windows.Forms.CheckBox> denetimi (`CredentialCheck`) ve <xref:System.Windows.Forms.TabControl> üç sekme sayfası olan bir denetimi olan bir formu varsayar.</span><span class="sxs-lookup"><span data-stu-id="b1bd6-119">The code below assumes a form with a <xref:System.Windows.Forms.CheckBox> control (`CredentialCheck`) and a <xref:System.Windows.Forms.TabControl> control with three tab pages.</span></span>  
  
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
  
     <span data-ttu-id="b1bd6-120">(Görsel C#, görsel C++) Olay işleyicisini kaydetmek için formun oluşturucusuna aşağıdaki kodu yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="b1bd6-120">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.tabControl1.SelectedIndexChanged +=   
       new System.EventHandler(this.tabControl1_SelectedIndexChanged);  
    ```  
  
    ```cpp  
    this->tabControl1->SelectedIndexChanged +=  
       gcnew System::EventHandler(this, &Form1::tabControl1_SelectedIndexChanged);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="b1bd6-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b1bd6-121">See also</span></span>

- [<span data-ttu-id="b1bd6-122">TabControl Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b1bd6-122">TabControl Control Overview</span></span>](tabcontrol-control-overview-windows-forms.md)
- [<span data-ttu-id="b1bd6-123">Nasıl yapılır: Sekme sayfasına denetim ekleme</span><span class="sxs-lookup"><span data-stu-id="b1bd6-123">How to: Add a Control to a Tab Page</span></span>](how-to-add-a-control-to-a-tab-page.md)
- [<span data-ttu-id="b1bd6-124">Nasıl yapılır: Windows Forms TabControl ile sekme ekleme ve kaldırma</span><span class="sxs-lookup"><span data-stu-id="b1bd6-124">How to: Add and Remove Tabs with the Windows Forms TabControl</span></span>](how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
- [<span data-ttu-id="b1bd6-125">Nasıl yapılır: Windows Forms TabControl görünümünü değiştirme</span><span class="sxs-lookup"><span data-stu-id="b1bd6-125">How to: Change the Appearance of the Windows Forms TabControl</span></span>](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
