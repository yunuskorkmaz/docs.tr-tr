---
title: Windows Forms DataGridView Denetimindeki Veri Biçimleri
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting data
- data [Windows Forms], formatting in grids
- data grids [Windows Forms], formatting data
ms.assetid: 07bf558d-3748-42ba-8ba0-37fdef924081
ms.openlocfilehash: 0016b87add6f20223bdeda72f10ac94b74ec9fcf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54737864"
---
# <a name="data-formatting-in-the-windows-forms-datagridview-control"></a>Windows Forms DataGridView Denetimindeki Veri Biçimleri
<xref:System.Windows.Forms.DataGridView> Denetim hücre değerlerini ve üst sütunlarını görüntüleyen veri türleri arasında otomatik dönüştürme sağlar. Metin kutusu sütunları, örneğin, tarih, saat, sayı ve numaralandırma değerlerinin dize temsillerini görüntülemek ve veri deposu tarafından gerekli olan türleri için kullanıcı tarafından girilen dize değerlerini dönüştürmek.  
  
## <a name="formatting-with-the-datagridviewcellstyle-class"></a>Biçimlendirme DataGridViewCellStyle sınıfı  
 <xref:System.Windows.Forms.DataGridView> Denetimi sağlar hücre değerlerini temel veri biçimlendirmesini <xref:System.Windows.Forms.DataGridViewCellStyle> sınıfı. Kullanabileceğiniz <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> açıklanan biçim belirticilerini kullanarak geçerli varsayılan kültür için tarih, saat, sayı ve sabit listesi değerlerini biçimlendirmek için özellik [biçimlendirme türleri](../../../../docs/standard/base-types/formatting-types.md). Ayrıca bu değerleri kullanarak belirli bir kültür için biçimlendirebilirsiniz <xref:System.Windows.Forms.DataGridViewCellStyle.FormatProvider%2A> özelliği. Belirtilen biçim verileri görüntüleyen ve belirtilen biçimde kullanıcının girdiği verileri ayrıştırmak için kullanılır.  
  
 <xref:System.Windows.Forms.DataGridViewCellStyle> Sınıf ek biçimlendirme özellikleri wordwrap, metin hizalamasını ve boş veritabanı değerlerini özel görüntülenmesini sağlar. Daha fazla bilgi için [nasıl yapılır: Verileri biçimlendirme Windows Forms DataGridView denetiminde](../../../../docs/framework/winforms/controls/how-to-format-data-in-the-windows-forms-datagridview-control.md).  
  
## <a name="formatting-with-the-cellformatting-event"></a>CellFormatting olayla biçimlendirme  
 Temel biçimlendirme gereksinimlerinizi karşılamıyorsa, özel veri için bir işleyici biçimlendirme sağlayabilirsiniz <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> olay. <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> İşleyicisine geçirilen sahip bir <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> ilk hücrenin değeri içeren özellik. Normalde, bu değeri otomatik olarak görünen türüne dönüştürülür. Değeri kendiniz dönüştürmek için ayarlanmış <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> özelliğini görünen türünde bir değer.  
  
> [!NOTE]
>  Bir biçim dizesi için hücre etkinse, onu geçersiz kılar, değişikliği <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> özellik değerini ayarlamadığınız sürece <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs.FormattingApplied%2A> özelliğini `true`.  
  
 <xref:System.Windows.Forms.DataGridView.CellFormatting> Olay, ayrıca, ayarlamak istediğiniz gerektiğinde kullanışlıdır <xref:System.Windows.Forms.DataGridViewCellStyle> özelliklerini tek tek hücreleri değerlerine bağlı. Daha fazla bilgi için [nasıl yapılır: Windows Forms DataGridView denetiminde veri biçimlendirmeyi özelleştirme](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).  
  
 Varsayılan kullanıcı tarafından belirtilen değerleri ayrıştırma gereksinimlerinizi karşılamıyorsa işleyebilir <xref:System.Windows.Forms.DataGridView.CellParsing> olayı <xref:System.Windows.Forms.DataGridView> özel ayrıştırma sağlamak için denetimi.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [Windows Forms DataGridView Denetiminde Verileri Görüntüleme](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetimindeki Hücre Stilleri](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)
- [Nasıl yapılır: Verileri biçimlendirme Windows Forms DataGridView denetimi](../../../../docs/framework/winforms/controls/how-to-format-data-in-the-windows-forms-datagridview-control.md)
- [Nasıl yapılır: Windows Forms DataGridView denetiminde veri biçimlendirmeyi özelleştirme](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
