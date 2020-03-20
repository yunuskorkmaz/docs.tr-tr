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
# <a name="how-to-disable-tab-pages"></a><span data-ttu-id="88205-102">Nasıl yapılır: Sekme Sayfalarını Devre Dışı Bırakma</span><span class="sxs-lookup"><span data-stu-id="88205-102">How to: Disable Tab Pages</span></span>
<span data-ttu-id="88205-103">Bazı durumlarda, Windows Forms uygulamanızda bulunan verilere erişimi kısıtlamak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="88205-103">On some occasions, you will want to restrict access to data that is available within your Windows Forms application.</span></span> <span data-ttu-id="88205-104">Bunun bir örneği, sekme denetiminin sekme sayfalarında görüntülenen veriler olduğunda olabilir; yöneticilerin bir sekme sayfasında konuk veya alt düzey kullanıcılardan kısıtlamak isteyeceğiniz bilgilere sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="88205-104">One example of this might be when you have data displayed in the tab pages of a tab control; administrators could have information on a tab page that you would want to restrict from guest or lower-level users.</span></span>  
  
### <a name="to-disable-tab-pages-programmatically"></a><span data-ttu-id="88205-105">Sekme sayfalarını programlı olarak devre dışı atmak için</span><span class="sxs-lookup"><span data-stu-id="88205-105">To disable tab pages programmatically</span></span>  
  
1. <span data-ttu-id="88205-106">Sekme denetiminin <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> olayını işlemek için kod yazın.</span><span class="sxs-lookup"><span data-stu-id="88205-106">Write code to handle the tab control's <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> event.</span></span> <span data-ttu-id="88205-107">Bu, kullanıcı bir sekmeden diğerine geçtiğinde ortaya çıkan olaydır.</span><span class="sxs-lookup"><span data-stu-id="88205-107">This is the event that is raised when the user switches from one tab to the next.</span></span>  
  
2. <span data-ttu-id="88205-108">Kimlik bilgilerini kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="88205-108">Check credentials.</span></span> <span data-ttu-id="88205-109">Sunulan bilgilere bağlı olarak, kullanıcının sekmeyi görüntülemesine izin vermeden önce kullanıcının oturum açtığı kullanıcı adını veya başka bir kimlik bilgisi formunu denetlemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="88205-109">Depending upon the information presented, you may want to check the user name the user has logged in with or some other form of credentials before allowing the user to view the tab.</span></span>  
  
3. <span data-ttu-id="88205-110">Kullanıcının uygun kimlik bilgileri varsa, tıklanan sekmeyi görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="88205-110">If the user has appropriate credentials, display the tab that was clicked.</span></span> <span data-ttu-id="88205-111">Kullanıcının uygun kimlik bilgileri yoksa, erişimi olmadığını belirten bir ileti kutusu veya başka bir kullanıcı arabirimi görüntüleyin ve ilk sekmeye dönün.</span><span class="sxs-lookup"><span data-stu-id="88205-111">If the user does not have appropriate credentials, display a message box or some other user interface indicating that they do not have access, and return to the initial tab.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="88205-112">Bu işlevselliği üretim uygulamalarınızda uyguladığınızda, formun <xref:System.Windows.Forms.Form.Load> olayı sırasında bu kimlik bilgisi denetimini gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="88205-112">When you implement this functionality in your production applications, you can perform this credential check during the form's <xref:System.Windows.Forms.Form.Load> event.</span></span> <span data-ttu-id="88205-113">Bu, programlamaya çok daha temiz bir yaklaşım olan herhangi bir kullanıcı arabirimi gösterilmeden önce sekmeyi gizlemenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="88205-113">This will allow you to hide the tab before any user interface is shown, which is a much cleaner approach to programming.</span></span> <span data-ttu-id="88205-114">Aşağıda kullanılan metodoloji (kimlik bilgilerini denetlemek ve <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> olay sırasında sekmeyi devre dışı bırakmak) açıklayıcı amaçlar içindir.</span><span class="sxs-lookup"><span data-stu-id="88205-114">The methodology used below (checking credentials and disabling the tab during the <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> event) is for illustrative purposes.</span></span>  
  
