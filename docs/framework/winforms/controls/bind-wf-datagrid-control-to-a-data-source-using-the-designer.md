---
title: "Nasıl yapılır: Tasarımcı Kullanarak Windows Formları DataGrid Denetimini Veri Kaynağına Bağlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- datasets [Windows Forms], binding to DataGrid control
- data binding [Windows Forms], DataGrid control
- DataGrid control [Windows Forms], data binding
- Windows Forms controls, data binding
- bound controls [Windows Forms]
ms.assetid: 4e96e3d0-b1cc-4de1-8774-bc9970ec4554
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 378f1d80392ae7b2058d5c3b2d987e4810cbd07b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Windows Formları DataGrid Denetimini Veri Kaynağına Bağlama
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Denetimi değiştirir ve işlevlerini ekler <xref:System.Windows.Forms.DataGrid> kontrol; ancak, <xref:System.Windows.Forms.DataGrid> denetim tutulur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz. Daha fazla bilgi için bkz: [farklar arasında Windows Forms DataGridView ve DataGrid denetimleri](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Windows Forms <xref:System.Windows.Forms.DataGrid> denetimi veri kaynağı bilgilerini görüntülemek için özel olarak tasarlanmıştır. Ayarlayarak tasarım zamanında denetimi bağlamak <xref:System.Windows.Forms.DataGrid.DataSource%2A> ve <xref:System.Windows.Forms.DataGrid.DataMember%2A> özelliklerini veya çağırarak çalışma zamanında <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> yöntemi. Çeşitli veri kaynakları verileri görüntüleyebilse de, en tipik veri kümeleri ve veri görünümleri kaynaklardır.  
  
 Tasarım zamanında veri kaynağının kullanılabilir olup olmadığını — Örneğin, form örneği bir veri kümesi veya bir veri görünümü içeriyorsa — kılavuz tasarım zamanında veri kaynağına bağlayabilirsiniz. Sonra veri kılavuzunda nasıl görüneceğini önizlemesini görebilirsiniz.  
  
 Kılavuz ayrıca programlı ve çalışma zamanında bağlayabilirsiniz. Çalışma zamanında alma bilgilere dayalı bir veri kaynağı istediğinizde kullanışlıdır. Örneğin, uygulamayı görüntülemek için bir tablo adını belirtin kullanıcı sağlayabilir. Ayrıca, burada veri kaynağı tasarım zamanında yok durumlarda gerekli değildir. Diziler, koleksiyonlar, yazılmayan veri kümeleri ve veri okuyucuları gibi veri kaynakları içerir.  
  
 Aşağıdaki yordam gerektiren bir **Windows uygulaması** içeren bir form ile proje bir <xref:System.Windows.Forms.DataGrid> denetim. Böyle bir proje ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir Windows uygulaması projesi oluşturduğunuzda](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) ve [nasıl yapılır: Windows Forms denetimlerine ekleme](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md). İçinde [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], <xref:System.Windows.Forms.DataGrid> denetim içinde değil **araç** varsayılan olarak. Bu ekleme hakkında daha fazla bilgi için bkz: [nasıl yapılır: araç kutusu öğeleri Ekle](http://msdn.microsoft.com/en-us/458e119e-17fe-450b-b889-e31c128bd7e0). Ayrıca, [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], kullanabileceğiniz **veri kaynakları** tasarım zamanı veri bağlama için penceresi. Daha fazla bilgi için bkz: [Visual Studio'da verilere denetimler bağlama](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-data-bind-the-datagrid-control-to-a-single-table-in-the-designer"></a>Veri DataGrid denetimini Tasarımcısı'nda tek bir tabloya bağlamak için  
  
1.  Denetimin ayarlamak <xref:System.Windows.Forms.DataGrid.DataSource%2A> özelliği bağlamak istediğiniz veri öğeleri içeren nesne.  
  
2.  Veri kaynağı bir veri kümesi ise <xref:System.Windows.Forms.DataGrid.DataMember%2A> özelliğini bağlamak için tablonun adı.  
  
3.  Veri kaynağı bir veri kümesi ya da bir veri kümesi tabloya dayalı bir veri görünümü ise, veri kümesini doldurmak üzere formuna kodu ekleyin.  
  
     Kullandığınız tam kod burada veri kümesi alma bağlıdır. Veri kümesi bir veritabanından doğrudan doldurulmuş, genellikle çağırmanız `Fill` adlı bir veri kümesi doldurur aşağıdaki kod örneğinde olduğu gibi bir veri bağdaştırıcısı yöntemi `DsCategories1`:  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
4.  (İsteğe bağlı) Sütun stilleri ve uygun tablo stilleri kılavuzuna ekleyin.  
  
     Hiçbir tablo stilleri varsa Tablo görürsünüz, ancak en az biçimlendirme ile tüm sütunları görünür.  
  
### <a name="to-data-bind-the-datagrid-control-to-multiple-tables-in-a-dataset-in-the-designer"></a>Veri DataGrid denetimini veri kümesi Tasarımcısı'nda birden fazla tabloya bağlamak için  
  
1.  Denetimin ayarlamak <xref:System.Windows.Forms.DataGrid.DataSource%2A> özelliği bağlamak istediğiniz veri öğeleri içeren nesne.  
  
2.  Veri kümesi, ilişkili tabloları içeriyorsa (diğer bir deyişle, bir ilişki nesnesi içeriyorsa) ayarlayın <xref:System.Windows.Forms.DataGrid.DataMember%2A> üst tablo adı özelliği.  
  
3.  Veri kümesini doldurmak için kod yazma.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DataGrid denetimine genel bakış](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)  
 [Nasıl yapılır: tabloları ekleyebilir ve sütunları Windows Forms DataGrid denetimi](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)  
 [DataGrid denetimi](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [Windows Forms veri bağlama](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [Visual Studio'da veri erişimi](/visualstudio/data-tools/accessing-data-in-visual-studio)
