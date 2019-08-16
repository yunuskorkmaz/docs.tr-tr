---
title: 'Nasıl yapılır: MDI Alt Formları Oluşturma'
ms.date: 03/30/2017
dev_langs:
- CSharp
- CPP
- VB
helpviewer_keywords:
- MDI [Windows Forms], creating forms
- child forms
ms.assetid: 164b69bb-2eca-4339-ada3-0679eb2c6dda
ms.openlocfilehash: f5e8682caf658d159f044528f040b99676355448
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040109"
---
# <a name="how-to-create-mdi-child-forms"></a>Nasıl yapılır: MDI alt formları oluşturma

MDI alt formları, [çok belgeli arabirim (MDI) uygulamalarının](multiple-document-interface-mdi-applications.md)temel bir öğesidir ve bu formlar kullanıcı etkileşiminin ortalarıdır.

Aşağıdaki yordamda, çoğu sözcük işleme uygulamasına benzer bir <xref:System.Windows.Forms.RichTextBox> Denetim görüntüleyen bir MDI alt formu oluşturmak için Visual Studio 'yu kullanacaksınız. Denetimi veya denetim karışımı gibi diğer denetimlerle <xref:System.Windows.Forms.DataGridView> denetimideğiştirerek,farklıolasılıklarlaMDIaltpencereleri(veuzantısı,MDIuygulamaları)oluşturabilirsiniz.<xref:System.Windows.Forms>

## <a name="create-mdi-child-forms"></a>MDI alt formları oluşturma

1. Visual Studio 'da yeni bir Windows Forms uygulama projesi oluşturun. Formun **Özellikler** penceresinde <xref:System.Windows.Forms.Form.IsMdiContainer%2A> , `true` `Maximized`özelliğini ve özelliğini olarak ayarlayın. `WindowsState`

   Bu, formu alt Windows için bir MDI kapsayıcısı olarak belirler.

2. `Toolbox`Öğesinden bir<xref:System.Windows.Forms.MenuStrip> denetimi forma sürükleyin. Özelliğini File olarak ayarlayın. `Text`

3. **Items** özelliğinin yanındaki üç nokta (...) işaretine tıklayın ve **Ekle** ' ye tıklayarak iki alt araç şeridi menü öğesi ekleyin. Bu öğelerin özelliğini yeni ve pencere olarak ayarlayın. `Text`

4. **Çözüm Gezgini**, projeye sağ tıklayın ve ardından**Yeni öğe** **Ekle** > ' yi seçin.

