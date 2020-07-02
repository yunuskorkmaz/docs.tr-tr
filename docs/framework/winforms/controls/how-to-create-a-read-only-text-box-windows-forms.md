---
title: 'Nasıl yapılır: Salt Okunur Metin Kutusu Oluşturma'
description: Düzenlenebilir bir Windows Forms metin kutusunu salt okunurdur Windows Forms metin kutusuna dönüştürme hakkında bilgi edinin.
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [Windows Forms], read-only
- read-only text boxes
- text boxes [Windows Forms], read-only
ms.assetid: 60baa9ab-fa57-44ad-bb7c-61b05aa64296
ms.openlocfilehash: 5baa7c66d5f16560a4ea23861d563b099592957f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619370"
---
# <a name="how-to-create-a-read-only-text-box-windows-forms"></a>Nasıl yapılır: Salt Okunur Metin Kutusu Oluşturma (Windows Forms)

Düzenlenebilir bir Windows Forms metin kutusunu salt bir denetimin içine dönüştürebilirsiniz. Örneğin, metin kutusu genellikle düzenlenmiş bir değer görüntüleyebilir, ancak şu anda uygulamanın durumu nedeniyle olmayabilir.

## <a name="to-create-a-read-only-text-box"></a>Salt okunurdur metin kutusu oluşturmak için

1. <xref:System.Windows.Forms.TextBox>Denetimin <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> özelliğini olarak ayarlayın `true` . Özelliği olarak ayarlandığında `true` , kullanıcılar değişikliklere izin vermeden metin kutusunda metin kaydırma ve vurgulamaya devam edebilir. Bir **kopyalama** komutu metin kutusunda çalışır, ancak **Kes** ve **Yapıştır** komutları değildir.

    > [!NOTE]
    > <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A>Özelliği yalnızca çalışma zamanında kullanıcı etkileşimini etkiler. Metin kutusunun özelliğini değiştirerek metin kutusu içeriğini çalışma zamanında programlı bir şekilde değiştirebilirsiniz <xref:System.Windows.Forms.TextBox.Text%2A> .

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.TextBox>
- [TextBox Denetimine Genel Bakış](textbox-control-overview-windows-forms.md)
- [Nasıl yapılır: Windows Forms TextBox Denetiminde Ekleme Noktasını Belirleme](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [Nasıl yapılır: Windows Forms TextBox Denetimi ile Parola Metin Kutusu Oluşturma](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [Nasıl yapılır: Dizeye Tırnak İşaretleri Koyma](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [Nasıl yapılır: Windows Forms TextBox Denetiminde Metni Seçme](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [Nasıl yapılır: Windows Forms TextBox Denetiminde Birden Fazla Çizgiyi Görüntüleme](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [TextBox Denetimi](textbox-control-windows-forms.md)
