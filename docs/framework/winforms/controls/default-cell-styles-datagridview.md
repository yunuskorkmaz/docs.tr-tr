---
title: 'Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGridView Denetimi İçin Varsayılan Hücre Stilleri ve Veri Biçimleri Ayarlama'
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], setting styles
- data formats
- data [Windows Forms], setting formats
ms.assetid: fc6da49f-8942-41da-b49f-b2afc38cc656
ms.openlocfilehash: 6d7d867b7c9e83b68589e046565bfb0199692f5f
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69658507"
---
# <a name="how-to-set-default-cell-styles-and-data-formats-for-the-windows-forms-datagridview-control-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGridView Denetimi İçin Varsayılan Hücre Stilleri ve Veri Biçimleri Ayarlama

<xref:System.Windows.Forms.DataGridView> Denetim, tüm denetim için varsayılan hücre stillerini ve hücre veri biçimlerini, belirli sütunlarda, satır ve sütun üstbilgilerini ve farklı satırların bir muhasebe etkisi oluşturmasını sağlar. Tüm denetim için ayarlanan varsayılan stiller, sütunlar ve alternatif satırlar için ayarlanan varsayılan stiller tarafından geçersiz kılınır. Ayrıca, ayrı satırlar ve hücreler için kodda ayarladığınız stiller varsayılan stilleri geçersiz kılar.

Hücre stilleri hakkında daha fazla bilgi için [Windows Forms DataGridView Denetimindeki Hücre stilleri](cell-styles-in-the-windows-forms-datagridview-control.md)bölümüne bakın. Alternatif satırlara yönelik stiller ayarlamak için bkz [. nasıl yapılır: Tasarımcıyı](set-alternating-row-styles-for-the-datagrid-using-the-designer.md)kullanarak Windows Forms DataGridView denetimi Için alternatif satır stillerini ayarlayın.

Ayrıca, denetime eklenecek tüm satırları etkilemek <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> için özelliğini kullanarak stilleri ayarlayabilirsiniz. Satır şablonu hakkında daha fazla bilgi için bkz [. nasıl yapılır: Windows Forms DataGridView Denetimindeki](use-the-row-template-to-customize-rows-in-the-datagrid.md)satırları özelleştirmek için satır şablonunu kullanın.

Aşağıdaki yordamlarda bir <xref:System.Windows.Forms.DataGridView> denetim içeren bir form ile **Windows uygulama** projesi gerekir. Böyle bir projeyi ayarlama hakkında daha fazla bilgi için bkz [. nasıl yapılır: Windows Forms bir uygulama projesi](/visualstudio/ide/step-1-create-a-windows-forms-application-project) oluşturun ve [şunları yapın: Windows Forms](how-to-add-controls-to-windows-forms.md)denetimleri ekleyin.

### <a name="to-set-default-styles-for-all-cells-in-the-control"></a>Denetimdeki tüm hücreler için varsayılan stilleri ayarlamak için

1. <xref:System.Windows.Forms.DataGridView> Tasarımcıda denetimi seçin.

2. **Özellikler** penceresinde![,, veya <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A>özelliğininyanındaki](./media/visual-studio-ellipsis-button.png) <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>üç nokta düğmesini (Visual Studio Özellikler penceresi) (...) tıklayın. <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> **CellStyle Builder** iletişim kutusu görüntülenir.

3. Seçimlerinizi onaylamak için **Önizleme** bölmesini kullanarak özellikleri ayarlayarak stili tanımlayın.

> [!NOTE]
> Görsel stiller etkinleştirilmişse, satır ve sütun başlıkları (hariç <xref:System.Windows.Forms.DataGridView.TopLeftHeaderCell%2A>) otomatik olarak geçerli Tema tarafından stillendirilmiş <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> ve <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> özellik değerlerini geçersiz kılar.
>
> Tasarımcıyı kullanarak seçilen <xref:System.Windows.Forms.DataGridView> birden fazla denetim için hücre stilleri ayarlayabilirsiniz, ancak yalnızca değiştirmek istediğiniz hücre stili özelliği için özdeş değerler varsa. Bu özellik için herhangi bir hücre stili farklıysa, **CellStyle Builder** Iletişim kutusunun **Özellikler** penceresi boş olur.

### <a name="to-set-default-styles-for-cells-in-individual-columns"></a>Tek sütunlardaki hücrelerin varsayılan stillerini ayarlamak için

1. Tasarımcıda <xref:System.Windows.Forms.DataGridView> denetime sağ tıklayın ve **Sütunları Düzenle**' yi seçin.

2. **Seçili sütunlar** listesinden bir sütun seçin.

3. **Sütun özellikleri** kılavuzunda,![ <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> özelliğin yanındaki üç nokta düğmesini (Visual Studio](./media/visual-studio-ellipsis-button.png)'nun Özellikler penceresi) üç nokta düğmesine (...) tıklayın. **CellStyle Builder** iletişim kutusu görüntülenir.

4. Seçimlerinizi onaylamak için **Önizleme** bölmesini kullanarak özellikleri ayarlayarak stili tanımlayın.

### <a name="to-format-data-in-cells"></a>Hücrelerdeki verileri biçimlendirmek için

1. Bir varsayılan hücre stili özelliğiyle ilgili bir **CellStyle Builder** iletişim kutusu göstermek için Yukarıdaki yordamlardan birini kullanın.

2. **CellStyle Builder** iletişim kutusunda,![ <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> özelliğin yanındaki üç nokta düğmesini (Visual Studio](./media/visual-studio-ellipsis-button.png)'nun Özellikler penceresi) tıklatın. **Biçim dizesi** iletişim kutusu görüntülenir.

3. Bir biçim türü seçin, sonra, Seçimlerinizi onaylamak için **örnek** kutusunu kullanarak türün ayrıntılarını (örneğin, görüntülenecek ondalık basamak sayısı) değiştirin.

4. <xref:System.Windows.Forms.DataGridView> Denetimi null değerleri içermesi muhtemel bir veri kaynağına bağlıyorsanız **null değer** metin kutusunu girin. Bu değer, hücre değeri null başvuruya eşitse görüntülenir (`Nothing` Visual Basic) veya. <xref:System.DBNull.Value?displayProperty=nameWithType>

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A?displayProperty=nameWithType>
- [Windows Forms DataGridView Denetimindeki Hücre Stilleri](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Nasıl yapılır: Tasarımcıyı kullanarak Windows Forms DataGridView denetimi için alternatif satır stillerini ayarlama](set-alternating-row-styles-for-the-datagrid-using-the-designer.md)
- [Nasıl yapılır: Windows Forms uygulama projesi oluşturma](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Nasıl yapılır: Windows Forms denetim ekleme](how-to-add-controls-to-windows-forms.md)
