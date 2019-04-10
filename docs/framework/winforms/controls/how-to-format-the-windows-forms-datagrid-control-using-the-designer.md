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
ms.openlocfilehash: fbe2aa724274022446498a89618f37787f0fa8bd
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59333580"
---
# <a name="how-to-format-the-windows-forms-datagrid-control-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGrid Denetimini Biçimlendirme

> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Denetimi değiştirir ve işlevsellik ekler <xref:System.Windows.Forms.DataGrid> denetler; ancak, <xref:System.Windows.Forms.DataGrid> denetim korunur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz. Daha fazla bilgi için [farklar arasında Windows Forms DataGridView ve DataGrid denetimleri](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Çeşitli bölümlerine farklı renkler uygulayarak bir <xref:System.Windows.Forms.DataGrid> denetim bilgileri içine okumak ve yorumlamak kolay hale getirmek için yardımcı olabilir. Satırları ve sütunları için renk uygulanabilir. Satırları ve sütunları da gizli veya gösterilen günlüklerinizin bekletilme.  
  
 Biçimlendirme üç temel unsur vardır <xref:System.Windows.Forms.DataGrid> denetimi:  
  
-   Verilerin görüntülendiği bir varsayılan stilde kurmak için özellikleri ayarlayabilirsiniz.  
  
-   Bu temelden belirli tablolar, çalışma zamanında görüntülenme biçimini özelleştirebilirsiniz.  
  
-   Son olarak, hangi sütunların renkleri yanı sıra veri kılavuzunda görüntülenen değiştirebilirsiniz ve diğer biçimlendirme gösterilir.  
  
 Bir ilk adım olarak, veri kılavuzu biçimlendirme özellikleri ayarlayabilirsiniz <xref:System.Windows.Forms.DataGrid> kendisi. Bu renk ve biçim seçimleri kendisinden sonra veri tabloları ve sütunları görüntülenen bağlı olarak değişiklik yapabilirsiniz bir temel oluşturur.  
  
 Aşağıdaki yordam gerektirir bir **Windows uygulama** proje içeren bir form içeren bir <xref:System.Windows.Forms.DataGrid> denetimi. Bu tür bir proje ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: Bir Windows Forms uygulaması projesi oluşturma](/visualstudio/ide/step-1-create-a-windows-forms-application-project) ve [nasıl yapılır: Windows Forms'a denetimler ekleme](how-to-add-controls-to-windows-forms.md). Visual Studio 2005 ' te <xref:System.Windows.Forms.DataGrid> denetimi içinde değil **araç kutusu** varsayılan olarak. Daha fazla bilgi için [nasıl yapılır: Araç kutusu öğeleri Ekle](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100)).  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-establish-a-default-style-for-the-datagrid-control"></a>DataGrid denetimi için bir varsayılan stilde oluşturmak için  
  
1. Seçin <xref:System.Windows.Forms.DataGrid> denetimi.  
  
