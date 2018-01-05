---
title: "Nasıl yapılır: Tasarımcı Kullanarak Windows Formları DataGridView Denetimi İçin Varsayılan Hücre Stilleri ve Veri Biçimleri Ayarlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], setting styles
- data formats
- data [Windows Forms], setting formats
ms.assetid: fc6da49f-8942-41da-b49f-b2afc38cc656
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2785b666039b9a8594e86cdd3a6fb25b9c382158
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-default-cell-styles-and-data-formats-for-the-windows-forms-datagridview-control-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Windows Formları DataGridView Denetimi İçin Varsayılan Hücre Stilleri ve Veri Biçimleri Ayarlama
<xref:System.Windows.Forms.DataGridView> Denetimi, varsayılan hücre stilleri belirtin ve veri biçimleri için tüm denetim, belirli sütunlar için satır ve sütun üstbilgilerinin ve muhasebe efekti oluşturmak için satır değişen hücre sağlar. Varsayılan stiller ayarlamak için tüm denetim stilleri değişen satırları ve sütunları için varsayılan tarafından geçersiz kılınır. Ayrıca, tek tek satır ve hücre kodunu kümesindeki stilleri varsayılan stillerini geçersiz kılar.  
  
 Hücre stilleri hakkında daha fazla bilgi için bkz: [Windows Forms DataGridView denetimindeki hücre stilleri](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md). Satırların değişerek stilleri ayarlamak için bkz: [nasıl yapılır: ayarlama Alternatif satır stillerini Windows Forms DataGridView denetimi kullanan bir tasarımcı](../../../../docs/framework/winforms/controls/set-alternating-row-styles-for-the-datagrid-using-the-designer.md).  
  
 Kullanarak stiller de ayarlayabilirsiniz <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> özelliği denetimine eklenecek tüm satırları etkiler. Satır şablonunu hakkında daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms DataGridView denetiminde satırları özelleştirmek için satır şablonunu kullanma](../../../../docs/framework/winforms/controls/use-the-row-template-to-customize-rows-in-the-datagrid.md).  
  
 Aşağıdaki yordamlar gerektiren bir **Windows uygulaması** içeren bir form ile proje bir <xref:System.Windows.Forms.DataGridView> denetim. Böyle bir proje ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir Windows uygulaması projesi oluşturduğunuzda](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) ve [nasıl yapılır: Windows Forms denetimlerine ekleme](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-set-default-styles-for-all-cells-in-the-control"></a>Varsayılan stiller tüm hücreler, denetimi ayarlamak için  
  
1.  Seçin <xref:System.Windows.Forms.DataGridView> Denetim Tasarımcısı'nda.  
  
2.  İçinde **özellikleri** penceresinde, üç nokta düğmesini (![VisualStudioEllipsesButton ekran](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) yanındaki <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A>, <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>, veya <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> özelliği. **CellStyle Oluşturucu** iletişim kutusu görüntülenir.  
  
3.  Kullanarak özellikleri ayarlayarak stil tanımlamak **Önizleme** bölmesinde seçimlerinizi onaylayın.  
  
> [!NOTE]
>  Görsel stiller etkinleştirilirse, satır ve sütun başlıkları (dışında <xref:System.Windows.Forms.DataGridView.TopLeftHeaderCell%2A>) geçerli tema tarafından otomatik olarak biçimlendirilmiş geçersiz kılma <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> ve <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> özellik değerleri.  
>   
>  Seçilen birden fazla hücre stilleri ayarlayabilirsiniz <xref:System.Windows.Forms.DataGridView> değiştirmek istediğiniz hücre stil özelliği için aynı değerleri varsa ancak yalnızca Tasarımcı kullanarak denetler. Bu özellik için bir hücre stilleri farklıysa **özellikleri** windows **CellStyle Oluşturucu** iletişim kutusu boş olacaktır.  
  
### <a name="to-set-default-styles-for-cells-in-individual-columns"></a>Tek tek sütunlarda hücreler için varsayılan stillerini ayarlamak için  
  
1.  Sağ <xref:System.Windows.Forms.DataGridView> Denetim Tasarımcısı'nda ve seçin **Edit Columns**.  
  
2.  Bir sütun seçin **seçili sütun** listesi.  
  
3.  İçinde **sütun özellikleri** kılavuz, üç nokta düğmesini (![VisualStudioEllipsesButton ekran](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) yanındaki <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> özelliği. **CellStyle Oluşturucu** iletişim kutusu görüntülenir.  
  
4.  Kullanarak özellikleri ayarlayarak stil tanımlamak **Önizleme** bölmesinde seçimlerinizi onaylayın.  
  
### <a name="to-format-data-in-cells"></a>Hücrelerde veri biçimlendirmek için  
  
1.  Görüntülemek için aşağıdaki yordamlardan birini kullanın bir **CellStyle Oluşturucu** iletişim kutusu için varsayılan hücre stili özellik ilgili.  
  
2.  İçinde **CellStyle Oluşturucu** iletişim kutusunda, üç nokta düğmesini (![VisualStudioEllipsesButton ekran](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) yanındaki <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> özellik. **Biçim dizesi** iletişim kutusu görüntülenir.  
  
3.  Bir biçim türü seçin, ardından türü (sayısı gibi görüntülenecek ondalık basamak), ayrıntılarını değiştirin kullanarak **örnek** Seçimlerinizi onaylamak için kutuyu.  
  
4.  Bağlıyorsanız <xref:System.Windows.Forms.DataGridView> Denetim null değerler içeren, doldurmak büyük olasılıkla bir veri kaynağına **Null değer** metin kutusu. Hücre değerini bir null başvuru eşit olduğunda bu değeri görüntülenir (`Nothing` Visual Basic'te) veya <xref:System.DBNull.Value?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A?displayProperty=nameWithType>  
 [Windows Forms DataGridView Denetimindeki Hücre Stilleri](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 [Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGridView Denetimi İçin Alternatif Satır Stillerini Ayarlama](../../../../docs/framework/winforms/controls/set-alternating-row-styles-for-the-datagrid-using-the-designer.md)  
 [Nasıl yapılır: bir Windows uygulaması projesi oluşturma](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [Nasıl yapılır: Windows Forms’a Denetimler Ekleme](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