5. **Yeni öğe Ekle** iletişim kutusunda, **Şablonlar** bölmesinden **Windows form** (Visual Basic veya görsel C#) veya **Windows Forms uygulama (.net)** (görsel C++) seçeneğini belirleyin. **Ad** kutusuna formu **Form2**olarak adlandırın. Formu projeye eklemek için **Aç** ' ı seçin.

    > [!NOTE]
    > Bu adımda oluşturduğunuz MDI alt formu standart bir Windows formundadır. Bu nedenle, formun saydamlığını denetlemenizi <xref:System.Windows.Forms.Form.Opacity%2A> sağlayan bir özelliğine sahiptir. Ancak, <xref:System.Windows.Forms.Form.Opacity%2A> özelliği üst düzey pencereler için tasarlanmıştır. Boyama sorunları gerçekleşebileceği için bunu MDI alt formları ile kullanmayın.

     Bu form, MDI alt formlarınızın şablonu olacaktır.

     **Windows Form Tasarımcısı** açılır, **Form2**görüntülüyor.

6. **Araç kutusundan**bir **RichTextBox** denetimini forma sürükleyin.

7. **Özellikler** `Anchor` penceresinde, özelliği **üst, sol** ve özelliğinidolduracakşekilde`Dock` ayarlayın.

   Bu, denetimin, form yeniden boyutlandırılırken bile MDI alt formunun alanını tamamen doldurmasını sağlar. <xref:System.Windows.Forms.RichTextBox>

8. **Yeni** menü öğesine çift tıklayarak onun için bir <xref:System.Windows.Forms.Control.Click> olay işleyicisi oluşturun.

9. Kullanıcı **Yeni** menü öğesine tıkladığında yenı bir MDI alt formu oluşturmak için aşağıdakine benzer bir kod ekleyin.

   > [!NOTE]
   > Aşağıdaki örnekte, olay işleyicisi <xref:System.Windows.Forms.Control.Click> `MenuItem2`olayını işler. Uygulama mimarinizin özelliklerine bağlı olarak **Yeni** menü öğesi `MenuItem2`bulunmayabilir.

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

   İçinde C++, Form1. h `#include` ' nin en üstüne aşağıdaki yönergeyi ekleyin:

   ```cpp
   #include "Form2.h"
   ```

10. **Özellikler** penceresinin üst kısmındaki aşağı açılan listede, **Dosya** menü şeridine karşılık gelen menü şeridi ' ni seçin <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> ve özelliği pencereye <xref:System.Windows.Forms.ToolStripMenuItem>ayarlayın.

    Bu, **pencere** menüsünün, etkin alt pencerenin yanındaki bir onay işaretiyle bırlıkte açık MDI alt pencereleri listesini korumasını sağlar.

11. Uygulamayı çalıştırmak için **F5** tuşuna basın. **Dosya** menüsünden **Yeni** ' yi seçerek, **pencere** menü öğesinde izlenen yeni MDI alt formları oluşturabilirsiniz.

    > [!NOTE]
    > Bir MDI alt formu <xref:System.Windows.Forms.MainMenu> bileşeni olduğunda (genellikle menü öğelerinin bir menü yapısıyla) ve <xref:System.Windows.Forms.MainMenu> bileşeni olan bir MDI parent formu içinde açılır (genellikle menü öğelerinin menü yapısı ile), menü öğeleri otomatik olarak birleştirilir <xref:System.Windows.Forms.MenuItem.MergeType%2A> özelliğini ayarladıysanız (ve isteğe bağlı olarak <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> özelliği). <xref:System.Windows.Forms.MenuMerge.MergeItems>Her iki <xref:System.Windows.Forms.MainMenu> bileşenin özelliğini ve alt formun tüm menü öğelerini olarak ayarlayın. <xref:System.Windows.Forms.MenuItem.MergeType%2A> Ayrıca, <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> özelliğini her iki menüdeki menü öğelerinin istenen sırada görünmesi için ayarlayın. Üstelik, bir MDI parent formunu kapattığınızda, MDI alt formlarının her biri MDI parent <xref:System.Windows.Forms.Form.Closing> <xref:System.Windows.Forms.Form.Closing> olayı oluşturulmadan önce bir olay harekete geçirdiğini aklınızda bulundurun. <xref:System.Windows.Forms.Form.Closing> MDI alt öğesinin olayının iptal edilmesi MDI üst öğesinin <xref:System.ComponentModel.CancelEventArgs> <xref:System.Windows.Forms.Form.Closing> olayının oluşmasını engellemez; ancak MDI parent <xref:System.Windows.Forms.Form.Closing> olayının bağımsız değişkeni şimdi olarak `true`ayarlanır. <xref:System.ComponentModel.CancelEventArgs> Bağımsız değişkenini olarak `false`ayarlayarak MDI parent ve tüm MDI alt formlarını kapanmaya zorlayabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Çok Belgeli Arabirim (MDI) Uygulamaları](multiple-document-interface-mdi-applications.md)
- [Nasıl yapılır: MDI üst formları oluşturma](how-to-create-mdi-parent-forms.md)
- [Nasıl yapılır: Etkin MDI alt öğesini belirleme](how-to-determine-the-active-mdi-child.md)
- [Nasıl yapılır: Etkin MDI alt öğesine veri gönderme](how-to-send-data-to-the-active-mdi-child.md)
- [Nasıl yapılır: MDI alt formlarını düzenleme](how-to-arrange-mdi-child-forms.md)
