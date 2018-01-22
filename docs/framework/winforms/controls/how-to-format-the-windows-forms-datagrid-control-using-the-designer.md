---
title: "Nasıl yapılır: Tasarımcı Kullanarak Windows Formları DataGrid Denetimini Biçimlendirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- columns [Windows Forms], DataGrid controls
- colors [Windows Forms], applying to DataGrid controls
- DataGrid control [Windows Forms], formatting
- DataGrid control [Windows Forms], default styles
- tables [Windows Forms], formatting in DataGrid control
- formatting [Windows Forms]
ms.assetid: 533b9814-6124-49dc-9fda-085f1502609f
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b47b0c2353764f5452c2bb3f6ca37af11d6d904c
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-format-the-windows-forms-datagrid-control-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Windows Formları DataGrid Denetimini Biçimlendirme
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Denetimi değiştirir ve işlevlerini ekler <xref:System.Windows.Forms.DataGrid> kontrol; ancak, <xref:System.Windows.Forms.DataGrid> denetim tutulur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz. Daha fazla bilgi için bkz: [farklar arasında Windows Forms DataGridView ve DataGrid denetimleri](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Farklı renkler için çeşitli kısımlarını uygulayarak bir <xref:System.Windows.Forms.DataGrid> denetim bilgileri okumak ve yorumlamak kolaylaştırmak için yardımcı olabilir. Renk satırlara ve sütunlara uygulanabilir. Satırları ve sütunları da gizlenebilir veya kümeleri gösterilmektedir.  
  
 Biçimlendirme üç temel nokta <xref:System.Windows.Forms.DataGrid> denetimi:  
  
-   Verilerin görüntülendiği varsayılan stilini kurmak için özellikleri ayarlayabilirsiniz.  
  
-   Bu taban, belirli tabloları çalışma zamanında görüntülenme biçimini özelleştirebilirsiniz.  
  
-   Son olarak, hangi sütunların renkleri yanı sıra veri kılavuzu görüntülenen değiştirebilir ve diğer biçimlendirme gösterilir.  
  
 Veri Kılavuzu biçimlendirme bir ilk adım, özellikleri ayarlayabilirsiniz <xref:System.Windows.Forms.DataGrid> kendisi. Bu renk ve biçime seçimler, ardından veri tabloları ve sütunları görüntülenen bağlı olarak değişiklik yapabilirsiniz bir temel oluşturur.  
  
 Aşağıdaki yordam gerektiren bir **Windows uygulaması** içeren bir form ile proje bir <xref:System.Windows.Forms.DataGrid> denetim. Böyle bir proje ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir Windows uygulaması projesi oluşturduğunuzda](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) ve [nasıl yapılır: Windows Forms denetimlerine ekleme](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md). İçinde [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], <xref:System.Windows.Forms.DataGrid> denetim içinde değil **araç** varsayılan olarak. Daha fazla bilgi için bkz: [nasıl yapılır: araç kutusu öğeleri Ekle](http://msdn.microsoft.com/library/458e119e-17fe-450b-b889-e31c128bd7e0).  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-establish-a-default-style-for-the-datagrid-control"></a>DataGrid denetimi için varsayılan stil oluşturmak için  
  
1.  Seçin <xref:System.Windows.Forms.DataGrid> denetim.  
  
2.  İçinde **özellikleri** penceresinde, aşağıdaki özellikleri uygun şekilde ayarlayın.  
  
    |Özellik|Açıklama|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>|`BackColor` Özelliği ızgaranın sayılı satırların rengi tanımlar. Ayarladığınızda <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> özelliği için farklı bir renk, her bir satır ayarlanmış bu yeni renge (satırları 1, 3, 5 ve benzeri).|  
    |<xref:System.Windows.Forms.DataGrid.BackColor%2A>|Izgaranın sayılı satırların arka plan rengi (satırları 0, 2, 4, 6 ve benzeri).|  
    |<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>|Oysa <xref:System.Windows.Forms.DataGrid.BackColor%2A> ve <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> özellikleri ızgara satırların rengini belirler <xref:System.Windows.Forms.DataGrid.BackgroundColor%2A> özelliği, kılavuzun altına kaydırılan veya birkaç satırlar yalnızca görülebilir satır alanının dışına alanının rengini belirler kılavuzda içeriyor.|  
    |<xref:System.Windows.Forms.DataGrid.BorderStyle%2A>|Izgaranın kenarlık stili, aşağıdakilerden birini <xref:System.Windows.Forms.BorderStyle> numaralandırma değerleri.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionBackColor%2A>|Hemen kılavuz görüntülenen kılavuz penceresinin başlık arka plan rengi.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionFont%2A>|Izgaranın üst başlık yazı tipi.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionForeColor%2A>|Izgaranın penceresinin başlık arka plan rengi.|  
    |<xref:System.Windows.Forms.Control.Font%2A>|Kılavuzda metni görüntülemek için kullanılan yazıtipi.|  
    |<xref:System.Windows.Forms.DataGrid.ForeColor%2A>|Veri Kılavuzu satırlardaki verileri tarafından görüntülenen yazı tipi rengi.|  
    |<xref:System.Windows.Forms.DataGrid.GridLineColor%2A>|Veri Kılavuzu kılavuz çizgilerinin rengi.|  
    |<xref:System.Windows.Forms.DataGrid.GridLineStyle%2A>|Kılavuz birini hücrelerinin ayırarak çizgi stilini <xref:System.Windows.Forms.DataGridLineStyle> numaralandırma değerleri.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderBackColor%2A>|Satır ve sütun üstbilgilerini arka plan rengi.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderFont%2A>|Sütun üst bilgileri için kullanılan yazıtipi.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderForeColor%2A>|Kılavuz sütun başlıklarını sütunu üstbilgi metni ve artı (+) ve eksi işareti (-) genişletin ve birden çok tablo işlerken satırları Daralt karakterleri dahil olmak üzere, ön plan rengini görüntülenir.|  
    |<xref:System.Windows.Forms.DataGrid.LinkColor%2A>|Alt tablolar, ilişki adı ve benzeri bağlantılar dahil olmak üzere veri kılavuzunda tüm bağlantıların metnin rengi.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsBackColor%2A>|Bir alt tabloda üst satırların arka plan rengini budur.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsForeColor%2A>|Bir alt tabloda üst satırların ön plan rengini budur.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsLabelStyle%2A>|Tablo ve sütun adlarını yoluyla üst satırda görüntülenip görüntülenmediğini belirler <xref:System.Windows.Forms.DataGridParentRowsLabelStyle> numaralandırması.|  
    |<xref:System.Windows.Forms.DataGrid.PreferredColumnWidth%2A>|Kılavuz sütunu varsayılan genişliğini (piksel cinsinden). Sıfırlamadan önce bu özelliği ayarlamak <xref:System.Windows.Forms.DataGrid.DataSource%2A> ve <xref:System.Windows.Forms.DataGrid.DataMember%2A> özellikleri (ya da ayrı ayrı aracılığıyla veya <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> yöntemi), ya da özelliğinin hiçbir etkisi olmaz.<br /><br /> Özelliği 0'dan daha düşük bir değere ayarlanamıyor.|  
    |<xref:System.Windows.Forms.DataGrid.PreferredRowHeight%2A>|Izgaradaki satırların (piksel cinsinden) satır yüksekliği. Sıfırlamadan önce bu özelliği ayarlamak <xref:System.Windows.Forms.DataGrid.DataSource%2A> ve <xref:System.Windows.Forms.DataGrid.DataMember%2A> özellikleri (ya da ayrı ayrı aracılığıyla veya <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> yöntemi), ya da özelliğinin hiçbir etkisi olmaz.<br /><br /> Özelliği 0'dan daha düşük bir değere ayarlanamıyor.|  
    |<xref:System.Windows.Forms.DataGrid.RowHeaderWidth%2A>|Izgaranın satır üstbilgilerinin genişliği.|  
    |<xref:System.Windows.Forms.DataGrid.SelectionBackColor%2A>|Bir satır veya hücre seçildiğinde, arka plan rengini budur.|  
    |<xref:System.Windows.Forms.DataGrid.SelectionForeColor%2A>|Bir satır veya hücre seçildiğinde, ön plan rengini budur.|  
  
    > [!NOTE]
    >  Denetimleri renkleri özelleştirirken denetimi zayıf renk seçim (örneğin, kırmızı ve yeşil) nedeniyle erişilemez hale mümkündür. Kullanılabilir renklerini kullan **sistem renkleri** bu sorunu önlemek için palet.  
  
     Aşağıdaki yordam gerektiren bir <xref:System.Windows.Forms.DataGrid> denetimine bağlı bir veri tablosuna. Daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms DataGrid denetimini veri kaynağına bağlama](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).  
  
