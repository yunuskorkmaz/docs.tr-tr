---
title: Tasarımcıyı kullanarak DataGridView denetimi için varsayılan hücre stilleri ve veri biçimleri ayarlama
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], setting styles
- data formats
- data [Windows Forms], setting formats
ms.assetid: fc6da49f-8942-41da-b49f-b2afc38cc656
ms.openlocfilehash: ca602fa15e4648550bfa171a9c3abd057e930eca
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731362"
---
# <a name="how-to-set-default-cell-styles-and-data-formats-for-the-windows-forms-datagridview-control-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Windows Formları DataGridView Denetimi İçin Varsayılan Hücre Stilleri ve Veri Biçimleri Ayarlama

<xref:System.Windows.Forms.DataGridView> denetimi, tüm denetim için varsayılan hücre stillerini ve hücre veri biçimlerini, satır ve sütun üstbilgilerini, satır ve sütun üstbilgilerini ve değişen satırların bir muhasebe etkisi oluşturmasını sağlar. Tüm denetim için ayarlanan varsayılan stiller, sütunlar ve alternatif satırlar için ayarlanan varsayılan stiller tarafından geçersiz kılınır. Ayrıca, ayrı satırlar ve hücreler için kodda ayarladığınız stiller varsayılan stilleri geçersiz kılar.

Hücre stilleri hakkında daha fazla bilgi için [Windows Forms DataGridView Denetimindeki Hücre stilleri](cell-styles-in-the-windows-forms-datagridview-control.md)bölümüne bakın. Alternatif satırlara yönelik stiller ayarlamak için, bkz. [nasıl yapılır: tasarımcı kullanarak Windows Forms DataGridView denetimi Için alternatif satır stillerini ayarlama](set-alternating-row-styles-for-the-datagrid-using-the-designer.md).

Ayrıca, denetime eklenecek tüm satırları etkilemek için <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> özelliğini kullanarak stiller ayarlayabilirsiniz. Satır şablonu hakkında daha fazla bilgi için bkz. [nasıl yapılır: Windows Forms DataGridView Denetimindeki satırları özelleştirmek Için satır şablonunu kullanma](use-the-row-template-to-customize-rows-in-the-datagrid.md).

Aşağıdaki yordamlar, bir <xref:System.Windows.Forms.DataGridView> denetimi içeren bir form ile **Windows uygulama** projesi gerektirir. Böyle bir projeyi ayarlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: oluşturma Windows Forms uygulama projesi](/visualstudio/ide/step-1-create-a-windows-forms-application-project) ve [nasıl yapılır: Windows Forms denetim ekleme](how-to-add-controls-to-windows-forms.md).

### <a name="to-set-default-styles-for-all-cells-in-the-control"></a>Denetimdeki tüm hücreler için varsayılan stilleri ayarlamak için

1. Tasarımcıda <xref:System.Windows.Forms.DataGridView> denetimini seçin.

2. **Özellikler** penceresinde, <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A>, <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>veya <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> özelliğinin yanındaki Visual Studio.](./media/visual-studio-ellipsis-button.png)) Özellikler penceresi üç nokta düğmesini (...)![tıklatın. **CellStyle Builder** iletişim kutusu görüntülenir.

3. Seçimlerinizi onaylamak için **Önizleme** bölmesini kullanarak özellikleri ayarlayarak stili tanımlayın.

> [!NOTE]
> Görsel stiller etkinleştirilmişse, satır ve sütun üst bilgileri (<xref:System.Windows.Forms.DataGridView.TopLeftHeaderCell%2A>hariç) otomatik olarak geçerli Tema tarafından stillendirilmiş ve <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> ve <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> özellik değerlerini geçersiz kılar.
>
> Tasarımcıyı kullanarak birden fazla seçili <xref:System.Windows.Forms.DataGridView> denetimi için hücre stilleri ayarlayabilirsiniz, ancak yalnızca değiştirmek istediğiniz hücre stili özelliği için özdeş değerler varsa. Bu özellik için herhangi bir hücre stili farklıysa, **CellStyle Builder** Iletişim kutusunun **Özellikler** penceresi boş olur.

### <a name="to-set-default-styles-for-cells-in-individual-columns"></a>Tek sütunlardaki hücrelerin varsayılan stillerini ayarlamak için

1. Tasarımcıda <xref:System.Windows.Forms.DataGridView> denetimine sağ tıklayın ve **Sütunları Düzenle**' yi seçin.

2. **Seçili sütunlar** listesinden bir sütun seçin.

3. **Sütun özellikleri** kılavuzunda, <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> özelliğinin yanındaki üç nokta düğmesine (Visual](./media/visual-studio-ellipsis-button.png)Studio 'nun Özellikler penceresi![(...) üç nokta düğmesini (...) tıklayın. **CellStyle Builder** iletişim kutusu görüntülenir.

4. Seçimlerinizi onaylamak için **Önizleme** bölmesini kullanarak özellikleri ayarlayarak stili tanımlayın.

### <a name="to-format-data-in-cells"></a>Hücrelerdeki verileri biçimlendirmek için

1. Bir varsayılan hücre stili özelliğiyle ilgili bir **CellStyle Builder** iletişim kutusu göstermek için Yukarıdaki yordamlardan birini kullanın.

2. **CellStyle Builder** iletişim kutusunda, <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> özelliğinin yanındaki üç nokta düğmesine (Visual](./media/visual-studio-ellipsis-button.png)Studio 'nun Özellikler penceresi![(...) üç nokta düğmesini (...) tıklayın. **Biçim dizesi** iletişim kutusu görüntülenir.

3. Bir biçim türü seçin, sonra, Seçimlerinizi onaylamak için **örnek** kutusunu kullanarak türün ayrıntılarını (örneğin, görüntülenecek ondalık basamak sayısı) değiştirin.

4. <xref:System.Windows.Forms.DataGridView> denetimini null değerleri içermesi olası bir veri kaynağına bağlıyorsanız **null değer** metin kutusunu girin. Bu değer, hücre değeri null başvuruya eşitse görüntülenir (Visual Basic`Nothing`) veya <xref:System.DBNull.Value?displayProperty=nameWithType>.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A?displayProperty=nameWithType>
- [Windows Forms DataGridView Denetimindeki Hücre Stilleri](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGridView Denetimi İçin Alternatif Satır Stillerini Ayarlama](set-alternating-row-styles-for-the-datagrid-using-the-designer.md)
- [Nasıl yapılır: Windows Forms uygulama projesi oluşturma](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Nasıl yapılır: Windows Forms’a Denetimler Ekleme](how-to-add-controls-to-windows-forms.md)
