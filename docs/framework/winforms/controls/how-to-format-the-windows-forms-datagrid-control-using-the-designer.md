---
title: 'Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGrid Denetimini Biçimlendirme'
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], DataGrid controls
- colors [Windows Forms], applying to DataGrid controls
- DataGrid control [Windows Forms], formatting
- DataGrid control [Windows Forms], default styles
- tables [Windows Forms], formatting in DataGrid control
- formatting [Windows Forms]
ms.assetid: 533b9814-6124-49dc-9fda-085f1502609f
ms.openlocfilehash: b3a85f5f9e51dae50a40058b8f07f92976da66f2
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2019
ms.locfileid: "69666169"
---
# <a name="how-to-format-the-windows-forms-datagrid-control-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGrid Denetimini Biçimlendirme

> [!NOTE]
> Denetim yerini alır ve <xref:System.Windows.Forms.DataGrid> <xref:System.Windows.Forms.DataGrid> denetime işlevsellik ekler; ancak, isterseniz denetim hem geri uyumluluk hem de gelecekteki kullanım için korunur. <xref:System.Windows.Forms.DataGridView> Daha fazla bilgi için bkz. [Windows Forms DataGridView ve DataGrid denetimleri arasındaki farklar](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).

Bir <xref:System.Windows.Forms.DataGrid> denetimin çeşitli bölümlerine farklı renkler uygulamak, bilgilerin okunmasını ve yorumlanması daha kolay hale getirmenize yardımcı olabilir. Renk, satırlara ve sütunlara uygulanabilir. Satırlar ve sütunlar da gizlenebilir veya sizin için de görünür.

<xref:System.Windows.Forms.DataGrid> Denetimi biçimlendirmenin üç temel yönü vardır:

- Özellikleri, verilerin görüntülendiği varsayılan bir stil oluşturmak için ayarlayabilirsiniz.

- Bu temelden, belirli tabloların çalışma zamanında görüntülenme şeklini özelleştirebilirsiniz.

- Son olarak, veri kılavuzunda görüntülenecek sütunları ve gösterilen renkleri ve diğer biçimlendirmeleri değiştirebilirsiniz.

Bir veri kılavuzunu biçimlendirirken ilk adım olarak, <xref:System.Windows.Forms.DataGrid> kendi özelliklerini ayarlayabilirsiniz. Bu renk ve biçim seçimleri, daha sonra görünen veri tablolarına ve sütunlara göre değişiklik yapabileceğiniz bir temel oluşturur.

Aşağıdaki yordam, bir <xref:System.Windows.Forms.DataGrid> denetim içeren bir form ile **Windows uygulama** projesi gerektirir. Böyle bir projeyi ayarlama hakkında daha fazla bilgi için bkz [. nasıl yapılır: Windows Forms bir uygulama projesi](/visualstudio/ide/step-1-create-a-windows-forms-application-project) oluşturun ve [şunları yapın: Windows Forms](how-to-add-controls-to-windows-forms.md)denetimleri ekleyin. Visual Studio 2005 ' de, <xref:System.Windows.Forms.DataGrid> denetim **araç kutusunda** varsayılan olarak değildir. Daha fazla bilgi için [nasıl yapılır: Araç kutusuna](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100))öğe ekleyin.

### <a name="to-establish-a-default-style-for-the-datagrid-control"></a>DataGrid denetimi için varsayılan bir stil oluşturmak için

1. <xref:System.Windows.Forms.DataGrid> Denetimi seçin.

