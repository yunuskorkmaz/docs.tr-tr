---
title: 'Nasıl yapılır: Salt okunurdur metin kutusu oluşturma (Windows Forms)'
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [Windows Forms], read-only
- read-only text boxes
- text boxes [Windows Forms], read-only
ms.assetid: 60baa9ab-fa57-44ad-bb7c-61b05aa64296
ms.openlocfilehash: 18d2f5ed2530957487ac25c3eb6240f8bc50a938
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971938"
---
# <a name="how-to-create-a-read-only-text-box-windows-forms"></a>Nasıl yapılır: Salt okunurdur metin kutusu oluşturma (Windows Forms)

Düzenlenebilir bir Windows Forms metin kutusunu salt bir denetimin içine dönüştürebilirsiniz. Örneğin, metin kutusu genellikle düzenlenmiş bir değer görüntüleyebilir, ancak şu anda uygulamanın durumu nedeniyle olmayabilir.

## <a name="to-create-a-read-only-text-box"></a>Salt okunurdur metin kutusu oluşturmak için

1. Denetimin özelliğini olarak`true`ayarlayın. <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> <xref:System.Windows.Forms.TextBox> Özelliği olarak `true`ayarlandığında, kullanıcılar değişikliklere izin vermeden metin kutusunda metin kaydırma ve vurgulamaya devam edebilir. Bir **kopyalama** komutu metin kutusunda çalışır, ancak **Kes** ve **Yapıştır** komutları değildir.

    > [!NOTE]
    > <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> Özelliği yalnızca çalışma zamanında kullanıcı etkileşimini etkiler. Metin kutusunun <xref:System.Windows.Forms.TextBox.Text%2A> özelliğini değiştirerek metin kutusu içeriğini çalışma zamanında programlı bir şekilde değiştirebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.TextBox>
- [TextBox Denetimine Genel Bakış](textbox-control-overview-windows-forms.md)
- [Nasıl yapılır: Windows Forms TextBox denetimindeki ekleme noktasını denetleme](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [Nasıl yapılır: Windows Forms TextBox denetimiyle bir parola metin kutusu oluşturma](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [Nasıl yapılır: Bir dizeye tırnak Işareti koyma](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [Nasıl yapılır: Windows Forms metin kutusu denetimindeki metni seçme](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [Nasıl yapılır: Windows Forms TextBox denetiminde birden çok satırı görüntüleme](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [TextBox Denetimi](textbox-control-windows-forms.md)
