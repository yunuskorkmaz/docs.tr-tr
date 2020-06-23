---
title: 'Nasıl yapılır: MDI Alt Formları Oluşturma'
description: Bir RichTextBox denetimi görüntüleyen birden çok belgeli arabirim (MDI) alt formu oluşturmak için Visual Studio 'Yu nasıl kullanacağınızı öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- MDI [Windows Forms], creating forms
- child forms
ms.assetid: 164b69bb-2eca-4339-ada3-0679eb2c6dda
ms.openlocfilehash: 7fe5cde342f0f5ee078f888b7492cd4618bea5c4
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903188"
---
# <a name="how-to-create-mdi-child-forms"></a>Nasıl yapılır: MDI alt formları oluşturma

MDI alt formları, [çok belgeli arabirim (MDI) uygulamalarının](multiple-document-interface-mdi-applications.md)temel bir öğesidir ve bu formlar kullanıcı etkileşiminin ortalarıdır.

Aşağıdaki yordamda, <xref:System.Windows.Forms.RichTextBox> çoğu sözcük işleme uygulamasına benzer bir denetim görüntüleyen BIR MDI alt formu oluşturmak Için Visual Studio 'yu kullanacaksınız. Denetimi veya denetim <xref:System.Windows.Forms> karışımı gibi diğer denetimlerle denetimi değiştirerek <xref:System.Windows.Forms.DataGridView> , farklı olasılıklarla MDI alt pencereleri (ve UZANTıSı, MDI uygulamaları) oluşturabilirsiniz.

## <a name="create-mdi-child-forms"></a>MDI alt formları oluşturma

1. Visual Studio 'da yeni bir Windows Forms uygulama projesi oluşturun. Formun **Özellikler** penceresinde, <xref:System.Windows.Forms.Form.IsMdiContainer%2A> özelliğini `true` ve `WindowsState` özelliğini olarak ayarlayın `Maximized` .

   Bu, formu alt Windows için bir MDI kapsayıcısı olarak belirler.

2. Öğesinden `Toolbox` bir <xref:System.Windows.Forms.MenuStrip> denetimi forma sürükleyin. `Text`Özelliğini **File**olarak ayarlayın.

3. **Items** özelliğinin yanındaki üç nokta (...) işaretine tıklayın ve **Ekle** ' ye tıklayarak iki alt araç şeridi menü öğesi ekleyin. `Text`Bu öğelerin özelliğini **Yeni** ve **pencere**olarak ayarlayın.

4. **Çözüm Gezgini**, projeye sağ tıklayın ve ardından **Add**  >  **Yeni öğe**Ekle ' yi seçin.

