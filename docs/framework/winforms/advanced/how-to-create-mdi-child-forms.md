---
title: 'Nasıl yapılır: MDI Alt Formları Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- MDI [Windows Forms], creating forms
- child forms
ms.assetid: 164b69bb-2eca-4339-ada3-0679eb2c6dda
ms.openlocfilehash: b49d43e0e1123921cb3800f0d60193d0ea7b3924
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75338590"
---
# <a name="how-to-create-mdi-child-forms"></a>Nasıl yapılır: MDI alt formları oluşturma

MDI alt formları, [çok belgeli arabirim (MDI) uygulamalarının](multiple-document-interface-mdi-applications.md)temel bir öğesidir ve bu formlar kullanıcı etkileşiminin ortalarıdır.

Aşağıdaki yordamda, çoğu sözcük işleme uygulamasına benzer bir <xref:System.Windows.Forms.RichTextBox> denetimi görüntüleyen bir MDI alt formu oluşturmak için Visual Studio 'Yu kullanacaksınız. <xref:System.Windows.Forms> denetimini <xref:System.Windows.Forms.DataGridView> denetimi veya denetimlerin karışımı gibi diğer denetimlerle değiştirerek, farklı olasılıklarla MDI alt pencereleri (ve uzantısı, MDI uygulamaları) oluşturabilirsiniz.

## <a name="create-mdi-child-forms"></a>MDI alt formları oluşturma

1. Visual Studio 'da yeni bir Windows Forms uygulama projesi oluşturun. Formun **Özellikler** penceresinde, <xref:System.Windows.Forms.Form.IsMdiContainer%2A> özelliğini `true` ve `WindowsState` özelliğini `Maximized`olarak ayarlayın.

   Bu, formu alt Windows için bir MDI kapsayıcısı olarak belirler.

2. `Toolbox`, bir <xref:System.Windows.Forms.MenuStrip> denetimini forma sürükleyin. `Text` özelliğini **File**olarak ayarlayın.

3. **Items** özelliğinin yanındaki üç nokta (...) işaretine tıklayın ve **Ekle** ' ye tıklayarak iki alt araç şeridi menü öğesi ekleyin. Bu öğelerin `Text` özelliğini **Yeni** ve **pencere**olarak ayarlayın.

4. **Çözüm Gezgini**, projeye sağ tıklayın ve ardından > **Yeni öğe** **Ekle** ' yi seçin.

