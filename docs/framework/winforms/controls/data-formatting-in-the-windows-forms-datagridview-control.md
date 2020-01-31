---
title: DataGridView denetiminde veri biçimlendirme
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting data
- data [Windows Forms], formatting in grids
- data grids [Windows Forms], formatting data
ms.assetid: 07bf558d-3748-42ba-8ba0-37fdef924081
ms.openlocfilehash: a041bcc5e1b65afb3123f1f42e0f1b5a479b5764
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743989"
---
# <a name="data-formatting-in-the-windows-forms-datagridview-control"></a>Windows Forms DataGridView Denetimindeki Veri Biçimleri
<xref:System.Windows.Forms.DataGridView> denetimi, hücre değerleri ve üst sütunların görüntüleyeceği veri türleri arasında otomatik dönüştürme sağlar. Metin kutusu sütunları, örneğin, tarih, saat, sayı ve numaralandırma değerlerinin dize temsillerini görüntüle ve Kullanıcı tarafından girilen dize değerlerini veri deposunun gerektirdiği türlere Dönüştür.  
  
## <a name="formatting-with-the-datagridviewcellstyle-class"></a>DataGridViewCellStyle sınıfıyla biçimlendirme  
 <xref:System.Windows.Forms.DataGridView> denetimi, <xref:System.Windows.Forms.DataGridViewCellStyle> sınıfı aracılığıyla hücre değerlerinin temel veri biçimlendirmesini sağlar. [Biçimlendirme türlerinde](../../../standard/base-types/formatting-types.md)açıklanan biçim belirticilerini kullanarak geçerli varsayılan kültür için tarih, saat, sayı ve numaralandırma değerlerini biçimlendirmek üzere <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> özelliğini kullanabilirsiniz. Bu değerleri, <xref:System.Windows.Forms.DataGridViewCellStyle.FormatProvider%2A> özelliğini kullanarak belirli kültürler için de biçimlendirebilirsiniz. Belirtilen biçim, her ikisi de verileri göstermek ve kullanıcının belirtilen biçimde girdiği verileri ayrıştırmak için kullanılır.  
  
 <xref:System.Windows.Forms.DataGridViewCellStyle> sınıfı, WordWrap, metin hizalaması ve null veritabanı değerlerinin özel görüntüsü için ek biçimlendirme özellikleri sağlar. Daha fazla bilgi için bkz. [nasıl yapılır: Windows Forms DataGridView Denetimindeki verileri biçimlendirme](how-to-format-data-in-the-windows-forms-datagridview-control.md).  
  
## <a name="formatting-with-the-cellformatting-event"></a>CellFormatting olayı ile biçimlendirme  
 Temel biçimlendirme gereksinimlerinizi karşılamıyorsa, <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> olayı için bir işleyicide özel veri biçimlendirmesi sağlayabilirsiniz. İşleyiciye geçirilen <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs>, başlangıçta hücre değerini içeren bir <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> özelliğine sahiptir. Normalde, bu değer otomatik olarak görüntüleme türüne dönüştürülür. Değeri kendiniz dönüştürmek için <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> özelliğini görüntüleme türünün bir değeri olarak ayarlayın.  
  
> [!NOTE]
> Hücre için bir biçim dizesi etkeyse, <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs.FormattingApplied%2A> özelliğini `true`olarak ayarlamadığınız müddetçe <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> Özellik değeri değişiklerinizi geçersiz kılar.  
  
 <xref:System.Windows.Forms.DataGridView.CellFormatting> olay, değerlerine göre tek tek hücreler için <xref:System.Windows.Forms.DataGridViewCellStyle> özellikleri ayarlamak istediğinizde de kullanışlıdır. Daha fazla bilgi için bkz. [nasıl yapılır: Windows Forms DataGridView Denetimindeki veri biçimlendirmeyi özelleştirme](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).  
  
 Kullanıcı tarafından belirtilen değerlerin varsayılan ayrıştırması gereksinimlerinizi karşılamıyorsa, özel ayrıştırma sağlamak için <xref:System.Windows.Forms.DataGridView> denetiminin <xref:System.Windows.Forms.DataGridView.CellParsing> olayını işleyebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [Windows Forms DataGridView Denetiminde Verileri Görüntüleme](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetimindeki Hücre Stilleri](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Nasıl yapılır: Windows Forms DataGridView Denetiminde Verileri Biçimlendirme](how-to-format-data-in-the-windows-forms-datagridview-control.md)
- [Nasıl yapılır: Windows Forms DataGridView Denetiminde Veri Biçimlendirmeyi Özelleştirme](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