### <a name="to-set-the-table-and-column-style-of-a-data-table-at-design-time"></a>Tasarım zamanında bir veri tablosunda tablo ve sütun stilini ayarlamak için  
  
1.  Seçin <xref:System.Windows.Forms.DataGrid> formunuzda denetim.  
  
2.  İçinde **özellikleri** penceresinde, seçin <xref:System.Windows.Forms.DataGrid.TableStyles%2A> özelliği ve tıklatın **üç nokta** (![VisualStudioEllipsesButton ekran] (../../../../docs/framework/winforms/media/vbellipsesbutton.png " vbEllipsesButton")) düğmesi.  
  
3.  İçinde **DataGridTableStyle Koleksiyonu Düzenleyicisi** iletişim kutusu, tıklatın **Ekle** tablo stili koleksiyona eklemek için.  
  
     İle **DataGridTableStyle Koleksiyonu Düzenleyicisi**, ekleyebilir ve Kaldır tablo stilleri, kümesi görüntüleme ve yerleşim özellikleri ve kümesi tablo stilleri için ad eşleştirme.  
  
4.  Ayarlama <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> her tablo stili eşleme adına özelliği.  
  
     Eşleme adı hangi tablo stili hangi tabloyla kullanılması gerektiğini belirtmek için kullanılır.  
  
5.  İçinde **DataGridTableStyle Koleksiyonu Düzenleyicisi**seçin <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> özelliği ve üç nokta düğmesini (![VisualStudioEllipsesButton ekran](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton ")).  
  
6.  İçinde **DataGridColumnStyle Koleksiyonu Düzenleyicisi** iletişim kutusunda, oluşturduğunuz tablo stili sütun stilleri ekleyin.  
  
     İle **DataGridColumnStyle Koleksiyonu Düzenleyicisi**, ekleme ve sütun stilleri kaldırma, görüntü ve düzen özelliklerini ayarlama ve eşleme adını ayarlayın ve sütunları dizeleri için verileri biçimlendirme.  
  
    > [!NOTE]
    >  Biçimlendirme dizeleri hakkında daha fazla bilgi için bkz: [biçimlendirme türleri](../../../../docs/standard/base-types/formatting-types.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.GridTableStylesCollection>  
 <xref:System.Windows.Forms.GridColumnStylesCollection>  
 <xref:System.Windows.Forms.DataGrid>  
 [Nasıl yapılır: Windows Forms DataGrid Denetiminde Sütunları Silme veya Gizleme](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)  
 [DataGrid Denetimi](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)
