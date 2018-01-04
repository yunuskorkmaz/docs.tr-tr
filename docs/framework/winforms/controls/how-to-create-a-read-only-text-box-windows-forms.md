---
title: "Nasıl yapılır: Salt Okunur Metin Kutusu Oluşturma (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TextBox control [Windows Forms], read-only
- read-only text boxes
- text boxes [Windows Forms], read-only
ms.assetid: 60baa9ab-fa57-44ad-bb7c-61b05aa64296
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 264ef1a7c1f121f889d57dcb0e36e216610418fe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-read-only-text-box-windows-forms"></a>Nasıl yapılır: Salt Okunur Metin Kutusu Oluşturma (Windows Forms)
Düzenlenebilir bir Windows Forms metin kutusunda salt okunur denetime dönüştürebilirsiniz. Örneğin, metin kutusunun genellikle düzenlenebilir ancak uygulama durumu nedeniyle şu anda olmayabilir bir değer görüntüleyebilir.  
  
### <a name="to-create-a-read-only-text-box"></a>Salt okunur metin kutusu oluşturmak için  
  
1.  Ayarlama <xref:System.Windows.Forms.TextBox> denetimin <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> özelliğine `true`. Ayarlanan özelliği ile `true`, kullanıcılar, hala kaydırın ve bir metin kutusundaki değişiklikler vermeden vurgulayın. A **kopya** komuttur işlevsel bir metin kutusunda, ancak **Kes** ve **Yapıştır** komutları değildir.  
  
    > [!NOTE]
    >  <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> Özelliği yalnızca çalışma zamanında kullanıcı etkileşimi etkiler. Hala metin kutusu içeriğinin program aracılığıyla çalışma zamanında değiştirerek değiştirebilirsiniz <xref:System.Windows.Forms.TextBox.Text%2A> metin kutusunun özelliği.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.TextBox>  
 [TextBox Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [Nasıl yapılır: Windows Forms TextBox Denetiminde Ekleme Noktasını Belirleme](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [Nasıl yapılır: Windows Forms TextBox Denetimi ile Parola Metin Kutusu Oluşturma](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [Nasıl yapılır: Dizeye Tırnak İşaretleri Koyma](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 [Nasıl yapılır: Windows Forms TextBox Denetiminde Metni Seçme](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [Nasıl yapılır: Windows Forms TextBox Denetiminde Birden Fazla Çizgiyi Görüntüleme](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 [TextBox Denetimi](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
