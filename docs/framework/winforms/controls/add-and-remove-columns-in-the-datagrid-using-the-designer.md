---
title: Tasarımcı kullanarak DataGridView denetiminde sütun ekleme ve kaldırma
ms.date: 03/30/2017
f1_keywords:
- vs.DataGridViewAddColumnDialog
helpviewer_keywords:
- DataGridView control [Windows Forms], adding columns
- DataGridView control [Windows Forms], removing columns
ms.assetid: 9e709f35-0a8c-4e7e-b4c4-bacb7a834077
ms.openlocfilehash: 717a0074f0750352a23b90a9b6e5eab1dc6c925a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732353"
---
# <a name="how-to-add-and-remove-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Windows Formları DataGridView Denetimine Sütunlar Ekleme ve Kaldırma
Windows Forms <xref:System.Windows.Forms.DataGridView> denetiminin verileri görüntülemesi için sütun içermesi gerekir. Denetimi el ile doldurmayı planlıyorsanız sütunları kendiniz eklemeniz gerekir. Alternatif olarak, denetimi bir veri kaynağına bağlayabilir ve sütunları otomatik olarak oluşturur ve doldurur. Veri kaynağı göstermek istediğinizden daha fazla sütun içeriyorsa, istenmeyen sütunları kaldırabilirsiniz.

 Aşağıdaki yordamlar, bir <xref:System.Windows.Forms.DataGridView> denetimi içeren bir form ile **Windows uygulama** projesi gerektirir. Böyle bir projeyi ayarlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: oluşturma Windows Forms uygulama projesi](/visualstudio/ide/step-1-create-a-windows-forms-application-project) ve [nasıl yapılır: Windows Forms denetim ekleme](how-to-add-controls-to-windows-forms.md).

## <a name="to-add-a-column-using-the-designer"></a>Tasarımcıyı kullanarak sütun eklemek için

1. <xref:System.Windows.Forms.DataGridView> denetiminin sağ üst köşesindeki akıllı etiket glifi ' ne (![akıllı etiket karakter](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) tıklayın ve ardından **sütun Ekle**' yi seçin.

2. **Sütun Ekle** iletişim kutusunda, veri kaynağı **sütunu** seçeneğini belirleyin ve veri kaynağından bir sütun seçin ya da **ilişkisiz sütun** seçeneğini belirleyin ve belirtilen alanları kullanarak sütunu tanımlayın.

3. Sütunu eklemek için **Ekle** düğmesine tıklayın, var olan sütunlar denetim görüntüleme alanını önceden doldurmadığında tasarımcıda görünmesine neden olur.

    > [!NOTE]
    > Sütun özelliklerini, denetimin akıllı etiketinden erişebileceğiniz **Sütunları Düzenle** iletişim kutusunda değiştirebilirsiniz.

## <a name="to-remove-a-column-using-the-designer"></a>Tasarımcıyı kullanarak bir sütunu kaldırmak için

1. Denetimin akıllı etiketindeki **Sütunları Düzenle** ' yi seçin.

2. **Seçili sütunlar** listesinden bir sütun seçin.

3. Sütunu silmek için **Kaldır** düğmesine tıklayın ve tasarımcı 'nın kaybolmasına neden olur.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- [Nasıl yapılır: Windows Forms uygulama projesi oluşturma](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Nasıl yapılır: Windows Forms’a Denetimler Ekleme](how-to-add-controls-to-windows-forms.md)
