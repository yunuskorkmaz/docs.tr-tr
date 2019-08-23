---
title: Windows Forms DataGridView Denetimindeki Veri Biçimleri
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting data
- data [Windows Forms], formatting in grids
- data grids [Windows Forms], formatting data
ms.assetid: 07bf558d-3748-42ba-8ba0-37fdef924081
ms.openlocfilehash: 5966f16238999655d6072c1127e5bf16aefde5e4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969181"
---
# <a name="data-formatting-in-the-windows-forms-datagridview-control"></a>Windows Forms DataGridView Denetimindeki Veri Biçimleri
Denetim <xref:System.Windows.Forms.DataGridView> , hücre değerleri ve üst sütunların görüntüleyeceği veri türleri arasında otomatik dönüştürme sağlar. Metin kutusu sütunları, örneğin, tarih, saat, sayı ve numaralandırma değerlerinin dize temsillerini görüntüle ve Kullanıcı tarafından girilen dize değerlerini veri deposunun gerektirdiği türlere Dönüştür.  
  
## <a name="formatting-with-the-datagridviewcellstyle-class"></a>DataGridViewCellStyle sınıfıyla biçimlendirme  
 Denetim, <xref:System.Windows.Forms.DataGridViewCellStyle> sınıf aracılığıyla hücre değerlerinin temel veri biçimlendirmesini sağlar. <xref:System.Windows.Forms.DataGridView> [Biçimlendirme türlerinde](../../../standard/base-types/formatting-types.md)açıklanan biçim <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> belirticilerini kullanarak geçerli varsayılan kültür için tarih, saat, sayı ve numaralandırma değerlerini biçimlendirmek için özelliğini kullanabilirsiniz. Bu değerleri, <xref:System.Windows.Forms.DataGridViewCellStyle.FormatProvider%2A> özelliğini kullanarak belirli kültürler için de biçimlendirebilirsiniz. Belirtilen biçim, her ikisi de verileri göstermek ve kullanıcının belirtilen biçimde girdiği verileri ayrıştırmak için kullanılır.  
  
 <xref:System.Windows.Forms.DataGridViewCellStyle> Sınıfı, WordWrap, metin hizalaması ve null veritabanı değerlerinin özel görüntüsü için ek biçimlendirme özellikleri sağlar. Daha fazla bilgi için [nasıl yapılır: Windows Forms DataGridView Denetimindeki](how-to-format-data-in-the-windows-forms-datagridview-control.md)verileri biçimlendirin.  
  
## <a name="formatting-with-the-cellformatting-event"></a>CellFormatting olayı ile biçimlendirme  
 Temel biçimlendirme gereksinimlerinizi karşılamıyorsa, <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> olay için bir işleyicide özel veri biçimlendirmesi sağlayabilirsiniz. İşleyicisine <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> geçirilen, başlangıçta hücre değerini içeren <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> bir özelliğe sahiptir. Normalde, bu değer otomatik olarak görüntüleme türüne dönüştürülür. Değeri kendiniz dönüştürmek için, <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> özelliği görüntüleme türünün bir değeri olarak ayarlayın.  
  
> [!NOTE]
> Hücre için bir biçim dizesi etkeyse, <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs.FormattingApplied%2A> özelliği olarak `true`ayarlamadığınız takdirde Özellik değeri değişiklerinizi geçersiz kılar.  
  
 Bu olay, değerlerine göre tek tek hücreler için Özellikler <xref:System.Windows.Forms.DataGridViewCellStyle> ayarlamak istediğinizde de yararlı olur. <xref:System.Windows.Forms.DataGridView.CellFormatting> Daha fazla bilgi için [nasıl yapılır: Windows Forms DataGridView Denetimindeki](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)veri biçimlendirmesini özelleştirin.  
  
 Kullanıcı tarafından belirtilen değerlerin varsayılan ayrıştırması gereksinimlerinizi karşılamıyorsa, özel ayrıştırma sağlamak için <xref:System.Windows.Forms.DataGridView.CellParsing> <xref:System.Windows.Forms.DataGridView> denetimin olayını işleyebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [Windows Forms DataGridView Denetiminde Verileri Görüntüleme](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetimindeki Hücre Stilleri](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Nasıl yapılır: Windows Forms DataGridView Denetimindeki verileri biçimlendirme](how-to-format-data-in-the-windows-forms-datagridview-control.md)
- [Nasıl yapılır: Windows Forms DataGridView Denetimindeki veri biçimlendirmeyi özelleştirme](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