2. İçinde **özellikleri** penceresinde aşağıdaki özellikleri uygun şekilde ayarlayın.  
  
    |Özellik|Açıklama|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>|`BackColor` Özelliği sayılı satır kılavuzunun rengini tanımlar. Ayarladığınızda <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> özelliği farklı bir renge, her bir satır için bu yeni renk ayarlanır (satırlar 1, 3, 5 vb.).|  
    |<xref:System.Windows.Forms.DataGrid.BackColor%2A>|Izgaranın sayılı satırların arka plan rengi (0, 2, 4, 6 ve benzeri satır).|  
    |<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>|Oysa <xref:System.Windows.Forms.DataGrid.BackColor%2A> ve <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> özellikleri ızgara satır rengini belirler <xref:System.Windows.Forms.DataGrid.BackgroundColor%2A> özellik Kılavuzu altına kaydırılan veya yalnızca birkaç satır yalnızca görünür durumda olan satır alanının dışına alanının rengini belirler kılavuzda yer alan.|  
    |<xref:System.Windows.Forms.DataGrid.BorderStyle%2A>|Izgaranın kenarlık stili, aşağıdakilerden birini <xref:System.Windows.Forms.BorderStyle> sabit listesi değerleri.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionBackColor%2A>|Kılavuzun üzerindeki hemen görünen kılavuz pencere başlığı arka plan rengi.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionFont%2A>|Kılavuz üst kısmındaki başlık yazı tipi.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionForeColor%2A>|Izgaranın pencere başlığı arka plan rengi.|  
    |<xref:System.Windows.Forms.Control.Font%2A>|Kılavuzda metni görüntülemek için kullanılan yazıtipi.|  
    |<xref:System.Windows.Forms.DataGrid.ForeColor%2A>|Veri Kılavuzu satırı verilerinde tarafından görüntülenen yazı tipi rengi.|  
    |<xref:System.Windows.Forms.DataGrid.GridLineColor%2A>|Veri Kılavuzu, kılavuz çizgilerinin rengi.|  
    |<xref:System.Windows.Forms.DataGrid.GridLineStyle%2A>|Kılavuzun birini hücreleri ayıran çizgilerin stili <xref:System.Windows.Forms.DataGridLineStyle> sabit listesi değerleri.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderBackColor%2A>|Satır ve sütun üst bilgilerinin arka plan rengi.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderFont%2A>|Sütun üst bilgilerini kullanılan yazıtipi.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderForeColor%2A>|Kılavuz sütun başlıklarının sütunu üstbilgi metni ve artı işaretine (+) ve eksi işareti (-) genişletin ve birden fazla ilgili tablo satırları Daralt karakterleri dahil olmak üzere, ön plan rengi görüntülenir.|  
    |<xref:System.Windows.Forms.DataGrid.LinkColor%2A>|Veri kılavuzunda alt tablolar, ilişki adı ve benzeri bağlantılar dahil olmak üzere tüm bağlantıların metnin rengi.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsBackColor%2A>|Bir alt tabloda üst satırların arka plan rengi budur.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsForeColor%2A>|Bir alt tabloda üst satırları ön plan rengini budur.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsLabelStyle%2A>|Tablo ve sütun adları üst satırın yoluyla görüntülenip görüntülenmediğini belirler <xref:System.Windows.Forms.DataGridParentRowsLabelStyle> sabit listesi.|  
    |<xref:System.Windows.Forms.DataGrid.PreferredColumnWidth%2A>|Izgara sütunları varsayılan genişliğini (piksel cinsinden). Sıfırlamadan önce bu özelliği ayarlayın <xref:System.Windows.Forms.DataGrid.DataSource%2A> ve <xref:System.Windows.Forms.DataGrid.DataMember%2A> özellikleri (ya da ayrı olarak aracılığıyla veya <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> yöntemi), veya özellik hiçbir etkisi olmaz.<br /><br /> Özelliği, 0'dan düşük bir değere ayarlanamaz.|  
    |<xref:System.Windows.Forms.DataGrid.PreferredRowHeight%2A>|Izgara satır satır yüksekliği (piksel cinsinden). Sıfırlamadan önce bu özelliği ayarlayın <xref:System.Windows.Forms.DataGrid.DataSource%2A> ve <xref:System.Windows.Forms.DataGrid.DataMember%2A> özellikleri (ya da ayrı olarak aracılığıyla veya <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> yöntemi), veya özellik hiçbir etkisi olmaz.<br /><br /> Özelliği, 0'dan düşük bir değere ayarlanamaz.|  
    |<xref:System.Windows.Forms.DataGrid.RowHeaderWidth%2A>|Izgaranın satır başlıklarında genişliği.|  
    |<xref:System.Windows.Forms.DataGrid.SelectionBackColor%2A>|Bu, bir satır veya hücre seçildiğinde, arka plan rengidir.|  
    |<xref:System.Windows.Forms.DataGrid.SelectionForeColor%2A>|Bu, bir satır veya hücre seçildiğinde, ön plan rengidir.|  
  
    > [!NOTE]
    >  Renkleri denetimlerin özelleştirirken, denetimi kötü renk seçimi (örneğin, kırmızı ve yeşil) nedeniyle erişilemez hale mümkündür. Kullanılabilir renklerini kullan **sistem renkleri** bu sorunu önlemek için palet.

     Aşağıdaki yordamı gerektiren bir <xref:System.Windows.Forms.DataGrid> denetim bir veri tablosuna bağlı. Daha fazla bilgi için [nasıl yapılır: Windows Forms DataGrid denetimini veri kaynağına bağlama](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).

### <a name="to-set-the-table-and-column-style-of-a-data-table-at-design-time"></a>Tasarım zamanında bir veri tablosu tablo ve sütun stilini ayarlamak için

1. Seçin <xref:System.Windows.Forms.DataGrid> formunuzdaki denetimi.

2. İçinde **özellikleri** penceresinde <xref:System.Windows.Forms.DataGrid.TableStyles%2A> özelliği ve tıklatın **üç nokta** (![VisualStudioEllipsesButton ekran](../media/vbellipsesbutton.png " vbEllipsesButton")) düğmesi.

3. İçinde **DataGridTableStyle Koleksiyonu Düzenleyicisi** iletişim kutusu, tıklayın **Ekle** tablo stili koleksiyona eklenecek.

     İle **DataGridTableStyle Koleksiyonu Düzenleyicisi**ekleyebilir ve Kaldır tablo stilleri, kümesini görüntüleme ve düzen özelliklerini ve kümesi için tablo stilleri ad eşleştirme.

4. Ayarlama <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> özelliğini her tablo stili için eşleme adı.

     Eşleme adı, hangi tablo stili ile hangi tabloyu kullanılması gerektiğini belirtmek için kullanılır.

5. İçinde **DataGridTableStyle Koleksiyonu Düzenleyicisi**seçin <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> özelliği ve üç nokta düğmesini (![VisualStudioEllipsesButton ekran](../media/vbellipsesbutton.png "vbEllipsesButton ")).

6. İçinde **DataGridColumnStyle Koleksiyonu Düzenleyicisi** iletişim kutusunda, oluşturduğunuz tablo stili sütun stil ekleyin.

     İle **DataGridColumnStyle Koleksiyonu Düzenleyicisi**, ekleme ve sütun stil kaldırın, görüntü ve düzen özelliklerini ayarlama ve eşleme adını ayarlayın ve sütunları dizeleri için veri biçimlendirme.

    > [!NOTE]
    >  Biçimlendirme dizeleri hakkında daha fazla bilgi için bkz. [biçimlendirme türleri](../../../standard/base-types/formatting-types.md).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.GridTableStylesCollection>
- <xref:System.Windows.Forms.GridColumnStylesCollection>
- <xref:System.Windows.Forms.DataGrid>
- [Nasıl yapılır: Windows Forms DataGrid Denetiminde Sütunları Silme veya Gizleme](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [DataGrid Denetimi](datagrid-control-windows-forms.md)