5. **Yeni öğe Ekle** iletişim kutusunda, **Şablonlar** bölmesinden **Windows formu** (Visual Basic veya Visual C# ' de) veya **Windows Forms uygulama (.net)** (Visual C++) seçeneğini belirleyin. **Ad** kutusuna formu **Form2**olarak adlandırın. Formu projeye eklemek için **Aç** ' ı seçin.

    > [!NOTE]
    > Bu adımda oluşturduğunuz MDI alt formu standart bir Windows formundadır. Bu nedenle, <xref:System.Windows.Forms.Form.Opacity%2A> formun saydamlığını denetlemenizi sağlayan bir özelliğine sahiptir. Ancak, <xref:System.Windows.Forms.Form.Opacity%2A> özelliği üst düzey pencereler için tasarlanmıştır. Boyama sorunları gerçekleşebileceği için bunu MDI alt formları ile kullanmayın.

     Bu form, MDI alt formlarınızın şablonu olacaktır.

     **Windows Form Tasarımcısı** açılır, **Form2**görüntülüyor.

6. **Araç kutusundan**bir **RichTextBox** denetimini forma sürükleyin.

7. **Özellikler** penceresinde, `Anchor` özelliği **üst, sol** ve `Dock` özelliğini **dolduracak**şekilde ayarlayın.

   Bu, <xref:System.Windows.Forms.RichTextBox> denetimin, form yeniden boyutlandırılırken bıle MDI alt formunun alanını tamamen doldurmasını sağlar.

8. **Yeni** menü öğesine çift tıklayarak <xref:System.Windows.Forms.Control.Click> onun için bir olay işleyicisi oluşturun.

9. Kullanıcı **Yeni** menü öğesine tıkladığında yenı bir MDI alt formu oluşturmak için aşağıdakine benzer bir kod ekleyin.

   > [!NOTE]
   > Aşağıdaki örnekte, olay işleyicisi <xref:System.Windows.Forms.Control.Click> olayını işler `MenuItem2` . Uygulama mimarinizin özelliklerine bağlı olarak **Yeni** menü öğesi bulunmayabilir `MenuItem2` .

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

   C++ ' da, `#include` Form1. h ' nin en üstüne aşağıdaki yönergeyi ekleyin:

   ```cpp
   #include "Form2.h"
   ```

10. **Özellikler** penceresinin üst kısmındaki aşağı açılan listede, **Dosya** menü şeridine karşılık gelen menü şeridi ' ni seçin ve <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> özelliği pencereye ayarlayın <xref:System.Windows.Forms.ToolStripMenuItem> .

    Bu, **pencere** menüsünün, etkin alt pencerenin yanındaki bir onay işaretiyle bırlıkte açık MDI alt pencereleri listesini korumasını sağlar.

11. Uygulamayı çalıştırmak için **F5**'e basın. **Dosya** menüsünden **Yeni** ' yi seçerek, **pencere** menü öğesinde izlenen yeni MDI alt formları oluşturabilirsiniz.

    > [!NOTE]
    > Bir MDI alt form <xref:System.Windows.Forms.MainMenu> bileşeni olduğunda (genellikle menü öğelerinin bir menü yapısı ile) ve bileşeni olan BIR MDI parent formu içinde ( <xref:System.Windows.Forms.MainMenu> genellikle menü öğelerinin bir menü yapısıyla) açılırsa, <xref:System.Windows.Forms.MenuItem.MergeType%2A> Özelliği (ve isteğe bağlı olarak, özelliğini) ayarladıysanız menü öğeleri otomatik olarak birleştirilir <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> . <xref:System.Windows.Forms.MenuItem.MergeType%2A>Her iki <xref:System.Windows.Forms.MainMenu> bileşenin özelliğini ve alt formun tüm menü öğelerini olarak ayarlayın <xref:System.Windows.Forms.MenuMerge.MergeItems> . Ayrıca, <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> özelliğini her iki menüdeki menü öğelerinin istenen sırada görünmesi için ayarlayın. Üstelik, bir MDI parent formunu kapattığınızda, MDI alt formlarının her biri <xref:System.Windows.Forms.Form.Closing> <xref:System.Windows.Forms.Form.Closing> MDI parent olayı oluşturulmadan önce bir olay harekete geçirdiğini aklınızda bulundurun. MDI alt öğesinin olayının iptal edilmesi <xref:System.Windows.Forms.Form.Closing> MDI üst öğesinin olayının oluşmasını engellemez <xref:System.Windows.Forms.Form.Closing> ; ancak <xref:System.ComponentModel.CancelEventArgs> MDI parent olayının bağımsız değişkeni <xref:System.Windows.Forms.Form.Closing> Şimdi olarak ayarlanır `true` . Bağımsız değişkenini olarak ayarlayarak MDI parent ve tüm MDI alt formlarını kapanmaya zorlayabilirsiniz <xref:System.ComponentModel.CancelEventArgs> `false` .

## <a name="see-also"></a>Ayrıca bkz.

- [Çoklu Belge Arabirimi (MDI) Uygulamaları](multiple-document-interface-mdi-applications.md)
- [Nasıl yapılır: MDI Üst Formları Oluşturma](how-to-create-mdi-parent-forms.md)
- [Nasıl yapılır: Etkin MDI Alt Öğesini Belirleme](how-to-determine-the-active-mdi-child.md)
- [Nasıl yapılır: Etkin MDI Alt Öğesine Veri Gönderme](how-to-send-data-to-the-active-mdi-child.md)
- [Nasıl yapılır: MDI Alt Formlarını Düzenleme](how-to-arrange-mdi-child-forms.md)
