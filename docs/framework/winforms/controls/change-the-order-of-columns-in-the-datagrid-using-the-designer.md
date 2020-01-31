---
title: Tasarımcı kullanarak DataGridView Denetimindeki sütunların sırasını değiştirme
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], order of
- DataGridView control [Windows Forms], column order
- Windows Forms, columns
- data [Windows Forms], displaying
ms.assetid: 7fe52a98-75d6-448c-97a5-65ca2c568c1a
ms.openlocfilehash: be4f67ca6530b74fc90cb50a10463b2378edb933
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743150"
---
# <a name="how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Windows Formları DataGridView Denetiminde Sütunların Sırasını Değiştirme

Bir Windows Forms <xref:System.Windows.Forms.DataGridView> denetimini bir veri kaynağına bağladığınızda, otomatik olarak oluşturulan sütunların görüntüleme sırası veri kaynağı tarafından belirlenir. Bu sıra tercih ettiğiniz değilse, Tasarımcıyı kullanarak sütunların sırasını değiştirebilirsiniz. Ayrıca denetime ilişkisiz sütunlar eklemek ve görüntüleme sıralarını değiştirmek isteyebilirsiniz. Sütun sırasını programlama yoluyla değiştirme hakkında daha fazla bilgi için, bkz. [nasıl yapılır: Windows Forms DataGridView Denetimindeki sütunların sırasını değiştirme](how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md).

Aşağıdaki yordam, bir <xref:System.Windows.Forms.DataGridView> denetimi içeren bir form ile **Windows uygulama** projesi gerektirir. Böyle bir projeyi ayarlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: oluşturma Windows Forms uygulama projesi](/visualstudio/ide/step-1-create-a-windows-forms-application-project) ve [nasıl yapılır: Windows Forms denetim ekleme](how-to-add-controls-to-windows-forms.md).

## <a name="to-change-the-column-order-using-the-designer"></a>Tasarımcı kullanarak sütun sırasını değiştirmek için

1. <xref:System.Windows.Forms.DataGridView> denetiminin sağ üst köşesindeki akıllı etiket glifi ' ne (![akıllı etiket karakter](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) tıklayın ve ardından **Sütunları Düzenle**' yi seçin.

2. **Seçili sütunlar** listesinden bir sütun seçin.

3. Seçili sütun istediğiniz konumda olana kadar **Seçili sütunlar** listesinin sağ tarafındaki yukarı veya aşağı oka tıklayın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- [Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGridView Denetimine Sütunlar Ekleme ve Kaldırma](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [Nasıl yapılır: Windows Forms uygulama projesi oluşturma](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Nasıl yapılır: Windows Forms’a Denetimler Ekleme](how-to-add-controls-to-windows-forms.md)
