---
title: "Nasıl yapılır: MDI Üst Formları Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parent forms
- MDI [Windows Forms], creating forms
ms.assetid: 12c71221-2377-4bb6-b10b-7b4b300fd462
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f768e01981f75e5e322fd984e73ccf7b185c5e20
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [Birden çok belge arabirimi (MDI) uygulamaları](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md)  
 [Nasıl yapılır: MDI alt formları oluşturma](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [Nasıl yapılır: etkin MDI alt öğesini belirleme](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md)  
 [Nasıl yapılır: etkin MDI alt öğesine veri gönderme](../../../../docs/framework/winforms/advanced/how-to-send-data-to-the-active-mdi-child.md)  
 [Nasıl yapılır: MDI alt formlarını düzenleme](../../../../docs/framework/winforms/advanced/how-to-arrange-mdi-child-forms.md)
