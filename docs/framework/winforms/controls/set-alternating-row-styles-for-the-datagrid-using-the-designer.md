---
title: 'Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGridView Denetimi İçin Alternatif Satır Stillerini Ayarlama'
ms.date: 03/30/2017
helpviewer_keywords:
- ledger-like formats
- DataGridView control [Windows Forms], row style alternation
- Windows Forms, rows
- rows [Windows Forms], alternating
- data [Windows Forms], displaying
ms.assetid: 02373442-bf94-4470-9f8a-e44c4a9d5b88
ms.openlocfilehash: 1be746d4cce36344e034692a0e2e8e6a9e9320d5
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040435"
---
# <a name="how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGridView Denetimi İçin Alternatif Satır Stillerini Ayarlama

Tablo verileri genellikle farklı satırlarda arka plan rengine sahip olan bir defter benzeri biçimde sunulur. Bu biçim, özellikle çok sayıda sütunu olan geniş tablolar ile, kullanıcıların her satırda hangi hücrelerin olduğunu söylemesini kolaylaştırır.

<xref:System.Windows.Forms.DataGridView> Denetimiyle, alternatif satırlar için tüm stil bilgilerini belirtebilirsiniz. Alternatif satırları ayırt etmek için arka plan rengine ek olarak, ön plan rengi ve yazı tipi gibi stil özellikleri kullanabilirsiniz. Daha fazla bilgi için [Windows Forms DataGridView Denetimindeki Hücre stilleri](cell-styles-in-the-windows-forms-datagridview-control.md)bölümüne bakın.

Aşağıdaki yordam, bir <xref:System.Windows.Forms.DataGridView> denetim içeren bir form ile **Windows uygulama** projesi gerektirir. Böyle bir projeyi ayarlama hakkında daha fazla bilgi için bkz [. nasıl yapılır: Windows Forms bir uygulama projesi](/visualstudio/ide/step-1-create-a-windows-forms-application-project) oluşturun ve [şunları yapın: Windows Forms](how-to-add-controls-to-windows-forms.md)denetimleri ekleyin.


### <a name="define-styles-for-alternating-rows"></a>Değişen satırlar için stiller tanımlayın

1. <xref:System.Windows.Forms.DataGridView> Tasarımcıda denetimi seçin.

2. **Özellikler** penceresinde,![ özelliğin<xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> yanındaki üç nokta düğmesini (Visual Studio](./media/visual-studio-ellipsis-button.png)Özellikler penceresi) (...) tıklayın.

3. **CellStyle Builder** iletişim kutusunda, özellikleri ayarlayarak stili tanımlayın ve Seçimlerinizi onaylamak için **Önizleme** bölmesini kullanın. Belirttiğiniz stiller, ikinci bir ile başlayan denetimde görüntülenen her bir satır için kullanılır.

4. Kalan satırların stillerini tanımlamak için <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> özelliği kullanarak 2. ve 3. adımları yineleyin.

    > [!NOTE]
    > Hücreler, birden çok özelliklerden devralınan stiller kullanılarak görüntülenir. Stil devralma hakkında daha fazla bilgi için bkz. [Windows Forms DataGridView Denetimindeki Hücre stilleri](cell-styles-in-the-windows-forms-datagridview-control.md).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- [Windows Forms DataGridView Denetimindeki Hücre Stilleri](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetimindeki Temel Biçim ve Stiller](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetimi ile Tasarımcı Kullanımı](using-the-designer-with-the-windows-forms-datagridview-control.md)
- [Nasıl yapılır: Windows Forms uygulama projesi oluşturma](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Nasıl yapılır: Windows Forms denetim ekleme](how-to-add-controls-to-windows-forms.md)
