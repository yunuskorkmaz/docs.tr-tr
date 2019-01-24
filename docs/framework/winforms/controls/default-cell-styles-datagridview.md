---
title: "Nasıl yapılır: Windows Forms DataGridView Tasarımcısı'nı kullanarak denetimi için varsayılan hücre stilleri ve veri biçimleri ayarlama"
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], setting styles
- data formats
- data [Windows Forms], setting formats
ms.assetid: fc6da49f-8942-41da-b49f-b2afc38cc656
ms.openlocfilehash: 003ddd68de22d60b771ca525cfa5cc6b2e1e1e3e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54650778"
---
# <a name="how-to-set-default-cell-styles-and-data-formats-for-the-windows-forms-datagridview-control-using-the-designer"></a>Nasıl yapılır: Windows Forms DataGridView Tasarımcısı'nı kullanarak denetimi için varsayılan hücre stilleri ve veri biçimleri ayarlama
<xref:System.Windows.Forms.DataGridView> Varsayılan hücre stilleri belirtmek ve veri biçimleri eksiksiz bir denetim için belirli sütunları için satır ve sütun üstbilgilerinin ve alternatif bir kayıt defteri etkisi oluşturmak için satırlar için hücre denetimi sağlar. Tüm denetim için ayarlanmış varsayılan stillerini stilleri değişen satırları ve sütunları için varsayılan tarafından geçersiz kılınır. Ayrıca, tek tek satırların ve hücrelerin kodunu kümesindeki stilleri varsayılan stillerini geçersiz kılar.  
  
 Hücre stilleri hakkında daha fazla bilgi için bkz: [Windows Forms DataGridView denetimindeki hücre stilleri](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md). Alternatif satırlar için stil ayarlamak için bkz [nasıl yapılır: Windows Forms DataGridView Tasarımcısı'nı kullanarak denetimi için alternatif satır stillerini ayarlama](../../../../docs/framework/winforms/controls/set-alternating-row-styles-for-the-datagrid-using-the-designer.md).  
  
 Stilleri kullanarak da ayarlayabilirsiniz <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> denetimine eklenecek olan tüm satırları etkilemek için özellik. Satır şablonunu hakkında daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms DataGridView denetimindeki satırları özelleştirmek için satır şablonunu kullanma](../../../../docs/framework/winforms/controls/use-the-row-template-to-customize-rows-in-the-datagrid.md).  
  
 Aşağıdaki yordamlar gerektiren bir **Windows uygulama** proje içeren bir form ile bir <xref:System.Windows.Forms.DataGridView> denetimi. Bu tür bir proje ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: Bir Windows uygulaması projesi oluşturmak](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) ve [nasıl yapılır: Windows Forms'a denetimler ekleme](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-set-default-styles-for-all-cells-in-the-control"></a>Denetimdeki tüm hücreler için varsayılan stillerini ayarlamak için  
  
1.  Seçin <xref:System.Windows.Forms.DataGridView> Denetim Tasarımcısı'nda.  
  
2.  İçinde **özellikleri** penceresinde üç nokta düğmesini (![VisualStudioEllipsesButton ekran](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) yanındaki <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A>, <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>, veya <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> özelliği. **CellStyle Oluşturucu** iletişim kutusu görüntülenir.  
  
3.  Stil kullanarak özelliklerini ayarlayarak tanımlamak **Önizleme** bölmesinde seçimlerinizi onaylayın.  
  
> [!NOTE]
>  Görsel stiller etkinleştirilirse, satır ve sütun üst bilgilerinin (dışında <xref:System.Windows.Forms.DataGridView.TopLeftHeaderCell%2A>) otomatik olarak geçerli tema tarafından stillere geçersiz kılma <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> ve <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> özellik değerleri.  
>   
>  Seçilen birden fazla hücre stilleri ayarlayabilirsiniz <xref:System.Windows.Forms.DataGridView> değiştirmek istediğiniz hücreyi stil özelliği için aynı değerlere sahiptirler ancak Tasarımcı kullanılarak denetler. Bu özellik için bir hücre stilleri farklıysa **özellikleri** windows **CellStyle Oluşturucu** iletişim kutusu boş olacaktır.  
  
### <a name="to-set-default-styles-for-cells-in-individual-columns"></a>Tek tek sütunlardaki varsayılan hücre stillerini ayarlama  
  
1.  Sağ <xref:System.Windows.Forms.DataGridView> seçin ve Denetim Tasarımcısı'nda **sütunları Düzenle**.  
  
2.  Bir sütun seçin **seçili sütun** listesi.  
  
3.  İçinde **sütun özellikleri** kılavuz, üç nokta düğmesini (![VisualStudioEllipsesButton ekran](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) yanındaki <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> özelliği. **CellStyle Oluşturucu** iletişim kutusu görüntülenir.  
  
4.  Stil kullanarak özelliklerini ayarlayarak tanımlamak **Önizleme** bölmesinde seçimlerinizi onaylayın.  
  
### <a name="to-format-data-in-cells"></a>Hücrelerine veri biçimlendirmek için  
  
1.  Görüntülemek için aşağıdaki yordamlardan birini kullanın bir **CellStyle Oluşturucu** iletişim kutusu için varsayılan hücre stili özellik ilgili.  
  
2.  İçinde **CellStyle Oluşturucu** iletişim kutusunda, üç nokta düğmesini (![VisualStudioEllipsesButton ekran](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) yanındaki <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> özellik. **Biçim dizesi** iletişim kutusu görüntülenir.  
  
3.  Biçim türü seçin ve ardından ayrıntılar (sayısı gibi görüntülenecek ondalık basamak), türün Değiştir kullanarak **örnek** kutusunu seçimlerinizi onaylayın.  
  
4.  Bağlıyorsanız <xref:System.Windows.Forms.DataGridView> null değerler içeremez, doldurmak büyük olasılıkla bir veri kaynağına denetim **Null değer** metin kutusu. Hücre değerini bir null başvuruya eşit olduğunda bu değeri görüntülenir (`Nothing` Visual Basic) veya <xref:System.DBNull.Value?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A?displayProperty=nameWithType>
- [Windows Forms DataGridView Denetimindeki Hücre Stilleri](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)
- [Nasıl yapılır: Windows Forms DataGridView Tasarımcısı'nı kullanarak denetimi için alternatif satır stillerini ayarlama](../../../../docs/framework/winforms/controls/set-alternating-row-styles-for-the-datagrid-using-the-designer.md)
- [Nasıl yapılır: Bir Windows uygulaması projesi oluşturma](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)
- [Nasıl yapılır: Windows Forms'a denetimler ekleme](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
