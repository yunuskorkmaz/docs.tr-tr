---
title: 'Nasıl yapılır: MDI üst formları oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- parent forms
- MDI [Windows Forms], creating forms
ms.assetid: 12c71221-2377-4bb6-b10b-7b4b300fd462
ms.openlocfilehash: 5da7f1a53412cf30a5898fec096aaa01e3aa65d2
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57722990"
---
# <a name="how-to-create-mdi-parent-forms"></a>Nasıl yapılır: MDI üst formları oluşturma
> [!IMPORTANT]
>  Bu konuda kullanan <xref:System.Windows.Forms.MainMenu> almıştır denetimi <xref:System.Windows.Forms.MenuStrip> denetimi. <xref:System.Windows.Forms.MainMenu> Denetim korunur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz.  Bir MDI oluşturma hakkında daha fazla bilgi formu kullanarak üst bir <xref:System.Windows.Forms.MenuStrip>, bkz: [nasıl yapılır: MenuStrip ile MDI pencere listesi oluşturma](../controls/how-to-create-an-mdi-window-list-with-menustrip-windows-forms.md).  
  
 Bir Çoklu belge arabirimi (MDI) uygulaması MDI üst formunun altyapıdır. Bu gibi kullanıcı MDI uygulamayla etkileşimiyle alt pencereleri MDI alt pencereleri içeren biçimidir. Bir MDI üst formu oluşturma Windows Form Tasarımcısı hem de program aracılığıyla kolaydır.  
  
### <a name="to-create-an-mdi-parent-form-at-design-time"></a>Tasarım zamanında MDI üst formu oluşturma  
  
1.  Bir Windows uygulaması projesi oluşturun.  
  
2.  İçinde **özellikleri** penceresinde <xref:System.Windows.Forms.Form.IsMdiContainer%2A> özelliğini **true**.  
  
     Bu, form alt pencereler için bir MDI kapsayıcısı olarak belirler.  
  
    > [!NOTE]
    >  Özellikleri ayarlanırken **özellikleri** penceresinde de ayarlayabilirsiniz `WindowState` özelliğini **Maximized**isterseniz, üst formu olduğunda MDI alt pencereleri yönetmek kolay olduğu gibi ekranı. Ayrıca, edge MDI üst formunun sistem rengi (Windows Sistem Denetim Masası'nda ayarlanan) seçer, arka plan rengi yerine kullanılarak ayarlanan unutmayın <xref:System.Windows.Forms.Control.BackColor%2A?displayProperty=nameWithType> özelliği.  
  
3.  Gelen **araç kutusu**, sürükleyin bir **MenuStrip** forma. Üst düzey menü öğesiyle oluşturma **metin** özelliğini **& Dosya** adlı alt öğeleri ile **& Yeni** ve **& Kapat**. Bir üst düzey menü öğesi adlı oluşturabilir **& Pencere**.  
  
     İlk menüsü oluşturabilir ve çalışma zamanında menü öğelerini gizleme ve ikinci menüsünün açık MDI alt pencereleri izlemek. Bu noktada, MDI üst penceresine oluşturdunuz.  
  
4.  Tuşuna **F5** uygulamayı çalıştırın. MDI alt MDI üst formu içinde çalışan windows oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: MDI alt formları Oluştur](how-to-create-mdi-child-forms.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Çok Belgeli Arabirim (MDI) Uygulamaları](multiple-document-interface-mdi-applications.md)
- [Nasıl yapılır: MDI alt formları oluştur](how-to-create-mdi-child-forms.md)
- [Nasıl yapılır: Etkin MDI alt öğesini belirleme](how-to-determine-the-active-mdi-child.md)
- [Nasıl yapılır: Etkin MDI alt öğesine veri gönderme](how-to-send-data-to-the-active-mdi-child.md)
- [Nasıl yapılır: MDI alt formlarını düzenleme](how-to-arrange-mdi-child-forms.md)
