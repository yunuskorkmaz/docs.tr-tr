---
title: "Nasıl yapılır: Tasarımcı Kullanarak Windows Formları DataGrid Denetimine Tablolar ve Sütunlar Ekleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- columns [Windows Forms], adding to DataGrid control
- tables [Windows Forms], adding to DataGrid control
- DataGrid control [Windows Forms], adding tables and columns
ms.assetid: 4a6d1b34-b696-476b-bf8a-57c6230aa9e1
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ccc310303c7edb968b43f4d529782979024e8e73
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Windows Formları DataGrid Denetimine Tablolar ve Sütunlar Ekleme
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Denetimi değiştirir ve işlevlerini ekler <xref:System.Windows.Forms.DataGrid> kontrol; ancak, <xref:System.Windows.Forms.DataGrid> denetim tutulur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz. Daha fazla bilgi için bkz: [farklar arasında Windows Forms DataGridView ve DataGrid denetimleri](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Windows Forms'ta verileri görüntüleyebilir <xref:System.Windows.Forms.DataGrid> tablolar ve sütunlar oluşturarak denetiminde <xref:System.Windows.Forms.DataGridTableStyle> nesneleri ve bunlara ekleme <xref:System.Windows.Forms.GridTableStylesCollection> üzerinden erişilen nesne <xref:System.Windows.Forms.DataGrid> denetimin <xref:System.Windows.Forms.DataGrid.TableStyles%2A> özelliği. Hangi veri tablosu belirtilen İçindekiler her tablo stili görüntüler <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> özelliği <xref:System.Windows.Forms.DataGridTableStyle>. Varsayılan olarak, bu veri tablosu içindeki tüm sütunlar tablo stili belirtilen sütun stillerini olmadan görüntüler. Ekleyerek tablodaki hangi sütunların görünür kısıtlayabilirsiniz <xref:System.Windows.Forms.DataGridColumnStyle> nesneleri <xref:System.Windows.Forms.GridColumnStylesCollection>, aracılığıyla erişilen <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> her özellik <xref:System.Windows.Forms.DataGridTableStyle>.  
  
 Aşağıdaki yordamlar gerektiren bir **Windows uygulaması** proje içeren bir form ile bir <xref:System.Windows.Forms.DataGrid> denetim. Böyle bir projeyi ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir Windows uygulaması projesi oluşturduğunuzda](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) ve [nasıl yapılır: Windows Forms denetimlerine ekleme](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md). Varsayılan olarak [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], <xref:System.Windows.Forms.DataGrid> denetim içinde değil **araç**. Bu ekleme hakkında daha fazla bilgi için bkz: [nasıl yapılır: araç kutusu öğeleri Ekle](http://msdn.microsoft.com/library/458e119e-17fe-450b-b889-e31c128bd7e0).  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-add-a-table-to-the-datagrid-control-in-the-designer"></a>Bir Tablo Tasarımcısı DataGrid denetiminde eklemek için  
  
1.  Tablodaki verileri görüntülemek için önce bağlamanız gerekir <xref:System.Windows.Forms.DataGrid> denetlemek için bir veri kümesi. Daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms DataGrid denetimini veri kaynağı kullanarak bir tasarımcı bağlama](../../../../docs/framework/winforms/controls/bind-wf-datagrid-control-to-a-data-source-using-the-designer.md).  
  
2.  Seçin <xref:System.Windows.Forms.DataGrid> denetimin <xref:System.Windows.Forms.DataGrid.TableStyles%2A> Özellikleri penceresinde özelliği ve üç nokta düğmesini (![VisualStudioEllipsesButton ekran görüntüsü](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) yanındaki görüntülenecek özelliği **DataGridTableStyle Koleksiyonu Düzenleyicisi**.  
  
3.  Koleksiyon Düzenleyicisi'nde tıklatın **Ekle** tablo stili eklemek için.  
  
4.  Tıklatın **Tamam** koleksiyon Düzenleyicisi'ni kapatın ve yanındaki üç nokta düğmesine tıklayarak yeniden <xref:System.Windows.Forms.DataGrid.TableStyles%2A> özelliği.  
  
     Koleksiyon Düzenleyicisi'ni yeniden açtığınızda denetime bağlı herhangi bir veri tabloları için aşağı açılan listesinde görünecektir <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> tablo stili özelliği.  
  
5.  İçinde **üyeleri** kutusunu Koleksiyonu Düzenleyicisi tablo stilini tıklatın.  
  
6.  İçinde **özellikleri** select Koleksiyonu Düzenleyicisi kutusunun <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> görüntülemek istediğiniz tablo için değer.  
  
### <a name="to-add-a-column-to-the-datagrid-control-in-the-designer"></a>DataGrid denetimi Tasarımcısı'nda bir sütun eklemek için  
  
1.  İçinde **üyeleri** kutusunun **DataGridTableStyle Koleksiyonu Düzenleyicisi**, uygun tablo stili seçin. İçinde **özellikleri** kutusu seçme Koleksiyonu Düzenleyicisi <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> koleksiyonu ve üç nokta düğmesini tıklatıp (![VisualStudioEllipsesButton ekran] (../../../../docs/framework/winforms/media/vbellipsesbutton.png " vbEllipsesButton")) görüntülenecek özelliği yanındaki **DataGridColumnStyle Koleksiyonu Düzenleyicisi**.  
  
2.  Koleksiyon Düzenleyicisi'nde tıklatın **Ekle** sütun stili veya yanındaki aşağı oka tıklayın **Ekle** sütun türünü belirtin.  
  
     Ya da seçin açılan kutusunda <xref:System.Windows.Forms.DataGridTextBoxColumn> veya <xref:System.Windows.Forms.DataGridBoolColumn> türü.  
  
3.  Kapatmak için Tamam'ı **DataGridColumnStyle Koleksiyonu Düzenleyicisi**ve yanındaki üç nokta düğmesine tıklayarak yeniden <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> özelliği.  
  
     Koleksiyon Düzenleyicisi'ni yeniden açtığınızda, bağlı veri tablosundaki tüm veri sütunları için aşağı açılan listesinde görünür <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> sütun stili özelliği.  
  
4.  İçinde **üyeleri** kutusunu Koleksiyonu Düzenleyicisi sütun stilini tıklatın.  
  
5.  İçinde **özellikleri** select Koleksiyonu Düzenleyicisi kutusunun <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> görüntülemek istediğiniz sütun için değer.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DataGrid Denetimi](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [Nasıl yapılır: Windows Forms DataGrid Denetiminde Sütunları Silme veya Gizleme](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
