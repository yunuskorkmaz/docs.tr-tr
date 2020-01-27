---
title: Tasarımcıyı kullanarak DataGridView denetimi için alternatif satır stillerini ayarlama
ms.date: 03/30/2017
helpviewer_keywords:
- ledger-like formats
- DataGridView control [Windows Forms], row style alternation
- Windows Forms, rows
- rows [Windows Forms], alternating
- data [Windows Forms], displaying
ms.assetid: 02373442-bf94-4470-9f8a-e44c4a9d5b88
ms.openlocfilehash: 74f65d03a359136de943f8a2937ed5e5f1e62519
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743053"
---
# <a name="how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Windows Formları DataGridView Denetimi İçin Alternatif Satır Stillerini Ayarlama

Tablo verileri genellikle farklı satırlarda arka plan rengine sahip olan bir defter benzeri biçimde sunulur. Bu biçim, özellikle çok sayıda sütunu olan geniş tablolar ile, kullanıcıların her satırda hangi hücrelerin olduğunu söylemesini kolaylaştırır.

<xref:System.Windows.Forms.DataGridView> denetimiyle, değişen satırlar için tüm stil bilgilerini belirtebilirsiniz. Alternatif satırları ayırt etmek için arka plan rengine ek olarak, ön plan rengi ve yazı tipi gibi stil özellikleri kullanabilirsiniz. Daha fazla bilgi için [Windows Forms DataGridView Denetimindeki Hücre stilleri](cell-styles-in-the-windows-forms-datagridview-control.md)bölümüne bakın.

Aşağıdaki yordam, bir <xref:System.Windows.Forms.DataGridView> denetimi içeren bir form ile **Windows uygulama** projesi gerektirir. Böyle bir projeyi ayarlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: oluşturma Windows Forms uygulama projesi](/visualstudio/ide/step-1-create-a-windows-forms-application-project) ve [nasıl yapılır: Windows Forms denetim ekleme](how-to-add-controls-to-windows-forms.md).

### <a name="define-styles-for-alternating-rows"></a>Değişen satırlar için stiller tanımlayın

1. Tasarımcıda <xref:System.Windows.Forms.DataGridView> denetimini seçin.

2. **Özellikler** penceresinde, <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> özelliğinin yanındaki Visual Studio.](./media/visual-studio-ellipsis-button.png)) Özellikler penceresi üç nokta düğmesini (...)![tıklatın.

3. **CellStyle Builder** iletişim kutusunda, özellikleri ayarlayarak stili tanımlayın ve Seçimlerinizi onaylamak için **Önizleme** bölmesini kullanın. Belirttiğiniz stiller, ikinci bir ile başlayan denetimde görüntülenen her bir satır için kullanılır.

4. Kalan satırların stillerini tanımlamak için <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> özelliğini kullanarak 2. ve 3. adımları yineleyin.

    > [!NOTE]
    > Hücreler, birden çok özelliklerden devralınan stiller kullanılarak görüntülenir. Stil devralma hakkında daha fazla bilgi için bkz. [Windows Forms DataGridView Denetimindeki Hücre stilleri](cell-styles-in-the-windows-forms-datagridview-control.md).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- [Windows Forms DataGridView Denetimindeki Hücre Stilleri](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetimindeki Temel Biçim ve Stiller](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetimi ile Tasarımcı Kullanımı](using-the-designer-with-the-windows-forms-datagridview-control.md)
- [Nasıl yapılır: Windows Forms uygulama projesi oluşturma](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Nasıl yapılır: Windows Forms’a Denetimler Ekleme](how-to-add-controls-to-windows-forms.md)
