---
title: 'Nasıl yapılır: MDI Üst Formları Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- parent forms
- MDI [Windows Forms], creating forms
ms.assetid: 12c71221-2377-4bb6-b10b-7b4b300fd462
ms.openlocfilehash: 8d7a25b771488540d4867143a62c5c2487803a95
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33525197"
---
# <a name="how-to-create-mdi-parent-forms"></a>Nasıl yapılır: MDI Üst Formları Oluşturma
> [!IMPORTANT]
>  Bu konuda kullanan <xref:System.Windows.Forms.MainMenu> almıştır denetim <xref:System.Windows.Forms.MenuStrip> denetim. <xref:System.Windows.Forms.MainMenu> Denetim tutulur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz.  Bir MDI oluşturma hakkında daha fazla bilgi için Form kullanarak üst bir <xref:System.Windows.Forms.MenuStrip>, bkz: [nasıl yapılır: MenuStrip ile MDI pencere listesi oluşturma](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-window-list-with-menustrip-windows-forms.md).  
  
 Bir Çoklu belge arabirimi (MDI) uygulaması MDI üst formu temelidir. Bu kullanıcı ile MDI uygulama müşteriyle etkileşim alt Windows MDI alt pencereleri içeren formdur. MDI üst formu oluşturma Windows Form Tasarımcısı hem program aracılığıyla kolaydır.  
  
### <a name="to-create-an-mdi-parent-form-at-design-time"></a>Tasarım zamanında MDI üst formu oluşturmak için  
  
1.  Bir Windows uygulaması projesi oluşturun.  
  
2.  İçinde **özellikleri** penceresindeki ayarlayın <xref:System.Windows.Forms.Form.IsMdiContainer%2A> özelliğine **doğru**.  
  
     Bu, formun alt windows için bir MDI kapsayıcı olarak belirler.  
  
    > [!NOTE]
    >  Özellikleri ayarlama sırasında **özellikleri** penceresinde de ayarlayabilirsiniz `WindowState` özelliğine **Maximized**isterseniz, üst formu olduğunda MDI alt pencereleri işlemek kolay olduğundan ekranı. Ayrıca, MDI üst formun kenarına sistem rengi (Windows Sistem Denetim Masası'nda kümesi) çeker, yerine arka plan rengi kullanılarak ayarlanan unutmayın <xref:System.Windows.Forms.Control.BackColor%2A?displayProperty=nameWithType> özelliği.  
  
3.  Gelen **araç**, sürükleyin bir **MenuStrip** forma denetim. Bir üst düzey menü öğesi oluşturma **metin** özelliğini **& Dosya** adlı alt menü öğeleriyle **& Yeni** ve **& Kapat**. Ayrıca bir en üst düzey menü öğesi adlı oluşturmak **& penceresi**.  
  
     İlk menü oluşturma ve çalışma zamanında menü öğelerini gizleme ve ikinci menüsü açık MDI alt pencereleri izlemek. Bu noktada, MDI üst penceresine oluşturdunuz.  
  
4.  Tuşuna **F5** uygulamayı çalıştırın. MDI alt MDI üst form içinde çalışan windows oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: MDI alt formları oluşturma](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çok Belgeli Arabirim (MDI) Uygulamaları](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md)  
 [Nasıl yapılır: MDI Alt Formları Oluşturma](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [Nasıl yapılır: Etkin MDI Alt Öğesini Belirleme](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md)  
 [Nasıl yapılır: Etkin MDI Alt Öğesine Veri Gönderme](../../../../docs/framework/winforms/advanced/how-to-send-data-to-the-active-mdi-child.md)  
 [Nasıl yapılır: MDI Alt Formlarını Düzenleme](../../../../docs/framework/winforms/advanced/how-to-arrange-mdi-child-forms.md)
