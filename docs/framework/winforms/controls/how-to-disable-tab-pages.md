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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59336076"
---
# <a name="how-to-disable-tab-pages"></a><span data-ttu-id="41b72-102">Nasıl yapılır: Sekme Sayfalarını Devre Dışı Bırakma</span><span class="sxs-lookup"><span data-stu-id="41b72-102">How to: Disable Tab Pages</span></span>
<span data-ttu-id="41b72-103">Bazı durumlarda, Windows Forms uygulamanızın içinden kullanılabilir verilere erişimi kısıtlamak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="41b72-103">On some occasions, you will want to restrict access to data that is available within your Windows Forms application.</span></span> <span data-ttu-id="41b72-104">Sekme denetimi sekmesi sayfalarında görüntülenen verileri varsa, bunun bir örneği olabilir; Yöneticiler, konuk veya alt düzey kullanıcılardan kısıtlamak istiyorsanız bir sekme sayfası hakkında bilgi olabilir.</span><span class="sxs-lookup"><span data-stu-id="41b72-104">One example of this might be when you have data displayed in the tab pages of a tab control; administrators could have information on a tab page that you would want to restrict from guest or lower-level users.</span></span>  
  
### <a name="to-disable-tab-pages-programmatically"></a><span data-ttu-id="41b72-105">Program aracılığıyla sekme sayfalarını devre dışı bırakmak için</span><span class="sxs-lookup"><span data-stu-id="41b72-105">To disable tab pages programmatically</span></span>  
  
1. <span data-ttu-id="41b72-106">Sekme denetim işlemek için kod yazma <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> olay.</span><span class="sxs-lookup"><span data-stu-id="41b72-106">Write code to handle the tab control's <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> event.</span></span> <span data-ttu-id="41b72-107">Kullanıcı sekmeden diğerine geçtiğinde başlatan olay budur.</span><span class="sxs-lookup"><span data-stu-id="41b72-107">This is the event that is raised when the user switches from one tab to the next.</span></span>  
  
2. <span data-ttu-id="41b72-108">Kimlik bilgilerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="41b72-108">Check credentials.</span></span> <span data-ttu-id="41b72-109">Sunulan bilgilere bağlı olarak, sekmesini görüntülemek kullanıcı izin vermeden önce kullanıcı ile oturum açmış kullanıcı adı veya diğer türde bir kimlik bilgileri denetlemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="41b72-109">Depending upon the information presented, you may want to check the user name the user has logged in with or some other form of credentials before allowing the user to view the tab.</span></span>  
  
3. <span data-ttu-id="41b72-110">Kullanıcı kimlik bilgilerinin doğru olduğundan, tıklandığını sekmeyi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="41b72-110">If the user has appropriate credentials, display the tab that was clicked.</span></span> <span data-ttu-id="41b72-111">Kullanıcı uygun kimlik bilgilerine sahip değilse, bir ileti kutusu görüntülemek veya gösteren başka bir kullanıcı arabirimi olmayan erişimi ve ilk sekmesine geri dönün.</span><span class="sxs-lookup"><span data-stu-id="41b72-111">If the user does not have appropriate credentials, display a message box or some other user interface indicating that they do not have access, and return to the initial tab.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="41b72-112">Üretim uygulamalarınızı bu işlevselliği uygulamak, formun sırasında bu kimlik bilgisi denetimi gerçekleştirebilir <xref:System.Windows.Forms.Form.Load> olay.</span><span class="sxs-lookup"><span data-stu-id="41b72-112">When you implement this functionality in your production applications, you can perform this credential check during the form's <xref:System.Windows.Forms.Form.Load> event.</span></span> <span data-ttu-id="41b72-113">Bu, bir çok daha net yaklaşım programlamaya olduğu herhangi bir kullanıcı arabirimi gösterilmeden önce sekmesini gizlemek olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="41b72-113">This will allow you to hide the tab before any user interface is shown, which is a much cleaner approach to programming.</span></span> <span data-ttu-id="41b72-114">Aşağıda kullanılan metodolojiyi (kimlik denetimi ve sekme sırasında devre dışı bırakma <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> olay) yalnızca tanım amaçlıdır.</span><span class="sxs-lookup"><span data-stu-id="41b72-114">The methodology used below (checking credentials and disabling the tab during the <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> event) is for illustrative purposes.</span></span>  
  
