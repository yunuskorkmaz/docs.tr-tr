---
title: 'Nasıl yapılır: Tasarımcı Kullanarak Windows Formları ile Çok Bölmeli bir Kullanıcı Arabirimi Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- user interface [Windows Forms], multipane
- SplitContainer control [Windows Forms], using the designer
- multipane user interface
ms.assetid: c3f9294d-a26c-4198-9242-f237f55f7573
ms.openlocfilehash: d0faf86ce31dad6bc053b5af8902e500d2b1c75b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-multipane-user-interface-with-windows-forms-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Windows Formları ile Çok Bölmeli bir Kullanıcı Arabirimi Oluşturma
Aşağıdaki yordamda, Microsoft Outlook ile kullanılan benzer çok bölmeli kullanıcı arabirimi oluşturacak bir **klasörü** listesinde, bir **iletileri** bölmesinde ve **Önizleme** bölmesi. Bu düzenlemenin, formun denetimleriyle chiefly yerleştirme aracılığıyla elde edilir.  
  
 Bir denetim noktası olduğunda, bir denetim üst kapsayıcı hangi kenarı fastened belirler. Bu nedenle, ayarlarsanız <xref:System.Windows.Forms.SplitContainer.Dock%2A> özelliğine <xref:System.Windows.Forms.DockStyle.Right>, denetimin sağ kenarı sağ, üst denetim kenarına yerleştirilir. Ayrıca, kapsayıcı denetiminin eşleşen denetim yerleşik kenarı boyutlandırılır. Ne hakkında daha fazla bilgi için <xref:System.Windows.Forms.SplitContainer.Dock%2A> özelliği çalıştığını görmek [nasıl yapılır: Windows formlarında denetimleri yerleştirme](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md).  
  
 Bu yordam, düzenleme üzerinde odaklanır <xref:System.Windows.Forms.SplitContainer> ve diğer denetimleri form üzerinde Microsoft Outlook taklit uygulama yapmayı işlevselliği ekleme değil.  
  
 Bu kullanıcı arabirimi oluşturmak için içindeki tüm denetimler yerleştirin bir <xref:System.Windows.Forms.SplitContainer> içeren denetim bir <xref:System.Windows.Forms.TreeView> sol panelinde denetim. Sağ taraftaki panelinin <xref:System.Windows.Forms.SplitContainer> denetimi içeren ikinci bir <xref:System.Windows.Forms.SplitContainer> ile denetleyen bir <xref:System.Windows.Forms.ListView> yukarıdaki denetimi bir <xref:System.Windows.Forms.RichTextBox> denetim. Bunlar <xref:System.Windows.Forms.SplitContainer> denetimlerini etkinleştir diğer denetimleri form üzerinde bağımsız yeniden boyutlandırma. Kendi craft özel kullanıcı arabirimleri için bu yordamdaki teknikleri uyarlayabilirsiniz.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-create-an-outlook-style-user-interface-at-design-time"></a>Tasarım zamanında Outlook stilinde bir kullanıcı arabirimi oluşturmak için  
  
1.  Yeni bir Windows uygulama projesi oluşturun. Ayrıntılar için bkz [nasıl yapılır: bir Windows uygulaması projesi oluşturduğunuzda](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  Sürükleme bir <xref:System.Windows.Forms.SplitContainer> gelen denetim **araç** form. İçinde **özellikleri** penceresindeki ayarlayın <xref:System.Windows.Forms.SplitContainer.Dock%2A> özelliğine <xref:System.Windows.Forms.DockStyle.Fill>.  
  
3.  Sürükleme bir <xref:System.Windows.Forms.TreeView> gelen denetim **araç** sol panelinde <xref:System.Windows.Forms.SplitContainer> denetim. İçinde **özellikleri** penceresindeki ayarlayın <xref:System.Windows.Forms.SplitContainer.Dock%2A> özelliğine <xref:System.Windows.Forms.DockStyle.Left> aşağı oka tıklatıldığında gösterilen değer Düzenleyici sol panelinde tıklatarak.  
  
4.  Başka bir sürükleyin <xref:System.Windows.Forms.SplitContainer> gelen denetim **araç**; sağ panelinde yerleştirin <xref:System.Windows.Forms.SplitContainer> formunuza eklediğiniz denetim. İçinde **özellikleri** penceresindeki ayarlayın <xref:System.Windows.Forms.SplitContainer.Dock%2A> özelliğine <xref:System.Windows.Forms.DockStyle.Fill> ve <xref:System.Windows.Forms.SplitContainer.Orientation%2A> özelliğine <xref:System.Windows.Forms.Orientation.Horizontal>.  
  
5.  Sürükleme bir <xref:System.Windows.Forms.ListView> gelen denetim **araç** ikinci üst paneline <xref:System.Windows.Forms.SplitContainer> formunuza eklediğiniz denetim. Ayarlama <xref:System.Windows.Forms.SplitContainer.Dock%2A> özelliği <xref:System.Windows.Forms.ListView> denetimini <xref:System.Windows.Forms.DockStyle.Fill>.  
  
6.  Sürükleme bir <xref:System.Windows.Forms.RichTextBox> gelen denetim **araç** ikinci alt paneline <xref:System.Windows.Forms.SplitContainer> denetim. Ayarlama <xref:System.Windows.Forms.SplitContainer.Dock%2A> özelliği <xref:System.Windows.Forms.RichTextBox> denetimini <xref:System.Windows.Forms.DockStyle.Fill>.  
  
     Bu noktada, uygulamayı çalıştırmak için F5 tuşuna basarsanız, formun Microsoft Outlook için benzer bir üç bölümlük kullanıcı arabirimi görüntüler.  
  
    > [!NOTE]
    >  Ayırıcılar içinde birini üzerinden fare işaretçisini yerleştirdiğinizde <xref:System.Windows.Forms.SplitContainer> denetimleri, iç boyutları yeniden boyutlandırabilirsiniz.  
  
     Bu noktada uygulama geliştirme, gelişmiş kullanıcı arabirimi hazırlanmış. Sonraki adım uygulamanın kendisinin, programlama ile belki de bağlanarak İlerliyor <xref:System.Windows.Forms.TreeView> denetim ve <xref:System.Windows.Forms.ListView> bazı türdeki veri kaynağının kontrol eder. Denetimleri verilerine bağlanma hakkında daha fazla bilgi için bkz: [verileri bağlama ve Windows Forms](../../../../docs/framework/winforms/data-binding-and-windows-forms.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.SplitContainer>  
 [SplitContainer Denetimi](../../../../docs/framework/winforms/controls/splitcontainer-control-windows-forms.md)