4. <span data-ttu-id="88205-115">İsteğe bağlı olarak, ikiden fazla sekme sayfanız varsa, orijinalinden farklı bir sekme sayfası görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="88205-115">Optionally, if you have more than two tab pages, display a tab page different from the original.</span></span>  
  
     <span data-ttu-id="88205-116">Aşağıdaki örnekte, <xref:System.Windows.Forms.CheckBox> sekmeye erişim ölçütleri uygulamaya göre değişeceği için kimlik bilgilerini denetlemek yerine bir denetim kullanılır.</span><span class="sxs-lookup"><span data-stu-id="88205-116">In the example below, a <xref:System.Windows.Forms.CheckBox> control is used in lieu of checking the credentials, as the criteria for access to the tab will vary by application.</span></span> <span data-ttu-id="88205-117"><xref:System.Windows.Forms.TabControl.SelectedIndexChanged> Olay yükseltildiğinde, kimlik bilgisi denetimi doğruysa (diğer bir deyişle, onay kutusu işaretlenir) ve `TabPage2` seçili sekme (bu örnekte `TabPage2` gizli bilgilerin yer alan sekmesi) görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="88205-117">When the <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> event is raised, if the credential check is true (that is, the check box is checked) and the selected tab is `TabPage2` (the tab with the confidential information, in this example), then `TabPage2` is displayed.</span></span> <span data-ttu-id="88205-118">Aksi `TabPage3` takdirde, görüntülenir ve kullanıcıya uygun erişim ayrıcalıkları olmadığını belirten bir ileti kutusu gösterilir.</span><span class="sxs-lookup"><span data-stu-id="88205-118">Otherwise, `TabPage3` is displayed and a message box is shown to the user, indicating they did not have appropriate access privileges.</span></span> <span data-ttu-id="88205-119">Aşağıdaki kod, denetimi olan <xref:System.Windows.Forms.CheckBox> bir`CredentialCheck`form ( <xref:System.Windows.Forms.TabControl> ) ve üç sekme sayfası olan bir denetim varsayar.</span><span class="sxs-lookup"><span data-stu-id="88205-119">The code below assumes a form with a <xref:System.Windows.Forms.CheckBox> control (`CredentialCheck`) and a <xref:System.Windows.Forms.TabControl> control with three tab pages.</span></span>  
  
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
  
     <span data-ttu-id="88205-120">(Görsel C#, Görsel C++) Olay işleyicisini kaydetmek için aşağıdaki kodu formun oluşturucusuna yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="88205-120">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.tabControl1.SelectedIndexChanged +=
       new System.EventHandler(this.tabControl1_SelectedIndexChanged);  
    ```  
  
    ```cpp  
    this->tabControl1->SelectedIndexChanged +=  
       gcnew System::EventHandler(this, &Form1::tabControl1_SelectedIndexChanged);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="88205-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="88205-121">See also</span></span>

- [<span data-ttu-id="88205-122">TabControl Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="88205-122">TabControl Control Overview</span></span>](tabcontrol-control-overview-windows-forms.md)
- [<span data-ttu-id="88205-123">Nasıl yapılır: Sekme Sayfasına Denetim Ekleme</span><span class="sxs-lookup"><span data-stu-id="88205-123">How to: Add a Control to a Tab Page</span></span>](how-to-add-a-control-to-a-tab-page.md)
- [<span data-ttu-id="88205-124">Nasıl yapılır: Windows Forms TabControl' ile Sekme Ekleme ve Kaldırma</span><span class="sxs-lookup"><span data-stu-id="88205-124">How to: Add and Remove Tabs with the Windows Forms TabControl</span></span>](how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
- [<span data-ttu-id="88205-125">Nasıl yapılır: Windows Forms TabControl’un Görünüşünü Değiştirme</span><span class="sxs-lookup"><span data-stu-id="88205-125">How to: Change the Appearance of the Windows Forms TabControl</span></span>](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