5. **Yeni öğe Ekle** iletişim kutusunda, **Şablonlar** bölmesinden **Windows form** (Visual Basic veya görsel C#) veya **Windows Forms uygulama (.net)** (görsel C++) seçeneğini belirleyin. **Ad** kutusuna formu **Form2**olarak adlandırın. Formu projeye eklemek için **Aç** ' ı seçin.

    > [!NOTE]
    > Bu adımda oluşturduğunuz MDI alt formu standart bir Windows formundadır. Bu nedenle, formun saydamlığını denetlemenizi sağlayan bir <xref:System.Windows.Forms.Form.Opacity%2A> özelliğine sahiptir. Ancak, <xref:System.Windows.Forms.Form.Opacity%2A> özelliği en üst düzey pencereler için tasarlanmıştır. Boyama sorunları gerçekleşebileceği için bunu MDI alt formları ile kullanmayın.

     Bu form, MDI alt formlarınızın şablonu olacaktır.

     **Windows Form Tasarımcısı** açılır, **Form2**görüntülüyor.

6. **Araç kutusundan**bir **RichTextBox** denetimini forma sürükleyin.

7. **Özellikler** penceresinde, `Anchor` özelliğini **üst, sol** ve `Dock` özelliğini **dolduracak**şekilde ayarlayın.

   Bu, form yeniden boyutlandırılırken bile <xref:System.Windows.Forms.RichTextBox> denetiminin MDI alt formunun alanını tamamen doldurmasını sağlar.

8. **Yeni** menü öğesine çift tıklayarak onun için <xref:System.Windows.Forms.Control.Click> bir olay işleyicisi oluşturun.

9. Kullanıcı **Yeni** menü öğesine tıkladığında yenı bir MDI alt formu oluşturmak için aşağıdakine benzer bir kod ekleyin.

   > [!NOTE]
   > Aşağıdaki örnekte, olay işleyicisi `MenuItem2`için <xref:System.Windows.Forms.Control.Click> olayını işler. Uygulama mimarinizin özelliklerine bağlı olarak, **Yeni** menü öğesi `MenuItem2`olmayabilir.

    ```vb
    Protected Sub MDIChildNew_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles MenuItem2.Click
       Dim NewMDIChild As New Form2()
       'Set the Parent Form of the Child window.
       NewMDIChild.MdiParent = Me
       'Display the new form.
       NewMDIChild.Show()
    End Sub
    ```

    ```csharp
    protected void MDIChildNew_Click(object sender, System.EventArgs e){
       Form2 newMDIChild = new Form2();
       // Set the Parent Form of the Child window.
       newMDIChild.MdiParent = this;
       // Display the new form.
       newMDIChild.Show();
    }
    ```

    ```cpp
    private:
       void menuItem2_Click(System::Object ^ sender,
          System::EventArgs ^ e)
       {
          Form2^ newMDIChild = gcnew Form2();
          // Set the Parent Form of the Child window.
          newMDIChild->MdiParent = this;
          // Display the new form.
          newMDIChild->Show();
       }
    ```

   İçinde C++, Form1. h ' nin en üstüne aşağıdaki `#include` yönergesini ekleyin:

   ```cpp
   #include "Form2.h"
   ```

10. **Özellikler** penceresinin üst kısmındaki aşağı açılan listede, **Dosya** menüsü şeridine karşılık gelen menü şeridi ' ni seçin ve <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> özelliğini pencere <xref:System.Windows.Forms.ToolStripMenuItem>olarak ayarlayın.

    Bu, **pencere** menüsünün, etkin alt pencerenin yanındaki bir onay işaretiyle bırlıkte açık MDI alt pencereleri listesini korumasını sağlar.

11. Uygulamayı çalıştırmak için **F5**'e basın. **Dosya** menüsünden **Yeni** ' yi seçerek, **pencere** menü öğesinde izlenen yeni MDI alt formları oluşturabilirsiniz.

    > [!NOTE]
    > Bir MDI alt formu <xref:System.Windows.Forms.MainMenu> bileşeni olduğunda (genellikle menü öğelerinin bir menü yapısıyla) ve bir <xref:System.Windows.Forms.MainMenu> bileşeni olan bir MDI parent formu içinde (genellikle menü öğelerinin bir menü yapısıyla) açılırsa, <xref:System.Windows.Forms.MenuItem.MergeType%2A> özelliğini (ve isteğe bağlı olarak, <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> özelliğini) ayarladıysanız menü öğeleri otomatik olarak birleştirilir. Hem <xref:System.Windows.Forms.MainMenu> bileşenlerinin hem de alt formun tüm menü öğelerinin <xref:System.Windows.Forms.MenuItem.MergeType%2A> özelliğini <xref:System.Windows.Forms.MenuMerge.MergeItems>olarak ayarlayın. Ayrıca, her iki menüdeki menü öğelerinin istenen sırada görünmesi için <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> özelliğini ayarlayın. Üstelik, bir MDI parent formunu kapattığınızda, MDI parent form <xref:System.Windows.Forms.Form.Closing> olayından önce MDI alt formlarının her biri <xref:System.Windows.Forms.Form.Closing> bir olay harekete geçirdiğini aklınızda bulundurun. MDI alt öğesinin <xref:System.Windows.Forms.Form.Closing> olayının iptal edilmesi, MDI üstünün <xref:System.Windows.Forms.Form.Closing> olayının oluşmasını engellemez; Ancak, MDI parent <xref:System.Windows.Forms.Form.Closing> olayının <xref:System.ComponentModel.CancelEventArgs> bağımsız değişkeni artık `true`olarak ayarlanacak. <xref:System.ComponentModel.CancelEventArgs> bağımsız değişkenini `false`olarak ayarlayarak MDI parent ve tüm MDI alt formlarını kapanmaya zorlayabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Çok Belgeli Arabirim (MDI) Uygulamaları](multiple-document-interface-mdi-applications.md)
- [Nasıl yapılır: MDI Üst Formları Oluşturma](how-to-create-mdi-parent-forms.md)
- [Nasıl yapılır: Etkin MDI Alt Öğesini Belirleme](how-to-determine-the-active-mdi-child.md)
- [Nasıl yapılır: Etkin MDI Alt Öğesine Veri Gönderme](how-to-send-data-to-the-active-mdi-child.md)
- [Nasıl yapılır: MDI Alt Formlarını Düzenleme](how-to-arrange-mdi-child-forms.md)
