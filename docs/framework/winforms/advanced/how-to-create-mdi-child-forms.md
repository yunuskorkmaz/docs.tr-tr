---
title: "Nasıl yapılır: MDI Alt Formları Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- MDI [Windows Forms], creating forms
- child forms
ms.assetid: 164b69bb-2eca-4339-ada3-0679eb2c6dda
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d0ee60e9b25ed4238ccdd738cd59a69876f6b55d
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-create-mdi-child-forms"></a>Nasıl yapılır: MDI Alt Formları Oluşturma
MDI alt formları olan önemli bir öğe [Çoklu belge arabirimi (MDI) uygulamaları](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md), bu formların kullanıcı etkileşimi merkezi olarak.  
  
 Aşağıdaki yordamda görüntüler MDI alt form oluşturacak bir <xref:System.Windows.Forms.RichTextBox> denetim, çoğu sözcük işlemci uygulamalarına benzer. Değiştirerek <xref:System.Windows.Forms> başka denetimlerle birlikte denetimini <xref:System.Windows.Forms.DataGridView> denetim veya denetimlerin bir karışımını MDI alt pencereleri oluşturmak etkinleştirir (ve uzantılarının, MDI uygulamaları) farklı sayıda olasılık ile.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-create-mdi-child-forms"></a>MDI alt formları oluşturma  
  
1.  Yeni bir Windows Forms projesi oluşturun. İçinde **özellikleri Windows** formun kendi <xref:System.Windows.Forms.Form.IsMdiContainer%2A> özelliğine `true`ve kendi `WindowsState` özelliğine `Maximized`.  
  
     Bu, formun alt windows için bir MDI kapsayıcı olarak belirler.  
  
2.  Gelen `Toolbox`, sürükleyin bir <xref:System.Windows.Forms.MenuStrip> forma denetim. Ayarlama, `Text` özelliğine **dosya**.  
  
3.  Yanındaki üç nokta (...) tıklatın **öğeleri** özelliği ve tıklatın **Ekle** iki alt aracı Şerit menü öğelerini eklemek için. Ayarlama `Text` özelliği bu öğeler için **yeni** ve **penceresi**.  
  
4.  İçinde **Çözüm Gezgini**, projeye sağ tıklayın, fareyle **Ekle**ve ardından **Yeni Öğe Ekle**.  
  
5.  İçinde **Yeni Öğe Ekle** iletişim kutusunda **Windows formu** (içinde [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] veya [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]) veya **Windows Forms uygulaması (.NET)** (içinde [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) gelen **şablonları** bölmesi. İçinde **adı** kutusunda, formun ad **Form2**. Tıklatın **açık** projeye form ekleme düğmesi.  
  
    > [!NOTE]
    >  Bu adımda oluşturduğunuz MDI alt standart Windows formu biçimidir. Bu nedenle, sahip bir <xref:System.Windows.Forms.Form.Opacity%2A> formun saydamlığını denetlemenize olanak sağlayan özelliği. Ancak, <xref:System.Windows.Forms.Form.Opacity%2A> özelliği, üst düzey windows için tasarlanmıştır. Boyama sorunları ortaya çıktığında MDI alt formları ile kullanmayın.  
  
     Bu form MDI alt formları için şablonu olacaktır.  
  
     **Windows Form Tasarımcısı** görüntüleme açılır **Form2**.  
  
6.  Gelen **araç**, sürükleyin bir **RichTextBox** forma denetim.  
  
7.  İçinde **özellikleri** penceresindeki ayarlayın `Anchor` özelliğine **üst, sol** ve `Dock` özelliğine **doldurun**.  
  
     Bu neden <xref:System.Windows.Forms.RichTextBox> bile formu boyutlandırıldığında tamamen MDI alt formunun alanını doldurmak için denetim.  
  
8.  Çift tıklayarak **yeni** menü öğesi oluşturmak için bir <xref:System.Windows.Forms.Control.Click> olay işleyicisi.  
  
9. Aşağıdaki kullanıcı tıklattığında yeni bir MDI alt form oluşturmak için benzer bir kod ekleme **yeni** menü öğesi.  
  
    > [!NOTE]
    >  Aşağıdaki örnekte, olay işleyicisi işleme <xref:System.Windows.Forms.Control.Click> olayı `MenuItem2`. Unutmayın, uygulama Mimarinizi ayrıntılarını bağlı olarak, **yeni** menü öğesi olmayabilir `MenuItem2`.  
  
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
  
     İçinde [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)], aşağıdakileri ekleyin `#include` Form1.h üstündeki yönerge:  
  
    ```cpp  
    #include "Form2.h"  
    ```  
  
