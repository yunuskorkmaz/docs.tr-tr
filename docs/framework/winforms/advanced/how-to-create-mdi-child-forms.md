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
ms.openlocfilehash: bdfbe59ef779de242e32be11ca28c84f68437240
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43486798"
---
# <a name="how-to-create-mdi-child-forms"></a>Nasıl yapılır: MDI Alt Formları Oluşturma
MDI alt formlarını olan önemli bir öğesidir [Çok Belgeli Arabirim (MDI) uygulamaları](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md), bu formları kullanıcı etkileşimi merkezi olarak.  
  
 Aşağıdaki yordamda görüntüler MDI alt formu oluşturur. bir <xref:System.Windows.Forms.RichTextBox> denetimi en sözcük uygulamalarına benzer. Değiştirerek <xref:System.Windows.Forms> diğer denetimlerle denetimini <xref:System.Windows.Forms.DataGridView> denetim veya denetimlerin bir karışımını sağlar, MDI alt pencereleri oluşturmak (ve uzantısı, MDI uygulamaları) ile çeşitli olanaklar.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-create-mdi-child-forms"></a>MDI alt formları oluşturmak için  
  
1.  Yeni bir Windows Forms projesi oluşturun. İçinde **özellikleri Windows** formun kendi <xref:System.Windows.Forms.Form.IsMdiContainer%2A> özelliğini `true`ve onun `WindowsState` özelliğini `Maximized`.  
  
     Bu, form alt pencereler için bir MDI kapsayıcısı olarak belirler.  
  
2.  Gelen `Toolbox`, sürükleyin bir <xref:System.Windows.Forms.MenuStrip> forma. Ayarlama, `Text` özelliğini **dosya**.  
  
3.  Yanındaki üç nokta (...) tıklayın **öğeleri** özelliği seçeneğine tıklayıp **Ekle** iki alt araç şeridi menü öğesi eklemek için. Ayarlama `Text` özelliği için bu öğeler için **yeni** ve **penceresi**.  
  
4.  İçinde **Çözüm Gezgini**, projeye sağ tıklayın, fareyle **Ekle**ve ardından **Yeni Öğe Ekle**.  
  
5.  İçinde **Yeni Öğe Ekle** iletişim kutusunda **Windows Form** (Visual Basic veya Visual C#) veya **Windows Forms uygulaması (.NET)** (içinde [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) gelen **Şablonları** bölmesi. İçinde **adı** kutusunda, formun adı **Form2**. Tıklayın **açık** projeye form ekleme düğmesi.  
  
    > [!NOTE]
    >  Bu adımda oluşturduğunuz MDI alt formu, bir standart Windows biçimidir. Bu nedenle, sahip bir <xref:System.Windows.Forms.Form.Opacity%2A> form saydamlığını denetlemenize olanak sağlayan özellik. Ancak, <xref:System.Windows.Forms.Form.Opacity%2A> özelliği, üst düzey pencerelere için tasarlanmıştır. Boyama sorunlar oluşabilir gibi MDI alt formlarını ile kullanmayın.  
  
     Bu form, MDI alt formlarını şablonu olacaktır.  
  
     **Windows Form Tasarımcısı** görüntüleme açıldığında **Form2**.  
  
6.  Gelen **araç kutusu**, sürükleyin bir **RichTextBox** forma.  
  
7.  İçinde **özellikleri** penceresinde `Anchor` özelliğini **üst, sol** ve `Dock` özelliğini **dolgu**.  
  
     Bu neden <xref:System.Windows.Forms.RichTextBox> bile formu yeniden boyutlandırıldığında alanı MDI alt formunun tamamen doldurmak için denetimi.  
  
8.  Çift tıklayarak **yeni** oluşturmak için menü öğesi bir <xref:System.Windows.Forms.Control.Click> olay işleyicisi.  
  
9. Kullanıcı tıkladığında, yeni bir MDI alt formu oluşturmak için aşağıdaki için benzer bir kod ekleme **yeni** menü öğesi.  
  
    > [!NOTE]
    >  Aşağıdaki örnekte olay işleyicisi işler <xref:System.Windows.Forms.Control.Click> olayı `MenuItem2`. Unutmayın uygulama mimarinizin ayrıntılarına bağlı olarak, uygulamanızın **yeni** menü öğesi olabilir `MenuItem2`.  
  
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
  
     İçinde [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)], aşağıdaki `#include` Form1.h üst kısmındaki yönergesi:  
  
    ```cpp  
    #include "Form2.h"  
    ```  
  
10. En üstündeki açılan listesinde **özellikleri** penceresinde karşılık gelen menü Şerit seçin **dosya** Şerit menüsü ve kümesi <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> özellik penceresine <xref:System.Windows.Forms.ToolStripMenuItem>.  
  
     Bu olanak tanıyacak **penceresi** etkin alt pencerenin yanında bir onay işareti ile açık MDI alt pencereleri listesini korumak için menü.  
  
11. Uygulamayı çalıştırmak için F5 tuşuna basın. Seçerek **yeni** gelen **dosya** menüsünde, hangi tutulan içinde izlemek yeni MDI alt formlarını oluşturabilirsiniz **penceresi** menü öğesi.  
  
    > [!NOTE]
    >  MDI alt formu olduğunda bir <xref:System.Windows.Forms.MainMenu> (sahip, genellikle bir menüsü yapısı menü öğelerinin) bileşen ve onu içeren MDI üst formu içinde açılır bir <xref:System.Windows.Forms.MainMenu> (sahip, genellikle bir menüsü yapısı menü öğelerinin) bileşen, menü öğeleri otomatik olarak birleştirilir ayarladıysanız <xref:System.Windows.Forms.MenuItem.MergeType%2A> özelliği (ve isteğe bağlı olarak <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> özelliği). Ayarlama <xref:System.Windows.Forms.MenuItem.MergeType%2A> her iki özellik <xref:System.Windows.Forms.MainMenu> bileşenlerini ve tüm alt formun menü öğelerinin <xref:System.Windows.Forms.MenuMerge.MergeItems>. Ayrıca, olarak <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> özelliği hem menülerden menü öğelerini böylece istenen sırada görünür. Ayrıca, MDI üst formu kapatın, her bir MDI alt harekete geçirirse forms akılda tutulması bir <xref:System.Windows.Forms.Form.Closing> olayından önce <xref:System.Windows.Forms.Form.Closing> MDI üst olayı oluşturulur. Bir MDI çocuk iptal <xref:System.Windows.Forms.Form.Closing> olay MDI üst öğenin engellemez <xref:System.Windows.Forms.Form.Closing> gerçekleştirilen; gelen olay ancak <xref:System.ComponentModel.CancelEventArgs> MDI üst öğenin için bağımsız değişken <xref:System.Windows.Forms.Form.Closing> olay artık ayarlanır `true`. MDI ve tüm MDI alt formlarını ayarlayarak kapanmaya zorlayabilir <xref:System.ComponentModel.CancelEventArgs> bağımsız değişkeni `false`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çok Belgeli Arabirim (MDI) Uygulamaları](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md)  
 [Nasıl yapılır: MDI Üst Formları Oluşturma](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [Nasıl yapılır: Etkin MDI Alt Öğesini Belirleme](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md)  
 [Nasıl yapılır: Etkin MDI Alt Öğesine Veri Gönderme](../../../../docs/framework/winforms/advanced/how-to-send-data-to-the-active-mdi-child.md)  
 [Nasıl yapılır: MDI Alt Formlarını Düzenleme](../../../../docs/framework/winforms/advanced/how-to-arrange-mdi-child-forms.md)
