---
title: 'Nasıl yapılır: Windows Forms TabControl ile sekme ekleyip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tabs [Windows Forms], removing from pages
- TabPage control
- TabControl control [Windows Forms], adding and removing tabs
- tabs [Windows Forms], adding to pages
- tab pages
ms.assetid: 66d4dfca-41e8-44e3-9c80-fb7ac4cb1619
ms.openlocfilehash: 4420f598f1243e6c834ecd82bb6ea7071cc95402
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707956"
---
# <a name="how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol"></a><span data-ttu-id="d8d90-102">Nasıl yapılır: Windows Forms TabControl ile sekme ekleyip</span><span class="sxs-lookup"><span data-stu-id="d8d90-102">How to: Add and Remove Tabs with the Windows Forms TabControl</span></span>
<span data-ttu-id="d8d90-103">Varsayılan olarak, bir <xref:System.Windows.Forms.TabControl> denetimi içeren iki <xref:System.Windows.Forms.TabPage> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="d8d90-103">By default, a <xref:System.Windows.Forms.TabControl> control contains two <xref:System.Windows.Forms.TabPage> controls.</span></span> <span data-ttu-id="d8d90-104">Bu sekmeler aracılığıyla erişebileceğiniz <xref:System.Windows.Forms.TabControl.TabPages%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="d8d90-104">You can access these tabs through the <xref:System.Windows.Forms.TabControl.TabPages%2A> property.</span></span>  
  
### <a name="to-add-a-tab-programmatically"></a><span data-ttu-id="d8d90-105">Program aracılığıyla sekme eklemek için</span><span class="sxs-lookup"><span data-stu-id="d8d90-105">To add a tab programmatically</span></span>  
  
-   <span data-ttu-id="d8d90-106">Kullanım <xref:System.Windows.Forms.TabControl.TabPageCollection.Add%2A> yöntemi <xref:System.Windows.Forms.TabControl.TabPages%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="d8d90-106">Use the <xref:System.Windows.Forms.TabControl.TabPageCollection.Add%2A> method of the <xref:System.Windows.Forms.TabControl.TabPages%2A> property.</span></span>  
  
    ```vb  
    Dim myTabPage As New TabPage()  
    myTabPage.Text = "TabPage" & (TabControl1.TabPages.Count + 1)  
    TabControl1.TabPages.Add(myTabPage)  
    ```  
  
    ```csharp  
    string title = "TabPage " + (tabControl1.TabCount + 1).ToString();  
    TabPage myTabPage = new TabPage(title);  
    tabControl1.TabPages.Add(myTabPage);  
    ```  
  
    ```cpp  
    String^ title = String::Concat("TabPage ",  
       (tabControl1->TabCount + 1).ToString());  
    TabPage^ myTabPage = gcnew TabPage(title);  
    tabControl1->TabPages->Add(myTabPage);  
    ```  
  
### <a name="to-remove-a-tab-programmatically"></a><span data-ttu-id="d8d90-107">Bir sekme programlı bir şekilde kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="d8d90-107">To remove a tab programmatically</span></span>  
  
-   <span data-ttu-id="d8d90-108">Seçili sekmeleri kaldırmak için <xref:System.Windows.Forms.TabControl.TabPageCollection.Remove%2A> yöntemi <xref:System.Windows.Forms.TabControl.TabPages%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="d8d90-108">To remove selected tabs, use the <xref:System.Windows.Forms.TabControl.TabPageCollection.Remove%2A> method of the <xref:System.Windows.Forms.TabControl.TabPages%2A> property.</span></span>  
  
     <span data-ttu-id="d8d90-109">-veya-</span><span class="sxs-lookup"><span data-stu-id="d8d90-109">-or-</span></span>  
  
-   <span data-ttu-id="d8d90-110">Tüm sekmeler kaldırmak için <xref:System.Windows.Forms.TabControl.TabPageCollection.Clear%2A> yöntemi <xref:System.Windows.Forms.TabControl.TabPages%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="d8d90-110">To remove all tabs, use the <xref:System.Windows.Forms.TabControl.TabPageCollection.Clear%2A> method of the <xref:System.Windows.Forms.TabControl.TabPages%2A> property.</span></span>  
  
    ```vb  
    ' Removes the selected tab:  
    TabControl1.TabPages.Remove(TabControl1.SelectedTab)  
    ' Removes all the tabs:  
    TabControl1.TabPages.Clear()  
    ```  
  
    ```csharp  
    // Removes the selected tab:  
    tabControl1.TabPages.Remove(tabControl1.SelectedTab);  
    // Removes all the tabs:  
    tabControl1.TabPages.Clear();  
    ```  
  
    ```cpp  
    // Removes the selected tab:  
    tabControl1->TabPages->Remove(tabControl1->SelectedTab);  
    // Removes all the tabs:  
    tabControl1->TabPages->Clear();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="d8d90-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d8d90-111">See also</span></span>
- [<span data-ttu-id="d8d90-112">TabControl Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d8d90-112">TabControl Control Overview</span></span>](tabcontrol-control-overview-windows-forms.md)
- [<span data-ttu-id="d8d90-113">Nasıl yapılır: Sekme sayfasına denetim ekleme</span><span class="sxs-lookup"><span data-stu-id="d8d90-113">How to: Add a Control to a Tab Page</span></span>](how-to-add-a-control-to-a-tab-page.md)
- [<span data-ttu-id="d8d90-114">Nasıl yapılır: Sekme sayfalarını devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="d8d90-114">How to: Disable Tab Pages</span></span>](how-to-disable-tab-pages.md)
- [<span data-ttu-id="d8d90-115">Nasıl yapılır: Windows Forms Tabcontrol'un görünüşünü değiştirme</span><span class="sxs-lookup"><span data-stu-id="d8d90-115">How to: Change the Appearance of the Windows Forms TabControl</span></span>](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