4. <span data-ttu-id="41b72-115">İkiden fazla sekme sayfaları varsa, isteğe bağlı olarak orijinal olandan arklı bir sekme sayfası görüntüler.</span><span class="sxs-lookup"><span data-stu-id="41b72-115">Optionally, if you have more than two tab pages, display a tab page different from the original.</span></span>  
  
     <span data-ttu-id="41b72-116">Aşağıdaki örnekte bir <xref:System.Windows.Forms.CheckBox> denetimi, uygulama tarafından erişim için sekmesinde değişir için kimlik bilgileri ölçüt olarak denetimi yerine kullanılır.</span><span class="sxs-lookup"><span data-stu-id="41b72-116">In the example below, a <xref:System.Windows.Forms.CheckBox> control is used in lieu of checking the credentials, as the criteria for access to the tab will vary by application.</span></span> <span data-ttu-id="41b72-117">Zaman <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> olayı oluşturulur, kimlik bilgisi onay true ise (diğer bir deyişle, onay kutusu işaretliyse) ve seçili `TabPage2` (Bu örnekte, gizli bilgilerle sekme), ardından `TabPage2` görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="41b72-117">When the <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> event is raised, if the credential check is true (that is, the check box is checked) and the selected tab is `TabPage2` (the tab with the confidential information, in this example), then `TabPage2` is displayed.</span></span> <span data-ttu-id="41b72-118">Aksi takdirde, `TabPage3` görüntülenir ve bunlar yoktu uygun erişim ayrıcalıkları belirten kullanıcıya bir ileti kutusu gösterilir.</span><span class="sxs-lookup"><span data-stu-id="41b72-118">Otherwise, `TabPage3` is displayed and a message box is shown to the user, indicating they did not have appropriate access privileges.</span></span> <span data-ttu-id="41b72-119">Aşağıdaki kod bir formla varsayar bir <xref:System.Windows.Forms.CheckBox> denetimi (`CredentialCheck`) ve bir <xref:System.Windows.Forms.TabControl> üç sekme sayfaları denetimi.</span><span class="sxs-lookup"><span data-stu-id="41b72-119">The code below assumes a form with a <xref:System.Windows.Forms.CheckBox> control (`CredentialCheck`) and a <xref:System.Windows.Forms.TabControl> control with three tab pages.</span></span>  
  
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
  
     <span data-ttu-id="41b72-120">(Visual C#, Visual C++) Aşağıdaki kod, olay işleyicisi kaydetmek için formun oluşturucuda yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="41b72-120">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.tabControl1.SelectedIndexChanged +=   
       new System.EventHandler(this.tabControl1_SelectedIndexChanged);  
    ```  
  
    ```cpp  
    this->tabControl1->SelectedIndexChanged +=  
       gcnew System::EventHandler(this, &Form1::tabControl1_SelectedIndexChanged);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="41b72-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="41b72-121">See also</span></span>

- [<span data-ttu-id="41b72-122">TabControl Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="41b72-122">TabControl Control Overview</span></span>](tabcontrol-control-overview-windows-forms.md)
- [<span data-ttu-id="41b72-123">Nasıl yapılır: Sekme sayfasına denetim ekleme</span><span class="sxs-lookup"><span data-stu-id="41b72-123">How to: Add a Control to a Tab Page</span></span>](how-to-add-a-control-to-a-tab-page.md)
- [<span data-ttu-id="41b72-124">Nasıl yapılır: Windows Forms TabControl ile sekme ekleyip</span><span class="sxs-lookup"><span data-stu-id="41b72-124">How to: Add and Remove Tabs with the Windows Forms TabControl</span></span>](how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
- [<span data-ttu-id="41b72-125">Nasıl yapılır: Windows Forms Tabcontrol'un görünüşünü değiştirme</span><span class="sxs-lookup"><span data-stu-id="41b72-125">How to: Change the Appearance of the Windows Forms TabControl</span></span>](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
