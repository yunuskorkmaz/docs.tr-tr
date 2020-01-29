---
title: TabControl ile sekme ekleme ve kaldırma
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
ms.openlocfilehash: 8292d8441f9b47334b98736cf3282c846673dbb4
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732710"
---
# <a name="how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol"></a>Nasıl yapılır: Windows Forms TabControl' ile Sekme Ekleme ve Kaldırma
Varsayılan olarak, bir <xref:System.Windows.Forms.TabControl> denetimi iki <xref:System.Windows.Forms.TabPage> denetimini içerir. Bu sekmelere <xref:System.Windows.Forms.TabControl.TabPages%2A> özelliği aracılığıyla erişebilirsiniz.  
  
### <a name="to-add-a-tab-programmatically"></a>Program aracılığıyla sekme eklemek için  
  
- <xref:System.Windows.Forms.TabControl.TabPages%2A> özelliğinin <xref:System.Windows.Forms.TabControl.TabPageCollection.Add%2A> yöntemini kullanın.  
  
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
  
### <a name="to-remove-a-tab-programmatically"></a>Bir sekmeyi programlı bir şekilde kaldırmak için  
  
- Seçili sekmeleri kaldırmak için <xref:System.Windows.Forms.TabControl.TabPages%2A> özelliğinin <xref:System.Windows.Forms.TabControl.TabPageCollection.Remove%2A> yöntemini kullanın.  
  
     veya  
  
- Tüm sekmeleri kaldırmak için <xref:System.Windows.Forms.TabControl.TabPages%2A> özelliğinin <xref:System.Windows.Forms.TabControl.TabPageCollection.Clear%2A> yöntemini kullanın.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [TabControl Denetimine Genel Bakış](tabcontrol-control-overview-windows-forms.md)
- [Nasıl yapılır: Sekme Sayfasına Denetim Ekleme](how-to-add-a-control-to-a-tab-page.md)
- [Nasıl yapılır: Sekme Sayfalarını Devre Dışı Bırakma](how-to-disable-tab-pages.md)
- [Nasıl yapılır: Windows Forms TabControl’un Görünüşünü Değiştirme](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
