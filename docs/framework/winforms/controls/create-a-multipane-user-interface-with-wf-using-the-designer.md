---
title: 'Nasıl yapılır: Tasarımcı Kullanarak Windows Forms ile Çok Bölmeli bir Kullanıcı Arabirimi Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- user interface [Windows Forms], multipane
- SplitContainer control [Windows Forms], using the designer
- multipane user interface
ms.assetid: c3f9294d-a26c-4198-9242-f237f55f7573
ms.openlocfilehash: 2b72d972d679a47213c0d5ed4270d2c623d713ca
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59082938"
---
# <a name="how-to-create-a-multipane-user-interface-with-windows-forms-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Windows Forms ile Çok Bölmeli bir Kullanıcı Arabirimi Oluşturma
Aşağıdaki yordamda, Microsoft Outlook ile kullanılan benzer çok bölmeli kullanıcı arabirimi oluşturacaksınız bir **klasör** listesinde bir **iletileri** bölmesinde ve **Önizleme** bölmesi. Bu düzenleme formu denetimleri yerleştirme temelde aracılığıyla sağlanır.  
  
 Bir denetim noktası, üst kapsayıcı hangi kenarı bir denetim için fastened belirleyin. Bu nedenle, eğer ayarlarsanız <xref:System.Windows.Forms.SplitContainer.Dock%2A> özelliğini <xref:System.Windows.Forms.DockStyle.Right>, denetimin sağ kenarı sağ, üst denetim kenarına yerleştirilir. Buna ek olarak, yerleşik uç denetimin, kapsayıcı denetimdeki eşleşmesi için yeniden boyutlandırılır. Nasıl hakkında daha fazla bilgi için <xref:System.Windows.Forms.SplitContainer.Dock%2A> özelliği çalıştığını görmek [nasıl yapılır: Windows Forms'da denetimleri](how-to-dock-controls-on-windows-forms.md).  
  
 Bu yordam, düzenleme üzerinde odaklanır <xref:System.Windows.Forms.SplitContainer> ve diğer denetimleri form üzerinde Microsoft Outlook taklit uygulama işlevselliği ekleme değil.  
  
 Bu kullanıcı arabirimi oluşturmak için içindeki tüm denetimleri yerleştirin. bir <xref:System.Windows.Forms.SplitContainer> içeren denetim bir <xref:System.Windows.Forms.TreeView> sol panelde bir denetim. ' In sağ bölmeyi <xref:System.Windows.Forms.SplitContainer> denetimi içeren ikinci bir <xref:System.Windows.Forms.SplitContainer> denetimini bir <xref:System.Windows.Forms.ListView> denetim yukarıdaki bir <xref:System.Windows.Forms.RichTextBox> denetimi. Bunlar <xref:System.Windows.Forms.SplitContainer> denetimleri, formdaki diğer denetimlerin bağımsız yeniden boyutlandırma sağlar. Kendi özel kullanıcı arabirimleri kolaylaştırıyor için bu yordamdaki teknikleri uyarlayabilirsiniz.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-create-an-outlook-style-user-interface-at-design-time"></a>Tasarım zamanında bir Outlook stili kullanıcı arabirimi oluşturmak için  
  
1.  Yeni bir Windows uygulaması projesi oluşturun (**dosya** > **yeni** > **proje** > **Visual C#** veya **Visual Basic** > **Klasik Masaüstü** > **Windows Forms uygulamalarındaki**).  
  
2.  Sürükleme bir <xref:System.Windows.Forms.SplitContainer> denetimi **araç kutusu** form. İçinde **özellikleri** penceresinde <xref:System.Windows.Forms.SplitContainer.Dock%2A> özelliğini <xref:System.Windows.Forms.DockStyle.Fill>.  
  
3.  Sürükleme bir <xref:System.Windows.Forms.TreeView> denetimi **araç kutusu** Sol paneli <xref:System.Windows.Forms.SplitContainer> denetimi. İçinde **özellikleri** penceresinde <xref:System.Windows.Forms.SplitContainer.Dock%2A> özelliğini <xref:System.Windows.Forms.DockStyle.Left> aşağı oka tıklandığında gösterilen değer Düzenleyicisi'nde sol paneli tıklayarak.  
  
4.  Başka bir sürükleyin <xref:System.Windows.Forms.SplitContainer> denetimi **araç kutusu**; sağ panelde yerleştirin <xref:System.Windows.Forms.SplitContainer> formunuza eklediğiniz denetimi. İçinde **özellikleri** penceresinde <xref:System.Windows.Forms.SplitContainer.Dock%2A> özelliğini <xref:System.Windows.Forms.DockStyle.Fill> ve <xref:System.Windows.Forms.SplitContainer.Orientation%2A> özelliğini <xref:System.Windows.Forms.Orientation.Horizontal>.  
  
5.  Sürükle bir <xref:System.Windows.Forms.ListView> denetimi **araç kutusu** ikinci üst paneline <xref:System.Windows.Forms.SplitContainer> formunuza eklediğiniz denetimi. Ayarlama <xref:System.Windows.Forms.SplitContainer.Dock%2A> özelliği <xref:System.Windows.Forms.ListView> denetimini <xref:System.Windows.Forms.DockStyle.Fill>.  
  
6.  Sürükleme bir <xref:System.Windows.Forms.RichTextBox> denetimi **araç kutusu** ikinci alt paneline <xref:System.Windows.Forms.SplitContainer> denetimi. Ayarlama <xref:System.Windows.Forms.SplitContainer.Dock%2A> özelliği <xref:System.Windows.Forms.RichTextBox> denetimini <xref:System.Windows.Forms.DockStyle.Fill>.  
  
     Bu noktada, uygulamayı çalıştırmak için F5 tuşuna basarsanız, form, Microsoft Outlook benzer, üç bölümden kullanıcı arabirimini görüntüler.  
  
    > [!NOTE]
    >  Ayırıcılar içinde birini üzerine fare işaretçisini yerleştirdiğinizde <xref:System.Windows.Forms.SplitContainer> denetimleri, iç boyutları yeniden boyutlandırabilirsiniz.  
  
     Bu noktada uygulama geliştirmesinde gelişmiş kullanıcı arabirimi hazırlanmış. Sonraki adım uygulamanın kendisi, programlama ile belki de bağlanarak İlerliyor <xref:System.Windows.Forms.TreeView> denetimi ve <xref:System.Windows.Forms.ListView> bazı türdeki veri kaynağının denetimleri. Denetimleri verilere bağlanma hakkında daha fazla bilgi için bkz. [veri bağlama ve Windows Forms](../data-binding-and-windows-forms.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.SplitContainer>
- [SplitContainer Denetimi](splitcontainer-control-windows-forms.md)