10. Aşağı açılan listesinde en üstündeki **özellikleri** penceresinde, karşılık gelen menü Şerit seçin **dosya** menü Şerit ve kümesi <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> penceresine özelliği <xref:System.Windows.Forms.ToolStripMenuItem>.  
  
     Bu etkinleştirecek **penceresi** etkin alt pencere yanındaki onay işaretiyle açık MDI alt pencereleri listesini korumak için menüsü.  
  
11. Uygulamayı çalıştırmak için F5 tuşuna basın. Seçerek **yeni** gelen **dosya** menüsünde hangi tutulan içinde izlemek yeni MDI alt formları oluşturabilirsiniz **penceresi** menü öğesi.  
  
    > [!NOTE]
    >  MDI alt formu olduğunda bir <xref:System.Windows.Forms.MainMenu> bileşeni (yapısıyla, genellikle, menü menü öğeleri) ve onu içeren MDI üst formu içinde açıldığında bir <xref:System.Windows.Forms.MainMenu> bileşeni (ile genellikle bir menü yapısı menü öğelerinin), öğeleri birleştirme otomatik olarak menüsü ayarlamış olmanız durumunda <xref:System.Windows.Forms.MenuItem.MergeType%2A> özelliği (ve isteğe bağlı olarak <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> özelliği). Ayarlama <xref:System.Windows.Forms.MenuItem.MergeType%2A> özelliği hem <xref:System.Windows.Forms.MainMenu> bileşenleri ve tüm alt formun menü öğelerinin <xref:System.Windows.Forms.MenuMerge.MergeItems>. Ayrıca, olarak <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> özelliği hem menülerden menü öğelerini böylece sıralamada görünür. Ayrıca, MDI üst formu kapattığınızda, her MDI alt başlatır forms göz önünde bulundurmanız bir <xref:System.Windows.Forms.Form.Closing> önce olay <xref:System.Windows.Forms.Form.Closing> MDI üst olayı oluşturulur. Bir MDI çocuğun iptal etme <xref:System.Windows.Forms.Form.Closing> olay MDI üst öğenin engellemez <xref:System.Windows.Forms.Form.Closing> gerçekleştirilen; gelen olay ancak <xref:System.ComponentModel.CancelEventArgs> MDI üst öğenin için bağımsız değişken <xref:System.Windows.Forms.Form.Closing> olay şimdi şekilde ayarlanacak `true`. MDI ve tüm MDI alt formları ayarlayarak kapatmaya zorlamak <xref:System.ComponentModel.CancelEventArgs> bağımsız değişkeni `false`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çok Belgeli Arabirim (MDI) Uygulamaları](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md)  
 [Nasıl yapılır: MDI Üst Formları Oluşturma](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [Nasıl yapılır: Etkin MDI Alt Öğesini Belirleme](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md)  
 [Nasıl yapılır: Etkin MDI Alt Öğesine Veri Gönderme](../../../../docs/framework/winforms/advanced/how-to-send-data-to-the-active-mdi-child.md)  
 [Nasıl yapılır: MDI Alt Formlarını Düzenleme](../../../../docs/framework/winforms/advanced/how-to-arrange-mdi-child-forms.md)
