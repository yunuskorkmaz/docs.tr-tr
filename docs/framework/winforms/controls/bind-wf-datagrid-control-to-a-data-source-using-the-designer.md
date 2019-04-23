---
title: 'Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGrid Denetimini Veri Kaynağına Bağlama'
ms.date: 03/30/2017
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
ms.openlocfilehash: fe54c650e1d19f36d681053c7da47e12527c5827
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59320892"
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGrid Denetimini Veri Kaynağına Bağlama

> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> Denetimi değiştirir ve işlevsellik ekler <xref:System.Windows.Forms.DataGrid> denetler; ancak, <xref:System.Windows.Forms.DataGrid> denetim korunur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz. Daha fazla bilgi için [farklar arasında Windows Forms DataGridView ve DataGrid denetimleri](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Windows Forms <xref:System.Windows.Forms.DataGrid> denetim bir veri kaynağından bilgileri görüntülemek için özel olarak tasarlanmıştır. Ayarlayarak tasarım zamanında denetimi bağlama <xref:System.Windows.Forms.DataGrid.DataSource%2A> ve <xref:System.Windows.Forms.DataGrid.DataMember%2A> özellikleri veya çağırarak çalışma zamanında <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> yöntemi. Çeşitli veri kaynaklarından verileri görüntüleyebilse de, en sık karşılaşılan veri kümeleri ve veri görünümleri kaynaklarıdır.  
  
 Tasarım zamanında veri kaynağının kullanılabilir olup olmadığını — Örneğin, bir veri kümesi veya bir veri görünümü örneği formu içeren — veri kaynağına kılavuz tasarım zamanında bağlayabilirsiniz. Sonra veri kılavuzunda nasıl görüneceğini önizlemesini görebilirsiniz.  
  
 Bu kılavuz ayrıca programlı olarak ve çalışma zamanında bağlayabilirsiniz. Çalışma zamanında alma bilgilere dayanarak bir veri kaynağı istediğinizde bu kullanışlıdır. Örneğin, uygulamayı görüntülemek için bir tablonun adını belirttiğiniz kullanıcı sağlayabilir. Gerekli durumlarda tasarım zamanında burada veri kaynağı yok. Bu, diziler, koleksiyonlar, yazılmayan veri kümeleri ve veri okuyucu gibi veri kaynakları içerir.  
  
 Aşağıdaki yordam gerektirir bir **Windows uygulama** proje içeren bir form içeren bir <xref:System.Windows.Forms.DataGrid> denetimi. Bu tür bir proje ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: Bir Windows Forms uygulaması projesi oluşturma](/visualstudio/ide/step-1-create-a-windows-forms-application-project) ve [nasıl yapılır: Windows Forms'a denetimler ekleme](how-to-add-controls-to-windows-forms.md). Visual Studio 2005 ' te <xref:System.Windows.Forms.DataGrid> denetimi içinde değil **araç kutusu** varsayılan olarak. Bu ekleme hakkında daha fazla bilgi için bkz: [nasıl yapılır: Araç kutusu öğeleri Ekle](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100)). Visual Studio 2005'te, ayrıca kullandığınız **veri kaynakları** penceresi tasarım zamanı veri bağlama için. Daha fazla bilgi için [Visual Studio'da verilere denetimler bağlama](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-data-bind-the-datagrid-control-to-a-single-table-in-the-designer"></a>Veri DataGrid denetimi Tasarımcısı'nda tek bir tabloya bağlama için  
  
1. Denetimin ayarlamak <xref:System.Windows.Forms.DataGrid.DataSource%2A> özelliğini bağlamak istediğiniz veri öğelerini içeren nesne.  
  
2. Veri kaynağı bir veri kümesi ise <xref:System.Windows.Forms.DataGrid.DataMember%2A> özelliğini bağlanacak tablonun adı.  
  
3. Veri kaynağı bir veri kümesi veya bir veri kümesi tabloyu temel alan bir veri görünümü, forma DataSet'i doldurmak için kod ekleyin.  
  
     Kullandığınız tam kod burada veri veri kümesi alma bağlıdır. Veri kümesi doğrudan bir veritabanından doldurulmuş, genellikle arama `Fill` adlı bir veri kümesi doldurur aşağıdaki kod örneğinde olduğu gibi bir veri bağdaştırıcısı yöntemi `DsCategories1`:  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
4. (İsteğe bağlı) Sütun stillerini ve uygun tablo stilleri kılavuza ekleyin.  
  
     Hiçbir tablo stilleri varsa, bir tablo görürsünüz ancak en az biçimlendirme ile tüm sütunlar görünür.  
  
### <a name="to-data-bind-the-datagrid-control-to-multiple-tables-in-a-dataset-in-the-designer"></a>Veri DataGrid denetimi için bir veri kümesi Tasarımcısı'nda birden çok tablodan bağlamak için  
  
1. Denetimin ayarlamak <xref:System.Windows.Forms.DataGrid.DataSource%2A> özelliğini bağlamak istediğiniz veri öğelerini içeren nesne.  
  
2. Veri kümesi, ilişkili tabloları içeriyorsa (diğer bir deyişle, bir ilişki nesnesi içeriyorsa) ayarlayın <xref:System.Windows.Forms.DataGrid.DataMember%2A> özelliğini üst tablonun adı.  
  
3. DataSet'i doldurmak için kod yazın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataGrid Denetimine Genel Bakış](datagrid-control-overview-windows-forms.md)
- [Nasıl yapılır: Windows Forms DataGrid denetimine tablolar ve sütunlar ekleme](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [DataGrid Denetimi](datagrid-control-windows-forms.md)
- [Windows Forms Veri Bağlama](../windows-forms-data-binding.md)
- [Visual Studio'da verilere erişime](/visualstudio/data-tools/accessing-data-in-visual-studio)
