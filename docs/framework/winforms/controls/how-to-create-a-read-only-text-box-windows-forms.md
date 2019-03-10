---
title: 'Nasıl yapılır: Salt okunur metin kutusu (Windows Forms) oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [Windows Forms], read-only
- read-only text boxes
- text boxes [Windows Forms], read-only
ms.assetid: 60baa9ab-fa57-44ad-bb7c-61b05aa64296
ms.openlocfilehash: 0a29e1c4dcb0bcc8e7d292725e64ea967e160d06
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707761"
---
# <a name="how-to-create-a-read-only-text-box-windows-forms"></a>Nasıl yapılır: Salt okunur metin kutusu (Windows Forms) oluşturma
Düzenlenebilir bir Windows Forms metin kutusunda salt okunur denetimine dönüştürebilirsiniz. Örneğin, metin kutusuna bir değer genellikle düzenlenebilir ancak şu anda uygulamanın durumu nedeniyle olmayabilir görüntüleyebilir.  
  
### <a name="to-create-a-read-only-text-box"></a>Bir salt okunur metin kutusu oluşturma  
  
1.  Ayarlama <xref:System.Windows.Forms.TextBox> denetimin <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> özelliğini `true`. Ayarlanan özelliği ile `true`, kullanıcılar hala kaydırın ve metin kutusundaki değişiklikler vermeden vurgulayın. A **kopyalama** komut işlevsel bir metin kutusunda, ancak **Kes** ve **Yapıştır** komutları değildir.  
  
    > [!NOTE]
    >  <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> Özelliği yalnızca çalışma zamanında kullanıcı etkileşimi etkiler. Yine de metin kutusu içeriklerinin program aracılığıyla çalışma zamanında değiştirerek değiştirebilirsiniz <xref:System.Windows.Forms.TextBox.Text%2A> metin kutusunun özelliği.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.TextBox>
- [TextBox Denetimine Genel Bakış](textbox-control-overview-windows-forms.md)
- [Nasıl yapılır: Windows Forms TextBox denetiminde ekleme noktasını belirleme](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [Nasıl yapılır: Windows Forms TextBox denetimi ile parola metin kutusu oluşturma](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [Nasıl yapılır: Dizeye tırnak işaretleri koyma](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [Nasıl yapılır: Windows Forms TextBox denetiminde metni Seç](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [Nasıl yapılır: Windows Forms TextBox denetiminde birden çok satır görüntüleme](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [TextBox Denetimi](textbox-control-windows-forms.md)