2. **Özellikler** penceresinde, aşağıdaki özellikleri uygun şekilde ayarlayın.

    |Özellik|Açıklama|
    |--------------|-----------------|
    |<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>|`BackColor` Özelliği, kılavuzun çift sayılı satırlarının rengini tanımlar. <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> Özelliği farklı bir renge ayarladığınızda, diğer her satır bu yeni renge ayarlanır (satır 1, 3, 5, vb.).|
    |<xref:System.Windows.Forms.DataGrid.BackColor%2A>|Kılavuzun çift sayılı satırlarının arka plan rengi (satırlar 0, 2, 4, 6, vb.).|
    |<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>|Ve özellikleri kılavuzdaki satırların rengini belirler, <xref:System.Windows.Forms.DataGrid.BackgroundColor%2A> özelliği satır alanı dışındaki alanın rengini belirler. Bu, yalnızca kılavuz en alta kaydırıldığında görünür veya yalnızca birkaç satır <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> <xref:System.Windows.Forms.DataGrid.BackColor%2A> kılavuzda yer alır.|
    |<xref:System.Windows.Forms.DataGrid.BorderStyle%2A>|Stilin kenarlık stili, <xref:System.Windows.Forms.BorderStyle> numaralandırma değerlerinden biri.|
    |<xref:System.Windows.Forms.DataGrid.CaptionBackColor%2A>|Kılavuzun hemen üstünde görünen kılavuzun pencere açıklamalı arka plan rengi.|
    |<xref:System.Windows.Forms.DataGrid.CaptionFont%2A>|Kılavuzun üst kısmındaki başlık yazı tipi.|
    |<xref:System.Windows.Forms.DataGrid.CaptionForeColor%2A>|Kılavuzun pencere açıklamalı arka plan rengi.|
    |<xref:System.Windows.Forms.Control.Font%2A>|Kılavuzdaki metni göstermek için kullanılan yazı tipi.|
    |<xref:System.Windows.Forms.DataGrid.ForeColor%2A>|Veri kılavuzu satırlarındaki veriler tarafından gösterilecek yazı tipi rengi.|
    |<xref:System.Windows.Forms.DataGrid.GridLineColor%2A>|Veri kılavuzunun kılavuz çizgilerinin rengi.|
    |<xref:System.Windows.Forms.DataGrid.GridLineStyle%2A>|<xref:System.Windows.Forms.DataGridLineStyle> Numaralandırma değerlerinden biri olan kılavuzun hücrelerini ayıran çizgilerin stili.|
    |<xref:System.Windows.Forms.DataGrid.HeaderBackColor%2A>|Satır ve sütun üst bilgilerinin arka plan rengi.|
    |<xref:System.Windows.Forms.DataGrid.HeaderFont%2A>|Sütun başlıkları için kullanılan yazı tipi.|
    |<xref:System.Windows.Forms.DataGrid.HeaderForeColor%2A>|Başlığın sütun üstbilgilerinin, sütun üst bilgisi metni ve artı işareti (+) ve eksi işareti (-) karakterleri de dahil olmak üzere, birden çok ilişkili tablo görüntülenirken satırları genişletir ve daraltır.|
    |<xref:System.Windows.Forms.DataGrid.LinkColor%2A>|Veri kılavuzundaki tüm bağlantıların, alt tablolara bağlantılar, ilişki adı vb. gibi tüm bağlantıların metin rengi.|
    |<xref:System.Windows.Forms.DataGrid.ParentRowsBackColor%2A>|Alt tabloda, bu, üst satırların arka plan rengidir.|
    |<xref:System.Windows.Forms.DataGrid.ParentRowsForeColor%2A>|Alt tabloda, bu, üst satırların ön plan rengidir.|
    |<xref:System.Windows.Forms.DataGrid.ParentRowsLabelStyle%2A>|Tablo ve sütun adlarının, <xref:System.Windows.Forms.DataGridParentRowsLabelStyle> numaralandırma yoluyla üst satırda görüntülenip görüntülenmeyeceğini belirler.|
    |<xref:System.Windows.Forms.DataGrid.PreferredColumnWidth%2A>|Kılavuzdaki sütunların varsayılan genişliği (piksel cinsinden). <xref:System.Windows.Forms.DataGrid.DataSource%2A> Ve <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> özelliklerini sıfırlamadan önce bu özelliği ayarlayın (Ayrıca, ya da yöntemi aracılığıyla) ya da özelliğin hiçbir etkisi olmayacaktır. <xref:System.Windows.Forms.DataGrid.DataMember%2A><br /><br /> Özellik 0 ' dan küçük bir değere ayarlanamaz.|
    |<xref:System.Windows.Forms.DataGrid.PreferredRowHeight%2A>|Kılavuzdaki satırların satır yüksekliği (piksel cinsinden). <xref:System.Windows.Forms.DataGrid.DataSource%2A> Ve <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> özelliklerini sıfırlamadan önce bu özelliği ayarlayın (Ayrıca, ya da yöntemi aracılığıyla) ya da özelliğin hiçbir etkisi olmayacaktır. <xref:System.Windows.Forms.DataGrid.DataMember%2A><br /><br /> Özellik 0 ' dan küçük bir değere ayarlanamaz.|
    |<xref:System.Windows.Forms.DataGrid.RowHeaderWidth%2A>|Kılavuzun satır üst bilgilerinin genişliği.|
    |<xref:System.Windows.Forms.DataGrid.SelectionBackColor%2A>|Bir satır veya hücre seçildiğinde, bu arka plan rengidir.|
    |<xref:System.Windows.Forms.DataGrid.SelectionForeColor%2A>|Bir satır veya hücre seçildiğinde bu, ön plan rengidir.|

    > [!NOTE]
    > Denetimlerin renklerini özelleştirirken, kötü renk seçimi (örneğin, kırmızı ve yeşil) nedeniyle denetimin erişilemez hale getirmek mümkündür. Bu sorundan kaçınmak için **sistem renkleri** paletindeki kullanılabilir renkleri kullanın.

    Aşağıdaki yordam bir veri tablosuna <xref:System.Windows.Forms.DataGrid> dayalı bir denetim gerektirir. Daha fazla bilgi için [nasıl yapılır: Windows Forms DataGrid denetimini bir veri kaynağına](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)bağlayın.

