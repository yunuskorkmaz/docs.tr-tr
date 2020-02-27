---
title: Tasarımcı kullanarak bir DataGridView sütununun türünü değiştirme
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], types
- DataGridView control [Windows Forms], changing column type
- data [Windows Forms], displaying
ms.assetid: 7f994d45-600d-4190-a187-35803214b40c
ms.openlocfilehash: 470f350a4791a3db39d08ab7992d86eb7b2e270a
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628624"
---
# <a name="how-to-change-the-type-of-a-windows-forms-datagridview-column-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Windows Formları DataGridView Sütununun Türünü Değiştirme
Bazen, zaten bir Windows Forms <xref:System.Windows.Forms.DataGridView> denetimine eklenmiş olan bir sütunun türünü değiştirmek isteyeceksiniz. Örneğin, denetimi bir veri kaynağına bağladığınızda otomatik olarak oluşturulan sütunlardan bazılarının türlerini değiştirmek isteyebilirsiniz. Bu, görüntülenen tabloda ilgili tablodaki satırlara yabancı anahtarlar içeren sütunlar olduğunda faydalıdır. Bu durumda, bu yabancı anahtarları görüntüleyen metin kutusu sütunlarını, ilişkili tablodan daha anlamlı değerler görüntüleyen Birleşik giriş kutusu sütunları ile değiştirmek isteyebilirsiniz.

 Aşağıdaki yordam, bir <xref:System.Windows.Forms.DataGridView> denetimi içeren bir form ile **Windows uygulama** projesi gerektirir. Böyle bir projeyi ayarlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: oluşturma Windows Forms uygulama projesi](/visualstudio/ide/step-1-create-a-windows-forms-application-project) ve [nasıl yapılır: Windows Forms denetim ekleme](how-to-add-controls-to-windows-forms.md).

### <a name="to-change-the-type-of-a-column-using-the-designer"></a>Tasarımcıyı kullanarak bir sütunun türünü değiştirmek için

1. <xref:System.Windows.Forms.DataGridView> denetiminin sağ üst köşesinde bulunan Tasarımcı eylemleri glifinin (![küçük siyah ok](./media/designer-actions-glyph.gif)) tıklayın ve ardından **Sütunları Düzenle**' yi seçin.

2. **Seçili sütunlar** listesinden bir sütun seçin.

3. **Sütun özellikleri** kılavuzunda `ColumnType` özelliğini yeni sütun türü olarak ayarlayın.

    > [!NOTE]
    > `ColumnType` özelliği, sütun türünü temsil eden sınıfı gösteren bir yalnızca tasarım zamanı özelliğidir. Bir sütun sınıfında tanımlanan gerçek bir özellik değildir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn>
- [Nasıl yapılır: Windows Forms uygulama projesi oluşturma](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Nasıl yapılır: Windows Forms’a Denetimler Ekleme](how-to-add-controls-to-windows-forms.md)
