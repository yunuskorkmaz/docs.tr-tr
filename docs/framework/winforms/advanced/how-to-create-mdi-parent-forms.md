---
title: 'Nasıl yapılır: MDI üst formları oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- parent forms
- MDI [Windows Forms], creating forms
ms.assetid: 12c71221-2377-4bb6-b10b-7b4b300fd462
ms.openlocfilehash: 1cc3d813b77ddf8220242f4a1dfc7fe39f9cb520
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54512573"
---
# <a name="how-to-create-mdi-parent-forms"></a>Nasıl yapılır: MDI üst formları oluşturma
> [!IMPORTANT]
>  Bu konuda kullanan <xref:System.Windows.Forms.MainMenu> almıştır denetimi <xref:System.Windows.Forms.MenuStrip> denetimi. <xref:System.Windows.Forms.MainMenu> Denetim korunur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz.  Bir MDI oluşturma hakkında daha fazla bilgi formu kullanarak üst bir <xref:System.Windows.Forms.MenuStrip>, bkz: [nasıl yapılır: MenuStrip ile MDI pencere listesi oluşturma](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-window-list-with-menustrip-windows-forms.md).  
  
 Bir Çoklu belge arabirimi (MDI) uygulaması MDI üst formunun altyapıdır. Bu gibi kullanıcı MDI uygulamayla etkileşimiyle alt pencereleri MDI alt pencereleri içeren biçimidir. Bir MDI üst formu oluşturma Windows Form Tasarımcısı hem de program aracılığıyla kolaydır.  
  
### <a name="to-create-an-mdi-parent-form-at-design-time"></a>Tasarım zamanında MDI üst formu oluşturma  
  
1.  Bir Windows uygulaması projesi oluşturun.  
  
2.  İçinde **özellikleri** penceresinde <xref:System.Windows.Forms.Form.IsMdiContainer%2A> özelliğini **true**.  
  
     Bu, form alt pencereler için bir MDI kapsayıcısı olarak belirler.  
  
    > [!NOTE]
    >  Özellikleri ayarlanırken **özellikleri** penceresinde de ayarlayabilirsiniz `WindowState` özelliğini **Maximized**isterseniz, üst formu olduğunda MDI alt pencereleri yönetmek kolay olduğu gibi ekranı. Ayrıca, edge MDI üst formunun sistem rengi (Windows Sistem Denetim Masası'nda ayarlanan) seçer, arka plan rengi yerine kullanılarak ayarlanan unutmayın <xref:System.Windows.Forms.Control.BackColor%2A?displayProperty=nameWithType> özelliği.  
  
3.  Gelen **araç kutusu**, sürükleyin bir **MenuStrip** forma. Üst düzey menü öğesiyle oluşturma **metin** özelliğini **& Dosya** adlı alt öğeleri ile **& Yeni** ve **& Kapat**. Bir üst düzey menü öğesi adlı oluşturabilir **& Pencere**.  
  
     İlk menüsü oluşturabilir ve çalışma zamanında menü öğelerini gizleme ve ikinci menüsünün açık MDI alt pencereleri izlemek. Bu noktada, MDI üst penceresine oluşturdunuz.  
  
4.  Tuşuna **F5** uygulamayı çalıştırın. MDI alt MDI üst formu içinde çalışan windows oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: MDI alt formları Oluştur](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Çok Belgeli Arabirim (MDI) Uygulamaları](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md)
- [Nasıl yapılır: MDI alt formları oluştur](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)
- [Nasıl yapılır: Etkin MDI alt öğesini belirleme](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md)
- [Nasıl yapılır: Etkin MDI alt öğesine veri gönderme](../../../../docs/framework/winforms/advanced/how-to-send-data-to-the-active-mdi-child.md)
- [Nasıl yapılır: MDI alt formlarını düzenleme](../../../../docs/framework/winforms/advanced/how-to-arrange-mdi-child-forms.md)