### <a name="to-set-the-table-and-column-style-of-a-data-table-at-design-time"></a>Tasarım zamanında bir veri tablosunun tablo ve sütun stilini ayarlamak için

1. <xref:System.Windows.Forms.DataGrid> Formunuzdaki denetimi seçin.

2. **Özellikler** penceresinde <xref:System.Windows.Forms.DataGrid.TableStyles%2A> , özelliği seçin ve **üç nokta** (![Visual Studio](./media/visual-studio-ellipsis-button.png)'nun Özellikler penceresi) düğmesine tıklayın.

3. Bir tablo stilini koleksiyona eklemek için, **DataGridTableStyle koleksiyon Düzenleyicisi** Iletişim kutusunda **Ekle** ' ye tıklayın.

     **DataGridTableStyle koleksiyon Düzenleyicisi**ile tablo stilleri ekleyip kaldırabilir, görüntüleme ve düzen özelliklerini ayarlayabilir ve tablo stillerinin eşleme adını ayarlayabilirsiniz.

4. Her tablo stilinin eşleme adına özelliğiniayarlayın.<xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A>

     Eşleme adı, hangi tablo stilinin hangi tabloyla kullanılması gerektiğini belirtmek için kullanılır.

5. **DataGridTableStyle koleksiyonu düzenleyicisinde**, <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> özelliğini seçin ve Visual Studio](./media/visual-studio-ellipsis-button.png)Özellikler penceresi üç nokta düğmesine (.![..) tıklayın.

6. **DataGridColumnStyle koleksiyon Düzenleyicisi** iletişim kutusunda, oluşturduğunuz tablo stiline sütun stilleri ekleyin.

     **DataGridColumnStyle koleksiyon Düzenleyicisi**ile sütun stilleri ekleyip kaldırabilir, görüntüleme ve düzen özelliklerini ayarlayabilir ve veri sütunlarının eşleme adını ve biçimlendirme dizelerini ayarlayabilirsiniz.

    > [!NOTE]
    > Biçimlendirme dizeleri hakkında daha fazla bilgi için bkz. [biçimlendirme türleri](../../../standard/base-types/formatting-types.md).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.GridTableStylesCollection>
- <xref:System.Windows.Forms.GridColumnStylesCollection>
- <xref:System.Windows.Forms.DataGrid>
- [Nasıl yapılır: Windows Forms DataGrid denetimindeki sütunları silme veya gizleme](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [DataGrid Denetimi](datagrid-control-windows-forms.md)
